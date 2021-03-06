---
title: Développement d'applications
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186003"
---
# <a name="application-development"></a>Développement d'applications
<a name="introduction"></a>Windows Presentation Foundation (WPF) est un cadre de présentation qui peut être utilisé pour développer les types d’applications suivants :  
  
- Applications autonomes (applications Windows de style traditionnel construites comme des assemblages exécutables qui sont installés et exécutés à partir de l’ordinateur client).  
  
- Applications de navigateur XAML (XBAPs) (applications composées de pages de navigation qui sont construites comme des assemblages exécutables et hébergées par des navigateurs Web tels que Microsoft Internet Explorer ou Mozilla Firefox).  
  
- Bibliothèques de contrôles personnalisés (assemblys non exécutables contenant des contrôles réutilisables).  
  
- Bibliothèques de classes (assemblys non exécutables contenant des classes réutilisables).  
  
> [!NOTE]
> L’utilisation de types WPF dans un service Windows est fortement déconseillée. Si vous tentez d’utiliser ces fonctionnalités dans un service Windows, elles risquent de ne pas fonctionner comme prévu.  
  
 Pour construire cet ensemble d’applications, WPF met en œuvre une foule de services. Cette rubrique fournit une vue d’ensemble de ces services et explique où trouver plus d’informations.  

<a name="Application_Management"></a>
## <a name="application-management"></a>Gestion des applications  
 Les applications WPF exécutables nécessitent généralement un ensemble de fonctionnalités de base qui comprend les éléments suivants :  
  
- Création et gestion de l’infrastructure d’application commune (dont la création d’une méthode de point d’entrée et une boucle de messages Windows pour recevoir les messages système et d’entrée).  
  
- Suivi et interaction avec la durée de vie d’une application.  
  
- Récupération et traitement des paramètres de ligne de commande.  
  
- Partage des propriétés de portée application et des ressources [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
- Détection et traitement des exceptions non gérées.  
  
- Retour de codes de sortie.  
  
- Gestion des fenêtres dans des applications autonomes.  
  
- Suivi de la navigation dans les applications de navigateur XAML (XBAP), et applications autonomes avec fenêtres et cadres de navigation.  
  
 Ces fonctionnalités sont implémentées par la classe <xref:System.Windows.Application> que vous ajoutez à vos applications à l’aide d’une *définition d’application*.  
  
 Pour plus d’informations, consultez [Vue d’ensemble de la gestion d’applications](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a>Fichiers de ressources, de contenu et de données d'une application WPF  
 WPF étend le support de base dans le cadre Microsoft .NET pour les ressources intégrées avec la prise en charge de trois types de fichiers de données non exécutables : les ressources, le contenu et les données. Pour plus d’informations, consultez [Fichiers de ressources, de contenu et de données d’une application WPF](wpf-application-resource-content-and-data-files.md).  
  
 Un élément clé du support pour les fichiers de données sans exécution WPF est la capacité de les identifier et de les charger à l’aide d’une URI unique. Pour plus d’informations, consultez [URI à en-tête pack dans WPF](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a>Fenêtres et boîtes de dialogue  
 Les utilisateurs interagissent avec les applications autonomes WPF à travers les fenêtres. Le rôle d’une fenêtre est d’héberger le contenu d’une application et de présenter les fonctionnalités de l’application qui permettent généralement aux utilisateurs d’interagir avec le contenu. Dans WPF, les fenêtres sont <xref:System.Windows.Window> encapsulées par la classe, qui prend en charge :  
  
- Création et affichage des fenêtres.  
  
- Établissement des relations entre fenêtres parentes et fenêtres enfants.  
  
- Configuration de l’aspect des fenêtres (par exemple taille, emplacement, icônes, texte de barre de titre, bordure).  
  
- Suivi et interaction avec la durée de vie d’une fenêtre.  
  
 Pour plus d’informations, consultez [Vue d’ensemble des fenêtres WPF](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> prend en charge la capacité à créer un type spécial de fenêtre appelé « boîte de dialogue ». Deux types de boîtes de dialogue, modales et non modales, peuvent être créés.  
  
 Pour plus de commodité, et les avantages de la réutilisabilité et une expérience utilisateur <xref:Microsoft.Win32.OpenFileDialog> <xref:Microsoft.Win32.SaveFileDialog>cohérente <xref:System.Windows.Controls.PrintDialog>à travers les applications, WPF expose trois des boîtes de dialogue Windows commune: , et .  
  
 Une boîte de message est un type spécial de boîte de dialogue qui permet d’afficher des informations textuelles importantes aux utilisateurs et de poser des questions simples du type Oui/Non/OK/Annuler. Vous utilisez la classe <xref:System.Windows.MessageBox> pour créer et afficher des boîtes de message.  
  
 Pour plus d’informations, consultez [Vue d’ensemble des boîtes de dialogue](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Navigation  
 WPF prend en charge la<xref:System.Windows.Controls.Page>navigation de style<xref:System.Windows.Documents.Hyperlink>Web à l’aide de pages ( ) et d’hyperliens ( ). La navigation peut être implémentée de diverses manières, notamment :  
  
- Pages autonomes hébergées dans un navigateur web.  
  
- Pages compilées dans un XBAP hébergé dans un navigateur Web.  
  
- Pages compilées dans une application autonome et hébergées par une fenêtre de navigation (<xref:System.Windows.Navigation.NavigationWindow>).  
  
- Pages qui sont hébergées<xref:System.Windows.Controls.Frame>par un cadre ( ), qui peuvent être hébergés dans une page autonome, ou une page compilée dans un XBAP ou une application autonome.  
  
 Pour faciliter la navigation, WPF met en œuvre ce qui suit :  
  
- <xref:System.Windows.Navigation.NavigationService>, le moteur de navigation partagé pour <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow>le traitement des demandes de navigation qui est utilisé par , , et XBAPs pour prendre en charge la navigation intra-application.  
  
- Méthodes de navigation pour lancer la navigation.  
  
- Événements de navigation pour suivre et interagir avec la durée de vie de la navigation.  
  
- Mémorisation de la navigation en avant et en arrière à l’aide d’un journal pouvant également être inspecté et manipulé.  
  
 Pour plus d’informations, consultez [Vue d’ensemble de la navigation](navigation-overview.md).  
  
 WPF prend également en charge un type spécial de navigation connu sous le nom de navigation structurée. La navigation structurée peut être utilisée pour appeler une ou plusieurs pages qui retournent des données de manière structurée et prévisible cohérente avec les appels de fonctions. Cette fonction dépend de la classe <xref:System.Windows.Navigation.PageFunction%601>, décrite plus loin dans [Vue d’ensemble de la navigation structurée](structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601> permet également de simplifier la création de topologies de navigation complexes, décrites dans [Vue d’ensemble des topologies de navigation](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>
## <a name="hosting"></a>Hébergement  
 Les XAP peuvent être hébergés dans Microsoft Internet Explorer ou Firefox. Chaque modèle d’hébergement possède son propre ensemble de considérations et de contraintes qui sont couvertes dans la rubrique [Hébergement d’applications WPF](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a>Génération et déploiement  
 Bien que des applications WPF simples puissent être construites à partir d’une invite de commande à l’aide de compilateurs de lignes de commande, WPF s’intègre à Visual Studio pour fournir un soutien supplémentaire qui a simplifié le processus de développement et de construction. Pour plus d’informations, consultez [Génération d’une application WPF](building-a-wpf-application-wpf.md).  
  
 Selon le type d’application que vous générez, vous avez le choix entre une ou plusieurs options de déploiement. Pour plus d’informations, consultez [Déploiement d’une application WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Vue d’ensemble de la gestion d’applications](application-management-overview.md)|Fournit une vue d’ensemble de la classe <xref:System.Windows.Application>, dont la gestion de la durée de vie de l’application, des fenêtres, des ressources de l’application et de la navigation.|  
|[Fenêtres dans les applications WPF](windows-in-wpf-applications.md)|Fournit des détails sur la gestion des fenêtres dans votre application, notamment la manière d’utiliser la classe <xref:System.Windows.Window> et les boîtes de dialogue.|  
|[Vue d’ensemble de la navigation](navigation-overview.md)|Fournit une vue d’ensemble de la gestion de la navigation entre les pages de votre application.|  
|[Hébergement](hosting-wpf-applications.md)|Fournit un aperçu des applications de navigateur XAML (XBAP).|  
|[Construire et déployer](building-and-deploying-wpf-applications.md)|Décrit comment générer et déployer votre application WPF.|  
|[Présentation de WPF dans Visual Studio 2015](../getting-started/introduction-to-wpf-in-vs.md)|Décrit les principales fonctionnalités de WPF.|  
|[Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Procédure pas à pas qui indique comment créer une application WPF à l’aide de la navigation entre les pages, la disposition, les contrôles, les images, les styles et la liaison.|
