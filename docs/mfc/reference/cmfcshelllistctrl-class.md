---
title: Classe de CMFCShellListCtrl affichant | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9073c3443b1c74a27c9de9be142c67fab7f40ba8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcshelllistctrl-class"></a>Classe de CMFCShellListCtrl affichant
La `CMFCShellListCtrl` classe fournit les fonctionnalités de contrôle de liste Windows et les étend en incluant la possibilité d’afficher une liste des éléments du shell.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Affiche une liste d’éléments contenus dans un dossier fourni.|  
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Affiche une liste d’éléments contenus dans le dossier qui est le parent du dossier actuellement affiché.|  
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Active ou désactive le menu contextuel.|  
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Récupère le chemin d’accès du dossier actif.|  
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Récupère le nom du dossier actif.|  
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Retourne le PIDL de l’élément de contrôle de liste actuel.|  
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Retourne un pointeur vers le dossier d’environnement actuels.|  
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Retourne le chemin d’accès textuelle d’un élément.|  
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Retourne les types d’éléments de Shell qui sont affichés par le contrôle de liste.|  
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Vérifie si le dossier actuellement sélectionné est le dossier Bureau.|  
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|L’infrastructure appelle cette méthode lorsqu’il compare deux éléments. (Substitue [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|  
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Appelé lorsque le framework récupère la date du fichier affichée par le contrôle de liste.|  
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Appelé lorsque l’infrastructure convertit la taille du fichier d’un contrôle de liste.|  
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Appelé lorsque le framework récupère l’icône d’un élément de contrôle de liste.|  
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Appelé lorsque le framework convertit le texte d’un élément de contrôle de liste.|  
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Appelé par l’infrastructure lorsqu’elle définit les noms des colonnes.|  
|[CMFCShellListCtrl::Refresh](#refresh)|Actualise et redessine le contrôle de liste.|  
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Définit le type d’éléments affichés par le contrôle de liste.|  
  
## <a name="remarks"></a>Notes  
 Le `CMFCShellListCtrl` classe étend les fonctionnalités de la [CMFCListCtrl classe](../../mfc/reference/cmfclistctrl-class.md) par l’activation de votre programme à la liste des éléments du shell Windows. Le format d’affichage utilisé est similaire à celle d’un affichage de liste pour une fenêtre d’Explorateur.  
  
 A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objet peut être associé un `CMFCShellListCtrl` objet pour créer une fenêtre d’Explorateur terminée. Puis, en sélectionnant un élément dans le `CMFCShellTreeCtrl` entraîne la `CMFCShellListCtrl` objet pour répertorier le contenu de l’élément sélectionné.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un objet de la `CMFCShellListCtrl` classe et comment afficher le dossier parent du dossier actuellement affiché. Cet extrait de code fait partie de la [exemple d’Explorateur](../../visual-cpp-samples.md).  
  
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
 **En-tête :** afxshelllistCtrl.h  
  
##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder  
 Affiche une liste d’éléments contenus dans le dossier fourni.  
  
```  
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszPath`  
 Chaîne qui contient le chemin d’accès d’un dossier.  
  
 [in] `lpItemInfo`  
 Un pointeur vers un `LPAFX_SHELLITEMINFO` structure qui décrit un dossier à afficher.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` en cas de réussite ; `E_FAIL` dans le cas contraire.  
  
##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder  
 Les mises à jour le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet pour afficher le dossier parent du dossier actuellement affiché.  
  
```  
virtual HRESULT DisplayParentFolder();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` en cas de réussite ; `E_FAIL` dans le cas contraire.  
  
##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu  
 Active le menu contextuel.  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 Valeur booléenne qui spécifie si le framework Active le menu contextuel.  
  
##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder  
 Récupère le chemin d’accès du dossier actuellement sélectionné dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.  
  
```  
BOOL GetCurrentFolder(CString& strPath) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `strPath`  
 Une référence à un paramètre de chaîne dans laquelle la méthode écrit le chemin d’accès.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi ; 0 dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Cette méthode échoue si aucun dossier sélectionné dans le `CMFCShellListCtrl`.  
  
##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName  
 Récupère le nom du dossier actuellement sélectionné dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.  
  
```  
BOOL GetCurrentFolderName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `strName`  
 Une référence à un paramètre de chaîne dans laquelle la méthode écrit le nom.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi ; 0 dans le cas contraire.  
  
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
 Un pointeur vers le [IShellFolder Interface](http://msdn.microsoft.com/library/windows/desktop/bb775075) pour l’objet sélectionné.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne `NULL` si aucun objet n’est actuellement sélectionné.  
  
##  <a name="getitempath"></a>  CMFCShellListCtrl::GetItemPath  
 Récupère le chemin d’accès d’un élément.  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    int iItem) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `strPath`  
 Une référence à une chaîne qui reçoit le chemin d’accès.  
  
 [in] `iItem`  
 Index de l’élément de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` en cas de réussite ; `FALSE` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 L’index fourni par `iItem` est basée sur les éléments actuellement affichés par le [CMFCShellListCtrl affichant classe](../../mfc/reference/cmfcshelllistctrl-class.md) objet.  
  
##  <a name="getitemtypes"></a>  CMFCShellListCtrl::GetItemTypes  
 Retourne le type d’éléments affichés par le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.  
  
```  
SHCONTF GetItemTypes() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539) valeur qui contient le type d’éléments répertoriés dans le `CMFCShellListCtrl`.  
  
### <a name="remarks"></a>Notes  
 Pour définir le type d’éléments répertoriés dans un `CMFCShellListCtrl`, appelez [CMFCShellListCtrl::SetItemTypes](#setitemtypes).  
  
##  <a name="isdesktop"></a>  CMFCShellListCtrl::IsDesktop  
 Détermine si le dossier qui est affiché dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet est le dossier Bureau.  
  
```  
BOOL IsDesktop() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le dossier affiché est le dossier Bureau. `FALSE` dans le cas contraire.  
  
##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lParam1`  
 [in] `lParam2`  
 [in] `iColumn`  
  
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
 [in] `tmFile`  
 La date associée à un fichier.  
  
 [out] `str`  
 Chaîne qui contient la date du fichier de mise en forme.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un [CMFCShellListCtrl affichant classe](../../mfc/reference/cmfcshelllistctrl-class.md) objet affiche la date associée à un fichier, elle doit convertir cette date en un format de chaîne. Le `CMFCShellListCtrl` utilise cette méthode pour effectuer cette conversion. Par défaut, cette méthode utilise les paramètres régionaux pour mettre en forme la date en une chaîne.  
  
##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize  
 L’infrastructure appelle cette méthode lorsqu’il convertit une chaîne de la taille d’un objet.  
  
```  
virtual void OnFormatFileSize(
    long lFileSize,  
    CString& str);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lFileSize`  
 La taille du fichier qui affiche l’infrastructure.  
  
 [out] `str`  
 Chaîne qui contient la taille du fichier de mise en forme.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un [CMFCShellListCtrl affichant classe](../../mfc/reference/cmfcshelllistctrl-class.md) objet doit afficher la taille d’un fichier, il doit convertir la taille du fichier dans un format de chaîne. Le `CMFCShellListCtrl` utilise cette méthode pour effectuer cette conversion. Par défaut, cette méthode convertit la taille du fichier à partir d’octets en kilo-octets et utilise ensuite les paramètres régionaux pour mettre en forme la taille en chaîne.  
  
##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon  
 L’infrastructure appelle cette méthode pour récupérer l’icône associée à un élément de liste de shell.  
  
```  
virtual int OnGetItemIcon(
    int iItem,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iItem`  
 L’index de l’élément.  
  
 [in] `pItem`  
 A `LPAFX_SHELLITEMINFO` paramètre qui décrit l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’image d’icône en cas de réussite ; -1 si la fonction échoue.  
  
### <a name="remarks"></a>Notes  
 L’index d’image icône repose sur la liste d’images système.  
  
 Par défaut, cette méthode s’appuie sur la `pItem` paramètre. La valeur de `iItem` n’est pas utilisé dans l’implémentation par défaut. Vous pouvez utiliser `iItem` pour implémenter un comportement personnalisé.  
  
##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText  
 L’infrastructure appelle cette méthode lorsqu’il doit récupérer le texte d’un élément de l’interpréteur de commandes.  
  
```  
virtual CString OnGetItemText(
    int iItem,  
    int iColumn,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iItem`  
 L’index de l’élément.  
  
 [in] `iColumn`  
 La colonne concernée.  
  
 [in] `pItem`  
 A `LPAFX_SHELLITEMINFO` paramètre qui décrit l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` qui contient le texte associé à l’élément.  
  
### <a name="remarks"></a>Notes  
 Chaque élément dans le `CMFCShellListCtrl` objet peut avoir de texte dans une ou plusieurs colonnes. Lorsque l’infrastructure appelle cette méthode, il spécifie la colonne qui l’intéressent. Si vous appelez cette fonction manuellement, vous devez également spécifier la colonne qui vous intéressez.  
  
 Par défaut, cette méthode s’appuie sur la `pItem` paramètre pour déterminer quel élément au processus. La valeur de `iItem` n’est pas utilisé dans l’implémentation par défaut.  
  
##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns  
 L’infrastructure appelle cette méthode lorsqu’elle définit les noms des colonnes.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Notes  
 Par défaut, l’infrastructure crée quatre colonnes dans un `CMFCShellListCtrl` objet. Les noms de ces colonnes sont `Name`, `Size`, `Type`, et `Modified`. Vous pouvez substituer cette méthode pour personnaliser le nombre de colonnes et de leurs noms.  
  
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
 Définit le type des éléments qui sont répertoriées dans le [CMFCShellListCtrl affichant](../../mfc/reference/cmfcshelllistctrl-class.md) objet.  
  
```  
void SetItemTypes(SHCONTF nTypes);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nTypes`  
 Les types d’élément de liste qui le `CMFCShellListCtrl` prend en charge de l’objet.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur la liste des types d’éléments, consultez [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl, classe](../../mfc/reference/cmfcshelltreectrl-class.md)
