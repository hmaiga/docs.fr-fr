---
title: Vue d'ensemble du composant PageSetupDialog
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744342"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>Vue d'ensemble du composant PageSetupDialog (Windows Forms)

Le composant Windows Forms <xref:System.Windows.Forms.PageSetupDialog> est une boîte de dialogue préconfigurée utilisée pour définir les détails de la page d’impression dans les applications Windows. Utilisez-le au sein de votre application Windows comme une solution simple permettant aux utilisateurs de définir des préférences de page plutôt que de configurer votre propre boîte de dialogue. Vous pouvez permettre aux utilisateurs de définir des ajustements de bordure et de marge, des en-têtes et des pieds de page, ainsi que l’orientation portrait ou paysage. En vous appuyant sur des boîtes de dialogue Windows standard, vous pouvez créer des applications dont la fonction de base est immédiatement familière aux utilisateurs.

## <a name="key-properties-and-methods"></a>Propriétés et méthodes de clé

Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l’exécution. Ce composant contient des propriétés que vous pouvez définir en relation avec une seule page (<xref:System.Drawing.Printing.PrintDocument> classe) ou n’importe quel document (classe<xref:System.Drawing.Printing.PageSettings>). En outre, le composant <xref:System.Windows.Forms.PageSetupDialog> peut être utilisé pour déterminer des paramètres d’imprimante spécifiques, qui sont stockés dans la classe <xref:System.Drawing.Printing.PrinterSettings>.

Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.PageSetupDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PageSetupDialog>
- [PageSetupDialog, composant](pagesetupdialog-component-windows-forms.md)
