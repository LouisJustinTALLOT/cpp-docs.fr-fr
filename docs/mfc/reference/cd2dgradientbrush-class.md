---
title: CD2DGradientBrush, classe
ms.date: 03/27/2019
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
ms.openlocfilehash: 861bc32382737bd6482a3d51eb8470bf834e8508
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369229"
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush, classe

La classe de base des cours CD2DLinearGradientBrush et CD2DRadialGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|Construit un objet CD2DGradientBrush.|
|[CD2DGradientBrush: CD2DGradientBrush](#_dtorcd2dgradientbrush)|Destructeur. Appelé quand un objet de brosse de gradient D2D est détruit.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DGradientBrush::Destroy](#destroy)|Détruit un objet CD2DGradientBrush. (Overrides [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|Array des structures D2D1_GRADIENT_STOP.|
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|L’espace dans lequel l’interpolation des couleurs entre les arrêts de gradient est effectuée.|
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|Le comportement du gradient en dehors de la gamme normalisée [0,1].|
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|Un pointeur à un tableau de structures D2D1_GRADIENT_STOP.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush (en anglais)](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="_dtorcd2dgradientbrush"></a>CD2DGradientBrush: CD2DGradientBrush

Destructeur. Appelé quand un objet de brosse de gradient D2D est détruit.

```
virtual ~CD2DGradientBrush();
```

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="cd2dgradientbrush"></a>CD2DGradientBrush::CD2DGradientBrush

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
Un pointeur à la cible de rendu.

*gradientStops*<br/>
Un pointeur à un tableau de structures D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Une valeur supérieure ou égale à 1 qui spécifie le nombre d’arrêts de gradient dans le tableau gradientStops.

*couleurInterpolationGamma*<br/>
L’espace dans lequel l’interpolation des couleurs entre les arrêts de gradient est effectuée.

*extendMode*<br/>
Le comportement du gradient en dehors de la gamme normalisée [0,1].

*pBrushProperties (en)*<br/>
Un pointeur à l’opacité et à la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dgradientbrushdestroy"></a><a name="destroy"></a>CD2DGradientBrush::Destroy

Détruit un objet CD2DGradientBrush.

```
virtual void Destroy();
```

## <a name="cd2dgradientbrushm_argradientstops"></a><a name="m_argradientstops"></a>CD2DGradientBrush::m_arGradientStops

Array des structures D2D1_GRADIENT_STOP.

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

## <a name="cd2dgradientbrushm_colorinterpolationgamma"></a><a name="m_colorinterpolationgamma"></a>CD2DGradientBrush::m_colorInterpolationGamma

L’espace dans lequel l’interpolation des couleurs entre les arrêts de gradient est effectuée.

```
D2D1_GAMMA m_colorInterpolationGamma;
```

## <a name="cd2dgradientbrushm_extendmode"></a><a name="m_extendmode"></a>CD2DGradientBrush::m_extendMode

Le comportement du gradient en dehors de la gamme normalisée [0,1].

```
D2D1_EXTEND_MODE m_extendMode;
```

## <a name="cd2dgradientbrushm_pgradientstops"></a><a name="m_pgradientstops"></a>CD2DGradientBrush::m_pGradientStops

Un pointeur à un tableau de structures D2D1_GRADIENT_STOP.

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
