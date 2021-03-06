---
title: 'Comment : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
ms.openlocfilehash: 1acd53fad6b0ab173f855850353339190ebdd893
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132542"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Comment : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure

En règle générale, lorsque vous effectuez des opérations arithmétiques de date et d’heure à l’aide de valeurs <xref:System.DateTime> ou <xref:System.DateTimeOffset>, le résultat ne reflète pas les règles d’ajustement des fuseaux horaires. Cela est vrai même lorsque le fuseau horaire de la valeur de date et d’heure est clairement identifiable (par exemple, lorsque la propriété <xref:System.DateTime.Kind%2A> est définie sur <xref:System.DateTimeKind.Local>). Cette rubrique montre comment effectuer des opérations arithmétiques sur les valeurs de date et d’heure qui appartiennent à un fuseau horaire particulier. Les résultats de ces opérations arithmétiques reflètent les règles d’ajustement du fuseau horaire.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Pour appliquer des règles d’ajustement dans les opérations arithmétiques de date et d’heure

1. Implémentez une méthode de couplage étroit d’une valeur de date et d’heure avec le fuseau horaire auquel elle appartient. Par exemple, déclarez une structure qui inclut à la fois la valeur de date et d’heure et son fuseau horaire. L’exemple suivant utilise cette approche pour lier une valeur <xref:System.DateTime> à son fuseau horaire.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Convertit une heure en temps universel coordonné (UTC) en appelant la méthode <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> ou la méthode <xref:System.TimeZoneInfo.ConvertTime%2A>.

3. Effectuez l’opération arithmétique sur l’heure UTC.

4. Convertit l’heure UTC dans le fuseau horaire associé à l’heure d’origine en appelant la méthode <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

L’exemple suivant ajoute deux heures et trente minutes à 9 mars 2008, à 1:30 A.M., heure du Centre des États-Unis. Le passage du fuseau horaire à l’heure d’été se produit trente minutes plus tard, à 2:00, le 9 mars 2008. Étant donné que cet exemple suit les quatre étapes répertoriées à la section précédente, il signale correctement l’heure obtenue, soit 5:00, le 9 mars 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> sont dissociées de tout fuseau horaire auquel elles peuvent appartenir. Pour effectuer des opérations arithmétiques de date et d’heure d’une manière qui applique automatiquement les règles d’ajustement d’un fuseau horaire, le fuseau horaire auquel toute valeur de date et d’heure appartient doit être identifiable immédiatement. Cela signifie qu’une date et une heure et leur fuseau horaire associé doivent être étroitement couplés. Il existe plusieurs manières de procéder, dont les suivantes :

- Supposez que toutes les heures utilisées dans une application appartiennent à un fuseau horaire particulier. Bien qu’appropriée dans certains cas, cette approche présente une souplesse limitée et une portabilité éventuellement limitée.

- Définissez un type qui couple étroitement une valeur de date et d’heure avec son fuseau horaire associé en incluant les deux comme champs. Cette approche est utilisée dans l’exemple de code qui définit une structure pour stocker la date et l’heure, et le fuseau horaire, dans deux champs membres.

L’exemple montre comment effectuer des opérations arithmétiques sur des valeurs de <xref:System.DateTime> afin que les règles d’ajustement de fuseau horaire soient appliquées au résultat. Toutefois, les valeurs <xref:System.DateTimeOffset> peuvent être utilisées tout aussi facilement. L’exemple suivant montre comment le code de l’exemple d’origine peut être adapté pour utiliser <xref:System.DateTimeOffset> au lieu de valeurs <xref:System.DateTime>.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Notez que si cet ajout est effectué simplement sur la valeur <xref:System.DateTimeOffset> sans le convertir au format UTC, le résultat reflète le point correct dans le temps, mais son décalage ne reflète pas celui du fuseau horaire désigné pour cette heure.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- L’importation de l’espace de noms <xref:System> avec l’instruction `using` ( C# obligatoire dans le code).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Exécution d’opérations arithmétiques avec des dates et heures](../../../docs/standard/datetime/performing-arithmetic-operations.md)
