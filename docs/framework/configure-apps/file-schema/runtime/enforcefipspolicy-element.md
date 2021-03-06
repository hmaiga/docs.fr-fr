---
title: Élément <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 0d6dd291a24928487a040c0427f058dee80bf836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117384"
---
# <a name="enforcefipspolicy-element"></a>\<élément enforceFIPSPolicy >
Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<enforceFIPSPolicy** >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie s’il faut activer la mise en application d’une exigence de configuration d’ordinateur que les algorithmes de chiffrement doivent être conformes à la norme FIPS.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|valeur|Description|  
|-----------|-----------------|  
|`true`|Si votre ordinateur est configuré pour exiger que les algorithmes de chiffrement soient compatibles FIPS, cette exigence est appliquée. Si une classe implémente un algorithme qui n’est pas compatible avec FIPS, les constructeurs ou les méthodes de `Create` pour cette classe lèvent des exceptions lorsqu’elles sont exécutées sur cet ordinateur. Il s'agit de la valeur par défaut.|  
|`false`|Les algorithmes de chiffrement utilisés par l’application ne doivent pas nécessairement être conformes à la norme FIPS, quelle que soit la configuration de l’ordinateur.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 À partir de la .NET Framework 2,0, la création de classes qui implémentent des algorithmes de chiffrement est contrôlée par la configuration de l’ordinateur. Si l’ordinateur est configuré pour exiger la conformité des algorithmes avec FIPS et qu’une classe implémente un algorithme qui n’est pas compatible avec FIPS, toute tentative de création d’une instance de cette classe lève une exception. Les constructeurs lèvent une exception <xref:System.InvalidOperationException>, et `Create` méthodes lèvent une exception <xref:System.Reflection.TargetInvocationException> avec une exception de <xref:System.InvalidOperationException> interne.  
  
 Si votre application s’exécute sur des ordinateurs dont les configurations nécessitent une compatibilité avec FIPS et que votre application utilise un algorithme qui n’est pas compatible avec FIPS, vous pouvez utiliser cet élément dans votre fichier de configuration pour empêcher le common language runtime (CLR) à partir de application de la conformité FIPS. Cet élément a été introduit dans le .NET Framework 2,0 Service Pack 1.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment empêcher le CLR d’appliquer la conformité FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Modèle de chiffrement](../../../../standard/security/cryptography-model.md)
