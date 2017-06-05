---
title: Classe de CPaneFrameWnd | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
dev_langs:
- C++
helpviewer_keywords:
- CPaneFrameWnd class
- Serialize method
- PreTranslateMessage method
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
caps.latest.revision: 28
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a8609643a9e64127af1d8035c496cedab4b1b1e9
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd (classe)
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Implémente une fenêtre mini-frame qui contient un volet. Le volet remplit la zone cliente de la fenêtre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPaneFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CPaneFrameWnd::AddPane](#addpane)|Ajoute un volet.|  
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Ajoute ou supprime un volet de la liste globale.|  
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|Ajuste la disposition de la fenêtre mini-frame.|  
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||  
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Calcule la taille des bordures d'une fenêtre mini-frame.|  
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcule le rectangle attendu d'une fenêtre ancrée.|  
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Détermine si le volet actif peut être ancré à un autre volet ou à une fenêtre frame.|  
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Détermine si la fenêtre mini-frame peut être ancrée à un volet.|  
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||  
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Convertit le volet en document à onglets.|  
|[CPaneFrameWnd::Create](#create)|Crée une fenêtre mini-frame et l'attache à l'objet `CPaneFrameWnd`.|  
|[CPaneFrameWnd::CreateEx](#createex)|Crée une fenêtre mini-frame et l'attache à l'objet `CPaneFrameWnd`.|  
|[CPaneFrameWnd::DockPane](#dockpane)|Ancre le volet.|  
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Recherche un volet à partir de l'ID de contrôle spécifié dans la liste globale des volets flottants.|  
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Recherche la fenêtre mini-frame contenant un point fourni par l'utilisateur.|  
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Retourne la hauteur de la légende de fenêtre mini-frame.|  
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Calcule le rectangle englobant d'une légende de fenêtre mini-frame.|  
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Retourne le texte de légende.|  
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||  
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Retourne le mode d'ancrage.|  
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Retourne le premier volet visible contenu dans une fenêtre mini-frame.|  
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||  
|[CPaneFrameWnd::GetPane](#getpane)|Retourne un volet contenu dans la fenêtre mini-frame.|  
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Retourne le nombre de volets contenus dans une fenêtre mini-frame.|  
|[CPaneFrameWnd::GetParent](#getparent)||  
|[CPaneFrameWnd::GetPinState](#getpinstate)||  
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||  
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Retourne le nombre de volets visibles contenus dans une fenêtre mini-frame.|  
|[CPaneFrameWnd::HitTest](#hittest)|Détermine la partie d'une fenêtre mini-frame qui se trouve à un point donné.|  
|[CPaneFrameWnd::IsCaptured](#iscaptured)||  
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||  
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Détermine si une fenêtre mini-frame doit être masquée.|  
|[CPaneFrameWnd::IsRollUp](#isrollup)|Détermine si une fenêtre mini-frame doit être affichée.|  
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Arrête le minuteur d'ancrage.|  
|[CPaneFrameWnd::LoadState](#loadstate)|Charge l'état du volet à partir du Registre.|  
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Détermine si l'ancrage est possible.|  
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Ancre la fenêtre mini-frame à sa dernière position.|  
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Arrête le minuteur d'affichage.|  
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Déplace la fenêtre mini-frame selon un décalage spécifié.|  
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Ajuste la disposition d'un volet contenu.|  
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Définit le minuteur d'affichage.|  
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Appelé par l'infrastructure quand un volet de la fenêtre mini-frame est masqué ou affiché.|  
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|Retourne un volet s'il contient un point fourni par l'utilisateur à l'intérieur d'une fenêtre mini-frame.|  
|[CPaneFrameWnd::Pin](#pin)||  
|`CPaneFrameWnd::PreTranslateMessage`|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour convertir des messages de fenêtre avant qu’ils soient distribués à le [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) fonctions de Windows.|  
|[CPaneFrameWnd::RedrawAll](#redrawall)|Redessine toutes les fenêtres mini-frame.|  
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Appelé par l'infrastructure pour supprimer les volets non valides.|  
|[CPaneFrameWnd::RemovePane](#removepane)|Supprime un volet de la fenêtre mini-frame.|  
|[CPaneFrameWnd::ReplacePane](#replacepane)|Remplace un volet par un autre.|  
|[CPaneFrameWnd::SaveState](#savestate)|Enregistre l'état du volet dans le Registre.|  
|`CPaneFrameWnd::Serialize`|Lit ou écrit cet objet dans une archive.|  
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Définit les boutons de légende.|  
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||  
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||  
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Définit le minuteur d'ancrage.|  
|[CPaneFrameWnd::SetDockState](#setdockstate)|Définit l'état d'ancrage.|  
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||  
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Appelé par l'infrastructure pour définir l'état de pré-ancrage.|  
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Ajuste une fenêtre mini-frame de sorte qu'elle ait une taille équivalente à celle d'un volet contenu.|  
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Détache un menu.|  
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||  
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Détermine si une fenêtre mini-frame doit être masquée ou affichée.|  
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Dessine les bordures d'une fenêtre mini-frame.|  
  
### <a name="data-members"></a>Membres de données  
  
|Nom|Description|  
|----------|-----------------|  
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Spécifie si la classe de fenêtre doit être inscrite avec le style de classe `CS_SAVEBITS`.|  
  
## <a name="remarks"></a>Remarques  
 L'infrastructure crée automatiquement un objet `CPaneFrameWnd` quand un volet passe de l'état ancré à l'état flottant.  
  
 Vous pouvez faire glisser une fenêtre mini-frame avec son contenu visible (ancrage immédiat) ou en utilisant un rectangle de glissement (ancrage standard). Le mode d'ancrage du volet conteneur du mini-frame détermine le comportement de glissement du mini-frame. Pour plus d’informations, consultez [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
 Une fenêtre mini-frame présente des boutons sur la légende en fonction du style du volet contenu. Si le volet peut être fermé ( [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), il affiche un bouton Fermer. Si le volet a la style `AFX_CBRS_AUTO_ROLLUP`, il affiche une épingle.  
  
 Si vous faites dériver une classe de `CPaneFrameWnd`, vous devez indiquer à l'infrastructure comment la créer. Créez la classe en substituant [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), ou définir le `CPane::m_pMiniFrameRTC` membre afin qu’il pointe vers les informations relatives à la classe runtime pour votre classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPaneFrameWnd`   
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxPaneFrameWnd.h  
  
##  <a name="addpane"></a>CPaneFrameWnd::AddPane  
 Ajoute un volet.  
  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWnd`  
 Volet à ajouter.  
  
##  <a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList  
 Ajoute ou supprime un volet de la liste globale.  
  
```  
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,  
    BOOL bAdd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWnd`  
 Le volet pour ajouter ou supprimer.  
  
 [in] `bAdd`  
 Si non nul, ajouter le volet. Si 0, supprimer le volet.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode a réussi ; sinon 0.  
  
##  <a name="adjustlayout"></a>CPaneFrameWnd::AdjustLayout  
 Ajuste la disposition de la fenêtre mini-frame.  
  
```  
virtual void AdjustLayout();
```  
  
##  <a name="adjustpaneframes"></a>CPaneFrameWnd::AdjustPaneFrames  

  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize  
 Calcule la taille de la bordure d’une fenêtre mini-frame.  
  
```  
virtual void CalcBorderSize(CRect& rectBorderSize) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `rectBorderSize`  
 Contient la taille, en pixels, de la bordure de la fenêtre mini-frame.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est appelée par l’infrastructure pour calculer la taille de la bordure d’une fenêtre mini-frame. La taille retournée dépend de si une fenêtre mini-frame contient une barre d’outils ou un [CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
##  <a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect  
 Calcule le rectangle attendu d'une fenêtre ancrée.  
  
```  
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndToDock`  
 Pointeur vers la fenêtre pour l’ancrer.  
  
 [in] `ptMouse`  
 L’emplacement de la souris.  
  
 [out] `rectResult`  
 Rectangle calculé.  
  
 [out] `bDrawTab`  
 Si `TRUE`, dessinez un onglet. Si `FALSE`, ne pas dessiner un onglet.  
  
 [out] `ppTargetBar`  
 Pointeur vers le volet cible.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode calcule le rectangle une fenêtre occuperait si un utilisateur a fait glisser la fenêtre vers le point spécifié par `ptMouse` et il il ancré.  
  
##  <a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached  
 Détermine si le volet actif peut être ancré à un autre volet ou à une fenêtre frame.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet peut être ancré à un autre volet ou une fenêtre frame ; dans le cas contraire `FALSE`.  
  
##  <a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane  
 Détermine si la fenêtre mini-frame peut être ancrée à un volet.  
  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDockingBar`  
 Un volet.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le mini-frame peut être ancré à `pDockingBar`; sinon, 0.  
  
##  <a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility  

  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument  
 Convertit le volet en document à onglets.  
  
```  
virtual void ConvertToTabbedDocument();
```  
  
##  <a name="create"></a>CPaneFrameWnd::Create  
 Crée une fenêtre mini-frame et l’attache à la [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) objet.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszWindowName`  
 Spécifie le texte à afficher dans la fenêtre mini-frame.  
  
 [in] `dwStyle`  
 Spécifie le style de fenêtre. Pour plus d’informations, consultez [Styles de fenêtre](../../mfc/reference/window-styles.md).  
  
 [in] `rect`  
 Spécifie la taille initiale et la position de la fenêtre mini-frame.  
  
 [in] [out]`pParentWnd`  
 Spécifie le frame parent de la fenêtre mini-frame. Cette valeur ne doit pas être `NULL`.  
  
 [in] [out]`pContext`  
 Spécifie le contexte défini par l’utilisateur.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fenêtre a été créée avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Une fenêtre mini-frame est créée en deux étapes. Tout d’abord, l’infrastructure crée un `CPaneFrameWnd` objet. Ensuite, il appelle `Create` pour créer la fenêtre de mini-frame Windows et l’attacher à la `CPaneFrameWnd` objet.  
  
##  <a name="createex"></a>CPaneFrameWnd::CreateEx  
 Crée une fenêtre mini-frame et l’attache à la [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) objet.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwStyleEx`  
 Spécifie le style de fenêtre étendus. Pour plus d’informations, consultez [Styles de fenêtre étendus](../../mfc/reference/extended-window-styles.md)  
  
 [in] `lpszWindowName`  
 Spécifie le texte à afficher dans la fenêtre mini-frame.  
  
 [in] `dwStyle`  
 Spécifie le style de fenêtre. Pour plus d’informations, consultez [Styles de fenêtre](../../mfc/reference/window-styles.md).  
  
 [in] `rect`  
 Spécifie la taille initiale et la position de la fenêtre mini-frame.  
  
 [in] [out]`pParentWnd`  
 Spécifie le frame parent de la fenêtre mini-frame. Cette valeur ne doit pas être `NULL`.  
  
 [in] [out]`pContext`  
 Spécifie le contexte défini par l’utilisateur.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fenêtre a été créée avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Une fenêtre mini-frame est créée en deux étapes. Tout d’abord, l’infrastructure crée un `CPaneFrameWnd` objet. Ensuite, il appelle `Create` pour créer la fenêtre de mini-frame Windows et l’attacher à la `CPaneFrameWnd` objet.  
  
##  <a name="dockpane"></a>CPaneFrameWnd::DockPane  
 Ancre le volet.  
  
```  
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `bWasDocked`  
 `TRUE`Si le volet est ancré déjà ; dans le cas contraire `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 Si l’opération a réussi, le `CDockablePane` que le volet est ancré ; sinon `NULL`.  
  
##  <a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID  
 Recherche un volet à partir de l'ID de contrôle spécifié dans la liste globale des volets flottants.  
  
```  
static CBasePane* FindFloatingPaneByID(UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nID`  
 Représente l’ID de contrôle du volet de recherche.  
  
### <a name="return-value"></a>Valeur de retour  
 Le volet avec l’ID du contrôle spécifié ; dans le cas contraire, `NULL`, si aucun volet ne possède l’ID du contrôle spécifié.  
  
##  <a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint  
 Recherche la fenêtre mini-frame qui contient le point spécifié.  
  
```  
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,  
    int nSensitivity,  
    CPaneFrameWnd* pFrameToExclude = NULL,  
    BOOL bFloatMultiOnly = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pt`  
 Le point, en coordonnées d’écran.  
  
 [in] `nSensitivity`  
 À cette taille, augmenter la zone de recherche de la fenêtre mini-frame. Une fenêtre mini-frame satisfait les critères de recherche si le point donné se trouve dans la zone accrue.  
  
 [in] `pFrameToExclude`  
 Spécifie une fenêtre mini-frame à exclure de la recherche.  
  
 [in] `bFloatMultiOnly`  
 Si `TRUE`, effectuer une recherche uniquement les fenêtres mini-frame qui ont le `CBRS_FLOAT_MULTI` style. Si `FALSE`, rechercher toutes les fenêtres mini-frame.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la fenêtre mini-frame qui contient `pt`; sinon `NULL`.  
  
##  <a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight  
 Retourne la hauteur de la légende de fenêtre mini-frame.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur, en pixels, de la fenêtre mini-frame.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour déterminer la hauteur d’une fenêtre mini-frame. Par défaut, la hauteur est définie sur `SM_CYSMCAPTION`. Pour plus d’informations, consultez [GetSystemMetrics fonction](http://msdn.microsoft.com/library/windows/desktop/ms724385).  
  
##  <a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect  
 Calcule le rectangle englobant d'une légende de fenêtre mini-frame.  
  
```  
virtual void GetCaptionRect(CRect& rectCaption) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `rectCaption`  
 Contient la taille et la position de la légende de fenêtre mini-frame, en coordonnées d’écran.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est appelée par l’infrastructure pour calculer le rectangle englobant d’une légende de fenêtre mini-frame.  
  
##  <a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText  
 Retourne le texte de légende.  
  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le texte de légende de la fenêtre mini-frame.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est appelée par l’infrastructure lors de l’affichage du texte de légende.  
  
##  <a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager  

  
```  
CDockingManager* GetDockingManager() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode  
 Retourne le mode d'ancrage.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le mode d’ancrage. Une des valeurs suivantes :  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
##  <a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane  
 Retourne le premier volet visible contenu dans une fenêtre mini-frame.  
  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le premier volet dans la fenêtre mini-frame, ou `NULL` si la fenêtre mini-frame ne contient aucun volets.  
  
##  <a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint  

  
```  
CPoint GetHotPoint() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getpane"></a>CPaneFrameWnd::GetPane  
 Retourne un volet contenu dans la fenêtre mini-frame.  
  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le volet de contenu dans le mini-frame, ou `NULL` si la fenêtre mini-frame ne contient aucun volets.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount  
 Retourne le nombre de volets contenus dans une fenêtre mini-frame.  
  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de volets dans la fenêtre mini-frame. Cette valeur peut être zéro.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getparent"></a>CPaneFrameWnd::GetParent  

  
```  
CWnd* GetParent();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getpinstate"></a>CPaneFrameWnd::GetPinState  

  
```  
BOOL GetPinState() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect  

  
```  
CRect GetRecentFloatingRect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount  
 Retourne le nombre de volets visibles contenus dans une fenêtre mini-frame.  
  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de volets visibles.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="hittest"></a>CPaneFrameWnd::HitTest  
 Détermine la partie d'une fenêtre mini-frame qui se trouve à un point donné.  
  
```  
virtual LRESULT HitTest(
    CPoint point,  
    BOOL bDetectCaption);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Point à tester.  
  
 [in] `bDetectCaption`  
 Si `TRUE`, vérifiez le point par rapport à la légende. Si `FALSE`, ignorer la légende.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs suivantes :  
  
|Valeur|Signification|  
|-----------|-------------|  
|`HTNOWHERE`|Le point est en dehors de la fenêtre mini-frame.|  
|`HTCLIENT`|Le point est dans la zone cliente.|  
|`HTCAPTION`|Le point est sur la légende.|  
|`HTTOP`|Le point est en haut.|  
|`HTTOPLEFT`|Le point est en haut à gauche.|  
|`HTTOPRIGHT`|Le point est en haut à droite.|  
|`HTLEFT`|Le point se trouve à gauche.|  
|`HTRIGHT`|Le point se trouve à droite.|  
|`HTBOTTOM`|Le point est bas.|  
|`HTBOTTOMLEFT`|Le point est en bas à gauche.|  
|`HTBOTTOMRIGHT`|Le point est en bas à droite.|  
  
##  <a name="iscaptured"></a>CPaneFrameWnd::IsCaptured  

  
```  
BOOL IsCaptured() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow  

  
```  
BOOL IsDelayShow() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="isrolldown"></a>CPaneFrameWnd::IsRollDown  
 Détermine si une fenêtre mini-frame doit être masquée.  
  
```  
virtual BOOL IsRollDown() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fenêtre mini-frame doit être restaurée dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est appelée par l’infrastructure pour déterminer si une fenêtre mini-frame doit être appliquée. La fonctionnalité de cumul/répercussion est activée pour une fenêtre mini-frame si elle contient au moins un volet qui a le `AFX_CBRS_AUTO_ROLLUP` indicateur. Cet indicateur est défini lors de la création d’un volet. Pour plus d’informations, consultez [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 Par défaut, l’infrastructure vérifie si le pointeur de la souris est dans le rectangle englobant de la fenêtre mini-frame afin de déterminer si la fenêtre doit être appliquée. Vous pouvez remplacer ce comportement dans une classe dérivée.  
  
##  <a name="isrollup"></a>CPaneFrameWnd::IsRollUp  
 Détermine si une fenêtre mini-frame doit être affichée.  
  
```  
virtual BOOL IsRollUp() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fenêtre mini-frame doit être restaurée dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par l’infrastructure pour déterminer si une fenêtre mini-frame doit être reportée. La fonctionnalité de cumul/répercussion est activée pour une fenêtre mini-frame si elle contient au moins un volet qui a le `AFX_CBRS_AUTO_ROLLUP` indicateur. Cet indicateur est défini lors de la création d’un volet. Pour plus d’informations, consultez [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 Par défaut, l’infrastructure vérifie si le pointeur de la souris est dans le rectangle englobant de la fenêtre mini-frame pour déterminer si la fenêtre doit être cumulée. Vous pouvez remplacer ce comportement dans une classe dérivée.  
  
##  <a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer  
 Arrête le minuteur d'ancrage.  
  
```  
void KillDockingTimer();
```  
  
##  <a name="loadstate"></a>CPaneFrameWnd::LoadState  
 Charge l'état du volet à partir du Registre.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszProfileName`  
 Nom du profil.  
  
 [in] `uiID`  
 L’ID du volet.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’état du volet a été chargée avec succès ; dans le cas contraire `FALSE`.  
  
##  <a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits  
 Spécifie s’il faut enregistrer la classe de fenêtre qui a le `CS_SAVEBITS` style de classe.  
  
```  
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;  
```  
  
### <a name="remarks"></a>Notes  
 Affecter à ce membre statique `TRUE` pour inscrire la classe de fenêtre mini-frame qui a le `CS_SAVEBITS` style. Cela permet de réduire le scintillement lorsqu’un utilisateur fait glisser la fenêtre mini-frame.  
  
##  <a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock  
 Détermine si l'ancrage est possible.  
  
```  
virtual BOOL OnBeforeDock();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la station d’accueil est possible ; dans le cas contraire, `FALSE`.  
  
##  <a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState  
 Détermine si une fenêtre mini-frame doit être masquée ou affichée.  
  
```  
virtual void OnCheckRollState();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par l’infrastructure pour déterminer si une fenêtre mini-frame doit être déployée vers le haut ou vers le bas.  
  
 Par défaut, le framework appelle [CPaneFrameWnd::IsRollUp](#isrollup) et [CPaneFrameWnd::IsRollDown](#isrolldown) et simplement agrandit ou restaure la fenêtre mini-frame. Vous pouvez substituer cette méthode dans une classe dérivée à utiliser un autre effet visuel.  
  
##  <a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos  
 Ancre la fenêtre mini-frame à sa dernière position.  
  
```  
virtual void OnDockToRecentPos();
```  
  
##  <a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder  
 Dessine les bordures d'une fenêtre mini-frame.  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Le contexte de périphérique utilisé pour dessiner la bordure.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est appelée par l’infrastructure pour dessiner les bordures de la fenêtre mini-frame.  
  
##  <a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer  
 Arrête le minuteur d'affichage.  
  
```  
virtual void OnKillRollUpTimer();
```  
  
##  <a name="onmovepane"></a>CPaneFrameWnd::OnMovePane  
 Déplace la fenêtre mini-frame selon un décalage spécifié.  
  
```  
virtual void OnMovePane(
    CPane* pBar,  
    CPoint ptOffset);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pBar`  
 Pointeur vers un volet (ignoré).  
  
 [in] `ptOffset`  
 Le décalage de déplacement du volet.  
  
##  <a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout  
 Ajuste la disposition d’un volet dans une fenêtre mini-frame.  
  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>Remarques  
 L’infrastructure appelle cette méthode lorsqu’il doit ajuster la disposition d’un volet dans une fenêtre mini-frame.  
  
 Par défaut, le volet est positionné pour couvrir la zone cliente complète de la fenêtre mini-frame.  
  
##  <a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer  
 Définit le minuteur d'affichage.  
  
```  
virtual void OnSetRollUpTimer();
```  
  
##  <a name="onshowpane"></a>CPaneFrameWnd::OnShowPane  
 Appelé par l'infrastructure quand un volet de la fenêtre mini-frame est masqué ou affiché.  
  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pBar`  
 Le volet qui est affiché ou masqué.  
  
 [in] `bShow`  
 `TRUE`Si le volet est affiché ; `FALSE` si le volet est masqué.  
  
### <a name="remarks"></a>Remarques  
 Appelé par l’infrastructure lorsqu’un volet dans la fenêtre mini-frame est affiché ou masqué. L'implémentation par défaut n'exécute aucune opération.  
  
##  <a name="pin"></a>CPaneFrameWnd::Pin  

  
```  
void Pin(BOOL bPin = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bPin`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="panefrompoint"></a>CPaneFrameWnd::PaneFromPoint  
 Retourne un volet s'il contient un point fourni par l'utilisateur à l'intérieur d'une fenêtre mini-frame.  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Le point sur lequel l’utilisateur a cliqué, en coordonnées d’écran.  
  
 [in] `nSensitivity`  
 Ce paramètre n'est pas utilisé.  
  
 [in] `bCheckVisibility`  
 `TRUE`Pour spécifier que les volets visibles uniquement doivent être retournés ; dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 Le volet sur lequel l’utilisateur a cliqué, ou `NULL` si aucun volet n’existe à cet emplacement.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour obtenir un volet qui contient le point donné.  
  
##  <a name="redrawall"></a>CPaneFrameWnd::RedrawAll  
 Redessine toutes les fenêtres mini-frame.  
  
```  
static void RedrawAll();
```  
  
### <a name="remarks"></a>Remarques  
 Cette méthode met à jour toutes les fenêtres mini-frame en appelant [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) pour chaque fenêtre.  
  
##  <a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes  
 Appelé par l'infrastructure pour supprimer les volets non valides.  
  
```  
virtual void RemoveNonValidPanes();
```  
  
##  <a name="removepane"></a>CPaneFrameWnd::RemovePane  
 Supprime un volet de la fenêtre mini-frame.  
  
```  
virtual void RemovePane(
    CBasePane* pWnd,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWnd`  
 Pointeur vers le volet à supprimer.  
  
 [in] `bDestroy`  
 Spécifie ce qui arrive à la fenêtre mini-frame. Si `bDestroy` est `TRUE`, cette méthode détruit la fenêtre mini-frame immédiatement. S’il est `FALSE`, cette méthode détruit la fenêtre mini-frame après un certain délai.  
  
 [in] `bNoDelayedDestroy`  
 Si `TRUE`, différées destruction est désactivée. Si `FALSE`, différées destruction est activée.  
  
### <a name="remarks"></a>Remarques  
 L’infrastructure peut détruire des fenêtres mini-frame immédiatement ou après un certain délai. Si vous voulez retarder la destruction des fenêtres mini-frame, transmettez `FALSE` dans le `bNoDelayedDestroy` paramètre. Destruction différée se produit lorsque le framework traite la `AFX_WM_CHECKEMPTYMINIFRAME` message.  
  
##  <a name="replacepane"></a>CPaneFrameWnd::ReplacePane  
 Remplace un volet par un autre.  
  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pBarOrg`  
 Pointeur vers le volet d’origine.  
  
 [in] `pBarReplaceWith`  
 Pointeur vers le volet qui remplace le volet d’origine.  
  
##  <a name="savestate"></a>CPaneFrameWnd::SaveState  
 Enregistre l'état du volet dans le Registre.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszProfileName`  
 Nom du profil.  
  
 [in] `uiID`  
 L’ID du volet.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si l’état du volet a été enregistré avec succès ; dans le cas contraire `FALSE`.  
  
##  <a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons  
 Définit les boutons de légende.  
  
```  
virtual void SetCaptionButtons(DWORD dwButtons);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwButtons`  
 Combinaison de bits OR des valeurs suivantes :  
  
- `AFX_CAPTION_BTN_CLOSE`  
  
- `AFX_CAPTION_BTN_PIN`  
  
- `AFX_CAPTION_BTN_MENU`  
  
- `AFX_CAPTION_BTN_CUSTOMIZE`  
  
##  <a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow  

  
```  
void SetDelayShow(BOOL bDelayShow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bDelayShow`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager  

  
```  
void SetDockingManager(CDockingManager* pManager);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pManager`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer  
 Définit le minuteur d'ancrage.  
  
```  
void SetDockingTimer(UINT nTimeOut);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nTimeOut`  
 Valeur de délai d’attente en millisecondes.  
  
##  <a name="setdockstate"></a>CPaneFrameWnd::SetDockState  
 Définit l'état d'ancrage.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDockManager`  
 Pointeur vers un gestionnaire d’ancrage.  
  
##  <a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint  

  
```  
void SetHotPoint(CPoint& ptNew);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `ptNew`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState  
 Appelé par l'infrastructure pour définir l'état de pré-ancrage.  
  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `preDockState`  
 Valeurs possibles :  
  
- `PDS_NOTHING`,  
  
- `PDS_DOCK_REGULAR`,  
  
- `PDS_DOCK_TO_TAB`  
  
 [in] `pBarToDock`  
 Pointeur vers le volet pour ancrer.  
  
 [in] `dockMethod`  
 La méthode d’ancrage. (Ce paramètre est ignoré.)  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fenêtre mini-frame est flottant ; `FALSE` si elle est ancrée.  
  
##  <a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent  
 Ajuste la taille d’une fenêtre mini-frame afin qu’elle soit équivalente à un volet de contenu.  
  
```  
virtual void SizeToContent();
```  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour ajuster la taille d’une fenêtre mini-frame à la taille d’un volet de contenu.  
  
##  <a name="starttearoff"></a>CPaneFrameWnd::StartTearOff  
 Détache un menu.  
  
```  
BOOL StartTearOff(CMFCPopu* pMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pMenu`  
 Pointeur vers un menu.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` si la méthode a réussi ; sinon, `FALSE`.  
  
##  <a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo  

  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pBar`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo  

  
```  
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,  
    CDockablePane* pTabbedBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDockingBar`  
 [in] `pTabbedBar`  
  
### <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)

