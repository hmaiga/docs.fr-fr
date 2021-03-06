---
title: Take, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349647"
---
# <a name="take-clause-visual-basic"></a>Take, clause (Visual Basic)
Retourne un nombre spécifié d'éléments contigus à partir du début d'une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Composants  
 `count`  
 Requis. Valeur ou expression qui prend la valeur du nombre d’éléments de la séquence à retourner.  
  
## <a name="remarks"></a>Notes  
 La clause `Take` amène une requête à inclure un nombre spécifié d’éléments contigus à partir du début d’une liste de résultats. Le nombre d’éléments à inclure est spécifié par le paramètre `count`.  
  
 Vous pouvez utiliser la clause `Take` avec la clause `Skip` pour retourner une plage de données à partir d’un segment d’une requête. Pour ce faire, transmettez l’index du premier élément de la plage à la clause `Skip` et la taille de la plage à la clause `Take`. Dans ce cas, la clause `Take` doit être spécifiée après la clause `Skip`.  
  
 Lorsque vous utilisez la clause `Take` dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui permettra à la clause `Take` d’inclure les résultats souhaités. Pour plus d’informations sur la façon de classer les résultats d’une requête, consultez [clause ORDER BY](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Vous pouvez utiliser la clause `TakeWhile` pour spécifier que seuls certains éléments doivent être retournés, en fonction d’une condition fournie.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise la clause `Take` avec la clause `Skip` pour retourner des données d’une requête dans des pages. La fonction GetCustomers utilise la clause `Skip` pour ignorer les clients de la liste jusqu’à la valeur d’index de départ fournie, et utilise la clause `Take` pour retourner une page de clients à partir de cette valeur d’index.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By (clause)](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While (clause)](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip (clause)](../../../visual-basic/language-reference/queries/skip-clause.md)
