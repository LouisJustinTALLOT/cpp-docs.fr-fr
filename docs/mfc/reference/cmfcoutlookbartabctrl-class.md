---
title: Cmfcoutlookbartabctrl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d30ad25a21bf380dd7687ccd0da0fb261aeeb023
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042307"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class
Contrôle onglet qui a l'apparence visuelle du **Volet de navigation** dans Microsoft Outlook.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Constructeur par défaut.|  
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Ajoute un contrôle Windows comme un nouvel onglet dans la barre Outlook.|  
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Appelé par l’infrastructure pour déterminer les dimensions de la zone d’édition qui apparaît lorsqu’un utilisateur renomme un onglet. (Substitue `CMFCBaseTabCtrl::CalcRectEdit`.)|  
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Appelé par l’infrastructure lors des opérations de redimensionnement pour déterminer si les boutons de page onglet de barre Outlook moins peuvent être affichées qu’actuellement visibles.|  
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Appelé par l’infrastructure lors des opérations de redimensionnement pour déterminer si plusieurs boutons de page onglet barre Outlook peut être affiché qu’actuellement visibles.|  
|[CMFCOutlookBarTabCtrl::Create](#create)|Crée le contrôle onglet de barre Outlook.|  
|`CMFCOutlookBarTabCtrl::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Spécifie si l’animation qui se produit pendant le basculement entre les onglets actifs est activée.|  
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Spécifie si un utilisateur peut modifier les étiquettes de texte sur les boutons de l’onglet de la barre Outlook. (Substitue [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|  
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Appelé par l’infrastructure pour activer les boutons qui permettent à l’utilisateur de faire défiler les boutons dans le volet de barre Outlook.|  
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identifie le volet qui contient un point spécifié. (Substitue [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|  
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Retourne la taille de bordure du contrôle onglet Outlook.|  
|`CMFCOutlookBarTabCtrl::GetTabArea`|Récupère la taille et la position de la zone d’onglet du contrôle onglet. (Substitue [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|  
|`CMFCOutlookBarTabCtrl::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||  
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Détermine si l’animation qui se produit pendant le basculement entre les onglets actifs est activée.|  
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Détermine si le contrôle onglet de barre Outlook est dans un mode qui émule Microsoft Outlook 2003.|  
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Détermine si un point se trouve à l’intérieur de la zone d’onglet. (Substitue [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|  
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Détermine si un onglet est détachable. (Substitue [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|  
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Appelé par l’infrastructure lorsqu’un onglet est inséré ou supprimé. (Substitue `CMFCBaseTabCtrl::OnChangeTabs`.)|  
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Appelé par l’infrastructure pour réduire le nombre de boutons de page d’onglet qui sont visibles.|  
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Appelé par l’infrastructure pour augmenter le nombre de boutons de page d’onglet qui sont visibles.|  
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Affiche la **Options du volet de Navigation** boîte de dialogue.|  
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Recalcule la disposition interne du contrôle onglet. (Substitue [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|  
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Définit l’onglet actif. (Substitue [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|  
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Définit la taille de bordure du contrôle onglet Outlook.|  
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Définit l’alignement de l’étiquette de texte sur les boutons de l’onglet de la barre Outlook.|  
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Définit l’image bitmap qui contient les icônes qui sont affichent au bas de la barre Outlook en mode Outlook 2003 (consultez [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)).|  
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||  
  
## <a name="remarks"></a>Notes  
 Pour créer une barre Outlook est prise en charge d’ancrage, utilisez un `CMFCOutlookBar` objet pour héberger le contrôle d’onglet de barre Outlook. Pour plus d’informations, consultez [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment initialiser un `CMFCOutlookBarTabCtrl` de l’objet et utiliser différentes méthodes de la `CMFCOutlookBarTabCtrl` classe. L’exemple montre comment activer la modification sur place de l’étiquette de texte sur les boutons de page d’onglet de la barre Outlook, activez l’animation, activer les poignées de défilement qui permettent à l’utilisateur à parcourir les boutons dans le volet de barre Outlook, définissez la taille de bordure de la suite d’onglet Outlook rôle et définissez l’alignement de l’étiquette de texte sur les boutons de l’onglet de la barre Outlook. Cet extrait de code fait partie de la [exemple de démonstration d’Outlook](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]  
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxoutlookbartabctrl.h  
  
##  <a name="addcontrol"></a>  CMFCOutlookBarTabCtrl::AddControl  
 Ajoute un contrôle Windows comme un nouvel onglet dans la barre Outlook.  
  
```  
void AddControl(
    CWnd* pWndCtrl,  
    LPCTSTR lpszName,  
    int nImageID=-1,  
    BOOL bDetachable=TRUE,  
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWndCtrl*  
 Pointeur vers un contrôle à ajouter.  
  
 [in] *le caractère*  
 Spécifie le nom de l’onglet.  
  
 [in] *bDetachable*  
 Si `TRUE`, la page sera créée comme détachable.  
  
 [in] *nImageID*  
 Index d’image dans la liste d’images interne pour l’image à afficher dans le nouvel onglet.  
  
 [in] *dwControlBarStyle*  
 Spécifie le AFX_ `CBRS_`* style pour les volets d’ancrage encapsulées.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction pour ajouter un contrôle en tant que nouvelle page d’une barre outlook.  
  
 Cette fonction appelle en interne sur [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).  
  
 Si vous définissez *bDetachable* à `TRUE`, `AddControl` crée en interne un `CDockablePaneAdapter` de l’objet et encapsule le contrôle ajouté. Il définit automatiquement la classe d’exécution de la fenêtre à onglets à la classe d’exécution de `CMFCOutlookBar` et la classe d’exécution de l’image flottante vers `CMultiPaneFrameWnd`.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `AddControl` méthode dans la `CMFCOutlookBarTabCtrl` classe. Cet extrait de code fait partie de la [exemple de démonstration d’Outlook](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]  
  
##  <a name="canshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowFewerPageButtons  
 Appelé par l’infrastructure lors du redimensionnement des opérations pour déterminer si les boutons de page onglet de barre Outlook moins peuvent être affichées qu’actuellement visibles.  
  
```  
virtual BOOL CanShowFewerPageButtons() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` s’il existe plusieurs boutons ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Le contrôle onglet de barre Outlook dynamiquement ajoute ou supprime des onglets de l’affichage en fonction de la quantité d’espace libre est disponible. Cette méthode est utilisée par l’infrastructure pour faciliter ce processus.  
  
##  <a name="canshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowMorePageButtons  
 Appelé par l’infrastructure lors du redimensionnement des opérations pour déterminer si les boutons de page onglet de barre Outlook plus peut être affiché qu’actuellement visibles.  
  
```  
virtual BOOL CanShowMorePageButtons() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` s’il existe des boutons qui ne sont pas actuellement visibles ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Le contrôle onglet de barre Outlook dynamiquement ajoute ou supprime des onglets de l’affichage, en fonction de la quantité d’espace libre est disponible. Cette méthode est utilisée par l’infrastructure pour faciliter ce processus.  
  
##  <a name="create"></a>  CMFCOutlookBarTabCtrl::Create  
 Crée le contrôle onglet de barre Outlook.  
  
```  
virtual BOOL Create(
    const CRect& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
 Spécifie la taille initiale et la position, en pixels.  
  
 [in] *pParentWnd*  
 Pointe vers la fenêtre parente. Ne doit pas être `NULL`.  
  
 [in] *nID*  
 L’ID du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le contrôle a été créé avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 En règle générale, les contrôles de barre d’onglet outlook sont créés lorsque [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md) contrôle le message WM_CREATE du processus.  
  
##  <a name="enableanimation"></a>  CMFCOutlookBarTabCtrl::EnableAnimation  
 Spécifie si l’animation qui se produit pendant le basculement entre les onglets actifs est activée.  
  
```  
static void EnableAnimation(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bActivez*  
 Spécifie si l’animation doit être activée ou désactivée.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour activer et désactiver l’animation. Lorsque l’utilisateur ouvre une page d’onglet, légende de la page diapositives vers le haut ou vers le bas si l’animation est activée. Si l’animation est désactivée, la page devient active immédiatement.  
  
 Par défaut, l’animation est activée.  
  
##  <a name="enableinplaceedit"></a>  CMFCOutlookBarTabCtrl::EnableInPlaceEdit  
 Spécifie si un utilisateur peut modifier les étiquettes de texte sur les boutons de page d’onglet de la barre Outlook.  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 *bActivez*  
 Si `TRUE`, activer la modification sur place de l’étiquette de texte. Si `FALSE`, désactiver la modification sur place.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour activer ou désactiver la modification sur place des étiquettes de texte sur les boutons de page d’onglet. La modification sur place est désactivée par défaut.  
  
##  <a name="enablescrollbuttons"></a>  CMFCOutlookBarTabCtrl::EnableScrollButtons  
 Appelé par l’infrastructure pour activer les poignées de défilement qui permettent à l’utilisateur de faire défiler les boutons dans le volet de barre Outlook.  
  
```  
void EnableScrollButtons(
    BOOL bEnable = TRUE,  
    BOOL bIsUp = TRUE,  
    BOOL bIsDown = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bActivez*  
 Détermine si les boutons de défilement sont affichées.  
  
 [in] *bIsUp*  
 Détermine si la barre de défilement supérieur est affiché.  
  
 [in] *bIsDown*  
 Détermine si la barre de défilement en bas est affichée.  
  
### <a name="remarks"></a>Notes  
 Permet d’afficher les boutons de défilement. Cette méthode est appelée par l’infrastructure lorsque l’onglet actif change pour restaurer les boutons de défilement.  
  
##  <a name="getbordersize"></a>  CMFCOutlookBarTabCtrl::GetBorderSize  
 Retourne la taille de bordure du contrôle onglet Outlook.  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille de la bordure, en pixels.  
  
##  <a name="getvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::GetVisiblePageButtons  

  
```  
int GetVisiblePageButtons() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isanimation"></a>  CMFCOutlookBarTabCtrl::IsAnimation  
 Spécifie si l’animation qui se produit pendant le basculement entre les onglets actifs est activée.  
  
```  
static BOOL IsAnimation();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’animation est activée ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appelez le [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) fonction pour activer ou désactiver l’animation.  
  
##  <a name="ismode2003"></a>  CMFCOutlookBarTabCtrl::IsMode2003  
 Détermine si le contrôle onglet de barre Outlook est dans un mode qui émule Microsoft Outlook 2003.  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le contrôle d’onglet de barre Outlook est en mode de Outlook 2003 ; dans le cas contraire `FALSE`;  
  
### <a name="remarks"></a>Notes  
 Cette valeur est définie [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).  
  
##  <a name="onshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowFewerPageButtons  
 Appelé par l’infrastructure pour réduire le nombre de boutons de page d’onglet qui sont visibles.  
  
```  
virtual void OnShowFewerPageButtons();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode ajuste le nombre de boutons d’onglet de page visible lorsque le contrôle est redimensionné.  
  
##  <a name="onshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowMorePageButtons  
 Appelé par l’infrastructure pour augmenter le nombre de boutons de page d’onglet qui sont visibles.  
  
```  
virtual void OnShowMorePageButtons();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode ajuster le nombre de boutons de page d’onglet qui sont visibles lorsque le contrôle est redimensionné.  
  
##  <a name="onshowoptions"></a>  CMFCOutlookBarTabCtrl::OnShowOptions  
 Affiche la **Options du volet de Navigation** boîte de dialogue.  
  
```  
virtual void OnShowOptions();
```  
  
### <a name="remarks"></a>Notes  
 Le **Options du volet de Navigation** boîte de dialogue permet à l’utilisateur à sélectionner les boutons de page d’onglet doivent être affichés et l’ordre dans lequel ils sont affichés.  
  
 Cette méthode est appelée par le framework lorsque l’utilisateur sélectionne le **Options du volet de Navigation** élément de menu à partir du menu de personnalisation du contrôle.  
  
##  <a name="setactivetab"></a>  CMFCOutlookBarTabCtrl::SetActiveTab  
 Définit l’onglet actif. L’onglet actif est celui qui est ouverte, avec son contenu visible.  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iTab*  
 Index de base zéro d’un onglet à ouvrir.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’onglet spécifié a été ouverte avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’effet de la définition de l’onglet actif dépend de si vous avez activé l’animation. Pour plus d’informations, consultez [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).  
  
##  <a name="setbordersize"></a>  CMFCOutlookBarTabCtrl::SetBorderSize  
 Définit la taille de bordure du contrôle onglet Outlook.  
  
```  
void SetBorderSize(int nBorderSize);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nBorderSize*  
 Spécifie la nouvelle taille de bordure en pixels.  
  
### <a name="remarks"></a>Notes  
 Définit la nouvelle taille de bordure et recalcule la disposition de fenêtre outlook.  
  
##  <a name="setpagebuttontextalign"></a>  CMFCOutlookBarTabCtrl::SetPageButtonTextAlign  
 Définit l’alignement de l’étiquette de texte sur les boutons de l’onglet de la barre Outlook.  
  
```  
void SetPageButtonTextAlign(
    UINT uiAlign,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiAlign*  
 Spécifie l’alignement du texte.  
  
 [in] *bRedraw*  
 Si `TRUE`, la fenêtre outlook est redessinée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet de modifier l’alignement du texte des boutons de page.  
  
 *uiAlign* peut prendre l’une des valeurs suivantes :  
  
|Constante|Signification|  
|--------------|-------------|  
|TA_LEFT|Alignement à gauche|  
|TA_CENTER|Alignement au centre|  
|TA_RIGHT|Alignement à droite|  
  
 La valeur par défaut est TA_CENTER.  
  
##  <a name="settoolbarimagelist"></a>  CMFCOutlookBarTabCtrl::SetToolbarImageList  
 Définit l’image bitmap qui contient les icônes qui sont affichent au bas de la barre Outlook en mode Outlook 2003.  
  
```  
BOOL SetToolbarImageList(
    UINT uiID,  
    int cx,  
    COLORREF clrTransp=RGB(255, 0, 255));
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiID*  
 Spécifie l’ID de ressource de l’image à charger.  
  
 [in] *cx*  
 Spécifie la largeur d’une image dans la liste d’images, en pixels.  
  
 [in] *clrTransp*  
 Une valeur RVB qui spécifie la couleur transparente.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` en cas de réussite ; sinon, retourne `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet de joindre une liste d’images dont les images sont affichées sur les boutons de barre d’outils en mode de Microsoft Office 2003. Index de l’image doivent correspondre à l’index de page.  
  
 Cette méthode ne doit pas être appelée si pas dans le mode de Microsoft Office 2003. Pour plus d’informations, consultez [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).  
  
##  <a name="setvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::SetVisiblePageButtons  

  
```  
void SetVisiblePageButtons(int nVisiblePageButtons);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nVisiblePageButtons*  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)   
 [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarPane, classe](../../mfc/reference/cmfcoutlookbarpane-class.md)
