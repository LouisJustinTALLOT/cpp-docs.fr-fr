---
title: COlePropertyPage, classe
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
ms.openlocfilehash: 872ade08438e54098da730012f98cdd906483887
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753788"
---
# <a name="colepropertypage-class"></a>COlePropertyPage, classe

Utilisée pour afficher les propriétés d'un contrôle personnalisé dans une interface graphique, similaire à une boîte de dialogue.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|Construit un objet `COlePropertyPage`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Indique si l’utilisateur a modifié la valeur du contrôle.|
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Retourne la gamme d’objets édités par la page de propriété.|
|[COlePropertyPage::GetPageSite](#getpagesite)|Retourne un pointeur à `IPropertyPageSite` l’interface de la page de propriété.|
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Détermine quels contrôles n’activent pas le bouton Apply.|
|[COlePropertyPage::IsModified](#ismodified)|Indique si l’utilisateur a modifié la page de propriété.|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Appelé par le cadre lorsque l’utilisateur modifie une propriété.|
|[COlePropertyPage::OnHelp](#onhelp)|Appelé par le cadre lorsque l’utilisateur invoque de l’aide.|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Appelé par le cadre lorsque la page de propriété est parasécée.|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Appelé par le cadre quand un autre contrôle OLE, avec de nouvelles propriétés, est choisi.|
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|Appelé par le cadre lorsque le cadre de la propriété fournit le site de la page.|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Définit un indicateur indiquant si l’utilisateur a modifié la valeur du contrôle.|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Définit la ressource de dialogue de la page de propriété.|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Définit le bref texte d’aide de la page de propriété, le nom de son fichier d’aide et son contexte d’aide.|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Définit un drapeau indiquant si l’utilisateur a modifié la page de propriété.|
|[COlePropertyPage::SetPageName](#setpagename)|Définit le nom de la page de propriété (légende).|

## <a name="remarks"></a>Notes

Par exemple, une page de propriété peut inclure un contrôle de modification qui permet à l’utilisateur de visualiser et de modifier la propriété de légende du contrôle.

Chaque propriété personnalisée ou de contrôle des stocks peut avoir un contrôle de dialogue qui permet à l’utilisateur du contrôle de visualiser la valeur actuelle de la propriété et de modifier cette valeur si nécessaire.

Pour plus d’informations sur l’utilisation `COlePropertyPage`, voir l’article [ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="colepropertypagecolepropertypage"></a><a name="colepropertypage"></a>COlePropertyPage::COlePropertyPage

Construit un objet `COlePropertyPage`.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Paramètres

*idDlg (en)*<br/>
Id de ressources du modèle de dialogue.

*idCaption (en)*<br/>
Id de ressources de la légende de la page de propriété.

### <a name="remarks"></a>Notes

Lorsque vous implémentez une sous-classe de , le constructeur de `COlePropertyPage`votre sous-classe doit utiliser le `COlePropertyPage` constructeur pour identifier la ressource de dialogue-modèle sur laquelle la page de propriété est basée et la ressource de chaîne contenant sa légende.

## <a name="colepropertypagegetcontrolstatus"></a><a name="getcontrolstatus"></a>COlePropertyPage::GetControlStatus

Détermine si l’utilisateur a modifié la valeur du contrôle de la page de propriété avec l’ID de ressource spécifié.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Id de ressources d’un contrôle de page de propriété.

### <a name="return-value"></a>Valeur de retour

VRAI si la valeur de contrôle a été modifiée; autrement FALSE.

## <a name="colepropertypagegetobjectarray"></a><a name="getobjectarray"></a>COlePropertyPage::GetObjectArray

Retourne la gamme d’objets édités par la page de propriété.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Paramètres

*pnObjects*<br/>
Pointeur vers un long integer non signé qui recevra le nombre d’objets édités par la page.

### <a name="return-value"></a>Valeur de retour

Pointeur à `IDispatch` un tableau de pointeurs, qui sont utilisés pour accéder aux propriétés de chaque contrôle sur la page de propriété. L’appelant ne doit pas libérer ces indications d’interface.

### <a name="remarks"></a>Notes

Chaque objet de page de propriété maintient `IDispatch` un tableau de pointeurs aux interfaces des objets édités par la page. Cette fonction définit son argument *pnObjects* au nombre d’éléments dans ce tableau et renvoie un pointeur au premier élément du tableau.

## <a name="colepropertypagegetpagesite"></a><a name="getpagesite"></a>COlePropertyPage::GetPageSite

Obtient un pointeur à `IPropertyPageSite` l’interface de la page de propriété.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur sur l’interface de la page de propriété. `IPropertyPageSite`

### <a name="remarks"></a>Notes

Les contrôles et les conteneurs coopèrent afin que les utilisateurs puissent parcourir et modifier les propriétés de contrôle. Le contrôle fournit des pages de propriété, dont chacune est un objet OLE qui permet à l’utilisateur de modifier un ensemble connexe de propriétés. Le conteneur fournit un cadre de propriété qui affiche les pages de propriété. Pour chaque page, le cadre de la `IPropertyPageSite` propriété fournit un site de page, qui prend en charge l’interface.

## <a name="colepropertypageignoreapply"></a><a name="ignoreapply"></a>COlePropertyPage::IgnoreApply

Détermine quels contrôles n’activent pas le bouton Apply.

```cpp
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
ID du contrôle à ignorer.

### <a name="remarks"></a>Notes

Le bouton Appliquer de la page de propriété n’est activé que lorsque les valeurs des contrôles de la page de propriété ont été modifiées. Utilisez cette fonction pour spécifier les contrôles qui ne permettent pas le bouton Apply lorsque leurs valeurs changent.

## <a name="colepropertypageismodified"></a><a name="ismodified"></a>COlePropertyPage::IsModified

Détermine si l’utilisateur a changé de valeur sur la page de propriété.

```
BOOL IsModified();
```

### <a name="return-value"></a>Valeur de retour

VRAI si la page de propriété a été modifiée.

## <a name="colepropertypageoneditproperty"></a><a name="oneditproperty"></a>COlePropertyPage::OnEditProperty

Le cadre appelle cette fonction lorsqu’une propriété spécifique doit être modifiée.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
Id d’expédition de la propriété en cours de modification.

### <a name="return-value"></a>Valeur de retour

La implémentation par défaut renvoie FALSE. Les remplacements de cette fonction doivent retourner VRAI.

### <a name="remarks"></a>Notes

Vous pouvez le remplacer pour définir l’accent sur le contrôle approprié sur la page. L’implémentation par défaut ne fait rien et renvoie FALSE.

## <a name="colepropertypageonhelp"></a><a name="onhelp"></a>COlePropertyPage::OnHelp

Le cadre appelle cette fonction lorsque l’utilisateur demande de l’aide en ligne.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Paramètres

*lpszHelpDir*<br/>
Répertoire contenant le fichier d’aide de la page de propriété.

### <a name="return-value"></a>Valeur de retour

La implémentation par défaut renvoie FALSE.

### <a name="remarks"></a>Notes

Remplacez-le si votre page de propriété doit effectuer une action spéciale lorsque l’utilisateur accède à l’aide. La mise en œuvre par défaut ne fait rien et renvoie FALSE, qui ordonne au cadre d’appeler WinHelp.

## <a name="colepropertypageoninitdialog"></a><a name="oninitdialog"></a>COlePropertyPage::OnInitDialog

Le cadre appelle cette fonction lorsque le dialogue de la page de propriété est paralysé.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

La implémentation par défaut renvoie FALSE.

### <a name="remarks"></a>Notes

Remplacez-le si une action spéciale est nécessaire lorsque le dialogue est paralysé. La implémentation par défaut appelle `CDialog::OnInitDialog` et renvoie FALSE.

## <a name="colepropertypageonobjectschanged"></a><a name="onobjectschanged"></a>COlePropertyPage::OnObjectsChanged

Appelé par le cadre quand un autre contrôle OLE, avec de nouvelles propriétés, est choisi.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Notes

Lors de l’affichage des propriétés d’un contrôle OLE dans l’environnement développeur, une boîte de dialogue sans mode est utilisé pour afficher ses pages de propriété. Si un autre contrôle est sélectionné, un ensemble différent de pages de propriété doit être affiché pour le nouvel ensemble de propriétés. Le cadre appelle cette fonction à informer la page de propriété de la modification.

Remplacez cette fonction pour recevoir la notification de cette action et effectuer toutes les actions spéciales.

## <a name="colepropertypageonsetpagesite"></a><a name="onsetpagesite"></a>COlePropertyPage::OnSetPageSite

Le cadre appelle cette fonction lorsque le cadre de propriété fournit le site de la page de propriété.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut charge la légende de la page et tente de déterminer la taille de la page à partir de la ressource de dialogue. Remplacer cette fonction si votre page de propriété nécessite une action supplémentaire; votre remplacement devrait appeler la mise en œuvre de la classe de base.

## <a name="colepropertypagesetcontrolstatus"></a><a name="setcontrolstatus"></a>COlePropertyPage::SetControlStatus

Modifie l’état d’un contrôle de page de propriété.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Contient l’ID d’un contrôle de page de propriété.

*bDirty (en)*<br/>
Précise si un champ de la page de propriété a été modifié. Définissez-le à VRAI si le champ a été modifié, FALSE s’il n’a pas été modifié.

### <a name="return-value"></a>Valeur de retour

VRAI, si le contrôle spécifié a été défini; autrement FALSE.

### <a name="remarks"></a>Notes

Si l’état d’un contrôle de page de propriété est sale lorsque la page de propriété est fermée ou que le bouton Apply est choisi, la propriété du contrôle sera mise à jour avec la valeur appropriée.

## <a name="colepropertypagesetdialogresource"></a><a name="setdialogresource"></a>COlePropertyPage::SetDialogResource

Définit la ressource de dialogue de la page de propriété.

```cpp
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Paramètres

*hDialog (en)*<br/>
Gérer la ressource de dialogue de la page de propriété.

## <a name="colepropertypagesethelpinfo"></a><a name="sethelpinfo"></a>COlePropertyPage::SetHelpInfo

Spécifie les informations de pointe d’outil, le nom de fichier d’aide, et le contexte d’aide pour votre page de propriété.

```cpp
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Paramètres

*lpszDocString (en)*<br/>
Une chaîne contenant de brèves informations d’aide pour l’affichage dans une barre d’état ou un autre endroit.

*lpszHelpFile*<br/>
Nom du fichier d’aide de la page de propriété.

*dwHelpContexte*<br/>
Contexte d’aide pour la page de propriété.

## <a name="colepropertypagesetmodifiedflag"></a><a name="setmodifiedflag"></a>COlePropertyPage::SetModifiedFlag

Indique si l’utilisateur a modifié la page de propriété.

```cpp
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Paramètres

*bModifié*<br/>
Spécifie la nouvelle valeur du drapeau modifié de la page de propriété.

## <a name="colepropertypagesetpagename"></a><a name="setpagename"></a>COlePropertyPage::SetPageName

Définit le nom de la page de propriété, que le cadre de propriété affichera généralement sur l’onglet de la page.

```cpp
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Paramètres

*lpszPageName*<br/>
Pointeur vers une chaîne contenant le nom de la page de propriété.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon CIRC3](../../overview/visual-cpp-samples.md)<br/>
[MFC Échantillon TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)
