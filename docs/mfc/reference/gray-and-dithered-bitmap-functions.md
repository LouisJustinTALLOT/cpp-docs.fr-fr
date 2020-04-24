---
title: fonctions d'image bitmap tramée et grise
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: a220596b880ee74d5f9ebf683d087156224ee7c5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751483"
---
# <a name="gray-and-dithered-bitmap-functions"></a>fonctions d'image bitmap tramée et grise

**Fonctions d’image bitmap grise**

MFC propose deux fonctions qui permettent de donner à une image bitmap l’apparence d’un contrôle désactivé.

![Comparaison des versions d'icônes grises et d'origine](../../mfc/reference/media/vcgraybitmap.gif "Comparaison des versions d'icônes grises et d'origine")

|||
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|Dessine une version grise d’une image bitmap.|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|Copie une version grise d’une image bitmap.|

**Fonctions d’image bitmap tramée**

MFC propose également deux fonctions qui permettent de remplacer l’arrière-plan d’une image bitmap par un motif tramé.

![Comparaison des versions d'icônes dégradées et d'origine](../../mfc/reference/media/vcditheredbitmap.gif "Comparaison des versions d'icônes dégradées et d'origine")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|Dessine une image bitmap avec un arrière-plan tramé.|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|Copie une image bitmap avec un arrière-plan tramé.|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a>AfxDrawGrayBitmap AfxDrawGrayBitmap

Dessine une version grise d’une image bitmap.

```cpp
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contrôleur de domaine de destination.

*x*<br/>
Coordonnée x de destination.

*y*<br/>
Coordonnée y de destination.

*rSrc (rSrc)*<br/>
Image bitmap source.

*crBackground*<br/>
Nouvelle couleur d’arrière-plan (généralement grise, comme COLOR_MENU).

### <a name="remarks"></a>Notes

Une image bitmap dessinée avec `AfxDrawGrayBitmap` a l’apparence d’un contrôle désactivé.

![Comparaison des versions d'icônes grises et d'origine](../../mfc/reference/media/vcgraybitmap.gif "Comparaison des versions d'icônes grises et d'origine")

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a>AfxGetGrayBitmap AfxGetGrayBitmap

Copie une version grise d’une image bitmap.

```cpp
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>Paramètres

*rSrc (rSrc)*<br/>
Image bitmap source.

*pDest*<br/>
Image bitmap de destination.

*crBackground*<br/>
Nouvelle couleur d’arrière-plan (généralement grise, comme COLOR_MENU).

### <a name="remarks"></a>Notes

Une image bitmap copiée avec `AfxGetGrayBitmap` a l’apparence d’un contrôle désactivé.

![Comparaison des versions d'icônes grises et d'origine](../../mfc/reference/media/vcgraybitmap.gif "Comparaison des versions d'icônes grises et d'origine")

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a>AfxDrawDitheredBitmap

Dessine une bitmap, remplaçant son arrière-plan par un modèle dithered (checker).

```cpp
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contrôleur de domaine de destination.

*x*<br/>
Coordonnée x de destination.

*y*<br/>
Coordonnée y de destination.

*rSrc (rSrc)*<br/>
Image bitmap source.

*cr1*<br/>
Une des deux couleurs de l’éthher, typiquement blanc.

*cr2*<br/>
L’autre couleur dither, typiquement gris clair (COLOR_MENU).

### <a name="remarks"></a>Notes

Le bitmap source est dessiné sur la destination DC avec un modèle à carreaux bicolores (*cr1* et *cr2)* remplaçant l’arrière-plan de la bitmap. L’arrière-plan de la bitmap source est défini comme ses pixels blancs et tous les pixels correspondant à la couleur du pixel dans le coin supérieur gauche de la bitmap.

![Comparaison des versions d'icônes dégradées et d'origine](../../mfc/reference/media/vcditheredbitmap.gif "Comparaison des versions d'icônes dégradées et d'origine")

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a>AfxGetDitheredBitmap

Copies d’une bitmap, remplaçant son arrière-plan par un modèle dithered (checker).

```cpp
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Paramètres

*rSrc (rSrc)*<br/>
Image bitmap source.

*pDest*<br/>
Image bitmap de destination.

*cr1*<br/>
Une des deux couleurs de l’éthher, typiquement blanc.

*cr2*<br/>
L’autre couleur dither, typiquement gris clair (COLOR_MENU).

### <a name="remarks"></a>Notes

La bitmap source est copiée à la bitmap de destination avec un modèle à carreaux de deux couleurs (*cr1* et *cr2)* remplaçant l’arrière-plan de la bitmap source. L’arrière-plan de la bitmap source est défini comme ses pixels blancs et tous les pixels correspondant à la couleur du pixel dans le coin supérieur gauche de la bitmap.

![Comparaison des versions d'icônes dégradées et d'origine](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
