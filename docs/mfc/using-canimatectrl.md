---
title: Utilisation de CAnimateCtrl
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: b967cc6dde6b4f639ef081b3821f6a7e5a2fe295
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351639"
---
# <a name="using-canimatectrl"></a>Utilisation de CAnimateCtrl

Un contrôle animation, représenté par la classe [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), est une fenêtre qui affiche un clip au format vidéo entrelacés AVI (Audio), le format audio/vidéo Windows standard. Un clip AVI est une série de frames bitmap, comme un film.

Dans la mesure où votre thread continue de s’exécuter pendant que le clip AVI s’affiche, une utilisation courante d’un contrôle animation consiste à indiquer l’activité du système pendant une longue opération. Par exemple, la boîte de dialogue Rechercher Windows affiche une loupe qui se déplace en tant que le système recherche un fichier.

Contrôles d’animation peuvent lire uniquement les éléments AVI simples, et ils ne prennent pas en charge son. (Pour obtenir une liste complète des limitations, consultez [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Étant donné que les fonctionnalités d’un contrôle animation sont très limitées et susceptibles d’être modifiées, vous devez utiliser une alternative tels que le contrôle MCIWnd si vous avez besoin d’un contrôle pour fournir la lecture multimédia et/ou les fonctions d’enregistrement. Pour plus d’informations sur le contrôle MCIWnd, consultez la documentation multimédia.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Utilisation d’un contrôle Animation](../mfc/using-an-animation-control.md)

- [Notifications envoyées par les contrôles d’animation](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)
