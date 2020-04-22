---
title: Classe COleControlContainer
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
ms.openlocfilehash: 83171e012db7ef2cce459d35cfc689746afd062c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749028"
---
# <a name="colecontrolcontainer-class"></a>Classe COleControlContainer

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
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modifie le contrôle spécifié du bouton.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Sélectionne le bouton radio spécifié d’un groupe.|
|[COleControlContainer::CreateControl](#createcontrol)|Crée un contrôle ActiveX hébergé.|
|[COleControlContainer::CreateOleFont](#createolefont)|Crée une police OLE.|
|[COleControlContainer::FindItem](#finditem)|Retourne le site personnalisé du contrôle spécifié.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Détermine si le site de contrôle accepte les événements.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Récupère la propriété ambiante spécifiée.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Récupère le contrôle de dialogue spécifié.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Récupère la valeur du contrôle de dialogue spécifié.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Récupère la légende du contrôle de dialogue spécifié.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Détermine si le conteneur gère WM_SETFOCUS messages.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Gère les messages envoyés à un contrôle sans fenêtre.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Détermine l’état du bouton spécifié.|
|[COleControlContainer::OnPaint](#onpaint)|Appelé à repeindre une partie du conteneur.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Appelé quand un contrôle est sur le point d’être activé sur place.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Appelé quand un contrôle est sur le point d’être désactivé.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Appelé par le cadre lorsque des messages de défilement sont reçus d’une fenêtre enfant.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Envoie un message au contrôle spécifié.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Définit la valeur du contrôle spécifié.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Définit le texte du contrôle spécifié.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|La couleur de fond du récipient.|
|[COleControlContainer::m_crFore](#m_crfore)|La couleur de premier plan du récipient.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Une liste des sites de contrôle pris en charge.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Le nombre de commandes sans fenêtre hébergées.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Un pointeur à la police OLE du site de contrôle personnalisé.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Pointeur vers le site de contrôle de capture.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Pointeur vers le contrôle qui a actuellement l’accent sur les entrées.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Pointeur vers le contrôle qui est actuellement activé sur place.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Pointeur vers la fenêtre implémentant le conteneur de contrôle.|
|[COleControlContainer::m_siteMap](#m_sitemap)|La carte du site.|

## <a name="remarks"></a>Notes

Ceci est fait en fournissant un soutien pour un `COleControlSite`ou plusieurs sites de contrôle ActiveX (mis en œuvre par ). `COleControlContainer`implémente intégralement les interfaces [IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) et [IOleContainer,](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) permettant aux contrôles ActiveX contenus de remplir leurs qualifications en tant qu’éléments sur place.

Généralement, cette classe est `COccManager` utilisée `COleControlSite` en conjonction avec et pour implémenter un conteneur de contrôle ActiveX personnalisé, avec des sites personnalisés pour un ou plusieurs contrôles ActiveX.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Spécifications

**En-tête:** afxocc.h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

Appelé par le cadre pour créer et attacher un site de contrôle.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Pointeur vers un objet `CWnd`.

*nIDC (en)*<br/>
L’ID du contrôle à attacher.

### <a name="remarks"></a>Notes

Remplacez cette fonction si vous souhaitez personnaliser ce processus.

> [!NOTE]
> Utilisez la première forme de cette fonction si vous êtes statiquement lié à la bibliothèque MFC. Utilisez le deuxième formulaire si vous êtes dynamiquement lié à la bibliothèque MFC.

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

Informe tous les contrôles hébergés qu’une propriété ambiante a changé.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’id de répartition de la propriété ambiante en cours de modification.

### <a name="remarks"></a>Notes

Cette fonction est appelée par le cadre quand une propriété ambiante a changé de valeur. Remplacer cette fonction pour personnaliser ce comportement.

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

Modifie l’état actuel du bouton.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Paramètres

*nIDButton (en)*<br/>
L’ID du bouton à modifier.

*nCheck (en)*<br/>
Spécifie l’état du bouton. Il peut s'agir d'une des méthodes suivantes :

- BST_CHECKED définit l’état du bouton à vérifier.

- BST_INDETERMINATE définit l’état du bouton à grisé, indiquant un état indéterminé. Utilisez cette valeur uniquement si le bouton a le BS_3STATE ou BS_AUTO3STATE style.

- BST_UNCHECKED définit l’état du bouton pour effacer.

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

Sélectionne un bouton radio spécifié dans un groupe et efface les boutons restants dans le groupe.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Paramètres

*nIDFirstButton (en)*<br/>
Spécifie l’identifiant du premier bouton radio du groupe.

*nIDLastButton*<br/>
Spécifie l’identifiant du dernier bouton radio du groupe.

*nIDCheckButton (en)*<br/>
Spécifie l’identifiant du bouton radio à vérifier.

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

Construit un objet `COleControlContainer`.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Un pointeur à la fenêtre parente du conteneur de contrôle.

### <a name="remarks"></a>Notes

Une fois que l’objet a été créé avec `AttachControlSite`succès, ajoutez un site de contrôle personnalisé avec un appel à .

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COleControlContainer::CreateControl

Crée un contrôle ActiveX, hébergé `COleControlSite` par l’objet spécifié.

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
Un pointeur à l’objet de fenêtre représentant le contrôle.

*clsid*<br/>
L’ID de classe unique du contrôle.

*lpszWindowName (en)*<br/>
Un pointeur sur le texte à afficher dans le contrôle. Définit la valeur de la propriété caption ou texte du contrôle (le cas échéant). Si NULL, la propriété caption ou texte du contrôle n’est pas modifiée.

*dwStyle (en)*<br/>
Styles Windows. Les styles disponibles sont répertoriés dans la section **Remarques.**

*Rect*<br/>
Spécifie la taille et la position du contrôle. Il peut s’agir `CRect` `RECT` d’un objet ou d’une structure.

*nID*<br/>
Spécifie l’id de fenêtre pour enfant du contrôle.

*pPersist pPersist*<br/>
Un pointeur `CFile` à un contenant de l’état persistant pour le contrôle. La valeur par défaut est NULL, ce qui indique que le contrôle se parasité sans restaurer son état à partir d’un stockage persistant. Si ce n’est pas NULL, il devrait être un pointeur à un `CFile`objet dérivé qui contient les données persistantes du contrôle, sous la forme d’un flux ou d’un stockage. Ces données auraient pu être enregistrées lors d’une activation précédente du client. Le `CFile` peut contenir d’autres données, mais doit avoir son pointeur de lecture-écriture `CreateControl`réglé à la première mise en place de données persistantes au moment de l’appel à .

*bStorage*<br/>
Indique si les données dans *pPersist* doivent être interprétées comme `IStorage` ou `IStream` des données. Si les données dans *pPersist* est un stockage, *bStorage* devrait être VRAI. Si les données dans *pPersist* est un flux, *bStorage* devrait être FALSE. La valeur par défaut est FALSE.

*bstrLicKey (en)*<br/>
Données clés de licence facultatives. Ces données sont nécessaires uniquement pour créer des contrôles qui nécessitent une clé de licence en temps de course. Si le contrôle prend en charge l’octroi de licences, vous devez fournir une clé de licence pour la création du contrôle pour réussir. La valeur par défaut est NULL.

*ppNewSite*<br/>
Un pointeur vers le site de contrôle existant qui hébergera le contrôle en cours de création. La valeur par défaut est NULL, ce qui indique qu’un nouveau site de contrôle sera automatiquement créé et attaché au nouveau contrôle.

*Ppt*<br/>
Pointeur d’une `POINT` structure qui contient le coin supérieur gauche du contrôle. La taille du contrôle est déterminée par la valeur de *psize*. Les valeurs *de ppt* et *de psize* sont une méthode facultative pour spécifier la taille et la position du contrôle.

*Psize*<br/>
Un pointeur `SIZE` vers une structure qui contient la taille du contrôle. Le coin supérieur gauche est déterminé par la valeur du *ppt*. Les valeurs *de ppt* et *de psize* sont une méthode facultative pour spécifier la taille et la position du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Seul un sous-ensemble des drapeaux Windows `CreateControl` *dwStyle* sont pris en charge par :

- WS_VISIBLE crée une fenêtre qui est initialement visible. Nécessaire si vous voulez que le contrôle soit visible immédiatement, comme les fenêtres ordinaires.

- WS_DISABLED crée une fenêtre qui est initialement désactivée. Une fenêtre désactivée ne peut pas recevoir l’entrée de l’utilisateur. Peut être défini si le contrôle a une propriété activée.

- WS_BORDER crée une fenêtre avec une bordure à ligne mince. Peut être défini si le contrôle a une propriété BorderStyle.

- WS_GROUP précise le premier contrôle d’un groupe de contrôles. L’utilisateur peut modifier la mise au point du clavier d’un contrôle dans le groupe à l’autre en utilisant les touches de direction. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le prochain contrôle avec le style WS_GROUP termine le groupe et commence le groupe suivant.

- WS_TABSTOP specifie un contrôle qui peut recevoir la mise au point du clavier lorsque l’utilisateur appuie sur la touche TAB. Appuyer sur la clé TAB change la mise au point du clavier pour le prochain contrôle du style WS_TABSTOP.

Utilisez la deuxième surcharge pour créer des commandes par défaut.

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COleControlContainer::CreateOleFont

Crée une police OLE.

```cpp
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
Un pointeur de la police à utiliser par le conteneur de contrôle.

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COleControlContainer::FindItem

Trouve le site personnalisé qui héberge l’élément spécifié.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identifiant de l’élément à trouver.

### <a name="return-value"></a>Valeur de retour

Un pointeur sur le site personnalisé de l’élément spécifié.

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

Détermine si le conteneur ignorera les événements des sites de contrôle ci-joints ou les acceptera.

```cpp
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Paramètres

*bFreeze (en)*<br/>
Nonzero si les événements seront traités; sinon 0.

### <a name="remarks"></a>Notes

> [!NOTE]
> Le contrôle n’est pas nécessaire pour arrêter les événements de tir si demandé par le conteneur de contrôle. Il peut continuer à tirer, mais tous les événements ultérieurs seront ignorés par le conteneur de contrôle.

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COleControlContainer::GetAmbientProp

Récupère la valeur d’une propriété ambiante spécifiée.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Paramètres

*pSite (en)*<br/>
Un pointeur vers un site de contrôle à partir duquel la propriété ambiante sera récupérée.

*dispid*<br/>
L’ID de répartition de la propriété ambiante désirée.

*pVarResult*<br/>
Un pointeur à la valeur de la propriété ambiante.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COleControlContainer::GetDlgItem

Récupère un pointeur à la fenêtre de contrôle ou d’enfant spécifiée dans une boîte de dialogue ou une autre fenêtre.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Identifiant de l’élément de dialogue à récupérer.

*phWnd*<br/>
Un pointeur à la poignée de l’objet de fenêtre de l’élément de dialogue spécifié.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre de l’élément de dialogue.

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt

Récupère la valeur du texte traduit du contrôle donné.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identifiant du contrôle.

*lpTrans (en)*<br/>
Pointeur vers une variable Boolean qui reçoit une valeur de succès de fonction/échec (TRUE indique le succès, FALSE indique l’échec).

*bSigned*<br/>
Précise si la fonction doit examiner le texte pour un signe moins au début et retourner une valeur d’intégrer signée si elle en trouve une. Si le paramètre *bSigned* est VRAI, spécifiant que la valeur à récupérer est une valeur d’entrée signée, jetez la valeur de retour à un type **int.** Pour obtenir des informations d’erreur étendues, appelez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Valeur de retour

En cas de succès, la variable pointée par *lpTrans* est définie sur TRUE, et la valeur de rendement est la valeur traduite du texte de contrôle.

Si la fonction échoue, la variable indiquée par *lpTrans* est réglée sur FALSE, et la valeur de rendement est nulle. Notez que, puisque zéro est une valeur traduite possible, une valeur de rendement de zéro n’indique pas en soi l’échec.

Si *lpTrans* est NULL, la fonction ne renvoie aucune information sur le succès ou l’échec.

### <a name="remarks"></a>Notes

La fonction traduit le texte récupéré en dépouillant les espaces supplémentaires au début du texte, puis en convertissant les chiffres décimaux. La fonction cesse de se traduire lorsqu’elle atteint la fin du texte ou rencontre un caractère nonnumérique.

Cette fonction renvoie zéro si la valeur traduite est supérieure à INT_MAX (pour les numéros signés) ou UINT_MAX (pour les numéros non signés).

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText

Récupère le texte du contrôle donné.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identifiant du contrôle.

*lpStr*<br/>
Pointeur sur le texte du contrôle.

*nMaxCount (en)*<br/>
Spécifie la longueur maximale, en caractères, de la corde à copier à la mémoire tampon pointée par *lpStr*. Si la longueur de la ficelle dépasse la limite, la ficelle est tronquée.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour spécifie le nombre de caractères copiés sur le tampon, sans compter le caractère nul de fin.

Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations d’erreur étendues, appelez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

Détermine si le conteneur gère WM_SETFOCUS messages.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le conteneur traite WM_SETFOCUS messages; autrement zéro.

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

Traite les messages de fenêtre pour les commandes sans fenêtre.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Paramètres

*message*<br/>
L’identifiant pour le message de fenêtre, fourni par Windows.

*wParam*<br/>
Paramètre du message; fourni par Windows. Spécifie des informations supplémentaires spécifiques au message. Le contenu de ce paramètre dépend de la valeur du paramètre du *message.*

*lParam*<br/>
Paramètre du message; fourni par Windows. Spécifie des informations supplémentaires spécifiques au message. Le contenu de ce paramètre dépend de la valeur du paramètre du *message.*

*plResult*<br/>
Code de résultat Windows. Spécifie le résultat du traitement du message et dépend du message envoyé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour personnaliser la manipulation des messages de contrôle sans fenêtre.

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked

Détermine l’état du bouton spécifié.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Paramètres

*nIDButton (en)*<br/>
L’identifiant du contrôle du bouton.

### <a name="return-value"></a>Valeur de retour

La valeur de retour, à partir d’un bouton créé avec le BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON, ou BS_3STATE style. Il peut s'agir d'une des méthodes suivantes :

- BST_CHECKED Button est vérifié.

- BST_INDETERMINATE Button est grisé, indiquant un état indéterminé (s’applique uniquement si le bouton a le style BS_3STATE ou BS_AUTO3STATE).

- BST_UNCHECKED Button est effacé.

### <a name="remarks"></a>Notes

Si le bouton est un contrôle à trois états, la fonction membre détermine s’il est tamisé, vérifié, ou ni l’un ni l’autre.

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COleControlContainer::m_crBack

La couleur de fond du récipient.

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COleControlContainer::m_crFore

La couleur de premier plan du récipient.

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds

Une liste des sites de contrôle hébergés par le conteneur.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

Le nombre de commandes sans fenêtre hébergées par le conteneur de contrôle.

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COleControlContainer::m_pOleFont

Un pointeur à la police OLE du site de contrôle personnalisé.

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture

Pointeur vers le site de contrôle de capture.

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus

Un pointeur vers le site de contrôle qui a actuellement l’accent sur les entrées.

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive

Un pointeur vers le site de contrôle qui est activé sur place.

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COleControlContainer::m_pWnd

Un pointeur de l’objet de fenêtre associé au conteneur.

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COleControlContainer::m_siteMap

La carte du site.

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COleControlContainer::OnPaint

Appelé par le cadre pour traiter WM_PAINT demandes.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Un pointeur sur le contexte de l’appareil utilisé par le conteneur.

### <a name="return-value"></a>Valeur de retour

Nonzero si le message a été manipulé; autrement zéro.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour personnaliser le processus de peinture.

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COleControlContainer::OnUIActivate

Appelé par le cadre lorsque le site de contrôle, pointé par *pSite*, est sur le point d’être activé en place.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Paramètres

*pSite (en)*<br/>
Un pointeur vers le site de contrôle sur le point d’être activé sur place.

### <a name="remarks"></a>Notes

L’activation sur place signifie que le menu principal du conteneur est remplacé par un menu composite sur place.

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate

Appelé par le cadre lorsque le site de contrôle, pointé par *pSite*, est sur le point d’être désactivé.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Paramètres

*pSite (en)*<br/>
Un pointeur vers le site de contrôle sur le point d’être désactivé.

### <a name="remarks"></a>Notes

Lorsque cette notification est reçue, le conteneur doit réinstaller son interface utilisateur et mettre au point.

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COleControlContainer::ScrollChildren

Appelé par le cadre lorsque des messages de défilement sont reçus d’une fenêtre enfant.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Paramètres

*Dx*<br/>
La quantité, en pixels, de défilement le long de l’axe x.

*Dy*<br/>
La quantité, en pixels, de défilement le long de l’axe y.

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

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
Spécifie l’identifiant du contrôle qui reçoit le message.

*message*<br/>
Spécifie le message à envoyer.

*wParam*<br/>
Spécifie des informations supplémentaires spécifiques au message.

*lParam*<br/>
Spécifie des informations supplémentaires spécifiques au message.

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

Définit le texte d’un contrôle dans une boîte de dialogue à la représentation de chaîne d’une valeur integer spécifiée.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identifiant du contrôle.

*nValue (en)*<br/>
La valeur de l’intégrant à afficher.

*bSigned*<br/>
Précise si le *paramètre nValue* est signé ou non signé. Si ce paramètre est VRAI, *nValue* est signé. Si ce paramètre est VRAI et *nValue* est inférieur à zéro, un signe moins est placé avant le premier chiffre de la chaîne. Si ce paramètre est FALSE, *nValue n’est* pas signé.

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText

Définit le texte du contrôle spécifié, à l’aide du texte contenu dans *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’identifiant du contrôle.

*lpszString (lpszString)*<br/>
Pointeur sur le texte du contrôle.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager, classe](../../mfc/reference/coccmanager-class.md)
