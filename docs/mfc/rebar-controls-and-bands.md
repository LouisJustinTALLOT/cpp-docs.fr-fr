---
title: Contrôles rebar et bandes
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
ms.openlocfilehash: 4bb7b4aeab1478138aa2b52649f41ca943b5daa4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378158"
---
# <a name="rebar-controls-and-bands"></a>Contrôles rebar et bandes

L’objectif principal d’un contrôle rebar est d’agir en tant que conteneur pour les fenêtres enfants, contrôles de boîte de dialogue commune, menus, barres d’outils et ainsi de suite. Cette relation contenant-contenu est pris en charge par le concept de « bande ». Chaque bande rebar peut contenir n’importe quelle combinaison d’une barre de redimensionnement, une image bitmap, une étiquette de texte et une fenêtre enfant.

Classe `CReBarCtrl` possède de nombreuses fonctions de membre que vous pouvez utiliser pour récupérer et manipuler des informations relatives à une bande rebar spécifique :

- [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount) récupère le nombre de bandes actuellement dans le contrôle rebar.

- [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo) Initialise un **REBARBANDINFO** structure avec des informations à partir de la bande spécifiée. Il existe un correspondant [SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo) fonction membre.

- [GetRect](../mfc/reference/crebarctrl-class.md#getrect) récupère le rectangle englobant d’une bande spécifiée.

- [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount) récupère le nombre de lignes de bandes dans un contrôle rebar.

- [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex) récupère l’index d’une bande spécifiée.

- [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders) récupère les bordures d’une bande.

En plus de la manipulation, plusieurs fonctions membres sont fournies qui permettent de fonctionner sur des bandes rebar spécifique.

[InsertBand](../mfc/reference/crebarctrl-class.md#insertband) et [DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband) ajouter et supprimer des bandes rebar. [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband) et [MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband) affectent la taille actuelle d’une bande rebar spécifique. [MoveBand](../mfc/reference/crebarctrl-class.md#moveband) modifie l’index d’une bande rebar spécifique. [ShowBand](../mfc/reference/crebarctrl-class.md#showband) affiche ou masque une bande rebar à partir de l’utilisateur.

L’exemple suivant illustre l’ajout d’une bande de la barre d’outils (*m_wndToolBar*) à un contrôle rebar existant (*m_wndReBar*). La bande est décrite en initialisant le `rbi` structure, puis en appelant le `InsertBand` fonction membre :

[!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
