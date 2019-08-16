---
title: CMFCShellListCtrl, classe
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
ms.openlocfilehash: 02d4883c6b5445515d891c5e76ccf10b6bb35bba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504921"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl, classe

La `CMFCShellListCtrl` classe fournit les fonctionnalités de contrôle de liste Windows et les développe en incluant la possibilité d’afficher une liste d’éléments de Shell.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Affiche la liste des éléments contenus dans un dossier fourni.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Affiche la liste des éléments contenus dans le dossier qui est le parent du dossier actuellement affiché.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Active ou désactive le menu contextuel.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Récupère le chemin d’accès du dossier actif.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Récupère le nom du dossier actif.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Retourne le PIDL de l’élément de contrôle de liste actuel.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Retourne un pointeur vers le dossier shell actuel.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Retourne le chemin d’accès textuel d’un élément.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Retourne les types d’éléments d’interpréteur de commandes qui sont affichés par le contrôle de liste.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Vérifie si le dossier actuellement sélectionné est le dossier bureau.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|L’infrastructure appelle cette méthode lorsqu’elle compare deux éléments. (Substitue [CMFCListCtrl:: OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Appelé lorsque l’infrastructure récupère la date de fichier affichée par le contrôle de liste.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Appelé lorsque l’infrastructure convertit la taille de fichier d’un contrôle de liste.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Appelé lorsque l’infrastructure récupère l’icône d’un élément de contrôle de liste.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Appelé lorsque l’infrastructure convertit le texte d’un élément de contrôle de liste.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Appelé par le Framework quand il définit les noms des colonnes.|
|[CMFCShellListCtrl::Refresh](#refresh)|Actualise et repeint le contrôle de liste.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Définit le type des éléments affichés par le contrôle de liste.|

## <a name="remarks"></a>Notes

La `CMFCShellListCtrl` classe étend les fonctionnalités de la [classe CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) en permettant à votre programme de répertorier les éléments de l’interpréteur de commandes Windows. Le format d’affichage utilisé est semblable à celui d’un affichage de liste pour une fenêtre d’explorateur.

Un objet [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) peut être associé à un `CMFCShellListCtrl` objet pour créer une fenêtre d’explorateur complète. Ensuite, si vous sélectionnez un élément `CMFCShellTreeCtrl` dans, `CMFCShellListCtrl` l’objet répertorie le contenu de l’élément sélectionné.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer un objet de la `CMFCShellListCtrl` classe et comment afficher le dossier parent du dossier actuellement affiché. Cet extrait de code fait partie de l' [exemple Explorer](../../overview/visual-cpp-samples.md).

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

## <a name="requirements"></a>Configuration requise

**En-tête:** afxshelllistCtrl. h

##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder

Affiche la liste des éléments contenus dans le dossier fourni.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
dans Chaîne qui contient le chemin d’accès d’un dossier.

*lpItemInfo*<br/>
dans Pointeur vers une `LPAFX_SHELLITEMINFO` structure qui décrit un dossier à afficher.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite; E_FAIL dans le cas contraire.

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

Met à jour l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) pour afficher le dossier parent du dossier actuellement affiché.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite; E_FAIL dans le cas contraire.

##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu

Active le menu contextuel.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans Valeur booléenne qui spécifie si l’infrastructure Active le menu contextuel.

##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder

Récupère le chemin d’accès du dossier actuellement sélectionné dans l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Paramètres

*strPath*<br/>
à Référence à un paramètre de chaîne où la méthode écrit le chemin d’accès.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode échoue si aucun dossier n’est sélectionné dans le `CMFCShellListCtrl`.

##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName

Récupère le nom du dossier actuellement sélectionné dans l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
à Référence à un paramètre de chaîne où la méthode écrit le nom.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode échoue si aucun dossier n’est sélectionné dans le `CMFCShellListCtrl`.

##  <a name="getcurrentitemidlist"></a>  CMFCShellListCtrl::GetCurrentItemIdList

Retourne le PIDL de l’élément actuellement sélectionné.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Valeur de retour

PIDL de l’élément actuel.

##  <a name="getcurrentshellfolder"></a>  CMFCShellListCtrl::GetCurrentShellFolder

Obtient un pointeur vers l’élément actuellement sélectionné dans l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l' [interface IShellFolder](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) pour l’objet sélectionné.

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur NULL si aucun objet n’est actuellement sélectionné.

##  <a name="getitempath"></a>  CMFCShellListCtrl::GetItemPath

Récupère le chemin d’accès d’un élément.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Paramètres

*strPath*<br/>
à Référence à une chaîne qui reçoit le chemin d’accès.

*iItem*<br/>
dans Index de l’élément de liste.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

L’index fourni par *iItem* est basé sur les éléments actuellement affichés par l’objet de [classe CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

##  <a name="getitemtypes"></a>  CMFCShellListCtrl::GetItemTypes

Retourne le type des éléments affichés par l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) qui contient le type d’éléments figurant dans le `CMFCShellListCtrl`.

### <a name="remarks"></a>Notes

Pour définir le type des éléments listés dans `CMFCShellListCtrl`un, appelez [CMFCShellListCtrl:: SetItemTypes](#setitemtypes).

##  <a name="isdesktop"></a>  CMFCShellListCtrl::IsDesktop

Détermine si le dossier affiché dans l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) est le dossier Desktop.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le dossier affiché est le dossier Desktop; FALSe dans le cas contraire.

##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems

Pour plus d’informations, consultez le code source situé dans le dossier **VC\\ATLMFC\\SRC\\MFC** de votre installation de Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Paramètres

dans *lParam1*<br/>
dans *lParam2*<br/>
dans *IColumn*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate

Le Framework appelle cette méthode lorsqu’il doit convertir la date associée à un objet en chaîne.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*tmFile*<br/>
dans Date associée à un fichier.

*str*<br/>
à Chaîne qui contient la date de fichier mise en forme.

### <a name="remarks"></a>Notes

Lorsqu’un objet de [classe CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) affiche la date associée à un fichier, il doit convertir cette date en un format de chaîne. `CMFCShellListCtrl` Utilise cette méthode pour effectuer cette conversion. Par défaut, cette méthode utilise les paramètres régionaux actuels pour mettre en forme la date dans une chaîne.

##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize

L’infrastructure appelle cette méthode lorsqu’elle convertit la taille d’un objet en une chaîne.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*lFileSize*<br/>
dans Taille du fichier qui sera affiché par le Framework.

*str*<br/>
à Chaîne qui contient la taille du fichier mis en forme.

### <a name="remarks"></a>Notes

Lorsqu’un objet de [classe CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) doit afficher la taille d’un fichier, il doit convertir la taille de fichier au format de chaîne. `CMFCShellListCtrl` Utilise cette méthode pour effectuer cette conversion. Par défaut, cette méthode convertit la taille du fichier de octets en kilo-octets, puis utilise les paramètres régionaux actuels pour mettre en forme la taille en chaîne.

##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon

L’infrastructure appelle cette méthode pour récupérer l’icône associée à un élément de liste de Shell.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
dans Index de l’élément.

*pItem*<br/>
dans Paramètre LPAFX_SHELLITEMINFO qui décrit l’élément.

### <a name="return-value"></a>Valeur de retour

Index de l’image d’icône en cas de réussite; -1 si la fonction échoue.

### <a name="remarks"></a>Notes

L’index d’image d’icône est basé sur la liste d’images système.

Par défaut, cette méthode s’appuie sur le paramètre *pItem* . La valeur de *iItem* n’est pas utilisée dans l’implémentation par défaut. Vous pouvez utiliser *iItem* pour implémenter un comportement personnalisé.

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

Le Framework appelle cette méthode lorsqu’il doit récupérer le texte d’un élément de Shell.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
dans Index de l’élément.

*iColumn*<br/>
dans Colonne qui vous intéresse.

*pItem*<br/>
dans Paramètre LPAFX_SHELLITEMINFO qui décrit l’élément.

### <a name="return-value"></a>Valeur de retour

`CString` Qui contient le texte associé à l’élément.

### <a name="remarks"></a>Notes

Chaque élément de l' `CMFCShellListCtrl` objet peut comporter du texte dans une ou plusieurs colonnes. Quand le Framework appelle cette méthode, il spécifie la colonne qui l’intéresse. Si vous appelez cette fonction manuellement, vous devez également spécifier la colonne qui vous intéresse.

Par défaut, cette méthode s’appuie sur le paramètre *pItem* pour déterminer l’élément à traiter. La valeur de *iItem* n’est pas utilisée dans l’implémentation par défaut.

##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns

L’infrastructure appelle cette méthode lorsqu’elle définit les noms des colonnes.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Notes

Par défaut, l’infrastructure crée quatre colonnes dans un `CMFCShellListCtrl` objet. Les noms de ces colonnes sont **nom**, **taille**, **type**et **modifié**. Vous pouvez remplacer cette méthode pour personnaliser le nombre de colonnes et leurs noms.

##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh

Actualise et repeint l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Valeur de retour

`S_OK`en cas de réussite; Sinon, une valeur d’erreur.

### <a name="remarks"></a>Notes

Appelez cette méthode pour actualiser la liste des éléments affichés par `CMFCShellListCtrl` l’objet.

##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes

Définit le type des éléments répertoriés dans l’objet [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Paramètres

*nTypes*<br/>
dans Liste des types d’éléments que l' `CMFCShellListCtrl` objet prend en charge.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la liste des types d’éléments, consultez [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl, classe](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl, classe](../../mfc/reference/cmfcshelltreectrl-class.md)
