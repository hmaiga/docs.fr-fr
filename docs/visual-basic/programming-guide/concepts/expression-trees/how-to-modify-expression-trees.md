---
title: 'Comment : modifier des arborescences d’expression'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 12ccad6df7d6c7d91ebc290163db362eae173209
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353747"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Comment : modifier les arborescences d’expressions (Visual Basic)

Cette rubrique montre comment modifier une arborescence d’expressions. Les arborescences d’expressions sont immuables, ce qui signifie qu’elles ne peuvent pas être modifiées directement. Pour changer une arborescence d’expressions, vous devez créer une copie d’une arborescence d’expressions existante et, quand vous créez la copie, apporter les modifications nécessaires. Vous pouvez utiliser la classe <xref:System.Linq.Expressions.ExpressionVisitor> pour parcourir une arborescence d’expressions existante et copier chaque nœud visité.

## <a name="to-modify-an-expression-tree"></a>Pour modifier une arborescence d’expressions

1. Créez un projet d’**Application console**.

2. Ajoutez une instruction `Imports` au fichier pour l’espace de noms `System.Linq.Expressions`.

3. Ajoutez la classe `AndAlsoModifier` à votre projet.

    ```vb
    Public Class AndAlsoModifier
        Inherits ExpressionVisitor

        Public Function Modify(ByVal expr As Expression) As Expression
            Return Visit(expr)
        End Function

        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression
            If b.NodeType = ExpressionType.AndAlso Then
                Dim left = Me.Visit(b.Left)
                Dim right = Me.Visit(b.Right)

                ' Make this binary expression an OrElse operation instead
                ' of an AndAlso operation.
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _
                                             b.IsLiftedToNull, b.Method)
            End If

            Return MyBase.VisitBinary(b)
        End Function
    End Class
    ```

    Cette classe hérite de la classe <xref:System.Linq.Expressions.ExpressionVisitor> et est spécialisée pour modifier les expressions qui représentent des opérations `AND` conditionnelles. Elle convertit ces opérations d’un `AND` conditionnel en un `OR` conditionnel. Pour ce faire, la classe substitue la méthode <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> du type de base, car les expressions `AND` conditionnelles sont représentées sous forme d’expressions binaires. Dans la méthode `VisitBinary`, si l’expression passée représente une opération `AND` conditionnelle, le code construit une nouvelle expression qui contient l’opérateur `OR` conditionnel au lieu de l’opérateur `AND` conditionnel. Si l’expression passée à `VisitBinary` ne représente pas une opération `AND` conditionnelle, la méthode emploie l’implémentation de classe de base. Les méthodes de classe de base construisent des nœuds qui sont comme les arborescences d’expressions passées, mais les nœuds voient leurs sous-arborescences remplacées par les arborescences d’expressions produites de manière récursive par le visiteur.

4. Ajoutez une instruction `Imports` au fichier pour l’espace de noms `System.Linq.Expressions`.

5. Ajoutez du code à la méthode `Main` dans le fichier Module1. vb pour créer une arborescence d’expressions et la passer à la méthode qui la modifiera.

    ```vb
    Dim expr As Expression(Of Func(Of String, Boolean)) = _
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")

    Console.WriteLine(expr)

    Dim modifier As New AndAlsoModifier()
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))

    Console.WriteLine(modifiedExpr)

    ' This code produces the following output:
    ' name => ((name.Length > 10) && name.StartsWith("G"))
    ' name => ((name.Length > 10) || name.StartsWith("G"))
    ```

    Le code crée une expression qui contient une opération `AND` conditionnelle. Il crée ensuite une instance de la classe `AndAlsoModifier` et passe l’expression à la méthode `Modify` de cette classe. Les arborescences d’expressions d’origine et modifiée sont toutes deux générées pour montrer la modification.

6. Compilez et exécutez l'application.

## <a name="see-also"></a>Voir aussi

- [Comment : exécuter des arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Arborescences d’expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
