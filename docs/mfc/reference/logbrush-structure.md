---
title: LOGBRUSH, structure
ms.date: 11/04/2016
f1_keywords:
- LOGBRUSH
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
ms.openlocfilehash: 0ca635690843c6dae9db05b0a8cc246cf38ce814
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579771"
---
# <a name="logbrush-structure"></a>LOGBRUSH, structure

Le `LOGBRUSH` structure définit le style, la couleur et le modèle d’un pinceau physique. Il est utilisé par le Windows [CreateBrushIndirect](/windows/desktop/api/wingdi/nf-wingdi-createbrushindirect) et [ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen) fonctions.

## <a name="syntax"></a>Syntaxe

```
typedef struct tag LOGBRUSH { /* lb */
    UINT lbStyle;
    COLORREF lbColor;
    LONG lbHatch;
} LOGBRUSH;
```

#### <a name="parameters"></a>Paramètres

*lbStyle*<br/>
Spécifie le style de pinceau. Le `lbStyle` membre doit être un des styles suivants :

- Pinceau de modèle BS_DIBPATTERN une par une bitmap indépendante du périphérique (DIB) spécification définie. Si *lbStyle* est BS_DIBPATTERN, le `lbHatch` membre contient un handle vers un DIB compressé.

- Pinceau de modèle BS_DIBPATTERNPT une par une bitmap indépendante du périphérique (DIB) spécification définie. Si *lbStyle* est BS_DIBPATTERNPT, le `lbHatch` membre contient un pointeur vers un DIB compressé.

- Pinceau BS_HATCHED hachée.

- Pinceau BS_HOLLOW creux.

- BS_NULL identique à BS_HOLLOW.

- Pinceau BS_PATTERN modèle défini par une image bitmap de mémoire.

- Pinceau BS_SOLID solide.

*lbColor*<br/>
Spécifie la couleur dans laquelle le pinceau doit être dessiné. Si *lbStyle* correspond au style BS_HOLLOW ou BS_PATTERN, *lbColor* est ignoré. Si *lbStyle* est BS_DIBPATTERN ou BS_DIBPATTERNBT, le mot de poids faible de *lbColor* Spécifie si le `bmiColors` membres de la [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) structure contiennent explicite rouge, vert, bleu valeurs (RVB) ou index dans la palette logique actuellement réalisée. Le `lbColor` membre doit être une des valeurs suivantes :

- DIB_PAL_COLORS la table des couleurs se compose d’un tableau d’indices de 16 bits dans la palette logique actuellement réalisée.

- DIB_RGB_COLORS la table des couleurs contient des valeurs RVB littérales.

*lbHatch*<br/>
Spécifie un style de hachurage. La signification varie selon le style de pinceau défini par *lbStyle*. Si *lbStyle* est BS_DIBPATTERN, le `lbHatch` membre contient un handle vers un DIB compressé. Si *lbStyle* est BS_DIBPATTERNPT, le `lbHatch` membre contient un pointeur vers un DIB compressé. Si *lbStyle* est BS_HATCHED, le `lbHatch` membre spécifie l’orientation des lignes utilisées pour créer le hachurage. Il peut prendre l’une des valeurs suivantes :

- Hachurage de vers le haut, gauche à droite la 45 degrés des A HS_BDIAGONAL

- HS_CROSS horizontale et verticale hachurage

- Hachurage de 45 degrés HS_DIAGCROSS

- Hachurage de vers le bas, de gauche à droite la 45 degrés des A HS_FDIAGONAL

- Hachures horizontales HS_HORIZONTAL

- Hachage HS_VERTICAL Vertical

Si *lbStyle* est BS_PATTERN, *lbHatch* est un handle de bitmap qui définit le modèle. Si *lbStyle* est BS_SOLID ou BS_HOLLOW, *lbHatch* est ignoré.

## <a name="remarks"></a>Notes

Bien que *lbColor* contrôle la couleur de premier plan d’un pinceau de hachurage, le [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) et [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) fonctions contrôlent la couleur d’arrière-plan.

## <a name="requirements"></a>Configuration requise

**En-tête :** wingdi.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

