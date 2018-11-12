---
title: NCCALCSIZE_PARAMS, structure
ms.date: 11/04/2016
f1_keywords:
- NCCALCSIZE_PARAMS
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
ms.openlocfilehash: 3dbe1fcdb941a94876dd95a0eed86d6f4a3e15c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443769"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS, structure

Le `NCCALCSIZE_PARAMS` structure contient des informations qu’une application peut utiliser lors du traitement du message WM_NCCALCSIZE pour calculer la taille, la position et le contenu valid de la zone cliente d’une fenêtre.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagNCCALCSIZE_PARAMS {
    RECT rgrc[3];
    PWINDOWPOS lppos;
} NCCALCSIZE_PARAMS;
```

#### <a name="parameters"></a>Paramètres

*rgrc*<br/>
Spécifie un tableau de rectangles. Le premier contient les nouvelles coordonnées d’une fenêtre qui a été déplacé ou redimensionné. Le deuxième contient les coordonnées de la fenêtre avant qu’elle a été déplacée ou redimensionnée. Le troisième contient les coordonnées de la zone cliente d’une fenêtre avant qu’elle a été déplacée ou redimensionnée. Si la fenêtre est une fenêtre enfant, les coordonnées sont relatives à la zone client de la fenêtre parente. Si la fenêtre est une fenêtre de niveau supérieur, les coordonnées sont par rapport à l’écran.

*lppos*<br/>
Pointe vers un [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) structure qui contient les valeurs de taille et la position spécifiées dans l’opération qui a provoqué la fenêtre à être déplacé ou redimensionné.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

