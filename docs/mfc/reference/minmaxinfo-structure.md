---
title: MINMAXINFO, structure
ms.date: 11/04/2016
f1_keywords:
- MINMAXINFO
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
ms.openlocfilehash: 11f55b1756623626769e21c006543b6993607b08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517843"
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO, structure

Le `MINMAXINFO` structure contient des informations sur la taille agrandie d’une fenêtre et position et sa taille minimale et maximale de suivi.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagMINMAXINFO {
    POINT ptReserved;
    POINT ptMaxSize;
    POINT ptMaxPosition;
    POINT ptMinTrackSize;
    POINT ptMaxTrackSize;
} MINMAXINFO;
```

#### <a name="parameters"></a>Paramètres

*ptReserved*<br/>
Réservé à un usage interne.

*ptMaxSize*<br/>
Spécifie la largeur agrandie (point.x) et la hauteur agrandie (point.y) de la fenêtre.

*ptMaxPosition*<br/>
Spécifie la position du côté gauche de la fenêtre agrandie (point.x) et la position du haut de la fenêtre agrandie (point.y).

*ptMinTrackSize*<br/>
Spécifie la largeur (point.x) de suivi minimale et la hauteur (point.y) de la fenêtre de suivi minimale.

*ptMaxTrackSize*<br/>
Spécifie le nombre maximal de suivi (point.x) de la largeur et la valeur maximale (point.y) de hauteur de la fenêtre de suivi.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

