---
title: Groupes avec onglet MDI | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7cf6420a331d46f2a158c16a30d439f334a46b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350352"
---
# <a name="mdi-tabbed-groups"></a>Groupes avec onglet MDI
La fonctionnalité de groupes avec onglet interface (multidocument MDI) document plusieurs permet à plusieurs applications d’interface (multidocument MDI) de document afficher une ou plusieurs fenêtres à onglets (ou des groupes de fenêtres, appelés *groupes avec onglet*) dans la zone cliente MDI. Les fenêtres avec onglet peuvent être alignées verticalement ou horizontalement. Si une application accueille plusieurs groupes avec onglet MDI, les groupes sont séparés par des séparateurs.  
  
## <a name="features"></a>Fonctionnalités  
 Les fonctionnalités des groupes avec onglet MDI sont les suivantes :  
  
-   Une application peut créer des fenêtres avec onglet dynamiquement.  
  
-   Une application peut aligner les fenêtres avec onglet horizontalement ou verticalement.  
  
-   Les groupes de fenêtres avec onglet sont séparés par des séparateurs. L'utilisateur peut redimensionner les groupes avec onglet à l'aide du séparateur.  
  
-   L'utilisateur peut faire glisser chaque onglet entre les groupes.  
  
-   L'utilisateur peut faire glisser chaque onglet pour créer des groupes.  
  
-   L'utilisateur peut déplacer des onglets ou créer des groupes à l'aide d'un menu contextuel.  
  
-   Une application peut enregistrer et charger la disposition des fenêtres avec onglet.  
  
-   Une application peut enregistrer et charger la liste des documents MDI.  
  
-   Une application peut accéder à tous les groupes avec onglet et modifier leurs paramètres.  
  
### <a name="using-mdi-tabbed-groups"></a>Utilisation des groupes avec onglet MDI  
 Voici quelques tâches couramment réalisées à l’aide des groupes avec onglet MDI :  
  
-   Pour activer les groupes avec onglet MDI pour une fenêtre frame principale, appelez [CMDIFrameWndEx::EnableMDITabbedGroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups). Le deuxième paramètre de cette méthode est une instance de la classe `CMDITabInfo`. Vous pouvez utiliser les paramètres par défaut ou les modifier avant d'appeler `CMDIFrameWndEx::EnableMDITabbedGroups`.  
  
-   Pour modifier les propriétés d'un groupe avec onglet MDI au moment de l'exécution, créez ou modifiez un objet `CMDITabInfo` et appelez de nouveau `CMDIFrameWndEx::EnableMDITabbedGroups`.  
  
-   Pour obtenir la liste des fenêtres avec onglet MDI, appelez `CMDIFrameWndEx::GetMDITabGroups`.  
  
-   Pour créer un groupe avec onglet MDI en regard d'un groupe avec onglet actif, appelez `CMDIFrameWndEx::MDITabNewGroup`.  
  
-   Pour déplacer le focus d'entrée vers la fenêtre précédente ou suivante d'un groupe avec onglet, appelez `CMDIFrameWndEx::MDITabMoveToNextGroup`.  
  
-   Pour déterminer si une fenêtre est membre d'un appel de groupe avec onglet MDI `CMDIFrameWndEx::IsMemberOfMDITabGroup`.  
  
-   Pour déterminer si les onglets MDI ou les groupes avec onglet MDI sont activés pour une fenêtre frame principale, appelez `CMDIFrameWndEx::AreMDITabs`. Pour déterminer si les groupes avec onglet MDI sont activés, appelez `CMDIFrameWndEx::IsMDITabbedGroup`.  
  
-   Pour afficher un menu contextuel lorsque l'utilisateur clique sur un onglet ou le fait glisser vers un autre groupe avec onglet MDI, remplacez `CMDIFrameWndEx::OnShowMDITabContextMenu` dans la classe dérivée `CMDIFrameWndEx`. Si vous n'appliquez pas cette méthode, l'application n'affichera pas le menu contextuel.  
  
-   Pour enregistrer la disposition des groupes avec onglet MDI dans une application, appelez `CMDIFrameWndEx::SaveMDIState`. Pour charger un profil de groupe avec onglet MDI déjà enregistré, appelez `CMDIFrameWndEx::LoadMDIState`. Vous pouvez également appeler les méthodes suivantes pour charger ou enregistrer la liste des documents ouverts dans une application MDI. Pour plus d’informations sur l’enregistrement et chargement d’état MDI, consultez [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate).  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)   
 [Classe CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)   
 [Classe CMDIChildWndEx](../mfc/reference/cmdichildwndex-class.md)   
 [CMDITabInfo, classe](../mfc/reference/cmditabinfo-class.md)
