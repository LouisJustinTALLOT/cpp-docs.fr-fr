---
description: 'En savoir plus sur : utilisation d’une liste d’images avec un contrôle rebar'
title: Utilisation d'une liste d'images avec un contrôle rebar
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: ae4aa0259cbe850dbab8ef4bc04277014b39e357
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271796"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Utilisation d'une liste d'images avec un contrôle rebar

Chaque bande rebar peut contenir, entre autres choses, une image d’une liste d’images associée. La procédure suivante détaille les étapes nécessaires à l’affichage d’une image dans une bande rebar.

### <a name="to-display-images-in-a-rebar-band"></a>Pour afficher des images dans une bande rebar

1. Attachez une liste d’images à votre objet de contrôle rebar en effectuant un appel à [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), en passant un pointeur vers une liste d’images existante.

1. Modifiez la structure **REBARBANDINFO** pour assigner une image à une bande rebar :

   - Définissez le membre *fmask* sur `RBBIM_IMAGE` , à l’aide de l’opérateur or au niveau du bit pour inclure des indicateurs supplémentaires si nécessaire.

   - Définissez le membre *IImage* sur l’index de liste d’images de l’image à afficher.

1. Initialisez tous les membres de données restants, tels que la taille, le texte et le handle de la fenêtre enfant à relation contenant-contenu, avec les informations nécessaires.

1. Insérez la nouvelle bande (avec l’image) avec un appel à [CReBarCtrl :: InsertBand](../mfc/reference/crebarctrl-class.md#insertband), en passant la structure **REBARBANDINFO** .

L’exemple suivant suppose qu’un objet de liste d’images existant avec deux images a été attaché à l’objet de contrôle rebar ( `m_wndReBar` ). Une nouvelle bande rebar (définie par `rbi` ), contenant la première image, est ajoutée avec un appel à `InsertBand` :

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
