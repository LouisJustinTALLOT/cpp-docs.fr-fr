---
title: Classe de CMFCReBar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
dev_langs:
- C++
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcef7bab4fd2b0cd913c0da929534d6964730215
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037959"
---
# <a name="cmfcrebar-class"></a>Classe de CMFCReBar
A `CMFCReBar` objet est une barre de contrôle qui fournit des informations d’état pour les contrôles rebar, la persistance et la mise en page.  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCReBar : public CPane  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCReBar::AddBar](#addbar)|Ajoute une bande à un contrôle rebar.|  
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Substitue [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCReBar::CanFloat](#canfloat)|(Substitue [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CMFCReBar::Create](#create)|Crée le contrôle rebar et l’attache à le `CMFCReBar` objet.|  
|[CMFCReBar::EnableDocking](#enabledocking)|(Substitue [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|  
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||  
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Fournit un accès direct à sous-jacent [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) contrôle commun.|  
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Substitue [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Substitue [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|  
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Substitue [CBasePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/e139f06a-9793-4ee2-bc3d-517389368c77).)|  
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Substitue [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|  
  
## <a name="remarks"></a>Notes  
 A `CMFCReBar` objet peut contenir plusieurs fenêtres enfants. Cela inclut les zones d’édition, des barres d’outils et des zones de liste. Vous pouvez redimensionner le rebar par programme, ou l’utilisateur peut redimensionner manuellement le rebar en faisant glisser sa barre de redimensionnement. Vous pouvez également définir l’arrière-plan d’un objet rebar à une image bitmap de votre choix.  
  
 Un objet rebar se comporte comme un objet de barre d’outils. Un contrôle rebar peut contenir une ou plusieurs bandes et que chaque bande peut contenir une barre de redimensionnement, une image bitmap, une étiquette de texte et une fenêtre enfant.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCReBar` classe. L’exemple montre comment créer un contrôle rebar et lui ajouter une bande. La bande fonctionne comme une barre d’outils interne. Cet extrait de code fait partie de la [échantillon Rebar](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxRebar.h  
  
##  <a name="addbar"></a>  CMFCReBar::AddBar  
 Ajoute une bande à un contrôle rebar.  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out] *pBar*  
 Pointeur vers la fenêtre enfant qui doit être insérée dans le rebar. L’objet référencé doit avoir le **WS_CHILD** style de fenêtre.  
  
 [in] *pszText*  
 Spécifie le texte à afficher sur le contrôle rebar. Le texte n’est pas partie de la fenêtre enfant. Au lieu de cela, il est affiché sur le rebar lui-même.  
  
 [in] [out] *pbmp*  
 Spécifie l’image bitmap à afficher sur l’arrière-plan du contrôle rebar.  
  
 [in] *dwStyle*  
 Contient le style à appliquer à la bande. Pour obtenir une liste complète des styles de bande, consultez la description de `fStyle` dans les [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) structure dans la documentation du Kit de développement logiciel Windows.  
  
 [in] *clrFore*  
 Représente la couleur de premier plan du rebar.  
  
 [in] *clrBack*  
 Représente la couleur d’arrière-plan du rebar.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la bande a été ajoutée avec succès pour le rebar ; dans le cas contraire, `FALSE`.  
  
##  <a name="create"></a>  CMFCReBar::Create  
 Crée le contrôle rebar et l’attache à la [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) objet.  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out] *pParentWnd*  
 Pointeur vers la fenêtre parente de ce contrôle rebar.  
  
 [in] *dwCtrlStyle*  
 Spécifie le style du contrôle rebar. La valeur de style par défaut est **RBS_BANDBORDERS**, qui affiche limiter les lignes entre les bandes contiguës sur le contrôle rebar. Pour obtenir la liste des styles valides, consultez [Styles de contrôle Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) dans la documentation du Kit de développement logiciel Windows.  
  
 [in] *dwStyle*  
 Le style de fenêtre du contrôle rebar. Pour obtenir la liste des styles valides, consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *nID*  
 ID de fenêtre enfant. du rebar  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le contrôle rebar a été créé avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl  
 Fournit un accès direct à `CReBarCtrl` le contrôle commun sous-jacent pour `CMFCReBar` objets.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à l’objet sous-jacent `CReBarCtrl` objet.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour tirer parti de la fonctionnalité de contrôle commune Windows rebar lorsque vous personnalisez votre rebar.  
  
##  <a name="calcfixedlayout"></a>  CMFCReBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bStretch*  
 [in] *bHorz*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="canfloat"></a>  CMFCReBar::CanFloat  

  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="enabledocking"></a>  CMFCReBar::EnableDocking  

  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *dwDockStyle*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getrebarbandinfosize"></a>  CMFCReBar::GetReBarBandInfoSize  

  
```  
UINT GetReBarBandInfoSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onshowcontrolbarmenu"></a>  CMFCReBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *CPoint*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest  

  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *point*  
 [in] *pTI*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pTarget*  
 [in] *bDisableIfNoHndler*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment  

  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *dwAlignment*  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CReBarCtrl (classe)](../../mfc/reference/crebarctrl-class.md)   
 [CPane, classe](../../mfc/reference/cpane-class.md)
