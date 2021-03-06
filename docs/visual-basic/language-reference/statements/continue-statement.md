---
title: Continue, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354111"
---
# <a name="continue-statement-visual-basic"></a>Continue, instruction (Visual Basic)
Transfère immédiatement le contrôle à l’itération suivante d’une boucle.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez transférer de l’intérieur d’une boucle `Do`, `For`ou `While` à l’itération suivante de cette boucle. Le contrôle est immédiatement passé au test de condition de boucle, ce qui équivaut à transférer vers l’instruction `For` ou `While`, ou à l’instruction `Do` ou `Loop` qui contient la clause `Until` ou `While`.  
  
 Vous pouvez utiliser `Continue` à n’importe quel emplacement de la boucle qui autorise les transferts. Les règles autorisant le transfert de contrôle sont les mêmes que celles de l' [instruction goto](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Par exemple, si une boucle est entièrement contenue dans un bloc `Try`, un bloc `Catch` ou un bloc `Finally`, vous pouvez utiliser `Continue` pour transférer la boucle. Si, en revanche, la structure `Try`...`End Try` est contenue dans la boucle, vous ne pouvez pas utiliser `Continue` pour transférer le contrôle hors du bloc `Finally`, et vous pouvez l’utiliser pour transférer un bloc `Try` ou `Catch` uniquement si vous transférez complètement en dehors de la structure `Try`...`End Try`.  
  
 Si vous disposez de boucles imbriquées du même type, par exemple une boucle `Do` dans une autre boucle `Do`, une instruction `Continue Do` passe à l’itération suivante de la boucle `Do` la plus profonde qui la contient. Vous ne pouvez pas utiliser `Continue` pour passer à l’itération suivante d’une boucle conteneur du même type.  
  
 Si vous avez des boucles imbriquées de types différents, par exemple une boucle `Do` dans une boucle `For`, vous pouvez passer à l’itération suivante de l’une ou l’autre boucle à l’aide de `Continue Do` ou `Continue For`.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise l’instruction `Continue While` pour passer à la colonne suivante d’un tableau si un diviseur est égal à zéro. La `Continue While` est à l’intérieur d’une boucle `For`. Elle est transférée à l’instruction `While col < lastcol`, qui est l’itération suivante de la boucle `While` la plus profonde qui contient la boucle `For`.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Voir aussi

- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
