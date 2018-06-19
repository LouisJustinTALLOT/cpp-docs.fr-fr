---
title: Classe de COccManager | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b292196eb6ac8178ba43f0e66bd4814368c916fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376110"
---
# <a name="coccmanager-class"></a>Classe de COccManager
Gère divers sites de contrôle personnalisés ; implémentée par les objets `COleControlContainer` et `COleControlSite` .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COccManager::CreateContainer](#createcontainer)|Crée un **COleContainer** objet.|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|Crée des contrôles ActiveX, hébergés par associé `COleContainer` objet.|  
|[COccManager::CreateSite](#createsite)|Crée un objet `COleClientSite`.|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|Récupère le code du bouton par défaut.|  
|[COccManager::IsDialogMessage](#isdialogmessage)|Détermine la cible d’un message de la boîte de dialogue.|  
|[COccManager::IsLabelControl](#islabelcontrol)|Détermine si le contrôle spécifié est un contrôle d’étiquette.|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Détermine si la mnémonique actuelle correspond à la mnémonique du contrôle spécifié.|  
|[COccManager::OnEvent](#onevent)|Essaie de gérer l’événement spécifié.|  
|[COccManager::PostCreateDialog](#postcreatedialog)|Libère les ressources allouées pendant la création de la boîte de dialogue.|  
|[COccManager::PreCreateDialog](#precreatedialog)|Traite un modèle de boîte de dialogue pour les contrôles ActiveX.|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|Active ou désactive l’état par défaut du contrôle spécifié.|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Sépare les contrôles ActiveX existants à partir de contrôles communs dans le modèle de boîte de dialogue spécifiée.|  
  
## <a name="remarks"></a>Notes  
 La classe de base **CNoTrackObject**, est une classe de base non documentée (située dans AFXTLS. (H). Conçu pour une utilisation par l’infrastructure MFC, les classes dérivées de la **CNoTrackObject** classe sont exempts de la détection des fuites de mémoire. Il n’est pas recommandé dériver directement de **CNoTrackObject**.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxocc.h  
  
##  <a name="createcontainer"></a>  COccManager::CreateContainer  
 Appelé par l’infrastructure pour créer un conteneur de contrôle.  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWnd`  
 Pointeur vers l’objet fenêtre associé au conteneur de site personnalisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le conteneur nouvellement créé ; dans le cas contraire **NULL**.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur la création de sites personnalisés, consultez [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).  
  
##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls  
 Appelez cette fonction pour créer des contrôles ActiveX spécifiés par le `pOccDialogInfo` paramètre.  
  
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
 *pWndParent*  
 Pointeur vers le parent de l’objet de la boîte de dialogue.  
  
 `lpszResourceName`  
 Le nom de la ressource en cours de création.  
  
 `pOccDialogInfo`  
 Pointeur vers le modèle de boîte de dialogue permet de créer l’objet de la boîte de dialogue.  
  
 `lpResource`  
 Pointeur vers une ressource.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le contrôle a été créé avec succès ; Sinon, zéro.  
  
##  <a name="createsite"></a>  COccManager::CreateSite  
 Appelée par l’infrastructure pour créer un site de contrôle, hébergé par le conteneur vers lequel pointé `pCtrlCont`.  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Paramètres  
 `pCtrlCont`  
 Pointeur vers le conteneur de contrôle qui héberge le nouveau site de contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le site de contrôle qui vient d’être créé.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour créer un contrôle personnalisé de site, à l’aide de votre [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-classe dérivée.  
  
 Chaque conteneur de contrôle peut héberger plusieurs sites. Créer des sites supplémentaires avec les appels multiples à `CreateSite`.  
  
##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode  
 Appelez cette fonction pour déterminer si le contrôle est un bouton de commande par défaut.  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWnd`  
 L’objet de la fenêtre contenant le contrôle bouton.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs suivantes :  
  
- **DLGC_DEFPUSHBUTTON** contrôle est le bouton par défaut dans la boîte de dialogue.  
  
- **DLGC_UNDEFPUSHBUTTON** contrôle n’est pas le bouton par défaut dans la boîte de dialogue.  
  
- **0** contrôle n’est pas un bouton.  
  
##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage  
 Appelé par l’infrastructure pour déterminer si un message est destiné à la boîte de dialogue spécifiée et, s’il s’agit, traite le message.  
  
```  
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWndDlg*  
 Pointeur vers la boîte de dialogue de destination du message.  
  
 `lpMsg`  
 Un pointeur vers un `MSG` structure qui contient le message doit être vérifiée.  
  
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
 `pWnd`  
 Pointeur vers la fenêtre contenant le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le contrôle est une étiquette. sinon zéro  
  
### <a name="remarks"></a>Notes  
 Un contrôle label est un objet qui agit comme une étiquette pour le contrôle est le suivant dans l’ordre.  
  
##  <a name="ismatchingmnemonic"></a>  COccManager::IsMatchingMnemonic  
 Appelez cette fonction pour déterminer si le mnémonique actuel correspond à représenté par le contrôle.  
  
```  
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,  
    LPMSG lpMsg);

 
static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWnd`  
 Pointeur vers la fenêtre contenant le contrôle.  
  
 `lpMsg`  
 Pointeur vers le message contenant la mnémonique pour faire correspondre.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la mnémonique correspond au contrôle ; sinon zéro  
  
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
 *pCmdTarget*  
 Un pointeur vers le `CCmdTarget` objet de gérer l’événement  
  
 `idCtrl`  
 L’ID de ressource du contrôle.  
  
 `pEvent`  
 L’événement géré.  
  
 `pHandlerInfo`  
 Si ce n’est pas **NULL**, `OnEvent` renseigne le **pTarget** et **pmf** membres de la **AFX_CMDHANDLERINFO** à la place de la structure la distribution de la commande. En règle générale, ce paramètre doit être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’événement a été géré, sinon zéro.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour personnaliser le processus de gestion des événements par défaut.  
  
##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog  
 Appelé par l’infrastructure pour traiter un modèle de boîte de dialogue pour les contrôles ActiveX avant de créer la boîte de dialogue réel.  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>Paramètres  
 `pOccDialogInfo`  
 Un **_AFX_OCC_DIALOG_INFO** structure contenant des informations sur le modèle de boîte de dialogue et les contrôles ActiveX hébergés par la boîte de dialogue.  
  
 *pOrigTemplate*  
 Pointeur vers le modèle de boîte de dialogue à utiliser lors de la création de la boîte de dialogue.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une structure de modèle de boîte de dialogue permet de créer la boîte de dialogue.  
  
### <a name="remarks"></a>Notes  
 Le comportement par défaut effectue un appel à `SplitDialogTemplate`, déterminer s’il y a tout contrôle ActiveX contrôle présent, puis retourne le modèle de boîte de dialogue résultante.  
  
 Remplacez cette fonction pour personnaliser le processus de création d’une boîte de dialogue héberger des contrôles ActiveX.  
  
##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog  
 Appelé par l’infrastructure pour libérer de la mémoire allouée pour le modèle de boîte de dialogue.  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Paramètres  
 `pOccDialogInfo`  
 Un **_AFX_OCC_DIALOG_INFO** structure contenant des informations sur le modèle de boîte de dialogue et les contrôles ActiveX hébergés par la boîte de dialogue.  
  
### <a name="remarks"></a>Notes  
 Cette mémoire a été allouée par un appel à `SplitDialogTemplate`et a été utilisé pour tous les contrôles ActiveX hébergés dans la boîte de dialogue.  
  
 Remplacez cette fonction pour personnaliser le processus de nettoyage de toutes les ressources utilisées par l’objet de boîte de dialogue.  
  
##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton  
 Appelez cette fonction pour définir le contrôle comme le bouton par défaut.  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWnd`  
 Pointeur vers la fenêtre contenant le contrôle.  
  
 `bDefault`  
 Différent de zéro si le contrôle doit être le bouton par défaut ; Sinon, zéro.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Le contrôle doit avoir la **OLEMISC_ACTSLIKEBUTTON** état bit défini. Pour plus d’informations sur **OLEMISC** indicateurs, consultez la [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) rubrique dans le SDK Windows.  
  
##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate  
 Appelé par l’infrastructure pour fractionner les contrôles ActiveX à partir de contrôles de boîte de dialogue commune.  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>Paramètres  
 `pTemplate`  
 Pointeur vers le modèle de boîte de dialogue doit être examinée.  
  
 `ppOleDlgItems`  
 Une liste de pointeurs vers les éléments de boîte de dialogue qui sont des contrôles ActiveX.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers une structure de modèle de boîte de dialogue contenant uniquement des contrôles ActiveX non. Si les contrôles ActiveX sont présents, **NULL** est retourné.  
  
### <a name="remarks"></a>Notes  
 Si tous les contrôles ActiveX sont trouvées, le modèle est analysé et un nouveau modèle, qui contient uniquement les contrôles ActiveX non, est créé. Tous les contrôles ActiveX trouvés au cours de ce processus sont ajoutés à `ppOleDlgItems`.  
  
 S’il en existe pas de contrôles ActiveX dans le modèle, **NULL** est retourné *.*  
  
> [!NOTE]
>  Mémoire allouée pour le nouveau modèle est libéré dans le `PostCreateDialog` (fonction).  
  
 Remplacez cette fonction pour personnaliser ce processus.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de COleControlSite](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer, classe](../../mfc/reference/colecontrolcontainer-class.md)
