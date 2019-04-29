---
title: Différences de programmation entre Windows Forms et MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: 998485a3384512f57cf35fc264e2321fa0996728
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384450"
---
# <a name="windows-formsmfc-programming-differences"></a>Différences de programmation entre Windows Forms et MFC

Les rubriques de [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) décrivent la prise en charge MFC pour Windows Forms. Si vous n’êtes pas familiarisé avec .NET Framework ou de la programmation MFC, cette rubrique fournit des informations générales sur les différences de programmation entre les deux.

Windows Forms est pour la création d’applications de Microsoft Windows sur le .NET Framework. Cette infrastructure fournit un ensemble modern, orienté objet, extensible de classes qui vous permettent de développer des applications Windows élaborées. Avec Windows Forms, vous êtes en mesure de créer une application client riche qui peut accéder à un large éventail de sources de données et fournir l’affichage de données et des fonctionnalités de modification de données à l’aide de contrôles Windows Forms.

Toutefois, si vous êtes habitué à MFC, vous pouvez servir à la création de certains types d’applications qui ne sont pas encore explicitement pris en charge dans les Windows Forms. Les applications Windows Forms sont équivalentes aux applications de boîte de dialogue MFC. Toutefois, ils ne fournissent pas de l’infrastructure pour prendre en charge directement d’autres types d’applications MFC comme serveur/conteneur de documents OLE, les documents ActiveX, la prise en charge Document/Vue pour l’interface monodocument (SDI), l’interface multidocument (MDI), et plusieurs interface de niveau supérieur (MTI). Vous pouvez écrire votre propre logique pour créer ces applications.

Pour plus d’informations sur les applications Windows Forms, consultez [Introduction à Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

Pour un exemple d’application qui illustre Windows Forms avec MFC, consultez [MFC et l’intégration de formulaires Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

La vue MFC ou document et fonctionnalités de routage des commandes suivantes ont pas d’équivalent dans les Windows Forms :

- Intégration de l’interpréteur de commandes

   MFC gère les commandes d’exchange (DDE) de données dynamiques et les arguments de ligne de commande par l’interpréteur de commandes pour vous avec le bouton droit à un document et sélectionnez des verbes, comme ouvrir, modifiez ou imprimez. Windows Forms n’a aucune interface intégrée et ne répond pas aux verbes du shell.

- Modèles de document

   Dans MFC, les modèles de document associent une vue, qui est contenue dans une fenêtre frame (en mode MDI, SDI ou MTI), le document ouvert. Windows Forms n’a aucun équivalent aux modèles de document.

- Documents

   MFC inscrit les types de fichiers de document et traite le type de document lors de l’ouverture d’un document à partir de l’interpréteur de commandes. Windows Forms n’a aucune prise en charge du document.

- États de document

   MFC gère les états modifiés pour le document. Par conséquent, lorsque vous fermez l’application, fermez la dernière vue qui contient l’application ou de sortie de Windows, MFC vous invite à enregistrer le document. Windows Forms n’a aucune prise en charge équivalente.

- Commandes

   MFC propose le concept de commandes. Le menu contextuel, la barre d’outils et la barre de menus peuvent appeler la même commande, par exemple, couper et copier. Dans les Windows Forms, les commandes sont des événements étroitement liés à partir d’un élément d’interface utilisateur particulier (par exemple, un élément de menu) ; Par conséquent, vous devez raccorder les événements de commande explicitement. Vous pouvez également gérer plusieurs événements avec un gestionnaire unique dans les Windows Forms. Pour plus d’informations, consultez [connexion de plusieurs événements à un seul gestionnaire d’événements dans les Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).

- Routage des commandes

   Routage des commandes MFC permet à la vue active ou le document pour traiter les commandes. Étant donné que la même commande a souvent des significations différentes pour des vues différentes (par exemple, copier se comporte différemment dans le texte modifier plutôt que dans un éditeur graphique), les commandes doivent être traitées par la vue active. Étant donné que les menus Windows Forms et des barres d’outils n’ont aucun une compréhension inhérente de la vue active, vous ne pouvez avoir un gestionnaire différent pour chaque type d’affichage pour votre **MenuItem.Click** événements sans écrire de code interne supplémentaire.

- Mécanisme de mise à jour de commande

   MFC dispose d’une commande de mise à jour. Par conséquent, le document ou la vue active est responsable de l’état des éléments de l’interface utilisateur (par exemple, l’activation ou la désactivation d’un bouton de menu élément ou l’outil et états vérifiés). Windows Forms n’a aucun équivalent d’un mécanisme de mise à jour de commande.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
