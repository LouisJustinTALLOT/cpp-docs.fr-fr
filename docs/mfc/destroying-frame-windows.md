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
ms.openlocfilehash: 20eefa2be6d0e0df4585834bae5c37cd258610a7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214137"
---
# <a name="destroying-frame-windows"></a>Destruction des fenêtres frame

L’infrastructure MFC gère la destruction des fenêtres ainsi que la création des fenêtres associées aux documents et aux vues de l’infrastructure. Si vous créez des fenêtres supplémentaires, vous êtes chargé de les détruire.

Dans l’infrastructure, lorsque l’utilisateur ferme la fenêtre frame, le gestionnaire [OnClose](reference/cwnd-class.md#onclose) par défaut de la fenêtre appelle [DestroyWindow](reference/cwnd-class.md#destroywindow). La dernière fonction membre appelée lorsque la fenêtre Windows est détruite est [OnNcDestroy](reference/cwnd-class.md#onncdestroy), qui effectue un nettoyage, appelle la fonction membre [par défaut](reference/cwnd-class.md#default) pour effectuer le nettoyage de Windows et enfin appelle la fonction membre virtuelle [PostNcDestroy](reference/cwnd-class.md#postncdestroy). L’implémentation [CFrameWnd](reference/cframewnd-class.md) de `PostNcDestroy` supprime l’objet fenêtre C++. Vous ne devez jamais utiliser l' **`delete`** opérateur C++ dans une fenêtre frame. Utilisez `DestroyWindow` à la place.

À la fermeture de la fenêtre principale, l’application se ferme. Si des documents non enregistrés sont modifiés, l’infrastructure affiche une boîte de message qui vous demande si les documents doivent être enregistrés et s’assure que les documents appropriés sont enregistrés si nécessaire.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres d’image de document](creating-document-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](using-frame-windows.md)
