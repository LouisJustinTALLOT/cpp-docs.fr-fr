---
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
ms.openlocfilehash: d03fb6f398e18957f68fc18c78d8a397efc67506
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369280"
---
# <a name="cd2dbrush-class"></a>CD2DBrush, classe

Un emballage pour ID2D1Brush.

## <a name="syntax"></a>Syntaxe

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Construit un objet CD2DBrush.|
|[CD2DBrush: :CD2DBrush](#_dtorcd2dbrush)|Destructeur. Appelé quand un objet de brosse D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DBrush::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DBrush::Destroy](#destroy)|Détruit un objet CD2DBrush. (Overrides [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBrush::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DBrush::Get](#get)|Retourne l’interface ID2D1Brush|
|[CD2DBrush::GetOpacity](#getopacity)|Obtient le degré d’opacité de ce pinceau|
|[CD2DBrush::GetTransform](#gettransform)|Obtient la transformation actuelle de la cible de rendu|
|[CD2DBrush::IsValid](#isvalid)|Vérifie la validité des ressources (Overrides [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DBrush::SetOpacity](#setopacity)|Définit le degré d’opacité de ce pinceau|
|[CD2DBrush::SetTransform](#settransform)|Applique la transformation spécifiée à la cible de rendu, remplaçant la transformation existante. Toutes les opérations de dessin subséquentes se déroulent dans l’espace transformé|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBrush::opérateur ID2D1Brush](#operator_id2d1brush_star)|Retourne l’interface ID2D1Brush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|Stocke un pointeur sur un objet ID2D1Brush.|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Propriétés de brosse.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a>CD2DBrush: :CD2DBrush

Destructeur. Appelé quand un objet de brosse D2D est détruit.

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a>CD2DBrush::Attach

Attache l’interface de ressources existante à l’objet.

```
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Ne peut pas avoir la valeur NULL.

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a>CD2DBrush::CD2DBrush

Construit un objet CD2DBrush.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Un pointeur à la cible de rendu.

*pBrushProperties (en)*<br/>
Un pointeur à l’opacité et à la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a>CD2DBrush::Destroy

Détruit un objet CD2DBrush.

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a>CD2DBrush::Detach

Détache l’interface des ressources de l’objet.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dbrushget"></a><a name="get"></a>CD2DBrush::Get

Retourne l’interface ID2D1Brush

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Brush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a>CD2DBrush::GetOpacity

Obtient le degré d’opacité de ce pinceau

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur comprise entre zéro et 1 qui indique l’opacité du pinceau. Cette valeur est un multiplicateur constant qui échelle linéairement la valeur alpha de tous les pixels remplis par le pinceau. Les valeurs d’opacité sont serrées dans la gamme 0 à 1 avant qu’elles ne soient multipliées ensemble.

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a>CD2DBrush::GetTransform

Obtient la transformation actuelle de la cible de rendu

```
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>Paramètres

*transform*<br/>
Lorsque cela revient, contient la transformation actuelle de la cible de rendu. Ce paramètre est passé non initialisé.

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a>CD2DBrush::IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la ressource est valide; autrement FALSE.

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a>CD2DBrush::m_pBrush

Stocke un pointeur sur un objet ID2D1Brush.

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a>CD2DBrush::m_pBrushProperties

Propriétés de brosse.

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a>CD2DBrush::opérateur ID2D1Brush

Retourne l’interface ID2D1Brush

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Brush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a>CD2DBrush::SetOpacity

Définit le degré d’opacité de ce pinceau

```
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>Paramètres

*Opacité*<br/>
Une valeur comprise entre zéro et 1 qui indique l’opacité du pinceau. Cette valeur est un multiplicateur constant qui échelle linéairement la valeur alpha de tous les pixels remplis par le pinceau. Les valeurs d’opacité sont serrées dans la gamme 0 à 1 avant qu’elles ne soient multipliées ensemble.

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a>CD2DBrush::SetTransform

Applique la transformation spécifiée à la cible de rendu, remplaçant la transformation existante. Toutes les opérations de dessin ultérieures se produisent dans l’espace transformé.

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>Paramètres

*transform*<br/>
La transformation à appliquer à la cible de rendu

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
