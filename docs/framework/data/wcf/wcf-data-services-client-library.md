---
title: Bibliothèque client services de données WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 556482e3e43460016162dfbdd9b31f9a68c0af46
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900874"
---
# <a name="wcf-data-services-client-library"></a>Bibliothèque client services de données WCF
Toute application peut interagir avec un service de données basé sur le Open Data Protocol (OData) si elle peut envoyer une requête HTTP et traiter le flux OData retourné par un service de données. Cette interopérabilité vous permet d’accéder à des services OData à partir d’une large gamme d’applications Web. WCF Data Services comprend des bibliothèques clientes qui fournissent une expérience de programmation plus riche lorsque vous consommez des flux OData à partir d’applications .NET Framework ou Silverlight.  
  
 Les deux classes principales de la bibliothèque cliente sont la classe <xref:System.Data.Services.Client.DataServiceContext> et la classe <xref:System.Data.Services.Client.DataServiceQuery%601>. La classe <xref:System.Data.Services.Client.DataServiceContext> encapsule des opérations prises en charge sur un service de données spécifié. Bien que les services OData soient sans État, le contexte ne l’est pas. Par conséquent, vous pouvez utiliser la classe <xref:System.Data.Services.Client.DataServiceContext> pour conserver l’État sur le client entre les interactions avec le service de données afin de prendre en charge des fonctionnalités telles que la gestion des modifications. Cette classe gère également des identités et suit les modifications. La classe <xref:System.Data.Services.Client.DataServiceQuery%601> représente une requête sur un jeu d'entités spécifique.  
  
 Cette section décrit comment utiliser des bibliothèques clientes pour accéder et modifier des données d'une application cliente .NET Framework. Pour plus d’informations sur l’utilisation de la bibliothèque cliente WCF Data Services avec une application Silverlight, consultez [WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v%3dvs.95)). D’autres bibliothèques clientes sont disponibles pour vous permettre de consommer un flux OData dans d’autres types d’applications. Pour plus d’informations sur le kit de développement logiciel (SDK) OData, consultez [exemple de code ODATA SDK](https://www.odata.org/ecosystem/#sdk).
  
## <a name="in-this-section"></a>Dans cette section  
 [Génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md)  
 Décrit comment générer une bibliothèque cliente et des classes de service de données client basées sur des flux OData.  
  
 [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)  
 Décrit comment interroger un service de données depuis une application .NET Framework à l'aide de bibliothèques clientes.  
  
 [Chargement de contenu différé](loading-deferred-content-wcf-data-services.md)  
 Décrit comment charger un contenu supplémentaire non inclus dans la réponse à la requête initiale.  
  
 [Mise à jour du service de données](updating-the-data-service-wcf-data-services.md)  
 Décrit comment créer, modifier et supprimer des entités et des relations à l'aide des bibliothèques clientes.  
  
 [Opérations asynchrones](asynchronous-operations-wcf-data-services.md)  
 Décrit les fonctions fournies par les bibliothèques clientes pour l'utilisation d'un service de données de façon asynchrone.  
  
 [Opérations de traitement par lots](batching-operations-wcf-data-services.md)  
 Décrit comment envoyer plusieurs demandes au service de données dans un lot unique à l'aide des bibliothèques clientes.  
  
 [Liaison de données aux contrôles](binding-data-to-controls-wcf-data-services.md)  
 Décrit comment lier des contrôles à un flux OData retourné par un service de données.  
  
 [Appel des opérations de service](calling-service-operations-wcf-data-services.md)  
 Décrit comment utiliser la bibliothèque cliente pour appeler des opérations de service.  
  
 [Gestion du contexte du service de données](managing-the-data-service-context-wcf-data-services.md)  
 Décrit les options de gestion du comportement de la bibliothèque cliente.  
  
 [Utilisation des données binaires](working-with-binary-data-wcf-data-services.md)  
 Décrit comment accéder à des données binaires retournées par le service de données sous forme de flux de données et les modifier.  
  
## <a name="see-also"></a>Voir aussi

- [Définition de WCF Data Services](defining-wcf-data-services.md)
- [Bien démarrer](getting-started-with-wcf-data-services.md)
