---
title: Créer des composants d’interface utilisateur réutilisables avec éblouissant
description: Découvrez comment créer des composants d’interface utilisateur réutilisables avec éblouissant et comment ils sont comparés aux contrôles ASP.NET Web Forms.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: b461cf1b572de389c746b894d79d157bf2791e48
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183951"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="5f44f-103">Créer des composants d’interface utilisateur réutilisables avec éblouissant</span><span class="sxs-lookup"><span data-stu-id="5f44f-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5f44f-104">L’une des merveilles de ASP.NET Web Forms est la façon dont il permet l’encapsulation de parties réutilisables de code d’interface utilisateur dans des contrôles d’interface utilisateur réutilisables.</span><span class="sxs-lookup"><span data-stu-id="5f44f-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="5f44f-105">Les contrôles utilisateur personnalisés peuvent être définis dans le balisage à l’aide de fichiers *. ascx* .</span><span class="sxs-lookup"><span data-stu-id="5f44f-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="5f44f-106">Vous pouvez également créer des contrôles serveur élaborés dans du code avec une prise en charge de concepteur complète.</span><span class="sxs-lookup"><span data-stu-id="5f44f-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="5f44f-107">Éblouissant prend également en charge l’encapsulation de l’interface utilisateur par le biais de *composants*.</span><span class="sxs-lookup"><span data-stu-id="5f44f-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="5f44f-108">Un composant :</span><span class="sxs-lookup"><span data-stu-id="5f44f-108">A component:</span></span>

* <span data-ttu-id="5f44f-109">Est un bloc d’interface utilisateur autonome.</span><span class="sxs-lookup"><span data-stu-id="5f44f-109">Is a self-contained chunk of UI.</span></span>
* <span data-ttu-id="5f44f-110">Conserve son propre État et sa logique de rendu.</span><span class="sxs-lookup"><span data-stu-id="5f44f-110">Maintains its own state and rendering logic.</span></span>
* <span data-ttu-id="5f44f-111">Peut définir des gestionnaires d’événements d’interface utilisateur, les lier aux données d’entrée et gérer leur propre cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="5f44f-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
* <span data-ttu-id="5f44f-112">Est généralement défini dans un fichier *. Razor* à l’aide de syntaxe Razor.</span><span class="sxs-lookup"><span data-stu-id="5f44f-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="5f44f-113">Présentation de Razor</span><span class="sxs-lookup"><span data-stu-id="5f44f-113">An introduction to Razor</span></span>

<span data-ttu-id="5f44f-114">Razor est un langage de création de balises léger basé sur HTML C#et.</span><span class="sxs-lookup"><span data-stu-id="5f44f-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="5f44f-115">Avec Razor, vous pouvez effectuer une transition transparente entre le C# balisage et le code pour définir la logique de rendu de votre composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="5f44f-116">Quand le fichier *. Razor* est compilé, la logique de rendu est capturée de manière structurée dans une classe .net.</span><span class="sxs-lookup"><span data-stu-id="5f44f-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="5f44f-117">Le nom de la classe compilée est extrait du nom de fichier *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="5f44f-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="5f44f-118">L’espace de noms est extrait de l’espace de noms par défaut du projet et du chemin d’accès au dossier, ou vous `@namespace` pouvez spécifier explicitement l’espace de noms à l’aide de la directive (plus d’informations sur les directives Razor ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="5f44f-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="5f44f-119">La logique de rendu d’un composant est créée à l’aide d’un balisage HTML C#normal avec la logique dynamique ajoutée à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="5f44f-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="5f44f-120">Le `@` caractère est utilisé pour effectuer la C#transition vers.</span><span class="sxs-lookup"><span data-stu-id="5f44f-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="5f44f-121">Razor est en général intelligent de déterminer quand vous avez rétabli en HTML.</span><span class="sxs-lookup"><span data-stu-id="5f44f-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="5f44f-122">Par exemple, le composant suivant effectue le rendu `<p>` d’une balise avec l’heure actuelle :</span><span class="sxs-lookup"><span data-stu-id="5f44f-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="5f44f-123">Pour spécifier explicitement le début et la fin d' C# une expression, utilisez des parenthèses :</span><span class="sxs-lookup"><span data-stu-id="5f44f-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="5f44f-124">Razor facilite également l’utilisation C# du workflow de contrôle dans votre logique de rendu.</span><span class="sxs-lookup"><span data-stu-id="5f44f-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="5f44f-125">Par exemple, vous pouvez restituer de façon conditionnelle du code HTML comme suit :</span><span class="sxs-lookup"><span data-stu-id="5f44f-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="5f44f-126">Ou vous pouvez générer une liste d’éléments à l’aide C# `foreach` d’une boucle normale comme suit :</span><span class="sxs-lookup"><span data-stu-id="5f44f-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>item.Text</li>
}
</ul>
```

<span data-ttu-id="5f44f-127">Les directives Razor, comme les directives dans ASP.NET Web Forms, contrôlent de nombreux aspects de la compilation d’un composant Razor.</span><span class="sxs-lookup"><span data-stu-id="5f44f-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="5f44f-128">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="5f44f-128">Examples include the component's:</span></span>

* <span data-ttu-id="5f44f-129">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="5f44f-129">Namespace</span></span>
* <span data-ttu-id="5f44f-130">Classe de base</span><span class="sxs-lookup"><span data-stu-id="5f44f-130">Base class</span></span>
* <span data-ttu-id="5f44f-131">Interfaces implémentées</span><span class="sxs-lookup"><span data-stu-id="5f44f-131">Implemented interfaces</span></span>
* <span data-ttu-id="5f44f-132">Paramètres génériques</span><span class="sxs-lookup"><span data-stu-id="5f44f-132">Generic parameters</span></span>
* <span data-ttu-id="5f44f-133">Espaces de noms importés</span><span class="sxs-lookup"><span data-stu-id="5f44f-133">Imported namespaces</span></span>
* <span data-ttu-id="5f44f-134">Routes</span><span class="sxs-lookup"><span data-stu-id="5f44f-134">Routes</span></span>

<span data-ttu-id="5f44f-135">Les directives Razor commencent par `@` le caractère et sont généralement utilisées au début d’une nouvelle ligne au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="5f44f-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="5f44f-136">Par exemple, la `@namespace` directive définit l’espace de noms du composant :</span><span class="sxs-lookup"><span data-stu-id="5f44f-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="5f44f-137">Le tableau suivant récapitule les différentes directives Razor utilisées dans éblouissant et leurs ASP.NET Web Forms équivalents, s’ils existent.</span><span class="sxs-lookup"><span data-stu-id="5f44f-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="5f44f-138">Directive</span><span class="sxs-lookup"><span data-stu-id="5f44f-138">Directive</span></span>    |<span data-ttu-id="5f44f-139">Description</span><span class="sxs-lookup"><span data-stu-id="5f44f-139">Description</span></span>|<span data-ttu-id="5f44f-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f44f-140">Example</span></span>|<span data-ttu-id="5f44f-141">Équivalent Web Forms</span><span class="sxs-lookup"><span data-stu-id="5f44f-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="5f44f-142">Ajoute un attribut de niveau classe au composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="5f44f-143">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5f44f-143">None</span></span>|
|`@code`      |<span data-ttu-id="5f44f-144">Ajoute des membres de classe au composant</span><span class="sxs-lookup"><span data-stu-id="5f44f-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="5f44f-145">Implémente l’interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="5f44f-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="5f44f-146">Utiliser du code-behind</span><span class="sxs-lookup"><span data-stu-id="5f44f-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="5f44f-147">Hérite de la classe de base spécifiée</span><span class="sxs-lookup"><span data-stu-id="5f44f-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="5f44f-148">Injecte un service dans le composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="5f44f-149">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5f44f-149">None</span></span>|
|`@layout`    |<span data-ttu-id="5f44f-150">Spécifie un composant de disposition pour le composant</span><span class="sxs-lookup"><span data-stu-id="5f44f-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="5f44f-151">Définit l’espace de noms pour le composant</span><span class="sxs-lookup"><span data-stu-id="5f44f-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="5f44f-152">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5f44f-152">None</span></span>|
|`@page`      |<span data-ttu-id="5f44f-153">Spécifie l’itinéraire pour le composant</span><span class="sxs-lookup"><span data-stu-id="5f44f-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="5f44f-154">Spécifie un paramètre de type générique pour le composant</span><span class="sxs-lookup"><span data-stu-id="5f44f-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="5f44f-155">Utiliser du code-behind</span><span class="sxs-lookup"><span data-stu-id="5f44f-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="5f44f-156">Spécifie un espace de noms à placer dans la portée</span><span class="sxs-lookup"><span data-stu-id="5f44f-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="5f44f-157">Ajouter un espace de noms dans *Web. config*</span><span class="sxs-lookup"><span data-stu-id="5f44f-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="5f44f-158">Les composants Razor utilisent également de manière intensive les *attributs de directive* sur les éléments pour contrôler différents aspects de la compilation des composants (gestion des événements, liaison de données, composants & références d’éléments, etc.).</span><span class="sxs-lookup"><span data-stu-id="5f44f-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="5f44f-159">Les attributs de directive suivent une syntaxe générique commune dans laquelle les valeurs entre parenthèses sont facultatives :</span><span class="sxs-lookup"><span data-stu-id="5f44f-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="5f44f-160">Le tableau suivant résume les différents attributs des directives Razor utilisées dans éblouissant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="5f44f-161">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f44f-161">Attribute</span></span>    |<span data-ttu-id="5f44f-162">Description</span><span class="sxs-lookup"><span data-stu-id="5f44f-162">Description</span></span>|<span data-ttu-id="5f44f-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f44f-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="5f44f-164">Génère le rendu d’un dictionnaire d’attributs</span><span class="sxs-lookup"><span data-stu-id="5f44f-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="5f44f-165">Crée une liaison de données bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="5f44f-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="5f44f-166">Ajoute un gestionnaire d’événements pour l’événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="5f44f-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="5f44f-167">Spécifie une clé à utiliser par l’algorithme de comparaison pour conserver les éléments d’une collection</span><span class="sxs-lookup"><span data-stu-id="5f44f-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="5f44f-168">Capture une référence au composant ou à l’élément HTML</span><span class="sxs-lookup"><span data-stu-id="5f44f-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="5f44f-169">Les différents attributs de directive utilisés par éblouissant (`@onclick`, `@bind`, `@ref`, etc.) sont traités dans les sections ci-dessous et les chapitres ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="5f44f-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="5f44f-170">La plupart des syntaxes utilisées dans les fichiers *. aspx* et *. ascx* ont des syntaxes parallèles dans Razor.</span><span class="sxs-lookup"><span data-stu-id="5f44f-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="5f44f-171">Vous trouverez ci-dessous une comparaison simple des syntaxes pour ASP.NET Web Forms et Razor.</span><span class="sxs-lookup"><span data-stu-id="5f44f-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="5f44f-172">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="5f44f-172">Feature</span></span>                      |<span data-ttu-id="5f44f-173">Web Forms</span><span class="sxs-lookup"><span data-stu-id="5f44f-173">Web Forms</span></span>           |<span data-ttu-id="5f44f-174">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f44f-174">Syntax</span></span>               |<span data-ttu-id="5f44f-175">Razor</span><span class="sxs-lookup"><span data-stu-id="5f44f-175">Razor</span></span>         |<span data-ttu-id="5f44f-176">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f44f-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="5f44f-177">Directives</span><span class="sxs-lookup"><span data-stu-id="5f44f-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="5f44f-178">Blocs de code</span><span class="sxs-lookup"><span data-stu-id="5f44f-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="5f44f-179">Expressions</span><span class="sxs-lookup"><span data-stu-id="5f44f-179">Expressions</span></span><br><span data-ttu-id="5f44f-180">(Encodé en HTML)</span><span class="sxs-lookup"><span data-stu-id="5f44f-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="5f44f-181">Implicit`@`</span><span class="sxs-lookup"><span data-stu-id="5f44f-181">Implicit: `@`</span></span><br><span data-ttu-id="5f44f-182">Explicitement`@()`</span><span class="sxs-lookup"><span data-stu-id="5f44f-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="5f44f-183">Commentaires</span><span class="sxs-lookup"><span data-stu-id="5f44f-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="5f44f-184">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="5f44f-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="5f44f-185">Pour ajouter des membres à la classe de composant Razor, `@code` utilisez la directive.</span><span class="sxs-lookup"><span data-stu-id="5f44f-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="5f44f-186">Cette technique est similaire à l’utilisation `<script runat="server">...</script>` d’un bloc dans un contrôle utilisateur ou une page ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="5f44f-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="5f44f-187">Comme Razor est basé sur C#, il doit être compilé à partir d' C# un projet ( *. csproj*).</span><span class="sxs-lookup"><span data-stu-id="5f44f-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="5f44f-188">Vous ne pouvez pas compiler de fichiers *. Razor* à partir d’un projet VB ( *. vbproj*).</span><span class="sxs-lookup"><span data-stu-id="5f44f-188">You can't compile *.razor* files from a VB project (*.vbproj*).</span></span> <span data-ttu-id="5f44f-189">Vous pouvez toujours référencer des projets VB à partir de votre projet éblouissant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-189">You can still reference VB projects from your Blazor project.</span></span> <span data-ttu-id="5f44f-190">L’inverse est également vrai.</span><span class="sxs-lookup"><span data-stu-id="5f44f-190">The opposite is true too.</span></span>

<span data-ttu-id="5f44f-191">Pour obtenir une référence complète syntaxe Razor, consultez [syntaxe Razor référence pour ASP.net Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="5f44f-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="5f44f-192">Utiliser des composants</span><span class="sxs-lookup"><span data-stu-id="5f44f-192">Use components</span></span>

<span data-ttu-id="5f44f-193">Hormis le code HTML normal, les composants peuvent également utiliser d’autres composants dans le cadre de leur logique de rendu.</span><span class="sxs-lookup"><span data-stu-id="5f44f-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="5f44f-194">La syntaxe d’utilisation d’un composant dans Razor est semblable à l’utilisation d’un contrôle utilisateur dans une application ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="5f44f-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="5f44f-195">Les composants sont spécifiés à l’aide d’une balise d’élément qui correspond au nom de type du composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="5f44f-196">Par exemple, vous pouvez ajouter un `Counter` composant comme suit :</span><span class="sxs-lookup"><span data-stu-id="5f44f-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="5f44f-197">Contrairement à ASP.NET Web Forms, les composants de éblouissant :</span><span class="sxs-lookup"><span data-stu-id="5f44f-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

* <span data-ttu-id="5f44f-198">N’utilisez pas de préfixe d’élément ( `asp:`par exemple,).</span><span class="sxs-lookup"><span data-stu-id="5f44f-198">Don't use an element prefix (for example, `asp:`).</span></span>
* <span data-ttu-id="5f44f-199">Ne nécessite pas d’inscription sur la page ou dans le *fichier Web. config*.</span><span class="sxs-lookup"><span data-stu-id="5f44f-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="5f44f-200">Considérez les composants Razor comme des types .NET, car c’est exactement ce qu’ils sont.</span><span class="sxs-lookup"><span data-stu-id="5f44f-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="5f44f-201">Si l’assembly contenant le composant est référencé, le composant peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="5f44f-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="5f44f-202">Pour placer l’espace de noms du composant dans la portée `@using` , appliquez la directive :</span><span class="sxs-lookup"><span data-stu-id="5f44f-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="5f44f-203">Comme indiqué dans les projets éblouissants par défaut, il est courant de `@using` placer les directives dans un fichier *_Imports. Razor* afin qu’elles soient importées dans tous les fichiers *. Razor* dans le même répertoire et dans les répertoires enfants.</span><span class="sxs-lookup"><span data-stu-id="5f44f-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="5f44f-204">Si l’espace de noms d’un composant n’est pas dans l’étendue, vous pouvez spécifier un composant à l’aide de son C#nom de type complet, comme vous pouvez le faire dans :</span><span class="sxs-lookup"><span data-stu-id="5f44f-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="5f44f-205">Paramètres de composant</span><span class="sxs-lookup"><span data-stu-id="5f44f-205">Component parameters</span></span>

<span data-ttu-id="5f44f-206">Dans ASP.NET Web Forms, vous pouvez transmettre des paramètres et des données à des contrôles à l’aide de propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="5f44f-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="5f44f-207">Ces propriétés peuvent être définies dans le balisage à l’aide d’attributs ou d’une valeur directement dans le code.</span><span class="sxs-lookup"><span data-stu-id="5f44f-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="5f44f-208">Les composants éblouissant fonctionnent de manière similaire, bien que les propriétés des composants doivent également être marquées `[Parameter]` avec l’attribut pour être considéré comme des paramètres de composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="5f44f-209">Le composant `Counter` suivant définit un paramètre de composant `IncrementAmount` appelé qui peut être utilisé pour `Counter` spécifier la quantité que doit être incrémentée chaque fois que l’utilisateur clique sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="5f44f-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

<span data-ttu-id="5f44f-210">Pour spécifier un paramètre de composant dans éblouissant, utilisez un attribut comme vous le feriez dans ASP.NET Web Forms :</span><span class="sxs-lookup"><span data-stu-id="5f44f-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="5f44f-211">Gestionnaires d’événements</span><span class="sxs-lookup"><span data-stu-id="5f44f-211">Event handlers</span></span>

<span data-ttu-id="5f44f-212">ASP.NET Web Forms et éblouissant fournissent un modèle de programmation basé sur les événements pour gérer les événements d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5f44f-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="5f44f-213">Les clics de bouton et l’entrée de texte sont des exemples de tels événements.</span><span class="sxs-lookup"><span data-stu-id="5f44f-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="5f44f-214">Dans ASP.NET Web Forms, vous utilisez des contrôles serveur HTML pour gérer les événements d’interface utilisateur exposés par le DOM ou vous pouvez gérer les événements exposés par les contrôles serveur Web.</span><span class="sxs-lookup"><span data-stu-id="5f44f-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="5f44f-215">Les événements sont exposés sur le serveur via des demandes de publication de formulaire.</span><span class="sxs-lookup"><span data-stu-id="5f44f-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="5f44f-216">Prenons l’exemple de clic de bouton Web Forms suivant :</span><span class="sxs-lookup"><span data-stu-id="5f44f-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="5f44f-217">*Counter. ascx*</span><span class="sxs-lookup"><span data-stu-id="5f44f-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="5f44f-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="5f44f-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="5f44f-219">Dans éblouissant, vous pouvez inscrire des gestionnaires pour les événements de l’interface utilisateur DOM directement à l’aide `@on{event}`des attributs de directive du formulaire.</span><span class="sxs-lookup"><span data-stu-id="5f44f-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="5f44f-220">L' `{event}` espace réservé représente le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="5f44f-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="5f44f-221">Par exemple, vous pouvez écouter les clics de bouton comme suit :</span><span class="sxs-lookup"><span data-stu-id="5f44f-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="5f44f-222">Les gestionnaires d’événements peuvent accepter un argument facultatif spécifique à l’événement pour fournir plus d’informations sur l’événement.</span><span class="sxs-lookup"><span data-stu-id="5f44f-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="5f44f-223">Par exemple, les événements de souris peuvent `MouseEventArgs` prendre un argument, mais ce n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5f44f-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e) 
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="5f44f-224">Au lieu de faire référence à un groupe de méthodes pour un gestionnaire d’événements, vous pouvez utiliser une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="5f44f-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="5f44f-225">Une expression lambda vous permet de fermer d’autres valeurs dans la portée.</span><span class="sxs-lookup"><span data-stu-id="5f44f-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="5f44f-226">Les gestionnaires d’événements peuvent s’exécuter de façon synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="5f44f-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="5f44f-227">Par exemple, le gestionnaire `OnClick` d’événements suivant s’exécute de façon asynchrone :</span><span class="sxs-lookup"><span data-stu-id="5f44f-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick() 
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="5f44f-228">Une fois qu’un événement est géré, le composant est rendu pour tenir compte des modifications d’état des composants.</span><span class="sxs-lookup"><span data-stu-id="5f44f-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="5f44f-229">Avec les gestionnaires d’événements asynchrones, le composant est rendu immédiatement après la fin de l’exécution du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="5f44f-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="5f44f-230">Le composant est *à nouveau* restitué une fois `Task` le asynchrone terminé.</span><span class="sxs-lookup"><span data-stu-id="5f44f-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="5f44f-231">Ce mode d’exécution asynchrone offre la possibilité d’afficher une interface utilisateur appropriée alors `Task` que le asynchrone est toujours en cours.</span><span class="sxs-lookup"><span data-stu-id="5f44f-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="Get message">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code 
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

<span data-ttu-id="5f44f-232">Les composants peuvent également définir leurs propres événements en définissant un paramètre de `EventCallback<TValue>`composant de type.</span><span class="sxs-lookup"><span data-stu-id="5f44f-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="5f44f-233">Les rappels d’événements prennent en charge toutes les variations des gestionnaires d’événements de l’interface utilisateur DOM : des arguments facultatifs, synchrones ou asynchrones, des groupes de méthodes ou des expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="5f44f-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="5f44f-234">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="5f44f-234">Data binding</span></span>

<span data-ttu-id="5f44f-235">Éblouissant fournit un mécanisme simple pour lier les données d’un composant de l’interface utilisateur à l’état du composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="5f44f-236">Cette approche diffère des fonctionnalités de ASP.NET Web Forms pour la liaison de données de sources de données à des contrôles d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5f44f-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="5f44f-237">Nous traiterons de la gestion des données de différentes sources de données dans la section relative [aux données](data.md) .</span><span class="sxs-lookup"><span data-stu-id="5f44f-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="5f44f-238">Pour créer une liaison de données bidirectionnelle entre un composant de l’interface utilisateur et l’état du `@bind` composant, utilisez l’attribut directive.</span><span class="sxs-lookup"><span data-stu-id="5f44f-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="5f44f-239">Dans l’exemple suivant, la valeur de la case à cocher est liée `isChecked` au champ.</span><span class="sxs-lookup"><span data-stu-id="5f44f-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="5f44f-240">Lorsque le composant est rendu, la valeur de la case à cocher est définie sur la `isChecked` valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="5f44f-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="5f44f-241">Lorsque l’utilisateur active ou désactive la case à `onchange` cocher, l’événement `isChecked` est déclenché et le champ est défini sur la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="5f44f-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="5f44f-242">Dans `@bind` ce cas, la syntaxe est équivalente à la balise suivante :</span><span class="sxs-lookup"><span data-stu-id="5f44f-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="5f44f-243">Pour modifier l’événement utilisé pour la liaison, utilisez l' `@bind:event` attribut.</span><span class="sxs-lookup"><span data-stu-id="5f44f-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="5f44f-244">Les composants peuvent également prendre en charge la liaison de données à leurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="5f44f-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="5f44f-245">Pour la liaison de données, définissez un paramètre de rappel d’événement portant le même nom que le paramètre pouvant être lié.</span><span class="sxs-lookup"><span data-stu-id="5f44f-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="5f44f-246">Le suffixe « modifié » est ajouté au nom.</span><span class="sxs-lookup"><span data-stu-id="5f44f-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="5f44f-247">*PasswordBox. Razor*</span><span class="sxs-lookup"><span data-stu-id="5f44f-247">*PasswordBox.razor*</span></span>

```razor
Password: <input 
    value="@Password" 
    @oninput="OnPasswordChanged" 
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

<span data-ttu-id="5f44f-248">Pour chaîner une liaison de données à un élément d’interface utilisateur sous-jacent, définissez la valeur et gérez l’événement directement sur l' `@bind` élément d’interface utilisateur au lieu d’utiliser l’attribut.</span><span class="sxs-lookup"><span data-stu-id="5f44f-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="5f44f-249">Pour établir une liaison avec un paramètre de composant `@bind-{Parameter}` , utilisez un attribut pour spécifier le paramètre auquel vous souhaitez effectuer la liaison.</span><span class="sxs-lookup"><span data-stu-id="5f44f-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="5f44f-250">Modification de l'état</span><span class="sxs-lookup"><span data-stu-id="5f44f-250">State changes</span></span>

<span data-ttu-id="5f44f-251">Si l’état du composant a été modifié en dehors d’un événement d’interface utilisateur normal ou d’un rappel d’événement, le composant doit indiquer manuellement qu’il doit être de nouveau restitué.</span><span class="sxs-lookup"><span data-stu-id="5f44f-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="5f44f-252">Pour signaler que l’état d’un composant a changé, appelez `StateHasChanged` la méthode sur le composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="5f44f-253">Dans l’exemple ci-dessous, un composant affiche un message `AppState` d’un service qui peut être mis à jour par d’autres parties de l’application.</span><span class="sxs-lookup"><span data-stu-id="5f44f-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="5f44f-254">Le composant inscrit sa `StateHasChanged` méthode avec l' `AppState.OnChange` événement afin que le composant soit rendu chaque fois que le message est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="5f44f-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        shortlist.Add(itinerary);
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a><span data-ttu-id="5f44f-255">Cycle de vie des composants</span><span class="sxs-lookup"><span data-stu-id="5f44f-255">Component lifecycle</span></span>

<span data-ttu-id="5f44f-256">ASP.NET Web Forms Framework a des méthodes de cycle de vie bien définies pour les modules, les pages et les contrôles.</span><span class="sxs-lookup"><span data-stu-id="5f44f-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="5f44f-257">Par exemple, le contrôle suivant implémente des gestionnaires d’événements pour `Init`les `Load`événements de `UnLoad` cycle de vie, et :</span><span class="sxs-lookup"><span data-stu-id="5f44f-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="5f44f-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="5f44f-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="5f44f-259">Les composants éblouissants disposent également d’un cycle de vie bien défini.</span><span class="sxs-lookup"><span data-stu-id="5f44f-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="5f44f-260">Le cycle de vie d’un composant peut être utilisé pour initialiser l’état d’un composant et implémenter des comportements de composant avancés.</span><span class="sxs-lookup"><span data-stu-id="5f44f-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span> 

<span data-ttu-id="5f44f-261">Toutes les méthodes de cycle de vie des composants de éblouissant ont des versions synchrones et asynchrones.</span><span class="sxs-lookup"><span data-stu-id="5f44f-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="5f44f-262">Le rendu des composants est synchrone.</span><span class="sxs-lookup"><span data-stu-id="5f44f-262">Component rendering is synchronous.</span></span> <span data-ttu-id="5f44f-263">Vous ne pouvez pas exécuter une logique asynchrone dans le cadre du rendu des composants.</span><span class="sxs-lookup"><span data-stu-id="5f44f-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="5f44f-264">Toute la logique asynchrone doit s’exécuter dans le `async` cadre d’une méthode Lifecycle.</span><span class="sxs-lookup"><span data-stu-id="5f44f-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="5f44f-265">OnInitialized</span><span class="sxs-lookup"><span data-stu-id="5f44f-265">OnInitialized</span></span>

<span data-ttu-id="5f44f-266">Les `OnInitialized` méthodes `OnInitializedAsync` et sont utilisées pour initialiser le composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="5f44f-267">Un composant est généralement initialisé après son premier rendu.</span><span class="sxs-lookup"><span data-stu-id="5f44f-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="5f44f-268">Une fois qu’un composant a été initialisé, il peut être restitué plusieurs fois avant d’être supprimé.</span><span class="sxs-lookup"><span data-stu-id="5f44f-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="5f44f-269">La `OnInitialized` méthode est similaire à l' `Page_Load` événement dans ASP.NET Web Forms les pages et les contrôles.</span><span class="sxs-lookup"><span data-stu-id="5f44f-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="5f44f-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="5f44f-270">OnParametersSet</span></span>

<span data-ttu-id="5f44f-271">Les `OnParametersSet` méthodes `OnParametersSetAsync` et sont appelées lorsqu’un composant a reçu des paramètres de son parent et que la valeur est assignée aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="5f44f-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="5f44f-272">Ces méthodes sont exécutées après l’initialisation du composant et *chaque fois que le composant est rendu*.</span><span class="sxs-lookup"><span data-stu-id="5f44f-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="5f44f-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="5f44f-273">OnAfterRender</span></span>

<span data-ttu-id="5f44f-274">Les `OnAfterRender` méthodes `OnAfterRenderAsync` et sont appelées après la fin du rendu d’un composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="5f44f-275">Les références à un élément et à un composant sont remplies à ce stade (en savoir plus sur ces concepts ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="5f44f-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="5f44f-276">L’interactivité avec le navigateur est activée à ce stade.</span><span class="sxs-lookup"><span data-stu-id="5f44f-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="5f44f-277">Les interactions avec l’exécution DOM et JavaScript peuvent être effectuées en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="5f44f-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span> 

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

<span data-ttu-id="5f44f-278">`OnAfterRender`et `OnAfterRenderAsync` *ne sont pas appelés lors du prérendu sur le serveur*.</span><span class="sxs-lookup"><span data-stu-id="5f44f-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="5f44f-279">Le `firstRender` paramètre est `true` la première fois que le composant est rendu ; sinon, sa valeur `false`est.</span><span class="sxs-lookup"><span data-stu-id="5f44f-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="5f44f-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="5f44f-280">IDisposable</span></span>

<span data-ttu-id="5f44f-281">Les composants éblouissant peuvent implémenter `IDisposable` pour supprimer des ressources lorsque le composant est supprimé de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5f44f-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="5f44f-282">Un composant Razor peut implémenter `IDispose` à l’aide de la `@implements` directive :</span><span class="sxs-lookup"><span data-stu-id="5f44f-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a><span data-ttu-id="5f44f-283">Références du composant de capture</span><span class="sxs-lookup"><span data-stu-id="5f44f-283">Capture component references</span></span>

<span data-ttu-id="5f44f-284">Dans ASP.NET Web Forms, il est courant de manipuler une instance de contrôle directement dans le code en faisant référence à son ID.</span><span class="sxs-lookup"><span data-stu-id="5f44f-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="5f44f-285">Dans éblouissant, il est également possible de capturer et manipuler une référence à un composant, bien qu’il soit bien moins courant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="5f44f-286">Pour capturer une référence de composant dans éblouissant, utilisez l' `@ref` attribut directive.</span><span class="sxs-lookup"><span data-stu-id="5f44f-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="5f44f-287">La valeur de l’attribut doit correspondre au nom d’un champ définissable avec le même type que le composant référencé.</span><span class="sxs-lookup"><span data-stu-id="5f44f-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

<span data-ttu-id="5f44f-288">Lors du rendu du composant parent, le champ est rempli avec l’instance du composant enfant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="5f44f-289">Vous pouvez ensuite appeler des méthodes sur l’instance de composant ou la manipuler.</span><span class="sxs-lookup"><span data-stu-id="5f44f-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="5f44f-290">La manipulation directe de l’état d’un composant à l’aide de références de composant n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="5f44f-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="5f44f-291">Ce faisant, vous empêchez le rendu automatique du composant aux moments appropriés.</span><span class="sxs-lookup"><span data-stu-id="5f44f-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="5f44f-292">Références des éléments de capture</span><span class="sxs-lookup"><span data-stu-id="5f44f-292">Capture element references</span></span>

<span data-ttu-id="5f44f-293">Les composants éblouissant peuvent capturer des références à un élément.</span><span class="sxs-lookup"><span data-stu-id="5f44f-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="5f44f-294">Contrairement aux contrôles serveur HTML dans ASP.NET Web Forms, vous ne pouvez pas manipuler le DOM directement à l’aide d’une référence d’élément dans éblouissant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="5f44f-295">Éblouissant gère la plupart des interactions DOM pour vous à l’aide de son algorithme de comparaison DOM.</span><span class="sxs-lookup"><span data-stu-id="5f44f-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="5f44f-296">Les références d’élément capturées dans éblouissant sont opaques.</span><span class="sxs-lookup"><span data-stu-id="5f44f-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="5f44f-297">Toutefois, elles sont utilisées pour passer une référence d’élément spécifique dans un appel d’interopérabilité JavaScript.</span><span class="sxs-lookup"><span data-stu-id="5f44f-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="5f44f-298">Pour plus d’informations sur l’interopérabilité JavaScript, consultez [ASP.net Core l’interopérabilité avec éblouissant](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="5f44f-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="5f44f-299">Composants basés sur un modèle</span><span class="sxs-lookup"><span data-stu-id="5f44f-299">Templated components</span></span>

<span data-ttu-id="5f44f-300">Dans ASP.NET Web Forms, vous pouvez créer des *contrôles basés*sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="5f44f-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="5f44f-301">Les contrôles basés sur un modèle permettent au développeur de spécifier une partie du code HTML utilisé pour restituer un contrôle conteneur.</span><span class="sxs-lookup"><span data-stu-id="5f44f-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="5f44f-302">La mécanique de la création de contrôles serveur basés sur des modèles est complexe, mais elle permet de puissants scénarios de rendu des données de manière personnalisable par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5f44f-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="5f44f-303">Les exemples de contrôles basés sur `Repeater` un `DataList`modèle incluent et.</span><span class="sxs-lookup"><span data-stu-id="5f44f-303">Examples of templated controls include `Repeater` and `DataList`.</span></span> 

<span data-ttu-id="5f44f-304">Les composants éblouissants peuvent également être basés sur un modèle en définissant `RenderFragment` des `RenderFragment<T>`paramètres de composant de type ou.</span><span class="sxs-lookup"><span data-stu-id="5f44f-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="5f44f-305">Un `RenderFragment` représente un segment de balisage Razor qui peut ensuite être rendu par le composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="5f44f-306">Un `RenderFragment<T>` est un segment de balisage Razor qui prend un paramètre qui peut être spécifié lors du rendu du fragment de rendu.</span><span class="sxs-lookup"><span data-stu-id="5f44f-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="5f44f-307">Contenu enfant</span><span class="sxs-lookup"><span data-stu-id="5f44f-307">Child content</span></span>

<span data-ttu-id="5f44f-308">Les composants éblouissants peuvent capturer leur contenu enfant sous `RenderFragment` la forme d’un et afficher ce contenu dans le cadre du rendu des composants.</span><span class="sxs-lookup"><span data-stu-id="5f44f-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="5f44f-309">Pour capturer le contenu enfant, définissez un paramètre de composant `RenderFragment` de type et `ChildContent`nommez-le.</span><span class="sxs-lookup"><span data-stu-id="5f44f-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="5f44f-310">*ChildContentComponent. Razor*</span><span class="sxs-lookup"><span data-stu-id="5f44f-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="5f44f-311">Un composant parent peut ensuite fournir le contenu enfant à l’aide d’un syntaxe Razor normal.</span><span class="sxs-lookup"><span data-stu-id="5f44f-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="5f44f-312">Paramètres de modèle</span><span class="sxs-lookup"><span data-stu-id="5f44f-312">Template parameters</span></span>

<span data-ttu-id="5f44f-313">Un composant éblouissant basé sur des modèles peut également définir plusieurs paramètres de composant `RenderFragment` de `RenderFragment<T>`type ou.</span><span class="sxs-lookup"><span data-stu-id="5f44f-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="5f44f-314">Le paramètre d’un `RenderFragment<T>` peut être spécifié lorsqu’il est appelé.</span><span class="sxs-lookup"><span data-stu-id="5f44f-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="5f44f-315">Pour spécifier un paramètre de type générique pour un composant, utilisez `@typeparam` la directive Razor.</span><span class="sxs-lookup"><span data-stu-id="5f44f-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="5f44f-316">*SimpleListView. Razor*</span><span class="sxs-lookup"><span data-stu-id="5f44f-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

<span data-ttu-id="5f44f-317">Lorsque vous utilisez un composant basé sur un modèle, les paramètres de modèle peuvent être spécifiés à l’aide d’éléments enfants qui correspondent aux noms des paramètres.</span><span class="sxs-lookup"><span data-stu-id="5f44f-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="5f44f-318">Les arguments de composant `RenderFragment<T>` de type passés comme éléments ont un paramètre `context`implicite nommé.</span><span class="sxs-lookup"><span data-stu-id="5f44f-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="5f44f-319">Vous pouvez modifier le nom de ce paramètre d’implémentation à `Context` l’aide de l’attribut sur l’élément enfant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="5f44f-320">Tous les paramètres de type générique peuvent être spécifiés à l’aide d’un attribut qui correspond au nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="5f44f-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="5f44f-321">Le paramètre de type sera déduit si possible :</span><span class="sxs-lookup"><span data-stu-id="5f44f-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Content="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="5f44f-322">La sortie de ce composant ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="5f44f-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="5f44f-323">Code-behind</span><span class="sxs-lookup"><span data-stu-id="5f44f-323">Code-behind</span></span>

<span data-ttu-id="5f44f-324">Un composant éblouissant est généralement créé dans un seul fichier *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="5f44f-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="5f44f-325">Toutefois, il est également possible de séparer le code et le balisage à l’aide d’un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="5f44f-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="5f44f-326">Pour utiliser un fichier de composant, ajoutez C# un fichier qui correspond au nom du fichier du composant, mais avec une extension *. cs* ajoutée (*Counter.Razor.cs*).</span><span class="sxs-lookup"><span data-stu-id="5f44f-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="5f44f-327">Utilisez le C# fichier pour définir une classe de base pour le composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="5f44f-328">Vous pouvez nommer la classe de base comme vous le souhaitez, mais il est courant de nommer la classe comme la classe du composant, mais avec une `Base` extension ajoutée (`CounterBase`).</span><span class="sxs-lookup"><span data-stu-id="5f44f-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="5f44f-329">La classe basée sur les composants doit également dériver de `ComponentBase`.</span><span class="sxs-lookup"><span data-stu-id="5f44f-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="5f44f-330">Ensuite, dans le fichier du composant Razor, ajoutez `@inherits` la directive pour spécifier la classe de base pour le`@inherits CounterBase`composant ().</span><span class="sxs-lookup"><span data-stu-id="5f44f-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="5f44f-331">*Counter. Razor*</span><span class="sxs-lookup"><span data-stu-id="5f44f-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="5f44f-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="5f44f-332">*Counter.razor.cs*</span></span>

```csharp
public class CounterBase : ComponentBase 
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

<span data-ttu-id="5f44f-333">La visibilité des membres du composant dans la classe de base doit être `protected` ou `public` pour être visible pour la classe de composant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="5f44f-334">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5f44f-334">Additional resources</span></span>

<span data-ttu-id="5f44f-335">Ce qui précède n’est pas un traitement exhaustif de tous les aspects des composants de éblouissant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="5f44f-336">Pour plus d’informations sur la [création et l’utilisation de ASP.net Core les composants Razor](/aspnet/core/blazor/components), consultez la documentation de l’éblouissant.</span><span class="sxs-lookup"><span data-stu-id="5f44f-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5f44f-337">[Précédent](app-startup.md)
>[Suivant](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="5f44f-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>