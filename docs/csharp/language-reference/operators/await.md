---
title: Opérateur await – Informations de référence sur C#
ms.custom: seodec18
ms.date: 08/30/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: c2172f651dd106825680de3195e26f032225a9ab
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169327"
---
# <a name="await-operator-c-reference"></a><span data-ttu-id="69e56-102">Opérateur await (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="69e56-102">await operator (C# reference)</span></span>

<span data-ttu-id="69e56-103">L’opérateur `await` suspend l’évaluation de la méthode [async](../keywords/async.md) englobante jusqu’à ce que l’opération asynchrone représentée par son opérande se termine.</span><span class="sxs-lookup"><span data-stu-id="69e56-103">The `await` operator suspends evaluation of the enclosing [async](../keywords/async.md) method until the asynchronous operation represented by its operand completes.</span></span> <span data-ttu-id="69e56-104">Une fois l’opération asynchrone terminée, l’opérateur `await` retourne le résultat de l’opération, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="69e56-104">When the asynchronous operation completes, the `await` operator returns the result of the operation, if any.</span></span> <span data-ttu-id="69e56-105">Quand l’opérateur `await` est appliqué à l’opérande qui représente l’opération déjà terminée, il retourne immédiatement le résultat de l’opération sans suspendre la méthode englobante.</span><span class="sxs-lookup"><span data-stu-id="69e56-105">When the `await` operator is applied to the operand that represents already completed operation, it returns the result of the operation immediately without suspension of the enclosing method.</span></span> <span data-ttu-id="69e56-106">L’opérateur `await` ne bloque pas le thread qui évalue la méthode async.</span><span class="sxs-lookup"><span data-stu-id="69e56-106">The `await` operator doesn't block the thread that evaluates the async method.</span></span> <span data-ttu-id="69e56-107">Quand l’opérateur `await` suspend la méthode englobante, le contrôle retourne à l’appelant de la méthode.</span><span class="sxs-lookup"><span data-stu-id="69e56-107">When the `await` operator suspends the enclosing method, the control returns to the caller of the method.</span></span>

<span data-ttu-id="69e56-108">Dans l’exemple suivant, la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> retourne l’instance `Task<byte[]>`, qui représente une opération asynchrone qui produit un tableau d’octets au moment où elle se termine.</span><span class="sxs-lookup"><span data-stu-id="69e56-108">In the following example, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> method returns the `Task<byte[]>` instance, which represents an asynchronous operation that produces a byte array when it completes.</span></span> <span data-ttu-id="69e56-109">Tant que l’opération n’est pas terminée, l’opérateur `await` suspend la méthode `DownloadDocsMainPageAsync`.</span><span class="sxs-lookup"><span data-stu-id="69e56-109">Until the operation completes, the `await` operator suspends the `DownloadDocsMainPageAsync` method.</span></span> <span data-ttu-id="69e56-110">Quand la méthode `DownloadDocsMainPageAsync` est suspendue, le contrôle est retourné à la méthode `Main`, qui est l’appelant de `DownloadDocsMainPageAsync`.</span><span class="sxs-lookup"><span data-stu-id="69e56-110">When `DownloadDocsMainPageAsync` gets suspended, control is returned to the `Main` method, which is the caller of `DownloadDocsMainPageAsync`.</span></span> <span data-ttu-id="69e56-111">La méthode `Main` s’exécute jusqu’à ce qu’elle ait besoin du résultat de l’opération asynchrone effectuée par la méthode `DownloadDocsMainPageAsync`.</span><span class="sxs-lookup"><span data-stu-id="69e56-111">The `Main` method executes until it needs the result of the asynchronous operation performed by the `DownloadDocsMainPageAsync` method.</span></span> <span data-ttu-id="69e56-112">Une fois que tous les octets ont été obtenus par <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, le reste de la méthode `DownloadDocsMainPageAsync` est évalué.</span><span class="sxs-lookup"><span data-stu-id="69e56-112">When <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> gets all the bytes, the rest of the `DownloadDocsMainPageAsync` method is evaluated.</span></span> <span data-ttu-id="69e56-113">Après cela, le reste de la méthode `Main` est évalué.</span><span class="sxs-lookup"><span data-stu-id="69e56-113">After that, the rest of the `Main` method is evaluated.</span></span>

[!code-csharp[await example](~/samples/csharp/language-reference/operators/AwaitOperator.cs)]

<span data-ttu-id="69e56-114">L’exemple précédent utilise la [méthode async `Main`](../../programming-guide/main-and-command-args/index.md), ce qui est possible depuis C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="69e56-114">The preceding example uses the [async `Main` method](../../programming-guide/main-and-command-args/index.md), which is possible starting with C# 7.1.</span></span> <span data-ttu-id="69e56-115">Pour plus d’informations, consultez la section [Opérateur await dans la méthode Main](#await-operator-in-the-main-method).</span><span class="sxs-lookup"><span data-stu-id="69e56-115">For more information, see the [await operator in the Main method](#await-operator-in-the-main-method) section.</span></span>

> [!NOTE]
> <span data-ttu-id="69e56-116">Pour obtenir une introduction à la programmation asynchrone, consultez [Programmation asynchrone avec async et await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="69e56-116">For an introduction to asynchronous programming, see [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="69e56-117">La programmation asynchrone avec `async` et `await` suit le [modèle asynchrone basé sur les tâches](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="69e56-117">Asynchronous programming with `async` and `await` follows the [task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

<span data-ttu-id="69e56-118">Vous pouvez utiliser l’opérateur `await` uniquement dans une méthode, une [expression lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ou une [méthode anonyme](delegate-operator.md) modifiée par le mot clé [async](../keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="69e56-118">You can use the `await` operator only in a method, [lambda expression](../../programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](delegate-operator.md) that is modified by the [async](../keywords/async.md) keyword.</span></span> <span data-ttu-id="69e56-119">Dans une méthode async, vous ne pouvez pas utiliser l’opérateur `await` dans le corps d’une fonction synchrone, à l’intérieur du bloc d’une [instruction lock](../keywords/lock-statement.md) et dans un contexte [unsafe](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="69e56-119">Within an async method, you cannot use the `await` operator in the body of a synchronous function, inside the block of a [lock statement](../keywords/lock-statement.md), and in an [unsafe](../keywords/unsafe.md) context.</span></span>
  
<span data-ttu-id="69e56-120">L’opérande de l’opérateur `await` est généralement un des types .NET suivants : <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="69e56-120">The operand of the `await` operator is usually of one of the following .NET types: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="69e56-121">Cependant, n’importe quelle expression awaitable peut être l’opérande de l’opérateur `await`.</span><span class="sxs-lookup"><span data-stu-id="69e56-121">However, any awaitable expression can be the operand of the `await` operator.</span></span> <span data-ttu-id="69e56-122">Pour plus d’informations, consultez la section [Expressions awaitable](~/_csharplang/spec/expressions.md#awaitable-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="69e56-122">For more information, see the [Awaitable expressions](~/_csharplang/spec/expressions.md#awaitable-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="69e56-123">Le type d’expression `await t` est `TResult` si le type d’expression `t` est <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="69e56-123">The type of expression `await t` is `TResult` if the type of expression `t` is <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="69e56-124">Si le type de `t` est <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.ValueTask>, le type de `await t` est `void`.</span><span class="sxs-lookup"><span data-stu-id="69e56-124">If the type of `t` is <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.ValueTask>, the type of `await t` is `void`.</span></span> <span data-ttu-id="69e56-125">Dans les deux cas, si `t` lève une exception, `await t` lève à nouveau l’exception.</span><span class="sxs-lookup"><span data-stu-id="69e56-125">In both cases, if `t` throws an exception, `await t` rethrows the exception.</span></span> <span data-ttu-id="69e56-126">Pour plus d’informations sur le gestion des exceptions, consultez la section [Exceptions dans les méthodes async](../keywords/try-catch.md#exceptions-in-async-methods) de l’article [Instruction try-catch](../keywords/try-catch.md).</span><span class="sxs-lookup"><span data-stu-id="69e56-126">For more information about exception handling, see the [Exceptions in async methods](../keywords/try-catch.md#exceptions-in-async-methods) section of the [try-catch statement](../keywords/try-catch.md) article.</span></span>

<span data-ttu-id="69e56-127">Les mots clés `async` et `await` sont disponibles depuis C# 5.</span><span class="sxs-lookup"><span data-stu-id="69e56-127">The `async` and `await` keywords are available starting with C# 5.</span></span>

## <a name="await-operator-in-the-main-method"></a><span data-ttu-id="69e56-128">Opérateur await dans la méthode Main</span><span class="sxs-lookup"><span data-stu-id="69e56-128">await operator in the Main method</span></span>

<span data-ttu-id="69e56-129">Depuis C# 7.1, la [méthode `Main`](../../programming-guide/main-and-command-args/index.md), qui est le point d’entrée de l’application, peut retourner `Task` ou `Task<int>`, ce qui lui permet d’être asynchrone. Vous pouvez ainsi utiliser l’opérateur `await` dans son corps.</span><span class="sxs-lookup"><span data-stu-id="69e56-129">Starting with C# 7.1, the [`Main` method](../../programming-guide/main-and-command-args/index.md), which is the application entry point, can return `Task` or `Task<int>`, enabling it to be async so you can use the `await` operator in its body.</span></span> <span data-ttu-id="69e56-130">Dans les versions antérieures de C#, pour être certain que la méthode `Main` attend la fin d’une opération asynchrone, vous pouvez récupérer la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> de l’instance <xref:System.Threading.Tasks.Task%601> retournée par la méthode asyn correspondante.</span><span class="sxs-lookup"><span data-stu-id="69e56-130">In earlier C# versions, to ensure that the `Main` method waits for the completion of an asynchronous operation, you can retrieve the value of the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property of the <xref:System.Threading.Tasks.Task%601> instance that is returned by the corresponding async method.</span></span> <span data-ttu-id="69e56-131">Pour les opérations asynchrones qui ne produisent pas de valeur, vous pouvez appeler la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="69e56-131">For asynchronous operations that don't produce a value, you can call the <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="69e56-132">Pour savoir comment sélectionner la version du langage, voir [Sélectionner la version du langage C#](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="69e56-132">For information about how to select the language version, see [Select the C# language version](../configure-language-version.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="69e56-133">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="69e56-133">C# language specification</span></span>

<span data-ttu-id="69e56-134">Pour plus d’informations, consultez la section [Expressions await](~/_csharplang/spec/expressions.md#await-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="69e56-134">For more information, see the [Await expressions](~/_csharplang/spec/expressions.md#await-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="69e56-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69e56-135">See also</span></span>

- [<span data-ttu-id="69e56-136">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="69e56-136">C# reference</span></span>](../index.md)
- [<span data-ttu-id="69e56-137">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="69e56-137">C# operators</span></span>](index.md)
- [<span data-ttu-id="69e56-138">async</span><span class="sxs-lookup"><span data-stu-id="69e56-138">async</span></span>](../keywords/async.md)
- [<span data-ttu-id="69e56-139">Programmation asynchrone avec async et await</span><span class="sxs-lookup"><span data-stu-id="69e56-139">Asynchronous programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="69e56-140">Modèle de programmation asynchrone des tâches</span><span class="sxs-lookup"><span data-stu-id="69e56-140">Task asynchronous programming model</span></span>](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [<span data-ttu-id="69e56-141">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="69e56-141">Asynchronous programming</span></span>](../../async.md)
- [<span data-ttu-id="69e56-142">Modèle asynchrone basé sur les tâches</span><span class="sxs-lookup"><span data-stu-id="69e56-142">Task-based asynchronous pattern</span></span>](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="69e56-143">Async en détail</span><span class="sxs-lookup"><span data-stu-id="69e56-143">Async in depth</span></span>](../../../standard/async-in-depth.md)
- [<span data-ttu-id="69e56-144">Procédure pas à pas : accès au web avec async et await</span><span class="sxs-lookup"><span data-stu-id="69e56-144">Walkthrough: accessing the Web by using async and await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)