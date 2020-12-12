---
description: 'En savoir plus sur : classe Cd2dradialgradientbrush,'
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
ms.openlocfilehash: c5e169a5d608edd246d5c7269c94e3b225fdd491
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118743"
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush, classe

Wrapper pour ID2D1RadialGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dradialgradientbrush, :: Cd2dradialgradientbrush,](#cd2dradialgradientbrush)|Construit un objet Cd2dlineargradientbrush,.|
|[Cd2dradialgradientbrush, :: ~ Cd2dradialgradientbrush,](#_dtorcd2dradialgradientbrush)|Destructeur. Appelé lorsqu’un objet pinceau de dégradé radial D2D est en cours de destruction.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dradialgradientbrush, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dradialgradientbrush, :: Create](#create)|Crée un Cd2dradialgradientbrush,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dradialgradientbrush, ::D estroy](#destroy)|Détruit un objet Cd2dradialgradientbrush,. (Substitue [CD2DGradientBrush, ::D estroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[Cd2dradialgradientbrush, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dradialgradientbrush, :: obtient](#get)|Retourne l’interface ID2D1RadialGradientBrush|
|[Cd2dradialgradientbrush, :: GetCenter](#getcenter)|Récupère le centre de l’ellipse de dégradé|
|[Cd2dradialgradientbrush, :: GetGradientOriginOffset](#getgradientoriginoffset)|Récupère le décalage de l’origine du dégradé par rapport au centre de l’ellipse du dégradé|
|[Cd2dradialgradientbrush, :: GetRadiusX](#getradiusx)|Récupère le rayon x de l’ellipse du dégradé|
|[Cd2dradialgradientbrush, :: GetRadiusY](#getradiusy)|Récupère le rayon y de l’ellipse du dégradé|
|[Cd2dradialgradientbrush, :: SetCenter](#setcenter)|Spécifie le centre de l’ellipse de dégradé dans l’espace de coordonnées du pinceau|
|[Cd2dradialgradientbrush, :: SetGradientOriginOffset](#setgradientoriginoffset)|Spécifie le décalage de l’origine du dégradé par rapport au centre de l’ellipse du dégradé|
|[Cd2dradialgradientbrush, :: SetRadiusX](#setradiusx)|Spécifie le rayon x de l’ellipse de dégradé, dans l’espace de coordonnées du pinceau|
|[Cd2dradialgradientbrush, :: SetRadiusY](#setradiusy)|Spécifie le rayon y de l’ellipse de dégradé, dans l’espace de coordonnées du pinceau|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dradialgradientbrush, :: Operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|Retourne l’interface ID2D1RadialGradientBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dradialgradientbrush, :: m_pRadialGradientBrush](#m_pradialgradientbrush)|Pointeur vers un ID2D1RadialGradientBrush.|
|[Cd2dradialgradientbrush, :: m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Centre, décalage d’origine du dégradé et rayon x et y du dégradé du pinceau.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

[Cd2dbrush,](../../mfc/reference/cd2dbrush-class.md)

[Cd2dgradientbrush,](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a> Cd2dradialgradientbrush, :: ~ Cd2dradialgradientbrush,

Destructeur. Appelé lorsqu’un objet pinceau de dégradé radial D2D est en cours de destruction.

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a> Cd2dradialgradientbrush, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas être NULL

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a> Cd2dradialgradientbrush, :: Cd2dradialgradientbrush,

Construit un objet Cd2dlineargradientbrush,.

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
Pointeur vers la cible de rendu.

*gradientStops*<br/>
Pointeur vers un tableau de structures D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Valeur supérieure ou égale à 1 qui spécifie le nombre de points de dégradé dans le tableau gradientStops.

*RadialGradientBrushProperties*<br/>
Centre, décalage d’origine du dégradé et rayon x et y du dégradé du pinceau.

*colorInterpolationGamma*<br/>
Espace dans lequel l’interpolation de couleur entre les arrêts de dégradé est effectuée.

*extendMode*<br/>
Comportement du dégradé en dehors de la plage normalisée [0, 1].

*pBrushProperties*<br/>
Pointeur vers l’opacité et la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a> Cd2dradialgradientbrush, :: Create

Crée un Cd2dradialgradientbrush,.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a> Cd2dradialgradientbrush, ::D estroy

Détruit un objet Cd2dradialgradientbrush,.

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a> Cd2dradialgradientbrush, ::D Etach

Détache l’interface de ressource de l’objet

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a> Cd2dradialgradientbrush, :: obtient

Retourne l’interface ID2D1RadialGradientBrush

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1RadialGradientBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a> Cd2dradialgradientbrush, :: GetCenter

Récupère le centre de l’ellipse de dégradé

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Valeur renvoyée

Centre de l’ellipse de dégradé. Cette valeur est exprimée dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a> Cd2dradialgradientbrush, :: GetGradientOriginOffset

Récupère le décalage de l’origine du dégradé par rapport au centre de l’ellipse du dégradé

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Valeur renvoyée

Décalage de l’origine du dégradé à partir du centre de l’ellipse du dégradé. Cette valeur est exprimée dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a> Cd2dradialgradientbrush, :: GetRadiusX

Récupère le rayon x de l’ellipse du dégradé

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Valeur renvoyée

Rayon x de l’ellipse de dégradé. Cette valeur est exprimée dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a> Cd2dradialgradientbrush, :: GetRadiusY

Récupère le rayon y de l’ellipse du dégradé

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Valeur renvoyée

Rayon y de l’ellipse de dégradé. Cette valeur est exprimée dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a> Cd2dradialgradientbrush, :: m_pRadialGradientBrush

Pointeur vers un ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a> Cd2dradialgradientbrush, :: m_RadialGradientBrushProperties

Centre, décalage d’origine du dégradé et rayon x et y du dégradé du pinceau.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a> Cd2dradialgradientbrush, :: Operator ID2D1RadialGradientBrush *

Retourne l’interface ID2D1RadialGradientBrush

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1RadialGradientBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a> Cd2dradialgradientbrush, :: SetCenter

Spécifie le centre de l’ellipse de dégradé dans l’espace de coordonnées du pinceau

```cpp
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Centre de l’ellipse de dégradé, dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a> Cd2dradialgradientbrush, :: SetGradientOriginOffset

Spécifie le décalage de l’origine du dégradé par rapport au centre de l’ellipse du dégradé

```cpp
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Paramètres

*gradientOriginOffset*<br/>
Décalage de l’origine du dégradé à partir du centre de l’ellipse du dégradé

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a> Cd2dradialgradientbrush, :: SetRadiusX

Spécifie le rayon x de l’ellipse de dégradé, dans l’espace de coordonnées du pinceau

```cpp
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Paramètres

*RADIUS*<br/>
Rayon x de l’ellipse de dégradé. Cette valeur se trouve dans l’espace de coordonnées du pinceau

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a> Cd2dradialgradientbrush, :: SetRadiusY

Spécifie le rayon y de l’ellipse de dégradé, dans l’espace de coordonnées du pinceau

```cpp
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Paramètres

*radiusY*<br/>
Rayon y de l’ellipse de dégradé. Cette valeur se trouve dans l’espace de coordonnées du pinceau

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
