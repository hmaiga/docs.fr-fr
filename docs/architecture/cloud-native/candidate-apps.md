---
title: Applications candidates pour le Cloud Native
description: Découvrez les types d’applications qui bénéficient d’une approche Cloud Native
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: a06ecdd9bfb3bd50757c484115eb123862a1bb9e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214005"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="c9360-103">Applications candidates pour le Cloud Native</span><span class="sxs-lookup"><span data-stu-id="c9360-103">Candidate apps for cloud native</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c9360-104">Examinez les applications de votre portefeuille.</span><span class="sxs-lookup"><span data-stu-id="c9360-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="c9360-105">Combien d’entre elles sont éligibles pour une architecture Cloud Native ?</span><span class="sxs-lookup"><span data-stu-id="c9360-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="c9360-106">Tous?</span><span class="sxs-lookup"><span data-stu-id="c9360-106">All of them?</span></span> <span data-ttu-id="c9360-107">Peut-être ?</span><span class="sxs-lookup"><span data-stu-id="c9360-107">Perhaps some?</span></span>

<span data-ttu-id="c9360-108">En appliquant une analyse des coûts/avantages, il y a de bonnes chances que la plupart ne prenne pas en charge la balise Price lourdeur nécessaire pour être Cloud native.</span><span class="sxs-lookup"><span data-stu-id="c9360-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="c9360-109">Le coût du Cloud Native dépasserait beaucoup la valeur métier de l’application.</span><span class="sxs-lookup"><span data-stu-id="c9360-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="c9360-110">Quel type d’application peut être candidat pour le Cloud Native ?</span><span class="sxs-lookup"><span data-stu-id="c9360-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="c9360-111">Un grand système d’entreprise stratégique qui doit faire évoluer constamment les fonctionnalités et fonctionnalités de l’entreprise</span><span class="sxs-lookup"><span data-stu-id="c9360-111">A large, strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="c9360-112">Application nécessitant une rapidité de publication élevée, avec une haute confiance</span><span class="sxs-lookup"><span data-stu-id="c9360-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="c9360-113">Système avec lequel des fonctionnalités individuelles doivent être libérées *sans* redéploiement complet de l’ensemble du système</span><span class="sxs-lookup"><span data-stu-id="c9360-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="c9360-114">Une application développée par les équipes ayant une expertise dans différentes piles technologiques</span><span class="sxs-lookup"><span data-stu-id="c9360-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="c9360-115">Application avec des composants qui doivent être mis à l’échelle indépendamment</span><span class="sxs-lookup"><span data-stu-id="c9360-115">An application with components that must scale independently</span></span>

<span data-ttu-id="c9360-116">Il existe alors des systèmes hérités.</span><span class="sxs-lookup"><span data-stu-id="c9360-116">Then there are legacy systems.</span></span> <span data-ttu-id="c9360-117">Bien que nous aimerions tout pour créer de nouvelles applications, nous sommes souvent responsables de la modernisation des charges de travail héritées qui sont essentielles pour l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="c9360-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="c9360-118">Au fil du temps, une application héritée peut être décomposée en microservices, en conteneur et finalement « replate-forme » dans une architecture Cloud native.</span><span class="sxs-lookup"><span data-stu-id="c9360-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>  

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="c9360-119">Moderniser des applications héritées</span><span class="sxs-lookup"><span data-stu-id="c9360-119">Modernizing legacy apps</span></span>

<span data-ttu-id="c9360-120">Le livre électronique gratuit de Microsoft, [moderniser les applications .NET existantes avec des conteneurs Cloud et Windows Azure](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) fournit des conseils pour la migration des charges de travail locales vers le Cloud.</span><span class="sxs-lookup"><span data-stu-id="c9360-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="c9360-121">La figure 1-8 montre qu’il n’existe pas de stratégie unique, unique et adaptée à la modernisation des applications héritées.</span><span class="sxs-lookup"><span data-stu-id="c9360-121">Figure 1-8 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

<span data-ttu-id="c9360-122">![Stratégies de migration des charges de](./media/strategies-for-migrating-legacy-workloads.png)
travail héritées**figure 1-8**.</span><span class="sxs-lookup"><span data-stu-id="c9360-122">![Strategies for migrating legacy workloads](./media/strategies-for-migrating-legacy-workloads.png)
**Figure 1-8**.</span></span> <span data-ttu-id="c9360-123">Stratégies de migration des charges de travail héritées</span><span class="sxs-lookup"><span data-stu-id="c9360-123">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="c9360-124">Les applications monolithiques non critiques bénéficient en grande partie d’une migration rapide (prête à l'[emploi pour l’infrastructure cloud](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-azure-iaas)).</span><span class="sxs-lookup"><span data-stu-id="c9360-124">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-azure-iaas)) migration.</span></span> <span data-ttu-id="c9360-125">Ici, la charge de travail locale est réhébergée sur une machine virtuelle basée sur le Cloud, sans modification.</span><span class="sxs-lookup"><span data-stu-id="c9360-125">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="c9360-126">Cette approche utilise le [modèle IaaS (infrastructure as a service)](https://azure.microsoft.com/overview/what-is-iaas/).</span><span class="sxs-lookup"><span data-stu-id="c9360-126">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="c9360-127">Azure comprend plusieurs outils tels que ([Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)et [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)) pour faciliter le déplacement.</span><span class="sxs-lookup"><span data-stu-id="c9360-127">Azure includes several tools such as ([Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)) to make such a move easier.</span></span> <span data-ttu-id="c9360-128">Bien que cette stratégie puisse entraîner des économies, ces applications n’ont généralement pas été conçues pour se déverrouiller et tirer parti des avantages de cloud computing.</span><span class="sxs-lookup"><span data-stu-id="c9360-128">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span> 

<span data-ttu-id="c9360-129">Les applications monolithiques qui sont essentielles pour l’entreprise bénéficient souvent d’une migration améliorée avec élévation et décalage (*optimisée*pour le Cloud).</span><span class="sxs-lookup"><span data-stu-id="c9360-129">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="c9360-130">Cette approche comprend des optimisations de déploiement qui activent les services de Cloud Computing clés, sans modifier l’architecture principale de l’application.</span><span class="sxs-lookup"><span data-stu-id="c9360-130">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="c9360-131">Par exemple, vous pouvez créer un [conteneur](https://docs.microsoft.com/virtualization/windowscontainers/about/) pour l’application et la déployer dans un Orchestrator de conteneur, comme [Azure Kubernetes services](https://azure.microsoft.com/services/kubernetes-service/), abordé plus loin dans cet ouvrage.</span><span class="sxs-lookup"><span data-stu-id="c9360-131">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="c9360-132">Une fois dans le Cloud, l’application peut consommer d’autres services Cloud tels que les bases de données, les files d’attente de messages, la surveillance et la mise en cache distribuée.</span><span class="sxs-lookup"><span data-stu-id="c9360-132">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="c9360-133">Enfin, les applications monolithiques qui exécutent des fonctions d’entreprise stratégiques peuvent tirer le meilleur parti d’une approche *Cloud Native* , l’objet de ce livre.</span><span class="sxs-lookup"><span data-stu-id="c9360-133">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="c9360-134">Cette approche offre une agilité et une vélocité.</span><span class="sxs-lookup"><span data-stu-id="c9360-134">This approach provides agility and velocity.</span></span> <span data-ttu-id="c9360-135">Mais il s’agit d’un coût de recréation de plate-forme, de remaniement et de réécriture du code.</span><span class="sxs-lookup"><span data-stu-id="c9360-135">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="c9360-136">Si vous et votre équipe estimez qu’une approche Cloud-native est appropriée, elle vous permet de rationaliser la décision avec votre organisation.</span><span class="sxs-lookup"><span data-stu-id="c9360-136">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="c9360-137">Qu’est-ce qui est exactement le problème de l’entreprise qu’une approche Cloud Native peut résoudre ?</span><span class="sxs-lookup"><span data-stu-id="c9360-137">What exactly is the business problem that a cloud- native approach will solve?</span></span> <span data-ttu-id="c9360-138">Comment l’aligner sur les besoins de l’entreprise ?</span><span class="sxs-lookup"><span data-stu-id="c9360-138">How would it align with business needs?</span></span>

- <span data-ttu-id="c9360-139">Versions rapides des fonctionnalités avec une confiance accrue ?</span><span class="sxs-lookup"><span data-stu-id="c9360-139">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="c9360-140">Évolutivité fine-une utilisation plus efficace des ressources ?</span><span class="sxs-lookup"><span data-stu-id="c9360-140">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="c9360-141">Amélioration de la résilience du système ?</span><span class="sxs-lookup"><span data-stu-id="c9360-141">Improved system resiliency?</span></span>

- <span data-ttu-id="c9360-142">Amélioration des performances du système ?</span><span class="sxs-lookup"><span data-stu-id="c9360-142">Improved system performance?</span></span>

- <span data-ttu-id="c9360-143">Plus de visibilité sur les opérations ?</span><span class="sxs-lookup"><span data-stu-id="c9360-143">More visibility into operations?</span></span>

- <span data-ttu-id="c9360-144">Fusionnez les plateformes de développement et les magasins de données pour obtenir l’outil le mieux adapté à la tâche.</span><span class="sxs-lookup"><span data-stu-id="c9360-144">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="c9360-145">Un investissement d’application durable ?</span><span class="sxs-lookup"><span data-stu-id="c9360-145">Future-proof application investment?</span></span>

<span data-ttu-id="c9360-146">La stratégie de migration appropriée dépend des priorités organisationnelles et des systèmes que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="c9360-146">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="c9360-147">Pour beaucoup, il peut s’avérer plus rentable de Cloud-optimiser une application monolithique ou d’ajouter des services à granularité grossière à une application multiniveau.</span><span class="sxs-lookup"><span data-stu-id="c9360-147">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="c9360-148">Dans ce cas, vous pouvez toujours tirer pleinement parti des fonctionnalités PaaS du Cloud, telles que celles proposées par Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="c9360-148">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="c9360-149">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="c9360-149">Summary</span></span>

<span data-ttu-id="c9360-150">Dans ce chapitre, nous avons introduit l’informatique Native Cloud.</span><span class="sxs-lookup"><span data-stu-id="c9360-150">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="c9360-151">Nous avons fourni une définition avec les fonctionnalités clés qui pilotent une application Cloud native.</span><span class="sxs-lookup"><span data-stu-id="c9360-151">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="c9360-152">Nous avons examiné les types d’applications susceptibles de justifier cet investissement et ce travail.</span><span class="sxs-lookup"><span data-stu-id="c9360-152">We looked the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="c9360-153">Avec l’introduction de, nous nous penchons maintenant sur un examen bien plus détaillé du Cloud native.</span><span class="sxs-lookup"><span data-stu-id="c9360-153">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="c9360-154">Références</span><span class="sxs-lookup"><span data-stu-id="c9360-154">References</span></span>

- [<span data-ttu-id="c9360-155">Base Cloud Native Computing</span><span class="sxs-lookup"><span data-stu-id="c9360-155">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="c9360-156">Microservices .NET : Architecture pour les applications .NET en conteneur</span><span class="sxs-lookup"><span data-stu-id="c9360-156">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="c9360-157">Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure</span><span class="sxs-lookup"><span data-stu-id="c9360-157">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="c9360-158">Modèles natifs Cloud par Cornelia Davis</span><span class="sxs-lookup"><span data-stu-id="c9360-158">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="c9360-159">Au-delà de l’application à 12 facteurs</span><span class="sxs-lookup"><span data-stu-id="c9360-159">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="c9360-160">Qu’est-ce que l’infrastructure en tant que code ?</span><span class="sxs-lookup"><span data-stu-id="c9360-160">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="c9360-161">Micro deploy de l’ingénierie Uber : Déploiement quotidien en toute confiance</span><span class="sxs-lookup"><span data-stu-id="c9360-161">Uber Engineering’s Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="c9360-162">Comment Netflix déploie le code</span><span class="sxs-lookup"><span data-stu-id="c9360-162">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="c9360-163">Contrôle de surcharge pour la mise à l’échelle des microservices WeChat</span><span class="sxs-lookup"><span data-stu-id="c9360-163">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

- [<span data-ttu-id="c9360-164">RayGun-étude de cas</span><span class="sxs-lookup"><span data-stu-id="c9360-164">RayGun - Case Study</span></span>](https://raygun.com/case-study/ovation)

>[!div class="step-by-step"]
><span data-ttu-id="c9360-165">[Précédent](definition.md)
>[Suivant](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="c9360-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>