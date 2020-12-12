---
description: 'En savoir plus sur : classe Cd2dlineargradientbrush,'
title: CD2DLinearGradientBrush, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: b133abe796e609a44d1ebe35a6e6e969c8ee2a68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180329"
---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush, classe

Wrapper pour ID2D1LinearGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dlineargradientbrush, :: Cd2dlineargradientbrush,](#cd2dlineargradientbrush)|Construit un objet Cd2dlineargradientbrush,.|
|[Cd2dlineargradientbrush, :: ~ Cd2dlineargradientbrush,](#_dtorcd2dlineargradientbrush)|Destructeur. Appelé lorsqu’un objet pinceau de dégradé linéaire D2D est en cours de destruction.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dlineargradientbrush, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dlineargradientbrush, :: Create](#create)|Crée un Cd2dlineargradientbrush,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dlineargradientbrush, ::D estroy](#destroy)|Détruit un objet Cd2dlineargradientbrush,. (Substitue [CD2DGradientBrush, ::D estroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[Cd2dlineargradientbrush, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dlineargradientbrush, :: obtient](#get)|Retourne l’interface ID2D1LinearGradientBrush|
|[Cd2dlineargradientbrush, :: GetEndPoint](#getendpoint)|Récupère les coordonnées de fin du dégradé linéaire|
|[Cd2dlineargradientbrush, :: GetStartPoint](#getstartpoint)|Récupère les coordonnées de début du dégradé linéaire|
|[Cd2dlineargradientbrush, :: SetEndPoint](#setendpoint)|Définit les coordonnées de fin du dégradé linéaire dans l’espace de coordonnées du pinceau|
|[Cd2dlineargradientbrush, :: SetStartPoint](#setstartpoint)|Définit les coordonnées de début du dégradé linéaire dans l’espace de coordonnées du pinceau|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dlineargradientbrush, :: Operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|Retourne l’interface ID2D1LinearGradientBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dlineargradientbrush, :: m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Points de début et de fin du dégradé.|
|[Cd2dlineargradientbrush, :: m_pLinearGradientBrush](#m_plineargradientbrush)|Pointeur vers un ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

[Cd2dbrush,](../../mfc/reference/cd2dbrush-class.md)

[Cd2dgradientbrush,](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a> Cd2dlineargradientbrush, :: ~ Cd2dlineargradientbrush,

Destructeur. Appelé lorsqu’un objet pinceau de dégradé linéaire D2D est en cours de destruction.

```
virtual ~CD2DLinearGradientBrush();
```

## <a name="cd2dlineargradientbrushattach"></a><a name="attach"></a> Cd2dlineargradientbrush, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas être NULL

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a> Cd2dlineargradientbrush, :: Cd2dlineargradientbrush,

Construit un objet Cd2dlineargradientbrush,.

```
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,
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

*LinearGradientBrushProperties*<br/>
Points de début et de fin du dégradé.

*colorInterpolationGamma*<br/>
Espace dans lequel l’interpolation de couleur entre les arrêts de dégradé est effectuée.

*extendMode*<br/>
Comportement du dégradé en dehors de la plage normalisée [0, 1].

*pBrushProperties*<br/>
Pointeur vers l’opacité et la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dlineargradientbrushcreate"></a><a name="create"></a> Cd2dlineargradientbrush, :: Create

Crée un Cd2dlineargradientbrush,.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dlineargradientbrushdestroy"></a><a name="destroy"></a> Cd2dlineargradientbrush, ::D estroy

Détruit un objet Cd2dlineargradientbrush,.

```
virtual void Destroy();
```

## <a name="cd2dlineargradientbrushdetach"></a><a name="detach"></a> Cd2dlineargradientbrush, ::D Etach

Détache l’interface de ressource de l’objet

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dlineargradientbrushget"></a><a name="get"></a> Cd2dlineargradientbrush, :: obtient

Retourne l’interface ID2D1LinearGradientBrush

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1LinearGradientBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a> Cd2dlineargradientbrush, :: GetEndPoint

Récupère les coordonnées de fin du dégradé linéaire

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Valeur renvoyée

Coordonnées à deux dimensions de fin du dégradé linéaire, dans l’espace de coordonnées du pinceau

## <a name="cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a> Cd2dlineargradientbrush, :: GetStartPoint

Récupère les coordonnées de début du dégradé linéaire

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Valeur renvoyée

Coordonnées à deux dimensions de départ du dégradé linéaire, dans l’espace de coordonnées du pinceau

## <a name="cd2dlineargradientbrushm_lineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a> Cd2dlineargradientbrush, :: m_LinearGradientBrushProperties

Points de début et de fin du dégradé.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

## <a name="cd2dlineargradientbrushm_plineargradientbrush"></a><a name="m_plineargradientbrush"></a> Cd2dlineargradientbrush, :: m_pLinearGradientBrush

Pointeur vers un ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

## <a name="cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a> Cd2dlineargradientbrush, :: Operator ID2D1LinearGradientBrush *

Retourne l’interface ID2D1LinearGradientBrush

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1LinearGradientBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a> Cd2dlineargradientbrush, :: SetEndPoint

Définit les coordonnées de fin du dégradé linéaire dans l’espace de coordonnées du pinceau

```cpp
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Coordonnées à deux dimensions de fin du dégradé linéaire, dans l’espace de coordonnées du pinceau

## <a name="cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a> Cd2dlineargradientbrush, :: SetStartPoint

Définit les coordonnées de début du dégradé linéaire dans l’espace de coordonnées du pinceau

```cpp
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Coordonnées à deux dimensions de départ du dégradé linéaire, dans l’espace de coordonnées du pinceau

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
