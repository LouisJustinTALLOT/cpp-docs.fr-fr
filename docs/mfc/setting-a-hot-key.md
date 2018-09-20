---
title: Définition d’une clé à chaud | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c634f9eac562be2b22f79e6a71c3010e3ea3e24
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435231"
---
# <a name="setting-a-hot-key"></a>Définition d'une touche d'accès rapide

Votre application peut utiliser les informations fournies par une touche d’accès rapide ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) contrôle de deux manières :

- Configurer une touche d’accès rapide pour activer une fenêtre non-enfant en envoyant un [message WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) message dans la fenêtre à activer.

- Définissez une touche d’accès rapide spécifiques aux threads en appelant la fonction Windows [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

