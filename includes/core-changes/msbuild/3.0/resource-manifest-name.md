---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451883"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="3a018-101">Noms des fichiers manifestes de ressources</span><span class="sxs-lookup"><span data-stu-id="3a018-101">Resource manifest file names</span></span>

<span data-ttu-id="3a018-102">À compter de .NET Core 3,0, le nom du fichier manifeste de la ressource générée a changé.</span><span class="sxs-lookup"><span data-stu-id="3a018-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a018-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3a018-103">Version introduced</span></span>

<span data-ttu-id="3a018-104">3.0</span><span class="sxs-lookup"><span data-stu-id="3a018-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a018-105">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="3a018-105">Change description</span></span>

<span data-ttu-id="3a018-106">Avant .NET Core 3,0, quand les métadonnées [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) étaient définies pour un fichier de ressources ( *. resx*) dans le fichier projet MSBuild, le nom du manifeste généré était *namespace. ClassName. Resources*.</span><span class="sxs-lookup"><span data-stu-id="3a018-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="3a018-107">Quand [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) n’a pas été défini, le nom du manifeste généré était *namespace. ClassName. FolderPathRelativeToRoot. culture. Resources*.</span><span class="sxs-lookup"><span data-stu-id="3a018-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="3a018-108">À compter de .NET Core 3,0, lorsqu’un fichier *. resx* est colocalisé avec un fichier source portant le même nom, par exemple dans Windows Forms Apps, le nom du manifeste de la ressource est généré à partir du nom complet du premier type dans le fichier source.</span><span class="sxs-lookup"><span data-stu-id="3a018-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="3a018-109">Par exemple, si *type.cs* est colocalisé avec *type. resx*, le nom du manifeste généré est *namespace. ClassName. Resources*.</span><span class="sxs-lookup"><span data-stu-id="3a018-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="3a018-110">Toutefois, si vous modifiez l’un des attributs de la propriété `EmbeddedResource` pour le fichier *. resx* , le nom du fichier manifeste généré peut être différent :</span><span class="sxs-lookup"><span data-stu-id="3a018-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="3a018-111">Si l’attribut `LogicalName` sur la propriété `EmbeddedResource` est défini, cette valeur est utilisée comme nom de fichier manifeste de la ressource.</span><span class="sxs-lookup"><span data-stu-id="3a018-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="3a018-112">Exemples :</span><span class="sxs-lookup"><span data-stu-id="3a018-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="3a018-113">**Nom du fichier manifeste de la ressource généré**: *nom. Resources* (indépendamment du nom du fichier *. resx* ou de la culture ou de toute autre métadonnée).</span><span class="sxs-lookup"><span data-stu-id="3a018-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="3a018-114">Si `LogicalName` n’est pas défini, mais que l’attribut `ManifestResourceName` de la propriété `EmbeddedResource` est défini, sa valeur, associée à l’extension de fichier *. Resources*, est utilisée comme nom de fichier manifeste de la ressource.</span><span class="sxs-lookup"><span data-stu-id="3a018-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="3a018-115">Exemples :</span><span class="sxs-lookup"><span data-stu-id="3a018-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="3a018-116">**Nom du fichier manifeste de la ressource généré**: *nom. Resources* ou *somename.fr-fr. Resources*.</span><span class="sxs-lookup"><span data-stu-id="3a018-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="3a018-117">Si les règles précédentes ne s’appliquent pas et que l’attribut `DependentUpon` sur l’élément `EmbeddedResource` a la valeur d’un fichier source, le nom de type de la première classe dans le fichier source est utilisé dans le nom du fichier manifeste de la ressource.</span><span class="sxs-lookup"><span data-stu-id="3a018-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="3a018-118">Plus précisément, le nom de fichier généré est *namespace. Classname\[. Culture]. Resources*.</span><span class="sxs-lookup"><span data-stu-id="3a018-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="3a018-119">Exemples :</span><span class="sxs-lookup"><span data-stu-id="3a018-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="3a018-120">**Nom du fichier manifeste de la ressource généré**: *namespace. ClassName. Resources* ou *namespace.ClassName.fr-fr. resources* (où `Namespace.Classname` est le nom de la première classe dans *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="3a018-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="3a018-121">Si les règles précédentes ne s’appliquent pas, `EmbeddedResourceUseDependentUponConvention` est `true` (valeur par défaut pour .NET Core) et un fichier source est colocalisé avec un fichier *. resx* qui porte le même nom de fichier de base, le fichier *. resx* est rendu dépendant du fichier source correspondant, et le nom généré est le même que dans la règle précédente.</span><span class="sxs-lookup"><span data-stu-id="3a018-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="3a018-122">Il s’agit de la règle « paramètres par défaut » pour les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a018-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="3a018-123">Exemples :</span><span class="sxs-lookup"><span data-stu-id="3a018-123">Examples:</span></span>
  
  <span data-ttu-id="3a018-124">Les fichiers *myTypes.cs* et *myTypes. resx* ou *myTypes.fr-fr. resx* se trouvent dans le même dossier.</span><span class="sxs-lookup"><span data-stu-id="3a018-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="3a018-125">**Nom du fichier manifeste de la ressource généré**: *namespace. ClassName. Resources* ou *namespace.ClassName.fr-fr. resources* (où `Namespace.Classname` est le nom de la première classe dans *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="3a018-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>
    
- <span data-ttu-id="3a018-126">Si aucune des règles précédentes ne s’applique, le nom du fichier manifeste de la ressource générée est *RootNamespace. RelativePathWithDotsForSlashes.\[culture.] ressources*.</span><span class="sxs-lookup"><span data-stu-id="3a018-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="3a018-127">Le chemin d’accès relatif est la valeur de l’attribut `Link` de l’élément `EmbeddedResource` s’il est défini.</span><span class="sxs-lookup"><span data-stu-id="3a018-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="3a018-128">Dans le cas contraire, le chemin d’accès relatif est la valeur de l’attribut `Identity` de l’élément `EmbeddedResource`.</span><span class="sxs-lookup"><span data-stu-id="3a018-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="3a018-129">Dans Visual Studio, il s’agit du chemin d’accès entre la racine du projet et le fichier dans Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="3a018-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a018-130">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3a018-130">Recommended action</span></span>

<span data-ttu-id="3a018-131">Si vous n’êtes pas satisfait des noms de manifeste générés, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="3a018-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="3a018-132">Modifiez les métadonnées de votre fichier de ressources en fonction de l’une des règles d’affectation de noms décrites précédemment.</span><span class="sxs-lookup"><span data-stu-id="3a018-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="3a018-133">Définissez `EmbeddedResourceUseDependentUponConvention` sur `false` dans votre fichier projet pour refuser entièrement la nouvelle Convention :</span><span class="sxs-lookup"><span data-stu-id="3a018-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="3a018-134">Si les attributs `LogicalName` ou `ManifestResourceName` sont présents, leurs valeurs sont toujours utilisées pour le nom de fichier généré.</span><span class="sxs-lookup"><span data-stu-id="3a018-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="3a018-135">Category</span><span class="sxs-lookup"><span data-stu-id="3a018-135">Category</span></span>

<span data-ttu-id="3a018-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="3a018-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a018-137">API affectées</span><span class="sxs-lookup"><span data-stu-id="3a018-137">Affected APIs</span></span>

<span data-ttu-id="3a018-138">N/A</span><span class="sxs-lookup"><span data-stu-id="3a018-138">N/A</span></span>