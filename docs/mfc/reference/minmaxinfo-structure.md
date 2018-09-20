---
title: Minmaxinfo, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b63589edbe47aa09b8a6be92b5b7eb7e29077c96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402289"
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

