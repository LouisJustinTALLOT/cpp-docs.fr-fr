---
title: CD2DGradientBrush, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
ms.openlocfilehash: f49a3a1a1aaebed47b05bf003926379c6f0b8102
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290974"
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush, classe

La classe de base des classes CD2DRadialGradientBrush et le CD2DLinearGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|Construit un objet CD2DGradientBrush.|
|[CD2DGradientBrush::~CD2DGradientBrush](#cd2dgradientbrush__~cd2dgradientbrush)|Destructeur. Appelé lorsqu’un objet de pinceau de dégradé D2D est détruit.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DGradientBrush::Destroy](#destroy)|Détruit un objet CD2DGradientBrush. (Substitue [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|Tableau des structures D2D1_GRADIENT_STOP.|
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|L’espace dans chacune des couleurs interpolation entre le dégradé est effectuée.|
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|Le comportement du dégradé en dehors de la plage [0,1] normalisée.|
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|Pointeur vers un tableau de structures de D2D1_GRADIENT_STOP.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget.h

##  <a name="_dtorcd2dgradientbrush"></a>  CD2DGradientBrush::~CD2DGradientBrush

Destructeur. Appelé lorsqu’un objet de pinceau de dégradé D2D est détruit.

```
virtual ~CD2DGradientBrush();
```

##  <a name="cd2dgradientbrush"></a>  CD2DGradientBrush::CD2DGradientBrush

Construit un objet CD2DGradientBrush.

```
CD2DGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
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

*colorInterpolationGamma*<br/>
L’espace dans chacune des couleurs interpolation entre le dégradé est effectuée.

*extendMode*<br/>
Le comportement du dégradé en dehors de la plage [0,1] normalisée.

*pBrushProperties*<br/>
Un pointeur vers l’opacité et de la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

##  <a name="destroy"></a>  CD2DGradientBrush::Destroy

Détruit un objet CD2DGradientBrush.

```
virtual void Destroy();
```

##  <a name="m_argradientstops"></a>  CD2DGradientBrush::m_arGradientStops

Tableau des structures D2D1_GRADIENT_STOP.

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

##  <a name="m_colorinterpolationgamma"></a>  CD2DGradientBrush::m_colorInterpolationGamma

L’espace dans chacune des couleurs interpolation entre le dégradé est effectuée.

```
D2D1_GAMMA m_colorInterpolationGamma;
```

##  <a name="m_extendmode"></a>  CD2DGradientBrush::m_extendMode

Le comportement du dégradé en dehors de la plage [0,1] normalisée.

```
D2D1_EXTEND_MODE m_extendMode;
```

##  <a name="m_pgradientstops"></a>  CD2DGradientBrush::m_pGradientStops

Pointeur vers un tableau de structures de D2D1_GRADIENT_STOP.

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
