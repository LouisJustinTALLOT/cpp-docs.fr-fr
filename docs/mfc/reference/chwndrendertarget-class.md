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
ms.openlocfilehash: 24cf4127c2f429f66143af3a0f49625f23a4e6ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372466"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget, classe

Un emballage pour ID2D1HwndRenderTarget.

## <a name="syntax"></a>Syntaxe

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Construit un objet CHwndRenderTarget à partir de HWND.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|Attache l’interface cible de rendu existante à l’objet|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Indique si le HWND associé à cette cible de rendu est occlus.|
|[CHwndRenderTarget::Créer](#create)|Crée une cible de rendu associée à la fenêtre|
|[CHwndRenderTarget::Detach](#detach)|Les détaches rendent l’interface cible de l’objet|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Retourne le HWND associé à cette cible de rendu.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Retourne l’interface ID2D1HwndRenderTarget.|
|[CHwndRenderTarget::ReCreate](#recreate)|Re-crée une cible de rendu associée à la fenêtre|
|[CHwndRenderTarget::Resize](#resize)|Modifie la taille de la cible de rendu à la taille spécifiée des pixels|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHwndRenderTarget::opérateur ID2D1HwndRenderTarget](#operator_id2d1hwndrendertarget_star)|Retourne l’interface ID2D1HwndRenderTarget.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Un pointeur à un objet ID2D1HwndRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="chwndrendertargetattach"></a><a name="attach"></a>CHwndRenderTarget::Attach

Attache l’interface cible de rendu existante à l’objet

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Interface cible de rendu existante. Impossible d’être NULL

## <a name="chwndrendertargetcheckwindowstate"></a><a name="checkwindowstate"></a>CHwndRenderTarget::CheckWindowState

Indique si le HWND associé à cette cible de rendu est occlus.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui indique si le HWND associé à cette cible de rendu est occlus.

## <a name="chwndrendertargetchwndrendertarget"></a><a name="chwndrendertarget"></a>CHwndRenderTarget::CHwndRenderTarget

Construit un objet CHwndRenderTarget à partir de HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Paramètres

*Hwnd*<br/>
Le HWND associé à cette cible de rendu

## <a name="chwndrendertargetcreate"></a><a name="create"></a>CHwndRenderTarget::Créer

Crée une cible de rendu associée à la fenêtre

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Le HWND associé à cette cible de rendu

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE

## <a name="chwndrendertargetdetach"></a><a name="detach"></a>CHwndRenderTarget::Detach

Les détaches rendent l’interface cible de l’objet

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur pour rendre détaché l’interface cible.

## <a name="chwndrendertargetgethwnd"></a><a name="gethwnd"></a>CHwndRenderTarget::GetHwnd

Retourne le HWND associé à cette cible de rendu.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Valeur de retour

Le HWND associé à cette cible de rendu.

## <a name="chwndrendertargetgethwndrendertarget"></a><a name="gethwndrendertarget"></a>CHwndRenderTarget::GetHwndRenderTarget

Retourne l’interface ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1HwndRenderTarget ou NULL si l’objet n’est pas encore paralysé.

## <a name="chwndrendertargetm_phwndrendertarget"></a><a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget

Un pointeur à un objet ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

## <a name="chwndrendertargetoperator-id2d1hwndrendertarget"></a><a name="operator_id2d1hwndrendertarget_star"></a>CHwndRenderTarget::opérateur ID2D1HwndRenderTarget

Retourne l’interface ID2D1HwndRenderTarget.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1HwndRenderTarget ou NULL si l’objet n’est pas encore paralysé.

## <a name="chwndrendertargetrecreate"></a><a name="recreate"></a>CHwndRenderTarget::ReCreate

Re-crée une cible de rendu associée à la fenêtre

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Le HWND associé à cette cible de rendu

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="chwndrendertargetresize"></a><a name="resize"></a>CHwndRenderTarget::Resize

Modifie la taille de la cible de rendu à la taille spécifiée des pixels

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
La nouvelle taille de la cible de rendu dans les pixels de l’appareil

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
