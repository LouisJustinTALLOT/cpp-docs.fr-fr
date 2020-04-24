---
title: Classe CMFCShellListCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: 445556535217b0887a02227a0773c287911922a2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753478"
---
# <a name="cmfcshelllistctrl-class"></a>Classe CMFCShellListCtrl

La `CMFCShellListCtrl` classe fournit des fonctionnalités de contrôle de liste Windows et l’élargit en incluant la possibilité d’afficher une liste d’éléments de coquille.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Affiche une liste d’éléments contenus dans un dossier fourni.|
|[CMFCShellListCtrl::DsplayParentFolder](#displayparentfolder)|Affiche une liste d’éléments contenus dans le dossier qui est le parent du dossier actuellement affiché.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Permet ou désactive le menu raccourci.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Récupère le chemin du dossier actuel.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Récupère le nom du dossier actuel.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Retourne le PIDL de l’élément de contrôle de liste actuel.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Retourne un pointeur sur le dossier Shell actuel.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Retourne le chemin textuel d’un élément.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Retourne les types d’éléments Shell qui sont affichés par le contrôle de liste.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Vérifie si le dossier actuellement sélectionné est le dossier de bureau.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Le cadre appelle cette méthode lorsqu’elle compare deux éléments. (Overrides [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Appelé lorsque le cadre récupère la date de fichier affichée par le contrôle de liste.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Appelé lorsque le cadre convertit la taille du fichier d’un contrôle de liste.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Appelé lorsque le cadre récupère l’icône d’un élément de contrôle de liste.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Appelé lorsque le cadre convertit le texte d’un élément de contrôle de liste.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Appelé par le cadre quand il définit les noms des colonnes.|
|[CMFCShellListCtrl::Refresh](#refresh)|Rafraîchit et repeinte le contrôle de liste.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Définit le type d’éléments affichés par le contrôle de liste.|

## <a name="remarks"></a>Notes

La `CMFCShellListCtrl` classe étend la fonctionnalité de la [classe CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) en permettant à votre programme d’énumérer les éléments de la coque Windows. Le format d’affichage qui est utilisé est comme celui d’une vue de liste pour une fenêtre Explorer.

Un objet [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) peut `CMFCShellListCtrl` être associé à un objet pour créer une fenêtre Explorer complète. Ensuite, la sélection d’un élément dans le `CMFCShellTreeCtrl` fera en sorte que l’objet `CMFCShellListCtrl` indique le contenu de l’élément sélectionné.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer `CMFCShellListCtrl` un objet de la classe et comment afficher le dossier parent du dossier actuellement affiché. Cet extrait de code fait partie de [l’échantillon Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>Spécifications

**En-tête:** afxshelllistCtrl.h

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder

Affiche une liste d’éléments contenus dans le dossier fourni.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
[dans] Une chaîne qui contient le chemin d’un dossier.

*lpItemInfo (en anglais)*<br/>
[dans] Un pointeur `LPAFX_SHELLITEMINFO` vers une structure qui décrit un dossier à afficher.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; E_FAIL autrement.

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a>CMFCShellListCtrl::DsplayParentFolder

Mise à jour de [l’objet CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) pour afficher le dossier parent du dossier actuellement affiché.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; E_FAIL autrement.

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu

Permet le menu raccourci.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] Un Boolean qui précise si le cadre permet le menu raccourci.

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder

Récupère le chemin du dossier actuellement sélectionné dans l’objet [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Paramètres

*strPath (en)*<br/>
[out] Une référence à un paramètre de chaîne où la méthode écrit le chemin.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; 0 autrement.

### <a name="remarks"></a>Notes

Cette méthode échoue s’il n’y a pas de dossier sélectionné dans le `CMFCShellListCtrl`.

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName

Récupère le nom du dossier actuellement sélectionné dans l’objet [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
[out] Une référence à un paramètre de chaîne où la méthode écrit le nom.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; 0 autrement.

### <a name="remarks"></a>Notes

Cette méthode échoue s’il n’y a pas de dossier sélectionné dans le `CMFCShellListCtrl`.

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

Retourne le PIDL de l’article actuellement sélectionné.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Valeur de retour

Le PIDL de l’élément actuel.

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder

Obtient un pointeur à l’élément actuellement sélectionné dans l’objet [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à [l’interface IShellFolder](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) pour l’objet sélectionné.

### <a name="remarks"></a>Notes

Cette méthode renvoie NULL si aucun objet n’est actuellement sélectionné.

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

Récupère le chemin pour un article.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Paramètres

*strPath (en)*<br/>
[out] Une référence à une chaîne qui reçoit le chemin.

*iItem*<br/>
[dans] L’index de l’élément de liste.

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès; FALSE autrement.

### <a name="remarks"></a>Notes

L’index fourni par *iItem* est basé sur les éléments actuellement affichés par l’objet [cmFCShellListCtrl Class.](../../mfc/reference/cmfcshelllistctrl-class.md)

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes

Retourne le type d’éléments affichés par l’objet [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) qui contient le `CMFCShellListCtrl`type d’articles énumérés dans le .

### <a name="remarks"></a>Notes

Pour définir le type d’éléments répertoriés dans un `CMFCShellListCtrl`, appelez [CMFCShellListCtrl::SetItemTypes](#setitemtypes).

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop

Détermine si le dossier qui est affiché dans l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) est le dossier de bureau.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le dossier affiché est le dossier de bureau; FALSE autrement.

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Paramètres

[dans] *lParam1*<br/>
[dans] *lParam2*<br/>
[dans] *iColumn iColumn*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate

Le cadre appelle cette méthode lorsqu’elle doit convertir la date associée à un objet en chaîne.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*tmFile*<br/>
[dans] La date associée à un fichier.

*Str*<br/>
[out] Une chaîne qui contient la date de fichier formatée.

### <a name="remarks"></a>Notes

Lorsqu’un objet [de classe CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) affiche la date associée à un fichier, il doit convertir cette date en format de chaîne. L’utilisation `CMFCShellListCtrl` de cette méthode pour faire cette conversion. Par défaut, cette méthode utilise le lieu actuel pour formater la date en une chaîne.

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize

Le cadre appelle cette méthode lorsqu’elle convertit la taille d’un objet en chaîne.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*lFileSize*<br/>
[dans] La taille du fichier que le cadre affichera.

*Str*<br/>
[out] Une chaîne qui contient la taille du fichier formaté.

### <a name="remarks"></a>Notes

Lorsqu’un objet [de classe CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) doit afficher la taille d’un fichier, il doit convertir la taille du fichier en format de chaîne. L’utilisation `CMFCShellListCtrl` de cette méthode pour faire cette conversion. Par défaut, cette méthode convertit la taille du fichier des octets en kilooctets, puis utilise le lieu actuel pour formater la taille en chaîne.

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon

Le cadre appelle cette méthode pour récupérer l’icône associée à un élément de liste de coquilles.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
[dans] L’index de l’élément.

*pItem (en)*<br/>
[dans] Un LPAFX_SHELLITEMINFO paramètre qui décrit l’élément.

### <a name="return-value"></a>Valeur de retour

L’index de l’image de l’icône en cas de succès; -1 si la fonction échoue.

### <a name="remarks"></a>Notes

L’indice d’image d’icône est basé sur la liste d’images du système.

Par défaut, cette méthode repose sur le *paramètre pItem.* La valeur *d’iItem* n’est pas utilisée dans la implémentation par défaut. Vous pouvez utiliser *iItem* pour implémenter un comportement personnalisé.

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText

Le cadre appelle cette méthode lorsqu’elle doit récupérer le texte d’un objet shell.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
[dans] L’index de l’élément.

*iColumn iColumn*<br/>
[dans] La colonne d’intérêt.

*pItem (en)*<br/>
[dans] Un LPAFX_SHELLITEMINFO paramètre qui décrit l’élément.

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient le texte associé à l’élément.

### <a name="remarks"></a>Notes

Chaque élément `CMFCShellListCtrl` de l’objet peut avoir du texte dans une ou plusieurs colonnes. Lorsque le cadre appelle cette méthode, il spécifie la colonne qui l’intéresse. Si vous appelez cette fonction manuellement, vous devez également spécifier la colonne qui vous intéresse.

Par défaut, cette méthode repose sur le *paramètre pItem* pour déterminer quel élément traiter. La valeur *d’iItem* n’est pas utilisée dans la implémentation par défaut.

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

Le cadre appelle cette méthode lorsqu’elle définit les noms des colonnes.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Notes

Par défaut, le cadre crée `CMFCShellListCtrl` quatre colonnes dans un objet. Les noms de ces colonnes sont **Nom**, **Taille**, **Type**, et **Modifié**. Vous pouvez passer outre à cette méthode pour personnaliser le nombre de colonnes et leurs noms.

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a>CMFCShellListCtrl::Refresh

Rafraîchit et repeinte l’objet [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Valeur de retour

`S_OK`en cas de succès; sinon une valeur d’erreur.

### <a name="remarks"></a>Notes

Appelez cette méthode pour actualiser la `CMFCShellListCtrl` liste des éléments affichés par l’objet.

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes

Définit le type d’éléments qui sont répertoriés dans l’objet [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```cpp
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Paramètres

*nTypes*<br/>
[dans] Une liste des types `CMFCShellListCtrl` d’éléments que l’objet prend en charge.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la liste des types d’objets, voir [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)<br/>
[Classe CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)
