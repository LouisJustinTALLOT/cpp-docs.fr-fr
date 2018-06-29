---
title: Création d’une Application MFC de Style Explorateur de fichiers | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcexplorer.project
dev_langs:
- C++
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a2c3e8e1c7956a5dff33cd8ff78612f5f844ad6
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078419"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>Création d'une application MFC de style Explorateur de fichiers
De nombreuses applications de système de Windows utilisent l’interface utilisateur (IU) de l’Explorateur de fichiers. Lorsque vous démarrez l’Explorateur de fichiers, par exemple, vous consultez une application avec un séparateur vertical de la barre séparant la zone cliente. Fournit des fonctionnalités de navigation et le côté gauche de la zone cliente et à droite de la zone cliente affiche des détails relatifs à la sélection dans le volet gauche. Lorsqu’un utilisateur clique sur un élément dans le volet gauche, l’application remplit à nouveau le volet de droite. Dans une application MDI, vous pouvez utiliser des commandes sur le **vue** menu pour modifier la quantité de détail affiché dans le volet droit. (Dans un SDI ou plusieurs documents de niveau supérieur, vous pouvez modifier le détail en utilisant les boutons de barre d’outils uniquement.)  
  
 Le contenu des volets dépend de l’application. Dans un navigateur de système de fichiers, le volet gauche affiche une vue hiérarchique des répertoires ou des ordinateurs ou des groupes d’ordinateurs, tandis que le volet droit affiche les dossiers, des fichiers individuels, ou les ordinateurs et plus d’informations. Le contenu n’ont pas nécessairement correspondre à des fichiers. Ils peut-être des messages électroniques, des rapports d’erreurs ou des autres éléments dans une base de données.  
  
 L’Assistant crée les classes suivantes pour vous :  
  
-   La `CLeftView` classe définit la partie gauche de la zone cliente. Il est toujours dérivé [CTreeView](../../mfc/reference/ctreeview-class.md).  
  
-   C*NomProj*classe View définit le volet droit de la zone cliente. Par défaut, elle est dérivée de [CListView](../../mfc/reference/clistview-class.md) mais peut être un autre type de vue en fonction de la classe que vous spécifiez à partir de la **classe de Base** liste dans le [Classes générées](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de la Assistant.  
  
 L’application générée peut avoir une interface monodocument (SDI), une interface multidocument (MDI) ou une architecture à plusieurs documents de niveau supérieur. Chaque fenêtre frame que l’application crée est fractionnée à l’aide de [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md). Codage de ce type d’application est semblable au codage d’une application MFC normale qui utilise un séparateur, sauf que ce type d’application dispose les vues de contrôle distincts au sein de chaque volet de fractionnement.  
  
 Si vous utilisez l’affichage de liste par défaut dans le volet droit, l’Assistant crée des choix de menu supplémentaires (dans les applications MDI uniquement) et les boutons de barre d’outils pour basculer le style de vue entre les grandes icônes, petites icônes, liste et les modes de détail.  
  
### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>Pour commencer à créer un fichier exécutable MFC de style Explorateur de fichiers  
  
1.  Suivez les instructions de [création d’une Application MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  Dans l’Assistant Application MFC [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page, sélectionnez le **l’Explorateur de fichiers** style de projet.  
  
3.  Définir d’autres options de que votre choix sur les autres pages de l’Assistant.  
  
4.  Cliquez sur **Terminer** pour générer l’application squelette.  
  
 Pour plus d'informations, voir :  
  
-   [Types multidocuments, vues et fenêtres frame](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Classes d’affichage dérivées](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Choix en matière de conception d’applications](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Création d’une Application MFC de Style navigateur Web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [Création d’une application MFC basée sur les formulaires](../../mfc/reference/creating-a-forms-based-mfc-application.md)

