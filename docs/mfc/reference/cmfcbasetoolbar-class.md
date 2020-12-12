---
description: 'En savoir plus sur : classe CMFCBaseToolBar'
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
ms.openlocfilehash: 37597e4cb300e0d6d16c92f105e332c18c5beda7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247915"
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar, classe

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
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Retourne le mode d'ancrage. (Substitue [CBasePane :: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Retourne la taille minimale d’une barre d’outils. (Substitue [CPane :: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Appelé par le Framework après que le parent du volet a été modifié. (Substitue [CBasePane :: OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxbasetoolbar. h

## <a name="cmfcbasetoolbargetdockingmode"></a><a name="getdockingmode"></a> CMFCBaseToolBar::GetDockingMode

Retourne le mode d'ancrage.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

Mode d’ancrage.

## <a name="cmfcbasetoolbargetminsize"></a><a name="getminsize"></a> CMFCBaseToolBar::GetMinSize

Retourne la taille minimale d’une barre d’outils.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Paramètres

*size*<br/>
à Taille minimale d’une barre d’outils.

## <a name="cmfcbasetoolbaronafterchangeparent"></a><a name="onafterchangeparent"></a> CMFCBaseToolBar::OnAfterChangeParent

Appelé par le Framework après que le parent du volet a été modifié.

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>Paramètres

*pWndOldParent*<br/>
dans Pointeur vers la fenêtre parente précédente.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
