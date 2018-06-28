---
title: Classe de CMFCColorButton | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd59f9575fdbde798b46bee343f7f7724968a478
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038310"
---
# <a name="cmfccolorbutton-class"></a>Classe de CMFCColorButton
Le `CMFCColorButton` et [CMFCColorBar classe](../../mfc/reference/cmfccolorbar-class.md) classes sont utilisées ensemble pour implémenter un contrôle de sélecteur de couleur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Construit un nouveau `CMFCColorButton` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Active ou désactive un bouton « automatic » qui est positionné au-dessus des boutons de couleur normale. (Le bouton automatique standard du système est intitulé **automatique**.)|  
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Active ou désactive un bouton « autre » qui se trouve sous les boutons de couleur normale. (Le système standard porte le nom « autre » bouton **plus de couleurs**.)|  
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Récupère la couleur automatique.|  
|[CMFCColorButton::GetColor](#getcolor)|Récupère la couleur d’un bouton.|  
|[CMFCColorButton::SetColor](#setcolor)|Définit la couleur d’un bouton.|  
|[CMFCColorButton::SetColorName](#setcolorname)|Définit un nom de couleur.|  
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Définit le nombre de colonnes dans la boîte de dialogue de sélecteur de couleurs.|  
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Spécifie une liste de couleurs spécifique au document qui sont affichés dans la boîte de dialogue de sélecteur de couleurs.|  
|[CMFCColorButton::SetPalette](#setpalette)|Spécifie une palette de couleurs d’affichage standard.|  
|[CMFCColorButton::SizeToContent](#sizetocontent)|Modifie la taille du contrôle de bouton, en fonction de sa taille de texte et image.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Indique si le bouton de couleur actuelle est affiché dans le style visuel de Windows XP.|  
|[CMFCColorButton::OnDraw](#ondraw)|Appelé par l’infrastructure pour afficher une image du bouton.|  
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Appelé par l’infrastructure pour afficher la bordure du bouton.|  
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Appelé par l’infrastructure pour afficher un rectangle de focus lorsque le bouton a le focus.|  
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Appelé par l’infrastructure lors de la boîte de dialogue de sélecteur de couleurs est sur le point d’être affiché.|  
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Initialise le `m_pPalette` protégé par les membres de données à la palette spécifiée ou dans la palette du système par défaut.|  
|[CMFCColorButton::UpdateColor](#updatecolor)|Appelé par le framework lorsque l’utilisateur sélectionne une couleur de la palette de la boîte de dialogue de sélecteur de couleurs.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|`m_bAltColorDlg`|Valeur booléenne. Si `TRUE`, l’infrastructure affiche le [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue de couleur lorsque la *autres* bouton est activé, ou si `FALSE`, la boîte de dialogue de couleur système. La valeur par défaut est `TRUE`. Pour plus d’informations, consultez [CMFCColorButton::EnableOtherButton](#enableotherbutton).|  
|`m_bAutoSetFocus`|Valeur booléenne. Si `TRUE`, le framework définit le focus sur le menu de couleur lorsque le menu s’affiche, ou si `FALSE`, ne change pas le focus. La valeur par défaut est `TRUE`.|  
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Indique si le mode de personnalisation est activé pour le bouton de couleur.|  
|`m_Color`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur. Contient la couleur actuellement sélectionnée.|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur. Contient la couleur actuellement sélectionnée par défaut.|  
|`m_Colors`|A [CArray](../../mfc/reference/carray-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeurs. Contient les couleurs disponibles.|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeurs. Contient les couleurs du document actif.|  
|`m_nColumns`|Entier. Contient le nombre de colonnes à afficher dans la grille de couleurs dans un menu de sélection de couleur.|  
|`m_pPalette`|Un pointeur vers un [CPalette](../../mfc/reference/cpalette-class.md). Contient les couleurs qui sont disponibles dans le menu de sélection de couleur actuelle.|  
|`m_pPopup`|Un pointeur vers un [CMFCColorPopupMenu classe](../../mfc/reference/cmfccolorpopupmenu-class.md) objet. Le menu de sélection de couleur qui s’affiche lorsque vous cliquez sur le bouton de couleur.|  
|`m_strAutoColorText`|Chaîne. L’étiquette du bouton « automatique » dans un menu de sélection de couleur.|  
|`m_strDocColorsText`|Chaîne. L’étiquette du bouton dans un menu de sélection de couleur qui affiche les couleurs du document.|  
|`m_strOtherText`|Chaîne. L’étiquette du bouton « autre » dans un menu de sélection de couleur.|  
  
## <a name="remarks"></a>Notes  
 Par défaut, la `CMFCColorButton` classe se comporte comme un bouton de commande qui ouvre une boîte de dialogue de sélecteur de couleurs. La boîte de dialogue de sélecteur de couleurs contient un tableau de boutons de petite couleur et un bouton « autre » qui affiche un sélecteur de couleurs personnalisées. (Le système standard porte le nom « autre » bouton **plus de couleurs**.) Lorsqu’un utilisateur sélectionne une nouvelle couleur, le `CMFCColorButton` objet reflète la modification et affiche la couleur sélectionnée.  
  
 Créer un contrôle de bouton de couleur directement dans votre code, ou à l’aide de la **ClassWizard** outil et un modèle de boîte de dialogue. Si vous créez un contrôle de bouton de couleur directement, ajouter un `CMFCColorButton` variable à votre application, puis appelez le constructeur et `Create` méthodes de la `CMFCColorButton` objet. Si vous utilisez la **ClassWizard**, ajoutez un `CButton` variable à votre application, puis modifiez le type de la variable de `CButton` à `CMFCColorButton`.  
  
 La boîte de dialogue de sélecteur de couleurs ( [CMFCColorBar classe](../../mfc/reference/cmfccolorbar-class.md)) est affiché par le [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) méthode lorsque l’infrastructure appelle la `OnLButtonDown` Gestionnaire d’événements. Le [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) méthode peut être substituée pour prendre en charge la sélection de couleurs personnalisées.  
  
 Le `CMFCColorButton` objet informe son parent de modification d’une couleur en l’envoyant un `WM_COMMAND | BN_CLICKED` notification. Le parent utilise la [CMFCColorButton::GetColor](#getcolor) pour récupérer la couleur actuelle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer un bouton de couleur à l’aide de différentes méthodes de la `CMFCColorButton` classe. Les méthodes de définir la couleur du bouton couleur et le nombre de colonnes et activer automatique et les autres boutons. Cet exemple fait partie de la [exemple de démonstration de barre d’état](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcolorbutton.h  
  
##  <a name="cmfccolorbutton"></a>  CMFCColorButton::CMFCColorButton  
 Construit un nouveau `CMFCColorButton` objet.  
  
```  
CMFCColorButton();
```  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton  
 Activer ou désactiver le bouton « automatic » d’un contrôle de sélecteur de couleurs et définir la couleur automatique (par défaut).  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszLabel*  
 Spécifie l’automatique texte du bouton.  
  
 [in] *automatiqueCouleur*  
 Une valeur RVB qui spécifie la couleur de valeur par défaut du bouton automatique.  
  
 [in] *bActivez*  
 Spécifie si le bouton automatique est activé ou désactivé.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton  
 Activer ou désactiver le bouton « autre » qui apparaît sous les boutons de couleur normale.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszLabel*  
 Spécifie le texte du bouton.  
  
 [in] *bAltColorDlg*  
 Spécifie si le [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue ou la boîte de dialogue couleur est ouvert lorsque l’utilisateur clique sur le bouton.  
  
 [in] *bActivez*  
 Spécifie si le bouton « autre » est activé ou désactivé.  
  
### <a name="remarks"></a>Notes  
 Cliquez sur le bouton « autre » pour afficher une boîte de dialogue couleur. Si le *bAltColorDlg* paramètre est `TRUE`, le [CMFCColorDialog classe](../../mfc/reference/cmfccolordialog-class.md) est affichée ; sinon, la boîte de dialogue couleur s’affiche.  
  
##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor  
 Récupère la couleur actuelle automatique (par défaut).  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur RVB représentant la couleur automatique.  
  
### <a name="remarks"></a>Notes  
 La couleur automatique est définie par le [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) (méthode).  
  
##  <a name="getcolor"></a>  CMFCColorButton::GetColor  
 Récupère la couleur actuellement sélectionnée.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme  
 Indique si le bouton de couleur actuelle est affiché dans le style visuel de Windows XP.  
  
```  
BOOL IsDrawXPTheme() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si les styles visuels sont pris en charge et le bouton de couleur actuelle s’affiche dans le style visuel de Windows XP ; dans le cas contraire, `FALSE`.  
  
##  <a name="m_benabledincustomizemode"></a>  CMFCColorButton::m_bEnabledInCustomizeMode  
 Définit un bouton de couleur pour le mode de personnalisation.  
  
```  
BOOL m_bEnabledInCustomizeMode;  
```  
  
### <a name="remarks"></a>Notes  
 Si vous devez ajouter un bouton de couleur à la page d’une boîte de dialogue Personnalisation (ou autoriser l’utilisateur à effectuer une autre sélection de couleur au cours de personnalisation), activer le bouton en définissant le `m_bEnabledInCustomizeMode` membre à `TRUE`. Par défaut, ce membre a la valeur `FALSE`.  
  
##  <a name="ondraw"></a>  CMFCColorButton::OnDraw  
 Appelé par l’infrastructure pour restituer une image du bouton.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointe vers le contexte de périphérique qui est utilisé pour restituer l’image du bouton.  
  
 [in] *rect*  
 Un rectangle qui englobe le bouton.  
  
 [in] *uiState*  
 Spécifie l’état visuel du bouton.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour personnaliser le processus de rendu.  
  
##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder  
 Appelé par l’infrastructure pour afficher la bordure du bouton.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointe vers le contexte de périphérique utilisé pour dessiner la bordure.  
  
 [in] *rectClient*  
 Un rectangle dans le contexte de périphérique spécifié par le le *pDC* paramètre qui définit les limites du bouton doit être dessiné.  
  
 [in] *uiState*  
 Spécifie l’état visuel du bouton.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour personnaliser l’apparence de bordure du bouton de couleur.  
  
##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect  
 Appelé par l’infrastructure pour afficher un rectangle de focus lorsque le bouton a le focus.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointe vers le contexte de périphérique utilisé pour dessiner le rectangle de focus.  
  
 [in] *rectClient*  
 Un rectangle dans le contexte de périphérique spécifié par le *pDC* paramètre qui définit les limites du bouton.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour personnaliser l’apparence du rectangle de focus.  
  
##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup  
 Appelé avant l’affichage de la barre de couleur contextuelle.  
  
```  
virtual void OnShowColorPopup();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette  
 Initialise le `m_pPalette` protégé par les membres de données à la palette spécifiée ou dans la palette du système par défaut.  
  
```  
void RebuildPalette(CPalette* pPal);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *pPal*|Un pointeur vers une palette logique ou `NULL`. Si `NULL`, la palette système par défaut est utilisée.|  
  
##  <a name="setcolor"></a>  CMFCColorButton::SetColor  
 Spécifie la couleur du bouton.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *couleur*  
 Une valeur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName  
 Spécifie le nom d’une couleur.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *couleur*  
 La valeur de couleur RVB.  
  
 [in] *strName*  
 Nom de la couleur.  
  
### <a name="remarks"></a>Notes  
 La liste des noms de couleurs est globale par application. Par conséquent, cette méthode transfère ses paramètres à [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).  
  
##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber  
 Définit le nombre de colonnes qui sont affichées dans le tableau de couleurs qui est présenté à l’utilisateur pendant le processus de sélection de couleur de l’utilisateur.  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nColumns*  
 Spécifie le nombre de colonnes.  
  
### <a name="remarks"></a>Notes  
 L’utilisateur peut sélectionner une couleur à partir d’une barre de couleurs contextuelle qui affiche un tableau de couleurs prédéfinies. Utilisez cette méthode pour définir le nombre de colonnes dans la table.  
  
##  <a name="setdocumentcolors"></a>  CMFCColorButton::SetDocumentColors  
 Spécifie un jeu de couleurs et le nom. Le jeu de couleurs est affiché en utilisant un [CMFCColorBar classe](../../mfc/reference/cmfccolorbar-class.md) objet.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszLabel*  
 Spécifie l’étiquette à afficher avec le jeu de couleurs du document.  
  
 [in] *lstColors*  
 Une référence à une liste de valeurs RVB.  
  
### <a name="remarks"></a>Notes  
 A `CMFCColorButton` objet conserve une liste de valeurs RVB qui sont transférées à un [CMFCColorBar classe](../../mfc/reference/cmfccolorbar-class.md) objet. Lorsque la barre de couleur s’affiche, ces couleurs sont affichées dans une section spéciale dont l’étiquette est spécifiée par le *lpszLabel* paramètre.  
  
##  <a name="setpalette"></a>  CMFCColorButton::SetPalette  
 Spécifie les couleurs standards à afficher sur la barre de couleur contextuelle.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pPalette*  
 Pointeur vers une palette de couleurs.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="sizetocontent"></a>  CMFCColorButton::SizeToContent  
 Redimensionne le contrôle bouton pour s’ajuster à son type text et image.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bCalcOnly*  
 Si elle est différente de zéro, la nouvelle taille du contrôle est calculée, mais la taille réelle n’est pas modifiée.  
  
### <a name="return-value"></a>Valeur de retour  
 A `CSize` objet qui spécifie une nouvelle taille du contrôle bouton.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="updatecolor"></a>  CMFCColorButton::UpdateColor  
 Appelé par le framework lorsque l’utilisateur sélectionne une couleur dans la barre de couleur qui s’affiche lorsque l’utilisateur clique sur le bouton de couleur.  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *couleur*  
 Une couleur sélectionnée par l’utilisateur.  
  
### <a name="remarks"></a>Notes  
 Le `UpdateColor` fonction modifie les couleurs du bouton sélectionné et informe son parent en envoyant un message WM_COMMAND avec notification BN_CLICKED standard. Utilisez le [CMFCColorButton::GetColor](#getcolor) pour récupérer la couleur sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCButton](../../mfc/reference/cmfcbutton-class.md)   
 [Classe de CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette (classe)](../../mfc/reference/cpalette-class.md)   
 [CArray (classe)](../../mfc/reference/carray-class.md)   
 [CList (classe)](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)
