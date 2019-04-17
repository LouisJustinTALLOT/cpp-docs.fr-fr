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
ms.openlocfilehash: a513a5e85ae5cf00f7ea874967a709245e016b34
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772109"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl, classe

Le `CMFCShellListCtrl` classe fournit des fonctionnalités de contrôle de liste Windows et se développe en incluant la possibilité d’afficher une liste d’éléments de l’interpréteur de commandes.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Affiche une liste d’éléments qui sont contenus dans un dossier fourni.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Affiche une liste d’éléments qui sont contenus dans le dossier qui est le parent du dossier actuellement affiché.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Active ou désactive le menu contextuel.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Récupère le chemin d’accès du dossier actif.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Récupère le nom du dossier actif.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Retourne le PIDL de l’élément de contrôle de liste actuel.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Retourne un pointeur vers le dossier d’interpréteur de commandes en cours.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Retourne le chemin d’accès textuelle d’un élément.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Retourne les types d’éléments de Shell qui sont affichés par le contrôle de liste.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Vérifie si le dossier actuellement sélectionné est le dossier Bureau.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|L’infrastructure appelle cette méthode lorsqu’il compare deux éléments. (Substitue [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Appelé lorsque le framework récupère la date du fichier affichée par le contrôle de liste.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Appelé lorsque le framework convertit la taille du fichier d’un contrôle de liste.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Appelé lorsque le framework récupère l’icône d’un élément de contrôle de liste.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Appelé lorsque le framework convertit le texte d’un élément de contrôle de liste.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Appelé par l’infrastructure lorsqu’elle définit les noms des colonnes.|
|[CMFCShellListCtrl::Refresh](#refresh)|Actualise et redessine le contrôle de liste.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Définit le type d’éléments affichés par le contrôle de liste.|

## <a name="remarks"></a>Notes

Le `CMFCShellListCtrl` classe étend les fonctionnalités de la [cmfclistctrl, classe](../../mfc/reference/cmfclistctrl-class.md) en activant votre programme répertorier les éléments du shell Windows. Le format d’affichage qui est utilisé est similaire à celui d’un affichage de liste pour une fenêtre d’Explorateur.

Un [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objet peut être associé un `CMFCShellListCtrl` objet à créer une fenêtre d’Explorateur terminée. Puis, en sélectionnant un élément dans le `CMFCShellTreeCtrl` entraîne la `CMFCShellListCtrl` objet pour répertorier le contenu de l’élément sélectionné.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer un objet de la `CMFCShellListCtrl` classe et comment afficher le dossier parent du dossier actuellement affiché. Cet extrait de code fait partie de la [exemple Explorer](../../overview/visual-cpp-samples.md).

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

**En-tête :** afxshelllistCtrl.h

##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder

Affiche une liste d’éléments qui sont contenus dans le dossier fourni.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
[in] Chaîne qui contient le chemin d’accès d’un dossier.

*lpItemInfo*<br/>
[in] Un pointeur vers un `LPAFX_SHELLITEMINFO` structure qui décrit un dossier à afficher.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; E_FAIL sinon.

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

Mises à jour le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet pour afficher le dossier parent du dossier actuellement affiché.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; E_FAIL sinon.

##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu

Active le menu contextuel.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[in] Valeur booléenne qui spécifie si le framework Active le menu contextuel.

##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder

Récupère le chemin d’accès du dossier actuellement sélectionné dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Paramètres

*strPath*<br/>
[out] Une référence à un paramètre de chaîne dans laquelle la méthode écrit le chemin d’accès.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; 0 dans le cas contraire.

### <a name="remarks"></a>Notes

Cette méthode échoue si aucun dossier sélectionné dans le `CMFCShellListCtrl`.

##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName

Récupère le nom du dossier actuellement sélectionné dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
[out] Une référence à un paramètre de chaîne dans laquelle la méthode écrit le nom.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; 0 dans le cas contraire.

### <a name="remarks"></a>Notes

Cette méthode échoue si aucun dossier sélectionné dans le `CMFCShellListCtrl`.

##  <a name="getcurrentitemidlist"></a>  CMFCShellListCtrl::GetCurrentItemIdList

Retourne le PIDL de l’élément actuellement sélectionné.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Valeur de retour

PIDL de l’élément actuel.

##  <a name="getcurrentshellfolder"></a>  CMFCShellListCtrl::GetCurrentShellFolder

Obtient un pointeur vers l’élément actuellement sélectionné dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le [IShellFolder Interface](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ishellfolder) pour l’objet sélectionné.

### <a name="remarks"></a>Notes

Cette méthode retourne NULL si aucun objet n’est actuellement sélectionné.

##  <a name="getitempath"></a>  CMFCShellListCtrl::GetItemPath

Récupère le chemin d’accès pour un élément.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Paramètres

*strPath*<br/>
[out] Une référence à une chaîne qui reçoit le chemin d’accès.

*iItem*<br/>
[in] Index de l’élément de liste.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite ; FALSE sinon.

### <a name="remarks"></a>Notes

L’index fourni par *iItem* repose sur les éléments actuellement affichés par le [CMFCShellListCtrl, classe](../../mfc/reference/cmfcshelllistctrl-class.md) objet.

##  <a name="getitemtypes"></a>  CMFCShellListCtrl::GetItemTypes

Retourne le type d’éléments affichés par le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Valeur de retour

Un [SHCONTF](/windows/desktop/api/shobjidl_core/ne-shobjidl_core-_shcontf) valeur qui contient le type d’éléments répertoriés dans le `CMFCShellListCtrl`.

### <a name="remarks"></a>Notes

Pour définir le type d’éléments répertoriés dans un `CMFCShellListCtrl`, appelez [CMFCShellListCtrl::SetItemTypes](#setitemtypes).

##  <a name="isdesktop"></a>  CMFCShellListCtrl::IsDesktop

Détermine si le dossier qui est affiché dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet est le dossier Bureau.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le dossier affiché est le dossier Bureau ; FALSE sinon.

##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Paramètres

[in] *lParam1*<br/>
[in] *lParam2*<br/>
[in] *iColumn*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate

L’infrastructure appelle cette méthode quand il doit convertir la date associée à un objet dans une chaîne.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*tmFile*<br/>
[in] La date associée à un fichier.

*str*<br/>
[out] Chaîne qui contient la date de mise en forme de fichier.

### <a name="remarks"></a>Notes

Quand un [CMFCShellListCtrl, classe](../../mfc/reference/cmfcshelllistctrl-class.md) objet affiche la date associée à un fichier, il doit convertir cette date dans un format de chaîne. Le `CMFCShellListCtrl` utilise cette méthode pour effectuer cette conversion. Par défaut, cette méthode utilise les paramètres régionaux actuels pour mettre en forme la date en une chaîne.

##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize

L’infrastructure appelle cette méthode lorsqu’il convertit la taille d’un objet en une chaîne.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*lFileSize*<br/>
[in] La taille du fichier que le framework affichera.

*str*<br/>
[out] Chaîne qui contient la taille du fichier de mise en forme.

### <a name="remarks"></a>Notes

Quand un [CMFCShellListCtrl, classe](../../mfc/reference/cmfcshelllistctrl-class.md) objet doit afficher la taille d’un fichier, il doit convertir la taille du fichier dans un format de chaîne. Le `CMFCShellListCtrl` utilise cette méthode pour effectuer cette conversion. Par défaut, cette méthode convertit la taille du fichier à partir d’octets à kilo-octets et utilise ensuite les paramètres régionaux actuels pour mettre en forme la taille en chaîne.

##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon

L’infrastructure appelle cette méthode pour récupérer l’icône associée à un élément de liste de shell.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
[in] L’index de l’élément.

*pItem*<br/>
[in] Un paramètre LPAFX_SHELLITEMINFO qui décrit l’élément.

### <a name="return-value"></a>Valeur de retour

L’index de l’image d’icône en cas de réussite ; -1 si la fonction échoue.

### <a name="remarks"></a>Notes

L’index d’image icône repose sur la liste d’images système.

Par défaut, cette méthode s’appuie sur le *pItem* paramètre. La valeur de *iItem* n’est pas utilisé dans l’implémentation par défaut. Vous pouvez utiliser *iItem* pour implémenter un comportement personnalisé.

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

L’infrastructure appelle cette méthode lorsqu’il doit récupérer le texte d’un élément de l’interpréteur de commandes.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
[in] L’index de l’élément.

*iColumn*<br/>
[in] La colonne concernée.

*pItem*<br/>
[in] Un paramètre LPAFX_SHELLITEMINFO qui décrit l’élément.

### <a name="return-value"></a>Valeur de retour

Un `CString` qui contient le texte associé à l’élément.

### <a name="remarks"></a>Notes

Chaque élément dans le `CMFCShellListCtrl` objet peut avoir de texte dans une ou plusieurs colonnes. Lorsque l’infrastructure appelle cette méthode, il spécifie la colonne qui l’intéressent. Si vous appelez cette fonction manuellement, vous devez également spécifier la colonne qui vous intéresse.

Par défaut, cette méthode s’appuie sur le *pItem* paramètre pour déterminer quel élément au processus. La valeur de *iItem* n’est pas utilisé dans l’implémentation par défaut.

##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns

L’infrastructure appelle cette méthode lorsqu’il définit les noms des colonnes.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Notes

Par défaut, l’infrastructure crée quatre colonnes dans un `CMFCShellListCtrl` objet. Les noms de ces colonnes sont **nom**, **taille**, **Type**, et **Modified**. Vous pouvez remplacer cette méthode pour personnaliser le nombre de colonnes et leurs noms.

##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh

Actualise et redessine le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Valeur de retour

`S_OK` en cas de réussite ; Sinon, une valeur d’erreur.

### <a name="remarks"></a>Notes

Appelez cette méthode pour actualiser la liste des éléments affichés par le `CMFCShellListCtrl` objet.

##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes

Définit le type d’éléments qui figurent dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Paramètres

*nTypes*<br/>
[in] Une liste d’éléments types que le `CMFCShellListCtrl` prend en charge de l’objet.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la liste des types d’éléments, consultez [SHCONTF](/windows/desktop/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl, classe](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl, classe](../../mfc/reference/cmfcshelltreectrl-class.md)
