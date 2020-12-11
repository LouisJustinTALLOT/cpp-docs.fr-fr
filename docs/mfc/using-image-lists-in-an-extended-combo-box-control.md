---
description: 'En savoir plus sur : utilisation des listes d’images dans un contrôle de zone de liste déroulante étendue'
title: Utilisation de listes d'images dans un contrôle de zone de liste déroulante étendue
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
ms.openlocfilehash: 9fb4b70f91a8ffc3d0175ec855cd005de10da280
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154368"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Utilisation de listes d'images dans un contrôle de zone de liste déroulante étendue

La principale fonctionnalité des contrôles de zone de liste déroulante étendus est la possibilité d’associer des images à partir d’une liste d’images à des éléments individuels dans un contrôle de zone de liste déroulante. Chaque élément peut afficher trois images différentes : une pour son état sélectionné, une pour son état non sélectionné et une troisième pour une image de superposition.

La procédure suivante associe une liste d’images à un contrôle de zone de liste déroulante étendue :

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Pour associer une liste d’images à un contrôle de zone de liste déroulante étendue

1. Construisez une nouvelle liste d’images (ou utilisez un objet de liste d’images existant) à l’aide du constructeur [CImageList](../mfc/reference/cimagelist-class.md) et en stockant le pointeur résultant.

1. Initialisez le nouvel objet de liste d’images en appelant [CImageList :: Create](../mfc/reference/cimagelist-class.md#create). Le code suivant est un exemple de cet appel.

   [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. Ajoutez des images facultatives pour chaque état possible : sélectionné ou non sélectionné et une superposition. Le code suivant ajoute trois images prédéfinies.

   [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. Associez la liste d’images au contrôle avec un appel à [CComboBoxEx :: SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).

Une fois la liste d’images associée au contrôle, vous pouvez spécifier individuellement les images qui seront utilisées par chaque élément pour les trois États possibles. Pour plus d’informations, consultez [définition des images d’un élément individuel](../mfc/setting-the-images-for-an-individual-item.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
