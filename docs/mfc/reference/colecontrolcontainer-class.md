---
description: 'En savoir plus sur : classe COleControlContainer'
title: COleControlContainer, classe
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: 6a798b7556e22ec2d2ed2a118182e946753452b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227531"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer, classe

Agit comme un conteneur de contrôles pour les contrôles ActiveX.

## <a name="syntax"></a>Syntaxe

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Construit un objet `COleControlContainer`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Crée un site de contrôle, hébergé par le conteneur.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informe tous les contrôles hébergés qu’une propriété ambiante a changé.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modifie le contrôle bouton spécifié.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Sélectionne la case d’option spécifiée d’un groupe.|
|[COleControlContainer :: CreateControl](#createcontrol)|Crée un contrôle ActiveX hébergé.|
|[COleControlContainer::CreateOleFont](#createolefont)|Crée une police OLE.|
|[COleControlContainer::FindItem](#finditem)|Retourne le site personnalisé du contrôle spécifié.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Détermine si le site de contrôle accepte des événements.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Récupère la propriété ambiante spécifiée.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Récupère le contrôle de boîte de dialogue spécifié.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Récupère la valeur du contrôle de boîte de dialogue spécifié.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Récupère la légende du contrôle de boîte de dialogue spécifié.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Détermine si le conteneur gère WM_SETFOCUS messages.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Gère les messages envoyés à un contrôle sans fenêtre.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Détermine l’état du bouton spécifié.|
|[COleControlContainer :: OnPaint](#onpaint)|Appelé pour repeindre une partie du conteneur.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Appelé lorsqu’un contrôle est sur le point d’être activé sur place.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Appelé lorsqu’un contrôle va être désactivé.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Appelée par l’infrastructure quand des messages de défilement sont reçus à partir d’une fenêtre enfant.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Envoie un message au contrôle spécifié.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Définit la valeur du contrôle spécifié.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Définit le texte du contrôle spécifié.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleControlContainer :: m_crBack](#m_crback)|Couleur d’arrière-plan du conteneur.|
|[COleControlContainer :: m_crFore](#m_crfore)|Couleur de premier plan du conteneur.|
|[COleControlContainer :: m_listSitesOrWnds](#m_listsitesorwnds)|Liste des sites de contrôle pris en charge.|
|[COleControlContainer :: m_nWindowlessControls](#m_nwindowlesscontrols)|Nombre de contrôles hébergés sans fenêtre.|
|[COleControlContainer :: m_pOleFont](#m_polefont)|Pointeur vers la police OLE du site de contrôle personnalisé.|
|[COleControlContainer :: m_pSiteCapture](#m_psitecapture)|Pointeur vers le site de contrôle de capture.|
|[COleControlContainer :: m_pSiteFocus](#m_psitefocus)|Pointeur vers le contrôle qui a actuellement le focus d’entrée.|
|[COleControlContainer :: m_pSiteUIActive](#m_psiteuiactive)|Pointeur vers le contrôle actuellement activé sur place.|
|[COleControlContainer :: m_pWnd](#m_pwnd)|Pointeur vers la fenêtre qui implémente le conteneur de contrôle.|
|[COleControlContainer :: m_siteMap](#m_sitemap)|Plan du site.|

## <a name="remarks"></a>Notes

Cela s’effectue en fournissant la prise en charge d’un ou plusieurs sites de contrôle ActiveX (implémentés par `COleControlSite` ). `COleControlContainer` implémente entièrement les interfaces [IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) et [IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) , ce qui permet aux contrôles ActiveX contenus de traiter leurs qualifications comme des éléments sur place.

En général, cette classe est utilisée conjointement avec `COccManager` et `COleControlSite` pour implémenter un conteneur de contrôles ActiveX personnalisé, avec des sites personnalisés pour un ou plusieurs contrôles ActiveX.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Spécifications

**En-tête :** afxocc. h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a> COleControlContainer::AttachControlSite

Appelé par l’infrastructure pour créer et attacher un site de contrôle.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers un objet `CWnd`.

*nIDC*<br/>
ID du contrôle à attacher.

### <a name="remarks"></a>Notes

Remplacez cette fonction si vous souhaitez personnaliser ce processus.

> [!NOTE]
> Utilisez la première forme de cette fonction si vous effectuez une liaison statique à la bibliothèque MFC. Utilisez le deuxième formulaire si vous établissez une liaison dynamique avec la bibliothèque MFC.

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a> COleControlContainer::BroadcastAmbientPropertyChange

Informe tous les contrôles hébergés qu’une propriété ambiante a changé.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Paramètres

*égal*<br/>
ID de dispatch de la propriété ambiante en cours de modification.

### <a name="remarks"></a>Notes

Cette fonction est appelée par l’infrastructure quand une propriété ambiante a une valeur modifiée. Substituez cette fonction pour personnaliser ce comportement.

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a> COleControlContainer::CheckDlgButton

Modifie l’état actuel du bouton.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Paramètres

*nIDButton*<br/>
ID du bouton à modifier.

*nConsultez*<br/>
Spécifie l’état du bouton. Il peut s'agir d'une des méthodes suivantes :

- BST_CHECKED affecte la valeur Checked à l’état du bouton.

- BST_INDETERMINATE affecte la valeur grisé à l’état du bouton, ce qui indique un état indéterminé. Utilisez cette valeur uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE.

- BST_UNCHECKED définit l’état du bouton sur effacé.

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a> COleControlContainer::CheckRadioButton

Sélectionne une case d’option spécifiée dans un groupe et efface les autres boutons du groupe.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Paramètres

*nIDFirstButton*<br/>
Spécifie l’identificateur de la première case d’option dans le groupe.

*nIDLastButton*<br/>
Spécifie l’identificateur de la dernière case d’option dans le groupe.

*nIDCheckButton*<br/>
Spécifie l’identificateur de la case d’option à vérifier.

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a> COleControlContainer::COleControlContainer

Construit un objet `COleControlContainer`.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre parente du conteneur de contrôles.

### <a name="remarks"></a>Notes

Une fois l’objet créé, ajoutez un site de contrôle personnalisé à l’aide d’un appel à `AttachControlSite` .

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a> COleControlContainer :: CreateControl

Crée un contrôle ActiveX, hébergé par l' `COleControlSite` objet spécifié.

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>Paramètres

*pWndCtrl*<br/>
Pointeur vers l’objet fenêtre représentant le contrôle.

*identificateur*<br/>
ID de classe unique du contrôle.

*lpszWindowName*<br/>
Pointeur vers le texte à afficher dans le contrôle. Définit la valeur de la propriété Text ou Caption du contrôle (le cas échéant). Si la valeur est NULL, la légende ou la propriété Text du contrôle n’est pas modifiée.

*dwStyle*<br/>
Styles Windows. Les styles disponibles sont répertoriés sous la section **Notes** .

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle. Il peut s’agir d’un `CRect` objet ou d’une `RECT` structure.

*nID*<br/>
Spécifie l’ID de fenêtre enfant du contrôle.

*pPersist*<br/>
Pointeur vers un `CFile` qui contient l’état persistant du contrôle. La valeur par défaut est NULL, ce qui indique que le contrôle s’initialise lui-même sans restaurer son état à partir d’un stockage persistant. Si la valeur n’est pas NULL, il doit s’agir d’un pointeur désignant un `CFile` objet dérivé de qui contient les données persistantes du contrôle, sous la forme d’un flux ou d’un stockage. Ces données peuvent avoir été enregistrées dans une précédente activation du client. Le `CFile` peut contenir d’autres données, mais doit avoir son pointeur de lecture-écriture défini sur le premier octet de données persistantes au moment de l’appel à `CreateControl` .

*bStorage*<br/>
Indique si les données dans *pPersist* doivent être interprétées comme des `IStorage` `IStream` données ou. Si les données dans *pPersist* sont un stockage, *bStorage* doit avoir la valeur true. Si les données dans *pPersist* sont un flux, *bStorage* doit avoir la valeur false. La valeur par défaut est FALSE.

*bstrLicKey*<br/>
Données de clé de licence facultatives. Ces données sont nécessaires uniquement pour créer des contrôles qui nécessitent une clé de licence d’exécution. Si le contrôle prend en charge la gestion des licences, vous devez fournir une clé de licence pour que la création du contrôle aboutisse. La valeur par défaut est NULL.

*ppNewSite*<br/>
Pointeur vers le site de contrôle existant qui hébergera le contrôle en cours de création. La valeur par défaut est NULL, ce qui indique qu’un nouveau site de contrôle sera automatiquement créé et attaché au nouveau contrôle.

*formations*<br/>
Pointeur vers une `POINT` structure qui contient l’angle supérieur gauche du contrôle. La taille du contrôle est déterminée par la valeur de *psize*. Les valeurs *PPT* et *psize* sont une méthode facultative de spécification de la taille et de la position du contrôle.

*psize*<br/>
Pointeur vers une `SIZE` structure qui contient la taille du contrôle. L’angle supérieur gauche est déterminé par la valeur de *PPT*. Les valeurs *PPT* et *psize* sont une méthode facultative de spécification de la taille et de la position du contrôle.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Seul un sous-ensemble des indicateurs *DwStyle* Windows est pris en charge par `CreateControl` :

- WS_VISIBLE crée une fenêtre qui est initialement visible. Obligatoire si vous souhaitez que le contrôle soit visible immédiatement, comme les fenêtres ordinaires.

- WS_DISABLED crée une fenêtre qui est initialement désactivée. Une fenêtre désactivée ne peut pas recevoir d’entrée de l’utilisateur. Peut être défini si le contrôle a une propriété Enabled.

- WS_BORDER crée une fenêtre avec une bordure fine. Peut être défini si le contrôle a une propriété BorderStyle.

- WS_GROUP spécifie le premier contrôle d’un groupe de contrôles. L’utilisateur peut modifier le focus clavier d’un contrôle du groupe à l’autre à l’aide des touches de direction. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le contrôle suivant avec le style de WS_GROUP termine le groupe et démarre le groupe suivant.

- WS_TABSTOP spécifie un contrôle qui peut recevoir le focus clavier lorsque l’utilisateur appuie sur la touche TAB. Si vous appuyez sur la touche TAB, le focus clavier passe au contrôle suivant du style de WS_TABSTOP.

Utilisez la deuxième surcharge pour créer des contrôles de taille par défaut.

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a> COleControlContainer::CreateOleFont

Crée une police OLE.

```cpp
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
Pointeur vers la police que le conteneur de contrôle doit utiliser.

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a> COleControlContainer::FindItem

Recherche le site personnalisé qui héberge l’élément spécifié.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Identificateur de l’élément à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le site personnalisé de l’élément spécifié.

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a> COleControlContainer::FreezeAllEvents

Détermine si le conteneur doit ignorer les événements des sites de contrôle attachés ou les accepter.

```cpp
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Paramètres

*bFreeze*<br/>
Différent de zéro si les événements sont traités ; Sinon, 0.

### <a name="remarks"></a>Notes

> [!NOTE]
> Le contrôle n’est pas requis pour arrêter le déclenchement d’événements si le conteneur de contrôle le demande. Il peut continuer à se déclencher, mais tous les événements suivants seront ignorés par le conteneur de contrôle.

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a> COleControlContainer::GetAmbientProp

Récupère la valeur d’une propriété ambiante spécifiée.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Paramètres

*pSite*<br/>
Pointeur vers un site de contrôle à partir duquel la propriété ambiante sera récupérée.

*égal*<br/>
ID de dispatch de la propriété ambiante souhaitée.

*pVarResult*<br/>
Pointeur vers la valeur de la propriété ambiante.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a> COleControlContainer::GetDlgItem

Récupère un pointeur vers le contrôle ou la fenêtre enfant spécifié dans une boîte de dialogue ou une autre fenêtre.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Identificateur de l’élément de boîte de dialogue à récupérer.

*phWnd*<br/>
Pointeur vers le handle de l’objet de fenêtre de l’élément de boîte de dialogue spécifié.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la fenêtre de l’élément de boîte de dialogue.

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a> COleControlContainer::GetDlgItemInt

Récupère la valeur du texte traduit du contrôle donné.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Identificateur du contrôle.

*lpTrans*<br/>
Pointeur vers une variable booléenne qui reçoit une valeur de réussite/d’échec de fonction (TRUE indique une réussite, FALSe indique un échec).

*bSigned*<br/>
Spécifie si la fonction doit examiner le texte pour un signe moins au début et retourner une valeur entière signée si elle en trouve une. Si le paramètre *bSigned* a la valeur true, en spécifiant que la valeur à récupérer est une valeur entière signée, effectuez un cast de la valeur de retour en un **`int`** type. Pour obtenir des informations détaillées sur l’erreur, appelez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, la variable vers laquelle pointe *lpTrans* a la valeur true et la valeur de retour est la valeur traduite du texte du contrôle.

Si la fonction échoue, la variable vers laquelle pointe *lpTrans* a la valeur false et la valeur de retour est zéro. Notez que, puisque zéro est une valeur traduite possible, une valeur de retour de zéro n’indique pas en soi une défaillance.

Si *lpTrans* a la valeur null, la fonction ne retourne aucune information sur la réussite ou l’échec.

### <a name="remarks"></a>Notes

La fonction convertit le texte récupéré en supprimant les espaces supplémentaires au début du texte, puis en convertissant les chiffres décimaux. La fonction arrête la translation lorsqu’elle atteint la fin du texte ou rencontre un caractère non numérique.

Cette fonction retourne zéro si la valeur traduite est supérieure à INT_MAX (pour les nombres signés) ou UINT_MAX (pour les nombres non signés).

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a> COleControlContainer::GetDlgItemText

Récupère le texte du contrôle donné.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Identificateur du contrôle.

*lpStr*<br/>
Pointeur vers le texte du contrôle.

*nMaxCount*<br/>
Spécifie la longueur maximale, en caractères, de la chaîne à copier dans la mémoire tampon vers laquelle pointe *lpStr*. Si la longueur de la chaîne dépasse la limite, la chaîne est tronquée.

### <a name="return-value"></a>Valeur renvoyée

Si la fonction est réussie, la valeur de retour spécifie le nombre de caractères copiés dans la mémoire tampon, à l’exclusion du caractère null de fin.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations détaillées sur l’erreur, appelez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a> COleControlContainer::HandleSetFocus

Détermine si le conteneur gère WM_SETFOCUS messages.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le conteneur gère WM_SETFOCUS messages ; Sinon, zéro.

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a> COleControlContainer::HandleWindowlessMessage

Traite les messages de fenêtre pour les contrôles sans fenêtre.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Paramètres

*message*<br/>
Identificateur du message de fenêtre, fourni par Windows.

*wParam*<br/>
Paramètre du message ; fourni par Windows. Spécifie des informations supplémentaires spécifiques au message. Le contenu de ce paramètre dépend de la valeur du paramètre de *message* .

*lParam*<br/>
Paramètre du message ; fourni par Windows. Spécifie des informations supplémentaires spécifiques au message. Le contenu de ce paramètre dépend de la valeur du paramètre de *message* .

*plResult*<br/>
Code de résultat Windows. Spécifie le résultat du traitement du message et dépend du message envoyé.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Substituez cette fonction pour personnaliser la gestion des messages de contrôle sans fenêtre.

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a> COleControlContainer::IsDlgButtonChecked

Détermine l’état du bouton spécifié.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Paramètres

*nIDButton*<br/>
Identificateur du contrôle bouton.

### <a name="return-value"></a>Valeur renvoyée

Valeur de retour, à partir d’un bouton créé avec le style BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON ou BS_3STATE. Il peut s'agir d'une des méthodes suivantes :

- BST_CHECKED bouton est activé.

- BST_INDETERMINATE bouton est grisé, ce qui indique un état indéterminé (s’applique uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE).

- BST_UNCHECKED bouton est désactivée.

### <a name="remarks"></a>Notes

Si le bouton est un contrôle à trois États, la fonction membre détermine si elle est grisée, vérifiée ou aucune des deux.

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a> COleControlContainer :: m_crBack

Couleur d’arrière-plan du conteneur.

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a> COleControlContainer :: m_crFore

Couleur de premier plan du conteneur.

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a> COleControlContainer :: m_listSitesOrWnds

Liste des sites de contrôle hébergés par le conteneur.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a> COleControlContainer :: m_nWindowlessControls

Nombre de contrôles sans fenêtre hébergés par le conteneur de contrôles.

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a> COleControlContainer :: m_pOleFont

Pointeur vers la police OLE du site de contrôle personnalisé.

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a> COleControlContainer :: m_pSiteCapture

Pointeur vers le site de contrôle de capture.

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a> COleControlContainer :: m_pSiteFocus

Pointeur vers le site de contrôle qui a actuellement le focus d’entrée.

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a> COleControlContainer :: m_pSiteUIActive

Pointeur vers le site de contrôle qui est activé sur place.

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a> COleControlContainer :: m_pWnd

Pointeur vers l’objet de fenêtre associé au conteneur.

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a> COleControlContainer :: m_siteMap

Plan du site.

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a> COleControlContainer :: OnPaint

Appelé par l’infrastructure pour gérer les demandes de WM_PAINT.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers le contexte de périphérique (Device Context) utilisé par le conteneur.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le message a été géré ; Sinon, zéro.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser le processus de peinture.

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a> COleControlContainer::OnUIActivate

Appelée par l’infrastructure quand le site de contrôle, désigné par *pSite*, est sur le point d’être activé sur place.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Paramètres

*pSite*<br/>
Pointeur vers le site de contrôle sur le point d’être activé sur place.

### <a name="remarks"></a>Notes

L’activation sur place signifie que le menu principal du conteneur est remplacé par un menu composite sur place.

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a> COleControlContainer::OnUIDeactivate

Appelée par l’infrastructure quand le site de contrôle, désigné par *pSite*, est sur le point d’être désactivé.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Paramètres

*pSite*<br/>
Pointeur vers le site de contrôle sur le point d’être désactivé.

### <a name="remarks"></a>Notes

Quand cette notification est reçue, le conteneur doit réinstaller son interface utilisateur et prendre le focus.

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a> COleControlContainer::ScrollChildren

Appelée par l’infrastructure quand des messages de défilement sont reçus à partir d’une fenêtre enfant.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Paramètres

*DX*<br/>
Quantité, en pixels, du défilement le long de l’axe x.

*DY*<br/>
Quantité, en pixels, du défilement le long de l’axe y.

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a> COleControlContainer::SendDlgItemMessage

Envoie un message au contrôle spécifié.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Spécifie l’identificateur du contrôle qui reçoit le message.

*message*<br/>
Spécifie le message à envoyer.

*wParam*<br/>
Spécifie des informations supplémentaires spécifiques au message.

*lParam*<br/>
Spécifie des informations supplémentaires spécifiques au message.

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a> COleControlContainer::SetDlgItemInt

Définit le texte d’un contrôle dans une boîte de dialogue sur la représentation sous forme de chaîne d’une valeur entière spécifiée.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Identificateur du contrôle.

*nValeur*<br/>
Valeur entière à afficher.

*bSigned*<br/>
Spécifie si le paramètre *nValeur* est signé ou non signé. Si ce paramètre a la valeur TRUE, *nValeur* est signé. Si ce paramètre a la valeur TRUE et que *nValeur* est inférieur à zéro, un signe moins est placé avant le premier chiffre de la chaîne. Si ce paramètre a la valeur FALSe, *nValeur* est non signé.

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a> COleControlContainer::SetDlgItemText

Définit le texte du contrôle spécifié, à l’aide du texte contenu dans *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Identificateur du contrôle.

*lpszString*<br/>
Pointeur vers le texte du contrôle.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite, classe](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager, classe](../../mfc/reference/coccmanager-class.md)
