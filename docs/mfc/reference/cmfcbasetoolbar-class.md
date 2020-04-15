---
title: CMFCBaseToolBar, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
ms.openlocfilehash: 027fe8569ff133bb3f348c9d0607f19c6d778c4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367830"
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar, classe

Classe de base pour barres d’outils.

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
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Retourne le mode d'ancrage. (Overrides [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Retourne la taille minimale d’une barre d’outils. (Overrides [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Appelé par le cadre après les changements parent du volet. (Overrides [CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxbasetoolbar.h

## <a name="cmfcbasetoolbargetdockingmode"></a><a name="getdockingmode"></a>CMFCBaseToolBar::GetDockingMode

Retourne le mode d'ancrage.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Valeur de retour

Le mode d’amarrage.

## <a name="cmfcbasetoolbargetminsize"></a><a name="getminsize"></a>CMFCBaseToolBar::GetMinSize

Retourne la taille minimale d’une barre d’outils.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
[out] La taille minimale d’une barre d’outils.

## <a name="cmfcbasetoolbaronafterchangeparent"></a><a name="onafterchangeparent"></a>CMFCBaseToolBar::OnAfterChangeParent

Appelé par le cadre après les changements parent du volet.

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>Paramètres

*pWndOldParent*<br/>
[dans] Un pointeur à la fenêtre précédente parent.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
