---
description: 'En savoir plus sur : classe CDCRenderTarget'
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
ms.openlocfilehash: 3959321bbd6274c821b1f02be5962b23ec9dbc95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185321"
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
|[CDCRenderTarget :: CDCRenderTarget](#cdcrendertarget)|Construit un objet CDCRenderTarget.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget :: Attach](#attach)|Attache l’interface cible de rendu existante à l’objet|
|[CDCRenderTarget :: BindDC](#binddc)|Lie la cible de rendu au contexte de périphérique dans lequel elle émet des commandes de dessin|
|[CDCRenderTarget :: Create](#create)|Crée un CDCRenderTarget.|
|[CDCRenderTarget ::D Etach](#detach)|Détache l’interface de la cible de rendu de l’objet|
|[CDCRenderTarget :: GetDCRenderTarget](#getdcrendertarget)|Retourne l’interface ID2D1DCRenderTarget|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget :: Operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|Retourne l’interface ID2D1DCRenderTarget|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget :: m_pDCRenderTarget](#m_pdcrendertarget)|Pointeur vers un objet ID2D1DCRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget,](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cdcrendertargetattach"></a><a name="attach"></a> CDCRenderTarget :: Attach

Attache l’interface cible de rendu existante à l’objet

```cpp
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Interface cible de rendu existante. Ne peut pas être NULL

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a> CDCRenderTarget :: BindDC

Lie la cible de rendu au contexte de périphérique dans lequel elle émet des commandes de dessin

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*métafichier*<br/>
Contexte de périphérique dans lequel la cible de rendu émet des commandes de dessin

*rectangulaire*<br/>
Dimensions du handle d’un contexte de périphérique (HDC) auquel la cible de rendu est liée

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a> CDCRenderTarget :: CDCRenderTarget

Construit un objet CDCRenderTarget.

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a> CDCRenderTarget :: Create

Crée un CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Paramètres

*props*<br/>
Le mode de rendu, le format de pixel, les options de communication à distance, les informations PPP et la prise en charge minimale de DirectX requise pour le rendu matériel.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cdcrendertargetdetach"></a><a name="detach"></a> CDCRenderTarget ::D Etach

Détache l’interface de la cible de rendu de l’objet

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface de la cible de rendu détachée.

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a> CDCRenderTarget :: GetDCRenderTarget

Retourne l’interface ID2D1DCRenderTarget

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1DCRenderTarget ou NULL si l’objet n’est pas encore initialisé.

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a> CDCRenderTarget :: m_pDCRenderTarget

Pointeur vers un objet ID2D1DCRenderTarget.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a> CDCRenderTarget :: Operator ID2D1DCRenderTarget *

Retourne l’interface ID2D1DCRenderTarget

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1DCRenderTarget ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
