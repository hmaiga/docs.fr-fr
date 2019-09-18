---
title: Emplacement de l’assembly
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6427f7d005c43ef9e83387e865f71009b683a7c4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973179"
---
# <a name="assembly-location"></a><span data-ttu-id="f2597-102">Emplacement de l’assembly</span><span class="sxs-lookup"><span data-stu-id="f2597-102">Assembly location</span></span>
<span data-ttu-id="f2597-103">L’emplacement d’un assembly détermine si le common language runtime peut le localiser quand il est référencé, et il peut aussi déterminer si l’assembly peut être partagé avec d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="f2597-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="f2597-104">Vous pouvez déployer un assembly dans les emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="f2597-104">You can deploy an assembly in the following locations:</span></span>  
  
- <span data-ttu-id="f2597-105">Répertoire ou sous-répertoires de l’application.</span><span class="sxs-lookup"><span data-stu-id="f2597-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="f2597-106">Il s’agit de l’emplacement le plus courant pour déployer un assembly.</span><span class="sxs-lookup"><span data-stu-id="f2597-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="f2597-107">Les sous-répertoires du répertoire racine d’une application peuvent être basés sur la langue ou la culture.</span><span class="sxs-lookup"><span data-stu-id="f2597-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="f2597-108">Si un assembly a des informations de l’attribut de culture, il doit se trouver dans un sous-répertoire sous le répertoire de l’application avec le nom de cette culture.</span><span class="sxs-lookup"><span data-stu-id="f2597-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
- <span data-ttu-id="f2597-109">Le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f2597-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="f2597-110">Il s’agit d’un cache de code au niveau de la machine, qui est installé partout où le common language runtime est installé.</span><span class="sxs-lookup"><span data-stu-id="f2597-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="f2597-111">Dans la plupart des cas, si vous prévoyez de partager un assembly entre plusieurs applications, vous devez le déployer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f2597-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
- <span data-ttu-id="f2597-112">Sur un serveur HTTP.</span><span class="sxs-lookup"><span data-stu-id="f2597-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="f2597-113">Un assembly déployé sur un serveur HTTP doit avoir un nom fort ; vous pointez vers l’assembly dans la section codebase du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f2597-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2597-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2597-114">See also</span></span>

- [<span data-ttu-id="f2597-115">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="f2597-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="f2597-116">Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="f2597-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="f2597-117">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="f2597-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="f2597-118">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="f2597-118">Program with assemblies</span></span>](program.md)