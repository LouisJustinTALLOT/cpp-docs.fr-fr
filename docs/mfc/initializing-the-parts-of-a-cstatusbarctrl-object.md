---
title: Initialisation des parties d'un objet CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: 0f00aee03a74799bf14563653b50c487ff001d02
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264329"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Initialisation des parties d'un objet CStatusBarCtrl

Par défaut, une barre d’état affiche des informations d’état à l’aide des volets distincts. Ces volets (également appelés en tant que parties) peuvent contenir une chaîne de texte, une icône ou les deux.

Utilisez [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) a pour définir le nombre de parties et la longueur, la barre d’état. Une fois que vous avez créé les parties de la barre d’état, effectuer des appels vers [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) et [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) pour définir le texte ou l’icône pour une partie spécifique de la barre d’état. Une fois que la partie a été correctement définie, le contrôle est automatiquement redessiné.

L’exemple suivant initialise un existant `CStatusBarCtrl` objet (`m_StatusBarCtrl`) avec quatre volets et définir une icône (IDI_ICON1) et du texte dans la deuxième partie.

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Pour plus d’informations sur la définition du mode d’un `CStatusBarCtrl` objet simple, consultez [définition du Mode d’un objet CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
