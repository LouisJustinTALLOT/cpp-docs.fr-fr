---
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
ms.openlocfilehash: 1fc422c3aca3efe1fb177e7a3567530d70c27119
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410059"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl, classe

Le `CMFCShellTreeCtrl` classe étend [classe CTreeCtrl](../../mfc/reference/ctreectrl-class.md) fonctionnalités en affichant une hiérarchie des éléments du Shell.

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Active ou désactive le menu contextuel.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Retourne une combinaison d’indicateurs qui sont passés à [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Récupère le chemin d’accès à un élément.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Retourne un pointeur vers le [CMFCShellListCtrl, classe](../../mfc/reference/cmfcshelllistctrl-class.md) objet qui est utilisé avec ce `CMFCShellTreeCtrl` objet à créer une fenêtre semblable à l’Explorateur.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Cette fonction membre est appelée par cette fenêtre parente lorsqu’il reçoit un message de notification qui s’applique à cette fenêtre. (Substitue [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|Actualise et redessine actuel `CMFCShellTreeCtrl` objet.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Sélectionne l’élément de contrôle d’arborescence approprié selon une PIDL fourni ou un chemin d’accès de la chaîne.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Définit des indicateurs pour filtrer le contexte de l’arborescence (similaire aux indicateurs utilisés par `IShellFolder::EnumObjects`).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Définit une relation entre le cours `CMFCShellTreeCtrl` objet et un `CMFCShellListCtrl` objet.|

## <a name="remarks"></a>Notes

Cette classe étend la `CTreeCtrl` classe en activant votre programme inclure les éléments de l’interpréteur de commandes Windows dans l’arborescence. Cette classe peut être associée un `CMFCShellListCtrl` objet à créer une fenêtre d’Explorateur terminée. Ensuite, en sélectionnant un élément dans l’arborescence affiche une liste d’éléments de l’interpréteur de commandes Windows dans la liste associée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxshelltreeCtrl.h

## <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet de la classe `CMFCShellTreeCtrl`. Cet extrait de code fait partie de la [exemple Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

Active le menu contextuel.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[in] Valeur booléenne qui spécifie s’il faut activer le menu contextuel.

##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags

Retourne les indicateurs définis pour le [CMFCShellTreeCtrl, classe](../../mfc/reference/cmfcshelltreectrl-class.md) objet.

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui spécifie la combinaison d’indicateurs actuellement définie.

### <a name="remarks"></a>Notes

Les indicateurs définis dans le `CMFCShellTreeCtrl` sont envoyés à la méthode [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) chaque fois que l’objet est actualisé. Vous pouvez modifier les indicateurs avec la [CMFCShellTreeCtrl::SetFlags](#setflags) (méthode).

##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath

Récupère le chemin d’accès d’un élément dans le [CMFCShellTreeCtrl, classe](../../mfc/reference/cmfcshelltreectrl-class.md) objet.

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Paramètres

*strPath*<br/>
[out] Une référence à un paramètre de chaîne. La méthode écrit le chemin d’accès de l’élément à ce paramètre.

*htreeItem*<br/>
[in] La méthode récupère le chemin d’accès pour cet élément de contrôle d’arborescence.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; 0 dans le cas contraire.

### <a name="remarks"></a>Notes

Si cette méthode échoue, *strPath* contient une chaîne vide.

Si vous ne spécifiez pas *hTreeItem*, cette méthode essaie d’obtenir la chaîne de l’élément actuellement sélectionné. Si aucun élément n’est sélectionné et *hTreeItem* est NULL, cette méthode échoue.

##  <a name="getrelatedlist"></a>  CMFCShellTreeCtrl::GetRelatedList

Retourne un pointeur vers le [CMFCShellListCtrl, classe](../../mfc/reference/cmfcshelllistctrl-class.md) objet qui est associé à ce [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objet.

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `CMFCShellListCtrl` objet associé à cet objet de contrôle d’arborescence.

### <a name="remarks"></a>Notes

En utilisant un `CMFCShellListCtrl` de l’objet avec un `CMFCShellTreeCtrl` de l’objet, vous pouvez créer une fenêtre semblable à l’Explorateur. Utilisez la méthode [CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist) pour associer les deux classes. Une fois qu’ils sont associés, le framework met automatiquement à jour le `CMFCShellListCtrl` si la sélection dans le `CMFCShellTreeCtrl` modifications.

##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Paramètres

[in] *message*<br/>
[in] *wParam*<br/>
[in] *lParam*<br/>
[in] *pLResult*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

[in] *pItem*<br/>
[in] *bSelected*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

[in] *pItem*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

Actualise et redessine le [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md).

```
void Refresh();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour actualiser la hiérarchie des éléments affichés dans le `CMFCShellTreeCtrl`.

##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath

Sélectionne un élément dans le [CMFCShellTreeCtrl, classe](../../mfc/reference/cmfcshelltreectrl-class.md) basé sur le chemin d’accès fourni.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
[in] Chaîne qui spécifie le chemin d’accès d’un élément.

*lpidl*<br/>
[in] Un PIDL qui spécifie l’élément

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; E_FAIL sinon.

##  <a name="setflags"></a>  CMFCShellTreeCtrl::SetFlags

Définit les indicateurs pour filtrer le contexte de l’arborescence.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
[in] Les indicateurs à définir.

*bRefresh*<br/>
[in] Valeur booléenne qui spécifie si le `CMFCShellTreeCtrl` doit être actualisée immédiatement.

### <a name="remarks"></a>Notes

Le `CMFCShellTreeCtrl` transmet toutes la valeur indicateurs [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Pour plus d’informations sur les valeurs des différents indicateurs, consultez [IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

##  <a name="setrelatedlist"></a>  CMFCShellTreeCtrl::SetRelatedList

Associe un [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) de l’objet avec un [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objet.

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Paramètres

*pShellList*<br/>
[in] Un pointeur vers un `CMFCShellListCtrl` objet.

### <a name="remarks"></a>Notes

Cette méthode associe un `CMFCShellListCtrl` avec un `CMFCShellTreeCtrl`. Ces objets peuvent être affichés dans une fenêtre semblable à l’Explorateur : si l’utilisateur sélectionne un objet dans le `CMFCShellTreeCtrl`, l’associées des éléments dans le `CMFCShellListCtrl` sera automatiquement mise à jour.

Utilisez la méthode [CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist) pour récupérer le `CMFCShellListCtrl` associé à un `CMFCShellTreeCtrl`.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl, classe](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl, classe](../../mfc/reference/cmfcshelllistctrl-class.md)
