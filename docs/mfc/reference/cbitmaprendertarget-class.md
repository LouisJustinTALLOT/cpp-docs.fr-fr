---
title: CBitmapRenderTarget, classe
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: 8ba8c8819b47185315d67d732fc90ab2ffc0ad0a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752934"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget, classe

Un emballage pour ID2D1BitmapRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Construit un objet CBitmapRenderTarget.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget::Attach](#attach)|Attache l’interface cible de rendu existante à l’objet|
|[CBitmapRenderTarget::Detach](#detach)|Les détaches rendent l’interface cible de l’objet|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Récupère la bitmap pour cette cible de rendu. Le bitmap retourné peut être utilisé pour les opérations de dessin.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Retourne l’interface ID2D1BitmapRenderTarget|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget::opérateur ID2D1BitmapRenderTarget](#operator_id2d1bitmaprendertarget_star)|Retourne l’interface ID2D1BitmapRenderTarget|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Un pointeur à un objet ID2D1BitmapRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cbitmaprendertargetattach"></a><a name="attach"></a>CBitmapRenderTarget::Attach

Attache l’interface cible de rendu existante à l’objet

```cpp
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Interface cible de rendu existante. Impossible d’être NULL

## <a name="cbitmaprendertargetcbitmaprendertarget"></a><a name="cbitmaprendertarget"></a>CBitmapRenderTarget::CBitmapRenderTarget

Construit un objet CBitmapRenderTarget.

```
CBitmapRenderTarget();
```

## <a name="cbitmaprendertargetdetach"></a><a name="detach"></a>CBitmapRenderTarget::Detach

Les détaches rendent l’interface cible de l’objet

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur pour rendre détaché l’interface cible.

## <a name="cbitmaprendertargetgetbitmap"></a><a name="getbitmap"></a>CBitmapRenderTarget::GetBitmap

Récupère la bitmap pour cette cible de rendu. Le bitmap retourné peut être utilisé pour les opérations de dessin.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Paramètres

*Bitmap*<br/>
Lorsque cette méthode revient, contient la bitmap valide pour cette cible de rendu. Cette bitmap peut être utilisée pour les opérations de dessin.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cbitmaprendertargetgetbitmaprendertarget"></a><a name="getbitmaprendertarget"></a>CBitmapRenderTarget::GetBitmapRenderTarget

Retourne l’interface ID2D1BitmapRenderTarget

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1BitmapRenderTarget ou NULL si l’objet n’est pas encore paralysé.

## <a name="cbitmaprendertargetm_pbitmaprendertarget"></a><a name="m_pbitmaprendertarget"></a>CBitmapRenderTarget::m_pBitmapRenderTarget

Un pointeur à un objet ID2D1BitmapRenderTarget.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

## <a name="cbitmaprendertargetoperator-id2d1bitmaprendertarget"></a><a name="operator_id2d1bitmaprendertarget_star"></a>CBitmapRenderTarget::opérateur ID2D1BitmapRenderTarget

Retourne l’interface ID2D1BitmapRenderTarget

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1BitmapRenderTarget ou NULL si l’objet n’est pas encore paralysé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
