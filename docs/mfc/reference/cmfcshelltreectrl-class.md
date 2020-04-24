---
title: Classe CMFCShellTreeCtrl
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
ms.openlocfilehash: c6f5856e92c2aca1d23ee6a37b99ea9700ea6db0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753441"
---
# <a name="cmfcshelltreectrl-class"></a>Classe CMFCShellTreeCtrl

La `CMFCShellTreeCtrl` classe étend la fonctionnalité [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md) en affichant une hiérarchie d’objets Shell.

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Permet ou désactive le menu raccourci.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Retourne une combinaison de drapeaux qui sont passés à [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Récupère le chemin vers un élément.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Retourne un pointeur à l’objet [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md) qui est utilisé avec cet `CMFCShellTreeCtrl` objet pour créer une fenêtre de style Explorer.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Cette fonction de membre est appelée par la fenêtre parente de cette fenêtre lorsqu’elle reçoit un message de notification qui s’applique à cette fenêtre. (Overrides [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|Rafraîchit et repeinte `CMFCShellTreeCtrl` l’objet actuel.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Sélectionne l’élément de commande d’arbre approprié basé sur un PIDL ou un chemin de chaîne fourni.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Définit des drapeaux pour filtrer le contexte `IShellFolder::EnumObjects`de l’arbre (semblable aux drapeaux utilisés par ).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Définit une relation `CMFCShellTreeCtrl` entre l’objet actuel et un `CMFCShellListCtrl` objet.|

## <a name="remarks"></a>Notes

Cette classe `CTreeCtrl` étend la classe en permettant à votre programme d’inclure des éléments Windows Shell dans l’arbre. Cette classe peut être `CMFCShellListCtrl` associée à un objet pour créer une fenêtre Explorer complète. Ensuite, la sélection d’un élément dans l’arbre affichera une liste d’éléments Windows Shell dans la liste associée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Spécifications

**En-tête:** afxshelltreeCtrl.h

## <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet de la classe `CMFCShellTreeCtrl`. Cet extrait de code fait partie de [l’échantillon Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu

Permet le menu raccourci.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] Un Boolean qui précise s’il faut activer le menu raccourci.

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a>CMFCShellTreeCtrl::GetFlags

Retourne les drapeaux fixés pour l’objet [cmFCShellTreeCtrl Class.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui spécifie la combinaison de drapeaux actuellement définis.

### <a name="remarks"></a>Notes

Les drapeaux placés dans le `CMFCShellTreeCtrl` sont envoyés à la méthode [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) chaque fois que l’objet est rafraîchi. Vous pouvez changer les drapeaux avec la [méthode CMFCShellTreeCtrl::SetFlags](#setflags) méthode.

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

Récupère le chemin d’un élément dans l’objet [cmFCShellTreeCtrl Class.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Paramètres

*strPath (en)*<br/>
[out] Une référence à un paramètre de chaîne. La méthode écrit le chemin de l’élément à ce paramètre.

*htreeItem (en)*<br/>
[dans] La méthode récupère le chemin pour cet élément de contrôle de l’arbre.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; 0 autrement.

### <a name="remarks"></a>Notes

Si cette méthode échoue, *strPath* contient la ficelle vide.

Si vous ne spécifiez pas *hTreeItem*, cette méthode tente d’obtenir la chaîne pour l’élément actuellement sélectionné. Si aucun élément n’est sélectionné et *hTreeItem* est NULL, cette méthode échoue.

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList

Retourne un pointeur à l’objet [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md) qui est associé à cet objet [CMFCShellTreeCtrl.](../../mfc/reference/cmfcshelltreectrl-class.md)

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CMFCShellListCtrl` de l’objet qui est associé à cet objet de contrôle de l’arbre.

### <a name="remarks"></a>Notes

En utilisant `CMFCShellListCtrl` un objet `CMFCShellTreeCtrl` avec un objet, vous pouvez créer une fenêtre de la nature d’un explorateur. Utilisez la méthode [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) pour associer les deux classes. Une fois qu’ils sont `CMFCShellListCtrl` associés, le `CMFCShellTreeCtrl` cadre met automatiquement à jour le si la sélection dans les modifications.

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Paramètres

[dans] *message*<br/>
[dans] *wParam (en)*<br/>
[dans] *lParam (en)*<br/>
[dans] *pLResult (en anglais)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

[dans] *pItem (en)*<br/>
[dans] *bSélectré*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

[dans] *pItem (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a>CMFCShellTreeCtrl::Refresh

Rafraîchit et repeinte le [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```cpp
void Refresh();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour actualiser la `CMFCShellTreeCtrl`hiérarchie des éléments affichés dans le .

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

Sélectionne un élément de la [classe CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) en fonction du chemin fourni.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
[dans] Une chaîne qui spécifie le chemin d’un élément.

*lpidl lpidl*<br/>
[dans] Un PIDL qui spécifie l’article

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; E_FAIL autrement.

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a>CMFCShellTreeCtrl::SetFlags

Définit des drapeaux pour filtrer le contexte de l’arbre.

```cpp
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
[dans] Les drapeaux à mettre.

*bRefresh (en)*<br/>
[dans] Un Boolean qui précise `CMFCShellTreeCtrl` si le doit être rafraîchi immédiatement.

### <a name="remarks"></a>Notes

Les `CMFCShellTreeCtrl` passes tous les drapeaux mis à [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Pour plus d’informations sur les valeurs des différents drapeaux, voir [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

Associe un objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) à un objet [CMFCShellTreeCtrl.](../../mfc/reference/cmfcshelltreectrl-class.md)

```cpp
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Paramètres

*liste de pShell*<br/>
[dans] Un pointeur `CMFCShellListCtrl` à un objet.

### <a name="remarks"></a>Notes

Cette méthode `CMFCShellListCtrl` associe `CMFCShellTreeCtrl`a avec un . Ces objets peuvent être affichés sous forme d’une fenêtre `CMFCShellTreeCtrl`de forme d’explorateur : si l’utilisateur sélectionne un objet dans le , les éléments associés dans le `CMFCShellListCtrl` seront automatiquement mis à jour.

Utilisez la méthode [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) pour récupérer l’associé `CMFCShellListCtrl` à un `CMFCShellTreeCtrl`.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl, classe](../../mfc/reference/ctreectrl-class.md)<br/>
[Classe CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)
