---
title: Détermination du type Object
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345201"
---
# <a name="determining-object-type-visual-basic"></a>Détermination du type Object (Visual Basic)
Les variables objets génériques (autrement dit, les variables que vous déclarez comme `Object`) peuvent contenir des objets de n’importe quelle classe. Lorsque vous utilisez des variables de type `Object`, vous devrez peut-être effectuer des actions différentes en fonction de la classe de l’objet. par exemple, certains objets peuvent ne pas prendre en charge une propriété ou une méthode particulière. Visual Basic fournit deux méthodes pour déterminer le type d’objet qui est stocké dans une variable objet : la fonction `TypeName` et l’opérateur `TypeOf...Is`.  
  
## <a name="typename-and-typeofis"></a>TypeName et TypeOf... Non  
 La fonction `TypeName` retourne une chaîne et constitue le meilleur choix lorsque vous avez besoin de stocker ou d’afficher le nom de classe d’un objet, comme indiqué dans le fragment de code suivant :  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 L’opérateur `TypeOf...Is` est le meilleur choix pour tester le type d’un objet, car il est beaucoup plus rapide qu’une comparaison de chaînes équivalente à l’aide de `TypeName`. Le fragment de code suivant utilise `TypeOf...Is` dans une instruction `If...Then...Else` :  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 Un mot de prudence est dû ici. L’opérateur `TypeOf...Is` retourne `True` si un objet est d’un type spécifique ou s’il est dérivé d’un type spécifique. Presque tout ce que vous faites avec Visual Basic implique des objets, qui incluent certains éléments qui ne sont normalement pas considérés comme des objets, tels que les chaînes et les entiers. Ces objets sont dérivés de et héritent des méthodes de <xref:System.Object>. En cas de réussite d’une `Integer` et évaluée avec `Object`, l’opérateur `TypeOf...Is` retourne `True`. L’exemple suivant indique que le paramètre `InParam` est à la fois un `Object` et un `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 L’exemple suivant utilise à la fois `TypeOf...Is` et `TypeName` pour déterminer le type d’objet qui lui est passé dans l’argument `Ctrl`. La procédure `TestObject` appelle `ShowType` avec trois types différents de contrôles.  
  
#### <a name="to-run-the-example"></a>Pour exécuter l'exemple  
  
1. Créez un projet d’application Windows et ajoutez un contrôle de <xref:System.Windows.Forms.Button>, un contrôle <xref:System.Windows.Forms.CheckBox> et un <xref:System.Windows.Forms.RadioButton> contrôle au formulaire.  
  
2. À partir du bouton de votre formulaire, appelez la procédure `TestObject`.  
  
3. Ajoutez le code suivant à votre formulaire :  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Appel d’une propriété ou méthode à l’aide d’un nom de chaîne](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [If...Then...Else (instruction)](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String (type de données)](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer (type de données)](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
