---
title: À l’aide de listes d’images dans un contrôle de zone de liste déroulante étendue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 080256f9a5de719e265009080036a3c0c2617118
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412234"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Utilisation de listes d'images dans un contrôle de zone de liste déroulante étendue

La principale fonctionnalité des contrôles de zone de liste déroulante étendue est la possibilité d’associer des images à partir d’une liste d’images avec des éléments individuels dans un contrôle de zone de liste déroulante. Chaque élément est en mesure d’afficher trois images différentes : une pour l’état sélectionné, l’autre pour son état désélectionné et une troisième pour une image de superposition.

La procédure suivante associe une liste d’images à un contrôle de zone de liste déroulante étendue :

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Pour associer une liste d’images à un contrôle de zone de liste déroulante étendue

1. Construire une liste d’images (ou utilisez un objet de liste d’images existant), à l’aide de la [CImageList](../mfc/reference/cimagelist-class.md) constructeur et stocker le pointeur résultant.

1. Initialiser le nouvel objet de liste d’images en appelant [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Le code suivant est un exemple de cet appel.

     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. Ajoutez des images facultatives pour chaque état possible : sélectionné ou non sélectionnées et qu’un segment de recouvrement. Le code suivant ajoute trois images prédéfinies.

     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. Associer la liste d’images avec le contrôle avec un appel à [CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).

Une fois que la liste d’images a été associée au contrôle, vous pouvez spécifier individuellement les images de que chaque élément utilisera pour les trois états possibles. Pour plus d’informations, consultez [définition des Images d’un élément individuel](../mfc/setting-the-images-for-an-individual-item.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

