---
description: 'En savoir plus sur : classe CD2DBitmapBrush'
title: CD2DBitmapBrush, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: a9d4c1955b1318ecb273482cd49025090bf97d3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227583"
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush, classe

Wrapper pour ID2D1BitmapBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Surchargé. Construit un objet CD2DBitmapBrush à partir d’un fichier.|
|[CD2DBitmapBrush :: ~ CD2DBitmapBrush](#dtor)|Destructeur. Appelé lorsqu’un objet pinceau de bitmap D2D est en cours de destruction.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[CD2DBitmapBrush :: Create](#create)|Crée un CD2DBitmapBrush. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush ::D estroy](#destroy)|Détruit un objet CD2DBitmapBrush. (Substitue [CD2DBrush, ::D estroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[CD2DBitmapBrush :: obtient](#get)|Retourne l’interface ID2D1BitmapBrush|
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Obtient la source bitmap que ce pinceau utilise pour peindre|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Obtient la méthode par laquelle le pinceau mosaïque horizontalement les zones qui s’étendent au-delà de sa bitmap.|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Obtient la méthode par laquelle le pinceau mosaïque verticalement les zones qui s’étendent au-delà de sa bitmap.|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Obtient la méthode d’interpolation utilisée lorsque la bitmap du pinceau est mise à l’échelle ou pivotée|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Spécifie la source de l’image bitmap utilisée par ce pinceau pour peindre|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Spécifie comment le pinceau mosaïque horizontalement les zones qui s’étendent au-delà de sa bitmap|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Spécifie comment le pinceau mosaïque verticalement les zones qui s’étendent au-delà de sa bitmap|
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Spécifie le mode d’interpolation utilisé lorsque l’image bitmap du pinceau est mise à l’échelle ou pivotée|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Initialise l’objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush :: Operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|Retourne l’interface ID2D1BitmapBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush :: m_pBitmap](#m_pbitmap)|Stocke un pointeur vers un objet Cd2dbitmap,.|
|[CD2DBitmapBrush :: m_pBitmapBrush](#m_pbitmapbrush)|Stocke un pointeur vers un objet ID2D1BitmapBrush.|
|[CD2DBitmapBrush :: m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Propriétés du pinceau bitmap.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

[Cd2dbrush,](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a> CD2DBitmapBrush :: ~ CD2DBitmapBrush

Destructeur. Appelé lorsqu’un objet pinceau de bitmap D2D est en cours de destruction.

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a> CD2DBitmapBrush :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas être NULL

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a> CD2DBitmapBrush::CD2DBitmapBrush

Construit un objet CD2DBitmapBrush.

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*pBitmapBrushProperties*<br/>
Pointeur vers les modes d’extension et le mode d’interpolation d’un pinceau bitmap.

*pBrushProperties*<br/>
Pointeur vers l’opacité et la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

*uiResID*<br/>
Numéro d’ID de ressource de la ressource.

*lpszType*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le type de ressource.

*Taille*<br/>
Taille de destination de l’image bitmap.

*lpszImagePath*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom du fichier.

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a> CD2DBitmapBrush::CommonInit

Initialise l’objet.

```cpp
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Paramètres

*pBitmapBrushProperties*<br/>
Pointeur vers les propriétés du pinceau bitmap.

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a> CD2DBitmapBrush :: Create

Crée un CD2DBitmapBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a> CD2DBitmapBrush ::D estroy

Détruit un objet CD2DBitmapBrush.

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a> CD2DBitmapBrush ::D Etach

Détache l’interface de ressource de l’objet

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dbitmapbrushget"></a><a name="get"></a> CD2DBitmapBrush :: obtient

Retourne l’interface ID2D1BitmapBrush

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1BitmapBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a> CD2DBitmapBrush::GetBitmap

Obtient la source bitmap que ce pinceau utilise pour peindre

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet Cd2dbitmap, ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a> CD2DBitmapBrush::GetExtendModeX

Obtient la méthode par laquelle le pinceau mosaïque horizontalement les zones qui s’étendent au-delà de sa bitmap.

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui spécifie comment le pinceau mosaïque horizontalement les zones qui s’étendent au-delà de sa bitmap.

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a> CD2DBitmapBrush::GetExtendModeY

Obtient la méthode par laquelle le pinceau mosaïque verticalement les zones qui s’étendent au-delà de sa bitmap.

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui spécifie comment le pinceau mosaïque verticalement les zones qui s’étendent au-delà de sa bitmap.

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a> CD2DBitmapBrush::GetInterpolationMode

Obtient la méthode d’interpolation utilisée lorsque la bitmap du pinceau est mise à l’échelle ou pivotée

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

Méthode d’interpolation utilisée lorsque l’image bitmap de pinceau est mise à l’échelle ou pivotée

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a> CD2DBitmapBrush :: m_pBitmap

Stocke un pointeur vers un objet Cd2dbitmap,.

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a> CD2DBitmapBrush :: m_pBitmapBrush

Stocke un pointeur vers un objet ID2D1BitmapBrush.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a> CD2DBitmapBrush :: m_pBitmapBrushProperties

Propriétés du pinceau bitmap.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a> CD2DBitmapBrush :: Operator ID2D1BitmapBrush *

Retourne l’interface ID2D1BitmapBrush

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1BitmapBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a> CD2DBitmapBrush::SetBitmap

Spécifie la source de l’image bitmap utilisée par ce pinceau pour peindre

```cpp
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

*pBitmap*<br/>
Source bitmap utilisée par le pinceau

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a> CD2DBitmapBrush::SetExtendModeX

Spécifie comment le pinceau mosaïque horizontalement les zones qui s’étendent au-delà de sa bitmap

```cpp
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Paramètres

*extendModeX*<br/>
Valeur qui spécifie comment le pinceau mosaïque horizontalement les zones qui s’étendent au-delà de sa bitmap.

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a> CD2DBitmapBrush::SetExtendModeY

Spécifie comment le pinceau mosaïque verticalement les zones qui s’étendent au-delà de sa bitmap

```cpp
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Paramètres

*extendModeY*<br/>
Valeur qui spécifie comment le pinceau mosaïque verticalement les zones qui s’étendent au-delà de sa bitmap.

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a> CD2DBitmapBrush::SetInterpolationMode

Spécifie le mode d’interpolation utilisé lorsque l’image bitmap du pinceau est mise à l’échelle ou pivotée

```cpp
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Paramètres

*interpolationMode*<br/>
Mode d’interpolation utilisé lorsque l’image bitmap de pinceau est mise à l’échelle ou pivotée

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
