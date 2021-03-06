---
title: "Comment : contrôler la disponibilité d'une variable"
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 886b57909cf6ba25dbaceea5c5f06eb4e3ba6f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345392"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Comment : contrôler la disponibilité d'une variable (Visual Basic)
Vous contrôlez la disponibilité d’une variable en spécifiant son *niveau d’accès*. Le niveau d’accès détermine le code qui a l’autorisation de lire ou d’écrire dans la variable.  
  
- Les *variables membres* (définies au niveau du module et en dehors de toute procédure) sont par défaut accessibles au public, ce qui signifie que tout code qui peut les voir peut y accéder. Vous pouvez modifier ce paramétrage en spécifiant un modificateur d’accès.  
  
- Les *variables locales* (définies à l’intérieur d’une procédure) ont un accès public, bien que seul le code au sein de leur procédure puisse y accéder. Vous ne pouvez pas modifier le niveau d’accès d’une variable locale, mais vous pouvez modifier le niveau d’accès de la procédure qui la contient.  
  
 Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Accès privé et public  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Pour rendre une variable accessible uniquement à partir de son module, de sa classe ou de sa structure  
  
1. Placez l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour la variable à l’intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.  
  
2. Incluez le mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md) dans l’instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à partir de n’importe quel endroit dans le module, la classe ou la structure, mais pas en dehors de celle-ci.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Pour rendre une variable accessible à partir de n’importe quel code qui peut la voir  
  
1. Pour une variable membre, placez l’instruction `Dim` pour la variable à l’intérieur d’un module, d’une classe ou d’une structure, mais en dehors d’une procédure.  
  
2. Incluez le mot clé [public](../../../../visual-basic/language-reference/modifiers/public.md) dans l’instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à partir de n’importe quel code qui interagit avec votre assembly.  
  
 -ou-  
  
1. Pour une variable locale, placez l’instruction `Dim` pour la variable à l’intérieur d’une procédure.  
  
2. N’incluez pas le mot clé `Public` dans l’instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à n’importe quel endroit de la procédure, mais pas en dehors de celle-ci.  
  
## <a name="protected-and-friend-access"></a>Accès protégé et ami  
 Vous pouvez limiter le niveau d’accès d’une variable à sa classe et à ses classes dérivées, ou à son assembly. Vous pouvez également spécifier l’Union de ces limitations, qui autorise l’accès à partir du code dans toute classe dérivée ou à tout autre emplacement dans le même assembly. Vous spécifiez cette Union en combinant les mots clés `Protected` et `Friend` dans la même déclaration.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Pour rendre une variable accessible uniquement à partir de sa classe et de toutes les classes dérivées  
  
1. Placez l’instruction `Dim` pour la variable à l’intérieur d’une classe, mais en dehors de toute procédure.  
  
2. Incluez le mot clé [protected](../../../../visual-basic/language-reference/modifiers/protected.md) dans l’instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à n’importe quel endroit de la classe, ainsi qu’à partir d’une classe dérivée de celle-ci, mais pas de l’extérieur d’une classe de la chaîne de dérivation.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Pour rendre une variable accessible uniquement à partir du même assembly  
  
1. Placez l’instruction `Dim` pour la variable à l’intérieur d’un module, d’une classe ou d’une structure, mais en dehors d’une procédure.  
  
2. Incluez le mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) dans l’instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable depuis n’importe quel endroit du module, de la classe ou de la structure, ainsi que depuis n’importe quel code dans le même assembly, mais pas à l’extérieur de l’assembly.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre des déclarations de variables avec des niveaux d’accès `Public`, `Protected`, `Friend`, `Protected Friend`et `Private`. Notez que lorsque l’instruction `Dim` spécifie un niveau d’accès, vous n’avez pas besoin d’inclure le mot clé `Dim`.  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Plus le niveau d’accès d’une variable est restrictif, plus les risques de mauvaise utilisation du code malveillant sont faibles.  
  
## <a name="see-also"></a>Voir aussi

- [Niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
