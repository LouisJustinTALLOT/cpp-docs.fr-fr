---
description: 'En savoir plus sur : classe Cd2dgradientbrush,'
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
ms.openlocfilehash: c1af08ae27bd2cbee48c4abe22f413ffeb85cd1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193394"
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush, classe

Classe de base des classes Cd2dlineargradientbrush, et Cd2dradialgradientbrush,.

## <a name="syntax"></a>Syntaxe

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dgradientbrush, :: Cd2dgradientbrush,](#cd2dgradientbrush)|Construit un objet Cd2dgradientbrush,.|
|[Cd2dgradientbrush, :: ~ Cd2dgradientbrush,](#_dtorcd2dgradientbrush)|Destructeur. Appelé lorsqu’un objet pinceau de dégradé D2D est détruit.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[Cd2dgradientbrush, ::D estroy](#destroy)|Détruit un objet Cd2dgradientbrush,. (Substitue [CD2DBrush, ::D estroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dgradientbrush, :: m_arGradientStops](#m_argradientstops)|Tableau des structures de D2D1_GRADIENT_STOP.|
|[Cd2dgradientbrush, :: m_colorInterpolationGamma](#m_colorinterpolationgamma)|Espace dans lequel l’interpolation de couleur entre les arrêts de dégradé est effectuée.|
|[Cd2dgradientbrush, :: m_extendMode](#m_extendmode)|Comportement du dégradé en dehors de la plage normalisée [0, 1].|
|[Cd2dgradientbrush, :: m_pGradientStops](#m_pgradientstops)|Pointeur vers un tableau de structures D2D1_GRADIENT_STOP.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

[Cd2dbrush,](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="_dtorcd2dgradientbrush"></a> Cd2dgradientbrush, :: ~ Cd2dgradientbrush,

Destructeur. Appelé lorsqu’un objet pinceau de dégradé D2D est détruit.

```
virtual ~CD2DGradientBrush();
```

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="cd2dgradientbrush"></a> Cd2dgradientbrush, :: Cd2dgradientbrush,

Construit un objet Cd2dgradientbrush,.

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
Pointeur vers un tableau de structures D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Valeur supérieure ou égale à 1 qui spécifie le nombre de points de dégradé dans le tableau gradientStops.

*colorInterpolationGamma*<br/>
Espace dans lequel l’interpolation de couleur entre les arrêts de dégradé est effectuée.

*extendMode*<br/>
Comportement du dégradé en dehors de la plage normalisée [0, 1].

*pBrushProperties*<br/>
Pointeur vers l’opacité et la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dgradientbrushdestroy"></a><a name="destroy"></a> Cd2dgradientbrush, ::D estroy

Détruit un objet Cd2dgradientbrush,.

```
virtual void Destroy();
```

## <a name="cd2dgradientbrushm_argradientstops"></a><a name="m_argradientstops"></a> Cd2dgradientbrush, :: m_arGradientStops

Tableau des structures de D2D1_GRADIENT_STOP.

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

## <a name="cd2dgradientbrushm_colorinterpolationgamma"></a><a name="m_colorinterpolationgamma"></a> Cd2dgradientbrush, :: m_colorInterpolationGamma

Espace dans lequel l’interpolation de couleur entre les arrêts de dégradé est effectuée.

```
D2D1_GAMMA m_colorInterpolationGamma;
```

## <a name="cd2dgradientbrushm_extendmode"></a><a name="m_extendmode"></a> Cd2dgradientbrush, :: m_extendMode

Comportement du dégradé en dehors de la plage normalisée [0, 1].

```
D2D1_EXTEND_MODE m_extendMode;
```

## <a name="cd2dgradientbrushm_pgradientstops"></a><a name="m_pgradientstops"></a> Cd2dgradientbrush, :: m_pGradientStops

Pointeur vers un tableau de structures D2D1_GRADIENT_STOP.

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
