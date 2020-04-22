---
title: CD2DRadialGradientBrush, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: 450314fdbf8441b0cc345430518d083573659add
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750305"
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush, classe

Un emballage pour ID2D1RadialGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Construit un objet CD2DLinearGradientBrush.|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destructeur. Appelé quand un objet de brosse de gradient radial D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DRadialGradientBrush::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DRadialGradientBrush::Créer](#create)|Crée un CD2DRadialGradientBrush. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Détruit un objet CD2DRadialGradientBrush. (Overrides [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DRadialGradientBrush::Get](#get)|Retourne l’interface ID2D1RadialGradientBrush|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Récupère le centre de l’ellipse de gradient|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Récupère le décalage de l’origine du gradient par rapport au centre de l’ellipse de gradient|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Récupère le rayon x de l’ellipse de gradient|
|[CD2DRadialGradientBrush::GetRadiusy](#getradiusy)|Récupère le y-radius de l’ellipse de gradient|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Spécifie le centre de l’ellipse de gradient dans l’espace de coordonnées de la brosse|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Spécifie le décalage de l’origine du gradient par rapport au centre de l’ellipse de gradient|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Spécifie le rayon x de l’ellipse de gradient, dans l’espace de coordonnées de la brosse|
|[CD2DRadialGradientBrush::SetRadiusy](#setradiusy)|Spécifie le rayon y de l’ellipse de gradient, dans l’espace de coordonnées de la brosse|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DRadialGradientBrush::opérateur ID2D1RadialGradientBrush](#operator_id2d1radialgradientbrush_star)|Retourne l’interface ID2D1RadialGradientBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Un pointeur à un ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Le centre, le décalage d’origine de gradient, et x-radius et y-radius du gradient de la brosse.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush (en anglais)](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush

Destructeur. Appelé quand un objet de brosse de gradient radial D2D est détruit.

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a>CD2DRadialGradientBrush::Attach

Attache l’interface de ressources existante à l’objet

```cpp
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Impossible d’être NULL

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush

Construit un objet CD2DLinearGradientBrush.

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Un pointeur à la cible de rendu.

*gradientStops*<br/>
Un pointeur à un tableau de structures D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Une valeur supérieure ou égale à 1 qui spécifie le nombre d’arrêts de gradient dans le tableau gradientStops.

*RadialGradientBrushProperties*<br/>
Le centre, le décalage d’origine de gradient, et x-radius et y-radius du gradient de la brosse.

*couleurInterpolationGamma*<br/>
L’espace dans lequel l’interpolation des couleurs entre les arrêts de gradient est effectuée.

*extendMode*<br/>
Le comportement du gradient en dehors de la gamme normalisée [0,1].

*pBrushProperties (en)*<br/>
Un pointeur à l’opacité et à la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a>CD2DRadialGradientBrush::Créer

Crée un CD2DRadialGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a>CD2DRadialGradientBrush::Destroy

Détruit un objet CD2DRadialGradientBrush.

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a>CD2DRadialGradientBrush::Detach

Détache l’interface des ressources de l’objet

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a>CD2DRadialGradientBrush::Get

Retourne l’interface ID2D1RadialGradientBrush

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1RadialGradientBrush ou NULL si l’objet n’est pas encore paralysé.

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter

Récupère le centre de l’ellipse de gradient

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Valeur de retour

Le centre de l’ellipse de gradient. Cette valeur s’exprime dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset

Récupère le décalage de l’origine du gradient par rapport au centre de l’ellipse de gradient

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Valeur de retour

Le décalage de l’origine de gradient du centre de l’ellipse de gradient. Cette valeur s’exprime dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX

Récupère le rayon x de l’ellipse de gradient

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Valeur de retour

Le rayon x de l’ellipse de gradient. Cette valeur s’exprime dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a>CD2DRadialGradientBrush::GetRadiusy

Récupère le y-radius de l’ellipse de gradient

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Valeur de retour

Le y-radius de l’ellipse de gradient. Cette valeur s’exprime dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush

Un pointeur à un ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties

Le centre, le décalage d’origine de gradient, et x-radius et y-radius du gradient de la brosse.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::opérateur ID2D1RadialGradientBrush

Retourne l’interface ID2D1RadialGradientBrush

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1RadialGradientBrush ou NULL si l’objet n’est pas encore paralysé.

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter

Spécifie le centre de l’ellipse de gradient dans l’espace de coordonnées de la brosse

```cpp
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Le centre de l’ellipse de gradient, dans l’espace de coordonnées de la brosse

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset

Spécifie le décalage de l’origine du gradient par rapport au centre de l’ellipse de gradient

```cpp
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Paramètres

*gradientOriginOffset*<br/>
Le décalage de l’origine de gradient du centre de l’ellipse de gradient

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX

Spécifie le rayon x de l’ellipse de gradient, dans l’espace de coordonnées de la brosse

```cpp
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Paramètres

*Radiusx*<br/>
Le rayon x de l’ellipse de gradient. Cette valeur est dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusy

Spécifie le rayon y de l’ellipse de gradient, dans l’espace de coordonnées de la brosse

```cpp
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Paramètres

*Radiusy*<br/>
Le y-radius de l’ellipse de gradient. Cette valeur est dans l’espace de coordonnées du pinceau

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
