---
title: Classe de CDockablePane | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePane
- AFXDOCKABLEPANE/CDockablePane
- AFXDOCKABLEPANE/CDockablePane::CDockablePane
- AFXDOCKABLEPANE/CDockablePane::AttachToTabWnd
- AFXDOCKABLEPANE/CDockablePane::CalcFixedLayout
- AFXDOCKABLEPANE/CDockablePane::CanAcceptMiniFrame
- AFXDOCKABLEPANE/CDockablePane::CanAcceptPane
- AFXDOCKABLEPANE/CDockablePane::CanAutoHide
- AFXDOCKABLEPANE/CDockablePane::CanBeAttached
- AFXDOCKABLEPANE/CDockablePane::ConvertToTabbedDocument
- AFXDOCKABLEPANE/CDockablePane::CopyState
- AFXDOCKABLEPANE/CDockablePane::Create
- AFXDOCKABLEPANE/CDockablePane::CreateDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::CreateEx
- AFXDOCKABLEPANE/CDockablePane::CreateTabbedPane
- AFXDOCKABLEPANE/CDockablePane::DockPaneContainer
- AFXDOCKABLEPANE/CDockablePane::DockPaneStandard
- AFXDOCKABLEPANE/CDockablePane::DockToRecentPos
- AFXDOCKABLEPANE/CDockablePane::DockToWindow
- AFXDOCKABLEPANE/CDockablePane::EnableAutohideAll
- AFXDOCKABLEPANE/CDockablePane::EnableGripper
- AFXDOCKABLEPANE/CDockablePane::GetAHRestoredRect
- AFXDOCKABLEPANE/CDockablePane::GetAHSlideMode
- AFXDOCKABLEPANE/CDockablePane::GetCaptionHeight
- AFXDOCKABLEPANE/CDockablePane::GetDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::GetDockingStatus
- AFXDOCKABLEPANE/CDockablePane::GetDragSensitivity
- AFXDOCKABLEPANE/CDockablePane::GetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::GetTabArea
- AFXDOCKABLEPANE/CDockablePane::GetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::HasAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::HitTest
- AFXDOCKABLEPANE/CDockablePane::IsAutohideAllEnabled
- AFXDOCKABLEPANE/CDockablePane::IsAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsDocked
- AFXDOCKABLEPANE/CDockablePane::IsHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsInFloatingMultiPaneFrameWnd
- AFXDOCKABLEPANE/CDockablePane::IsResizable
- AFXDOCKABLEPANE/CDockablePane::IsTabLocationBottom
- AFXDOCKABLEPANE/CDockablePane::IsTracked
- AFXDOCKABLEPANE/CDockablePane::IsVisible
- AFXDOCKABLEPANE/CDockablePane::OnAfterChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnAfterDockFromMiniFrame
- AFXDOCKABLEPANE/CDockablePane::OnBeforeChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnBeforeFloat
- AFXDOCKABLEPANE/CDockablePane::RemoveFromDefaultPaneDividier
- AFXDOCKABLEPANE/CDockablePane::ReplacePane
- AFXDOCKABLEPANE/CDockablePane::RestoreDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideParents
- AFXDOCKABLEPANE/CDockablePane::SetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::SetRestoredDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::ShowPane
- AFXDOCKABLEPANE/CDockablePane::Slide
- AFXDOCKABLEPANE/CDockablePane::ToggleAutoHide
- AFXDOCKABLEPANE/CDockablePane::UndockPane
- AFXDOCKABLEPANE/CDockablePane::CheckAutoHideCondition
- AFXDOCKABLEPANE/CDockablePane::CheckStopSlideCondition
- AFXDOCKABLEPANE/CDockablePane::DrawCaption
- AFXDOCKABLEPANE/CDockablePane::OnPressButtons
- AFXDOCKABLEPANE/CDockablePane::OnSlide
- AFXDOCKABLEPANE/CDockablePane::m_bDisableAnimation
- AFXDOCKABLEPANE/CDockablePane::m_bHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::m_nSlideSteps
dev_langs:
- C++
helpviewer_keywords:
- CDockablePane class
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dea1f1ce66c0e9bedbe83109ab62055a4af2ebce
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="cdockablepane-class"></a>CDockablePane Class
Implémente un volet qui peut être ancré dans un site d'ancrage ou être inclus dans un volet à onglets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDockablePane : public CPane  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDockablePane::CDockablePane](#cdockablepane)|Construit et initialise un objet `CDockablePane`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDockablePane::AttachToTabWnd](#attachtotabwnd)|Attache un volet à un autre volet. Cela crée un volet à onglets.|  
|[CDockablePane::CalcFixedLayout](#calcfixedlayout)|Retourne la taille du rectangle de volet.|  
|[CDockablePane::CanAcceptMiniFrame](#canacceptminiframe)|Détermine si les mini frame spécifié peut être ancré dans le volet.|  
|[CDockablePane::CanAcceptPane](#canacceptpane)|Détermine si un autre volet peut être ancré dans le volet en cours.|  
|[CDockablePane::CanAutoHide](#canautohide)|Détermine si le volet prend en charge le mode de masquage automatique. (Substitue [CBasePane::CanAutoHide](../../mfc/reference/cbasepane-class.md#canautohide).)|  
|[CDockablePane::CanBeAttached](#canbeattached)|Détermine si le volet actif peut être ancré à un autre volet.|  
|[CDockablePane::ConvertToTabbedDocument](#converttotabbeddocument)|Convertit un ou plusieurs volets ancrables documents MDI avec onglets.|  
|[CDockablePane::CopyState](#copystate)|Copie de l’état d’un volet Ancrable.|  
|[CDockablePane::Create](#create)|Crée le contrôle Windows et l’attache à le `CDockablePane` objet.|  
|[CDockablePane::CreateDefaultPaneDivider](#createdefaultpanedivider)|Crée un séparateur de valeur par défaut pour le volet comme elle est en cours ancrée à une fenêtre frame.|  
|[CDockablePane::CreateEx](#createex)|Crée le contrôle Windows et l’attache à le `CDockablePane` objet.|  
|[CDockablePane::CreateTabbedPane](#createtabbedpane)|Crée un volet à onglets dans le volet actif.|  
|[CDockablePane::DockPaneContainer](#dockpanecontainer)|Ancre un conteneur dans le volet.|  
|[CDockablePane::DockPaneStandard](#dockpanestandard)|Ancre un volet à l’aide de plan de la station d’accueil (standard).|  
|`CDockablePane::DockToFrameWindow`|Utilisé en interne. Pour ancrer un volet, utilisez [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) ou [CDockablePane::DockToWindow](#docktowindow).|  
|[CDockablePane::DockToRecentPos](#docktorecentpos)|Ancre un volet à sa position d’ancrage récente stockée.|  
|[CDockablePane::DockToWindow](#docktowindow)|Ancre un volet d’ancrage à un autre volet d’ancrage.|  
|[CDockablePane::EnableAutohideAll](#enableautohideall)|Active ou désactive le mode de masquage automatique pour ce volet, ainsi que d’autres volets dans le conteneur.|  
|[CDockablePane::EnableGripper](#enablegripper)|Affiche ou masque la légende (barre de redimensionnement).|  
|[CDockablePane::GetAHRestoredRect](#getahrestoredrect)|Spécifie la position du volet quand il est visible en mode de masquage automatique.|  
|[CDockablePane::GetAHSlideMode](#getahslidemode)|Récupère le mode de diapositive masquage automatique pour le volet.|  
|`CDockablePane::GetAutoHideButton`|Utilisé en interne.|  
|`CDockablePane::GetAutoHideToolBar`|Utilisé en interne.|  
|[CDockablePane::GetCaptionHeight](#getcaptionheight)|Retourne la hauteur de la légende en cours.|  
|[CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)|Retourne le diviseur de volet par défaut pour le conteneur du volet.|  
|[CDockablePane::GetDockingStatus](#getdockingstatus)|Détermine la possibilité d’un volet ancré selon l’emplacement du pointeur fourni.|  
|[CDockablePane::GetDragSensitivity](#getdragsensitivity)|Retourne la sensibilité de glissement d’un volet d’ancrage.|  
|[CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)|Récupère le pourcentage d’espace occupé par un volet dans son conteneur.|  
|[CDockablePane::GetTabArea](#gettabarea)|Récupère la zone des onglets du volet.|  
|[CDockablePane::GetTabbedPaneRTC](#gettabbedpanertc)|Retourne les informations de classe d’exécution sur une fenêtre avec onglets qui est créée lorsqu’un autre volet est ancré dans le volet en cours.|  
|[CDockablePane::HasAutoHideMode](#hasautohidemode)|Spécifie si un volet d’ancrage peut être basculé en mode de masquage automatique.|  
|[CDockablePane::HitTest](#hittest)|Spécifie l’emplacement spécifique dans un volet sur lequel l’utilisateur clique sur la souris.|  
|`CDockablePane::IsAccessibilityCompatible`|Utilisé en interne.|  
|[CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)|Indique si le volet d’ancrage et tous les autres volets dans le conteneur peuvent être placés en mode de masquage automatique.|  
|[CDockablePane::IsAutoHideMode](#isautohidemode)|Détermine si un volet est en mode de masquage automatique.|  
|`CDockablePane::IsChangeState`|Utilisé en interne.|  
|[CDockablePane::IsDocked](#isdocked)|Détermine si le volet actif est ancré.|  
|[CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode)|Détermine le comportement d’un volet qui est en mode de masquage automatique ou s’il est indiqué (masqué) en appelant `ShowPane`.|  
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Spécifie si le volet est dans une fenêtre frame de plusieurs volets.|  
|[CDockablePane::IsResizable](#isresizable)|Spécifie si le volet peut être redimensionnée.|  
|[CDockablePane::IsTabLocationBottom](#istablocationbottom)|Spécifie si les onglets sont situés en haut ou en bas du volet.|  
|[CDockablePane::IsTracked](#istracked)|Spécifie si un volet est déplacé par l’utilisateur.|  
|[CDockablePane::IsVisible](#isvisible)|Détermine si le volet actif est visible.|  
|[CDockablePane::LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917)|Utilisé en interne.|  
|[CDockablePane::OnAfterChangeParent](#onafterchangeparent)|Appelé par l’infrastructure lorsque le parent d’un volet a été modifiée. (Substitue [CPane::OnAfterChangeParent](../../mfc/reference/cpane-class.md#onafterchangeparent).)|  
|[CDockablePane::OnAfterDockFromMiniFrame](#onafterdockfromminiframe)|Appelé par l’infrastructure lorsqu’une barre d’ancrage flottante est ancré à une fenêtre frame.|  
|[CDockablePane::OnBeforeChangeParent](#onbeforechangeparent)|Appelé par l’infrastructure lorsque le parent du volet est sur le point de changer. (Substitue [CPane::OnBeforeChangeParent](../../mfc/reference/cpane-class.md#onbeforechangeparent).)|  
|[CDockablePane::OnBeforeFloat](#onbeforefloat)|Appelé par l’infrastructure lorsqu’un volet est sur le type float. (Substitue [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CDockablePane::RemoveFromDefaultPaneDividier](#removefromdefaultpanedividier)|L’infrastructure appelle cette méthode lorsqu’un volet est en cours flottant.|  
|[CDockablePane::ReplacePane](#replacepane)|Remplace le volet volet spécifié.|  
|[CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider)|Le framework appelle cette méthode comme un volet est désérialisé afin de restaurer le diviseur de volet par défaut.|  
|`CDockablePane::SaveState`|Utilisé en interne.|  
|`CDockablePane::Serialize`|Sérialise le volet. (Substitue `CBasePane::Serialize`.)|  
|[CDockablePane::SetAutoHideMode](#setautohidemode)|Bascule le volet d’ancrage entre visible et le mode de masquage automatique.|  
|[CDockablePane::SetAutoHideParents](#setautohideparents)|Définit le bouton Masquer automatiquement et la barre d’outils de masquage automatique pour le volet.|  
|`CDockablePane::SetDefaultPaneDivider`|Utilisé en interne.|  
|[CDockablePane::SetLastPercentInPaneContainer](#setlastpercentinpanecontainer)|Définit le pourcentage d’espace occupé par un volet dans son conteneur.|  
|`CDockablePane::SetResizeMode`|Utilisé en interne.|  
|[CDockablePane::SetRestoredDefaultPaneDivider](#setrestoreddefaultpanedivider)|Définit le diviseur de volet par défaut.|  
|[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)|Définit les informations de classe d’exécution d’une fenêtre à onglets qui est créée lorsque deux volets d’ancrage ensemble.|  
|[CDockablePane::ShowPane](#showpane)|Affiche ou masque un volet.|  
|[CDockablePane::Slide](#slide)|Affiche ou masque un volet avec une animation décalée qui affiche uniquement lorsque le volet est en mode de masquage automatique.|  
|[CDockablePane::ToggleAutoHide](#toggleautohide)|Mode de masquage automatique bascule. (Substitue [CPane::ToggleAutoHide](../../mfc/reference/cpane-class.md#toggleautohide) .)|  
|[CDockablePane::UndockPane](#undockpane)|Détache un volet à partir d’un conteneur de fenêtre mini-frame ou la fenêtre frame principale.|  
|`CDockablePane::UnSetAutoHideMode`|Utilisé en interne. Pour définir le mode de masquage automatique, utilisez [CDockablePane::SetAutoHideMode](#setautohidemode)|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CDockablePane::CheckAutoHideCondition](#checkautohidecondition)|Détermine si le volet d’ancrage est masqué (en mode de masquage automatique).|  
|[CDockablePane::CheckStopSlideCondition](#checkstopslidecondition)|Détermine quand un volet d’ancrage masquage automatique doit s’arrêter coulissant.|  
|[CDockablePane::DrawCaption](#drawcaption)|Dessine la légende volet d’ancrage (barre de redimensionnement).|  
|[CDockablePane::OnPressButtons](#onpressbuttons)|Appelé lorsque l’utilisateur appuie sur un bouton de légende autres que les `AFX_HTCLOSE` et `AFX_HTMAXBUTTON` boutons.|  
|[CDockablePane::OnSlide](#onslide)|Appelé par l’infrastructure pour afficher l’effet de masquage automatique lorsque le volet est affiché ou masqué.|  
  
### <a name="data-members"></a>Membres de données  
  
|Nom|Description|  
|----------|-----------------|  
|[CDockablePane::m_bDisableAnimation](#m_bdisableanimation)|Indique si l’animation masquer du volet « dockable » est désactivée.|  
|[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)|Détermine le comportement du volet lorsque le volet est en mode de masquage automatique.|  
|[CDockablePane::m_nSlideSteps](#m_nslidesteps)|Spécifie la vitesse d’animation du volet lorsqu’il est affiché ou masqué en mode de masquage automatique.|  
  
## <a name="remarks"></a>Remarques  
 `CDockablePane`implémente les fonctionnalités suivantes :  
  
-   Un volet d’ancrage dans une fenêtre frame principale.  
  
-   Passage d’un volet en mode de masquage automatique.  
  
-   Attachement d’un volet à une fenêtre avec onglets.  
  
-   Flottant un volet dans une fenêtre mini-frame.  
  
-   Un volet d’ancrage à un autre volet est flottant dans une fenêtre mini-frame.  
  
-   Le redimensionnement d’un volet.  
  
-   Chargement et enregistrement de l’état d’un volet d’ancrage.  
  
    > [!NOTE]
    >  Les informations d’état sont enregistrées dans le Registre Windows.  
  
-   Création d’un volet avec ou sans légende. La légende peut avoir une étiquette de texte et il peut être rempli avec un dégradé de couleur.  
  
-   En faisant glisser un volet lors de l’affichage du contenu du volet  
  
-   Faites glisser un volet lors de l’affichage d’un rectangle de glissement.  
  
 Pour utiliser un volet d’ancrage dans votre application, dérivez votre classe de volet de la `CDockablePane` classe. Soit incorporer l’objet dérivé dans l’objet de fenêtre frame principale ou dans un objet de fenêtre qui contrôle l’instance du volet. Puis appelez le [CDockablePane::Create](#create) (méthode) ou [CDockablePane::CreateEx](#createex) méthode lorsque vous traitez le `WM_CREATE` message dans la fenêtre frame principale. Enfin, définissez l’objet de volet en appelant [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking), [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane), ou [CDockablePane::AttachToTabWnd](#attachtotabwnd).  
  
## <a name="customization-tips"></a>Conseils de personnalisation  
 Les conseils suivants s’appliquent aux `CDockablePane` objets :  
  
-   Si vous appelez [CDockablePane::AttachToTabWnd](#attachtotabwnd) pour deux volets ancrables, non à onglets, un pointeur vers une fenêtre à onglets sera retourné dans le `ppTabbedControlBar` paramètre. Vous pouvez continuer à ajouter des onglets dans la fenêtre à onglets à l’aide de ce paramètre.  
  
-   Le type de volet à onglets qui est créé par [CDockablePane::AttachToTabWnd](#attachtotabwnd) est déterminée par le `CDockablePane` de l’objet dans le `pTabControlBarAttachTo` paramètre. Vous pouvez appeler [CDockablePane::SetTabbedPaneRTC](#settabbedpanertc) pour définir le type de volet à onglets qui le `CDockablePane` va créer. Le type par défaut est déterminé par le `dwTabbedStyle` de [CDockablePane::Create](#create) lorsque vous créez le `CDockablePane`. Si `dwTabbedStyle` est le type par défaut est de AFX_CBRS_OUTLOOK_TABS [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md); si `dwTabbedStyle` est le type par défaut est de AFX_CBRS_REGULAR_TABS [CTabbedPane classe](../../mfc/reference/ctabbedpane-class.md).  
  
-   Si vous souhaitez ancrer un volet ancrable vers un autre, appelez le [CDockablePane::DockToWindow](#docktowindow) (méthode). Le volet d’origine doit être ancré dans un endroit avant d’appeler cette méthode.  
  
-   La variable membre [CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode) contrôles de comportement des volets ancrables dans automatique masquer en mode lorsque vous appelez [CDockablePane::ShowPane](#showpane). Si cette variable membre est définie sur `TRUE`, volets ancrables et leurs boutons de masquage automatique seront masquées. Sinon, ils seront des diapositives et l’extraction.  
  
-   Vous pouvez désactiver l’animation masquer en définissant le [CDockablePane::m_bDisableAnimation](#m_bdisableanimation) variable de membre pour `TRUE`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer un `CDockablePane` à l’aide de différentes méthodes dans la `CDockablePane` classe. L’exemple illustre comment faire pour activer la fonction Masquer automatiquement toutes les fonctionnalités du volet « dockable », la légende ou la barre de redimensionnement, activer le mode de masquage automatique, afficher le volet et animer un volet en mode de masquage automatique. Cet extrait de code fait partie de la [exemple de Visual Studio démonstration](../../visual-cpp-samples.md).  
  
 [!code-cpp[27 NVC_MFC_VisualStudioDemo](../../mfc/codesnippet/cpp/cdockablepane-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo&#28;](../../mfc/codesnippet/cpp/cdockablepane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxDockablePane.h  
  
##  <a name="attachtotabwnd"></a>CDockablePane::AttachToTabWnd  
 Attache le volet actif vers un volet cible, création d’un volet à onglets.  
  
```  
virtual CDockablePane* AttachToTabWnd(
    CDockablePane* pTabControlBarAttachTo,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bSetActive= TRUE,  
    CDockablePane** ppTabbedControlBar = NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out]`pTabControlBarAttachTo`  
 Spécifie le volet cible que le volet actif s’attache à. Le volet cible doit être un volet Ancrable.  
  
 [in] `dockMethod`  
 Spécifie la méthode d’ancrage.  
  
 [in] `bSetActive`  
 `TRUE`Pour activer le volet à onglets après l’opération d’attachement ; dans le cas contraire, `FALSE`.  
  
 [out] `ppTabbedControlBar`  
 Contient le volet à onglets qui résulte de l’opération d’attachement.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le volet actif, si elle n’est pas un volet à onglets. Sinon, un pointeur vers le volet à onglets qui résulte de l’opération d’attachement. La valeur de retour est `NULL` si le volet actif ne peut pas être joint, ou si une erreur se produit.  
  
### <a name="remarks"></a>Remarques  
 Lorsqu’un volet ancrable est joint à un autre volet, à l’aide de cette méthode, les événements suivants se produisent :  
  
1.  Le framework vérifie si le volet cible `pTabControlBarAttachTo` ordinaire d’accueil volet ou si elle est dérivée de [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md).  
  
2.  Si le volet cible est un volet à onglets, le framework ajoute le volet actif dans un onglet.  
  
3.  Si le volet cible est un volet d’ancrage standard, l’infrastructure crée un volet à onglets.  
  
    -   Le framework appelle `pTabControlBarAttachTo->CreateTabbedPane`. Le style du nouveau volet à onglets dépend de le `m_pTabbedControlBarRTC` membre. Par défaut, ce membre est défini à la classe d’exécution de [CTabbedPane](../../mfc/reference/ctabbedpane-class.md). Si vous passez le `AFX_CBRS_OUTLOOK_TABS` style comme la `dwTabbedStyle` paramètre à la [CDockablePane::Create](#create) méthode, l’objet de classe d’exécution est définie sur la classe d’exécution de [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md). Vous pouvez modifier ce membre à tout moment pour modifier le style du nouveau volet.  
  
    -   Lorsque cette méthode crée un volet à onglets, le framework remplace le pointeur `pTabControlBarAttachTo` (si le volet est ancrés ou flottants dans une fenêtre mini-frame-multiple) avec un pointeur vers le nouveau volet à onglets.  
  
    -   Le framework ajoute le `pTabControlBarAttachTo` volet vers le volet à onglets, comme le premier onglet. Le framework ajoute ensuite le volet actif en tant que deuxième onglet.  
  
4.  Si le volet actif est dérivé de `CBaseTabbedPane`, tous ses onglets sont déplacés vers `pTabControlBarAttachTo` et le volet actif est détruit. Par conséquent, soyez prudent lorsque vous appelez cette méthode, car un pointeur vers le volet actif peut être non valide lorsque la méthode retourne.  
  
 Si vous attachez un volet à l’autre lors de la création d’une mise en page d’accueil, `dockMethod` à `DM_SHOW`.  
  
 Vous devez s’ancrer le premier volet avant de joindre un autre volet à elle.  
  
##  <a name="calcfixedlayout"></a>CDockablePane::CalcFixedLayout  
 Retourne la taille du rectangle de volet.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bStretch`  
 Non utilisé.  
  
 [in] `bHorz`  
 Non utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CSize` objet qui contient la taille du rectangle de volet.  
  
##  <a name="canacceptminiframe"></a>CDockablePane::CanAcceptMiniFrame  
 Détermine si le mini-frame spécifié peut être ancré dans le volet.  
  
```  
virtual BOOL CanAcceptMiniFrame(CPaneFrameWnd* pMiniFrame) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pMiniFrame`  
 Pointeur vers un `CPaneFrameWnd` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si `pMiniFrame` peuvent être ancrés dans le volet ; sinon, `FALSE`.  
  
##  <a name="canacceptpane"></a>CDockablePane::CanAcceptPane  
 Détermine si un autre volet peut être ancré dans le volet en cours.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pBar`  
 Spécifie le volet pour ancrer dans le volet actif.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet spécifié peut être ancré dans ce volet ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Le framework appelle cette méthode avant d’un volet soit ancré dans le volet en cours.  
  
 Remplacez cette fonction dans une classe dérivée pour activer ou désactiver l’ancrage d’un volet spécifique.  
  
 Par défaut, cette méthode retourne `TRUE` si `pBar` ou son parent est de type `CDockablePane`.  
  
##  <a name="canautohide"></a>CDockablePane::CanAutoHide  
 Détermine si le volet peut masquer.  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet peut masquer ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 `CDockablePane::CanAutoHide`Retourne `FALSE` dans les situations suivantes :  
  
-   Le volet n’a aucun parent.  
  
-   Le Gestionnaire d’ancrage n’autorise pas à masquer les volets.  
  
-   Le volet n’est pas ancré.  
  
##  <a name="canbeattached"></a>CDockablePane::CanBeAttached  
 Détermine si le volet actif peut être ancré à un autre volet.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet « dockable » peut être ancré à un autre volet ou à la fenêtre frame principale. dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Par défaut, cette méthode retourne toujours `TRUE`. Substituez cette méthode dans une classe dérivée pour activer ou désactiver l’ancrage sans appeler [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="cdockablepane"></a>CDockablePane::CDockablePane  
 Construit et initialise un [CDockablePane](../../mfc/reference/cdockablepane-class.md) objet.  
  
```  
CDockablePane();
```  
  
### <a name="remarks"></a>Notes  
 Après avoir construit un objet pane ancrable, appelez [CDockablePane::Create](#create) ou [CDockablePane::CreateEx](#createex) pour le créer.  
  
##  <a name="converttotabbeddocument"></a>CDockablePane::ConvertToTabbedDocument  
 Convertit un ou plusieurs volets ancrables documents MDI avec onglets.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bActiveTabOnly`  
 Lorsque vous convertissez un `CTabbedPane`, spécifiez `TRUE` convertir uniquement l’onglet actif. Spécifiez `FALSE` pour convertir tous les onglets dans le volet.  
  
##  <a name="checkautohidecondition"></a>CDockablePane::CheckAutoHideCondition  
 Détermine si le volet d’ancrage est masqué (également appelé mode de masquage automatique).  
  
```  
virtual BOOL CheckAutoHideCondition();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la condition de masquage est remplie ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 L’infrastructure utilise un minuteur pour vérifier périodiquement s’il faut masquer un volet ancrable masquage automatique. La méthode retourne `TRUE` lorsque le volet n’est pas actif, le volet n’est pas en cours de redimensionnement et le pointeur de la souris n’est pas sur le volet.  
  
 Si toutes les conditions précédentes sont remplies, le framework appelle [CDockablePane::Slide](#slide) pour masquer le volet.  
  
##  <a name="checkstopslidecondition"></a>CDockablePane::CheckStopSlideCondition  
 Détermine quand un volet d’ancrage masquage automatique doit s’arrêter coulissant.  
  
```  
virtual BOOL CheckStopSlideCondition(BOOL bDirection);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bDirection`  
 `TRUE`Si le volet est visible ; `FALSE` si le volet est masqué.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la condition d’arrêt est remplie ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un volet « dockable » est défini en mode de masquage automatique, le framework utilise des effets glissantes pour afficher ou masquer le volet. L’infrastructure appelle cette fonction lorsque le volet est décalée. `CheckStopSlideCondition`Retourne `TRUE` lorsque le volet est entièrement visible ou lorsqu’il est entièrement masqué.  
  
 Substituez cette méthode dans une classe dérivée pour implémenter des effets de masquage automatique personnalisé.  
  
##  <a name="copystate"></a>CDockablePane::CopyState  
 Copie de l’état d’un volet Ancrable.  
  
```  
virtual void CopyState(CDockablePane* pOrgBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pOrgBar`  
 Pointeur vers un volet Ancrable.  
  
### <a name="remarks"></a>Notes  
 `CDockablePane::CopyState`copie de l’état de `pOrgBar` dans le volet en cours en appelant les méthodes suivantes :  
  
- [CPane::CopyState](../../mfc/reference/cpane-class.md#copystate)  
  
- [CDockablePane::GetAHRestoredRect](#getahrestoredrect)  
  
- [CDockablePane::GetAHSlideMode](#getahslidemode)  
  
- [CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)  
  
- [CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)  
  
##  <a name="create"></a>CDockablePane::Create  
 Crée le contrôle Windows et l’attache à la [CDockablePane](../../mfc/reference/cdockablepane-class.md) objet.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);

 
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    CSize sizeDefault,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle = WS_CHILD|WS_VISIBLE|CBRS_TOP|CBRS_HIDE_INPLACE,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszCaption`  
 Spécifie le nom de la fenêtre.  
  
 [in] [out]`pParentWnd`  
 Spécifie la fenêtre parente.  
  
 [in] `rect`  
 Spécifie la taille et la position de la fenêtre, en coordonnées clientes de `pParentWnd`.  
  
 [in] `bHasGripper`  
 `TRUE`Pour créer le volet avec une légende ; dans le cas contraire, `FALSE`.  
  
 [in] `nID`  
 Spécifie l’ID de la fenêtre enfant. Cette valeur doit être unique si vous souhaitez enregistrer l’état d’ancrage pour ce volet d’ancrage.  
  
 [in] `dwStyle`  
 Spécifie les attributs de style de fenêtre.  
  
 [in] `dwTabbedStyle`  
 Spécifie le style d’une fenêtre à onglets qui est créé lorsque l’utilisateur fait glisser un volet sur la légende de ce volet à onglets.  
  
 [in] `dwControlBarStyle`  
 Spécifie les attributs de style supplémentaires.  
  
 [in] [out]`pContext`  
 Spécifie le contexte de la création de la fenêtre.  
  
 [in] `lpszWindowName`  
 Spécifie le nom de la fenêtre.  
  
 [in] `sizeDefault`  
 Spécifie la taille de la fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet « dockable » est créé avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Crée un volet Windows et l’attache à le `CDockablePane` objet.  
  
 Si le `dwStyle` style de fenêtre a la `CBRS_FLOAT_MULTI` indicateur, la fenêtre mini-frame peut flotter avec d’autres volets de la fenêtre mini-frame. Par défaut, volets d’ancrage peuvent uniquement faire flotter individuellement.  
  
 Si le `dwTabbedStyle` paramètre a la `AFX_CBRS_OUTLOOK_TABS` indicateur spécifié, le volet crée des volets de type Outlook avec onglets lorsqu’un autre volet est attaché à ce volet à l’aide de la [CDockablePane::AttachToTabWnd](#attachtotabwnd) (méthode). Par défaut, les volets ancrables créent les volets à onglets régulières de type [CTabbedPane](../../mfc/reference/ctabbedpane-class.md).  
  
##  <a name="createdefaultpanedivider"></a>CDockablePane::CreateDefaultPaneDivider  
 Crée un séparateur de valeur par défaut pour le volet comme elle est en cours ancrée à une fenêtre frame.  
  
```  
static CPaneDivider* __stdcall CreateDefaultPaneDivider(
    DWORD dwAlignment,  
    CWnd* pParent,  
    CRuntimeClass* pSliderRTC = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwAlignment`  
 Spécifie le côté du frame principal auquel le volet est en cours ancré. Si `dwAlignment` contient le `CBRS_ALIGN_LEFT` ou `CBRS_ALIGN_RIGHT` indicateur, cette méthode crée un vertical ( `CPaneDivider::SS_VERT`) ligne de séparation ; sinon, cette méthode crée un horizontal ( `CPaneDivider::SS_HORZ`) séparateur.  
  
 [in] `pParent`  
 Pointeur vers le frame parent.  
  
 [in] `pSliderRTC`  
 Non utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne un pointeur vers le séparateur qui vient d’être créé, ou `NULL` en cas de création de la ligne de séparation.  
  
### <a name="remarks"></a>Remarques  
 `dwAlignment`peut être une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|Le volet est en cours ancré en haut de la zone cliente d’une fenêtre frame.|  
|`CBRS_ALIGN_BOTTOM`|Le volet est en cours ancré au bas de la zone cliente d’une fenêtre frame.|  
|`CBRS_ALIGN_LEFT`|Le volet est en cours ancré sur le côté gauche de la zone cliente d’une fenêtre frame.|  
|`CBRS_ALIGN_RIGHT`|Le volet est est ancré à droite de la zone cliente d’une fenêtre frame.|  
  
##  <a name="createex"></a>CDockablePane::CreateEx  
 Crée le contrôle Windows et l’attache à la [CDockablePane](../../mfc/reference/cdockablepane-class.md) objet.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwStyleEx`  
 Spécifie les attributs de style étendu pour la nouvelle fenêtre.  
  
 [in] `lpszCaption`  
 Spécifie le nom de la fenêtre.  
  
 [in] [out]`pParentWnd`  
 Spécifie la fenêtre parente.  
  
 [in] `rect`  
 Spécifie la taille et la position de la fenêtre, en coordonnées clientes de `pParentWnd`.  
  
 [in] `bHasGripper`  
 `TRUE`Pour créer le volet avec une légende ; dans le cas contraire, `FALSE`.  
  
 [in] `nID`  
 Spécifie l’ID de la fenêtre enfant. Cette valeur doit être unique si vous souhaitez enregistrer l’état d’ancrage pour ce volet d’ancrage.  
  
 [in] `dwStyle`  
 Spécifie les attributs de style de fenêtre.  
  
 [in] `dwTabbedStyle`  
 Spécifie le style d’une fenêtre à onglets qui est créé lorsque l’utilisateur fait glisser un volet sur la légende de ce volet à onglets.  
  
 [in] `dwControlBarStyle`  
 Spécifie les attributs de style supplémentaires.  
  
 [in] [out]`pContext`  
 Spécifie le contexte de la création de la fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet « dockable » est créé avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Crée un volet Windows et l’attache à le `CDockablePane` objet.  
  
 Si le `dwStyle` style de fenêtre a la `CBRS_FLOAT_MULTI` indicateur, la fenêtre mini-frame peut flotter avec d’autres volets de la fenêtre mini-frame. Par défaut, volets d’ancrage peuvent uniquement faire flotter individuellement.  
  
 Si le `dwTabbedStyle` paramètre a la `AFX_CBRS_OUTLOOK_TABS` indicateur spécifié, le volet crée des volets de type Outlook avec onglets lorsqu’un autre volet est attaché à ce volet à l’aide de la [CDockablePane::AttachToTabWnd](#attachtotabwnd) (méthode). Par défaut, les volets ancrables créent les volets à onglets régulières de type [CTabbedPane](../../mfc/reference/ctabbedpane-class.md).  
  
##  <a name="createtabbedpane"></a>CDockablePane::CreateTabbedPane  
 Crée un volet à onglets dans le volet actif.  
  
```  
virtual CTabbedPane* CreateTabbedPane();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nouveau volet à onglets, ou `NULL` si l’opération de création a échoué.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode lorsqu’il crée un volet à onglets pour remplacer ce volet. Pour plus d’informations, consultez [CDockablePane::AttachToTabWnd](#attachtotabwnd).  
  
 Remplacement de cette méthode dans une classe dérivée pour personnaliser les volets à onglets comment sont créés et initialisés.  
  
 L’onglet est créé selon les informations de classe d’exécution stockées dans le `m_pTabbedControlBarRTC` member, qui est initialisée par le [CDockablePane::CreateEx](#createex) (méthode).  
  
##  <a name="dockpanecontainer"></a>CDockablePane::DockPaneContainer  
 Ancre un conteneur dans le volet.  
  
```  
virtual BOOL DockPaneContainer(
    CPaneContainerManager& barContainerManager,  
    DWORD dwAlignment,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `barContainerManager`  
 Une référence au Gestionnaire de conteneur du conteneur qui est en cours ancré.  
  
 [in] `dwAlignment`  
 `DWORD`qui spécifie le côté du volet dans lequel le conteneur est en cours ancré.  
  
 [in] `dockMethod`  
 Non utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le conteneur a été ancré avec succès vers le volet ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 `dwAlignment`peut être une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|Le conteneur est en cours ancré en haut du volet.|  
|`CBRS_ALIGN_BOTTOM`|Le conteneur est en cours ancré au bas du volet.|  
|`CBRS_ALIGN_LEFT`|Le conteneur est en cours ancré à gauche du volet.|  
|`CBRS_ALIGN_RIGHT`|Le conteneur est en cours ancré à droite du volet.|  
  
##  <a name="dockpanestandard"></a>CDockablePane::DockPaneStandard  
 Ancre un volet à l’aide de plan de la station d’accueil (standard).  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bWasDocked`  
 Lorsque la méthode est retournée, cette valeur contient `TRUE` si celui-ci a été correctement ancrée ; sinon, il contient `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le volet est ancré à une fenêtre avec onglets, ou si une fenêtre à onglets a été créée à la suite d’ancrage, cette méthode retourne un pointeur vers la fenêtre à onglets. Si le volet était sinon ancrée avec succès, cette méthode retourne le `this` pointeur. Si d’ancrage a échoué, cette méthode retourne `NULL`.  
  
##  <a name="docktorecentpos"></a>CDockablePane::DockToRecentPos  
 Ancre un volet à sa position d’ancrage stockée.  
  
```  
BOOL CDockablePane::DockToRecentPos();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet est ancré avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Volets ancrables stockent des informations d’ancrage récentes dans une [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md) objet.  
  
##  <a name="docktowindow"></a>CDockablePane::DockToWindow  
 Ancre un volet d’ancrage à un autre volet d’ancrage.  
  
```  
virtual BOOL DockToWindow(
    CDockablePane* pTargetWindow,  
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out]`pTargetWindow`  
 Spécifie le volet pour ancrer ce volet pour Ancrable.  
  
 [in] `dwAlignment`  
 Spécifie l’alignement du volet d’ancrage. Peut être CBRS_ALIGN_LEFT, CBRS_ALIGN_TOP, CBRS_ALIGN_RIGHT, CBRS_ALIGN_BOTTOM ou CBRS_ALIGN_ANY. (Défini dans afxres.h.)  
  
 [in] `lpRect`  
 Spécifie le rectangle d’ancrage du volet.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet est ancré avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour ancrer un volet à un autre volet, avec l’alignement spécifié par `dwAlignment`.  
  
##  <a name="drawcaption"></a>CDockablePane::DrawCaption  
 Dessine la légende (également appelée la barre de redimensionnement) d’un volet d’ancrage.  
  
```  
virtual void DrawCaption(
    CDC* pDC,  
    CRect rectCaption);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Représente le contexte de périphérique utilisé pour le dessin.  
  
 [in] `rectCaption`  
 Spécifie le rectangle englobant dans légende du volet.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode pour dessiner la légende d’un volet Ancrable.  
  
 Substituez cette méthode dans une classe dérivée pour personnaliser l’apparence de la légende.  
  
##  <a name="enableautohideall"></a>CDockablePane::EnableAutohideAll  
 Active ou désactive le mode de masquage automatique pour ce volet et pour les autres volets dans le conteneur.  
  
```  
void EnableAutohideAll(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour activer la fonction Masquer automatiquement toutes les fonctionnalités du volet ancrable ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Lorsque l’utilisateur maintient le `Ctrl` clé et clique sur le bouton pin pour basculer d’un volet en mode de masquage automatique, tous les autres volets dans le même conteneur sont également passe en mode de masquage automatique.  
  
 Appelez cette méthode avec `bEnable` la valeur `FALSE` pour désactiver cette fonctionnalité pour un volet spécifique.  
  
##  <a name="enablegripper"></a>CDockablePane::EnableGripper  
 Affiche ou masque la légende (également appelée la barre de redimensionnement).  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour activer la légende ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Lorsque l’infrastructure crée les volets ancrables, ils n’ont pas la **WS_STYLE** style de fenêtre, même s’il est spécifié. Cela signifie que légende du volet est une zone non cliente qui est contrôlée par l’infrastructure, mais cette zone diffère de la légende de fenêtre standard.  
  
 Vous pouvez afficher ou masquer la légende à tout moment. L’infrastructure masque la légende lorsqu’un volet est ajouté sous forme d’onglet dans une fenêtre à onglets ou lorsqu’un volet est flotter dans une fenêtre mini-frame.  
  
##  <a name="getahrestoredrect"></a>CDockablePane::GetAHRestoredRect  
 Spécifie la position du volet en mode de masquage automatique.  
  
```  
CRect GetAHRestoredRect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CRect` objet qui contient la position du volet lorsqu’il est en mode de masquage automatique.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getahslidemode"></a>CDockablePane::GetAHSlideMode  
 Récupère le mode slide masquer le volet.  
  
```  
virtual UINT GetAHSlideMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `UINT` qui spécifie le mode slide masquer le volet. La valeur de retour peut être soit `AFX_AHSM_MOVE` ou `AFX_AHSM_STRETCH`, mais l’implémentation utilise uniquement `AFX_AHSM_MOVE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcaptionheight"></a>CDockablePane::GetCaptionHeight  
 Retourne la hauteur, en pixels, de la légende en cours.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur de la légende, en pixels.  
  
### <a name="remarks"></a>Remarques  
 Hauteur de la légende est 0 si la légende est masquée par la [CDockablePane::EnableGripper](#enablegripper) (méthode), ou si le volet ne possède pas de légende.  
  
##  <a name="getdefaultpanedivider"></a>CDockablePane::GetDefaultPaneDivider  
 Retourne le diviseur de volet par défaut pour le conteneur du volet.  
  
```  
CPaneDivider* GetDefaultPaneDivider() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valide [CPaneDivider](../../mfc/reference/cpanedivider-class.md) objet si le volet ancrable est ancré à la fenêtre frame principale, ou `NULL` si le volet « dockable » n’est pas ancré ou flotter.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations sur les séparateurs de volets, consultez [CPaneDivider classe](../../mfc/reference/cpanedivider-class.md).  
  
##  <a name="getdockingstatus"></a>CDockablePane::GetDockingStatus  
 Détermine la possibilité d’un volet ancré selon l’emplacement du pointeur fourni.  
  
```  
virtual AFX_CS_STATUS GetDockingStatus(
    CPoint pt,  
    int nSensitivity);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pt`  
 L’emplacement du pointeur en coordonnées d’écran.  
  
 [in] `nSensitivity`  
 La distance, en pixels, en dehors de la bordure d’un rectangle le pointeur doit être à l’activation de l’ancrage.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs d’état suivantes :  
  
|Valeur `AFX_CS_STATUS`|Signification|  
|---------------------------|-------------|  
|`CS_NOTHING`|Le pointeur n’est pas sur un site d’ancrage. Le framework ne pas ancrer le volet.|  
|`CS_DOCK_IMMEDIATELY`|Le pointeur se trouve sur le site d’ancrage en mode exécution (utilise le volet de la `DT_IMMEDIATE` mode d’ancrage). Le framework ancre le volet immédiatement.|  
|`CS_DELAY_DOCK`|Le pointeur se trouve sur un site d’ancrage est un autre volet d’ancrage ou un bord de l’image principale. Le framework ancre le volet après un certain délai. Consultez la section Notes pour plus d’informations sur ce délai.|  
|`CS_DELAY_DOCK_TO_TAB`|Le pointeur se trouve sur un site d’ancrage qui provoque le volet ancré dans une fenêtre à onglets. Cela se produit lorsque le pointeur se trouve sur la légende d’un autre volet d’ancrage ou sur la zone de l’onglet d’un volet à onglets.|  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode pour gérer l’ancrage d’un volet flottant.  
  
 Pour les barres d’outils flottantes ou ancrage volets qui utilisent la `DT_IMMEDIATE` ancrage mode, le framework retarde la commande d’ancrage pour permettre aux utilisateurs de déplacer la fenêtre hors de la zone cliente du frame parent avant d’ancrage. La longueur du délai est exprimée en millisecondes et est contrôlée par le [CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock) membre de données... La valeur par défaut [CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock) est 200. Ce comportement émule le comportement d’ancrage [!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)] 2007.  
  
 Pour un différé d’accueil des États ( `CS_DELAY_DOCK` et `CS_DELAY_DOCK_TO_TAB`), le framework n’effectue pas d’ancrage jusqu'à ce que l’utilisateur relâche le bouton de la souris. Si un volet utilise le `DT_STANDARD` ancrage mode, l’infrastructure affiche un rectangle à l’emplacement d’ancrage projetée. Si un volet utilise le `DT_SMART` ancrage mode, l’infrastructure affiche des marqueurs d’ancrage intelligents et des rectangles semi-transparent à l’emplacement d’ancrage projetée. Pour spécifier le mode d’ancrage de votre volet, appelez le [CBasePane::SetDockingMode](../../mfc/reference/cbasepane-class.md#setdockingmode) (méthode). Pour plus d’informations sur l’ancrage actif, consultez [CDockingManager::GetSmartDockingParams](../../mfc/reference/cdockingmanager-class.md#getsmartdockingparams).  
  
##  <a name="getdragsensitivity"></a>CDockablePane::GetDragSensitivity  
 Retourne la sensibilité de glissement d’un volet d’ancrage.  
  
```  
static const CSize& GetDragSensitivity();
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objet qui contient la largeur et la hauteur, en pixels, d’un rectangle centré sur un point de glissement. L’opération de glissement ne commence pas tant que le pointeur de la souris se déplace en dehors de ce rectangle.  
  
##  <a name="getlastpercentinpanecontainer"></a>CDockablePane::GetLastPercentInPaneContainer  
 Récupère le pourcentage d’espace occupé par un volet dans son conteneur ( [CPaneContainer classe](../../mfc/reference/cpanecontainer-class.md)).  
  
```  
int GetLastPercentInPaneContainer() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `int` qui spécifie le pourcentage d’espace occupé par le volet dans son conteneur.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est utilisée lorsque le conteneur s’ajuste sa disposition.  
  
##  <a name="gettabarea"></a>CDockablePane::GetTabArea  
 Récupère la zone des onglets du volet.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rectTabAreaTop`  
 `GetTabArea`remplit cette variable avec la zone de l’onglet si les onglets sont situés en haut du volet. Si les onglets sont situés en bas du volet, cette variable est remplie avec un rectangle vide.  
  
 [in] `rectTabAreaBottom`  
 `GetTabArea`remplit cette variable avec la zone de l’onglet si les onglets sont situés en bas du volet. Si les onglets sont situés en haut du volet, cette variable est remplie avec un rectangle vide.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est utilisée uniquement dans les classes dérivées de `CDockablePane` et onglets. Pour plus d’informations, consultez [CTabbedPane::GetTabArea](../../mfc/reference/ctabbedpane-class.md#gettabarea) et [CMFCOutlookBar::GetTabArea](../../mfc/reference/cmfcoutlookbar-class.md#gettabarea).  
  
##  <a name="gettabbedpanertc"></a>CDockablePane::GetTabbedPaneRTC  
 Retourne les informations de classe d’exécution sur une fenêtre avec onglets qui est créée lorsqu’un autre volet est ancré dans le volet en cours.  
  
```  
CRuntimeClass* GetTabbedPaneRTC() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Les informations de classe runtime pour le volet Ancrable.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour récupérer les informations de classe d’exécution pour les volets à onglets qui sont créés dynamiquement. Cela peut se produire lorsqu’un utilisateur fait glisser un volet à la légende d’un autre volet, ou si vous appelez le [CDockablePane::AttachToTabWnd](#attachtotabwnd) méthode pour créer par programme un volet à onglets de deux volets ancrables.  
  
 Vous pouvez définir les informations de classe d’exécution en appelant le [CDockablePane::SetTabbedPaneRTC](#settabbedpanertc) (méthode).  
  
##  <a name="hasautohidemode"></a>CDockablePane::HasAutoHideMode  
 Spécifie si un volet d’ancrage peut être basculé en mode de masquage automatique.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet « dockable » peut être basculé en mode de masquage automatique ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Substituez cette méthode dans une classe dérivée pour désactiver le mode de masquage automatique pour un volet ancrable spécifique.  
  
##  <a name="hittest"></a>CDockablePane::HitTest  
 Spécifie l’emplacement d’un volet sur lequel l’utilisateur clique sur la souris.  
  
```  
virtual int HitTest(
    CPoint point,  
    BOOL bDetectCaption = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Spécifie le point à tester.  
  
 [in] `bDetectCaption`  
 `TRUE`Si `HTCAPTION` doit être retournée si le point se trouve sur la légende du volet ; sinon, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs suivantes :  
  
- `HTNOWHERE`Si `point` n’est pas dans le volet « dockable ».  
  
- `HTCLIENT`Si `point` se trouve dans la zone cliente du volet Ancrable.  
  
- `HTCAPTION`Si `point` se trouve dans la zone de légende du volet Ancrable.  
  
- `AFX_HTCLOSE`Si `point` se trouve sur le bouton Fermer.  
  
- `HTMAXBUTTON`Si `point` se trouve sur le bouton pin.  
  
##  <a name="isautohideallenabled"></a>CDockablePane::IsAutohideAllEnabled  
 Indique si le volet d’ancrage et tous les autres volets dans le conteneur peuvent être basculés en mode de masquage automatique.  
  
```  
virtual BOOL IsAutohideAllEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet « dockable » et tous les autres volets dans le conteneur, peuvent être basculés en mode de masquage automatique ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Un utilisateur Active le mode de masquage automatique en cliquant sur le bouton pin d’ancrage tout en maintenant la **Ctrl** clé  
  
 Pour activer ou désactiver ce comportement, appelez le [CDockablePane::EnableAutohideAll](#enableautohideall) (méthode).  
  
##  <a name="isautohidemode"></a>CDockablePane::IsAutoHideMode  
 Détermine si un volet est en mode de masquage automatique.  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet « dockable » est en mode de masquage automatique ; dans le cas contraire, `FALSE`.  
  
##  <a name="isdocked"></a>CDockablePane::IsDocked  
 Détermine si le volet actif est ancré.  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet ancrable n’appartient pas à une fenêtre mini-frame ou s’il est flottant dans une fenêtre mini-frame avec un autre volet. `FALSE`Si le volet est un enfant d’une fenêtre mini-frame et qu’aucun autres volets qui appartiennent à la fenêtre mini-frame.  
  
### <a name="remarks"></a>Remarques  
 Pour déterminer si le volet est ancré à la fenêtre frame principale, appelez [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider). Si la méthode retourne un pointeur non NULL, le volet est ancré à la fenêtre frame principale.  
  
##  <a name="ishideinautohidemode"></a>CDockablePane::IsHideInAutoHideMode  
 Détermine le comportement d’un volet qui est en mode de masquage automatique ou s’il est indiqué (masqué) en appelant [CDockablePane::ShowPane](#showpane).  
  
```  
virtual BOOL IsHideInAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet « dockable » doit être masqué en mode de masquage automatique ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Lorsqu’un volet « dockable » est en mode de masquage automatique, il comporte différemment lorsque vous appelez `ShowPane` pour masquer ou afficher le volet. Ce comportement est contrôlé par le membre statique [CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode). Si ce membre est `TRUE`, le volet ancrable et sa barre d’outils connexes masquage automatique ou le bouton masquage automatique est masqué ou affiché lorsque vous appelez `ShowPane`. Dans le cas contraire, le volet « dockable » est activé ou désactivé, et sa barre d’outils associés de masquage automatique ou le bouton masquage automatique est toujours visible.  
  
 Substituez cette méthode dans une classe dérivée pour modifier le comportement par défaut pour les volets individuels.  
  
 La valeur par défaut de `m_bHideInAutoHideMode` est `FALSE`.  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CDockablePane::IsInFloatingMultiPaneFrameWnd  
 Spécifie si le volet est dans une fenêtre frame de plusieurs volets ( [CMultiPaneFrameWnd classe](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet est dans une fenêtre frame de plusieurs volets ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="isresizable"></a>CDockablePane::IsResizable  
 Spécifie si le volet peut être redimensionnée.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet est redimensionnable ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Par défaut, les volets ancrables sont redimensionnables. Pour empêcher le redimensionnement, substituez cette méthode dans une classe dérivée et retourner `FALSE`. Notez qu’un `FALSE` valeur entraîne un échec `ASSERT` dans [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane). Utilisez [CDockingManager::AddPane](../../mfc/reference/cdockingmanager-class.md#addpane) à la place pour ancrer un volet au sein d’un frame parent.  
  
 Volets qui ne peuvent pas être redimensionnés peuvent ni float ni entrer en mode de masquage automatique et sont toujours situés sur le bord du frame parent.  
  
##  <a name="istablocationbottom"></a>CDockablePane::IsTabLocationBottom  
 Spécifie si les onglets sont situés en haut ou en bas du volet.  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si les onglets sont situés en bas du volet. `FALSE` si les onglets sont situés en haut du volet.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [CTabbedPane::IsTabLocationBottom](../../mfc/reference/ctabbedpane-class.md#istablocationbottom).  
  
##  <a name="istracked"></a>CDockablePane::IsTracked  
 Spécifie si un volet est déplacé par l’utilisateur.  
  
```  
BOOL IsTracked() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet est déplacé ; dans le cas contraire, `FALSE`.  
  
##  <a name="isvisible"></a>CDockablePane::IsVisible  
 Détermine si le volet actif est visible.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet « dockable » est visible ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour déterminer si un volet ancrable est visible. Vous pouvez utiliser cette méthode au lieu d’appeler [CWnd::IsWindowVisible](../../mfc/reference/cwnd-class.md#iswindowvisible) ou des tests pour les `WS_VISIBLE` style. L’état de visibilité retourné dépend si le mode de masquage automatique est activé ou désactivé et la valeur de la [CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode) propriété.  
  
 Si le volet « dockable » est en mode de masquage automatique et `IsHideInAutoHideMode` retourne `FALSE` l’état de visibilité est toujours `FALSE`.  
  
 Si le volet « dockable » est en mode de masquage automatique et `IsHideInAutoHideMode` retourne `TRUE` dépend de l’état de visibilité sur l’état de visibilité de la barre d’outils connexes masquage automatique.  
  
 Si le volet « dockable » n’est pas en mode de masquage automatique, l’état de visibilité est déterminée par le [CBasePane::IsVisible](../../mfc/reference/cbasepane-class.md#isvisible) (méthode).  
  
##  <a name="m_bdisableanimation"></a>CDockablePane::m_bDisableAnimation  
 Indique si l’animation de masquage automatique du volet « dockable » est désactivée.  
  
```  
AFX_IMPORT_DATA static BOOL m_bDisableAnimation;  
```  
  
##  <a name="m_bhideinautohidemode"></a>CDockablePane::m_bHideInAutoHideMode  
 Détermine le comportement du volet lorsque le volet est en mode de masquage automatique.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideInAutoHideMode;  
```  
  
### <a name="remarks"></a>Remarques  
 Cette valeur affecte tous les volets d’ancrage dans l’application.  
  
 Si vous définissez ce membre sur `TRUE`, volets ancrables seront affichés ou masqués avec leurs boutons et barres d’outils connexes Masquer automatiquement lorsque vous appelez [CDockablePane::ShowPane](#showpane).  
  
 Si vous définissez ce membre sur `FALSE`, volets ancrables sont activées ou désactivées lorsque vous appelez [CDockablePane::ShowPane](#showpane).  
  
##  <a name="m_nslidesteps"></a>CDockablePane::m_nSlideSteps  
 Spécifie la vitesse d’animation du volet lorsqu’elle est en mode de masquage automatique.  
  
```  
AFX_IMPORT_DATA static int m_nSlideSteps;  
```  
  
### <a name="remarks"></a>Notes  
 Pour un effet d’animation plus rapidement, réduisez cette valeur. Pour un effet d’animation plus lent, augmentez cette valeur.  
  
##  <a name="onafterchangeparent"></a>CDockablePane::OnAfterChangeParent  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndOldParent`  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onafterdockfromminiframe"></a>CDockablePane::OnAfterDockFromMiniFrame  
 Appelé par l’infrastructure lorsqu’une barre d’ancrage flottante est ancré à une fenêtre frame.  
  
```  
virtual void OnAfterDockFromMiniFrame();
```  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette méthode ne fait rien.  
  
##  <a name="onbeforechangeparent"></a>CDockablePane::OnBeforeChangeParent  
 Le framework appelle cette méthode avant de définir le parent du volet.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndNewParent`  
 Pointeur vers la nouvelle fenêtre parent.  
  
 [in] `bDelay`  
 `BOOL`qui spécifie s’il faut différer le recalcul de la mise en page d’accueil si le volet est flottant. Pour plus d’informations, consultez [CDockablePane::UndockPane](#undockpane).  
  
### <a name="remarks"></a>Remarques  
 Si le volet est ancré et le nouveau parent n’autorise pas d’ancrage, cette méthode détache le volet.  
  
 Si le volet est converti en un document à onglets, cette méthode stocke sa position d’ancrage récente. L’infrastructure utilise la position d’ancrage récente pour restaurer la position du volet lorsqu’il est converti dans un état ancré.  
  
##  <a name="onbeforefloat"></a>CDockablePane::OnBeforeFloat  
 L’infrastructure appelle cette méthode avant d’un volet de transitions à l’état flottant.  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rectFloat`  
 Spécifie la position et la taille du volet lorsqu’elle est dans un état flottant.  
  
 [in] `dockMethod`  
 Spécifie la méthode d’ancrage. Consultez la page [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) pour obtenir la liste des valeurs possibles.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le volet peut flotter ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est appelée par l’infrastructure lorsqu’un volet est sur le type float. Vous pouvez substituer cette méthode dans une classe dérivée si vous souhaitez effectuer tout traitement avant le volet flotte.  
  
##  <a name="onpressbuttons"></a>CDockablePane::OnPressButtons  
 Appelé lorsque l’utilisateur appuie sur un bouton de légende autres que les `AFX_HTCLOSE` et `AFX_HTMAXBUTTON` boutons.  
  
```  
virtual void OnPressButtons(UINT nHit);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nHit`  
 Ce paramètre n'est pas utilisé.  
  
### <a name="remarks"></a>Notes  
 Si vous ajoutez un bouton personnalisé à la légende d’un volet ancrable, substituez cette méthode pour recevoir des notifications lorsque l’utilisateur appuie sur le bouton.  
  
##  <a name="onslide"></a>CDockablePane::OnSlide  
 Appelé par l’infrastructure pour animer le volet lorsqu’il est en mode de masquage automatique.  
  
```  
virtual void OnSlide(BOOL bSlideOut);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bSlideOut`  
 `TRUE`Pour afficher le volet ; `FALSE` pour masquer le volet.  
  
### <a name="remarks"></a>Remarques  
 Substituez cette méthode dans une classe dérivée pour implémenter des effets de masquage automatique personnalisé.  
  
##  <a name="removefromdefaultpanedividier"></a>CDockablePane::RemoveFromDefaultPaneDividier  
 L’infrastructure appelle cette méthode lorsqu’un volet est en cours flottant.  
  
```  
void RemoveFromDefaultPaneDividier();
```  
  
### <a name="remarks"></a>Remarques  
 Cette méthode définit le diviseur de volet par défaut `NULL` et supprime le volet de son conteneur.  
  
##  <a name="replacepane"></a>CDockablePane::ReplacePane  
 Remplace le volet volet spécifié.  
  
```  
BOOL ReplacePane(
    CDockablePane* pBarToReplaceWith,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bRegisterWithFrame = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pBarToReplaceWith`  
 Pointeur vers un volet Ancrable.  
  
 [in] `dockMethod`  
 Non utilisé.  
  
 [in] `bRegisterWithFrame`  
 Si `TRUE`, le nouveau volet est inscrit avec le Gestionnaire du parent de l’ancien volet d’ancrage. Le nouveau volet est inséré à l’index de l’ancien volet dans la liste des volets qui est gérée par le Gestionnaire d’ancrage.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le remplacement a réussi ; dans le cas contraire, `FALSE`.  
  
##  <a name="restoredefaultpanedivider"></a>CDockablePane::RestoreDefaultPaneDivider  
 Lorsqu’un volet est désérialisé, le framework appelle cette méthode pour restaurer le diviseur de volet par défaut.  
  
```  
void RestoreDefaultPaneDivider();
```  
  
### <a name="remarks"></a>Notes  
 Le diviseur de volet par défaut restaurée remplace le diviseur de volet par défaut actuel, si elle existe.  
  
##  <a name="setautohidemode"></a>CDockablePane::SetAutoHideMode  
 Bascule le volet d’ancrage entre visible et le mode de masquage automatique.  
  
```  
virtual CMFCAutoHideBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bMode`  
 `TRUE`Pour activer le mode de masquage automatique ; `FALSE` pour activer le mode d’ancrage standard.  
  
 [in] `dwAlignment`  
 Spécifie l’alignement du volet masquage automatique pour la créer.  
  
 [in] [out]`pCurrAutoHideBar`  
 Pointeur vers la barre d’outils de masquage automatique en cours. Peut être `NULL`.  
  
 [in] `bUseTimer`  
 Spécifie s’il faut utiliser l’effet de masquer automatiquement lorsque l’utilisateur bascule le volet en mode de masquage automatique ou masquer le volet immédiatement.  
  
### <a name="return-value"></a>Valeur de retour  
 La barre d’outils de masquage automatique a été créé en passant en mode de masquage automatique, ou `NULL`.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode lorsqu’un utilisateur clique sur le bouton pin pour basculer le volet « dockable » au mode de masquage automatique ou en mode d’ancrage normal.  
  
 Appelez cette méthode pour passer un volet ancrable en mode de masquage automatique par programme. Le volet doit être ancré à la fenêtre frame principale ( [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider) doit retourner un pointeur valide vers le [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
##  <a name="setautohideparents"></a>CDockablePane::SetAutoHideParents  
 Définit le bouton Masquer automatiquement et la barre d’outils de masquage automatique pour le volet.  
  
```  
void SetAutoHideParents(
    CMFCAutoHideBar* pToolBar,  
    CMFCAutoHideButton* pBtn);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pToolBar`  
 Pointeur vers une barre d’outils de masquage automatique.  
  
 [in] `pBtn`  
 Pointeur vers un bouton Masquer automatiquement.  
  
##  <a name="setlastpercentinpanecontainer"></a>CDockablePane::SetLastPercentInPaneContainer  
 Définit le pourcentage d’espace occupé par un volet dans son conteneur.  
  
```  
void SetLastPercentInPaneContainer(int n);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `n`  
 Un `int` qui spécifie le pourcentage d’espace occupé par le volet dans son conteneur.  
  
### <a name="remarks"></a>Remarques  
 Le framework ajuste le volet pour utiliser la nouvelle valeur lors de la mise en page est recalculée.  
  
##  <a name="setrestoreddefaultpanedivider"></a>CDockablePane::SetRestoredDefaultPaneDivider  
 Définit le diviseur de volet par défaut.  
  
```  
void SetRestoredDefaultPaneDivider(HWND hRestoredSlider);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hRestoredSlider`  
 Handle d’une barre de séparation (curseur).  
  
### <a name="remarks"></a>Remarques  
 Un diviseur de volet par défaut est obtenu lorsqu’un volet est désérialisé. Pour plus d’informations, consultez [CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider).  
  
##  <a name="settabbedpanertc"></a>CDockablePane::SetTabbedPaneRTC  
 Définit les informations de classe d’exécution d’une fenêtre à onglets qui est créée lorsque deux volets d’ancrage ensemble.  
  
```  
void SetTabbedPaneRTC(CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pRTC`  
 Les informations de classe runtime pour le volet à onglets.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour définir les informations de la classe runtime pour les volets à onglets qui sont créés dynamiquement. Cela peut se produire lorsqu’un utilisateur fait glisser un volet à la légende d’un autre volet, ou si vous appelez le [CDockablePane::AttachToTabWnd](#attachtotabwnd) méthode pour créer par programme un volet à onglets de deux volets ancrables.  
  
 La classe d’exécution par défaut est définie en fonction de la `dwTabbedStyle` paramètre de [CDockablePane::Create](#create) et [CDockablePane::CreateEx](#createex). Pour personnaliser les nouveaux volets à onglets, dérivez votre classe d’une des classes suivantes :  
  
- [CBaseTabbedPane (classe)](../../mfc/reference/cbasetabbedpane-class.md)  
  
- [CTabbedPane (classe)](../../mfc/reference/ctabbedpane-class.md)  
  
- [Classe de CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Ensuite, appelez cette méthode avec le pointeur vers ses informations de classe d’exécution.  
  
##  <a name="showpane"></a>CDockablePane::ShowPane  
 Affiche ou masque un volet.  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bShow`  
 `TRUE`Pour afficher le volet ; `FALSE` pour masquer le volet.  
  
 [in] `bDelay`  
 `TRUE`pour différer l’ajustement de la mise en page d’accueil ; `FALSE` pour ajuster la disposition d’ancrage immédiatement.  
  
 [in] `bActivate`  
 `TRUE`Pour activer le volet lorsque affichée ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode au lieu de la [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) lors de l’affichage ou masquage des volets ancrables.  
  
##  <a name="slide"></a>CDockablePane::Slide  
 Anime un volet en mode de masquage automatique.  
  
```  
virtual void Slide(
    BOOL bSlideOut,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bSlideOut`  
 `TRUE`Pour afficher le volet ; `FALSE` pour masquer le volet.  
  
 [in] `bUseTimer`  
 `TRUE`Pour afficher ou masquer le volet de l’effet de masquage automatique ; `FALSE` pour afficher ou masquer le volet immédiatement.  
  
### <a name="remarks"></a>Notes  
 Le framework appelle cette méthode pour animer un volet en mode de masquage automatique.  
  
 Cette méthode utilise le `CDockablePane::m_nSlideDefaultTimeOut` afin de déterminer le délai d’expiration de l’effet de diapositive. La valeur par défaut pour le délai d’attente est 1. Si vous personnalisez l’algorithme de masquage automatique, modifiez ce membre pour modifier le délai d’attente.  
  
##  <a name="toggleautohide"></a>CDockablePane::ToggleAutoHide  
 Active ou désactive le volet entre toujours visible et le mode de masquage automatique.  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>Remarques  
 Cette méthode active ou désactive le mode de masquage automatique pour le volet en appelant [CDockablePane::SetAutoHideMode](#setautohidemode).  
  
##  <a name="undockpane"></a>CDockablePane::UndockPane  
 Détache un volet à partir d’un conteneur de fenêtre mini-frame ou la fenêtre frame principale.  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bDelay`  
 `TRUE`pour différer le calcul de la mise en page d’accueil ; `FALSE` pour recalculer la disposition d’ancrage immédiatement.  
  
### <a name="remarks"></a>Remarques  
 Appelez cette méthode pour détacher un volet à partir de la fenêtre frame principale ou d’un conteneur de fenêtre multi-mini-frame (volet est flottant dans une fenêtre mini-frame unique avec d’autres).  
  
 Vous devez détacher un volet avant d’effectuer toute opération externe qui n’est pas effectuée par le [CDockingManager](../../mfc/reference/cdockingmanager-class.md). Par exemple, vous devez déconnecter un volet déplacer par programme à partir d’un emplacement à un autre.  
  
 L’infrastructure déconnecte automatiquement volets avant qu’ils sont détruits.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CPane (classe)](../../mfc/reference/cpane-class.md)

