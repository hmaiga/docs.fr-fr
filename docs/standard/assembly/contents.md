---
title: Contenu de l’assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- assemblies [.NET Core]
- single-file assemblies
- multifile assemblies [.NET Framework]
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d9268b0ec1ea919730a2ebcd209507692284cc6
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973375"
---
# <a name="assembly-contents"></a><span data-ttu-id="7aba9-102">Contenu de l’assembly</span><span class="sxs-lookup"><span data-stu-id="7aba9-102">Assembly contents</span></span>
<span data-ttu-id="7aba9-103">En général, un assembly statique peut comporter les quatre éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="7aba9-103">In general, a static assembly can consist of four elements:</span></span>

- <span data-ttu-id="7aba9-104">Le [manifeste d’assembly](manifest.md), qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7aba9-104">The [assembly manifest](manifest.md), which contains assembly metadata.</span></span>

- <span data-ttu-id="7aba9-105">les métadonnées des types ;</span><span class="sxs-lookup"><span data-stu-id="7aba9-105">Type metadata.</span></span>  

- <span data-ttu-id="7aba9-106">le code MSIL (Microsoft Intermediate Language) qui implémente les types ;</span><span class="sxs-lookup"><span data-stu-id="7aba9-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span> <span data-ttu-id="7aba9-107">Il est généré par le compilateur à partir d’un ou de plusieurs fichiers de code source.</span><span class="sxs-lookup"><span data-stu-id="7aba9-107">It is generated by the compiler from one or more source code files.</span></span>

- <span data-ttu-id="7aba9-108">un ensemble de ressources.</span><span class="sxs-lookup"><span data-stu-id="7aba9-108">A set of resources.</span></span>  

<span data-ttu-id="7aba9-109">Seul le manifeste d'assembly est requis, mais soit les types, soit les ressources sont nécessaires pour donner à l'assembly des fonctionnalités significatives.</span><span class="sxs-lookup"><span data-stu-id="7aba9-109">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>

<span data-ttu-id="7aba9-110">L’illustration suivante montre ces éléments regroupés dans un seul fichier physique.</span><span class="sxs-lookup"><span data-stu-id="7aba9-110">The following illustration shows these elements grouped in a single physical file.</span></span>

![Diagramme qui montre un assembly à fichier unique appelé MyAssembly.dll.](./media/contents/single-file-assembly.gif)

<span data-ttu-id="7aba9-112">Dans cette illustration, les trois fichiers appartiennent à un assembly, comme décrit dans le manifeste de l'assembly contenu dans MyAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="7aba9-112">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="7aba9-113">Pour le système de fichiers, il s'agit de trois fichiers distincts.</span><span class="sxs-lookup"><span data-stu-id="7aba9-113">To the file system, they are three separate files.</span></span> <span data-ttu-id="7aba9-114">Notez que le fichier Util.netmodule a été compilé comme un module car il ne contient pas d'information sur l'assembly.</span><span class="sxs-lookup"><span data-stu-id="7aba9-114">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="7aba9-115">Lorsque l'assembly a été créé, le manifeste de l'assembly a été ajouté à MyAssembly.dll, en indiquant sa relation avec Util.netmodule et Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="7aba9-115">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>

<span data-ttu-id="7aba9-116">Actuellement, à mesure que vous concevez votre code source, vous prenez des décisions explicites concernant le mode de partition des fonctionnalités de votre application dans un ou plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="7aba9-116">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="7aba9-117">Lors du design de code .NET Framework, vous prendrez des décisions similaires sur le mode de partition des fonctionnalités dans un ou plusieurs assemblys.</span><span class="sxs-lookup"><span data-stu-id="7aba9-117">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="7aba9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aba9-118">See also</span></span>

- [<span data-ttu-id="7aba9-119">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="7aba9-119">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="7aba9-120">Manifeste d’assembly</span><span class="sxs-lookup"><span data-stu-id="7aba9-120">Assembly manifest</span></span>](manifest.md)
- [<span data-ttu-id="7aba9-121">Considérations sur la sécurité des assemblys</span><span class="sxs-lookup"><span data-stu-id="7aba9-121">Assembly security considerations</span></span>](security-considerations.md)