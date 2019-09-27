---
title: Vue d’ensemble de gRPC-gRPC pour les développeurs WCF
description: En savoir plus sur l’ensemble de principes guidant le développement de gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b372cc9dcdb2efd605b3d9b688513e4ff8530b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184441"
---
# <a name="grpc-overview"></a><span data-ttu-id="76b91-103">présentation de gRPC</span><span class="sxs-lookup"><span data-stu-id="76b91-103">gRPC overview</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="76b91-104">Après avoir examiné les Genesis de WCF et gRPC dans le dernier chapitre, ce chapitre traite des principales fonctionnalités de gRPC et de la façon dont elles sont comparées à WCF.</span><span class="sxs-lookup"><span data-stu-id="76b91-104">After looking at the genesis of both WCF and gRPC in the last chapter, this chapter will consider some of the key features of gRPC and how they compare to WCF.</span></span>

<span data-ttu-id="76b91-105">ASP.NET Core 3,0 est la première version de ASP.NET qui prend en charge gRPC en mode natif en tant que citoyen de première classe, avec les équipes Microsoft qui contribuent à l’implémentation officielle .NET de gRPC.</span><span class="sxs-lookup"><span data-stu-id="76b91-105">ASP.NET Core 3.0 is the first release of ASP.NET that natively supports gRPC as a first-class citizen, with Microsoft teams contributing to the official .NET implementation of gRPC.</span></span> <span data-ttu-id="76b91-106">Il est recommandé d’utiliser la meilleure approche pour créer des applications distribuées avec .NET, qui peuvent interagir avec tous les autres langages et infrastructures de programmation principaux.</span><span class="sxs-lookup"><span data-stu-id="76b91-106">It's recommended as the best approach for building distributed applications with .NET that can interoperate with all other major programming languages and frameworks.</span></span>

## <a name="key-principles"></a><span data-ttu-id="76b91-107">Principes clés</span><span class="sxs-lookup"><span data-stu-id="76b91-107">Key principles</span></span>

<span data-ttu-id="76b91-108">Comme indiqué dans le chapitre 1, Google souhaitait utiliser l’introduction du protocole HTTP/2 pour retravailler Stubby, son infrastructure RPC interne et à usage général.</span><span class="sxs-lookup"><span data-stu-id="76b91-108">As discussed in chapter 1, Google wanted to use the introduction of HTTP/2 to rework Stubby, its internal, general purpose RPC infrastructure.</span></span> <span data-ttu-id="76b91-109">Stubby, renommé gRPC, peut désormais tirer parti de la normalisation et étendre son applicabilité à l’informatique mobile, au Cloud et aux Internet des objets.</span><span class="sxs-lookup"><span data-stu-id="76b91-109">Stubby, renamed gRPC, now could take advantage of standardization and would extend its applicability to mobile computing, the cloud, and the Internet of Things.</span></span>

<span data-ttu-id="76b91-110">Pour y parvenir, [CNCF (Cloud Native Computing Foundation)](https://www.cncf.io/) a établi un ensemble de principes qui régissent gRPC.</span><span class="sxs-lookup"><span data-stu-id="76b91-110">To achieve this, the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) established a set of principles that would govern gRPC.</span></span> <span data-ttu-id="76b91-111">La liste suivante présente les éléments les plus pertinents, principalement liés à l’optimisation de l’accessibilité et de la convivialité :</span><span class="sxs-lookup"><span data-stu-id="76b91-111">The following list shows the most relevant ones, which are mainly concerned with maximizing accessibility and usability:</span></span>

- <span data-ttu-id="76b91-112">**Gratuit et ouvert** : tous les artefacts doivent être open source avec des licences qui ne contraignent pas les développeurs à adopter gRPC.</span><span class="sxs-lookup"><span data-stu-id="76b91-112">**Free and open** – all artifacts should be open source with licensing that doesn't constrain developers from adopting gRPC.</span></span>
- <span data-ttu-id="76b91-113">**Couverture et simplicité** : gRPC doit être disponible sur toutes les plateformes populaires et être suffisamment simple pour être généré sur n’importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="76b91-113">**Coverage and simplicity** – gRPC should be available across every popular platform and simple enough to build on any platform.</span></span>
- <span data-ttu-id="76b91-114">**Interopérabilité et portée** : il doit être possible d’utiliser gRPC sur n’importe quel réseau, indépendamment de la bande passante ou de la latence, à l’aide de normes réseau largement disponibles.</span><span class="sxs-lookup"><span data-stu-id="76b91-114">**Interoperability and reach** – it should be possible to use gRPC on any network, regardless of bandwidth or latency, using widely available network standards.</span></span>
- <span data-ttu-id="76b91-115">**Usage général et performant** : l’infrastructure doit être utilisable par autant de cas d’utilisation que possible sans compromettre les performances.</span><span class="sxs-lookup"><span data-stu-id="76b91-115">**General purpose and performant** – the framework should be usable by as broad a range of use-cases as possible without compromising performance.</span></span>
- <span data-ttu-id="76b91-116">**Streaming** : le protocole doit fournir une sémantique de diffusion en continu pour les jeux de données volumineux ou la messagerie asynchrone.</span><span class="sxs-lookup"><span data-stu-id="76b91-116">**Streaming** – the protocol should provide streaming semantics for large data-sets or asynchronous messaging.</span></span>
- <span data-ttu-id="76b91-117">**Échange de métadonnées** : le protocole permet aux données non professionnelles, telles que les jetons d’authentification, d’être gérées séparément des données métier réelles.</span><span class="sxs-lookup"><span data-stu-id="76b91-117">**Metadata exchange** – the protocol allow non-business data, such as authentication tokens, to be handled separately from actual business data.</span></span>
- <span data-ttu-id="76b91-118">**Codes d’État normalisés** : la variabilité des codes d’erreur doit être réduite pour que les décisions de gestion des erreurs soient plus claires et, dans le cas où une meilleure gestion des erreurs plus riche est nécessaire, un mécanisme de gestion de ce mécanisme doit être fourni pour gérer ce problème au sein de l’échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="76b91-118">**Standardized status codes** – the variability of error codes should be reduced to make error handling decisions clearer and, where additional richer error handling is required, a mechanism should be provided for managing this within the metadata exchange.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="76b91-119">[Précédent](introduction.md)
>[Suivant](approach.md)</span><span class="sxs-lookup"><span data-stu-id="76b91-119">[Previous](introduction.md)
[Next](approach.md)</span></span>