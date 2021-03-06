---
title: Sécurisation des microservices .NET et des applications web
description: 'Sécurité dans les microservices .NET et les applications web : Découvrez les options d’authentification dans les applications web ASP.NET Core.'
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 56ebd95c8a24c7c8d30d3c6acef6650cb63383c6
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988113"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Sécuriser les microservices .NET et les applications web

La sécurité dans les microservices et les applications web est un sujet tellement vaste que la rubrique pourrait facilement remplir plusieurs manuels comme celui-ci. C’est pourquoi nous allons nous concentrer sur l’authentification, l’autorisation et les secrets d’application dans cette section.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implémenter l’authentification dans les microservices .NET et les applications web

Il est souvent nécessaire de limiter l’accès aux ressources et aux API publiées par un service à certains utilisateurs ou clients approuvés. La première étape d’une telle décision d’approbation au niveau des API passe par l’authentification. L’authentification est le processus de vérification fiable de l’identité d’un utilisateur.

Dans les scénarios de microservices, l’authentification est généralement gérée de manière centralisée. Si vous utilisez une passerelle d’API, celle-ci est parfaitement indiquée pour l’authentification, comme l’illustre la figure 9-1. Si vous utilisez cette approche, vérifiez que les différents microservices ne sont pas directement accessibles (sans la passerelle d’API), à moins qu’un dispositif de sécurité supplémentaire ait été mis en place pour authentifier les messages en provenance ou non de la passerelle.

![Diagramme montrant comment l’application mobile client interagit avec le backend.](./media/index/api-gateway-centralized-authentication.png)

**Figure 9-1**. authentification centralisée avec une passerelle d’API

Lorsque la passerelle d’API centralise l’authentification, elle ajoute des informations utilisateur quand les demandes sont transférées aux microservices. Si les services sont accessibles directement, un service d’authentification, comme Azure Active Directory ou un microservice d’authentification dédié faisant office de service d’émission de jeton de sécurité (STS), peut être utilisé pour authentifier les utilisateurs. Les décisions d’approbation sont partagées entre les services à l’aide de jetons de sécurité ou de cookies. (Ces jetons peuvent être partagés entre ASP.NET applications Core, si nécessaire, en implémentant le partage de [cookies](/aspnet/core/security/cookie-sharing).) Ce modèle est illustré dans la figure 9-2.

![Diagramme montrant l’authentification par les microservices de backend.](./media/index/identity-microservice-authentication.png)

**Figure 9-2**. authentification par un microservice d’identité ; l’approbation est partagée à l’aide d’un jeton d’autorisation

Quand les microservices sont accessibles directement, l’approbation, qui comprend l’authentification et l’autorisation, est gérée par un jeton de sécurité émis par un microservice dédié et partagé entre les microservices.

### <a name="authenticate-with-aspnet-core-identity"></a>S’authentifier avec ASP.NET Core Identity

Le principal mécanisme de ASP.NET Core pour identifier les utilisateurs d’une application est le [système d’adhésion ASP.NET Core Identity.](/aspnet/core/security/authentication/identity) ASP.NET Core Identity stocke les informations utilisateur (notamment les revendications, les rôles et les informations de connexion) dans un magasin de données configuré par le développeur. En règle générale, le magasin de données d’ASP.NET Core Identity est un magasin Entity Framework fourni dans le package `Microsoft.AspNetCore.Identity.EntityFrameworkCore`. Cependant, il est possible d’utiliser des magasins personnalisés ou d’autres packages tiers pour stocker les informations d’identité dans Stockage Table Azure, CosmosDB ou à d’autres emplacements.

> [!TIP]
> ASP.NET Core 2.1 et fournit plus tard [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) en tant que razor Class [Library](/aspnet/core/razor-pages/ui-class), de sorte que vous ne verrez pas beaucoup de code nécessaire dans votre projet, comme ce fut le cas pour les versions précédentes. Pour plus de détails sur la façon de personnaliser le code d’identité en fonction de vos besoins, voir [Scaffold Identity dans ASP.NET projets Core](/aspnet/core/security/authentication/scaffold-identity).

Le code suivant est tiré du modèle de projet ASP.NET Core Web Application MVC 3.1 avec l’authentification individuelle du compte utilisateur sélectionnée. Il montre comment configurer ASP.NET’identité de base `Startup.ConfigureServices` en utilisant Le noyau cadre d’entité dans la méthode.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
    //...
}
```

Une fois que ASP.NET’identité de base est configurée, vous l’activez en ajoutant le `app.UseAuthentication()` code suivant dans `endpoints.MapRazorPages()` la méthode du `Startup.Configure` service :

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    //...
    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
    //...
}
```

> [!IMPORTANT]
> Les lignes du code de précédage **DOIVENT être DANS l’ORDRE SHOWN** pour que l’identité fonctionne correctement.

L’utilisation d’ASP.NET Core Identity autorise plusieurs scénarios :

- Création d’informations utilisateur à l’aide du type UserManager (userManager.CreateAsync).

- Authentification des utilisateurs à l’aide du type SignInManager. Vous pouvez `signInManager.SignInAsync` utiliser pour vous `signInManager.PasswordSignInAsync` connecter directement, ou pour confirmer que le mot de passe de l’utilisateur est correct, puis les connecter.

- Identifiez un utilisateur en fonction des informations stockées dans un cookie (qui est lu par ASP.NET Core Identity middleware) afin que les demandes ultérieures d’un navigateur incluront l’identité et les revendications d’un utilisateur connecté.

Par ailleurs, ASP.NET Core Identity prend en charge l’[authentification à deux facteurs](/aspnet/core/security/authentication/2fa).

Pour les scénarios d’authentification qui utilisent un magasin de données utilisateur local et qui conservent l’identité entre les requêtes au moyen de cookies (comme c’est généralement le cas avec les applications web MVC), ASP.NET Core Identity est une solution recommandée.

### <a name="authenticate-with-external-providers"></a>S’authentifier avec des fournisseurs externes

ASP.NET Core prend aussi en charge l’utilisation de [fournisseurs d’authentification externes](/aspnet/core/security/authentication/social/) pour permettre aux utilisateurs de se connecter via des flux [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2). Cela signifie que les utilisateurs peuvent se connecter en utilisant les processus d’authentification existants de certains fournisseurs, tels que Microsoft, Google, Facebook ou Twitter, et associer ces identités à une identité ASP.NET Core dans votre application.

Pour utiliser l’authentification externe, en plus d’inclure l’authentification middleware comme mentionné précédemment, en utilisant la `app.UseAuthentication()` méthode, vous devez également enregistrer le fournisseur externe comme `Startup` indiqué dans l’exemple suivant:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddAuthentication()
        .AddMicrosoftAccount(microsoftOptions =>
        {
            microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ClientId"];
            microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:ClientSecret"];
        })
        .AddGoogle(googleOptions => { ... })
        .AddTwitter(twitterOptions => { ... })
        .AddFacebook(facebookOptions => { ... });
    //...
}
```

Les fournisseurs d’authentification externes courants et les packages NuGet qui leur sont associés vous sont présentés dans le tableau suivant :

| **Fournisseur**  | **Package**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

Dans tous les cas, vous devez effectuer une procédure d’enregistrement des demandes qui dépend du fournisseur et qui implique habituellement :

1. Obtenir une pièce d’identité d’application client.
2. Obtenir un secret d’application client.
3. Configurer une URL de redirection, qui est gérée par le middleware d’autorisation et le fournisseur enregistré
4. Optionnellement, configurer une URL de signature pour gérer correctement le signe dans un seul signe sur (SSO) scénario.

Pour plus de détails sur la configuration de votre application pour un fournisseur externe, consultez [l’authentification du fournisseur externe dans la documentation ASP.NET Core](/aspnet/core/security/authentication/social/)).

>[!TIP]
>Tous les détails sont gérés par l’autorisation middleware et les services mentionnés précédemment. Ainsi, vous n’avez qu’à choisir **l’option** d’authentification de compte utilisateur individuel lorsque vous créez le projet d’application Web ASP.NET Code dans Visual Studio, comme le montre la figure 9-3, en plus d’enregistrer les fournisseurs d’authentification mentionnés précédemment.

![Capture d’écran du dialogue New ASP.NET Core Web Application.](./media/index/select-individual-user-account-authentication-option.png)

**Figure 9-3**. Sélection de l’option Comptes utilisateur individuels, pour l’utilisation de l’authentification externe, lors de la création d’un projet d’application web dans Visual Studio 2019.

Outre les fournisseurs d’authentification externe mentionnés ci-dessus, il existe des packages tiers qui proposent un intergiciel permettant l’utilisation d’un nombre bien plus important de fournisseurs d’authentification externe. Pour une liste, voir le référentiel [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) sur GitHub.

Vous pouvez également créer votre propre middleware d’authentification externe pour répondre à des besoins particuliers.

### <a name="authenticate-with-bearer-tokens"></a>S’authentifier avec des jetons du porteur

L’authentification avec ASP.NET Core Identity (ou Identity couplé à des fournisseurs d’authentification externe) est parfaitement adaptée à de nombreux scénarios d’application web dans lesquels il est approprié de stocker les informations utilisateur dans un cookie. En revanche, dans d’autres scénarios, il n’est pas commun de conserver et de transmettre les données au moyen de cookies.

Par exemple, dans une API web ASP.NET Core qui expose les points de terminaison RESTful potentiellement accessibles par des applications à page unique, des clients natifs, voire d’autres API web, l’authentification par jeton du porteur est généralement privilégiée. Les applications de ce type n’utilisent pas de cookies, mais elles peuvent facilement récupérer un jeton du porteur et l’inclure dans l’en-tête d’autorisation des requêtes suivantes. Pour activer l’authentification par jeton, ASP.NET Core prend en charge plusieurs options en vue d’utiliser [OAuth 2.0](https://oauth.net/2/) et [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>S’authentifier avec un fournisseur d’identité OpenID Connect ou OAuth 2.0

Si les informations utilisateur sont stockées dans Azure Active Directory ou une autre solution d’identité qui prend en charge OpenID Connect ou OAuth 2.0, vous pouvez utiliser le package **Microsoft.AspNetCore.Authentication.OpenIdConnect** pour une authentification via le workflow OpenID Connect. Par exemple, pour s’authentifier auprès du microservice Identity.Api dans eShopOnContainers, une application web ASP.NET Core peut utiliser le middleware de ce package, comme indiqué dans l’exemple simplifié suivant dans `Startup.cs` :

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");
    var sessionCookieLifetime = configuration.GetValue("SessionCookieLifetimeMinutes", 60);

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddCookie(setup => setup.ExpireTimeSpan = TimeSpan.FromMinutes(sessionCookieLifetime))
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl.ToString();
        options.SignedOutRedirectUri = callBackUrl.ToString();
        options.ClientId = useLoadTest ? "mvctest" : "mvc";
        options.ClientSecret = "secret";
        options.ResponseType = useLoadTest ? "code id_token token" : "code id_token";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

Notez que lorsque vous utilisez ce workflow, le middleware ASP.NET Core Identity n’est pas nécessaire dans la mesure où le stockage des informations utilisateur et l’authentification sont gérés par le service Identity.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Émettre des jetons de sécurité à partir d’un service ASP.NET Core

Si vous préférez émettre des jetons de sécurité pour les utilisateurs locaux d’ASP.NET Core Identity plutôt que de faire appel à un fournisseur d’identité externe, vous pouvez profiter de quelques bibliothèques intéressantes.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) et [OpenIddict](https://github.com/openiddict/openiddict-core) sont des fournisseurs OpenID Connect qui s’intègrent facilement à ASP.NET Core Identity pour vous permettre d’émettre des jetons de sécurité à partir d’un service ASP.NET Core. La [documentation IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) explique en détail comment utiliser la bibliothèque. Ceci étant, voici sommairement comment émettre des jetons à l’aide d’IdentityServer4 :

1. Vous appelez l’application. UtilisezIdentityServer dans la méthode Startup.Configure pour ajouter IdentityServer4 au pipeline de traitement des demandes HTTP de l’application. Cela permet à la bibliothèque de remettre les requêtes aux points de terminaison OpenID Connect et OAuth2 comme connect/token.

2. Configurez IdentityServer4 dans Startup.ConfigureServices en effectuant un appel à services.AddIdentityServer.

3. Configurez le serveur d’identité en définissant les données suivantes :

   - Les [informations d’identification](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) à utiliser pour la signature.

   - Les [ressources d’identité et d’API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) auxquelles les utilisateurs pourraient demander à accéder :

      - Les ressources d’API représentent les données protégées ou les fonctionnalités auxquelles un utilisateur peut accéder avec un jeton d’accès. Par exemple, il peut s’agit d’une API web (ou un ensemble d’API) qui nécessite une autorisation.

      - Les ressources d’identité représentent les informations (revendications) qui sont fournies à un client pour identifier un utilisateur. Les revendications peuvent inclure le nom d’utilisateur, l’adresse de messagerie, etc.

   - Les [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) appelés à se connecter pour demander des jetons.

   - Le mécanisme de stockage des informations de l’utilisateur, tel que [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) ou une solution équivalente.

Au moment de spécifier les clients et les ressources que doit utiliser IdentityServer4, vous pouvez transmettre une collection <xref:System.Collections.Generic.IEnumerable%601> du type approprié aux méthodes qui acceptent les magasins de clients ou de ressources en mémoire. Pour les scénarios plus complexes, vous pouvez aussi indiquer des types de fournisseurs de clients ou de ressources via l’injection de dépendances.

Voici un exemple de configuration qui vise à faire utiliser à IdentityServer4 les ressources et les clients en mémoire fournis par un type IClientStore personnalisé :

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //...
    services.AddSingleton<IClientStore, CustomClientStore>();
    services.AddIdentityServer()
        .AddSigningCredential("CN=sts")
        .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
        .AddAspNetIdentity<ApplicationUser>();
    //...
}
```

### <a name="consume-security-tokens"></a>Consommer des jetons de sécurité

L’authentification auprès d’un point de terminaison OpenID Connect ou l’émission de vos propres jetons de sécurité recouvrent certains scénarios. Mais qu’en est-il d’un service qui doit simplement limiter l’accès aux utilisateurs disposant de jetons de sécurité valides qui ont été fournis par un autre service ?

Pour ce scénario, le middleware d’authentification qui gère les jetons JWT est disponible dans le package **Microsoft.AspNetCore.Authentication.JwtBearer**. JWT est l’acronyme de « [JSON Web Token](https://tools.ietf.org/html/rfc7519) » (jeton web JSON). Il s’agit d’un format de jeton de sécurité courant (défini par la norme RFC 7519) destiné à communiquer les revendications de sécurité. Un exemple simplifié d’utilisation de middlewares pour consommer ces jetons pourrait ressembler à ce fragment de code, pris du microservice Ordering.Api d’eShopOnContainers.

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

Les paramètres utilisés dans ce cas sont les suivants :

- `Audience` représente le récepteur du jeton entrant ou la ressource à laquelle le jeton accorde l’accès. Si la valeur spécifiée dans ce paramètre ne correspond pas à celle du paramètre du jeton, celui-ci est rejeté.

- `Authority` est l’adresse du serveur d’authentification émetteur de jetons. L’intergiciel d’authentification du porteur de jeton JWT utilise cet URI pour obtenir la clé publique qui permet de valider la signature du jeton. Par ailleurs, le middleware vérifie que la valeur du paramètre `iss` du jeton correspond à cet URI.

Un autre paramètre, `RequireHttpsMetadata`, est utile pour les tests ; vous définissez ce paramètre avec la valeur false pour effectuer des tests dans des environnements où vous n’avez pas de certificats. Dans les déploiements réels, les jetons du porteur JWT doivent toujours être transmis uniquement sur HTTPS.

Quand cet intergiciel est en place, les jetons JWT sont automatiquement extraits des en-têtes d’autorisation. Ils sont ensuite désérialisés, validés (en utilisant les valeurs des paramètres `Audience` et `Authority`) puis stockés en tant qu’informations utilisateur pour être référencées par la suite par des actions MVC ou des filtres d’autorisation.

L’intergiciel d’authentification du porteur JWT peut aussi prendre en charge des scénarios plus avancés, tels que l’utilisation d’un certificat local pour valider un jeton si l’autorité n’est pas disponible. Pour ce scénario, vous pouvez spécifier un objet `TokenValidationParameters` dans l’objet `JwtBearerOptions`.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Partager des cookies entre les applications** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Introduction à l’identité** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. Authentification à deux facteurs avec SMS** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Permettre l’authentification à l’aide de Facebook, Google et d’autres fournisseurs externes** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. Une introduction à OAuth 2** \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **AspNet.Security.OAuth.Providers** (référentiel GitHub pour fournisseurs d’autorisation OAuth ASP.NET) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **IdentityServer4. Documentation officielle** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Suivant précédent](../implement-resilient-applications/monitor-app-health.md)
>[Next](authorization-net-microservices-web-applications.md)
