---
title: Windows Forms-différences de programmation MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: 165c72b4f91073947d3914ae773e277cce192564
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "70311904"
---
# <a name="windows-formsmfc-programming-differences"></a>Différences de programmation entre Windows Forms et MFC

Les rubriques de [l’utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) décrivent la prise en charge MFC pour Windows Forms. Si vous n’êtes pas familiarisé avec la programmation .NET Framework ou MFC, cette rubrique fournit des informations générales sur les différences de programmation entre les deux.

Windows Forms concerne la création d’applications Microsoft Windows sur le .NET Framework. Ce Framework fournit un ensemble de classes extensible, orienté objet et moderne, qui vous permettent de développer des applications Windows riches. Avec Windows Forms, vous pouvez créer une application client riche qui peut accéder à une grande variété de sources de données et fournir des fonctionnalités d’affichage et de modification des données à l’aide de Windows Forms contrôles.

Toutefois, si vous êtes habitué aux MFC, vous pouvez utiliser pour créer certains types d’applications qui ne sont pas encore explicitement prises en charge dans Windows Forms. Les applications de Windows Forms sont équivalentes aux applications de boîte de dialogue MFC. Toutefois, ils ne fournissent pas l’infrastructure permettant de prendre directement en charge d’autres types d’applications MFC tels que le serveur de documents/conteneur OLE, les documents ActiveX, la prise en charge de document/vue pour l’interface SDI (single-document interface), l’interface multidocument (MDI, multiple-document interface) et interface de niveau supérieur multiple (MTI). Vous pouvez écrire votre propre logique pour créer ces applications.

Pour plus d’informations sur les applications Windows Forms, consultez [Introduction à la Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

Pour obtenir un exemple d’application qui montre Windows Forms utilisé avec MFC, consultez [MFC and Windows Forms Integration](https://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

La vue MFC ou les fonctionnalités de routage de documents et de commandes suivantes n’ont pas d’équivalents dans Windows Forms :

- Intégration de Shell

   MFC gère les commandes DDE (Dynamic Data Exchange) et les arguments de ligne de commande que l’interpréteur de commandes utilise lorsque vous cliquez avec le bouton droit sur un document et que vous sélectionnez ces verbes comme ouvrir, modifier ou imprimer. Windows Forms n’a pas d’intégration de Shell et ne répond pas aux verbes de Shell.

- Modèles de document

   Dans MFC, les modèles de document associent une vue, contenue dans une fenêtre frame (en mode MDI, SDI ou MTI), au document que vous avez ouvert. Windows Forms n’a pas d’équivalent aux modèles de document.

- Documents

   MFC inscrit les types de fichiers de document et traite le type de document lors de l’ouverture d’un document à partir de l’interpréteur de commandes. Windows Forms n’a pas de prise en charge de document.

- États du document

   MFC conserve les États de modification du document. Par conséquent, lorsque vous fermez l’application, que vous fermez la dernière vue qui contient l’application, ou que vous quittez à partir de Windows, MFC vous invite à enregistrer le document. Windows Forms n’a pas de prise en charge équivalente.

- Commandes

   MFC présente le concept de commandes. La barre de menus, la barre d’outils et le menu contextuel peuvent tous appeler la même commande, par exemple couper et copier. Dans Windows Forms, les commandes sont des événements étroitement liés à partir d’un élément d’interface utilisateur particulier (tel qu’un élément de menu); par conséquent, vous devez raccorder explicitement tous les événements de commande. Vous pouvez également gérer plusieurs événements avec un seul gestionnaire dans Windows Forms. Pour plus d’informations, consultez [connexion de plusieurs événements à un même gestionnaire d’événements dans Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).

- Routage des commandes

   Le routage des commandes MFC permet à la vue active ou au document de traiter des commandes. Étant donné que la même commande a souvent des significations différentes pour différents affichages (par exemple, la fonction Copy se comporte différemment en mode édition de texte que dans un éditeur Graphics), les commandes doivent être gérées par la vue active. Étant donné que les menus et les barres d’outils de Windows Forms n’ont aucune compréhension inhérente de la vue active, vous ne pouvez pas avoir un gestionnaire différent pour chaque type d’affichage pour vos événements **MenuItem. Click** sans écrire de code interne supplémentaire.

- Mécanisme de mise à jour de commande

   MFC possède un mécanisme de mise à jour de commande. Par conséquent, la vue ou le document actif est responsable de l’état des éléments d’interface utilisateur (par exemple, l’activation ou la désactivation d’un élément de menu ou d’un bouton d’outil et les États activés). Windows Forms n’a pas d’équivalent d’un mécanisme de mise à jour de commande.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
