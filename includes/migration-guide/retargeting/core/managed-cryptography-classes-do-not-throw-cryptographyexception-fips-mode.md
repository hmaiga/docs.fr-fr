---
ms.openlocfilehash: 2b768047a8b08501a8de4666d240072318427f28
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803458"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a><span data-ttu-id="97e9b-101">Les classes de chiffrement managées ne lèvent pas d’exception de chiffrement en mode FIPS</span><span class="sxs-lookup"><span data-stu-id="97e9b-101">Managed cryptography classes do not throw a CryptographyException in FIPS mode</span></span>

|   |   |
|---|---|
|<span data-ttu-id="97e9b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="97e9b-102">Details</span></span>|<span data-ttu-id="97e9b-103">Dans .NET Framework 4.7.2 et versions antérieures, les classes de fournisseur de chiffrement managées comme <xref:System.Security.Cryptography.SHA256Managed> lèvent une <xref:System.Security.Cryptography.CryptographicException> quand les bibliothèques de chiffrement système sont configurées en mode FIPS.</span><span class="sxs-lookup"><span data-stu-id="97e9b-103">In .NET Framework 4.7.2 and earlier versions, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in FIPS mode.</span></span> <span data-ttu-id="97e9b-104">Ces exceptions sont levées parce que les versions managées ne sont pas sous la certification 140-2 FIPS (Federal Information Processing Standards), et dans le but de bloquer les algorithmes de chiffrement qui n’étaient pas considérés comme approuvés selon les règles FIPS.</span><span class="sxs-lookup"><span data-stu-id="97e9b-104">These exceptions are thrown because the managed versions have not undergone FIPS (Federal Information Processing Standards) 140-2 certification, as well as to block cryptographic algorithms that were not considered to be approved based on the FIPS rules.</span></span>  <span data-ttu-id="97e9b-105">Étant donné que peu de développeurs ont leurs ordinateurs de développement en mode FIPS, ces exceptions sont fréquemment levées sur les systèmes de production uniquement. Les applications qui ciblent .NET Framework 4.8 et versions ultérieures basculent automatiquement vers la stratégie plus récente et plus souple afin qu’une <xref:System.Security.Cryptography.CryptographicException> ne soit plus levée par défaut dans ces cas précis.</span><span class="sxs-lookup"><span data-stu-id="97e9b-105">Because few developers have their development machines in FIPS mode, these exceptions are frequently thrown only on production systems.Applications that target .NET Framework 4.8 and later versions automatically switch to the newer, relaxed policy, so that a <xref:System.Security.Cryptography.CryptographicException> is no longer thrown by default in such cases.</span></span> <span data-ttu-id="97e9b-106">Les classes de chiffrement managées redirigent plutôt les opérations de chiffrement vers une bibliothèque de chiffrement système.</span><span class="sxs-lookup"><span data-stu-id="97e9b-106">Instead, the managed cryptography classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="97e9b-107">Ce changement de stratégie supprime efficacement une différence pouvant potentiellement prêter à confusion entre les environnements de développement et les environnements de production, et permet d’exécuter les composants natifs et les composants managés sous la même stratégie de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="97e9b-107">This policy change effectively removes a potentially confusing difference between developer environments and the production environments and makes native components and managed components operate under the same cryptographic policy.</span></span>|
|<span data-ttu-id="97e9b-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="97e9b-108">Suggestion</span></span>|<span data-ttu-id="97e9b-109">Si ce comportement est indésirable, vous pouvez choisir de ne plus y adhérer et restaurer le comportement précédent pour qu’une <xref:System.Security.Cryptography.CryptographicException> soit levée en mode FIPS en ajoutant le paramètre de configuration [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant dans la section [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="97e9b-109">If this behavior is undesirable, you can opt out of it and restore the previous behavior so that a <xref:System.Security.Cryptography.CryptographicException> is thrown in FIPS mode by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><span data-ttu-id="97e9b-110">Si votre application cible .NET Framework 4.7.2 ou antérieur, vous pouvez aussi choisir d’adhérer à ce changement en ajoutant le paramètre de configuration [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant dans la section [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="97e9b-110">If your application targets .NET Framework 4.7.2 or earlier, you can also opt in to this change by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="97e9b-111">Portée</span><span class="sxs-lookup"><span data-stu-id="97e9b-111">Scope</span></span>|<span data-ttu-id="97e9b-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="97e9b-112">Edge</span></span>|
|<span data-ttu-id="97e9b-113">Version</span><span class="sxs-lookup"><span data-stu-id="97e9b-113">Version</span></span>|<span data-ttu-id="97e9b-114">4.8</span><span class="sxs-lookup"><span data-stu-id="97e9b-114">4.8</span></span>|
|<span data-ttu-id="97e9b-115">Type</span><span class="sxs-lookup"><span data-stu-id="97e9b-115">Type</span></span>|<span data-ttu-id="97e9b-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="97e9b-116">Retargeting</span></span>|
|<span data-ttu-id="97e9b-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="97e9b-117">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType></li></ul>|
