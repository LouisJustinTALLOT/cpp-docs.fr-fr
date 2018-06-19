---
title: Classe de CMFCDropDownToolBar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4f56a02f469babe22c8e5cbb9ebb4d6b806499f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369806"
---
# <a name="cmfcdropdowntoolbar-class"></a>Classe de CMFCDropDownToolBar
Barre d'outils qui s'affiche lorsque l'utilisateur appuie sur un bouton de barre d'outils de niveau supérieur et le maintient enfoncé.  
  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Substitue `CPane::AllowShowOnPaneMenu`.)|  
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Substitue [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|  
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Substitue [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|  
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||  
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||  
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Substitue `CMFCToolBar::OnSendCommand`.)|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Substitue [CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/571a38ab-2a56-4968-9796-273516126f80).)|  
  
### <a name="remarks"></a>Notes  
 A `CMFCDropDownToolBar` objet combine l’apparence d’une barre d’outils et le comportement d’un menu contextuel. Lorsqu’un utilisateur appuie sur et contient un bouton de barre d’outils déroulante (consultez [CMFCDropDownToolbarButton classe](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), une barre d’outils de la liste déroulante s’affiche, et que l’utilisateur peut sélectionner un bouton de la barre d’outils de la liste déroulante en le défilement à celui-ci et en libérant de la souris bouton. Une fois que l’utilisateur sélectionne un bouton dans la barre d’outils de la liste déroulante, ce bouton s’affiche en tant que bouton dans la barre d’outils de niveau supérieur en cours.  
  
 Une barre d’outils de la liste déroulante ne peut pas être personnalisé ou ancré, et il n’a pas un état détachable.  
  
 L’illustration suivante montre un `CMFCDropDownToolBar` objet :  
  
 ![Exemple de CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")  
  
 Vous créez un `CMFCDropDownToolBar` l’objet de la même façon que vous créez une barre d’outils ordinaire (consultez [CMFCToolBar classe](../../mfc/reference/cmfctoolbar-class.md)).  
  
 Pour insérer la barre d’outils de la liste déroulante dans une barre d’outils parent :  
  
 1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.  
  
 2. Créer un `CMFCDropDownToolBarButton` objet qui contient la barre d’outils déroulante (pour plus d’informations, consultez [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).  
  
 3. Remplacer le bouton factice avec le `CMFCDropDownToolBarButton` à l’aide de l’objet [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Pour plus d’informations sur les boutons de barre d’outils, consultez [procédure pas à pas : placement le contrôle sur la barre de d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md). Pour obtenir un exemple d’une barre d’outils de la liste déroulante, consultez l’exemple de projet VisualStudioDemo.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `Create` méthode dans la `CMFCDropDownToolBar` classe. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdropdowntoolbar.h  
  
##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap  
 Charge les images de barre d’outils à partir des ressources de l’application.  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiResID`  
 L’ID de ressource de la bitmap qui fait référence aux images de barre d’outils réactives.  
  
 [in] `uiColdResID`  
 L’ID de ressource de la bitmap qui fait référence aux images de barre d’outils non réactives.  
  
 [in] `uiMenuResID`  
 L’ID de ressource de la bitmap qui fait référence aux images de menu normales.  
  
 [in] `bLocked`  
 `TRUE` Pour verrouiller la barre d’outils ; dans le cas contraire `FALSE`.  
  
 [in] `uiDisabledResID`  
 L’ID de ressource de la bitmap qui fait référence aux images de barre d’outils désactivées.  
  
 [in] `uiMenuDisabledResID`  
 L’ID de ressource de la bitmap qui fait référence aux images de menu désactivées.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) appelle cette méthode pour charger les images qui sont associés à la barre d’outils. Surchargez cette méthode pour effectuer un chargement personnalisé des ressources d’images.  
  
 Appelez la méthode `LoadBitmapEx` pour charger des images supplémentaires après avoir créé la barre d’outils.  
  
##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar  

  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID = 0,  
    UINT uiMenuResID = 0,
    BOOL = FALSE,  
    UINT uiDisabledResID = 0,  
    UINT uiMenuDisabledResID = 0,  
    UINT uiHotResID = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiResID`  
 [in] `uiColdResID`  
 [in] `uiMenuResID`  
 [in] `BOOL`  
 [in] `uiDisabledResID`  
 [in] `uiMenuDisabledResID`  
 [in] `uiHotResID`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp  

  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nFlags`  
 [in] `point`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove  

  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nFlags`  
 [in] `point`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pButton`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pTarget`  
 [in] `bDisableIfNoHndler`  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Classe de CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [Procédure pas à pas : placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)



