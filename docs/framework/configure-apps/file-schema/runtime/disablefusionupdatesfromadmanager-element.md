---
title: Élément <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117440"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<élément disableFusionUpdatesFromADManager >
Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableFusionUpdatesFromADManager** >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie si la capacité par défaut de remplacer les paramètres de fusion est désactivée.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|valeur|Description|  
|-----------|-----------------|  
|0|Ne désactivez pas la possibilité de remplacer les paramètres de fusion. Il s’agit du comportement par défaut, à partir du .NET Framework 4.|  
|1|Désactivez la possibilité de remplacer les paramètres de fusion. Cela revient au comportement des versions antérieures du .NET Framework.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 À partir du .NET Framework 4, le comportement par défaut consiste à autoriser l’objet <xref:System.AppDomainManager> à substituer des paramètres de configuration à l’aide de la propriété <xref:System.AppDomainSetup.ConfigurationFile%2A> ou de la méthode <xref:System.AppDomainSetup.SetConfigurationBytes%2A> de l’objet <xref:System.AppDomainSetup> qui est passé à votre implémentation de la méthode <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> , dans votre sous-classe de <xref:System.AppDomainManager>. Pour le domaine d’application par défaut, les paramètres que vous modifiez remplacent ceux qui ont été spécifiés par le fichier de configuration de l’application. Pour les autres domaines d’application, ils remplacent les paramètres de configuration qui ont été transmis à la méthode <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>.  
  
 Vous pouvez transmettre de nouvelles informations de configuration ou passer la valeur null (`Nothing` dans Visual Basic) pour éliminer les informations de configuration qui ont été transmises.  
  
 Ne transmettez pas d’informations de configuration à la fois à la propriété <xref:System.AppDomainSetup.ConfigurationFile%2A> et à la méthode <xref:System.AppDomainSetup.SetConfigurationBytes%2A>. Si vous passez des informations de configuration aux deux, les informations que vous passez à la propriété <xref:System.AppDomainSetup.ConfigurationFile%2A> sont ignorées, car la méthode <xref:System.AppDomainSetup.SetConfigurationBytes%2A> substitue les informations de configuration du fichier de configuration de l’application. Si vous utilisez la propriété <xref:System.AppDomainSetup.ConfigurationFile%2A>, vous pouvez passer NULL (`Nothing` dans Visual Basic) à la méthode <xref:System.AppDomainSetup.SetConfigurationBytes%2A> pour éliminer les octets de configuration qui ont été spécifiés dans l’appel à la méthode <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>.  
  
 Outre les informations de configuration, vous pouvez modifier les paramètres suivants sur l’objet <xref:System.AppDomainSetup> qui est passé à votre implémentation de la méthode <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> : <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>et <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 En guise d’alternative à l’utilisation de l’élément `<disableFusionUpdatesFromADManager>`, vous pouvez désactiver le comportement par défaut en créant un paramètre de registre ou en définissant une variable d’environnement. Dans le registre, créez une valeur DWORD nommée `COMPLUS_disableFusionUpdatesFromADManager` sous `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`, puis définissez la valeur sur 1. Sur la ligne de commande, définissez la variable d’environnement `COMPLUS_disableFusionUpdatesFromADManager` sur 1.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment désactiver la possibilité de substituer des paramètres de fusion à l’aide de l’élément `<disableFusionUpdatesFromADManager>`.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Méthode de localisation des assemblys par le runtime](../../../deployment/how-the-runtime-locates-assemblies.md)
