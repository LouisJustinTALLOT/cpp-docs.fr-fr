---
title: CBitmapRenderTarget, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee70825711efd82ce451a0433a63d98d93850552
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417057"
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
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Construit un objet CBitmapRenderTarget.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget::Attach](#attach)|Interface de cible à l’objet de rendu attache existant|
|[CBitmapRenderTarget::Detach](#detach)|Détache l’interface de cible de rendu de l’objet|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Récupère l’image bitmap de cette cible de rendu. La bitmap retournée peut être utilisée pour les opérations de dessin.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Renvoie l’interface ID2D1BitmapRenderTarget|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|Renvoie l’interface ID2D1BitmapRenderTarget|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Pointeur vers un objet ID2D1BitmapRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="attach"></a>  CBitmapRenderTarget::Attach

Interface de cible à l’objet de rendu attache existant

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Interface de cible de rendu existante. Ne peut pas être NULL

##  <a name="cbitmaprendertarget"></a>  CBitmapRenderTarget::CBitmapRenderTarget

Construit un objet CBitmapRenderTarget.

```
CBitmapRenderTarget();
```

##  <a name="detach"></a>  CBitmapRenderTarget::Detach

Détache l’interface de cible de rendu de l’objet

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Valeur de retour

Interface de cible de rendu de pointeur vers détachée.

##  <a name="getbitmap"></a>  CBitmapRenderTarget::GetBitmap

Récupère l’image bitmap de cette cible de rendu. La bitmap retournée peut être utilisée pour les opérations de dessin.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Paramètres

*bitmap*<br/>
Lorsque cette méthode est retournée, contient l’image bitmap valide pour cette cible de rendu. Cette image bitmap peut être utilisée pour les opérations de dessin.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne TRUE. Sinon, elle retourne FALSE.

##  <a name="getbitmaprendertarget"></a>  CBitmapRenderTarget::GetBitmapRenderTarget

Renvoie l’interface ID2D1BitmapRenderTarget

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1BitmapRenderTarget ou NULL si l’objet n’est pas encore initialisé.

##  <a name="m_pbitmaprendertarget"></a>  CBitmapRenderTarget::m_pBitmapRenderTarget

Pointeur vers un objet ID2D1BitmapRenderTarget.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

##  <a name="operator_id2d1bitmaprendertarget_star"></a>  CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *

Renvoie l’interface ID2D1BitmapRenderTarget

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1BitmapRenderTarget ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
