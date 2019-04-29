---
title: Groupes avec onglet MDI
ms.date: 11/04/2016
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
ms.openlocfilehash: 6b68d1bc06a6827ca94b05fa2760206f424d40fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310837"
---
# <a name="mdi-tabbed-groups"></a>Groupes avec onglet MDI

La fonctionnalité des groupes avec onglet interface (multidocument MDI) document multiples permet à plusieurs applications d’interface (multidocument MDI) de document afficher une ou plusieurs fenêtres à onglets (ou des groupes de fenêtres à onglets, appelés *groupes avec onglet*) dans la zone cliente MDI. Les fenêtres avec onglet peuvent être alignées verticalement ou horizontalement. Si une application accueille plusieurs groupes avec onglet MDI, les groupes sont séparés par des séparateurs.

## <a name="features"></a>Fonctionnalités

Les fonctionnalités des groupes avec onglet MDI sont les suivantes :

- Une application peut créer des fenêtres avec onglet dynamiquement.

- Une application peut aligner les fenêtres avec onglet horizontalement ou verticalement.

- Les groupes de fenêtres avec onglet sont séparés par des séparateurs. L'utilisateur peut redimensionner les groupes avec onglet à l'aide du séparateur.

- L'utilisateur peut faire glisser chaque onglet entre les groupes.

- L'utilisateur peut faire glisser chaque onglet pour créer des groupes.

- L'utilisateur peut déplacer des onglets ou créer des groupes à l'aide d'un menu contextuel.

- Une application peut enregistrer et charger la disposition des fenêtres avec onglet.

- Une application peut enregistrer et charger la liste des documents MDI.

- Une application peut accéder à tous les groupes avec onglet et modifier leurs paramètres.

### <a name="using-mdi-tabbed-groups"></a>Utilisation des groupes avec onglet MDI

Voici quelques tâches couramment réalisées à l’aide des groupes avec onglet MDI :

- Pour activer les groupes avec onglet MDI d’une fenêtre frame principale, appelez [CMDIFrameWndEx::EnableMDITabbedGroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups). Le deuxième paramètre de cette méthode est une instance de la classe `CMDITabInfo`. Vous pouvez utiliser les paramètres par défaut ou les modifier avant d'appeler `CMDIFrameWndEx::EnableMDITabbedGroups`.

- Pour modifier les propriétés d'un groupe avec onglet MDI au moment de l'exécution, créez ou modifiez un objet `CMDITabInfo` et appelez de nouveau `CMDIFrameWndEx::EnableMDITabbedGroups`.

- Pour obtenir la liste des fenêtres avec onglet MDI, appelez `CMDIFrameWndEx::GetMDITabGroups`.

- Pour créer un groupe avec onglet MDI en regard d'un groupe avec onglet actif, appelez `CMDIFrameWndEx::MDITabNewGroup`.

- Pour déplacer le focus d'entrée vers la fenêtre précédente ou suivante d'un groupe avec onglet, appelez `CMDIFrameWndEx::MDITabMoveToNextGroup`.

- Pour déterminer si une fenêtre est membre d'un appel de groupe avec onglet MDI `CMDIFrameWndEx::IsMemberOfMDITabGroup`.

- Pour déterminer si les onglets MDI ou les groupes avec onglet MDI sont activés pour une fenêtre frame principale, appelez `CMDIFrameWndEx::AreMDITabs`. Pour déterminer si les groupes avec onglet MDI sont activés, appelez `CMDIFrameWndEx::IsMDITabbedGroup`.

- Pour afficher un menu contextuel lorsque l'utilisateur clique sur un onglet ou le fait glisser vers un autre groupe avec onglet MDI, remplacez `CMDIFrameWndEx::OnShowMDITabContextMenu` dans la classe dérivée `CMDIFrameWndEx`. Si vous n'appliquez pas cette méthode, l'application n'affichera pas le menu contextuel.

- Pour enregistrer la disposition des groupes avec onglet MDI dans une application, appelez `CMDIFrameWndEx::SaveMDIState`. Pour charger un profil de groupe avec onglet MDI déjà enregistré, appelez `CMDIFrameWndEx::LoadMDIState`. Vous pouvez également appeler les méthodes suivantes pour charger ou enregistrer la liste des documents ouverts dans une application MDI. Pour plus d’informations sur l’enregistrement et chargement d’état MDI, consultez [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate).

## <a name="see-also"></a>Voir aussi

[Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)<br/>
[CMDIFrameWndEx, classe](../mfc/reference/cmdiframewndex-class.md)<br/>
[CMDIChildWndEx, classe](../mfc/reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo, classe](../mfc/reference/cmditabinfo-class.md)
