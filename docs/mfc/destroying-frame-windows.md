---
title: Destruction des fenêtres frame
ms.date: 11/04/2016
f1_keywords:
- PostNcDestroy
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
ms.openlocfilehash: b64298bd2b0f14c30c824d78947a17628adec8b5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258201"
---
# <a name="destroying-frame-windows"></a>Destruction des fenêtres frame

L’infrastructure MFC gère la destruction de fenêtres, ainsi que la création de ces fenêtres associées aux vues et les documents de framework. Si vous créez des fenêtres supplémentaires, vous êtes responsable de leur destruction.

Dans le framework, lorsque l’utilisateur ferme la fenêtre frame, la valeur par défaut de la fenêtre [OnClose](../mfc/reference/cwnd-class.md#onclose) appels du gestionnaire [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). Est la dernière fonction membre appelée lorsque la fenêtre Windows est détruite [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), qui effectue un nettoyage, appelle le [par défaut](../mfc/reference/cwnd-class.md#default) membre de fonction pour effectuer un nettoyage de Windows et enfin appelle la fonction membre virtuelle [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). Le [CFrameWnd](../mfc/reference/cframewnd-class.md) implémentation de `PostNcDestroy` supprime l’objet fenêtre C++. Vous ne devez jamais utiliser le C++ **supprimer** opérateur sur une fenêtre frame. Utilisez plutôt `DestroyWindow`.

Lorsque la fenêtre principale est fermée, l’application se ferme. S’il sont modifiés des documents non enregistrés, l’infrastructure affiche une boîte de message pour demander si les documents doivent être enregistrées et garantit que les documents appropriés sont enregistrés si nécessaire.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de fenêtres frame](../mfc/using-frame-windows.md)
