---
description: 'En savoir plus sur : destruction des fenêtres Frame'
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
ms.openlocfilehash: 192b1b21881f4a9f94a4fb1d6c7b18b4a91ac579
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327856"
---
# <a name="destroying-frame-windows"></a>Destruction des fenêtres frame

L’infrastructure MFC gère la destruction des fenêtres ainsi que la création des fenêtres associées aux documents et aux vues de l’infrastructure. Si vous créez des fenêtres supplémentaires, vous êtes chargé de les détruire.

Dans l’infrastructure, lorsque l’utilisateur ferme la fenêtre frame, le gestionnaire [OnClose](reference/cwnd-class.md#onclose) par défaut de la fenêtre appelle [DestroyWindow](reference/cwnd-class.md#destroywindow). La dernière fonction membre appelée lorsque la fenêtre Windows est détruite est [OnNcDestroy](reference/cwnd-class.md#onncdestroy), qui effectue un nettoyage, appelle la fonction membre [par défaut](reference/cwnd-class.md#default) pour effectuer le nettoyage de Windows et enfin appelle la fonction membre virtuelle [PostNcDestroy](reference/cwnd-class.md#postncdestroy). L’implémentation [CFrameWnd](reference/cframewnd-class.md) de `PostNcDestroy` supprime l’objet fenêtre C++. Vous ne devez jamais utiliser l' **`delete`** opérateur C++ dans une fenêtre frame. Utilisez `DestroyWindow` à la place.

À la fermeture de la fenêtre principale, l’application se ferme. Si des documents non enregistrés sont modifiés, l’infrastructure affiche une boîte de message qui vous demande si les documents doivent être enregistrés et s’assure que les documents appropriés sont enregistrés si nécessaire.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres d’image de document](creating-document-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](using-frame-windows.md)
