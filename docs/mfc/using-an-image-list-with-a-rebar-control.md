---
title: À l’aide d’une liste d’images avec un contrôle Rebar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f902cb24d5cd8525a99f58fc5feeac416138148
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381743"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Utilisation d'une liste d'images avec un contrôle rebar
Chaque bande rebar peut contenir, entre autres choses, une image à partir d’une liste d’images associée. La procédure suivante détaille les étapes nécessaires pour afficher une image dans une bande rebar.  
  
### <a name="to-display-images-in-a-rebar-band"></a>Pour afficher des images dans une bande rebar  
  
1.  Attachement d’une liste d’images à votre objet de contrôle rebar en effectuant un appel à [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), passant un pointeur vers une liste d’images existant.  
  
2.  Modifier la **REBARBANDINFO** structure pour assigner une image à une bande rebar :  
  
    -   Définir le **cas** membre **RBBIM_IMAGE**, à l’aide de l’opérateur OR au niveau du bit pour inclure des indicateurs supplémentaires si nécessaire.  
  
    -   Définir le `iImage` membre à l’index de liste d’images de l’image à afficher.  
  
3.  Initialiser les membres de données restantes, telles que la taille, le texte et le handle de la fenêtre enfant contenue, avec les informations nécessaires.  
  
4.  Insérez la nouvelle bande (avec l’image) avec un appel à [CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband), en passant le **REBARBANDINFO** structure.  
  
 L’exemple suivant suppose qu’un objet de liste d’images existant avec deux images a été attaché à l’objet de contrôle rebar (`m_wndReBar`). Une nouvelle bande rebar (définie par `rbi`), qui contient la première image, est ajouté par un appel à `InsertBand`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

