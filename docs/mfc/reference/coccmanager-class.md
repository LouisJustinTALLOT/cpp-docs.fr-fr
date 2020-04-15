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
ms.openlocfilehash: 5637a4709e90bb14caff3fe4e396487e62e213e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360364"
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
|[COccManager::CreateContainer](#createcontainer)|Crée un objet `COleContainer` .|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Crée des commandes ActiveX, `COleContainer` hébergées par l’objet associé.|
|[COccManager::CreateSite](#createsite)|Crée un objet `COleClientSite` .|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Récupère le code du bouton par défaut.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Détermine la cible d’un message de dialogue.|
|[COccManager::IsLabelControl](#islabelcontrol)|Détermine si le contrôle spécifié est un contrôle de l’étiquette.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Détermine si le mnémonique actuel correspond au mnémonique du contrôle spécifié.|
|[COccManager::OnEvent](#onevent)|Tentatives pour gérer l’événement spécifié.|
|[COccManager::PostCreateDialog](#postcreatedialog)|Libère les ressources allouées lors de la création de dialogue.|
|[COccManager::PreCreateDialog](#precreatedialog)|Traite un modèle de dialogue pour les contrôles ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Toggles l’état par défaut du contrôle spécifié.|
|[COccManager:SplitDialogTemplate](#splitdialogtemplate)|Sépare tous les contrôles ActiveX existants des contrôles courants dans le modèle de dialogue spécifié.|

## <a name="remarks"></a>Notes

La classe `CNoTrackObject`de base, , est une classe de base sans papiers (situé dans AFXTLS. H). Conçues pour être utilisées par le cadre `CNoTrackObject` MFC, les classes dérivées de la classe sont exemptées de la détection des fuites de mémoire. Il n’est pas recommandé `CNoTrackObject`que vous tiriez directement de .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Spécifications

**En-tête:** afxocc.h

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a>COccManager::CreateContainer

Appelé par le cadre pour créer un conteneur de contrôle.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Un pointeur vers l’objet de fenêtre associé au conteneur personnalisé du site.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le conteneur nouvellement créé; autrement NULL.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la création de sites personnalisés, voir [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>COccManager::CreateDlgControls

Appelez cette fonction pour créer des contrôles ActiveX spécifiés par le paramètre *pOccDialogInfo.*

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
Un pointeur pour le parent de l’objet de dialogue.

*lpszResourceName (en)*<br/>
Le nom de la ressource en cours de création.

*pOccDialogInfo*<br/>
Un pointeur vers le modèle de dialogue utilisé pour créer l’objet de dialogue.

*lpResource*<br/>
Un pointeur vers une ressource.

### <a name="return-value"></a>Valeur de retour

Nonzero si le contrôle a été créé avec succès; autrement zéro.

## <a name="coccmanagercreatesite"></a><a name="createsite"></a>COccManager::CreateSite

Appelé par le cadre pour créer un site de contrôle, hébergé par le conteneur pointé par *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Paramètres

*pCtrlCont*<br/>
Un pointeur pour le conteneur de contrôle hébergeant le nouveau site de contrôle.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le site de contrôle nouvellement créé.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour créer un site de contrôle personnalisé, en utilisant votre classe dérivée [de COleControlSite.](../../mfc/reference/colecontrolsite-class.md)

Chaque conteneur de commande peut héberger plusieurs sites. Créez des sites supplémentaires `CreateSite`avec plusieurs appels vers .

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>COccManager::GetDefBtnCode

Appelez cette fonction pour déterminer si le contrôle est un bouton push par défaut.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
L’objet de fenêtre contenant le contrôle du bouton.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs suivantes :

- DLGC_DEFPUSHBUTTON Control est le bouton par défaut dans le dialogue.

- DLGC_UNDEFPUSHBUTTON Control n’est pas le bouton par défaut dans le dialogue.

- **0** Le contrôle n’est pas un bouton.

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>COccManager::IsDialogMessage

Appelé par le cadre pour déterminer si un message est destiné à la boîte de dialogue spécifiée et, si c’est le cas, traite le message.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*pWndDlg*<br/>
Un pointeur sur le dialogue cible prévu du message.

*lpMsg*<br/>
Un pointeur `MSG` vers une structure qui contient le message à vérifier.

### <a name="return-value"></a>Valeur de retour

Nonzero si le message est traité; autrement zéro.

### <a name="remarks"></a>Notes

Le comportement `IsDialogMessage` par défaut est de vérifier les messages clavier et de les convertir en sélections pour la boîte de dialogue correspondante. Par exemple, la clé TAB, lorsqu’elle est pressée, sélectionne le contrôle suivant ou le groupe de commandes.

Remplacer cette fonction pour fournir un comportement personnalisé pour les messages envoyés au dialogue spécifié.

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>COccManager::IsLabelControl

Appelez cette fonction pour déterminer si le contrôle spécifié est un contrôle d’étiquette.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Un pointeur à la fenêtre contenant le contrôle.

### <a name="return-value"></a>Valeur de retour

Nonzero si le contrôle est une étiquette; sinon zéro

### <a name="remarks"></a>Notes

Un contrôle de l’étiquette est celui qui agit comme une étiquette pour tout contrôle est le prochain dans la commande.

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

Appelez cette fonction pour déterminer si les correspondances mnémoniques actuelles qui ont représenté par le contrôle.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Un pointeur à la fenêtre contenant le contrôle.

*lpMsg*<br/>
Un pointeur sur le message contenant le mnémonique à assortir.

### <a name="return-value"></a>Valeur de retour

Nonzero si le mnémonique correspond au contrôle; sinon zéro

### <a name="remarks"></a>Notes

## <a name="coccmanageronevent"></a><a name="onevent"></a>COccManager::OnEvent

Appelé par le cadre pour gérer l’événement spécifié.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Paramètres

*pCmdTarget*<br/>
Un pointeur `CCmdTarget` sur l’objet qui tente de gérer l’événement

*idCtrl idCtrl*<br/>
L’ID de ressource du contrôle.

*pEvent*<br/>
L’événement est géré.

*pHandlerInfo (en anglais)*<br/>
Si ce `OnEvent` n’est `pTarget` pas `pmf` NULL, `AFX_CMDHANDLERINFO` remplit le et les membres de la structure au lieu d’expédier le commandement. Typiquement, ce paramètre devrait être NULL.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’événement a été géré, sinon zéro.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser le processus de traitement par défaut des événements.

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COccManager::PreCreateDialog

Appelé par le cadre pour traiter un modèle de dialogue pour les contrôles ActiveX avant de créer la boîte de dialogue réelle.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Paramètres

*pOccDialogInfo*<br/>
Une `_AFX_OCC_DIALOG_INFO` structure contenant des informations sur le modèle de dialogue et tous les contrôles ActiveX hébergés par le dialogue.

*pOrigTemplate*<br/>
Un pointeur sur le modèle de dialogue à utiliser dans la création de la boîte de dialogue.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une structure de modèle de dialogue utilisée pour créer la boîte de dialogue.

### <a name="remarks"></a>Notes

Le comportement par défaut `SplitDialogTemplate`fait un appel à , déterminer s’il ya des contrôles ActiveX présents, puis retourne le modèle de dialogue résultant.

Remplacez cette fonction pour personnaliser le processus de création d’une boîte de dialogue hébergeant les contrôles ActiveX.

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>COccManager::PostCreateDialog

Appelé par le cadre à la mémoire libre allouée pour le modèle de dialogue.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Paramètres

*pOccDialogInfo*<br/>
Une `_AFX_OCC_DIALOG_INFO` structure contenant des informations sur le modèle de dialogue et tous les contrôles ActiveX hébergés par le dialogue.

### <a name="remarks"></a>Notes

Cette mémoire a été attribuée `SplitDialogTemplate`par un appel à , et a été utilisé pour tous les contrôles Hébergés ActiveX dans la boîte de dialogue.

Remplacer cette fonction pour personnaliser le processus de nettoyage des ressources utilisées par l’objet de boîte de dialogue.

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>COccManager::SetDefaultButton

Appelez cette fonction pour définir le contrôle comme le bouton par défaut.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Un pointeur à la fenêtre contenant le contrôle.

*bDefault (en)*<br/>
Nonzero si le contrôle doit devenir le bouton par défaut; autrement zéro.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

> [!NOTE]
> Le contrôle doit avoir le OLEMISC_ACTSLIKEBUTTON jeu de statut. Pour plus d’informations sur les drapeaux OLEMISC, voir le sujet [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) dans le SDK Windows.

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>COccManager:SplitDialogTemplate

Appelé par le cadre à diviser les contrôles ActiveX des contrôles de dialogue communs.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Paramètres

*pTemplate (en)*<br/>
Un pointeur sur le modèle de dialogue à examiner.

*ppOleDlgItems*<br/>
Une liste de pointeurs pour dialoguer les éléments de boîte qui sont des contrôles ActiveX.

### <a name="return-value"></a>Valeur de retour

Pointeur d’une structure de modèle de dialogue contenant uniquement des contrôles non-ActiveX. Si aucun contrôle ActiveX n’est présent, NULL est retourné.

### <a name="remarks"></a>Notes

Si des contrôles ActiveX sont trouvés, le modèle est analysé et un nouveau modèle, contenant uniquement des contrôles non actifs, est créé. Tous les contrôles ActiveX trouvés au cours de ce processus sont ajoutés à *ppOleDlgItems*.

S’il n’y a pas de contrôles ActiveX dans le modèle, NULL est retourné *.*

> [!NOTE]
> La mémoire allouée pour le `PostCreateDialog` nouveau modèle est libérée dans la fonction.

Remplacer cette fonction pour personnaliser ce processus.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[Classe COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)
