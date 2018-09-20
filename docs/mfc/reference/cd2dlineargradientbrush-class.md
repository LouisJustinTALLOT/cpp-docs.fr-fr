---
title: Classe de CD2DLinearGradientBrush | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b33b49c818a290d5bcbae20864a4e73006dd1f01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403927"
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
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Construit un objet CD2DLinearGradientBrush.|
|[CD2DLinearGradientBrush :: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destructeur. Appelé lorsqu’un objet de pinceau de dégradé linéaire D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DLinearGradientBrush::Attach](#attach)|Attache existant à l’objet interface de la ressource|
|[CD2DLinearGradientBrush::Create](#create)|Crée un CD2DLinearGradientBrush. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLinearGradientBrush::Destroy](#destroy)|Détruit un objet CD2DLinearGradientBrush. (Substitue [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DLinearGradientBrush::Detach](#detach)|Détache l’interface de ressources de l’objet|
|[CD2DLinearGradientBrush::Get](#get)|Renvoie l’interface ID2D1LinearGradientBrush|
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Récupère les coordonnées de fin du dégradé linéaire|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Récupère les coordonnées de début du dégradé linéaire|
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Définit les coordonnées de fin du dégradé linéaire dans l’espace de coordonnées du pinceau|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Définit les coordonnées de début du dégradé linéaire dans l’espace de coordonnées du pinceau|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|Renvoie l’interface ID2D1LinearGradientBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Les points de début et fin du dégradé.|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Pointeur vers un ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="_dtorcd2dlineargradientbrush"></a>  CD2DLinearGradientBrush :: ~ CD2DLinearGradientBrush

Destructeur. Appelé lorsqu’un objet de pinceau de dégradé linéaire D2D est détruit.

```
virtual ~CD2DLinearGradientBrush();
```

##  <a name="attach"></a>  CD2DLinearGradientBrush::Attach

Attache existant à l’objet interface de la ressource

```
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource*<br/>
Interface de la ressource existante. Ne peut pas être NULL

##  <a name="cd2dlineargradientbrush"></a>  CD2DLinearGradientBrush::CD2DLinearGradientBrush

Construit un objet CD2DLinearGradientBrush.

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
Pointeur vers un tableau de structures de D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Une valeur supérieure ou égale à 1 qui spécifie le nombre de points de dégradé dans le tableau gradientStops.

*LinearGradientBrushProperties*<br/>
Les points de début et fin du dégradé.

*colorInterpolationGamma*<br/>
L’espace dans chacune des couleurs interpolation entre le dégradé est effectuée.

*extendMode*<br/>
Le comportement du dégradé en dehors de la plage [0,1] normalisée.

*pBrushProperties*<br/>
Un pointeur vers l’opacité et de la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

##  <a name="create"></a>  CD2DLinearGradientBrush::Create

Crée un CD2DLinearGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="destroy"></a>  CD2DLinearGradientBrush::Destroy

Détruit un objet CD2DLinearGradientBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLinearGradientBrush::Detach

Détache l’interface de ressources de l’objet

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface de la ressource détachée.

##  <a name="get"></a>  CD2DLinearGradientBrush::Get

Renvoie l’interface ID2D1LinearGradientBrush

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1LinearGradientBrush ou NULL si l’objet n’est pas encore initialisé.

##  <a name="getendpoint"></a>  CD2DLinearGradientBrush::GetEndPoint

Récupère les coordonnées de fin du dégradé linéaire

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Valeur de retour

Les coordonnées à deux dimensions de fin du dégradé linéaire, dans l’espace de coordonnées du pinceau

##  <a name="getstartpoint"></a>  CD2DLinearGradientBrush::GetStartPoint

Récupère les coordonnées de début du dégradé linéaire

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Valeur de retour

Les coordonnées à deux dimensions de début du dégradé linéaire, dans l’espace de coordonnées du pinceau

##  <a name="m_lineargradientbrushproperties"></a>  CD2DLinearGradientBrush::m_LinearGradientBrushProperties

Les points de début et fin du dégradé.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

##  <a name="m_plineargradientbrush"></a>  CD2DLinearGradientBrush::m_pLinearGradientBrush

Pointeur vers un ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

##  <a name="operator_id2d1lineargradientbrush_star"></a>  CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *

Renvoie l’interface ID2D1LinearGradientBrush

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1LinearGradientBrush ou NULL si l’objet n’est pas encore initialisé.

##  <a name="setendpoint"></a>  CD2DLinearGradientBrush::SetEndPoint

Définit les coordonnées de fin du dégradé linéaire dans l’espace de coordonnées du pinceau

```
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Les coordonnées à deux dimensions de fin du dégradé linéaire, dans l’espace de coordonnées du pinceau

##  <a name="setstartpoint"></a>  CD2DLinearGradientBrush::SetStartPoint

Définit les coordonnées de début du dégradé linéaire dans l’espace de coordonnées du pinceau

```
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Les coordonnées à deux dimensions de début du dégradé linéaire, dans l’espace de coordonnées du pinceau

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
