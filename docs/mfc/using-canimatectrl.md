---
title: Utilisation de CAnimateCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b02a07b1f5a433ffa9525da8e8a7f942c9034d54
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398454"
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

