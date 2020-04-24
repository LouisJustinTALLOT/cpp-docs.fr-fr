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
ms.openlocfilehash: 8c07962c017d160cb3ce5841a75f1ae8a8761641
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753392"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget, classe

Un emballage pour ID2D1DCRenderTarget.

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
|[CDCRenderTarget::Attach](#attach)|Attache l’interface cible de rendu existante à l’objet|
|[CDCRenderTarget::BindDC](#binddc)|Lie la cible de rendu au contexte de l’appareil auquel il émet des commandes de dessin|
|[CDCRenderTarget::Créer](#create)|Crée un CDCRenderTarget.|
|[CDCRenderTarget::Detach](#detach)|Les détaches rendent l’interface cible de l’objet|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Retourne l’interface ID2D1DCRenderTarget|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget::opérateur ID2D1DCRenderTarget](#operator_id2d1dcrendertarget_star)|Retourne l’interface ID2D1DCRenderTarget|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Un pointeur à un objet ID2D1DCRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cdcrendertargetattach"></a><a name="attach"></a>CDCRenderTarget::Attach

Attache l’interface cible de rendu existante à l’objet

```cpp
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Interface cible de rendu existante. Impossible d’être NULL

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a>CDCRenderTarget::BindDC

Lie la cible de rendu au contexte de l’appareil auquel il émet des commandes de dessin

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*Dc*<br/>
Le contexte de l’appareil auquel la cible rend les questions de dessin des commandes

*Rect*<br/>
Les dimensions de la poignée vers un contexte d’appareil (HDC) auquel la cible de rendu est liée

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget

Construit un objet CDCRenderTarget.

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a>CDCRenderTarget::Créer

Crée un CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Paramètres

*Accessoires*<br/>
Le mode de rendu, le format pixel, les options de remotage, les informations DPI et le support DirectX minimum requis pour le rendu matériel.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cdcrendertargetdetach"></a><a name="detach"></a>CDCRenderTarget::Detach

Les détaches rendent l’interface cible de l’objet

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur pour rendre détaché l’interface cible.

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget

Retourne l’interface ID2D1DCRenderTarget

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1DCRenderTarget ou NULL si l’objet n’est pas encore initialisé.

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget

Un pointeur à un objet ID2D1DCRenderTarget.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::opérateur ID2D1DCRenderTarget

Retourne l’interface ID2D1DCRenderTarget

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1DCRenderTarget ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
