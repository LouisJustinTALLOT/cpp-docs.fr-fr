---
title: Utilisation d'une liste d'images avec un contrôle rebar
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: 3cf359a5d06396f9c2c31cbec511c04784053e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641432"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Utilisation d'une liste d'images avec un contrôle rebar

Chaque bande rebar peut contenir, entre autres choses, une image à partir d’une liste d’images associée. La procédure suivante décrit en détail les étapes nécessaires pour afficher une image dans une bande rebar.

### <a name="to-display-images-in-a-rebar-band"></a>Pour afficher des images dans une bande rebar

1. Attacher une liste d’images à votre objet de contrôle rebar en effectuant un appel à [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), passant un pointeur vers une liste d’images existant.

1. Modifier le **REBARBANDINFO** structure pour affecter une image à une bande rebar :

   - Définir le *cas* membre à `RBBIM_IMAGE`, à l’aide de l’opérateur OR au niveau du bit pour inclure des indicateurs supplémentaires en fonction des besoins.

   - Définir le *iImage* membre à l’index de liste d’image de l’image à afficher.

1. Initialiser aucun membre de données restantes, telles que la taille, le texte et le handle de la fenêtre de la relation contenant-contenu enfant, avec les informations nécessaires.

1. Insérer la nouvelle bande (avec l’image) avec un appel à [CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband), en passant le **REBARBANDINFO** structure.

L’exemple suivant suppose qu’un objet de liste d’images existant avec deux images a été attaché à l’objet de contrôle rebar (`m_wndReBar`). Une bande rebar (définie par `rbi`), contenant la première image, est ajouté avec un appel à `InsertBand`:

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

