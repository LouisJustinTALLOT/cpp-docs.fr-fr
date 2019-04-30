---
title: COccManager, classe
ms.date: 11/04/2016
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
ms.openlocfilehash: a83f58b8de2411577d9fc025f7a8f8dc535ea8b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388265"
---
# <a name="coccmanager-class"></a>COccManager, classe

Gère divers sites de contrôle personnalisés ; implémentée par les objets `COleControlContainer` et `COleControlSite` .

## <a name="syntax"></a>Syntaxe

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COccManager::CreateContainer](#createcontainer)|Crée un objet `COleContainer`.|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Crée les contrôles ActiveX, hébergés par associé `COleContainer` objet.|
|[COccManager::CreateSite](#createsite)|Crée un objet `COleClientSite`.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Récupère le code du bouton par défaut.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Détermine la cible d’un message de la boîte de dialogue.|
|[COccManager::IsLabelControl](#islabelcontrol)|Détermine si le contrôle spécifié est un contrôle d’étiquette.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Détermine si le mnémonique actuel correspond à la mnémonique du contrôle spécifié.|
|[COccManager::OnEvent](#onevent)|Essaie de gérer l’événement spécifié.|
|[COccManager::PostCreateDialog](#postcreatedialog)|Libère les ressources allouées lors de la création de la boîte de dialogue.|
|[COccManager::PreCreateDialog](#precreatedialog)|Traite un modèle de boîte de dialogue pour les contrôles ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Active ou désactive l’état par défaut du contrôle spécifié.|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Sépare les contrôles ActiveX existants à partir de contrôles communs dans le modèle de boîte de dialogue spécifiée.|

## <a name="remarks"></a>Notes

La classe de base, `CNoTrackObject`, est une classe de base non documentée (située dans AFXTLS. (H). Conçu pour être utilisé par l’infrastructure MFC, classes dérivées de la `CNoTrackObject` classe sont exempts de détection des fuites de mémoire. Il n’est pas recommandé de dériver directement de `CNoTrackObject`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxocc.h

##  <a name="createcontainer"></a>  COccManager::CreateContainer

Appelé par le framework pour créer un conteneur de contrôle.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers l’objet de fenêtre associé au conteneur de site personnalisé.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le conteneur nouvellement créé ; Sinon, NULL.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la création de sites personnalisés, consultez [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls

Appelez cette fonction pour créer des contrôles ActiveX spécifiés par le *pOccDialogInfo* paramètre.

```
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    LPCTSTR lpszResourceName,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    void* lpResource,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
Pointeur vers le parent de l’objet de la boîte de dialogue.

*lpszResourceName*<br/>
Le nom de la ressource en cours de création.

*pOccDialogInfo*<br/>
Pointeur vers le modèle de boîte de dialogue permet de créer l’objet de la boîte de dialogue.

*lpResource*<br/>
Pointeur vers une ressource.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le contrôle a été créé avec succès ; Sinon, zéro.

##  <a name="createsite"></a>  COccManager::CreateSite

Appelé par le framework pour créer un site de contrôle, hébergé par le conteneur vers lequel pointé *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Paramètres

*pCtrlCont*<br/>
Pointeur vers le conteneur de contrôle qui héberge le nouveau site de contrôle.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le site de contrôle qui vient d’être créé.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour créer un contrôle personnalisé de site, à l’aide de votre [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-classe dérivée.

Chaque conteneur de contrôle peut héberger plusieurs sites. Créez des sites supplémentaires avec plusieurs appels à `CreateSite`.

##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode

Appelez cette fonction pour déterminer si le contrôle est un bouton de commande par défaut.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
L’objet de fenêtre qui contient le contrôle de bouton.

### <a name="return-value"></a>Valeur de retour

Une des valeurs suivantes :

- Contrôle de DLGC_DEFPUSHBUTTON est le bouton par défaut dans la boîte de dialogue.

- Contrôle de DLGC_UNDEFPUSHBUTTON n’est pas le bouton par défaut dans la boîte de dialogue.

- **0** contrôle n’est pas un bouton.

##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage

Appelé par l’infrastructure pour déterminer si un message est destiné à la boîte de dialogue spécifiée et, s’il est, traite le message.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*pWndDlg*<br/>
Pointeur vers la boîte de dialogue cible prévue du message.

*lpMsg*<br/>
Un pointeur vers un `MSG` structure qui contient le message à vérifier.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le message est traité ; Sinon, zéro.

### <a name="remarks"></a>Notes

Le comportement par défaut de `IsDialogMessage` consiste à vérifier les messages de clavier et de les convertir en les sélections pour la boîte de dialogue correspondante. Par exemple, la touche TAB, lorsque vous appuyez sur, sélectionne le contrôle suivant ou le groupe de contrôles.

Remplacez cette fonction pour fournir un comportement personnalisé pour les messages envoyés à la boîte de dialogue spécifiée.

##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl

Appelez cette fonction pour déterminer si le contrôle spécifié est un contrôle d’étiquette.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre qui contient le contrôle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le contrôle est une étiquette ; sinon zéro

### <a name="remarks"></a>Notes

Un contrôle label est une qui agit comme une étiquette pour le contrôle qui est le suivant dans l’ordre.

##  <a name="ismatchingmnemonic"></a>  COccManager::IsMatchingMnemonic

Appelez cette fonction pour déterminer si le mnémonique actuel correspond à représentée par le contrôle.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre qui contient le contrôle.

*lpMsg*<br/>
Pointeur vers le message contenant le mnémonique pour faire correspondre.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le mnémonique correspond au contrôle ; sinon zéro

### <a name="remarks"></a>Notes

##  <a name="onevent"></a>  COccManager::OnEvent

Appelé par l’infrastructure pour gérer l’événement spécifié.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Paramètres

*pCmdTarget*<br/>
Un pointeur vers le `CCmdTarget` objet tenter de gérer l’événement

*idCtrl*<br/>
L’ID de ressource du contrôle.

*pEvent*<br/>
L’événement géré.

*pHandlerInfo*<br/>
Si non NULL, `OnEvent` renseigne le `pTarget` et `pmf` membres de la `AFX_CMDHANDLERINFO` structure au lieu de la distribution de la commande. En règle générale, ce paramètre doit être NULL.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’événement a été géré, zéro sinon.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser le processus de gestion des événements par défaut.

##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog

Appelé par l’infrastructure pour traiter un modèle de boîte de dialogue pour les contrôles ActiveX avant de créer la boîte de dialogue proprement dites.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Paramètres

*pOccDialogInfo*<br/>
Un `_AFX_OCC_DIALOG_INFO` structure contenant des informations sur le modèle de boîte de dialogue et tous les contrôles ActiveX hébergées par la boîte de dialogue.

*pOrigTemplate*<br/>
Pointeur vers le modèle de boîte de dialogue à utiliser lors de la création de la boîte de dialogue.

### <a name="return-value"></a>Valeur de retour

Pointeur vers une structure de modèle de boîte de dialogue permet de créer la boîte de dialogue.

### <a name="remarks"></a>Notes

Le comportement par défaut effectue un appel à `SplitDialogTemplate`, déterminer s’il existe tout contrôle ActiveX contrôle présent, puis retourne le modèle de boîte de dialogue résultante.

Remplacez cette fonction pour personnaliser le processus de création d’une boîte de dialogue héberger des contrôles ActiveX.

##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog

Appelé par l’infrastructure pour libérer de la mémoire allouée pour le modèle de boîte de dialogue.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Paramètres

*pOccDialogInfo*<br/>
Un `_AFX_OCC_DIALOG_INFO` structure contenant des informations sur le modèle de boîte de dialogue et tous les contrôles ActiveX hébergées par la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette mémoire a été allouée par un appel à `SplitDialogTemplate`et a été utilisée pour tous les contrôles ActiveX hébergés dans la boîte de dialogue.

Remplacez cette fonction pour personnaliser le processus de nettoyage de toutes les ressources utilisées par l’objet de boîte de dialogue.

##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton

Appelez cette fonction pour définir le contrôle comme le bouton par défaut.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre qui contient le contrôle.

*bDefault*<br/>
Différent de zéro si le contrôle devient le bouton par défaut ; Sinon, zéro.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Le contrôle doit avoir le OLEMISC_ACTSLIKEBUTTON status bit défini. Pour plus d’informations sur les indicateurs OLEMISC, consultez le [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) rubrique dans le SDK Windows.

##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate

Appelé par l’infrastructure pour fractionner les contrôles ActiveX à partir de contrôles de boîte de dialogue commune.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Paramètres

*pTemplate*<br/>
Pointeur vers le modèle de boîte de dialogue doit être examinée.

*ppOleDlgItems*<br/>
Une liste de pointeurs vers des éléments de boîte de dialogue qui sont des contrôles ActiveX.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une structure de modèle de boîte de dialogue contenant uniquement des contrôles non ActiveX. Si les contrôles ActiveX sont présents, la valeur NULL est retournée.

### <a name="remarks"></a>Notes

Si tous les contrôles ActiveX sont trouvés, le modèle est analysé et un nouveau modèle, qui contient uniquement des contrôles non ActiveX, est créé. Tous les contrôles ActiveX trouvés pendant ce processus sont ajoutés à *ppOleDlgItems*.

S’il n’y a pas de contrôles ActiveX dans le modèle, la valeur NULL est retournée *.*

> [!NOTE]
>  Mémoire allouée pour le nouveau modèle est libéré dans le `PostCreateDialog` (fonction).

Remplacez cette fonction pour personnaliser ce processus.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite, classe](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer, classe](../../mfc/reference/colecontrolcontainer-class.md)
