---
title: CHwndRenderTarget, classe
ms.date: 11/04/2016
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
ms.openlocfilehash: 439ff0152ec69575f21faa332d8fac4bbe779a16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551864"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget, classe

Wrapper pour ID2D1HwndRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Construit un objet CHwndRenderTarget de HWND.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|Interface de cible à l’objet de rendu attache existant|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Indique si le HWND associé à cette cible de rendu est bloqué.|
|[CHwndRenderTarget::Create](#create)|Crée une cible de rendu associée à la fenêtre|
|[CHwndRenderTarget::Detach](#detach)|Détache l’interface de cible de rendu de l’objet|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Retourne le HWND associé à cette cible de rendu.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Renvoie l’interface ID2D1HwndRenderTarget.|
|[CHwndRenderTarget::ReCreate](#recreate)|Crée de nouveau une cible de rendu associée à la fenêtre|
|[CHwndRenderTarget::Resize](#resize)|Modifie la taille de la cible de rendu à la taille de pixel spécifié|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|Renvoie l’interface ID2D1HwndRenderTarget.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Pointeur vers un objet ID2D1HwndRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="attach"></a>  CHwndRenderTarget::Attach

Interface de cible à l’objet de rendu attache existant

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Interface de cible de rendu existante. Ne peut pas être NULL

##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState

Indique si le HWND associé à cette cible de rendu est bloqué.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui indique si le HWND associé à cette cible de rendu est bloquée.

##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget

Construit un objet CHwndRenderTarget de HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Paramètres

*HWND*<br/>
Le HWND associé à cette cible de rendu

##  <a name="create"></a>  CHwndRenderTarget::Create

Crée une cible de rendu associée à la fenêtre

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Le HWND associé à cette cible de rendu

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne TRUE. Sinon, elle retourne FALSE

##  <a name="detach"></a>  CHwndRenderTarget::Detach

Détache l’interface de cible de rendu de l’objet

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Valeur de retour

Interface de cible de rendu de pointeur vers détachée.

##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd

Retourne le HWND associé à cette cible de rendu.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Valeur de retour

Le HWND associé à cette cible de rendu.

##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget

Renvoie l’interface ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1HwndRenderTarget ou NULL si l’objet n’est pas encore initialisé.

##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget

Pointeur vers un objet ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget *

Renvoie l’interface ID2D1HwndRenderTarget.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1HwndRenderTarget ou NULL si l’objet n’est pas encore initialisé.

##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate

Crée de nouveau une cible de rendu associée à la fenêtre

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Le HWND associé à cette cible de rendu

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne TRUE. Sinon, elle retourne FALSE.

##  <a name="resize"></a>  CHwndRenderTarget::Resize

Modifie la taille de la cible de rendu à la taille de pixel spécifié

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
La nouvelle taille de la cible de rendu en pixels du périphérique

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne TRUE. Sinon, elle retourne FALSE.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
