---
title: Where, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 60b7ebe96ce0c4580c36675b2e4aa5f9888732c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349626"
---
# <a name="where-clause-visual-basic"></a>Where, clause (Visual Basic)
Spécifie la condition de filtrage pour une requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Composants  
 `condition`  
 Requis. Expression qui détermine si les valeurs de l’élément actuel dans la collection sont incluses dans la collection de sortie. L’expression doit correspondre à une valeur `Boolean` ou à l’équivalent d’une valeur `Boolean`. Si la condition a la valeur `True`, l’élément est inclus dans le résultat de la requête ; dans le cas contraire, l’élément est exclu du résultat de la requête.  
  
## <a name="remarks"></a>Notes  
 La clause `Where` vous permet de filtrer les données d’une requête en sélectionnant uniquement les éléments qui répondent à certains critères. Les éléments dont les valeurs sont à l’origine de l’évaluation de la clause `Where` `True` sont inclus dans le résultat de la requête ; d’autres éléments sont exclus. L’expression utilisée dans une clause `Where` doit correspondre à une `Boolean` ou à l’équivalent d’un `Boolean`, tel qu’un entier qui prend la valeur `False` lorsque sa valeur est égale à zéro. Vous pouvez combiner plusieurs expressions dans une clause `Where` à l’aide d’opérateurs logiques tels que `And`, `Or`, `AndAlso`, `OrElse`, `Is`et `IsNot`.  
  
 Par défaut, les expressions de requête ne sont pas évaluées jusqu’à ce qu’elles soient accessibles, par exemple quand elles sont liées aux données ou parcourues dans une boucle `For`. Par conséquent, la clause `Where` n’est pas évaluée tant que la requête n’est pas accédée. Si vous avez des valeurs externes à la requête utilisées dans la clause `Where`, assurez-vous que la valeur appropriée est utilisée dans la clause `Where` au moment de l’exécution de la requête. Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Vous pouvez appeler des fonctions dans une clause `Where` pour effectuer un calcul ou une opération sur une valeur de l’élément actuel dans la collection. L’appel d’une fonction dans une clause `Where` peut provoquer l’exécution immédiate de la requête lorsqu’elle est définie au lieu de l’accès. Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `cust` pour chaque objet `Customer` dans la collection `customers`. La clause `Where` utilise la variable de portée pour limiter la sortie aux clients de la région spécifiée. La boucle `For Each` affiche le nom de la société pour chaque client dans le résultat de la requête.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `And` et `Or` opérateurs logiques dans la clause `Where`.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next (instruction)](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
