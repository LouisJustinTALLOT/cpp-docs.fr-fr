---
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
ms.openlocfilehash: e26202392bf4783598aec0dddfea514fce806a8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369297"
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush, classe

Un emballage pour ID2D1BitmapBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Surchargé. Construit un objet CD2DBitmapBrush à partir du fichier.|
|[CD2DBitmapBrush: CD2DBitmapBrush](#dtor)|Destructeur. Appelé quand un objet de brosse à bitmap D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DBitmapBrush::Créer](#create)|Crée un cd2DBitmapBrush. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::Destroy](#destroy)|Détruit un objet CD2DBitmapBrush. (Overrides [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DBitmapBrush::Get](#get)|Retourne l’interface ID2D1BitmapBrush|
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Obtient la source de bitmap que ce pinceau utilise pour peindre|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Obtient la méthode par laquelle la brosse tuiles horizontalement les zones qui s’étendent au-delà de sa bitmap|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Obtient la méthode par laquelle la brosse verticalement tuiles les zones qui s’étendent au-delà de sa bitmap|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Obtient la méthode d’interpolation utilisée lorsque le bitmap de brosse est écaillé ou tourné|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Spécifie la source de bitmap que ce pinceau utilise pour peindre|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Précise comment la brosse tuiles horizontalement les zones qui s’étendent au-delà de sa bitmap|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Précise comment la brosse tuiles verticalement les zones qui s’étendent au-delà de sa bitmap|
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Spécifie le mode d’interpolation utilisé lorsque le bitmap de brosse est mis à l’échelle ou tourné|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Initialise l’objet|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush::opérateur ID2D1BitmapBrush](#operator_id2d1bitmapbrush_star)|Retourne l’interface ID2D1BitmapBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Stocke un pointeur sur un objet CD2DBitmap.|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Stocke un pointeur sur un objet ID2D1BitmapBrush.|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Propriétés de brosse De bitmap.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush (en anglais)](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a>CD2DBitmapBrush: CD2DBitmapBrush

Destructeur. Appelé quand un objet de brosse à bitmap D2D est détruit.

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a>CD2DBitmapBrush::Attach

Attache l’interface de ressources existante à l’objet

```
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Impossible d’être NULL

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush

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
Un pointeur à la cible de rendu.

*pBitmapBrushProperties*<br/>
Un pointeur vers les modes d’extension et le mode d’interpolation d’une brosse bitmap.

*pBrushProperties (en)*<br/>
Un pointeur à l’opacité et à la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

*uiResID*<br/>
Le numéro d’identification des ressources de la ressource.

*lpszType (lpszType)*<br/>
Pointeur vers une chaîne non terminée qui contient le type de ressource.

*tailleDest*<br/>
Taille de destination de la bitmap.

*lpszImagePath*<br/>
Pointeur vers une chaîne non terminée qui contient le nom du fichier.

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a>CD2DBitmapBrush::CommonInit

Initialise l’objet

```
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Paramètres

*pBitmapBrushProperties*<br/>
Un pointeur pour les propriétés de brosse de bitmap.

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a>CD2DBitmapBrush::Créer

Crée un cd2DBitmapBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a>CD2DBitmapBrush::Destroy

Détruit un objet CD2DBitmapBrush.

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a>CD2DBitmapBrush::Detach

Détache l’interface des ressources de l’objet

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dbitmapbrushget"></a><a name="get"></a>CD2DBitmapBrush::Get

Retourne l’interface ID2D1BitmapBrush

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1BitmapBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a>CD2DBitmapBrush::GetBitmap

Obtient la source de bitmap que ce pinceau utilise pour peindre

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet CD2DBitmap ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX

Obtient la méthode par laquelle la brosse tuiles horizontalement les zones qui s’étendent au-delà de sa bitmap

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui spécifie comment la brosse tuiles horizontalement les zones qui s’étendent au-delà de sa bitmap

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY

Obtient la méthode par laquelle la brosse verticalement tuiles les zones qui s’étendent au-delà de sa bitmap

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui spécifie comment la brosse tuiles verticalement les zones qui s’étendent au-delà de sa bitmap

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode

Obtient la méthode d’interpolation utilisée lorsque le bitmap de brosse est écaillé ou tourné

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Valeur de retour

La méthode d’interpolation utilisée lorsque le bitmap de brosse est mis à l’échelle ou tourné

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap

Stocke un pointeur sur un objet CD2DBitmap.

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush

Stocke un pointeur sur un objet ID2D1BitmapBrush.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties

Propriétés de brosse De bitmap.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::opérateur ID2D1BitmapBrush

Retourne l’interface ID2D1BitmapBrush

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1BitmapBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap

Spécifie la source de bitmap que ce pinceau utilise pour peindre

```
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

*pBitmap (en)*<br/>
La source de bitmap utilisée par la brosse

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX

Précise comment la brosse tuiles horizontalement les zones qui s’étendent au-delà de sa bitmap

```
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Paramètres

*extendModeX*<br/>
Une valeur qui spécifie comment la brosse tuiles horizontalement les zones qui s’étendent au-delà de sa bitmap

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY

Précise comment la brosse tuiles verticalement les zones qui s’étendent au-delà de sa bitmap

```
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Paramètres

*extendModeY*<br/>
Une valeur qui spécifie comment la brosse tuiles verticalement les zones qui s’étendent au-delà de sa bitmap

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a>CD2DBitmapBrush::SetInterpolationMode

Spécifie le mode d’interpolation utilisé lorsque le bitmap de brosse est mis à l’échelle ou tourné

```
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Paramètres

*interpolationMode*<br/>
Le mode d’interpolation utilisé lorsque le bitmap de brosse est mis à l’échelle ou tourné

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
