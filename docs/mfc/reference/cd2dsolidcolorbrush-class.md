---
description: 'En savoir plus sur : classe Cd2dsolidcolorbrush,'
title: CD2DSolidColorBrush, classe
ms.date: 03/27/2019
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
ms.openlocfilehash: 57df3732a3c4239af6d9121426aa272c6f58417d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154602"
---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush, classe

Wrapper pour ID2D1SolidColorBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dsolidcolorbrush, :: Cd2dsolidcolorbrush,](#cd2dsolidcolorbrush)|Surchargé. Construit un objet Cd2dsolidcolorbrush,.|
|[Cd2dsolidcolorbrush, :: ~ Cd2dsolidcolorbrush,](#_dtorcd2dsolidcolorbrush)|Destructeur. Appelé lorsqu’un objet pinceau plein D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dsolidcolorbrush, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dsolidcolorbrush, :: Create](#create)|Crée un Cd2dsolidcolorbrush,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dsolidcolorbrush, ::D estroy](#destroy)|Détruit un objet Cd2dsolidcolorbrush,. (Substitue [CD2DBrush, ::D estroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[Cd2dsolidcolorbrush, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dsolidcolorbrush, :: obtient](#get)|Retourne l’interface ID2D1SolidColorBrush|
|[Cd2dsolidcolorbrush, :: GetColor](#getcolor)|Récupère la couleur du pinceau de couleur unie|
|[Cd2dsolidcolorbrush, :: SetColor](#setcolor)|Spécifie la couleur de ce pinceau de couleur unie|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dsolidcolorbrush, :: Operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|Retourne l’interface ID2D1SolidColorBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dsolidcolorbrush, :: m_colorSolid](#m_colorsolid)|Couleur unie du pinceau.|
|[Cd2dsolidcolorbrush, :: m_pSolidColorBrush](#m_psolidcolorbrush)|Stocke un pointeur vers un objet ID2D1SolidColorBrush.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

[Cd2dbrush,](../../mfc/reference/cd2dbrush-class.md)

[Cd2dsolidcolorbrush,](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a> Cd2dsolidcolorbrush, :: ~ Cd2dsolidcolorbrush,

Destructeur. Appelé lorsqu’un objet pinceau plein D2D est détruit.

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a> Cd2dsolidcolorbrush, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas être NULL

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a> Cd2dsolidcolorbrush, :: Cd2dsolidcolorbrush,

Construit un objet Cd2dsolidcolorbrush,.

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*color*<br/>
Les valeurs rouge, vert, bleu et alpha de la couleur du pinceau.

*pBrushProperties*<br/>
Pointeur vers l’opacité et la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

*nAlpha*<br/>
Opacité de la couleur du pinceau.

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a> Cd2dsolidcolorbrush, :: Create

Crée un Cd2dsolidcolorbrush,.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a> Cd2dsolidcolorbrush, ::D estroy

Détruit un objet Cd2dsolidcolorbrush,.

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a> Cd2dsolidcolorbrush, ::D Etach

Détache l’interface de ressource de l’objet

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a> Cd2dsolidcolorbrush, :: obtient

Retourne l’interface ID2D1SolidColorBrush

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1SolidColorBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a> Cd2dsolidcolorbrush, :: GetColor

Récupère la couleur du pinceau de couleur unie

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Couleur de ce pinceau de couleur unie

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a> Cd2dsolidcolorbrush, :: m_colorSolid

Couleur unie du pinceau.

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a> Cd2dsolidcolorbrush, :: m_pSolidColorBrush

Stocke un pointeur vers un objet ID2D1SolidColorBrush.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a> Cd2dsolidcolorbrush, :: Operator ID2D1SolidColorBrush *

Retourne l’interface ID2D1SolidColorBrush

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1SolidColorBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a> Cd2dsolidcolorbrush, :: SetColor

Spécifie la couleur de ce pinceau de couleur unie

```cpp
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
Couleur de ce pinceau de couleur unie

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
