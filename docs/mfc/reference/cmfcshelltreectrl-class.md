---
description: 'En savoir plus sur : classe CMFCShellTreeCtrl'
title: CMFCShellTreeCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
ms.openlocfilehash: 86b18d1cb919eaa36c3aed0d6e1623bab530a0aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339668"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl, classe

La `CMFCShellTreeCtrl` classe étend les fonctionnalités de la [classe CTreeCtrl](../../mfc/reference/ctreectrl-class.md) en affichant une hiérarchie d’éléments de Shell.

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Active ou désactive le menu contextuel.|
|[CMFCShellTreeCtrl :: GetFlags](#getflags)|Retourne une combinaison d’indicateurs passés à [IShellFolder :: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Récupère le chemin d’accès à un élément.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Retourne un pointeur vers l’objet de [classe CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) utilisé avec cet `CMFCShellTreeCtrl` objet pour créer une fenêtre similaire à l’Explorateur.|
|[CMFCShellTreeCtrl :: OnChildNotify](#onchildnotify)|Cette fonction membre est appelée par la fenêtre parente de cette fenêtre lorsqu’elle reçoit un message de notification qui s’applique à cette fenêtre. (Substitue [CWnd :: OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl :: Refresh](#refresh)|Actualise et repeint l' `CMFCShellTreeCtrl` objet actuel.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Sélectionne l’élément de contrôle d’arborescence approprié en fonction d’un PIDL ou d’un chemin d’accès de chaîne fourni.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Définit des indicateurs pour filtrer le contexte d’arborescence (semblable aux indicateurs utilisés par `IShellFolder::EnumObjects` ).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Définit une relation entre l' `CMFCShellTreeCtrl` objet actuel et un `CMFCShellListCtrl` objet.|

## <a name="remarks"></a>Notes

Cette classe étend la `CTreeCtrl` classe en permettant à votre programme d’inclure des éléments de shell Windows dans l’arborescence. Cette classe peut être associée à un `CMFCShellListCtrl` objet pour créer une fenêtre d’explorateur complète. Ensuite, si vous sélectionnez un élément dans l’arborescence, la liste des éléments de l’interpréteur de commandes Windows s’affiche dans la liste associée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxshelltreeCtrl. h

## <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet de la classe `CMFCShellTreeCtrl`. Cet extrait de code fait partie de l' [exemple Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a> CMFCShellTreeCtrl::EnableShellContextMenu

Active le menu contextuel.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans Valeur booléenne qui spécifie s’il faut activer le menu contextuel.

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a> CMFCShellTreeCtrl :: GetFlags

Retourne les indicateurs définis pour l’objet de la [classe CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur DWORD qui spécifie la combinaison des indicateurs actuellement définis.

### <a name="remarks"></a>Notes

Les indicateurs définis dans le `CMFCShellTreeCtrl` sont envoyés à la méthode [IShellFolder :: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) à chaque actualisation de l’objet. Vous pouvez modifier les indicateurs avec la méthode [CMFCShellTreeCtrl :: SetFlags](#setflags) .

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a> CMFCShellTreeCtrl::GetItemPath

Récupère le chemin d’accès d’un élément dans l’objet de [classe CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Paramètres

*strPath*<br/>
à Référence à un paramètre de chaîne. La méthode écrit le chemin d’accès de l’élément dans ce paramètre.

*htreeItem*<br/>
dans La méthode récupère le chemin d’accès pour cet élément de contrôle d’arborescence.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; Sinon, 0.

### <a name="remarks"></a>Notes

Si cette méthode échoue, *strPath* contient la chaîne vide.

Si vous ne spécifiez pas *hTreeItem*, cette méthode tente d’obtenir la chaîne pour l’élément actuellement sélectionné. Si aucun élément n’est sélectionné et que *hTreeItem* a la valeur null, cette méthode échoue.

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a> CMFCShellTreeCtrl::GetRelatedList

Retourne un pointeur vers l’objet de [classe CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) associé à cet objet [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `CMFCShellListCtrl` objet associé à cet objet de contrôle d’arborescence.

### <a name="remarks"></a>Notes

En utilisant un `CMFCShellListCtrl` objet avec un `CMFCShellTreeCtrl` objet, vous pouvez créer une fenêtre similaire à l’Explorateur. Utilisez la méthode [CMFCShellTreeCtrl :: SetRelatedList](#setrelatedlist) pour associer les deux classes. Une fois qu’ils sont associés, l’infrastructure met automatiquement à jour le `CMFCShellListCtrl` si la sélection est `CMFCShellTreeCtrl` modifiée.

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a> CMFCShellTreeCtrl :: OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Paramètres

dans *message*<br/>
dans *wParam*<br/>
dans *lParam*<br/>
dans *pLResult*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a> CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

dans *pItem*<br/>
dans *bSelected*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a> CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

dans *pItem*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a> CMFCShellTreeCtrl :: Refresh

Actualise et repeint le [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```cpp
void Refresh();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour actualiser la hiérarchie des éléments affichés dans le `CMFCShellTreeCtrl` .

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a> CMFCShellTreeCtrl::SelectPath

Sélectionne un élément dans la [classe CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) en fonction du chemin d’accès fourni.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
dans Chaîne qui spécifie le chemin d’accès d’un élément.

*lpidl*<br/>
dans PIDL qui spécifie l’élément.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, E_FAIL.

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a> CMFCShellTreeCtrl::SetFlags

Définit des indicateurs pour filtrer le contexte d’arborescence.

```cpp
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
dans Indicateurs à définir.

*bRefresh*<br/>
dans Valeur booléenne qui spécifie si `CMFCShellTreeCtrl`  doit être actualisé immédiatement.

### <a name="remarks"></a>Notes

Le `CMFCShellTreeCtrl` passe tous les indicateurs Set à [IShellFolder :: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Pour plus d’informations sur les valeurs des différents indicateurs, consultez [IShellFolder :: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a> CMFCShellTreeCtrl::SetRelatedList

Associe un objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) à un objet [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) .

```cpp
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Paramètres

*pShellList*<br/>
dans Pointeur vers un `CMFCShellListCtrl` objet.

### <a name="remarks"></a>Notes

Cette méthode associe un `CMFCShellListCtrl` à un `CMFCShellTreeCtrl` . Ces objets peuvent être affichés sous la forme d’une fenêtre similaire à l’Explorateur : si l’utilisateur sélectionne un objet dans le `CMFCShellTreeCtrl` , les éléments associés dans le `CMFCShellListCtrl` sont automatiquement mis à jour.

Utilisez la méthode [CMFCShellTreeCtrl :: GetRelatedList](#getrelatedlist) pour récupérer le `CMFCShellListCtrl` associé à un `CMFCShellTreeCtrl` .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl (classe)](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl, classe](../../mfc/reference/cmfcshelllistctrl-class.md)
