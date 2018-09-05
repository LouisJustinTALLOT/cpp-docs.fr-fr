---
title: Cbasetabbedpane, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
dev_langs:
- C++
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5585ad86b0c55a7ab47cd026fd0bb7032db11b9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690432"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane, classe
Étend les fonctionnalités de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) pour prendre en charge la création de fenêtres à onglet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|Constructeur par défaut.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CBaseTabbedPane::AddTab](#addtab)|Ajoute un nouvel onglet à un volet à onglets.|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Spécifie si un volet à onglets vide peut être détruit.|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Applique les paramètres d’onglet, qui sont chargés à partir du Registre, à un volet à onglets.|  
|[CBaseTabbedPane::CanFloat](#canfloat)|Détermine si le volet peut flotter. (Substitue [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Détermine si la légende pour le volet à onglets doit afficher le même texte sous l’onglet actif.|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Substitue [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|  
|[CBaseTabbedPane::DetachPane](#detachpane)|Convertit un ou plusieurs volets ancrables à des documents avec onglet MDI.|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Active ou désactive la possibilité du volet à onglets pour synchroniser le texte de légende avec le texte d’étiquette sur l’onglet actif.|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Restaure l’ordre de tabulation interne dans un état par défaut.|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Retourne un volet qui réside dans un onglet lorsque l’onglet est identifié par un index de base zéro de tabulation.|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Retourne un volet qui est identifié par l’ID de volet.|  
|[CBaseTabbedPane::FloatTab](#floattab)|Fait flotter un volet, mais seulement si le volet réside actuellement dans un onglet détachable.|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Retourne l’ordre par défaut des onglets dans le volet.|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Récupère un pointeur vers le premier onglet affiché.|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|Récupère la valeur minimale autorisée pour le volet. (Substitue [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Retourne un handle vers l’icône du volet. (Substitue [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Retourne une liste de volets qui sont contenus dans le volet à onglets.|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Retourne les rectangles englobants pour les zones d’onglet en haut et bas.|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Retourne le nombre d’onglets dans une fenêtre de l’onglet.|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Obtient la fenêtre d’onglet (encapsulé) sous-jacent.|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Retourne le nombre d’onglets affichés.|  
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Détermine si le volet à onglets peut être basculé en mode de masquage automatique.|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Détermine si le volet à onglets est masqué si seul un onglet s’affiche.|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Utilisé en interne pendant la sérialisation.|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Recalcule les informations de disposition pour le volet. (Substitue [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|  
|[CBaseTabbedPane::RemovePane](#removepane)|Supprime un volet dans le volet à onglets.|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|Utilisé en interne pendant la sérialisation.|  
|`CBaseTabbedPane::Serialize`|(Substitue [CDockablePane::Serialize](cdockablepane-class.md).)|  
|`CBaseTabbedPane::SerializeTabWindow`|Utilisé en interne pendant la sérialisation.|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Détermine si la barre de contrôle à onglets est détruite automatiquement.|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Affiche ou masque le volet d’ancrage affiché entre et mode de masquage automatique. (Substitue [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|  
|[CBaseTabbedPane::ShowTab](#showtab)|Affiche ou masque un onglet.|  
  
## <a name="remarks"></a>Notes  
 Cette classe est une classe abstraite et ne peut pas être instanciée. Il implémente les services qui sont communes à tous les types de volets à onglets.  
  
 Actuellement, la bibliothèque inclut deux classes dérivées de volet à onglets : [ctabbedpane, classe](../../mfc/reference/ctabbedpane-class.md) et [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Un `CBaseTabbedPane` objet encapsule un pointeur vers un [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) objet. [Classe CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) devient alors une fenêtre enfant du volet à onglets.  
  
 Pour plus d’informations sur la création de volets à onglets, consultez [CDockablePane, classe](../../mfc/reference/cdockablepane-class.md), [ctabbedpane, classe](../../mfc/reference/ctabbedpane-class.md), et [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 `CBaseTabbedPane`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxBaseTabbedPane.h  
  
##  <a name="addtab"></a>  CBaseTabbedPane::AddTab  
 Ajoute un nouvel onglet à un volet à onglets.  
  
```  
virtual BOOL AddTab(
    CWnd* pNewBar,  
    BOOL bVisible = TRUE,  
    BOOL bSetActive = TRUE,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out] *pNewBar*  
 Pointeur vers le volet à ajouter. Ce pointeur peut devenir non valide après avoir appelé cette méthode. Pour plus d'informations, consultez la section Remarques.  
  
 [in] *bVisible*  
 TRUE pour afficher l’onglet ; Sinon, FALSE.  
  
 [in] *bSetActive*  
 TRUE si l’onglet l’onglet actif ; Sinon, FALSE.  
  
 [in] *bDetachable*  
 TRUE si l’onglet détachables ; Sinon, FALSE.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le volet a été correctement ajouté sous forme d’onglet et a été détruit pas dans le processus. FALSE si le volet ajouté est un objet de type `CBaseTabbedPane`. Pour plus d'informations, consultez la section Remarques.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour ajouter un volet en tant qu’un nouvel onglet dans un volet à onglets. Si *pNewBar* pointe vers un objet de type `CBaseTabbedPane`, tous ses onglets sont copiés dans le volet à onglets, puis *pNewBar* est détruit. Par conséquent, *pNewBar* se transforme en un pointeur non valide et ne doit pas être utilisé.  
  
##  <a name="allowdestroyemptytabbedpane"></a>  CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 Spécifie si un volet à onglets vide peut être détruit.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si un volet à onglets vide peut être détruit ; Sinon, FALSE. Toujours l’implémentation par défaut retourne la valeur TRUE.  
  
### <a name="remarks"></a>Notes  
 Si un volet à onglets vide n’est pas autorisé à être détruit, le framework masque le volet à la place.  
  
##  <a name="applyrestoredtabinfo"></a>  CBaseTabbedPane::ApplyRestoredTabInfo  
 Charge les paramètres de tabulation définis à partir du Registre et les applique à un volet à onglets.  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bUseTabIndexes*  
 Ce paramètre est utilisé en interne par l’infrastructure.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par l’infrastructure lors du rechargement des informations d’état d’ancrage à partir du Registre. La méthode obtient des informations sur l’ordre de tabulation et les noms des onglets pour un volet à onglets.  
  
##  <a name="canfloat"></a>  CBaseTabbedPane::CanFloat  
 Spécifie si le volet à onglets peut flotter.  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le volet peut flotter ; Sinon, FALSE.  
  
##  <a name="cansetcaptiontexttotabname"></a>  CBaseTabbedPane::CanSetCaptionTextToTabName  
 Détermine si la légende pour le volet à onglets doit afficher le même texte sous l’onglet actif.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le texte de légende du volet à onglets est défini pour le texte de l’onglet actif ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 La méthode est utilisée pour déterminer si le texte affiché sur les doublons de légende du volet à onglets l’étiquette de l’onglet actif. Vous pouvez activer ou désactiver cette fonctionnalité en appelant [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).  
  
##  <a name="converttotabbeddocument"></a>  CBaseTabbedPane::ConvertToTabbedDocument  
 Convertit un ou plusieurs volets ancrables à des documents avec onglet MDI.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bActiveTabOnly*  
 Lorsque vous convertissez un volet à onglets, spécifiez TRUE pour convertir uniquement l’onglet actif. Spécifiez la valeur FALSE pour convertir tous les onglets dans le volet.  
  
##  <a name="detachpane"></a>  CBaseTabbedPane::DetachPane  
 Détache un volet dans le volet à onglets.  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pBar*  
 Pointeur vers le volet à détacher.  
  
 [in] *bHide*  
 Paramètre booléen qui spécifie si le framework masque le volet après que elle est détachée.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le framework détache avec succès le volet. FALSE si *pBar* est NULL ou fait référence à un volet qui n’est pas dans le volet à onglets.  
  
### <a name="remarks"></a>Notes  
 Le framework flotte le volet détaché si possible. Pour plus d’informations, consultez [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).  
  
##  <a name="enablesetcaptiontexttotabname"></a>  CBaseTabbedPane::EnableSetCaptionTextToTabName  
 Active ou désactive la possibilité du volet à onglets pour synchroniser le texte de légende avec le texte d’étiquette sur l’onglet actif.  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bActivez*  
 TRUE pour synchroniser la légende du volet à onglets avec la légende de l’onglet actif ; Sinon, FALSE.  
  
##  <a name="filldefaulttabsorderarray"></a>  CBaseTabbedPane::FillDefaultTabsOrderArray  
 Restaure l’ordre de tabulation interne dans un état par défaut.  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsque l’infrastructure restaure une barre Outlook dans un état initial.  
  
##  <a name="findpanebyid"></a>  CBaseTabbedPane::FindPaneByID  
 Retourne un volet identifié par l’ID du volet.  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uBarID*  
 Spécifie l’ID du volet à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le volet s’il a été trouvé ; Sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Cette méthode compare tous les onglets dans le volet et retourne l’un avec l’ID spécifié par le *uBarID* paramètre.  
  
##  <a name="findbarbytabnumber"></a>  CBaseTabbedPane::FindBarByTabNumber  
 Retourne un volet qui réside dans un onglet.  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nTabNum*  
 Spécifie l’index de base zéro de l’onglet à récupérer.  
  
 [in] *bGetWrappedBar*  
 TRUE pour retourner la fenêtre sous-jacente (encapsulée) du volet au lieu du volet lui-même ; Sinon, FALSE. Cela s’applique uniquement aux volets dérivés de [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).  
  
### <a name="return-value"></a>Valeur de retour  
 Si le volet est trouvé, un pointeur valide vers le volet recherché est retourné ; Sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour récupérer le volet résidant dans l’onglet spécifié par le *nTabNum* paramètre.  
  
##  <a name="floattab"></a>  CBaseTabbedPane::FloatTab  
 Fait flotter un volet, mais seulement si le volet réside actuellement dans un onglet détachable.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out] *pBar*  
 Un pointeur vers le volet pour float.  
  
 [in] *nTabID*  
 Spécifie l’index de base zéro de l’onglet en float.  
  
 [in] *dockMethod*  
 Spécifie la méthode à utiliser pour détacher le volet. Pour plus d'informations, consultez la section Remarques.  
  
 [in] *bHide*  
 TRUE pour masquer le volet avant flottante. Sinon, FALSE.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le volet flottantes ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour rendre flottant un volet qui se trouve actuellement dans un onglet détachable.  
  
 Si vous souhaitez détacher un volet par programme, spécifiez DM_SHOW pour la *dockMethod* paramètre. Si vous souhaitez détacher le volet dans la même position où il flottantes précédemment, spécifiez DM_DBL_CLICK comme le *dockMethod* paramètre.  
  
##  <a name="getdefaulttabsorder"></a>  CBaseTabbedPane::GetDefaultTabsOrder  
 Retourne l’ordre par défaut des onglets dans le volet.  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CArray` objet qui spécifie l’ordre par défaut des onglets dans le volet.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode lorsqu’une barre Outlook est réinitialisée à son état initial.  
  
##  <a name="getfirstvisibletab"></a>  CBaseTabbedPane::GetFirstVisibleTab  
 Récupère un pointeur vers le premier onglet affiché.  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iTabNum*  
 Une référence à un entier. Cette méthode écrit l’index de base zéro du premier onglet affiché pour ce paramètre, ou -1 si non affichés onglet est trouvé.  
  
### <a name="return-value"></a>Valeur de retour  
 Si l’opération réussit, un pointeur vers le premier onglet affiché ; Sinon, NULL.  
  
##  <a name="getminsize"></a>  CBaseTabbedPane::GetMinSize  
 Récupère la valeur minimale autorisée pour le volet.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *taille*  
 Un `CSize` objet qui est rempli avec la valeur minimale autorisée.  
  
### <a name="remarks"></a>Notes  
 Si la gestion cohérente des tailles de volet minimale est active ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *taille* est rempli avec la valeur minimale autorisée pour l’onglet actif. Sinon, *taille* est rempli avec la valeur de retour de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpaneicon"></a>  CBaseTabbedPane::GetPaneIcon  
 Récupère la valeur minimale autorisée pour le volet.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *taille*  
 Un `CSize` objet qui est rempli avec la valeur minimale autorisée.  
  
### <a name="remarks"></a>Notes  
 Si la gestion cohérente des tailles de volet minimale est active ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *taille* est rempli avec la valeur minimale autorisée pour l’onglet actif. Sinon, *taille* est rempli avec la valeur de retour de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpanelist"></a>  CBaseTabbedPane::GetPaneList  
 Retourne une liste de volets qui sont contenus dans le volet à onglets.  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *lst*  
 Un `CObList` qui est rempli avec les volets qui sont contenus dans le volet à onglets.  
  
 [in] *pRTCFilter*  
 Si elle n’est pas NULL, la liste retournée contient uniquement les volets qui sont de la classe runtime spécifié.  
  
##  <a name="gettabarea"></a>  CBaseTabbedPane::GetTabArea  
 Retourne les rectangles englobants pour les zones d’onglet en haut et bas.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *rectTabAreaTop*  
 Reçoit les coordonnées d’écran de la zone d’onglet supérieur.  
  
 [out] *rectTabAreaBottom*  
 Reçoit les coordonnées d’écran de la zone d’onglet inférieur.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour déterminer les rectangles englobants, en coordonnées d’écran, pour les zones de l’onglet supérieure et inférieure.  
  
##  <a name="gettabsnum"></a>  CBaseTabbedPane::GetTabsNum  
 Retourne le nombre d’onglets dans une fenêtre de l’onglet.  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’onglets dans le volet à onglets.  
  
##  <a name="getunderlyingwindow"></a>  CBaseTabbedPane::GetUnderlyingWindow  
 Obtient la fenêtre d’onglet (encapsulé) sous-jacent.  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’onglet de fenêtre sous-jacent.  
  
##  <a name="getvisibletabsnum"></a>  CBaseTabbedPane::GetVisibleTabsNum  
 Retourne le nombre d’onglets visibles.  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’onglets visibles, ce qui sera supérieur ou égal à zéro.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour déterminer le nombre d’onglets visibles dans le volet à onglets.  
  
##  <a name="hasautohidemode"></a>  CBaseTabbedPane::HasAutoHideMode  
 Détermine si le volet à onglets peut passer en mode masquage automatique.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le volet peut être basculé en mode de masquage automatique ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Si le mode de masquage automatique est désactivé, aucun bouton pin ne s’affiche sur la légende du volet à onglets.  
  
##  <a name="ishidesingletab"></a>  CBaseTabbedPane::IsHideSingleTab  
 Détermine si le volet à onglets est masqué si seul un onglet s’affiche.  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la fenêtre de l’onglet n’est pas affichée quand il n'est qu’un seul onglet visible ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Si le volet ne s’affiche pas, car qu’un seul onglet est ouvert, vous pouvez appeler cette méthode pour déterminer si le volet à onglets fonctionne correctement.  
  
##  <a name="removepane"></a>  CBaseTabbedPane::RemovePane  
 Supprime un volet dans le volet à onglets.  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out] *pBar*  
 Pointeur vers le volet à supprimer dans le volet à onglets.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le volet a été supprimé avec succès à partir du volet à onglets et si le volet à onglets est toujours valide. FALSE si le dernier volet a été supprimé à partir du volet à onglets et le volet à onglets est sur le point d’être détruit. Si la valeur de retour est FALSE, n’utilisez pas le volet à onglets plus.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour supprimer le volet spécifié par le *pBar* paramètre dans le volet à onglets.  
  
##  <a name="setautodestroy"></a>  CBaseTabbedPane::SetAutoDestroy  
 Détermine si la barre de contrôle à onglets est détruite automatiquement.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bAutoDestroy*  
 TRUE si le volet à onglets a été créé dynamiquement et vous ne contrôlez pas sa durée de vie ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Définir la destruction automatique mode True si vous créez un volet à onglets dynamiquement et si vous ne contrôlez pas sa durée de vie. Si destruction automatique mode a la valeur TRUE, le volet à onglets sera détruit automatiquement par l’infrastructure.  
  
##  <a name="showtab"></a>  CBaseTabbedPane::ShowTab  
 Affiche ou masque un onglet.  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pBar*  
 Un pointeur vers le volet pour afficher ou masquer.  
  
 [in] *bShow*  
 TRUE pour afficher le volet. FALSE pour masquer le volet.  
  
 [in] *bDelay*  
 TRUE pour différer l’ajustement de la disposition des onglets ; Sinon, FALSE.  
  
 [in] *bActivate*  
 TRUE si l’onglet l’onglet actif ; Sinon, FALSE.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’onglet a été soit affiché ou masqué avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous appelez cette méthode, un volet est affiché ou masqué, selon la valeur de la *bShow* paramètre. Si vous masquez un onglet, et il est le dernier onglet visible dans l’onglet de fenêtre sous-jacent, le volet à onglets est masqué. Si vous affichez un onglet lorsqu’il n’existait auparavant aucun onglet visible, le volet à onglets s’affiche.  
  
##  <a name="recalclayout"></a>  CBaseTabbedPane::RecalcLayout  
 Recalcule les informations de disposition pour le volet.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Notes  
 Si le volet est flottant, cette méthode notifie l’infrastructure pour redimensionner le volet de la taille actuelle de la mini-frame.  
  
 Si le volet est ancré, cette méthode ne fait rien.  
  
##  <a name="setautohidemode"></a>  CBaseTabbedPane::SetAutoHideMode  
 Définit le mode de masquage automatique pour les volets détachables dans le volet à onglets.  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bMode*  
 TRUE pour activer le mode de masquage automatique ; FALSE pour activer le mode d’ancrage standard.  
  
 [in] *dwAlignment*  
 Spécifie l’alignement du volet masquage automatique qui doit être créé. Pour obtenir la liste des valeurs possibles, consultez [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).  
  
 [in] [out] *pCurrAutoHideBar*  
 Pointeur vers la barre d’outils de masquage automatique en cours. Peut être NULL.  
  
 [in] *bUseTimer*  
 Spécifie s’il faut utiliser l’effet de masquage automatique lorsque l’utilisateur bascule le volet en mode de masquage automatique, ou masquer le volet immédiatement.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la barre d’outils de masquage automatique est créé lorsque vous passez au mode de masquage automatique, ou NULL si aucune barre d’outils n’est créé.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode lorsqu’un utilisateur choisit le bouton épingler pour basculer le volet à onglets au mode de masquage automatique ou en mode d’ancrage normal.  
  
 Mode de masquage automatique est défini pour chaque volet détachable dans le volet à onglets. Les volets qui sont non amovibles sont ignorés. Pour plus d’informations, consultez [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).  
  
 Appelez cette méthode pour basculer d’un volet à onglets pour le mode de masquage automatique par programmation. Le volet doit être ancré à la fenêtre frame principale ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) doit retourner un pointeur valide vers le [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)
