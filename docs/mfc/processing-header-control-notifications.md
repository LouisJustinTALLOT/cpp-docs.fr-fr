---
description: En savoir plus sur le traitement des notifications Header-Control
title: Traitement des notifications de contrôle Header
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: ac1cdbf5efc3e82cdf417a38072cf344ca2ee1a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154849"
---
# <a name="processing-header-control-notifications"></a>Traitement des notifications de contrôle Header

Dans votre classe d’affichage ou de boîte de dialogue, utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour créer une fonction de gestionnaire [OnChildNotify](reference/cwnd-class.md#onchildnotify) avec une instruction switch pour tous les messages de notification de contrôle d’en-tête ([CHeaderCtrl](reference/cheaderctrl-class.md)) que vous souhaitez gérer (consultez [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md)). Les notifications sont envoyées à la fenêtre parente lorsque l’utilisateur clique ou double-clique sur un élément d’en-tête, fait glisser un séparateur entre les éléments, et ainsi de suite.

Les messages de notification associés à un contrôle d’en-tête sont répertoriés dans [référence de contrôle d’en-tête](/windows/win32/controls/header-control-reference) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](using-cheaderctrl.md)<br/>
[Contrôles](controls-mfc.md)
