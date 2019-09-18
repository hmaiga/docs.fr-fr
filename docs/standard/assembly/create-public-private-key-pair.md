---
title: 'Procédure : Créer une paire de clés publique/privée'
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 62c38494e29541bd490d69ccc8de485217b9514a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991702"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="7a5d1-102">Procédure : Créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="7a5d1-102">How to: Create a public-private key pair</span></span>

<span data-ttu-id="7a5d1-103">Pour signer un assembly avec un nom fort, vous devez disposer d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="7a5d1-104">Cette paire de clés de chiffrement public et privé est utilisée lors de la compilation pour créer un assembly avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="7a5d1-105">Vous pouvez créer une paire de clés à l’aide de l’[outil Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="7a5d1-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="7a5d1-106">Les fichiers de paire de clés ont généralement une extension *. snk* .</span><span class="sxs-lookup"><span data-stu-id="7a5d1-106">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="7a5d1-107">Dans Visual Studio, les C# pages de propriétés du projet et Visual Basic comprennent un onglet **signature** qui vous permet de sélectionner des fichiers de clé existants ou de générer de nouveaux fichiers de clé sans utiliser *sn. exe*.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="7a5d1-108">Dans Visual C++, vous pouvez spécifier l’emplacement d’un fichier de clés existant dans la page de propriétés **Avancé** de la section **Éditeur de liens**, dans la section **Propriétés de Configuration** de la fenêtre **Pages de propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="7a5d1-109">L’utilisation de l' <xref:System.Reflection.AssemblyKeyFileAttribute> attribut pour identifier les paires de fichiers de clés est devenue obsolète à partir de Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="7a5d1-110">Créer une paire de clés</span><span class="sxs-lookup"><span data-stu-id="7a5d1-110">Create a key pair</span></span>

<span data-ttu-id="7a5d1-111">Pour créer une paire de clés, à l’invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7a5d1-111">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="7a5d1-112">**sn –k** \<*nom de fichier*></span><span class="sxs-lookup"><span data-stu-id="7a5d1-112">**sn –k** \<*file name*></span></span>

<span data-ttu-id="7a5d1-113">Dans cette commande, *nom de fichier* est le nom du fichier de sortie contenant la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="7a5d1-114">L’exemple suivant crée une paire de clés appelée *sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-114">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="7a5d1-115">Si vous avez l’intention de temporiser la signature d’un assembly et que vous contrôlez la paire de clés entière (ce qui est improbable en dehors des scénarios de test), vous pouvez utiliser les commandes suivantes pour générer une paire de clés et ensuite en extraire la clé publique dans un fichier distinct.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="7a5d1-116">Commencez par créer la paire de clés :</span><span class="sxs-lookup"><span data-stu-id="7a5d1-116">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="7a5d1-117">Procédez ensuite à l’extraction de la clé publique de la paire de clés et copiez-la dans un fichier distinct :</span><span class="sxs-lookup"><span data-stu-id="7a5d1-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="7a5d1-118">Une fois que vous avez créé la paire de clés, vous devez placer le fichier à l’endroit où les outils de signature de nom fort peuvent le trouver.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="7a5d1-119">Lorsque vous signez un assembly avec un nom fort, l’utilitaire [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) recherche le fichier de clés par rapport au répertoire en cours et au répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="7a5d1-120">Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez vous contenter de copier la clé dans le répertoire en cours contenant vos modules de code.</span><span class="sxs-lookup"><span data-stu-id="7a5d1-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="7a5d1-121">Si vous utilisez une version antérieure de Visual Studio qui ne dispose pas d’onglet **Signature** dans les propriétés du projet, l’emplacement du fichier de clés recommandé est le répertoire du projet avec l’attribut de fichier spécifié comme suit :</span><span class="sxs-lookup"><span data-stu-id="7a5d1-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="7a5d1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a5d1-122">See also</span></span>

- [<span data-ttu-id="7a5d1-123">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="7a5d1-123">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)