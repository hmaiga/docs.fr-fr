---
title: Journalisation et suivi-.NET Core
description: Présentation de la journalisation et du suivi de .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 06781c6a5c1d771b1fa772539705cd1e2b3ad2d4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "70234642"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="26bb9-103">Journalisation et suivi .NET Core</span><span class="sxs-lookup"><span data-stu-id="26bb9-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="26bb9-104">La journalisation et le suivi sont en fait deux noms pour la même technique.</span><span class="sxs-lookup"><span data-stu-id="26bb9-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="26bb9-105">La technique simple a été utilisée depuis les premiers jours d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="26bb9-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="26bb9-106">Cela implique simplement l’instrumentation d’une application pour écrire la sortie à consommer ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="26bb9-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="26bb9-107">Raisons pour utiliser la journalisation et le suivi</span><span class="sxs-lookup"><span data-stu-id="26bb9-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="26bb9-108">Cette technique simple est étonnamment puissante.</span><span class="sxs-lookup"><span data-stu-id="26bb9-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="26bb9-109">Il peut être utilisé dans les situations où un débogueur échoue:</span><span class="sxs-lookup"><span data-stu-id="26bb9-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="26bb9-110">Les problèmes survenant sur de longues périodes de temps peuvent être difficiles à déboguer avec un débogueur traditionnel.</span><span class="sxs-lookup"><span data-stu-id="26bb9-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="26bb9-111">Les journaux permettent d’obtenir des informations détaillées sur de longues périodes de temps.</span><span class="sxs-lookup"><span data-stu-id="26bb9-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="26bb9-112">En revanche, les débogueurs sont limités à l’analyse en temps réel.</span><span class="sxs-lookup"><span data-stu-id="26bb9-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="26bb9-113">Les applications multithread et les applications distribuées sont souvent difficiles à déboguer.</span><span class="sxs-lookup"><span data-stu-id="26bb9-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="26bb9-114">L’attachement d’un débogueur tend à modifier les comportements.</span><span class="sxs-lookup"><span data-stu-id="26bb9-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="26bb9-115">Les journaux détaillés peuvent être analysés en fonction des besoins pour comprendre les systèmes complexes.</span><span class="sxs-lookup"><span data-stu-id="26bb9-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="26bb9-116">Les problèmes dans les applications distribuées peuvent provenir d’une interaction complexe entre de nombreux composants et il n’est pas judicieux de connecter un débogueur à chaque partie du système.</span><span class="sxs-lookup"><span data-stu-id="26bb9-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="26bb9-117">De nombreux services ne doivent pas être bloqués.</span><span class="sxs-lookup"><span data-stu-id="26bb9-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="26bb9-118">L’attachement d’un débogueur provoque souvent des échecs de dépassement de délai.</span><span class="sxs-lookup"><span data-stu-id="26bb9-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="26bb9-119">Les problèmes ne sont pas toujours prévus.</span><span class="sxs-lookup"><span data-stu-id="26bb9-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="26bb9-120">La journalisation et le suivi sont conçus pour une faible surcharge, afin que les programmes puissent toujours être enregistrées en cas de problème.</span><span class="sxs-lookup"><span data-stu-id="26bb9-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="26bb9-121">API .NET Core</span><span class="sxs-lookup"><span data-stu-id="26bb9-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="26bb9-122">API de style d’impression</span><span class="sxs-lookup"><span data-stu-id="26bb9-122">Print style APIs</span></span>

<span data-ttu-id="26bb9-123">Les <xref:System.Console?displayProperty=nameWithType>classes <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, et<xref:System.Diagnostics.Debug?displayProperty=nameWithType> fournissent chacune des API de style d’impression similaires pratiques pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="26bb9-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="26bb9-124">Vous avez le choix de l’API de style d’impression à utiliser.</span><span class="sxs-lookup"><span data-stu-id="26bb9-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="26bb9-125">Les principales différences sont les suivantes:</span><span class="sxs-lookup"><span data-stu-id="26bb9-125">The key differences are:</span></span>
- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="26bb9-126">Toujours activé et écrit toujours sur la console.</span><span class="sxs-lookup"><span data-stu-id="26bb9-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="26bb9-127">Utile pour les informations que votre client peut avoir besoin de voir dans la version.</span><span class="sxs-lookup"><span data-stu-id="26bb9-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="26bb9-128">Étant donné qu’il s’agit de l’approche la plus simple, elle est souvent utilisée pour le débogage temporaire ad hoc.</span><span class="sxs-lookup"><span data-stu-id="26bb9-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="26bb9-129">Ce code de débogage n’est souvent jamais archivé dans le contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="26bb9-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="26bb9-130">Activé uniquement lorsque `TRACE` est défini.</span><span class="sxs-lookup"><span data-stu-id="26bb9-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="26bb9-131">Écrit dans attaché <xref:System.Diagnostics.Trace.Listeners>, par <xref:System.Diagnostics.DefaultTraceListener>défaut.</span><span class="sxs-lookup"><span data-stu-id="26bb9-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="26bb9-132">Utilisez cette API lors de la création de journaux qui seront activés dans la plupart des builds.</span><span class="sxs-lookup"><span data-stu-id="26bb9-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="26bb9-133">Activé uniquement lorsque `DEBUG` est défini.</span><span class="sxs-lookup"><span data-stu-id="26bb9-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="26bb9-134">Écrit dans un débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="26bb9-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="26bb9-135">Lors `*nix` de l’écriture dans `COMPlus_DebugWriteToStdErr` stderr si est défini.</span><span class="sxs-lookup"><span data-stu-id="26bb9-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="26bb9-136">Utilisez cette API lors de la création de journaux qui seront activés uniquement dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="26bb9-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="26bb9-137">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="26bb9-137">Logging events</span></span>

<span data-ttu-id="26bb9-138">Les API suivantes sont plus orientées événement.</span><span class="sxs-lookup"><span data-stu-id="26bb9-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="26bb9-139">Au lieu d’enregistrer des chaînes simples, elles consignent des objets d’événement.</span><span class="sxs-lookup"><span data-stu-id="26bb9-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="26bb9-140">EventSource est l’API principale de suivi .NET Core racine.</span><span class="sxs-lookup"><span data-stu-id="26bb9-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="26bb9-141">Disponible dans toutes les versions de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="26bb9-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="26bb9-142">Autorise uniquement le suivi des objets sérialisables.</span><span class="sxs-lookup"><span data-stu-id="26bb9-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="26bb9-143">Écrit dans les [écouteurs d’événements](xref:System.Diagnostics.Tracing.EventListener)attachés.</span><span class="sxs-lookup"><span data-stu-id="26bb9-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="26bb9-144">.NET Core fournit des écouteurs pour:</span><span class="sxs-lookup"><span data-stu-id="26bb9-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="26bb9-145">EventPipe de .NET Core sur toutes les plateformes</span><span class="sxs-lookup"><span data-stu-id="26bb9-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="26bb9-146">Suivi d’v nements pour Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="26bb9-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="26bb9-147">Infrastructure de suivi LTTng pour Linux</span><span class="sxs-lookup"><span data-stu-id="26bb9-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="26bb9-148">Inclus dans .NET Core et en tant que [package NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pour .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="26bb9-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="26bb9-149">Permet le suivi en cours des objets non sérialisables.</span><span class="sxs-lookup"><span data-stu-id="26bb9-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="26bb9-150">Comprend un pont pour permettre l’écriture de champs sélectionnés d’objets journalisés dans <xref:System.Diagnostics.Tracing.EventSource>un.</span><span class="sxs-lookup"><span data-stu-id="26bb9-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="26bb9-151">Fournit un moyen définitif d’identifier les messages du journal qui résultent d’une activité ou d’une transaction spécifique.</span><span class="sxs-lookup"><span data-stu-id="26bb9-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="26bb9-152">Cet objet peut être utilisé pour mettre en corrélation les journaux entre différents services.</span><span class="sxs-lookup"><span data-stu-id="26bb9-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="26bb9-153">Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="26bb9-153">Windows only.</span></span>
  - <span data-ttu-id="26bb9-154">Écrit des messages dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="26bb9-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="26bb9-155">Les administrateurs système attendent que des messages d’erreur d’application irrécupérables s’affichent dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="26bb9-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="26bb9-156">Frameworks ILogger et Logging</span><span class="sxs-lookup"><span data-stu-id="26bb9-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="26bb9-157">Les API de bas niveau ne sont peut-être pas le bon choix pour vos besoins de journalisation.</span><span class="sxs-lookup"><span data-stu-id="26bb9-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="26bb9-158">Vous pouvez envisager d’utiliser un Framework de journalisation.</span><span class="sxs-lookup"><span data-stu-id="26bb9-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="26bb9-159">L' <xref:Microsoft.Extensions.Logging.ILogger> interface a été utilisée pour créer une interface de journalisation commune dans laquelle les enregistreurs d’événements peuvent être insérés via l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="26bb9-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="26bb9-160">Par exemple, pour vous permettre de choisir le meilleur choix pour votre application `ASP.NET` , vous pouvez prendre en charge une sélection de frameworks intégrés et tiers:</span><span class="sxs-lookup"><span data-stu-id="26bb9-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>
- [<span data-ttu-id="26bb9-161">ASP.NET intégrés aux fournisseurs de journalisation</span><span class="sxs-lookup"><span data-stu-id="26bb9-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="26bb9-162">ASP.NET fournisseurs de journalisation tiers</span><span class="sxs-lookup"><span data-stu-id="26bb9-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="26bb9-163">Références associées à la journalisation</span><span class="sxs-lookup"><span data-stu-id="26bb9-163">Logging related references</span></span>

- [<span data-ttu-id="26bb9-164">Guide pratique : effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="26bb9-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="26bb9-165">Guide pratique : Ajouter des instructions de suivi au code d’application</span><span class="sxs-lookup"><span data-stu-id="26bb9-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="26bb9-166">La [journalisation ASP.net](/aspnet/core/fundamentals/logging) fournit une vue d’ensemble des techniques de journalisation qu’elle prend en charge.</span><span class="sxs-lookup"><span data-stu-id="26bb9-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="26bb9-167">L’interpolation de chaîne peut simplifier l’écriture du code de journalisation. [ C# ](../../csharp/language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="26bb9-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="26bb9-168">La <xref:System.Exception.Message?displayProperty=nameWithType> propriété est utile pour la journalisation des exceptions.</span><span class="sxs-lookup"><span data-stu-id="26bb9-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="26bb9-169">La <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe peut être utile pour fournir des informations de pile dans vos journaux.</span><span class="sxs-lookup"><span data-stu-id="26bb9-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="26bb9-170">Considérations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="26bb9-170">Performance considerations</span></span>

<span data-ttu-id="26bb9-171">La mise en forme des chaînes peut prendre un temps de traitement de l’UC notable.</span><span class="sxs-lookup"><span data-stu-id="26bb9-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="26bb9-172">Dans les applications critiques pour les performances, il est recommandé de:</span><span class="sxs-lookup"><span data-stu-id="26bb9-172">In performance critical applications, it's recommended that you:</span></span>
- <span data-ttu-id="26bb9-173">Évitez un grand nombre de journaux quand aucun n’est à l’écoute.</span><span class="sxs-lookup"><span data-stu-id="26bb9-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="26bb9-174">Évitez de créer des messages de journalisation coûteux en vérifiant si la journalisation est activée en premier.</span><span class="sxs-lookup"><span data-stu-id="26bb9-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="26bb9-175">Consignez uniquement ce qui est utile.</span><span class="sxs-lookup"><span data-stu-id="26bb9-175">Only log what's useful.</span></span>
- <span data-ttu-id="26bb9-176">Différer la mise en forme complète à l’étape d’analyse.</span><span class="sxs-lookup"><span data-stu-id="26bb9-176">Defer fancy formatting to the analysis stage.</span></span>