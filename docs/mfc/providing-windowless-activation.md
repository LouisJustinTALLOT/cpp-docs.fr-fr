---
title: Mise à disposition de l'activation sans fenêtre
ms.date: 11/04/2016
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
ms.openlocfilehash: 9d60c309d5644c106e6c85a0c7b3988916be7193
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386770"
---
# <a name="providing-windowless-activation"></a>Mise à disposition de l'activation sans fenêtre

Code de création de fenêtre (autrement dit, tout ce qui se produit lorsque vous appelez `CreateWindow`) est coûteux à exécuter. Un contrôle qui gère une fenêtre affichée à l'écran doit gérer les messages de la fenêtre. Les contrôles sans fenêtre sont donc plus rapides que les contrôles avec fenêtre.

Un autre avantage des contrôles sans fenêtre est que, contrairement aux contrôles fenêtrés, ils prennent en charge les zones d'affichage sans teinte non-rectangulaires. Un exemple classique d'un contrôle transparent est un contrôle de texte avec un arrière-plan transparent. Les contrôles peignent le texte mais pas l'arrière-plan, ainsi tout ce qui est sous le texte transparaît. De nouvelles formes utilisent souvent des contrôles non-rectangulaires, tels que les flèches et les boutons arrondis.

Souvent, un contrôle n'a pas besoin d'avoir sa propre fenêtre, mais peut utiliser les services de fenêtre de son conteneur, à condition que le conteneur ait été écrit pour prendre en charge les objets sans fenêtre. Les contrôles sans fenêtre sont à compatibilité descendante avec les conteneurs plus anciens. Dans les conteneurs anciens et non écrits pour prendre en charge les contrôles sans fenêtre, les contrôles sans fenêtre créent une fenêtre lorsqu'ils sont actifs.

Les contrôles sans fenêtre n'ont pas leurs propres fenêtres, le conteneur (qui lui possède une fenêtre) est chargé de fournir des services qui auraient dans tous les cas été fournis par la propre fenêtre du contrôle. Par exemple, si votre contrôle a besoin d'interroger le focus clavier, d'intercepter la souris ou d'obtenir le contexte de périphérique, ces opérations sont gérées par le conteneur. Le conteneur achemine les messages d'entrée utilisateur envoyés dans la fenêtre au contrôle sans fenêtre approprié, à l'aide de l'interface `IOleInPlaceObjectWindowless`. (Consultez le *ActiveX SDK* pour obtenir une description de cette interface.) `COleControl` fonctions membres appellent ces services à partir du conteneur.

Pour rendre votre contrôle à utiliser l’activation sans fenêtre, inclure les **windowlessActivate** indicateur dans le jeu d’indicateurs retournés par [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Exemple :

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

Le code pour inclure cet indicateur est automatiquement généré si vous sélectionnez le **l’activation sans fenêtre** option sur le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page de l’Assistant de contrôle ActiveX MFC.

Lorsque l'activation sans fenêtre est opérationnelle, le conteneur délègue les messages d'entrée à l'interface `IOleInPlaceObjectWindowless` du contrôle. L'implémentation de `COleControl` pour cette interface distribue les messages via la table des messages de votre contrôle, après avoir analysé les coordonnées de la souris correctement. Vous pouvez traiter les messages comme des messages de fenêtre ordinaires, en ajoutant des entrées correspondantes dans la table des messages. Dans les gestionnaires de ces messages, évitez d’utiliser le *m_hWnd* variable membre (ou n’importe quelle fonction membre qui l’utilise) sans vérifier au préalable que sa valeur n’est pas **NULL**.

`COleControl` fournit les fonctions membres qui appellent la capture de la souris, le focus clavier, le défilement et d'autres services de la fenêtre du conteneur selon le cas, notamment :

- [GetFocus](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [GetCapture](../mfc/reference/colecontrol-class.md#getcapture), [SetCapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)

- [GetDC](../mfc/reference/colecontrol-class.md#getdc), [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)

- [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)

- [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)

- [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)

Dans les contrôles sans fenêtre, vous devez toujours utiliser les fonctions membres `COleControl` au lieu des fonctions membres `CWnd` correspondantes ou leurs fonctions API Win32 associées.

Vous pouvez souhaiter qu'un contrôle sans fenêtre soit la cible d'une opération glisser-déplacer OLE. Normalement, cela suppose que la fenêtre de contrôle soit stockée en tant que cible de déplacement. Puisque le contrôle n'a aucune fenêtre qui lui est propre, le conteneur utilise sa propre fenêtre comme cible de déplacement. Le contrôle fournit une implémentation de l'interface de `IDropTarget` à laquelle le conteneur peut déléguer des appels au moment opportun. Pour exposer cette interface au conteneur, vous devez substituer [COleControl::GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget). Exemple :

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : Optimisation](../mfc/mfc-activex-controls-optimization.md)
