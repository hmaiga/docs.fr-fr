---
title: Branches et boucles – Tutoriel d’introduction à C#
description: Dans ce tutoriel sur les branches et les boucles, vous allez écrire du code en C# pour explorer la syntaxe du langage qui gère les branches et les boucles conditionnelles permettant d’exécuter des instructions de manière répétée.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396878"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Découvrir la logique conditionnelle avec des instructions de branches et de boucles

Ce tutoriel explique comment écrire du code qui examine des variables et modifie le chemin d’exécution en fonction de ces variables. Vous allez écrire un code en C# et afficher les résultats de la compilation et de l’exécution du code. Ce tutoriel comporte une série de leçons visant à explorer les constructions de type branches et boucles en C#. Ces leçons présentent les concepts de base du langage C#.

Ce tutoriel suppose de disposer d’un ordinateur utilisable pour le développement. Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS. Vous trouverez une brève vue d’ensemble des commandes utilisées dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.

## <a name="make-decisions-using-the-if-statement"></a>Prendre des décisions à l’aide de l’instruction `if`

Créez un répertoire nommé *branches-tutorial*. Créez le répertoire actif et exécutez la commande suivante :

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

Cette commande crée une nouvelle application console .NET Core dans le répertoire actuel.

Ouvrez *Program.cs* dans votre éditeur favori, puis remplacez la ligne `Console.WriteLine("Hello World!");` par le code qui suit :

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Essayez ce code en tapant `dotnet run` dans la fenêtre de console. Le message « La réponse est supérieure à 10 » doit s’afficher dans votre console.

Modifiez la déclaration de `b` pour que la somme soit inférieure à 10 :

```csharp
int b = 3;
```

Tapez `dotnet run` à nouveau. La réponse étant inférieure à 10, rien ne s’affiche. La **condition** que vous testez a une valeur false. Vous n’avez pas de code à exécuter, car vous avez uniquement écrit l’une des branches possibles pour une instruction `if` : la branche true.

> [!TIP]
> Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code. Le compilateur détectera et signalera les erreurs. Observez attentivement la sortie d’erreur et le code ayant généré l’erreur. L’erreur du compilateur peut en général vous aider à trouver le problème.

Le premier exemple montre la puissance de l’instruction `if` et des types booléens. Un *booléen* est une variable qui peut avoir l’une des deux valeurs suivantes : `true` ou `false`. C# définit un type spécial, `bool`, pour les variables booléennes. L’instruction `if` vérifie la valeur d’un `bool`. Quand la valeur est `true`, l’instruction qui suit `if` s’exécute. Dans le cas contraire, elle est ignorée.

Ce processus de vérification des conditions et d’exécution d’instructions en fonction de ces conditions est puissant.

## <a name="make-if-and-else-work-together"></a>Utiliser if et else ensemble

Pour exécuter un code différent dans les branches true et false, vous créez une branche `else` qui s’exécute quand la condition a une valeur false. Essayez ceci. Ajoutez les deux dernières lignes dans le code ci-dessous à votre méthode `Main` (vous devriez déjà avoir les quatre premières lignes) :

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

L’instruction qui suit le mot clé `else` s’exécute uniquement quand la condition testée a une valeur `false`. La combinaison de `if` et `else` avec des conditions booléennes offre les hautes performances dont vous avez besoin pour traiter une condition `true` et une condition `false`.

> [!IMPORTANT]
> La mise en retrait sous les instructions `if` et `else` a simplement pour but de faciliter la lecture.
> Le langage C# ne considère pas la mise en retrait ou les espaces blancs comme des éléments significatifs.
> L’instruction qui suit le mot clé `if` ou `else` sera exécutée en fonction de la condition. Tous les exemples de ce tutoriel suivent une pratique courante qui consiste à mettre en retrait les lignes en fonction du flux de contrôle des instructions.

Étant donné que la mise en retrait n’est pas significative, vous devez utiliser `{` et `}` pour indiquer quand vous souhaitez que plusieurs instructions fassent partie du bloc qui s’exécute de manière conditionnelle. Les programmeurs C# utilisent généralement les accolades pour toutes les clauses `if` et `else`. L’exemple suivant est identique à celui que vous avez créé. Modifiez votre code ci-dessus pour qu’il corresponde au code suivant :

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> Dans le reste de ce didacticiel, tous les exemples de code incluent les accolades, conformément aux pratiques acceptées.

Vous pouvez tester des conditions plus complexes. Ajoutez le code suivant à votre méthode `Main` après le code que vous avez écrit jusque-là :

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

Le symbole `==` teste *l’égalité*. `==` se distingue du test d’égalité d’attribution, que nous avons vu avec `a = 5`.

`&&` représente « et ». Cela signifie que les deux conditions doivent être true pour que l’instruction s’exécute dans la branche true.  Ces exemples montrent également que vous pouvez avoir plusieurs instructions dans chaque branche conditionnelle, à condition de les mettre entre `{` et `}`.

Vous pouvez également utiliser `||` pour représenter « ou ». Ajoutez le code suivant après ce que vous avez écrit jusque-là :

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

Modifiez les valeurs de `a`, `b` et `c` et passez de `&&` à `||` et inversement. Vous comprendrez mieux comment fonctionnent les opérateurs `&&` et `||`.

Vous avez terminé la première étape. Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte. Cela nous permettra de travailler plus facilement avec un nouvel exemple. Renommez votre méthode `Main``ExploreIf` et écrivez une nouvelle méthode `Main` qui appelle `ExploreIf`. Lorsque vous avez terminé, votre code doit ressembler à ceci :

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

Commentez l’appel à `ExploreIf()`. La sortie est ainsi moins encombrée lorsque vous travaillez dans cette section :

```csharp
//ExploreIf();
```

`//` démarre un **commentaire** dans C#. Les commentaires correspondent à du texte que vous voulez conserver dans votre code source sans l’exécuter en tant que code. Le compilateur ne génère pas de code exécutable à partir de commentaires.

## <a name="use-loops-to-repeat-operations"></a>Utiliser des boucles pour répéter des opérations

Dans cette section, vous utilisez des **boucles** pour répéter des instructions. Essayez ce code dans votre méthode `Main` :

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

L’instruction `while` vérifie une condition et exécute l’instruction ou le bloc d’instructions qui suit `while`. Elle répète la vérification de la condition et l’exécution de ces instructions jusqu'à ce que la condition soit false.

Cet exemple contient un nouvel opérateur. `++` après la variable `counter` est l’opérateur d’**incrémentation**. Il ajoute 1 à la valeur de `counter` et stocke cette valeur dans la variable de `counter`.

> [!IMPORTANT]
> Assurez-vous que la condition de boucle `while` devient false quand vous exécutez le code. Dans le cas contraire, vous allez créer une **boucle infinie** dans laquelle votre programme ne se terminera jamais. Ceci n’est pas démontré dans cet exemple, car vous devez forcer la fermeture de votre programme avec **CTRL-C** ou à l’aide d’autres moyens.

La boucle `while` teste la condition avant d’exécuter le code qui suit `while`. La boucle `do` ... `while` exécute d’abord le code, puis vérifie la condition. La boucle *do while* est illustrée dans le code suivant :

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Cette boucle `do` et la boucle antérieure `while` produisent la même sortie.

## <a name="work-with-the-for-loop"></a>Utiliser la boucle for

La boucle **for** est couramment utilisée dans C#. Essayez ce code dans votre méthode Main() :

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Le code précédent effectue le même travail que la `while` boucle et la `do` boucle que vous avez déjà utilisée. L’instruction `for` comprend trois parties qui contrôlent son fonctionnement.

La première partie est l' **initialiseur**: `int index = 0;` déclare qui `index` est la variable de boucle et définit sa valeur initiale sur `0` .

La partie centrale est la **condition for**: `index < 10` déclare que cette `for` boucle continue à s’exécuter tant que la valeur du compteur est inférieure à 10.

La dernière partie est l' **itérateur for**: `index++` spécifie comment modifier la variable de boucle après l’exécution du bloc après l' `for` instruction. Il spécifie ici que `index` doit être incrémenté de 1 chaque fois que le bloc s’exécute.

Expérimentez vous-même. Essayez chacune des variantes suivantes :

- Modifiez l’initialiseur pour définir le démarrage à une valeur différente.
- Modifiez la condition pour définir l’arrêt à une valeur différente.

Une fois terminé, vous allez vous-même écrire des codes pour mettre en pratique ce que vous avez appris.

Il existe une autre instruction de boucle qui n’est pas traitée dans ce didacticiel : l' `foreach` instruction. L' `foreach` instruction répète son instruction pour chaque élément d’une séquence d’éléments. La plupart du temps, elle est utilisée avec les *regroupements*. elle est donc traitée dans le didacticiel suivant.

## <a name="created-nested-loops"></a>Boucles imbriquées créées

Une `while` `do` boucle, ou `for` peut être imbriquée dans une autre boucle pour créer une matrice à l’aide de la combinaison de chaque élément de la boucle externe avec chaque élément de la boucle interne. Nous allons donc créer un ensemble de paires alphanumériques pour représenter les lignes et les colonnes.

Une seule `for` boucle peut générer les lignes :

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

Une autre boucle peut générer les colonnes :

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

Vous pouvez imbriquer une boucle à l’intérieur de l’autre pour former des paires :

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

Vous pouvez voir que la boucle externe incrémente une fois pour chaque exécution complète de la boucle interne. Inversez l’imbrication de lignes et de colonnes et observez les modifications pour vous-même.

## <a name="combine-branches-and-loops"></a>Combiner des branches et des boucles

Maintenant que vous avez vu l’instruction `if` et la création de boucles en langage C#, vérifiez si vous pouvez écrire un code C# pour obtenir la somme de tous les entiers de 1 à 20 divisibles par 3.  Voici quelques conseils :

- L’opérateur `%` vous donne le reste d’une opération de division.
- L’instruction `if` vous donne la condition pour vérifier si un nombre doit être inclus dans la somme.
- La boucle `for` peut vous aider à répéter une série d’étapes pour tous les nombres de 1 à 20.

Essayez par vous-même et vérifiez le résultat. Vous devriez obtenir 63 comme réponse. Vous pouvez voir une réponse possible en [consultant le code terminé sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

Vous avez terminé le didacticiel « Branches et boucles ».

Vous pouvez passer au tutoriel [Tableaux et collections](arrays-and-collections.md) dans votre propre environnement de développement.

Pour plus d’informations sur ces concepts, consultez les articles suivants :

- [Instruction if et else](../../language-reference/keywords/if-else.md)
- [While (instruction)](../../language-reference/keywords/while.md)
- [Instruction do](../../language-reference/keywords/do.md)
- [Instruction for](../../language-reference/keywords/for.md)
