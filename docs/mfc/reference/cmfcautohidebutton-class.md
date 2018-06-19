---
title: Classe CMFCAutoHideButton | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48dc35a5b3e7f6b12376a47d68a95602bed48c49
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375309"
---
# <a name="cmfcautohidebutton-class"></a>Cmfcautohidebutton, classe
Bouton qui affiche ou masque une [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) configurée pour être masquée.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCAutoHideButton : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCAutoHideButton::BringToTop](#bringtotop)||  
|[CMFCAutoHideButton::Create](#create)|Crée et initialise les bouton masquer automatiquement.|  
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Récupère l'alignement du bouton masquer automatiquement.|  
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Retourne le [CDockablePane](../../mfc/reference/cdockablepane-class.md) objet associé avec le bouton Masquer automatiquement.|  
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||  
|[CMFCAutoHideButton::GetRect](#getrect)||  
|[CMFCAutoHideButton::GetSize](#getsize)|Détermine la taille du bouton masquer automatiquement.|  
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Retourne la taille de l'étiquette de texte du bouton masquer automatiquement.|  
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Met en évidence le bouton masquer automatiquement.|  
|[CMFCAutoHideButton::IsActive](#isactive)|Indique si le bouton masquer automatiquement est actif.|  
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Fait état de la mise en évidence du bouton masquer automatiquement.|  
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Détermine si le bouton masquer automatiquement est horizontal ou vertical.|  
|[CMFCAutoHideButton::IsTop](#istop)||  
|[CMFCAutoHideButton::IsVisible](#isvisible)|Indique si le bouton est visible.|  
|[CMFCAutoHideButton::Move](#move)||  
|[CMFCAutoHideButton::OnDraw](#ondraw)|L'infrastructure appelle cette méthode au moment de dessiner le bouton masquer automatiquement.|  
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|L'infrastructure appelle cette méthode au moment de dessiner la bordure d'un bouton masquer automatiquement.|  
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|L'infrastructure appelle cette méthode au moment de remplir l'arrière-plan d'un bouton masquer automatiquement.|  
|[CMFCAutoHideButton::ReplacePane](#replacepane)||  
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Affiche ou masque associé [classe CDockablePane](../../mfc/reference/cdockablepane-class.md).|  
|[CMFCAutoHideButton::ShowButton](#showbutton)|Affiche ou masque le bouton masquer automatiquement.|  
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||  
  
## <a name="remarks"></a>Notes  
 La création, la `CMFCAutoHideButton` objet est attaché à un [classe CDockablePane](../../mfc/reference/cdockablepane-class.md). L'objet `CDockablePane` est masqué ou affiché quand l'utilisateur interagit avec l'objet `CMFCAutoHideButton`.  
  
 Par défaut, l'infrastructure crée automatiquement un `CMFCAutoHideButton` quand l'utilisateur active le bouton masquer automatiquement. L'infrastructure peut créer un élément d'une classe d'interface utilisateur personnalisée à la place de la classe `CMFCAutoHideButton`. Pour spécifier la classe d'interface utilisateur personnalisée que l'infrastructure doit utiliser, attribuez à la variable de membre statique `CMFCAutoHideBar::m_pAutoHideButtonRTS` la même valeur que la classe d'interface utilisateur personnalisée. Par défaut, cette variable a la valeur `CMFCAutoHideButton`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment construire un objet `CMFCAutoHideButton` et utiliser différentes méthodes de la classe `CMFCAutoHideButton`. L'exemple montre comment initialiser un objet `CMFCAutoHideButton` en utilisant sa méthode `Create`, afficher la classe `CDockablePane` associée et afficher le bouton masquer automatiquement.  
  
 [!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAutoHideButton`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxautohidebutton.h  
  
##  <a name="bringtotop"></a>  CMFCAutoHideButton::BringToTop  

  
```  
void BringToTop();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="create"></a>  CMFCAutoHideButton::Create  
 Crée et initialise un bouton Masquer automatiquement.  
  
```  
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,  
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pParentBar`  
 Pointeur vers la barre d’outils parente.  
  
 [in] `pAutoHideWnd`  
 Un pointeur vers un [CDockablePane](../../mfc/reference/cdockablepane-class.md) objet. Ce bouton Masquer automatiquement masque et montre que `CDockablePane`.  
  
 [in] `dwAlignment`  
 Une valeur qui spécifie l’alignement du bouton avec la fenêtre frame principale.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous créez un `CMFCAutoHideButton` de l’objet, vous devez associer le bouton Masquer automatiquement un spécifique `CDockablePane`. L’utilisateur peut utiliser le bouton Masquer automatiquement pour masquer et afficher les informations associé `CDockablePane`.  
  
 Le paramètre `dwAlignment` indique l’emplacement du bouton Masquer automatiquement dans l’application. Le paramètre peut avoir l’une des valeurs suivantes :  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="getalignment"></a>  CMFCAutoHideButton::GetAlignment  
 Récupère l'alignement du bouton masquer automatiquement.  
  
```  
DWORD GetAlignment() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A `DWORD` valeur qui contient l’alignement actuel du bouton Masquer automatiquement.  
  
### <a name="remarks"></a>Notes  
 L’alignement du bouton Masquer automatiquement indique où se trouve le bouton sur l’application. Il peut prendre l’une des valeurs suivantes :  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CRBS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="getautohidewindow"></a>  CMFCAutoHideButton::GetAutoHideWindow  
 Retourne le [CDockablePane](../../mfc/reference/cdockablepane-class.md) objet associé avec le bouton Masquer automatiquement.  
  
```  
CDockablePane* GetAutoHideWindow() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’associée `CDockablePane` objet.  
  
### <a name="remarks"></a>Notes  
 Pour associer un bouton Masquer automatiquement avec un `CDockablePane`, passez le `CDockablePane` en tant que paramètre à la [CMFCAutoHideButton::Create](#create) (méthode).  
  
##  <a name="getparenttoolbar"></a>  CMFCAutoHideButton::GetParentToolBar  

  
```  
CMFCAutoHideBar* GetParentToolBar();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getrect"></a>  CMFCAutoHideButton::GetRect  

  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getsize"></a>  CMFCAutoHideButton::GetSize  
 Détermine la taille du bouton masquer automatiquement.  
  
```  
CSize GetSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A `CSize` objet qui contient la taille du bouton.  
  
### <a name="remarks"></a>Notes  
 La taille calculée inclut la taille de la bordure du bouton Masquer automatiquement.  
  
##  <a name="gettextsize"></a>  CMFCAutoHideButton::GetTextSize  
 Retourne la taille de l'étiquette de texte du bouton masquer automatiquement.  
  
```  
virtual CSize GetTextSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objet qui contient la taille du texte pour le bouton Masquer automatiquement.  
  
##  <a name="isactive"></a>  CMFCAutoHideButton::IsActive  
 Indique si le bouton masquer automatiquement est actif.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le bouton Masquer automatiquement est actif ; `FALSE` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Un bouton Masquer automatiquement est active lorsque associé [classe CDockablePane](../../mfc/reference/cdockablepane-class.md) fenêtre est affichée.  
  
##  <a name="ishorizontal"></a>  CMFCAutoHideButton::IsHorizontal  
 Détermine si le bouton masquer automatiquement est horizontal ou vertical.  
  
```  
BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bouton est horizontal ; 0 dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Le framework définit l’orientation d’un [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) de l’objet lors de sa création.  Vous pouvez contrôler l’orientation en utilisant le `dwAlignment` paramètre dans le [CMFCAutoHideButton::Create](#create) (méthode).  
  
##  <a name="istop"></a>  CMFCAutoHideButton::IsTop  

  
```  
BOOL IsTop() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isvisible"></a>  CMFCAutoHideButton::IsVisible  
 Indique si le bouton Masquer automatiquement est visible.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le bouton est visible ; `FALSE` dans le cas contraire.  
  
##  <a name="ondraw"></a>  CMFCAutoHideButton::OnDraw  
 L'infrastructure appelle cette méthode au moment de dessiner le bouton masquer automatiquement.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez personnaliser l’apparence des boutons Masquer automatiquement dans votre application, créez une classe dérivée de `CMFCAutoHideButton`. Dans votre classe dérivée, substituez cette méthode.  
  
##  <a name="ondrawborder"></a>  CMFCAutoHideButton::OnDrawBorder  
 L'infrastructure appelle cette méthode au moment de dessiner la bordure d'un bouton masquer automatiquement.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `rectBounds`  
 Le rectangle englobant du bouton Masquer automatiquement.  
  
 [in] `rectBorderSize`  
 L’épaisseur de la bordure de chaque côté du bouton Masquer automatiquement.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez personnaliser la bordure de chaque bouton Masquer automatiquement dans votre application, créez une classe dérivée de la `CMFCAutoHideButton`. Dans votre classe dérivée, substituez cette méthode.  
  
##  <a name="onfillbackground"></a>  CMFCAutoHideButton::OnFillBackground  
 L'infrastructure appelle cette méthode au moment de remplir l'arrière-plan d'un bouton masquer automatiquement.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `rect`  
 Le rectangle englobant du bouton Masquer automatiquement.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez personnaliser l’arrière-plan de boutons Masquer automatiquement dans votre application, créez une classe dérivée de la `CMFCAutoHideButton`. Dans votre classe dérivée, substituez cette méthode.  
  
##  <a name="showattachedwindow"></a>  CMFCAutoHideButton::ShowAttachedWindow  
 Affiche ou masque associé [classe CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
```  
void ShowAttachedWindow(BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bShow`  
 Valeur booléenne qui spécifie si cette méthode affiche le fichier joint `CDockablePane`.  
  
##  <a name="showbutton"></a>  CMFCAutoHideButton::ShowButton  
 Affiche ou masque le bouton masquer automatiquement.  
  
```  
virtual void ShowButton(BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bShow`  
 Valeur booléenne qui spécifie s’il faut afficher le bouton Masquer automatiquement.  
  
##  <a name="move"></a>  CMFCAutoHideButton::Move  

  
```  
void Move(int nOffset);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nOffset`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="replacepane"></a>  CMFCAutoHideButton::ReplacePane  

  
```  
void ReplacePane(CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pNewBar`  
  
### <a name="remarks"></a>Notes  
  
##  <a name="unsetautohidemode"></a>  CMFCAutoHideButton::UnSetAutoHideMode  
 Désactivez le mode de masquage automatique.  
  
```  
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pFirstBarInGroup`  
 Pointeur vers la première barre du groupe.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="highlightbutton"></a>  CMFCAutoHideButton::HighlightButton  
 Met en surbrillance le bouton Masquer automatiquement.  
  
```  
virtual void HighlightButton(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Paramètres  
 `bHighlight`  
 Spécifie l’état du bouton de masquer nouvelle. `TRUE` Indique le bouton est mis en surbrillance, `FALSE` indique le bouton n’est pas mis en surbrillance.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ishighlighted"></a>  CMFCAutoHideButton::IsHighlighted  
 Retourne l’état de mise en surbrillance du bouton Masquer automatiquement.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` si le bouton Masquer automatiquement est mis en surbrillance ; sinon `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Cmfcautohidebar, classe](../../mfc/reference/cmfcautohidebar-class.md)   
 [CAutoHideDockSite, classe](../../mfc/reference/cautohidedocksite-class.md)
