---
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
ms.openlocfilehash: 5aa3d7688046b0c1b04983f2d27fe5579dd7c680
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369060"
---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush, classe

Un emballage pour ID2D1SolidColorBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Surchargé. Construit un objet CD2DSolidColorBrush.|
|[CD2DSolidColorBrush: CD2DSolidColorBrush](#_dtorcd2dsolidcolorbrush)|Destructeur. Appelé quand un objet de brosse solide D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DSolidColorBrush::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DSolidColorBrush::Créer](#create)|Crée un cd2DSolidColorBrush. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DSolidColorBrush::Destroy](#destroy)|Détruit un objet CD2DSolidColorBrush. (Overrides [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DSolidColorBrush::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DSolidColorBrush::Get](#get)|Retourne l’interface ID2D1SolidColorBrush|
|[CD2DSolidColorBrush::GetColor](#getcolor)|Récupère la couleur de la brosse couleur solide|
|[CD2DSolidColorBrush::SetColor](#setcolor)|Specifie la couleur de cette brosse à couleurs solides|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DSolidColorBrush::opérateur ID2D1SolidColorBrush](#operator_id2d1solidcolorbrush_star)|Retourne l’interface ID2D1SolidColorBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Brossez la couleur solide.|
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Stocke un pointeur sur un objet ID2D1SolidColorBrush.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush (en anglais)](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a>CD2DSolidColorBrush: CD2DSolidColorBrush

Destructeur. Appelé quand un objet de brosse solide D2D est détruit.

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a>CD2DSolidColorBrush::Attach

Attache l’interface de ressources existante à l’objet

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Impossible d’être NULL

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a>CD2DSolidColorBrush::CD2DSolidColorBrush

Construit un objet CD2DSolidColorBrush.

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
Un pointeur à la cible de rendu.

*Couleur*<br/>
Les valeurs rouges, vertes, bleues et alpha de la couleur du pinceau.

*pBrushProperties (en)*<br/>
Un pointeur à l’opacité et à la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

*nAlpha*<br/>
L’opacité de la couleur du pinceau.

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a>CD2DSolidColorBrush::Créer

Crée un cd2DSolidColorBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a>CD2DSolidColorBrush::Destroy

Détruit un objet CD2DSolidColorBrush.

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a>CD2DSolidColorBrush::Detach

Détache l’interface des ressources de l’objet

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a>CD2DSolidColorBrush::Get

Retourne l’interface ID2D1SolidColorBrush

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1SolidColorBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a>CD2DSolidColorBrush::GetColor

Récupère la couleur de la brosse couleur solide

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur de cette brosse à couleurs solides

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a>CD2DSolidColorBrush::m_colorSolid

Brossez la couleur solide.

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a>CD2DSolidColorBrush::m_pSolidColorBrush

Stocke un pointeur sur un objet ID2D1SolidColorBrush.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a>CD2DSolidColorBrush::opérateur ID2D1SolidColorBrush

Retourne l’interface ID2D1SolidColorBrush

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1SolidColorBrush ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a>CD2DSolidColorBrush::SetColor

Specifie la couleur de cette brosse à couleurs solides

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
La couleur de cette brosse à couleurs solides

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
