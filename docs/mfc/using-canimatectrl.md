---
title: Utilisation de CAnimateCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: 79c1a0111317514ef6fd68acd0c6a2ebdccc3ba4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447107"
---
# <a name="using-canimatectrl"></a>Utilisation de CAnimateCtrl

Un contrôle d’animation, représenté par la classe [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), est une fenêtre qui affiche un clip au format AVI (Audio Video entrelacé), le format vidéo/audio Windows standard. Un clip AVI est une série de frames bitmap, comme un film.

Étant donné que votre thread continue de s’exécuter pendant l’affichage du clip AVI, une utilisation courante pour un contrôle d’animation consiste à indiquer l’activité système pendant une opération de longue durée. Par exemple, la boîte de dialogue Rechercher de Windows affiche une loupe mobile lorsque le système recherche un fichier.

Les contrôles d’animation peuvent uniquement lire des clips AVI simples et ne prennent pas en charge le son. (Pour obtenir la liste complète des limitations, consultez [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Étant donné que les fonctionnalités d’un contrôle d’animation sont sérieusement limitées et sujettes à modification, vous devez utiliser une alternative telle que le contrôle MCIWnd si vous avez besoin d’un contrôle pour fournir des fonctionnalités de lecture et/ou d’enregistrement multimédias. Pour plus d’informations sur le contrôle MCIWnd, consultez la documentation multimédia.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Utilisation d’un contrôle Animation](../mfc/using-an-animation-control.md)

- [Notifications envoyées par les contrôles d’animation](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)
