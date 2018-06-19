---
title: Différences de programmation entre Windows Forms MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ad9e47ba2bb3d9a5e5b21620a4bf4b50177d63b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172669"
---
# <a name="windows-formsmfc-programming-differences"></a>Différences de programmation entre Windows Forms et MFC
Les rubriques de [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) décrivent la prise en charge MFC pour Windows Forms. Si vous n’êtes pas familiarisé avec .NET Framework ou de la programmation MFC, cette rubrique fournit des informations générales sur les différences de programmation entre les deux.  
  
 Windows Forms est pour la création d’applications Microsoft Windows sur le .NET Framework. Cette infrastructure fournit un ensemble de modern, orientée objet, extensible de classes qui vous permettent de développer des applications Windows élaborées. Avec Windows Forms, vous êtes en mesure de créer une application client riche qui peut accéder à un large éventail de sources de données et fournir l’affichage de données et des fonctionnalités d’édition de données à l’aide de contrôles Windows Forms.  
  
 Toutefois, si vous êtes habitué à MFC, vous avez peut-être utilisé à la création de certains types d’applications qui ne sont pas encore explicitement pris en charge dans les Windows Forms. Les applications Windows Forms sont équivalentes aux applications de boîte de dialogue MFC. Toutefois, elles ne fournissent pas de l’infrastructure pour prendre en charge directement d’autres types d’applications MFC comme serveur/conteneur de documents OLE, les documents ActiveX, la prise en charge Document/Vue pour l’interface monodocument (SDI), l’interface multidocument (MDI), et plusieurs interface de niveau supérieur (MTI). Vous pouvez écrire votre propre logique pour créer ces applications.  
  
 Pour plus d’informations sur les applications Windows Forms, consultez [Introduction à Windows Forms](/dotnet/framework/winforms/windows-forms-overview).  
  
 Pour un exemple d’application qui affiche des Windows Forms avec les MFC, consultez [intégration de Windows Forms et MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
 La vue MFC ou document et fonctionnalités de routage des commandes suivantes ont pas d’équivalent dans les Windows Forms :  
  
-   Intégration de l’interpréteur de commandes  
  
     MFC gère les commandes d’exchange (DDE) de données dynamiques et les arguments de ligne de commande par l’interpréteur de commandes lorsqu’un document d’avec le bouton droit et sélectionnez des verbes ouvert, modifier ou imprimer. Windows Forms ne sont pas intégrées de l’interpréteur de commandes et ne répond pas aux verbes du shell.  
  
-   Modèles de document  
  
     Dans MFC, les modèles de document associent une vue, qui est contenue dans une fenêtre frame (en mode MDI, SDI ou MTI), le document ouvert. Il n’y a aucun équivalent aux modèles de document pour Windows Forms.  
  
-   Documents  
  
     MFC inscrit les types de fichier de document et traite le type de document lors de l’ouverture d’un document à partir de l’interpréteur de commandes. Windows Forms n’offre aucune prise en charge du document.  
  
-   États de document  
  
     MFC conserve des états modifiés pour le document. Par conséquent, lorsque vous fermez l’application, fermez la dernière vue qui contient l’application ou quittez Windows, MFC vous invite à enregistrer le document. Windows Forms n’offre aucune prise en charge équivalente.  
  
-   Commandes  
  
     MFC propose le concept de commandes. La barre de menus, la barre d’outils et le menu contextuel peuvent tous appeler la même commande, par exemple, couper et copier. Dans les Windows Forms, les commandes sont des événements étroitement liés à partir d’un élément d’interface utilisateur particulier (par exemple, un élément de menu) ; Par conséquent, vous devez connecter explicitement tous les événements de commande. Vous pouvez également gérer plusieurs événements à un seul gestionnaire dans les Windows Forms. Pour plus d’informations, consultez [connexion de plusieurs événements à un seul gestionnaire d’événements dans les Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).  
  
-   Routage des commandes  
  
     Routage des commandes MFC permet à la vue active ou le document pour traiter les commandes. Étant donné que la même commande a souvent des significations différentes pour des vues différentes (par exemple, copier se comporte différemment dans le texte modifier plutôt que dans un éditeur d’images), les commandes doivent être traitées par la vue active. Barres d’outils et des menus Windows Forms ayant aucune inhérents à la compréhension de la vue active, vous ne pouvez avoir un gestionnaire différent pour chaque type d’affichage pour votre **MenuItem.Click** événements sans écrire de code interne supplémentaire.  
  
-   Mécanisme de mise à jour de commande  
  
     MFC dispose d’une commande de mise à jour. Par conséquent, la vue active ou le document est responsable de l’état des éléments d’interface utilisateur (par exemple, l’activation ou désactivation d’un bouton de menu élément ou l’outil et les états vérifiés). Il n’y a aucun équivalent d’un mécanisme de mise à jour de commande pour Windows Forms.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Procédures pas à pas relatives aux Windows Forms](http://msdn.microsoft.com/en-us/fd44d13d-4733-416f-aefc-32592e59e5d9)