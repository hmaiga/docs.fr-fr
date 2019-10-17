---
ms.openlocfilehash: 4c676a185ff4a7a825acb059bf0a5842ca3922fc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393893"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="b4a1b-101">Framework cible : la prise en charge de .NET Framework a été supprimée</span><span class="sxs-lookup"><span data-stu-id="b4a1b-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="b4a1b-102">À compter de ASP.NET Core 3,0, .NET Framework est un Framework cible non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b4a1b-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="b4a1b-103">Change description</span></span>

<span data-ttu-id="b4a1b-104">.NET Framework 4,8 est la dernière version principale de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="b4a1b-105">Les nouvelles applications de ASP.NET Core doivent être basées sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="b4a1b-106">À compter de la version 3,0 de .NET Core, vous pouvez considérer ASP.NET Core 3,0 comme faisant partie de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="b4a1b-107">Les clients qui utilisent ASP.NET Core avec .NET Framework peuvent continuer de manière totalement prise en charge à l’aide de la [version 2,1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="b4a1b-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="b4a1b-108">Le support et la maintenance pour 2,1 se poursuivent jusqu’au 21 août 2021.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="b4a1b-109">Cette date est de trois ans après la déclaration de la version LTS pour la [stratégie de support .net](https://www.microsoft.com/net/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="b4a1b-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="b4a1b-110">La prise en charge des packages ASP.NET Core 2,1 **sur .NET Framework** s’étend indéfiniment, de manière similaire à la [stratégie de maintenance pour d’autres frameworks ASP.net basés sur des packages](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="b4a1b-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="b4a1b-111">Pour plus d’informations sur le portage à partir de .NET Framework vers .NET Core, consultez [portage vers .net Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4a1b-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="b4a1b-112">les packages `Microsoft.Extensions` (tels que la journalisation, l’injection de dépendances et la configuration) et les Entity Framework Core ne sont pas affectés.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="b4a1b-113">Ils continueront de prendre en charge .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="b4a1b-114">Pour plus d’informations sur la motivation de cette modification, consultez le billet de [blog d’origine](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span><span class="sxs-lookup"><span data-stu-id="b4a1b-114">For more information on the motivation for this change, see [the original blog post](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b4a1b-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b4a1b-115">Version introduced</span></span>

<span data-ttu-id="b4a1b-116">3,0</span><span class="sxs-lookup"><span data-stu-id="b4a1b-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b4a1b-117">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="b4a1b-117">Old behavior</span></span>

<span data-ttu-id="b4a1b-118">ASP.NET Core applications peuvent s’exécuter sur .NET Core ou sur .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b4a1b-119">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="b4a1b-119">New behavior</span></span>

<span data-ttu-id="b4a1b-120">Les applications ASP.NET Core ne peuvent être exécutées que sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b4a1b-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b4a1b-121">Recommended action</span></span>

<span data-ttu-id="b4a1b-122">Effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4a1b-122">Take one of the following actions:</span></span>

- <span data-ttu-id="b4a1b-123">Conservez votre application sur ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="b4a1b-124">Migrez votre application et les dépendances vers .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="b4a1b-125">Category</span><span class="sxs-lookup"><span data-stu-id="b4a1b-125">Category</span></span>

<span data-ttu-id="b4a1b-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b4a1b-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b4a1b-127">API affectées</span><span class="sxs-lookup"><span data-stu-id="b4a1b-127">Affected APIs</span></span>

<span data-ttu-id="b4a1b-128">aucune.</span><span class="sxs-lookup"><span data-stu-id="b4a1b-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->