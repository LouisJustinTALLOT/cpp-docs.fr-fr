---
title: Détruire des fenêtres Frame | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81182c0e5633e19126d3036b5793de7658ad3d2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343474"
---
# <a name="destroying-frame-windows"></a>Destruction des fenêtres frame
L’infrastructure MFC gère la destruction des fenêtres ainsi que la création des fenêtres associées avec des vues et des documents de framework. Si vous créez des fenêtres supplémentaires, vous êtes responsable de leur destruction.  
  
 Dans le framework, lorsque l’utilisateur ferme la fenêtre frame, la valeur par défaut de la fenêtre [OnClose](../mfc/reference/cwnd-class.md#onclose) appels du Gestionnaire de [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La dernière fonction membre appelée lorsque la fenêtre Windows est détruite est [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), qui procède au nettoyage, appelle le [par défaut](../mfc/reference/cwnd-class.md#default) membre de la fonction pour effectuer un nettoyage de Windows et enfin appelle la fonction membre virtuelle [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). Le [CFrameWnd](../mfc/reference/cframewnd-class.md) implémentation de `PostNcDestroy` supprime l’objet fenêtre C++. Vous ne devez jamais utiliser C++ **supprimer** opérateur sur une fenêtre frame. Utilisez plutôt `DestroyWindow`.  
  
 La fermeture de la fenêtre principale, l’application se ferme. S’il sont modifiés des documents non enregistrés, l’infrastructure affiche une boîte de message pour demander si les documents doivent être enregistrés et permet de s’assurer que les documents appropriés sont enregistrés si nécessaire.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

