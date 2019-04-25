---
title: CDCRenderTarget, classe
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 70169d2b89d9ea657898f7a96dea27556023d4e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168171"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget, classe

Wrapper pour ID2D1DCRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Construit un objet CDCRenderTarget.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget::Attach](#attach)|Interface de cible à l’objet de rendu attache existant|
|[CDCRenderTarget::BindDC](#binddc)|Lie la cible de rendu pour le contexte de périphérique auquel il émet des commandes de dessin|
|[CDCRenderTarget::Create](#create)|Crée un CDCRenderTarget.|
|[CDCRenderTarget::Detach](#detach)|Détache l’interface de cible de rendu de l’objet|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Renvoie l’interface ID2D1DCRenderTarget|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget::operator ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|Renvoie l’interface ID2D1DCRenderTarget|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Pointeur vers un objet ID2D1DCRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="attach"></a>  CDCRenderTarget::Attach

Interface de cible à l’objet de rendu attache existant

```
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Interface de cible de rendu existante. Ne peut pas être NULL

##  <a name="binddc"></a>  CDCRenderTarget::BindDC

Lie la cible de rendu pour le contexte de périphérique auquel il émet des commandes de dessin

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*dc*<br/>
Le contexte de périphérique pour lequel la cible de rendu émet des commandes de dessin

*rect*<br/>
Les dimensions de la poignée pour un contexte de périphérique (HDC) auquel est liée la cible de rendu

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne TRUE. Sinon, elle retourne FALSE.

##  <a name="cdcrendertarget"></a>  CDCRenderTarget::CDCRenderTarget

Construit un objet CDCRenderTarget.

```
CDCRenderTarget();
```

##  <a name="create"></a>  CDCRenderTarget::Create

Crée un CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Paramètres

*props*<br/>
Le mode de rendu, format de pixel, options de communication à distance, informations PPP et la prise en charge DirectX minimale requise pour le rendu matériel.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne TRUE. Sinon, elle retourne FALSE.

##  <a name="detach"></a>  CDCRenderTarget::Detach

Détache l’interface de cible de rendu de l’objet

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Valeur de retour

Interface de cible de rendu de pointeur vers détachée.

##  <a name="getdcrendertarget"></a>  CDCRenderTarget::GetDCRenderTarget

Renvoie l’interface ID2D1DCRenderTarget

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1DCRenderTarget ou NULL si l’objet n’est pas encore initialisé.

##  <a name="m_pdcrendertarget"></a>  CDCRenderTarget::m_pDCRenderTarget

Pointeur vers un objet ID2D1DCRenderTarget.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

##  <a name="operator_id2d1dcrendertarget_star"></a>  CDCRenderTarget::operator ID2D1DCRenderTarget*

Renvoie l’interface ID2D1DCRenderTarget

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1DCRenderTarget ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
