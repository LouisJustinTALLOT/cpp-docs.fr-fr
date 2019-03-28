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
ms.openlocfilehash: f225198193443c11d0294010a5fb71858514c81e
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565410"
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
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Surchargé. Construit un objet CD2DSolidColorBrush.|
|[CD2DSolidColorBrush::~CD2DSolidColorBrush](#_dtorcd2dsolidcolorbrush)|Destructeur. Appelé lorsqu’un objet de pinceau uni D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DSolidColorBrush::Attach](#attach)|Attache existant à l’objet interface de la ressource|
|[CD2DSolidColorBrush::Create](#create)|Crée un CD2DSolidColorBrush. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DSolidColorBrush::Destroy](#destroy)|Détruit un objet CD2DSolidColorBrush. (Substitue [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DSolidColorBrush::Detach](#detach)|Détache l’interface de ressources de l’objet|
|[CD2DSolidColorBrush::Get](#get)|Renvoie l’interface ID2D1SolidColorBrush|
|[CD2DSolidColorBrush::GetColor](#getcolor)|Récupère la couleur du pinceau couleur unie|
|[CD2DSolidColorBrush::SetColor](#setcolor)|Spécifie la couleur de ce pinceau de couleur unie|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush*](#operator_id2d1solidcolorbrush_star)|Renvoie l’interface ID2D1SolidColorBrush|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Pinceau de couleur unie.|
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Stocke un pointeur vers un objet ID2D1SolidColorBrush.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="_dtorcd2dsolidcolorbrush"></a>  CD2DSolidColorBrush::~CD2DSolidColorBrush

Destructeur. Appelé lorsqu’un objet de pinceau uni D2D est détruit.

```
virtual ~CD2DSolidColorBrush();
```

##  <a name="attach"></a>  CD2DSolidColorBrush::Attach

Attache existant à l’objet interface de la ressource

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource*<br/>
Interface de la ressource existante. Ne peut pas être NULL

##  <a name="cd2dsolidcolorbrush"></a>  CD2DSolidColorBrush::CD2DSolidColorBrush

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
Pointeur vers la cible de rendu.

*color*<br/>
Les valeurs rouges, verts, bleu et alphabétiques de la couleur du pinceau.

*pBrushProperties*<br/>
Un pointeur vers l’opacité et de la transformation d’un pinceau.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

*nAlpha*<br/>
L’opacité de la couleur du pinceau.

##  <a name="create"></a>  CD2DSolidColorBrush::Create

Crée un CD2DSolidColorBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="destroy"></a>  CD2DSolidColorBrush::Destroy

Détruit un objet CD2DSolidColorBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DSolidColorBrush::Detach

Détache l’interface de ressources de l’objet

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface de la ressource détachée.

##  <a name="get"></a>  CD2DSolidColorBrush::Get

Renvoie l’interface ID2D1SolidColorBrush

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1SolidColorBrush ou NULL si l’objet n’est pas encore initialisé.

##  <a name="getcolor"></a>  CD2DSolidColorBrush::GetColor

Récupère la couleur du pinceau couleur unie

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur de ce pinceau de couleur unie

##  <a name="m_colorsolid"></a>  CD2DSolidColorBrush::m_colorSolid

Pinceau de couleur unie.

```
D2D1_COLOR_F m_colorSolid;
```

##  <a name="m_psolidcolorbrush"></a>  CD2DSolidColorBrush::m_pSolidColorBrush

Stocke un pointeur vers un objet ID2D1SolidColorBrush.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

##  <a name="operator_id2d1solidcolorbrush_star"></a>  CD2DSolidColorBrush::operator ID2D1SolidColorBrush*

Renvoie l’interface ID2D1SolidColorBrush

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1SolidColorBrush ou NULL si l’objet n’est pas encore initialisé.

##  <a name="setcolor"></a>  CD2DSolidColorBrush::SetColor

Spécifie la couleur de ce pinceau de couleur unie

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
La couleur de ce pinceau de couleur unie

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
