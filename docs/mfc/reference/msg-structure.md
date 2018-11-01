---
title: MSG, structure
ms.date: 11/04/2016
f1_keywords:
- MSG
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
ms.openlocfilehash: 1a953f8d0d685e25beedd2d401e227c934414208
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499808"
---
# <a name="msg-structure"></a>MSG, structure

Le `MSG` structure contient des informations de message à partir de la file d’attente des messages d’un thread.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagMSG {     // msg
    HWND hwnd;
    UINT message;
    WPARAM wParam;
    LPARAM lParam;
    DWORD time;
    POINT pt;
} MSG;
```

#### <a name="parameters"></a>Paramètres

*HWND*<br/>
Identifie la fenêtre dont la procédure de fenêtre reçoit le message.

*message*<br/>
Spécifie le numéro du message.

*wParam*<br/>
Spécifie des informations supplémentaires sur le message. La signification exacte dépend de la valeur de la `message` membre.

*lParam*<br/>
Spécifie des informations supplémentaires sur le message. La signification exacte dépend de la valeur de la `message` membre.

*time*<br/>
Spécifie l’heure à laquelle le message a été publié.

*pt*<br/>
Spécifie la position du curseur, en coordonnées d’écran, lorsque le message a été publié.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

