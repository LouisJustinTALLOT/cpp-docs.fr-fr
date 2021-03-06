---
description: 'En savoir plus sur : initialisation des parties d’un objet CStatusBarCtrl'
title: Initialisation des parties d'un objet CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: 52eb738f5fe54a54e54a6415a602a68123869b32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197528"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Initialisation des parties d'un objet CStatusBarCtrl

Par défaut, une barre d’état affiche des informations d’État à l’aide de volets séparés. Ces volets (également appelés parties) peuvent contenir une chaîne de texte, une icône ou les deux.

Utilisez [SetParts](reference/cstatusbarctrl-class.md#setparts) pour définir le nombre de parties, et la longueur, de la barre d’État. Après avoir créé les parties de la barre d’État, effectuez des appels à [SetText](reference/cstatusbarctrl-class.md#settext) et [seticon](reference/cstatusbarctrl-class.md#seticon) pour définir le texte ou l’icône d’une partie spécifique de la barre d’État. Une fois la partie correctement définie, le contrôle est automatiquement redessiné.

L’exemple suivant initialise un objet existant `CStatusBarCtrl` ( `m_StatusBarCtrl` ) avec quatre volets, puis définit une icône (IDI_ICON1) et du texte dans la deuxième partie.

[!code-cpp[NVC_MFCControlLadenDialog#31](codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Pour plus d’informations sur la définition du mode d’un `CStatusBarCtrl` objet sur simple, consultez [définition du mode d’un objet CStatusBarCtrl](setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[Contrôles](controls-mfc.md)
