---
description: 'En savoir plus sur : classe COccManager'
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
ms.openlocfilehash: 8acd39825f7f842a266a4b1dbf187ba4f7f9b5ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331424"
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
|[COccManager :: CreateContainer](#createcontainer)|Crée un objet `COleContainer`.|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Crée des contrôles ActiveX, hébergés par l' `COleContainer` objet associé.|
|[COccManager :: CreateSite](#createsite)|Crée un objet `COleClientSite`.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Récupère le code du bouton par défaut.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Détermine la cible d’un message de dialogue.|
|[COccManager::IsLabelControl](#islabelcontrol)|Détermine si le contrôle spécifié est un contrôle d’étiquette.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Détermine si le mnémonique actuel correspond à la mnémonique du contrôle spécifié.|
|[COccManager :: OnEvent](#onevent)|Tente de gérer l’événement spécifié.|
|[COccManager ::P ostCreateDialog](#postcreatedialog)|Libère les ressources allouées pendant la création du dialogue.|
|[COccManager ::P reCreateDialog](#precreatedialog)|Traite un modèle de boîte de dialogue pour les contrôles ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Active ou désactive l’État par défaut du contrôle spécifié.|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Sépare les contrôles ActiveX existants des contrôles communs dans le modèle de boîte de dialogue spécifié.|

## <a name="remarks"></a>Notes

La classe de base, `CNoTrackObject` , est une classe de base non documentée (située dans AFXTLS. H). Conçu pour être utilisé par l’infrastructure MFC, les classes dérivées de la `CNoTrackObject` classe sont exemptes de la détection des fuites de mémoire. Il n’est pas recommandé de dériver directement de `CNoTrackObject` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Spécifications

**En-tête :** afxocc. h

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a> COccManager :: CreateContainer

Appelé par l’infrastructure pour créer un conteneur de contrôle.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers l’objet de fenêtre associé au conteneur de site personnalisé.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le conteneur nouvellement créé ; Sinon, NULL.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la création de sites personnalisés, consultez [COleControlContainer :: AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a> COccManager::CreateDlgControls

Appelez cette fonction pour créer des contrôles ActiveX spécifiés par le paramètre *pOccDialogInfo* .

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
Pointeur vers le parent de l’objet Dialog.

*lpszResourceName*<br/>
Nom de la ressource en cours de création.

*pOccDialogInfo*<br/>
Pointeur vers le modèle de boîte de dialogue utilisé pour créer l’objet de boîte de dialogue.

*lpResource*<br/>
Pointeur vers une ressource.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le contrôle a été créé avec succès ; Sinon, zéro.

## <a name="coccmanagercreatesite"></a><a name="createsite"></a> COccManager :: CreateSite

Appelé par l’infrastructure pour créer un site de contrôle, hébergé par le conteneur pointé par *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Paramètres

*pCtrlCont*<br/>
Pointeur vers le conteneur de contrôle qui héberge le nouveau site de contrôle.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le nouveau site de contrôle créé.

### <a name="remarks"></a>Notes

Substituez cette fonction pour créer un site de contrôle personnalisé à l’aide de votre classe dérivée de [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

Chaque conteneur de contrôle peut héberger plusieurs sites. Créer des sites supplémentaires avec plusieurs appels à `CreateSite` .

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a> COccManager::GetDefBtnCode

Appelez cette fonction pour déterminer si le contrôle est un bouton de commande par défaut.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Objet de fenêtre contenant le contrôle bouton.

### <a name="return-value"></a>Valeur renvoyée

Une des valeurs suivantes :

- DLGC_DEFPUSHBUTTON contrôle est le bouton par défaut dans la boîte de dialogue.

- DLGC_UNDEFPUSHBUTTON contrôle n’est pas le bouton par défaut dans la boîte de dialogue.

- le contrôle **0** n’est pas un bouton.

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a> COccManager::IsDialogMessage

Appelée par l’infrastructure pour déterminer si un message est destiné à la boîte de dialogue spécifiée et, si tel est le cas, traite le message.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*pWndDlg*<br/>
Pointeur vers la boîte de dialogue cible prévue du message.

*lpMsg*<br/>
Pointeur vers une `MSG` structure qui contient le message à vérifier.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le message est traité ; Sinon, zéro.

### <a name="remarks"></a>Notes

Le comportement par défaut `IsDialogMessage` consiste à rechercher les messages de clavier et à les convertir en sélections pour la boîte de dialogue correspondante. Par exemple, la touche TAB, lorsqu’elle est enfoncée, sélectionne le contrôle suivant ou le groupe de contrôles.

Remplacez cette fonction pour fournir un comportement personnalisé pour les messages envoyés à la boîte de dialogue spécifiée.

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a> COccManager::IsLabelControl

Appelez cette fonction pour déterminer si le contrôle spécifié est un contrôle Label.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le contrôle est une étiquette ; sinon zéro

### <a name="remarks"></a>Notes

Un contrôle Label est un contrôle qui agit comme une étiquette pour le contrôle suivant dans l’ordre.

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a> COccManager::IsMatchingMnemonic

Appelez cette fonction pour déterminer si le mnémonique actuel correspond à celui représenté par le contrôle.

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
Pointeur vers la fenêtre contenant le contrôle.

*lpMsg*<br/>
Pointeur vers le message contenant le mnémonique à faire correspondre.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le mnémonique correspond au contrôle ; sinon zéro

### <a name="remarks"></a>Notes

## <a name="coccmanageronevent"></a><a name="onevent"></a> COccManager :: OnEvent

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
Pointeur vers l' `CCmdTarget` objet qui tente de gérer l’événement.

*idCtrl*<br/>
ID de ressource du contrôle.

*pEvent*<br/>
Événement qui est géré.

*pHandlerInfo*<br/>
Si la valeur n’est pas NULL, `OnEvent` remplit les `pTarget` `pmf` membres et de la `AFX_CMDHANDLERINFO` structure au lieu de distribuer la commande. En général, ce paramètre doit avoir la valeur NULL.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’événement a été géré ; sinon, zéro.

### <a name="remarks"></a>Notes

Substituez cette fonction pour personnaliser le processus de gestion des événements par défaut.

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a> COccManager ::P reCreateDialog

Appelé par l’infrastructure pour traiter un modèle de boîte de dialogue pour les contrôles ActiveX avant la création de la boîte de dialogue réelle.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Paramètres

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO`Structure contenant des informations sur le modèle de boîte de dialogue et les contrôles ActiveX hébergés par la boîte de dialogue.

*pOrigTemplate*<br/>
Pointeur vers le modèle de boîte de dialogue à utiliser pour créer la boîte de dialogue.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une structure de modèle de boîte de dialogue utilisée pour créer la boîte de dialogue.

### <a name="remarks"></a>Notes

Le comportement par défaut effectue un appel à `SplitDialogTemplate` , en déterminant si des contrôles ActiveX sont présents, puis retourne le modèle de boîte de dialogue résultant.

Substituez cette fonction pour personnaliser le processus de création d’une boîte de dialogue hébergeant des contrôles ActiveX.

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a> COccManager ::P ostCreateDialog

Appelé par l’infrastructure pour libérer de la mémoire allouée pour le modèle de boîte de dialogue.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Paramètres

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO`Structure contenant des informations sur le modèle de boîte de dialogue et les contrôles ActiveX hébergés par la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette mémoire a été allouée par un appel à `SplitDialogTemplate` et a été utilisée pour tous les contrôles ActiveX hébergés dans la boîte de dialogue.

Remplacez cette fonction pour personnaliser le processus de nettoyage des ressources utilisées par l’objet de boîte de dialogue.

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a> COccManager::SetDefaultButton

Appelez cette fonction pour définir le contrôle comme bouton par défaut.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre contenant le contrôle.

*bDefault*<br/>
Différent de zéro si le contrôle doit devenir le bouton par défaut ; Sinon, zéro.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

> [!NOTE]
> Le bit d’état de OLEMISC_ACTSLIKEBUTTON doit être défini pour le contrôle. Pour plus d’informations sur les indicateurs OLEMISC, consultez la rubrique [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) dans le SDK Windows.

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a> COccManager::SplitDialogTemplate

Appelé par l’infrastructure pour fractionner les contrôles ActiveX des contrôles de boîte de dialogue communs.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Paramètres

*pTemplate*<br/>
Pointeur vers le modèle de boîte de dialogue à examiner.

*ppOleDlgItems*<br/>
Liste de pointeurs vers des éléments de boîte de dialogue qui sont des contrôles ActiveX.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une structure de modèle de boîte de dialogue contenant uniquement des contrôles non ActiveX. Si aucun contrôle ActiveX n’est présent, la valeur NULL est retournée.

### <a name="remarks"></a>Notes

Si des contrôles ActiveX sont trouvés, le modèle est analysé et un nouveau modèle, contenant uniquement des contrôles non ActiveX, est créé. Tous les contrôles ActiveX détectés au cours de ce processus sont ajoutés à *ppOleDlgItems*.

S’il n’existe aucun contrôle ActiveX dans le modèle, la valeur NULL est retournée *.*

> [!NOTE]
> La mémoire allouée pour le nouveau modèle est libérée dans la `PostCreateDialog` fonction.

Substituez cette fonction pour personnaliser ce processus.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite, classe](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer, classe](../../mfc/reference/colecontrolcontainer-class.md)
