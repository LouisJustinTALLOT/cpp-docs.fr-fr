---
description: 'En savoir plus sur : contrôles Rebar et bandes'
title: Contrôles rebar et bandes
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
ms.openlocfilehash: 27ada3633a560ad8b5852b05bdd6330a0936fb99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248565"
---
# <a name="rebar-controls-and-bands"></a>Contrôles rebar et bandes

Le principal objectif d’un contrôle rebar est d’agir en tant que conteneur pour les fenêtres enfants, les contrôles de boîte de dialogue communs, les menus, les barres d’outils, etc. Cette relation contenant-contenu est prise en charge par le concept de « Band ». Chaque bande rebar peut contenir n’importe quelle combinaison d’une barre de redimensionnement, d’une image bitmap, d’une étiquette de texte et d’une fenêtre enfant.

`CReBarCtrl`La classe possède de nombreuses fonctions membres que vous pouvez utiliser pour récupérer et manipuler des informations pour une bande rebar spécifique :

- [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount) Récupère le nombre de bandes actuelles dans le contrôle rebar.

- [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo) Initialise une structure **REBARBANDINFO** avec les informations de la bande spécifiée. Il existe une fonction membre [SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo) correspondante.

- [GetRect](../mfc/reference/crebarctrl-class.md#getrect) Récupère le rectangle englobant d’une bande spécifiée.

- [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount) Récupère le nombre de lignes de bande dans un contrôle rebar.

- [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex) Récupère l’index d’une bande spécifiée.

- [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders) Récupère les bordures d’une bande.

En plus de la manipulation, plusieurs fonctions membres sont fournies pour vous permettre de travailler sur des bandes rebar spécifiques.

[InsertBand](../mfc/reference/crebarctrl-class.md#insertband) et [DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband) ajoutent et suppriment des bandes rebar. [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband) et [MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband) affectent la taille actuelle d’une bande rebar spécifique. [MoveBand](../mfc/reference/crebarctrl-class.md#moveband) modifie l’index d’une bande rebar spécifique. [Showband](../mfc/reference/crebarctrl-class.md#showband) affiche ou masque une bande rebar de l’utilisateur.

L’exemple suivant illustre l’ajout d’une bande de barre d’outils (*m_wndToolBar*) à un contrôle rebar existant (*m_wndReBar*). La bande est décrite en initialisant la `rbi` structure, puis en appelant la `InsertBand` fonction membre :

[!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
