---
title: PAINTSTRUCT, structure
ms.date: 11/04/2016
f1_keywords:
- PAINTSTRUCT
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
ms.openlocfilehash: b5179a1bcba4a654ff235885ec2d0516e801fbb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677121"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT, structure

Le `PAINTSTRUCT` structure contient des informations qui peuvent être utilisées pour peindre la zone cliente d’une fenêtre.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagPAINTSTRUCT {
    HDC hdc;
    BOOL fErase;
    RECT rcPaint;
    BOOL fRestore;
    BOOL fIncUpdate;
    BYTE rgbReserved[16];
} PAINTSTRUCT;
```

#### <a name="parameters"></a>Paramètres

*HDC*<br/>
Identifie le contexte d’affichage à utiliser pour peindre.

*fErase*<br/>
Spécifie si l’arrière-plan doit être redessiné. Il n’est pas 0 si l’application doit redessiner l’arrière-plan. L’application est responsable du dessin de l’arrière-plan si une classe de fenêtre Windows est créée sans un pinceau d’arrière-plan (consultez la description de la `hbrBackground` membre de la [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) structure dans le SDK Windows).

*rcPaint*<br/>
Spécifie l’angle supérieur gauche et inférieure droite du rectangle dans lequel la peinture est demandée.

*fRestore*<br/>
Membre réservé. Il est utilisé en interne par Windows.

*fIncUpdate*<br/>
Membre réservé. Il est utilisé en interne par Windows.

*rgbReserved [16]*<br/>
Membre réservé. Un bloc de mémoire utilisée en interne par Windows réservé.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

