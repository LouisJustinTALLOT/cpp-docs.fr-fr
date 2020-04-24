---
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
ms.openlocfilehash: d87cdae5c24eae391be8db2fcdd04f91d592e427
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753158"
---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush, classe

Un emballage pour ID2D1LinearGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Construit un objet CD2DLinearGradientBrush.|
|[CD2DLinearGradientBrush: CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destructeur. Appelé lorsqu’un objet de brosse de gradient linéaire D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DLinearGradientBrush::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DLinearGradientBrush::Créer](#create)|Crée un pinceau CD2DLinearGradientBrush. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLinearGradientBrush::Destroy](#destroy)|Détruit un objet CD2DLinearGradientBrush. (Overrides [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DLinearGradientBrush::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DLinearGradientBrush::Get](#get)|Retourne l’interface ID2D1LinearGradientBrush|
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Récupère les coordonnées de fin du gradient linéaire|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Récupère les coordonnées de départ du gradient linéaire|
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Définit les coordonnées de fin du gradient linéaire dans l’espace de coordonnées de la brosse|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Définit les coordonnées de départ du gradient linéaire dans l’espace de coordonnées du pinceau|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DLinearGradientBrush::opérateur ID2D1LinearGradientBrush](#operator_id2d1lineargradientbrush_star)|Retourne l’interface ID2D1LinearGradientBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Les points de départ et de fin du gradient.|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Un pointeur à un ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush (en anglais)](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush: CD2DLinearGradientBrush

Destructeur. Appelé lorsqu’un objet de brosse de gradient linéaire D2D est détruit.

```
virtual ~CD2DLinearGradientBrush();
```

## <a name="cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2DLinearGradientBrush::Attach

Attache l’interface de ressources existante à l’objet

```cpp
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Impossible d’être NULL

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush

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
Un pointeur à la cible de rendu.

*gradientStops*<br/>
Un pointeur à un tableau de structures D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Une valeur supérieure ou égale à 1 qui spécifie le nombre d’arrêts de gradient dans le tableau gradientStops.

*LinéaireGradientBrushProperties*<br/>
Les points de départ et de fin du gradient.

*couleurInterpolationGamma*<br/>
L’espace dans lequel l’interpolation des couleurs entre les arrêts de gradient est effectuée.

*extendMode*<br/>
Le comportement du gradient en dehors de la gamme normalisée [0,1].

*pBrushProperties (en)*<br/>
Un pointeur à l’opacité et à la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2DLinearGradientBrush::Créer

Crée un pinceau CD2DLinearGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2DLinearGradientBrush::Destroy

Détruit un objet CD2DLinearGradientBrush.

```
virtual void Destroy();
```

## <a name="cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2DLinearGradientBrush::Detach

Détache l’interface des ressources de l’objet

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dlineargradientbrushget"></a><a name="get"></a>CD2DLinearGradientBrush::Get

Retourne l’interface ID2D1LinearGradientBrush

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1LinearGradientBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint

Récupère les coordonnées de fin du gradient linéaire

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Valeur de retour

Les coordonnées bidimensionnelles de fin du gradient linéaire, dans l’espace de coordonnées de la brosse

## <a name="cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint

Récupère les coordonnées de départ du gradient linéaire

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Valeur de retour

Les coordonnées bidimensionnelles de départ du gradient linéaire, dans l’espace de coordonnées de la brosse

## <a name="cd2dlineargradientbrushm_lineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties

Les points de départ et de fin du gradient.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

## <a name="cd2dlineargradientbrushm_plineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush

Un pointeur à un ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

## <a name="cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::opérateur ID2D1LinearGradientBrush

Retourne l’interface ID2D1LinearGradientBrush

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1LinearGradientBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint

Définit les coordonnées de fin du gradient linéaire dans l’espace de coordonnées de la brosse

```cpp
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Les coordonnées bidimensionnelles de fin du gradient linéaire, dans l’espace de coordonnées de la brosse

## <a name="cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint

Définit les coordonnées de départ du gradient linéaire dans l’espace de coordonnées du pinceau

```cpp
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Les coordonnées bidimensionnelles de départ du gradient linéaire, dans l’espace de coordonnées de la brosse

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
