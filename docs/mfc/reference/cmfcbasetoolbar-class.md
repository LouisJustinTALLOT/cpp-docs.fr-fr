---
title: Cmfcbasetoolbar, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 023b8d4c48d5e9f04aeb1207db2236d6ef8b7ba6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395477"
---
# <a name="cmfcbasetoolbar-class"></a>Cmfcbasetoolbar, classe

Classe de base pour les barres d’outils.

## <a name="syntax"></a>Syntaxe

```
class CMFCBaseToolBar : public CPane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCBaseToolBar::CMFCBaseToolBar`|Constructeur par défaut.|
|`CMFCBaseToolBar::~CMFCBaseToolBar`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCBaseToolBar::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Retourne le mode d'ancrage. (Substitue [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Retourne la taille minimale d’une barre d’outils. (Substitue [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Appelé par l’infrastructure après modification du parent du volet. (Substitue [CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxbasetoolbar.h

##  <a name="getdockingmode"></a>  CMFCBaseToolBar::GetDockingMode

Retourne le mode d'ancrage.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Valeur de retour

Le mode d’ancrage.

##  <a name="getminsize"></a>  CMFCBaseToolBar::GetMinSize

Retourne la taille minimale d’une barre d’outils.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Paramètres

*size*<br/>
[out] La taille minimale d’une barre d’outils.

##  <a name="onafterchangeparent"></a>  CMFCBaseToolBar::OnAfterChangeParent

Appelé par l’infrastructure après modification du parent du volet.

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>Paramètres

*pWndOldParent*<br/>
[in] Pointeur vers la fenêtre parente précédente.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
