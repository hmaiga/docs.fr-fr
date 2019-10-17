---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394433"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="06ded-101">Framework partagé : suppression de Microsoft. AspNetCore. All</span><span class="sxs-lookup"><span data-stu-id="06ded-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="06ded-102">À partir de ASP.NET Core 3,0, le reconditionnement `Microsoft.AspNetCore.All` et l’infrastructure partagée `Microsoft.AspNetCore.All` correspondante ne sont plus produits.</span><span class="sxs-lookup"><span data-stu-id="06ded-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="06ded-103">Ce package est disponible dans ASP.NET Core 2,2 et continuera à recevoir des mises à jour de maintenance dans ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="06ded-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="06ded-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="06ded-104">Version introduced</span></span>

<span data-ttu-id="06ded-105">3,0</span><span class="sxs-lookup"><span data-stu-id="06ded-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="06ded-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="06ded-106">Old behavior</span></span>

<span data-ttu-id="06ded-107">Les applications peuvent utiliser le reconditionnement `Microsoft.AspNetCore.All` pour cibler l’infrastructure partagée `Microsoft.AspNetCore.All` sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="06ded-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="06ded-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="06ded-108">New behavior</span></span>

<span data-ttu-id="06ded-109">.NET Core 3,0 n’inclut pas d’infrastructure partagée @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="06ded-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="06ded-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="06ded-110">Reason for change</span></span>

<span data-ttu-id="06ded-111">Le sous-package `Microsoft.AspNetCore.All` incluait un grand nombre de dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="06ded-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="06ded-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="06ded-112">Recommended action</span></span>

<span data-ttu-id="06ded-113">Migrez votre projet pour utiliser l’infrastructure `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="06ded-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="06ded-114">Les composants qui étaient précédemment disponibles dans `Microsoft.AspNetCore.All` sont toujours disponibles sur NuGet.</span><span class="sxs-lookup"><span data-stu-id="06ded-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="06ded-115">Ces composants sont maintenant déployés avec votre application au lieu d’être inclus dans le Framework partagé.</span><span class="sxs-lookup"><span data-stu-id="06ded-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="06ded-116">Category</span><span class="sxs-lookup"><span data-stu-id="06ded-116">Category</span></span>

<span data-ttu-id="06ded-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="06ded-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="06ded-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="06ded-118">Affected APIs</span></span>

<span data-ttu-id="06ded-119">aucune.</span><span class="sxs-lookup"><span data-stu-id="06ded-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->