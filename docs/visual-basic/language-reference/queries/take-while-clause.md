---
title: Take While, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347110"
---
# <a name="take-while-clause-visual-basic"></a>Take While, clause (Visual Basic)
Inclut les éléments d’une collection tant qu’une condition spécifiée a la valeur `true` et ignore les éléments restants.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`expression`|Requis. Expression qui représente une condition pour laquelle tester des éléments. L’expression doit retourner une valeur `Boolean` ou un équivalent fonctionnel, tel qu’un `Integer` à évaluer en tant que `Boolean`.|  
  
## <a name="remarks"></a>Notes  
 La clause `Take While` comprend des éléments à partir du début d’un résultat de requête jusqu’à ce que le `expression` fourni retourne `false`. Une fois que le `expression` a retourné `false`, la requête contourne tous les éléments restants. La `expression` est ignorée pour les résultats restants.  
  
 La clause `Take While` diffère de la clause `Where` dans la mesure où la clause `Where` peut être utilisée pour inclure tous les éléments d’une requête qui remplissent une condition particulière. La clause `Take While` comprend uniquement des éléments jusqu’à la première fois que la condition n’est pas satisfaite. La clause `Take While` est très utile lorsque vous travaillez avec un résultat de requête ordonné.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise la clause `Take While` pour récupérer les résultats jusqu’à ce que le premier client sans ordre soit trouvé.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take (clause)](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While (clause)](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
