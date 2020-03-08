---
title: COlePropertyPage (classe)
ms.date: 11/04/2016
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
ms.openlocfilehash: 8253b2c2fa6b93ec51c7ede983ef710eed039970
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865884"
---
# <a name="colepropertypage-class"></a>COlePropertyPage (classe)

Utilisée pour afficher les propriétés d'un contrôle personnalisé dans une interface graphique, similaire à une boîte de dialogue.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[COlePropertyPage :: COlePropertyPage](#colepropertypage)|Construit un objet `COlePropertyPage`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[COlePropertyPage :: GetControlStatus](#getcontrolstatus)|Indique si l’utilisateur a modifié la valeur dans le contrôle.|
|[COlePropertyPage :: GetObjectArray](#getobjectarray)|Retourne le tableau d’objets en cours de modification par la page de propriétés.|
|[COlePropertyPage :: GetPageSite](#getpagesite)|Retourne un pointeur vers l’interface `IPropertyPageSite` de la page de propriétés.|
|[COlePropertyPage :: IgnoreApply](#ignoreapply)|Détermine les contrôles qui n’activent pas le bouton appliquer.|
|[COlePropertyPage :: IsModified](#ismodified)|Indique si l’utilisateur a modifié la page de propriétés.|
|[COlePropertyPage :: OnEditProperty](#oneditproperty)|Appelée par l’infrastructure quand l’utilisateur modifie une propriété.|
|[COlePropertyPage :: OnHelp](#onhelp)|Appelé par le Framework lorsque l’utilisateur appelle l’aide.|
|[COlePropertyPage :: OnInitDialog](#oninitdialog)|Appelé par le Framework lorsque la page de propriétés est initialisée.|
|[COlePropertyPage :: OnObjectsChanged](#onobjectschanged)|Appelée par l’infrastructure lorsqu’un autre contrôle OLE, avec de nouvelles propriétés, est choisi.|
|[COlePropertyPage :: OnSetPageSite](#onsetpagesite)|Appelé par le Framework lorsque le frame de propriété fournit le site de la page.|
|[COlePropertyPage :: SetControlStatus](#setcontrolstatus)|Définit un indicateur qui spécifie si l’utilisateur a modifié la valeur dans le contrôle.|
|[COlePropertyPage :: SetDialogResource](#setdialogresource)|Définit la ressource de boîte de dialogue de la page de propriétés.|
|[COlePropertyPage :: SetHelpInfo](#sethelpinfo)|Définit le bref texte d’aide de la page de propriétés, le nom de son fichier d’aide et son contexte d’aide.|
|[COlePropertyPage :: SetModifiedFlag](#setmodifiedflag)|Définit un indicateur qui spécifie si l’utilisateur a modifié la page de propriétés.|
|[COlePropertyPage :: SetPageName](#setpagename)|Définit le nom de la page de propriétés (Caption).|

## <a name="remarks"></a>Notes

Par exemple, une page de propriétés peut inclure un contrôle d’édition qui permet à l’utilisateur d’afficher et de modifier la propriété de légende du contrôle.

Chaque propriété de contrôle personnalisé ou stock peut avoir un contrôle de boîte de dialogue qui permet à l’utilisateur du contrôle d’afficher la valeur de la propriété actuelle et de modifier cette valeur si nécessaire.

Pour plus d’informations sur l’utilisation de `COlePropertyPage`, consultez l’article [contrôles ActiveX : pages de propriétés](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

##  <a name="colepropertypage"></a>COlePropertyPage :: COlePropertyPage

Construit un objet `COlePropertyPage`.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Paramètres

*idDlg*<br/>
ID de ressource du modèle de boîte de dialogue.

*idCaption*<br/>
ID de ressource de la légende de la page de propriétés.

### <a name="remarks"></a>Notes

Quand vous implémentez une sous-classe de `COlePropertyPage`, le constructeur de votre sous-classe doit utiliser le constructeur `COlePropertyPage` pour identifier la ressource de modèle de boîte de dialogue sur laquelle la page de propriétés est basée et la ressource de chaîne contenant sa légende.

##  <a name="getcontrolstatus"></a>COlePropertyPage :: GetControlStatus

Détermine si l’utilisateur a modifié la valeur du contrôle de page de propriétés avec l’ID de ressource spécifié.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
ID de ressource d’un contrôle de page de propriétés.

### <a name="return-value"></a>Valeur de retour

TRUE si la valeur du contrôle a été modifiée ; Sinon, FALSe.

##  <a name="getobjectarray"></a>COlePropertyPage :: GetObjectArray

Retourne le tableau d’objets en cours de modification par la page de propriétés.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Paramètres

*pnObjects*<br/>
Pointeur vers un entier long non signé qui recevra le nombre d’objets en cours de modification par la page.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un tableau de pointeurs `IDispatch`, qui sont utilisés pour accéder aux propriétés de chaque contrôle sur la page de propriétés. L’appelant ne doit pas libérer ces pointeurs d’interface.

### <a name="remarks"></a>Notes

Chaque objet de page de propriétés conserve un tableau de pointeurs vers les interfaces `IDispatch` des objets en cours de modification par la page. Cette fonction définit son argument *pnObjects* sur le nombre d’éléments de ce tableau et retourne un pointeur vers le premier élément du tableau.

##  <a name="getpagesite"></a>COlePropertyPage :: GetPageSite

Obtient un pointeur vers l’interface `IPropertyPageSite` de la page de propriétés.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface `IPropertyPageSite` de la page de propriétés.

### <a name="remarks"></a>Notes

Les contrôles et les conteneurs coopèrent afin que les utilisateurs puissent parcourir et modifier les propriétés des contrôles. Le contrôle fournit des pages de propriétés, chacune d’elles étant un objet OLE qui permet à l’utilisateur de modifier un ensemble de propriétés associé. Le conteneur fournit un frame de propriété qui affiche les pages de propriétés. Pour chaque page, le frame de propriété fournit un site de page, qui prend en charge l’interface `IPropertyPageSite`.

##  <a name="ignoreapply"></a>COlePropertyPage :: IgnoreApply

Détermine les contrôles qui n’activent pas le bouton appliquer.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
ID du contrôle à ignorer.

### <a name="remarks"></a>Notes

Le bouton appliquer de la page de propriétés est activé uniquement lorsque les valeurs des contrôles de la page de propriétés ont été modifiées. Utilisez cette fonction pour spécifier des contrôles qui n’entraînent pas l’activation du bouton appliquer lorsque leurs valeurs changent.

##  <a name="ismodified"></a>COlePropertyPage :: IsModified

Détermine si l’utilisateur a modifié les valeurs de la page de propriétés.

```
BOOL IsModified();
```

### <a name="return-value"></a>Valeur de retour

TRUE si la page de propriétés a été modifiée.

##  <a name="oneditproperty"></a>COlePropertyPage :: OnEditProperty

L’infrastructure appelle cette fonction lorsqu’une propriété spécifique doit être modifiée.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Paramètres

*égal*<br/>
ID de dispatch de la propriété en cours de modification.

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut retourne FALSe. Les substitutions de cette fonction doivent retourner la valeur TRUE.

### <a name="remarks"></a>Notes

Vous pouvez la remplacer pour définir le focus sur le contrôle approprié sur la page. L’implémentation par défaut ne fait rien et retourne FALSe.

##  <a name="onhelp"></a>COlePropertyPage :: OnHelp

L’infrastructure appelle cette fonction lorsque l’utilisateur demande de l’aide en ligne.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Paramètres

*lpszHelpDir*<br/>
Répertoire contenant le fichier d’aide de la page de propriétés.

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut retourne FALSe.

### <a name="remarks"></a>Notes

Remplacez-la si votre page de propriétés doit effectuer une action spéciale lorsque l’utilisateur accède à l’aide. L’implémentation par défaut ne fait rien et retourne FALSe, qui indique à l’infrastructure d’appeler WinHelp.

##  <a name="oninitdialog"></a>COlePropertyPage :: OnInitDialog

L’infrastructure appelle cette fonction lorsque la boîte de dialogue de la page de propriétés est initialisée.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut retourne FALSe.

### <a name="remarks"></a>Notes

Remplacez-la si une action spéciale est requise lorsque la boîte de dialogue est initialisée. L’implémentation par défaut appelle `CDialog::OnInitDialog` et retourne FALSe.

##  <a name="onobjectschanged"></a>COlePropertyPage :: OnObjectsChanged

Appelée par l’infrastructure lorsqu’un autre contrôle OLE, avec de nouvelles propriétés, est choisi.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Notes

Lorsque vous affichez les propriétés d’un contrôle OLE dans l’environnement de développement, une boîte de dialogue non modale est utilisée pour afficher ses pages de propriétés. Si un autre contrôle est sélectionné, un ensemble différent de pages de propriétés doit être affiché pour le nouvel ensemble de propriétés. L’infrastructure appelle cette fonction pour notifier la page de propriétés de la modification.

Remplacez cette fonction pour recevoir une notification de cette action et effectuer toutes les actions spéciales.

##  <a name="onsetpagesite"></a>COlePropertyPage :: OnSetPageSite

L’infrastructure appelle cette fonction lorsque le frame de propriété fournit le site de la page de propriétés.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut charge la légende de la page et tente de déterminer la taille de la page à partir de la ressource de boîte de dialogue. Substituez cette fonction si la page de propriétés requiert une action supplémentaire ; votre substitution doit appeler l’implémentation de la classe de base.

##  <a name="setcontrolstatus"></a>COlePropertyPage :: SetControlStatus

Modifie l’état d’un contrôle de page de propriétés.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Contient l’ID d’un contrôle de page de propriétés.

*bDirty*<br/>
Spécifie si un champ de la page de propriétés a été modifié. A la valeur TRUE si le champ a été modifié, FALSe s’il n’a pas été modifié.

### <a name="return-value"></a>Valeur de retour

TRUE si le contrôle spécifié a été défini ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si l’état d’un contrôle de page de propriétés est modifié lorsque la page de propriétés est fermée ou que le bouton appliquer est sélectionné, la propriété du contrôle est mise à jour avec la valeur appropriée.

##  <a name="setdialogresource"></a>COlePropertyPage :: SetDialogResource

Définit la ressource de boîte de dialogue de la page de propriétés.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Paramètres

*hDialog*<br/>
Handle vers la ressource de boîte de dialogue de la page de propriétés.

##  <a name="sethelpinfo"></a>COlePropertyPage :: SetHelpInfo

Spécifie les informations d’info-bulle, le nom de fichier d’aide et le contexte d’aide de votre page de propriétés.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Paramètres

*lpszDocString*<br/>
Chaîne contenant des informations d’aide brèves pour l’affichage dans une barre d’État ou un autre emplacement.

*lpszHelpFile*<br/>
Nom du fichier d’aide de la page de propriétés.

*dwHelpContext*<br/>
Contexte d’aide pour la page de propriétés.

##  <a name="setmodifiedflag"></a>COlePropertyPage :: SetModifiedFlag

Indique si l’utilisateur a modifié la page de propriétés.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Paramètres

*bModified*<br/>
Spécifie la nouvelle valeur de l’indicateur de modification de la page de propriétés.

##  <a name="setpagename"></a>COlePropertyPage :: SetPageName

Définit le nom de la page de propriétés, que le frame de propriété affichera généralement dans l’onglet de la page.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Paramètres

*lpszPageName*<br/>
Pointeur vers une chaîne contenant le nom de la page de propriétés.

## <a name="see-also"></a>Voir aussi

[Exemple MFC CIRC3](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)
