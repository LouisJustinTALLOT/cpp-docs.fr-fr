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
ms.openlocfilehash: 57f163fd36c0f25508d94a84495fcaf1956e277d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837201"
---
# <a name="gray-and-dithered-bitmap-functions"></a>fonctions d'image bitmap tramée et grise

**Fonctions d’image bitmap grise**

MFC propose deux fonctions qui permettent de donner à une image bitmap l’apparence d’un contrôle désactivé.

![Comparaison des versions d'icônes grises et d'origine](../../mfc/reference/media/vcgraybitmap.gif "Comparaison des versions d'icônes grises et d'origine")

|Nom|Description|
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|Dessine une version grise d’une image bitmap.|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|Copie une version grise d’une image bitmap.|

**Fonctions d’image bitmap tramée**

MFC propose également deux fonctions qui permettent de remplacer l’arrière-plan d’une image bitmap par un motif tramé.

![Comparaison des versions d'icônes dégradées et d'origine](../../mfc/reference/media/vcditheredbitmap.gif "Comparaison des versions d'icônes dégradées et d'origine")

|Nom|Description|
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|Dessine une image bitmap avec un arrière-plan tramé.|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|Copie une image bitmap avec un arrière-plan tramé.|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a> AfxDrawGrayBitmap

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

*Maîtres*<br/>
Pointe vers le contrôleur de domaine de destination.

*x*<br/>
Coordonnée x de destination.

*y*<br/>
Coordonnée y de destination.

*rSrc*<br/>
Image bitmap source.

*crBackground*<br/>
Nouvelle couleur d’arrière-plan (généralement grise, comme COLOR_MENU).

### <a name="remarks"></a>Notes

Une image bitmap dessinée avec `AfxDrawGrayBitmap` a l’apparence d’un contrôle désactivé.

![Comparaison des versions d'icônes grises et d'origine](../../mfc/reference/media/vcgraybitmap.gif "Comparaison des versions d'icônes grises et d'origine")

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a> AfxGetGrayBitmap

Copie une version grise d’une image bitmap.

```cpp
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
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

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a> AfxDrawDitheredBitmap

Dessine une bitmap, en remplaçant son arrière-plan par un modèle tramé (vérificateur).

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

*Maîtres*<br/>
Pointe vers le contrôleur de domaine de destination.

*x*<br/>
Coordonnée x de destination.

*y*<br/>
Coordonnée y de destination.

*rSrc*<br/>
Image bitmap source.

*cr1*<br/>
L’une des deux couleurs de tramage, généralement en blanc.

*CR2*<br/>
Autre couleur de tramage, en général gris clair (COLOR_MENU).

### <a name="remarks"></a>Notes

Le bitmap source est dessiné sur le DC de destination avec un modèle à damier à deux couleurs (*CR1* et *CR2*) qui remplace l’arrière-plan de la bitmap. L’arrière-plan de la bitmap source est défini comme ses pixels blancs et tous les pixels correspondant à la couleur du pixel dans le coin supérieur gauche de l’image bitmap.

![Comparaison des versions d'icônes dégradées et d'origine](../../mfc/reference/media/vcditheredbitmap.gif "Comparaison des versions d'icônes dégradées et d'origine")

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a> AfxGetDitheredBitmap

Copie une image bitmap, en remplaçant son arrière-plan par un modèle tramé (vérificateur).

```cpp
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Image bitmap source.

*pDest*<br/>
Image bitmap de destination.

*cr1*<br/>
L’une des deux couleurs de tramage, généralement en blanc.

*CR2*<br/>
Autre couleur de tramage, en général gris clair (COLOR_MENU).

### <a name="remarks"></a>Notes

La bitmap source est copiée dans le bitmap de destination avec un modèle à damier à deux couleurs (*CR1* et *CR2*) qui remplace l’arrière-plan de la bitmap source. L’arrière-plan de la bitmap source est défini comme ses pixels blancs et tous les pixels correspondant à la couleur du pixel dans le coin supérieur gauche de l’image bitmap.

![Comparaison des versions d'icônes dégradées et d'origine](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
