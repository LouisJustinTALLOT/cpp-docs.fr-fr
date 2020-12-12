---
description: 'En savoir plus sur : classe CBitmapRenderTarget,'
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
ms.openlocfilehash: a7987651c988dcf7fcd4c4decf4a2bd474ab8619
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122679"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget, classe

Wrapper pour ID2D1BitmapRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget, :: CBitmapRenderTarget,](#cbitmaprendertarget)|Construit un objet CBitmapRenderTarget,.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget, :: Attach](#attach)|Attache l’interface cible de rendu existante à l’objet|
|[CBitmapRenderTarget, ::D Etach](#detach)|Détache l’interface de la cible de rendu de l’objet|
|[CBitmapRenderTarget, :: GetBitmap](#getbitmap)|Récupère l’image bitmap de cette cible de rendu. Le bitmap retourné peut être utilisé pour les opérations de dessin.|
|[CBitmapRenderTarget, :: GetBitmapRenderTarget](#getbitmaprendertarget)|Retourne l’interface ID2D1BitmapRenderTarget|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget, :: Operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|Retourne l’interface ID2D1BitmapRenderTarget|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget, :: m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Pointeur vers un objet ID2D1BitmapRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget,](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cbitmaprendertargetattach"></a><a name="attach"></a> CBitmapRenderTarget, :: Attach

Attache l’interface cible de rendu existante à l’objet

```cpp
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Interface cible de rendu existante. Ne peut pas être NULL

## <a name="cbitmaprendertargetcbitmaprendertarget"></a><a name="cbitmaprendertarget"></a> CBitmapRenderTarget, :: CBitmapRenderTarget,

Construit un objet CBitmapRenderTarget,.

```
CBitmapRenderTarget();
```

## <a name="cbitmaprendertargetdetach"></a><a name="detach"></a> CBitmapRenderTarget, ::D Etach

Détache l’interface de la cible de rendu de l’objet

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface de la cible de rendu détachée.

## <a name="cbitmaprendertargetgetbitmap"></a><a name="getbitmap"></a> CBitmapRenderTarget, :: GetBitmap

Récupère l’image bitmap de cette cible de rendu. Le bitmap retourné peut être utilisé pour les opérations de dessin.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Paramètres

*bitmap*<br/>
Lorsque cette méthode est retournée, contient l’image bitmap valide pour cette cible de rendu. Cette image bitmap peut être utilisée pour les opérations de dessin.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cbitmaprendertargetgetbitmaprendertarget"></a><a name="getbitmaprendertarget"></a> CBitmapRenderTarget, :: GetBitmapRenderTarget

Retourne l’interface ID2D1BitmapRenderTarget

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1BitmapRenderTarget ou NULL si l’objet n’est pas encore initialisé.

## <a name="cbitmaprendertargetm_pbitmaprendertarget"></a><a name="m_pbitmaprendertarget"></a> CBitmapRenderTarget, :: m_pBitmapRenderTarget

Pointeur vers un objet ID2D1BitmapRenderTarget.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

## <a name="cbitmaprendertargetoperator-id2d1bitmaprendertarget"></a><a name="operator_id2d1bitmaprendertarget_star"></a> CBitmapRenderTarget, :: Operator ID2D1BitmapRenderTarget *

Retourne l’interface ID2D1BitmapRenderTarget

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1BitmapRenderTarget ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
