---
description: 'En savoir plus sur : classe Cd2dbrush,'
title: CD2DBrush, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
ms.openlocfilehash: 6d19601258951a297a734aa304e2a22c98baf5c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227570"
---
# <a name="cd2dbrush-class"></a>CD2DBrush, classe

Wrapper pour ID2D1Brush.

## <a name="syntax"></a>Syntaxe

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dbrush, :: Cd2dbrush,](#cd2dbrush)|Construit un objet Cd2dbrush,.|
|[Cd2dbrush, :: ~ Cd2dbrush,](#_dtorcd2dbrush)|Destructeur. Appelé lorsqu’un objet Brush D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dbrush, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dbrush, ::D estroy](#destroy)|Détruit un objet Cd2dbrush,. (Substitue [CD2DResource, ::D estroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[Cd2dbrush, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dbrush, :: obtient](#get)|Retourne l’interface ID2D1Brush|
|[Cd2dbrush, :: GetOpacity](#getopacity)|Obtient le degré d’opacité de ce pinceau|
|[Cd2dbrush, :: GetTransform](#gettransform)|Obtient la transformation actuelle de la cible de rendu|
|[Cd2dbrush, :: IsValid](#isvalid)|Vérifie la validité des ressources (Substitue [CD2DResource, :: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[Cd2dbrush, :: SetOpacity](#setopacity)|Définit le degré d’opacité de ce pinceau|
|[Cd2dbrush, :: SetTransform](#settransform)|Applique la transformation spécifiée à la cible de rendu, en remplaçant la transformation existante. Toutes les opérations de dessin suivantes se produisent dans l’espace transformé|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dbrush, :: Operator ID2D1Brush *](#operator_id2d1brush_star)|Retourne l’interface ID2D1Brush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dbrush, :: m_pBrush](#m_pbrush)|Stocke un pointeur vers un objet ID2D1Brush.|
|[Cd2dbrush, :: m_pBrushProperties](#m_pbrushproperties)|Propriétés de pinceau.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a> Cd2dbrush, :: ~ Cd2dbrush,

Destructeur. Appelé lorsqu’un objet Brush D2D est détruit.

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a> Cd2dbrush, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas avoir la valeur NULL.

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a> Cd2dbrush, :: Cd2dbrush,

Construit un objet Cd2dbrush,.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*pBrushProperties*<br/>
Pointeur vers l’opacité et la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a> Cd2dbrush, ::D estroy

Détruit un objet Cd2dbrush,.

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a> Cd2dbrush, ::D Etach

Détache l’interface de ressource de l’objet.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dbrushget"></a><a name="get"></a> Cd2dbrush, :: obtient

Retourne l’interface ID2D1Brush

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Brush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a> Cd2dbrush, :: GetOpacity

Obtient le degré d’opacité de ce pinceau

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur comprise entre zéro et 1 qui indique l’opacité du pinceau. Cette valeur est un multiplicateur de constante qui met à l’échelle de façon linéaire la valeur alpha de tous les pixels remplis par le pinceau. Les valeurs d’opacité sont ancrées dans la plage de 0 à 1 avant d’être multipliées ensemble.

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a> Cd2dbrush, :: GetTransform

Obtient la transformation actuelle de la cible de rendu

```cpp
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>Paramètres

*transform*<br/>
Lorsque cette valeur est retournée, contient la transformation actuelle de la cible de rendu. Ce paramètre est passé sans être initialisé.

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a> Cd2dbrush, :: IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la ressource est valide ; Sinon, FALSe.

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a> Cd2dbrush, :: m_pBrush

Stocke un pointeur vers un objet ID2D1Brush.

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a> Cd2dbrush, :: m_pBrushProperties

Propriétés de pinceau.

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a> Cd2dbrush, :: Operator ID2D1Brush *

Retourne l’interface ID2D1Brush

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Brush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a> Cd2dbrush, :: SetOpacity

Définit le degré d’opacité de ce pinceau

```cpp
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>Paramètres

*'*<br/>
Valeur comprise entre zéro et 1 qui indique l’opacité du pinceau. Cette valeur est un multiplicateur de constante qui met à l’échelle de façon linéaire la valeur alpha de tous les pixels remplis par le pinceau. Les valeurs d’opacité sont ancrées dans la plage de 0 à 1 avant d’être multipliées ensemble.

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a> Cd2dbrush, :: SetTransform

Applique la transformation spécifiée à la cible de rendu, en remplaçant la transformation existante. Toutes les opérations de dessin suivantes se produisent dans l’espace transformé.

```cpp
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>Paramètres

*transform*<br/>
Transformation à appliquer à la cible de rendu

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
