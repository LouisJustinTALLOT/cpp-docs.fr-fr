---
description: 'En savoir plus sur : définition des images d’un élément individuel'
title: Définition des images d'un élément individuel
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 12b27b4cdff20690b86fe194dfcc83f958744a86
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217131"
---
# <a name="setting-the-images-for-an-individual-item"></a>Définition des images d'un élément individuel

Les différents types d’images utilisés par l’élément de zone de liste déroulante étendue sont déterminés par les valeurs des membres *IImage*, *iSelectedImage* et *IOverlay* de la structure [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) . Chaque valeur est l’index d’une image dans la liste d’images associée du contrôle. Par défaut, ces membres ont la valeur 0, ce qui amène le contrôle à ne pas afficher d’image pour l’élément. Si vous souhaitez utiliser des images pour un élément spécifique, vous pouvez modifier la structure en conséquence, soit lors de l’insertion de l’élément de zone de liste déroulante, soit en modifiant un élément de zone de liste déroulante existant.

## <a name="setting-the-image-for-a-new-item"></a>Définition de l’image d’un nouvel élément

Si vous insérez un nouvel élément, initialisez les membres de la structure *IImage*, *iSelectedImage* et *IOverlay* avec les valeurs appropriées, puis insérez l’élément avec un appel à [CComboBoxEx :: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).

L’exemple suivant insère un nouvel élément de zone de liste déroulante étendue ( `cbi` ) dans le contrôle de zone de liste déroulante étendue ( `m_comboEx` ), en fournissant des index pour les trois États d’image :

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>Définition de l’image d’un élément existant

Si vous modifiez un élément existant, vous devez utiliser le membre *Mask* d’une structure **COMBOBOXEXITEM** .

#### <a name="to-modify-an-existing-item-to-use-images"></a>Pour modifier un élément existant afin d’utiliser des images

1. Déclarez une structure **COMBOBOXEXITEM** et définissez le membre de données de *masque* sur les valeurs que vous souhaitez modifier.

1. À l’aide de cette structure, effectuez un appel à [CComboBoxEx :: GetItem](../mfc/reference/ccomboboxex-class.md#getitem).

1. Modifiez les membres *Mask*, *IImage* et *iSelectedImage* de la structure récemment retournée, en utilisant les valeurs appropriées.

1. Effectuez un appel à [CComboBoxEx :: SetItem](../mfc/reference/ccomboboxex-class.md#setitem), en passant la structure modifiée.

L’exemple suivant illustre cette procédure en échangeant les images sélectionnées et non sélectionnées du troisième élément de zone de liste déroulante étendue :

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
