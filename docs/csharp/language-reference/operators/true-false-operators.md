---
title: Opérateurs true et false - Référence C#
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 5ccd08a348478902bbbac36e99acf7ffc1fc814b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846215"
---
# <a name="true-and-false-operators-c-reference"></a>Opérateurs true et false (rférence C#)

L’opérateur `true` retourne la `true` valeur [bool](../builtin-types/bool.md) pour indiquer que son opérand est certainement vrai. L’opérateur `false` `bool` retourne `true` la valeur pour indiquer que son opérande est définitivement faux. Les opérateurs `true` et `false` ne sont pas forcément complémentaires. Autrement dit, les opérateurs `true` et `false` peuvent retourner la valeur `bool``false` pour le même opérande. Si un type définit un des deux opérateurs, il doit aussi définir un autre opérateur.

> [!TIP]
> Utilisez `bool?` le type, si vous avez besoin de prendre en charge la logique à trois valeur (par exemple, lorsque vous travaillez avec des bases de données qui prennent en charge un type Boolean de trois valeur). C# fournit les opérateurs `&` et `|` qui prennent en charge la logique à trois valeurs avec les opérandes `bool?`. Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](boolean-logical-operators.md).

## <a name="boolean-expressions"></a>Expressions booléennes

Un type avec l’opérateur `true` défini peut être le type de résultat d’une expression conditionnelle de contrôle dans les instructions [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md) et [for](../keywords/for.md) et dans [l’opérateur conditionnel `?:`](conditional-operator.md). Pour plus d’informations, voir la section [Expressions booléennes](~/_csharplang/spec/expressions.md#boolean-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="user-defined-conditional-logical-operators"></a>Opérateurs logiques conditionnels définis par l’utilisateur

Si un type avec les opérateurs `true` et `false` définis [surcharge](operator-overloading.md)[l’opérateur OR logique](boolean-logical-operators.md#logical-or-operator-) `|` ou [l’opérateur AND logique](boolean-logical-operators.md#logical-and-operator-) `&` d’une façon, [l’opérateur OR logique conditionnel](boolean-logical-operators.md#conditional-logical-or-operator-) `||` ou [l’opérateur AND logique conditionnel](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectivement, peut être évalué pour les opérandes de ce type. Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="example"></a> Exemple

L’exemple suivant présente le type qui définit les opérateurs `true` et `false`. Le type surcharge également l’opérateur `&` logique ET `&&` de telle sorte que l’opérateur peut également être évalué pour les opérandes de ce type.

[!code-csharp[true and false operators example](snippets/TrueFalseOperators.cs)]

Remarquez le comportement de court-circuit de l’opérateur `&&`. Lorsque la méthode `GetFuelLaunchStatus` retourne `LaunchStatus.Red`, l’opérande de partie droite de l’opérateur `&&` n’est pas évalué. En effet, `LaunchStatus.Red` est false. Le résultat du AND logique ne dépend donc pas de la valeur de l’opérande de partie droite. Voici la sortie de l’exemple :

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
