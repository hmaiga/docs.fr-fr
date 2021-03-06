---
title: Utilisation des mots clés comme noms d'éléments dans le code
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 4cdcda7c5c78481af1633bf29d75070c521ab393
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347393"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Utilisation des mots clés comme noms d'éléments dans le code (Visual Basic)
Tout élément de programme (par exemple, une variable, une classe ou un membre) peut avoir le même nom qu’un mot clé restreint. Par exemple, vous pouvez créer une variable nommée `Loop`. Toutefois, pour faire référence à votre version de celle-ci (qui porte le même nom que le mot clé `Loop` restreint), vous devez la faire précéder d’une chaîne de qualification complète ou la placer entre crochets (`[ ]`), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 Si vous n’effectuez pas l’une de ces opérations, Visual Basic suppose l’utilisation du mot clé `Loop` intrinsèque et génère une erreur, comme dans l’exemple suivant :  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Vous pouvez utiliser des crochets lorsque vous faites référence à des formulaires et des contrôles, et lorsque vous déclarez une variable ou que vous définissez une procédure portant le même nom qu’un mot clé restreint. Il peut être facile d’oublier de qualifier des noms ou d’inclure des crochets, et donc d’introduire des erreurs dans votre code et de le rendre plus difficile à lire. Pour cette raison, nous vous recommandons de ne pas utiliser de mots clés restreints comme noms d’éléments de programme. Toutefois, si une version ultérieure de Visual Basic définit un nouveau mot clé qui est en conflit avec un nom de formulaire ou de contrôle existant, vous pouvez utiliser cette technique lors de la mise à jour de votre code pour utiliser la nouvelle version.  
  
> [!NOTE]
> Votre programme peut également inclure des noms d’éléments fournis par d’autres assemblys référencés. Si ces noms sont en conflit avec des mots clés restreints, si vous placez des crochets autour, les Visual Basic les interprètent comme des éléments définis.  
  
## <a name="see-also"></a>Voir aussi

- [Conventions d’affectation de noms Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
