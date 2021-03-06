---
title: Opérateurs d'égalité
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 34fc8eef5270369419b76899f0dbe1ace106caf6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741693"
---
# <a name="equality-operators"></a>Opérateurs d'égalité
Cette section traite de la surcharge des opérateurs d’égalité et fait référence à `operator==` et `operator!=` en tant qu’opérateurs d’égalité.

 ❌ ne surchargent pas l’un des opérateurs d’égalité et non l’autre.

 ✔️ Assurez-vous que <xref:System.Object.Equals%2A?displayProperty=nameWithType> et les opérateurs d’égalité ont exactement la même sémantique et les mêmes caractéristiques de performances similaires.

 Cela signifie souvent que `Object.Equals` doit être substitué lorsque les opérateurs d’égalité sont surchargés.

 ❌ éviter de lever des exceptions à partir d’opérateurs d’égalité.

 Par exemple, retourne false si l’un des arguments a la valeur null au lieu de lever `NullReferenceException`.

## <a name="equality-operators-on-value-types"></a>Opérateurs d’égalité sur les types valeur
 ✔️ surchargent les opérateurs d’égalité sur les types valeur, si l’égalité est significative.

 Dans la plupart des langages de programmation, il n’y a pas d’implémentation par défaut de `operator==` pour les types valeur.

## <a name="equality-operators-on-reference-types"></a>Opérateurs d’égalité sur les types référence
 ❌ éviter de surcharger les opérateurs d’égalité sur les types référence mutables.

 De nombreux langages ont des opérateurs d’égalité intégrés pour les types référence. Les opérateurs intégrés implémentent généralement l’égalité des références, et de nombreux développeurs sont surpris lorsque le comportement par défaut est remplacé par l’égalité de la valeur.

 Ce problème est atténué pour les types référence immuables, car l’immuabilité rend beaucoup plus difficile la différence entre l’égalité des références et l’égalité des valeurs.

 ❌ éviter de surcharger les opérateurs d’égalité sur les types référence si l’implémentation est beaucoup plus lente que celle de l’égalité de référence.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
