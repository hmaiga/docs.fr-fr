---
title: Réflexion dans .NET
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET], reflection
- EventInfo class, reflection
- common language runtime, reflection
- FieldInfo class, reflection
- ParameterInfo class, reflection
- ConstructorInfo class, reflection
- Assembly class, reflection
- value types, reflection
- reflection, about reflection
- modules, reflection
- runtime, reflection
- Module class, reflection
- MethodInfo class, reflection
- PropertyInfo class, reflection
- type browsers
- reflection
- discovering type information at run time
- type system, reflection
ms.assetid: d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775
ms.openlocfilehash: 90d9cf4c473d73d1eeeb5f2a1098f8626c20359f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180474"
---
# <a name="reflection-in-net"></a>Réflexion dans .NET

Les classes de l' <xref:System.Reflection> espace de noms, <xref:System.Type?displayProperty=nameWithType>ainsi que, vous permettent d’obtenir des informations sur les [assemblys](../../standard/assembly/index.md) chargés et les types définis dans ceux-ci, tels que les [classes](../../standard/base-types/common-type-system.md#classes), les [interfaces](../../standard/base-types/common-type-system.md#interfaces)et les types valeur (autrement dit, les [structures](../../standard/base-types/common-type-system.md#structures) et les [énumérations](../../standard/base-types/common-type-system.md#enumerations)). Vous pouvez également utiliser la réflexion pour créer des instances de types au moment de l'exécution, et pour les appeler et y accéder. Pour obtenir des informations sur des aspects spécifiques de la réflexion, consultez [Rubriques connexes](#related_topics) à la fin de cette vue d’ensemble.
  
Le chargeur du [common language runtime](../../standard/clr.md) gère les [domaines d’application](../app-domains/application-domains.md). Ceux-ci constituent des limites définies autour des objets qui ont la même portée d’application. Cette gestion comprend le chargement de chaque assembly dans le domaine d'application approprié et le contrôle de la disposition en mémoire de la hiérarchie des types dans chaque assembly.  
  
Les [assemblys](../app-domains/index.md) contiennent des modules, les modules contiennent des types, et les types contiennent des membres. La réflexion fournit des objets qui encapsulent les assemblys, les modules et les types. Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d'un type, pour lier le type à un objet existant ou pour obtenir le type d'un objet existant. Vous pouvez ensuite appeler les méthodes du type ou accéder à ses champs et à ses propriétés. Les utilisations courantes de la réflexion sont les suivantes :  
  
- Utilisez <xref:System.Reflection.Assembly> pour définir et charger des assemblys, charger les modules répertoriés dans le manifeste d'assembly, et pour localiser un type de cet assembly et créer une instance de celui-ci.  
  
- Utilisez <xref:System.Reflection.Module> pour découvrir des informations comme l'assembly qui contient le module et les classes de ce module. Vous pouvez également obtenir toutes les méthodes globales ou d'autres méthodes spécifiques non globales définies sur le module.  
  
- Utilisez <xref:System.Reflection.ConstructorInfo> pour découvrir des informations comme le nom, les paramètres, les modificateurs d'accès (comme `public` ou `private`) et les détails d'implémentation (comme `abstract` ou `virtual`) d'un constructeur. Utilisez la méthode <xref:System.Type.GetConstructors%2A> ou <xref:System.Type.GetConstructor%2A> d'un type <xref:System.Type> pour appeler un constructeur spécifique.  
  
- Utilisez <xref:System.Reflection.MethodInfo> pour découvrir des informations comme le nom, le type de retour, les paramètres, les modificateurs d'accès (comme `public` ou `private`) et les détails d'implémentation (comme `abstract` ou `virtual`) d'une méthode. Utilisez la méthode <xref:System.Type.GetMethods%2A> ou <xref:System.Type.GetMethod%2A> d'un type <xref:System.Type> pour appeler une méthode spécifique.  
  
- Utilisez <xref:System.Reflection.FieldInfo> pour découvrir des informations comme le nom, les modificateurs d'accès (comme `public` ou `private`) et les détails d'implémentation (comme `static`) d'un champ, et pour obtenir ou définir les valeurs du champ.  
  
- Utilisez <xref:System.Reflection.EventInfo> pour découvrir des informations comme le nom, le type de données du gestionnaire d'événements, les attributs personnalisés, le type déclarant et le type réfléchi d'un événement, et pour ajouter ou supprimer des gestionnaires d'événements.  
  
- Utilisez <xref:System.Reflection.PropertyInfo> pour découvrir des informations comme le nom, le type de données, le type déclarant, le type réfléchi, et l'état en lecture seule ou en écriture d'une propriété, et pour obtenir ou définir les valeurs de la propriété.  
  
- Utilisez <xref:System.Reflection.ParameterInfo> pour découvrir des informations comme le nom d'un paramètre, son type de données, si un paramètre est un paramètre d'entrée ou de sortie, et la position du paramètre dans la signature d'une méthode.  
  
- Utilisez <xref:System.Reflection.CustomAttributeData> pour découvrir des informations sur les attributs personnalisés quand vous travaillez dans le contexte de réflexion uniquement d'un domaine d'application. <xref:System.Reflection.CustomAttributeData> vous permet d'examiner des attributs sans créer des instances de ceux-ci.  
  
Les classes de l'espace de noms <xref:System.Reflection.Emit> fournissent une forme de réflexion spécialisée qui vous permet de créer des types au moment de l'exécution.  
  
La réflexion peut également être utilisée pour créer des applications appelées explorateurs de types, qui permettent aux utilisateurs de sélectionner des types et d'afficher les informations sur ces types.  
  
Il existe d'autres utilisations de la réflexion. Les compilateurs de langages comme JScript utilisent la réflexion pour construire des tables de symboles. Les classes de l'espace de noms <xref:System.Runtime.Serialization> utilisent la réflexion pour accéder aux données et pour déterminer les champs à rendre persistants. Les classes de l'espace de noms <xref:System.Runtime.Remoting> utilisent la réflexion indirectement via la sérialisation.  
  
## <a name="runtime-types-in-reflection"></a>Types au moment de l'exécution dans la réflexion  
La réflexion fournit des classes, comme <xref:System.Type> et <xref:System.Reflection.MethodInfo>, pour représenter des types, des membres, des paramètres et d'autres entités de code. Cependant, quand vous utilisez la réflexion, vous ne travaillez pas directement avec ces classes, dont la plupart sont abstraites (`MustInherit` en Visual Basic). Au lieu de cela, vous utilisez des types fournis par le common language runtime (CLR).  
  
Par exemple, quand vous utilisez l'opérateur C# `typeof` (`GetType` en Visual Basic) pour obtenir un objet <xref:System.Type>, l'objet est réellement d'un type `RuntimeType`. `RuntimeType` dérive de <xref:System.Type> et fournit des implémentation de toutes les méthodes abstraites.  
  
Ces classes d'exécution sont `internal` (`Friend` en Visual Basic). Elles ne sont pas documentées distinctement de leurs classes de base, car leur comportement est décrit par la documentation de la classe de base.  
  
<a name="related_topics"></a>

## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Affichage des informations de type](viewing-type-information.md)|Décrit la classe <xref:System.Type> et fournit des exemples de code qui montrent comment utiliser <xref:System.Type> avec plusieurs classes de réflexion pour obtenir des informations sur les constructeurs, les méthodes, les champs, les propriétés et les événements.|  
|[Réflexion et types génériques](reflection-and-generic-types.md)|Explique comment la réflexion gère les paramètres de types et les arguments de types des types génériques et des méthodes génériques.|  
|[Considérations sur la sécurité de la réflexion](security-considerations-for-reflection.md)|Décrit les règles qui déterminent à quel degré la réflexion peut être utilisée pour découvrir des informations sur les types et accéder aux types.|  
|[Chargement et utilisation dynamiques des types](dynamically-loading-and-using-types.md)|Décrit l’interface de liaison personnalisée de la réflexion qui prend en charge la liaison tardive.|  
|[Guide pratique pour charger des assemblys dans le contexte de réflexion uniquement](how-to-load-assemblies-into-the-reflection-only-context.md)|Décrit le contexte de chargement de réflexion seule. Montre comment charger un assembly, tester le contexte et examiner les attributs appliqués à un assembly dans le contexte de réflexion uniquement.|  
|[Accès aux attributs personnalisés](accessing-custom-attributes.md)|Montre l'utilisation de la réflexion pour déterminer l'existence et les valeurs des attributs.|  
|[Spécification des noms de types qualifiés complets](specifying-fully-qualified-type-names.md)|Décrit le format des noms complets des types sous la forme Backus-Naur (BNF) et la syntaxe requise pour spécifier les caractères spéciaux, les noms d'assemblys, les pointeurs, les références et les tableaux.|  
|[Guide pratique pour raccorder un délégué à l’aide de la réflexion](how-to-hook-up-a-delegate-using-reflection.md)|Explique comment créer un délégué pour une méthode et raccorder le délégué à un événement. Explique comment créer une méthode de gestion d'événements à l'exécution à l'aide de <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Émission d’assemblys et de méthodes dynamiques](emitting-dynamic-methods-and-assemblies.md)|Explique comment générer des assemblys dynamiques et des méthodes dynamiques.|  
  
## <a name="reference"></a>Informations de référence  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  
