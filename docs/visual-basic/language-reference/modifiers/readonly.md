---
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 8c7e7e7c1571fd7c595ebfd54fb5767078ef41f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351278"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Spécifie qu’une variable ou une propriété peut être lue mais pas écrite.

## <a name="remarks"></a>Notes

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Vous pouvez utiliser `ReadOnly` seulement au niveau du module. Cela signifie que le contexte de déclaration pour un élément `ReadOnly` doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms ou une procédure.

- **Modificateurs combinés.** Vous ne pouvez pas spécifier `ReadOnly` avec `Static` dans la même déclaration.

- **Affectation d’une valeur.** Le code utilisant une propriété `ReadOnly` ne peut pas définir sa valeur. Toutefois, le code qui a accès au stockage sous-jacent peut affecter ou modifier la valeur à tout moment.

     Vous pouvez assigner une valeur à une variable `ReadOnly` uniquement dans sa déclaration ou dans le constructeur d’une classe ou d’une structure dans laquelle elle est définie.

## <a name="when-to-use-a-readonly-variable"></a>Quand utiliser une variable ReadOnly

Dans certaines situations, vous ne pouvez pas utiliser une [instruction Const](../../../visual-basic/language-reference/statements/const-statement.md) pour déclarer et assigner une valeur de constante. Par exemple, l’instruction `Const` peut ne pas accepter le type de données que vous souhaitez affecter, ou vous ne pourrez peut-être pas calculer la valeur au moment de la compilation avec une expression constante. Vous ne connaissez peut-être même pas la valeur au moment de la compilation. Dans ce cas, vous pouvez utiliser une variable `ReadOnly` pour contenir une valeur constante.

> [!IMPORTANT]
> Si le type de données de la variable est un type référence, tel qu’un tableau ou une instance de classe, ses membres peuvent être modifiés même si la variable elle-même est `ReadOnly`. L’exemple suivant illustre ces actions.

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

En cas d’initialisation, le tableau désigné par `characterArray()` contient « x », « y » et « z ». Étant donné que la variable `characterArray` est `ReadOnly`, vous ne pouvez pas modifier sa valeur une fois qu’elle est initialisée ; autrement dit, vous ne pouvez pas lui assigner un nouveau tableau. Toutefois, vous pouvez modifier les valeurs d’un ou plusieurs membres du tableau. Suite à un appel à la procédure `ChangeArrayElement`, le tableau désigné par `characterArray()` contient « x », « M » et « z ».

Notez que cela est semblable à la déclaration d’un paramètre de procédure à [ByVal](byval.md), ce qui empêche la procédure de modifier l’argument appelant lui-même, mais lui permet de modifier ses membres.

## <a name="example"></a>Exemple

L’exemple suivant définit une propriété `ReadOnly` pour la date d’embauche d’un employé. La classe stocke la valeur de propriété en interne en tant que `Private` variable, et seul le code à l’intérieur de la classe peut changer cette valeur. Toutefois, la propriété est `Public`, et tout code qui peut accéder à la classe peut lire la propriété.

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

Le modificateur `ReadOnly` peut être utilisé dans les contextes suivants :

- [Dim (instruction)](../statements/dim-statement.md)
- [Property (instruction)](../statements/property-statement.md)

## <a name="see-also"></a>Voir aussi

- [WriteOnly](writeonly.md)
- [Mots clés](../keywords/index.md)
