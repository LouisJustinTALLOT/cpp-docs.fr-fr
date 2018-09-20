---
title: COleControlContainer, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f016773102b5989d5272ebb51931e00ff1972ce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409103"
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
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informe toutes étant hébergées contrôles qu’une propriété ambiante a changé.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modifie le contrôle de bouton spécifié.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Sélectionne le bouton radio spécifié d’un groupe.|
|[COleControlContainer::CreateControl](#createcontrol)|Crée un contrôle ActiveX hébergé.|
|[COleControlContainer::CreateOleFont](#createolefont)|Crée une police OLE.|
|[COleControlContainer::FindItem](#finditem)|Retourne le site personnalisé du contrôle spécifié.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Détermine si le site de contrôle accepte d’événements.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Récupère la propriété ambiante spécifiée.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Récupère le contrôle de boîte de dialogue spécifiée.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Récupère la valeur du contrôle de boîte de dialogue spécifiée.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Récupère la légende du contrôle de boîte de dialogue spécifiée.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Détermine si le conteneur gère les messages WM_SETFOCUS.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Gère les messages envoyés à un contrôle sans fenêtre.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Détermine l’état du bouton spécifié.|
|[COleControlContainer::OnPaint](#onpaint)|Appelé pour repeindre une partie du conteneur.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Appelé lorsqu’un contrôle est sur le point d’être activé sur place.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Appelé lorsqu’un contrôle est sur le point d’être désactivé.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Appelé par l’infrastructure lors de la réception des messages de défilement à partir d’une fenêtre enfant.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Envoie un message au contrôle spécifié.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Définit la valeur du contrôle spécifié.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Définit le texte du contrôle spécifié.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|La couleur d’arrière-plan du conteneur.|
|[COleControlContainer::m_crFore](#m_crfore)|La couleur de premier plan du conteneur.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Une liste des sites de contrôle pris en charge.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Le nombre de contrôles sans fenêtre hébergés.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Pointeur vers la police OLE du site de contrôle personnalisé.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Pointeur vers le site de contrôle de capture.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Pointeur vers le contrôle qui a le focus.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Pointeur vers le contrôle qui est actuellement activé sur place.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Pointeur vers la fenêtre du conteneur de contrôle de mise en œuvre.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Le plan du site.|

## <a name="remarks"></a>Notes

Pour cela, la prise en charge d’un ou plusieurs sites de contrôle ActiveX (implémentée par `COleControlSite`). `COleControlContainer` implémente entièrement le [IOleInPlaceFrame](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceframe) et [IOleContainer](/windows/desktop/api/oleidl/nn-oleidl-iolecontainer) interfaces, pour permettre les contrôles ActiveX de relation contenant-contenus répondre à leurs compétences en tant qu’éléments de la place.

En général, cette classe est utilisée conjointement avec `COccManager` et `COleControlSite` pour implémenter un conteneur de contrôle ActiveX personnalisé, avec des sites personnalisés pour un ou plusieurs contrôles ActiveX.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxocc.h

##  <a name="attachcontrolsite"></a>  COleControlContainer::AttachControlSite

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
Un pointeur vers un `CWnd` objet.

*nIDC*<br/>
L’ID du contrôle à attacher.

### <a name="remarks"></a>Notes

Remplacez cette fonction si vous souhaitez personnaliser ce processus.

> [!NOTE]
>  Utiliser la première forme de cette fonction si vous effectuez une liaison statique à la bibliothèque MFC. Utilisez la deuxième forme si vous effectuez une liaison dynamique à la bibliothèque MFC.

##  <a name="broadcastambientpropertychange"></a>  COleControlContainer::BroadcastAmbientPropertyChange

Informe toutes étant hébergées contrôles qu’une propriété ambiante a changé.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Paramètres

*DISPID*<br/>
L’ID de dispatch de la propriété ambiante en cours de modification.

### <a name="remarks"></a>Notes

Cette fonction est appelée par le framework lorsqu’une propriété ambiante a changé de valeur. Remplacez cette fonction pour personnaliser ce comportement.

##  <a name="checkdlgbutton"></a>  COleControlContainer::CheckDlgButton

Modifie l’état actuel du bouton.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Paramètres

*nIDButton*<br/>
L’ID du bouton à modifier.

*nVérifiez*<br/>
Spécifie l’état du bouton. Il peut s'agir d'une des valeurs suivantes :

- BST_CHECKED définit l’état du bouton à vérifiée.

- BST_INDETERMINATE définit l’état du bouton est grisé, indiquant un état indéterminé. Utilisez cette valeur uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE.

- BST_UNCHECKED définit l’état de bouton à effacé.

##  <a name="checkradiobutton"></a>  COleControlContainer::CheckRadioButton

Sélectionne un bouton radio spécifié dans un groupe et efface les boutons restants dans le groupe.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Paramètres

*nIDFirstButton*<br/>
Spécifie l’identificateur de la première case dans le groupe.

*nIDLastButton*<br/>
Spécifie l’identificateur du dernier bouton de case d’option dans le groupe.

*nIDCheckButton*<br/>
Spécifie l’identificateur de la case à vérifier.

##  <a name="colecontrolcontainer"></a>  COleControlContainer::COleControlContainer

Construit un objet `COleControlContainer`.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre parente du conteneur de contrôle.

### <a name="remarks"></a>Notes

Une fois que l’objet a été créé avec succès, ajoutez un site de contrôle personnalisé avec un appel à `AttachControlSite`.

##  <a name="createcontrol"></a>  COleControlContainer::CreateControl

Crée un contrôle ActiveX, hébergé par spécifié `COleControlSite` objet.

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
Pointeur vers l’objet window représentant le contrôle.

*clsid*<br/>
L’ID de classe unique du contrôle.

*lpszWindowName*<br/>
Un pointeur vers le texte à afficher dans le contrôle. Définit la valeur de propriété de légende ou le texte du contrôle (le cas échéant). Si NULL, la propriété de légende ou le texte du contrôle n’est pas modifiée.

*dwStyle*<br/>
Styles de Windows. Les styles disponibles sont répertoriés sous la **notes** section.

*Rect*<br/>
Spécifie la taille et la position du contrôle. Il peut s’agir un `CRect` objet ou un `RECT` structure.

*nID*<br/>
Spécifie la fenêtre de l’enfant. du contrôle

*pPersist*<br/>
Un pointeur vers un `CFile` contenant l’état persistant du contrôle. La valeur par défaut est NULL, indiquant que le contrôle initialise lui-même sans restaurer son état à partir de n’importe quel stockage persistant. Si non NULL, il doit être un pointeur vers un `CFile`-objet qui contient les données du contrôle persistant, sous la forme d’un flux ou un stockage dérivé. Ces données pourraient avoir été enregistrées dans une précédente activation du client. Le `CFile` peut contenir des autres données, mais doit avoir son pointeur en lecture-écriture au moment de l’appel à la valeur du premier octet de données persistantes `CreateControl`.

*bStorage*<br/>
Indique si les données dans *pPersist* doivent être interprétées comme `IStorage` ou `IStream` données. Si les données dans *pPersist* est un type de stockage, *bStorage* doit être TRUE. Si les données dans *pPersist* est un flux, *bStorage* doit être FALSE. La valeur par défaut est FALSE.

*bstrLicKey*<br/>
Données de clé de licence facultatif. Ces données sont nécessaire uniquement pour la création de contrôles qui nécessitent une clé de licence d’exécution. Si le contrôle prend en charge la gestion des licences, vous devez fournir une clé de licence pour la création du contrôle réussisse. La valeur par défaut est NULL.

*ppNewSite*<br/>
Pointeur vers le site de contrôle existant qui va héberger le contrôle en cours de création. La valeur par défaut est NULL, indiquant qu’un nouveau site de contrôle est automatiquement créé et attaché au nouveau contrôle.

*ppt*<br/>
Un pointeur vers un `POINT` structure qui contient le coin supérieur gauche du contrôle. La taille du contrôle est déterminée par la valeur de *psize*. Le *ppt* et *psize* les valeurs sont une méthode facultative de spécification de la taille et la position du contrôle.

*psize*<br/>
Un pointeur vers un `SIZE` structure qui contient la taille du contrôle. L’angle supérieur gauche est déterminée par la valeur de *ppt*. Le *ppt* et *psize* les valeurs sont une méthode facultative de spécification de la taille et la position du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Seul un sous-ensemble de la Windows *dwStyle* indicateurs sont pris en charge par `CreateControl`:

- WS_VISIBLE crée une fenêtre est visible initialement. Requis si vous souhaitez le contrôle soit visible immédiatement, comme windows ordinaires.

- WS_DISABLED crée une fenêtre qui est initialement désactivée. Une fenêtre désactivée ne peut pas recevoir des entrées de l’utilisateur. Peut être définie si le contrôle a une propriété Enabled.

- WS_BORDER crée une fenêtre avec une bordure de ligne de dynamique. Peut être définie si le contrôle a une propriété BorderStyle.

- WS_GROUP Spécifie le premier contrôle d’un groupe de contrôles. L’utilisateur peut modifier le focus clavier d’un contrôle dans le groupe à l’autre en utilisant les touches de direction. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le prochain contrôle avec le style WS_GROUP termine le groupe et démarre le prochain groupe.

- WS_TABSTOP spécifie un contrôle qui peut recevoir le focus clavier lorsque l’utilisateur appuie sur la touche TAB. En appuyant sur la touche TAB modifie le focus clavier au contrôle suivant du style WS_TABSTOP.

La deuxième surcharge permet de créer des contrôles de taille par défaut.

##  <a name="createolefont"></a>  COleControlContainer::CreateOleFont

Crée une police OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
Pointeur vers la police à utiliser par le conteneur de contrôle.

##  <a name="finditem"></a>  COleControlContainer::FindItem

Recherche le site personnalisé qui héberge l’élément spécifié.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identificateur de l’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le site personnalisé de l’élément spécifié.

##  <a name="freezeallevents"></a>  COleControlContainer::FreezeAllEvents

Détermine si le conteneur sera ignorer les événements à partir des sites contrôle attaché ou les accepter.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Paramètres

*bFreeze*<br/>
Différent de zéro si les événements seront traités ; sinon 0.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Le contrôle n’est pas nécessaire d’arrêter le déclenchement d’événements si demandé par le conteneur de contrôle. Il peut continuer le déclenchement de l’événement, mais tous les événements suivants seront ignorés par le conteneur de contrôle.

##  <a name="getambientprop"></a>  COleControlContainer::GetAmbientProp

Récupère la valeur d’une propriété ambiante spécifiée.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Paramètres

*pSite*<br/>
Pointeur vers un site de contrôle à partir de laquelle la propriété ambiante est récupérée.

*DISPID*<br/>
L’ID de dispatch de la propriété ambiante souhaitée.

*pVarResult*<br/>
Pointeur vers la valeur de la propriété ambiante.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="getdlgitem"></a>  COleControlContainer::GetDlgItem

Récupère un pointeur vers la fenêtre de contrôle ou enfant spécifiée dans une boîte de dialogue ou une autre fenêtre.

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
Un pointeur vers le handle d’objet de fenêtre de l’élément de boîte de dialogue spécifiée.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre de l’élément de la boîte de dialogue.

##  <a name="getdlgitemint"></a>  COleControlContainer::GetDlgItemInt

Récupère la valeur du texte traduit du contrôle donné.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identificateur du contrôle.

*lpTrans*<br/>
Pointeur vers une variable booléenne qui reçoit une valeur de réussite/échec (fonction) (la valeur TRUE indique la réussite, FALSE indique un échec).

*bSigned*<br/>
Spécifie si la fonction doit examiner le texte pour un signe moins au début et à retourner une valeur entière signée, s’il en trouve. Si le *bSigned* paramètre a la valeur TRUE, en spécifiant que la valeur à récupérer est une valeur entière signée, convertir la valeur de retour pour une **int** type. Pour obtenir les informations d’erreur étendues, appelez [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="return-value"></a>Valeur de retour

Si réussie, la variable vers laquelle pointe *lpTrans* est définie sur TRUE, et la valeur de retour est la valeur traduite du texte du contrôle.

Si la fonction échoue, la variable vers laquelle pointe *lpTrans* est définie sur FALSE, et la valeur de retour est égale à zéro. Notez que, puisque zéro est une valeur traduite possible, une valeur de retour de zéro ne signifie pas échec.

Si *lpTrans* est NULL, la fonction ne retourne aucune information sur la réussite ou l’échec.

### <a name="remarks"></a>Notes

La fonction traduit le texte récupéré par la suppression des espaces supplémentaires au début du texte, puis en convertissant les chiffres décimaux. La fonction arrête la traduction lorsqu’il atteint la fin du texte ou rencontre un caractère non numérique.

Cette fonction retourne zéro si la valeur convertie est supérieure à INT_MAX (pour les nombres signés) ou UINT_MAX (pour les nombres non signés).

##  <a name="getdlgitemtext"></a>  COleControlContainer::GetDlgItemText

Récupère le texte du contrôle donné.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identificateur du contrôle.

*lpStr*<br/>
Pointeur vers le texte du contrôle.

*nMaxCount*<br/>
Spécifie la longueur maximale, en caractères, de la chaîne à copier vers la mémoire tampon vers laquelle pointée *lpStr*. Si la longueur de la chaîne dépasse la limite, la chaîne est tronquée.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour Spécifie le nombre de caractères copiés vers la mémoire tampon, non compris le caractère null de fin.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir les informations d’erreur étendues, appelez [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

##  <a name="handlesetfocus"></a>  COleControlContainer::HandleSetFocus

Détermine si le conteneur gère les messages WM_SETFOCUS.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le conteneur gère les messages WM_SETFOCUS ; Sinon, zéro.

##  <a name="handlewindowlessmessage"></a>  COleControlContainer::HandleWindowlessMessage

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
L’identificateur du message de fenêtre, fourni par Windows.

*wParam*<br/>
Paramètre du message ; fourni par Windows. Spécifie des informations supplémentaires spécifiques au message. Le contenu de ce paramètre dépend de la valeur de la *message* paramètre.

*lParam*<br/>
Paramètre du message ; fourni par Windows. Spécifie des informations supplémentaires spécifiques au message. Le contenu de ce paramètre dépend de la valeur de la *message* paramètre.

*plResult*<br/>
Code de sortie de Windows. Spécifie le résultat du traitement du message et varie selon le message envoyé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser la gestion des messages de contrôle sans fenêtre.

##  <a name="isdlgbuttonchecked"></a>  COleControlContainer::IsDlgButtonChecked

Détermine l’état du bouton spécifié.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Paramètres

*nIDButton*<br/>
L’identificateur du contrôle bouton.

### <a name="return-value"></a>Valeur de retour

La valeur de retour à partir d’un bouton créé avec le style BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON ou BS_3STATE. Il peut s'agir d'une des valeurs suivantes :

- Bouton de BST_CHECKED est activé.

- BST_INDETERMINATE bouton est grisé, ce qui indique un état indéterminé (s’applique uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE).

- Bouton de BST_UNCHECKED est désactivée.

### <a name="remarks"></a>Notes

Si le bouton est à trois états, la fonction membre détermine si elle est grisée, activée, ou aucun.

##  <a name="m_crback"></a>  COleControlContainer::m_crBack

La couleur d’arrière-plan du conteneur.

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>  COleControlContainer::m_crFore

La couleur de premier plan du conteneur.

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>  COleControlContainer::m_listSitesOrWnds

Une liste des sites de contrôle hébergé par le conteneur.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>  COleControlContainer::m_nWindowlessControls

Le nombre de contrôles sans fenêtre hébergé par le conteneur de contrôle.

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>  COleControlContainer::m_pOleFont

Pointeur vers la police OLE du site de contrôle personnalisé.

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture

Pointeur vers le site de contrôle de capture.

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus

Pointeur vers le site de contrôle qui actuellement a le focus.

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive

Pointeur vers le site de contrôle est activé sur place.

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>  COleControlContainer::m_pWnd

Pointeur vers l’objet de fenêtre associé au conteneur.

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap

Le plan du site.

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>  COleControlContainer::OnPaint

Appelé par l’infrastructure pour gérer les demandes WM_PAINT.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Pointeur vers le contexte de périphérique utilisé par le conteneur.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le message a été géré ; Sinon, zéro.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser le processus de peinture.

##  <a name="onuiactivate"></a>  COleControlContainer::OnUIActivate

Appelé par le framework lorsque le site de contrôle vers lequel pointe *pSite*, doit être activé sur place.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Paramètres

*pSite*<br/>
Pointeur vers le site de contrôle sur le point d’être activé sur place.

### <a name="remarks"></a>Notes

Activation en place signifie que le menu principal du conteneur est remplacé par un menu composite sur place.

##  <a name="onuideactivate"></a>  COleControlContainer::OnUIDeactivate

Appelé par le framework lorsque le site de contrôle vers lequel pointe *pSite*, doit être désactivé.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Paramètres

*pSite*<br/>
Pointeur vers le site de contrôle sur le point d’être désactivé.

### <a name="remarks"></a>Notes

Quand cette notification est reçue, le conteneur doit réinstaller son interface utilisateur et prendre le focus.

##  <a name="scrollchildren"></a>  COleControlContainer::ScrollChildren

Appelé par l’infrastructure lors de la réception des messages de défilement à partir d’une fenêtre enfant.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Paramètres

*DX*<br/>
La quantité, en pixels, de défilement sur l’axe x.

*dy*<br/>
La quantité, en pixels, de défilement sur l’axe y.

##  <a name="senddlgitemmessage"></a>  COleControlContainer::SendDlgItemMessage

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

##  <a name="setdlgitemint"></a>  COleControlContainer::SetDlgItemInt

Définit le texte d’un contrôle dans une boîte de dialogue à la représentation sous forme de chaîne d’une valeur d’entier spécifié.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identificateur du contrôle.

*%n%nValeur*<br/>
La valeur entière à afficher.

*bSigned*<br/>
Spécifie si le *%n%nValeur* paramètre est signé ou non signé. Si ce paramètre est TRUE, *%n%nValeur* est signé. Si ce paramètre a la valeur TRUE et *%n%nValeur* est inférieur à zéro, un signe moins signe est placé avant le premier chiffre de la chaîne. Si ce paramètre est FALSE, *%n%nValeur* n’est pas signé.

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

Définit le texte du contrôle spécifié, à l’aide du texte contenu dans *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identificateur du contrôle.

*lpszString*<br/>
Pointeur vers le texte du contrôle.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite, classe](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager, classe](../../mfc/reference/coccmanager-class.md)
