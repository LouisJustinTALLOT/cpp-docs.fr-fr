---
title: Classe de CMFCColorMenuButton | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea9fddef1b032d1e17ea46229a992c23ca960822
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039022"
---
# <a name="cmfccolormenubutton-class"></a>Classe de CMFCColorMenuButton
La `CMFCColorMenuButton` classe prend en charge une commande de menu ou un bouton de barre d’outils qui démarre une boîte de dialogue de sélecteur de couleurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Construit un objet `CMFCColorMenuButton`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Active ou désactive un bouton « automatic » qui est positionné au-dessus des boutons de couleur normale. (Le bouton automatique standard du système est intitulé **automatique**.)|  
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Active l’affichage des couleurs spécifiques au document au lieu de couleurs système.|  
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Active ou désactive un bouton « autre » qui se trouve sous les boutons de couleur normale. (Le système standard porte le nom « autre » bouton **plus de couleurs**.)|  
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Permet de détacher un volet de couleur.|  
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Récupère la couleur automatique.|  
|[CMFCColorMenuButton::GetColor](#getcolor)|Récupère la couleur du bouton de l’actuelle.|  
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Récupère la couleur qui correspond à un ID de commande spécifiée.|  
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le framework lorsque la fenêtre parente change.|  
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Ouvre une boîte de dialogue de sélection de couleur.|  
|[CMFCColorMenuButton::SetColor](#setcolor)|Définit la couleur du bouton de couleur actuelle.|  
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Définit la couleur du bouton de menu couleur spécifiée.|  
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Définit un nouveau nom pour la couleur spécifiée.|  
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Définit le nombre de colonnes qui sont affichées par un `CMFCColorBar` objet.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Copie un autre bouton de barre d’outils sur le bouton en cours.|  
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Crée une boîte de dialogue de sélecteur de couleurs.|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Indique si les menus vides sont pris en charge.|  
|[CMFCColorMenuButton::OnDraw](#ondraw)|Appelé par l’infrastructure pour afficher une image sur un bouton.|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Appelé par le framework avant une `CMFCColorMenuButton` objet s’affiche dans la liste d’une boîte de dialogue de personnalisation de barre d’outils.|  
  
## <a name="remarks"></a>Notes  
 Pour remplacer le bouton de barre d’outils ou de la commande de menu d’origine avec une `CMFCColorMenuButton` d’objet, de créer le `CMFCColorMenuButton` objet, définissez tous les appropriées [CMFCColorBar classe](../../mfc/reference/cmfccolorbar-class.md) styles, puis appelez le `ReplaceButton` procédé de la [CMFCToolBar classe](../../mfc/reference/cmfctoolbar-class.md) classe. Si vous personnalisez une barre d’outils, appelez le [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) (méthode).  
  
 La boîte de dialogue de sélecteur de couleurs est créée lors du traitement de la [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) Gestionnaire d’événements. Le Gestionnaire d’événements informe le frame parent avec un `WM_COMMAND` message. Le `CMFCColorMenuButton` objet envoie l’ID de contrôle qui est affectée au bouton de barre d’outils ou de la commande de menu d’origine.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer et configurer un bouton de menu de couleur à l’aide de différentes méthodes de la `CMFCColorMenuButton` classe. Dans l’exemple, un `CPalette` objet est d’abord créé et ensuite utilisé pour construire un objet de la `CMFCColorMenuButton` classe. Le `CMFCColorMenuButton` objet est ensuite configuré en activant automatiquement et autres boutons et en définissant sa couleur et le nombre de colonnes. Ce code fait partie de la [exemple Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcolormenubutton.h  
  
##  <a name="cmfccolormenubutton"></a>  CMFCColorMenuButton::CMFCColorMenuButton  
 Construit un objet `CMFCColorMenuButton`.  
  
```  
CMFCColorMenuButton();

 
CMFCColorMenuButton(
    UINT uiCmdID,  
    LPCTSTR lpszText,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmdID*  
 Un ID de commande de bouton.  
  
 [in] *lpszText*  
 Le texte du bouton.  
  
 [in] *pPalette*  
 Pointeur vers la palette de couleurs du bouton.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Le premier constructeur est le constructeur par défaut. Couleur actuelle de l’objet et de couleur automatique sont initialisés à bleu (RVB (0, 0, 0)).  
  
 Le deuxième constructeur initialise le bouton de la couleur qui correspond à l’ID de commande spécifiée.  
  
##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom  
 Copie une [CMFCToolBarMenuButton classe](../../mfc/reference/cmfctoolbarmenubutton-class.md)-objet dérivé vers un autre.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *src*  
 Bouton de la source à copier.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour copier les objets qui sont dérivés de la `CMFCColorMenuButton` objet.  
  
##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu  
 Crée une boîte de dialogue de sélecteur de couleurs.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Objet qui représente une boîte de dialogue de sélecteur de couleurs.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par le framework lorsque l’utilisateur appuie sur un bouton de menu de couleur.  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton  
 Active ou désactive un bouton « automatic » qui est positionné au-dessus des boutons de couleur normale. (Le bouton automatique standard du système est intitulé **automatique**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszLabel*  
 Spécifie le texte du bouton qui s’affiche lorsque le bouton est automatique.  
  
 [in] *automatiqueCouleur*  
 Spécifie une nouvelle couleur automatique.  
  
 [in] *bActivez*  
 Spécifie si le bouton est automatique ou non.  
  
### <a name="remarks"></a>Notes  
 Le bouton automatique s’applique à la couleur par défaut en cours.  
  
##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors  
 Active l’affichage des couleurs spécifiques au document au lieu de couleurs système.  
  
```  
void EnableDocumentColors(
    LPCTSTR lpszLabel,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszLabel*  
 Spécifie le texte du bouton.  
  
 [in] *bActivez*  
 `TRUE` Pour afficher les couleurs spécifiques au document ou `FALSE` pour afficher les couleurs système.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour afficher les couleurs du document en cours ou la palette de couleurs système lorsque l’utilisateur clique sur un bouton de menu de couleur.  
  
##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton  
 Active ou désactive un bouton « autre » qui se trouve sous les boutons de couleur normale. (Le système standard porte le nom « autre » bouton **plus de couleurs**.)  
  
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
 Spécifiez `TRUE` pour afficher les `CMFCColorDialog` boîte de dialogue, ou `FALSE` pour afficher la boîte de dialogue couleur système standard.  
  
 [in] *bActivez*  
 Spécifiez `TRUE` pour afficher le bouton « autre » ; sinon, `FALSE`. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff  
 Permet de détacher un volet de couleur.  
  
```  
void EnableTearOff(
    UINT uiID,  
    int nVertDockColumns=-1,  
    int nHorzDockRows=-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiID*  
 Spécifie l’ID du volet détachable.  
  
 [in] *nVertDockColumns*  
 Spécifie le nombre de colonnes dans le volet ancré verticalement de couleur dans un état détachable.  
  
 [in] *nHorzDockRows*  
 Spécifie le nombre de lignes du volet ancré horizontalement de couleur dans un état détachable.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour activer la fonctionnalité « détacher » pour le volet de couleur qui s’affiche lorsque le `CMFCColorMenuButton` bouton est enfoncé.  
  
##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor  
 Récupère la couleur automatique.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur de couleur RVB qui représente la couleur automatique.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour obtenir la couleur automatique est définie par [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).  
  
##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor  
 Récupère la couleur du bouton de l’actuelle.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur du bouton.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID  
 Récupère la couleur qui correspond à un ID de commande spécifiée.  
  
```  
static COLORREF GetColorByCmdID(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmdID*  
 Un ID de commande.  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur qui correspond à l’ID de commande spécifiée.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode lorsque vous avez plusieurs boutons de couleur dans une application. Lorsque l’utilisateur clique sur un bouton de couleur, le bouton envoie son ID de commande dans un message WM_COMMAND avec son parent. Le `GetColorByCmdID` méthode utilise l’ID de commande pour récupérer la couleur correspondante.  
  
##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed  
 Indique si les menus vides sont pris en charge.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les menus vides sont autorisées ; Sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Menus vides sont pris en charge par défaut. Substituez cette méthode pour modifier ce comportement dans une classe dérivée.  
  
##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd  
 Appelé par le framework lorsque la fenêtre parente change.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWndParent*  
 Pointeur vers la nouvelle fenêtre parent.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw  
 Appelé par l’infrastructure pour afficher une image sur un bouton.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz=TRUE,  
    BOOL bCustomizeMode=FALSE,  
    BOOL bHighlight=FALSE,  
    BOOL bDrawBorder=TRUE,  
    BOOL bGrayDisabledButtons=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *rect*  
 Un rectangle qui délimite la zone à être redessiné.  
  
 [in] *pImages*  
 Pointe vers une liste d’images de barre d’outils.  
  
 [in] *bHorz*  
 `TRUE` Pour spécifier que la barre d’outils est dans un état ancré horizontal ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.  
  
 [in] *bCustomizeMode*  
 `TRUE` Pour spécifier que l’application est en mode de personnalisation ; dans le cas contraire, `FALSE`. La valeur par défaut est `FALSE`.  
  
 [in] *bHighlight*  
 `TRUE` Pour spécifier que le bouton est mis en surbrillance ; dans le cas contraire, `FALSE`. La valeur par défaut est `FALSE`.  
  
 [in] *bDrawBorder*  
 `TRUE` Pour spécifier que la bordure du bouton est affichée ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.  
  
 [in] *bGrayDisabledButtons*  
 `TRUE` Pour spécifier que désactivé les boutons sont grisées (grisé) dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList  
 Appelé par le framework avant une `CMFCColorMenuButton` objet s’affiche dans la liste d’une boîte de dialogue de personnalisation de barre d’outils.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *rect*  
 Un rectangle qui englobe le bouton doit être dessiné.  
  
 [in] *bSelected*  
 `TRUE` Spécifie que le bouton est dans l’état sélectionné ; dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur du bouton.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par l’infrastructure lorsqu’un `CMFCColorMenuButton` objet s’affiche dans la zone de liste pendant le processus de personnalisation de barre d’outils.  
  
##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog  
 Ouvre une boîte de dialogue de sélection de couleur.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *colorDefault*  
 La couleur par défaut qui est sélectionnée dans la boîte de dialogue couleur.  
  
 [out] *colorRes*  
 Retourne la couleur de l’utilisateur sélectionne dans la boîte de dialogue couleur.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’utilisateur sélectionne une nouvelle couleur ; Sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous cliquez sur le bouton de menu, appelez cette méthode pour ouvrir une boîte de dialogue couleur. Si la valeur de retour est différente de zéro, la couleur que l’utilisateur sélectionne est stockée dans le *colorRes* paramètre. Utilisez le [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) méthode pour basculer entre la boîte de dialogue couleurs standard et le [CMFCColorDialog classe](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue.  
  
##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor  
 Définit la couleur du bouton de couleur actuelle.  
  
```  
virtual void SetColor(
    COLORREF clr,  
    BOOL bNotify=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *clr*  
 Une valeur de couleur RVB.  
  
 [in] *bNotify*  
 `TRUE` Pour appliquer le *clr* couleur de paramètre à n’importe quel bouton de menu associé ou d’un bouton de barre d’outils ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour modifier la couleur du bouton de couleur actuelle. Si le *bNotify* le paramètre est différente de zéro, la couleur du bouton correspondant sur une barre d’outils ou un menu contextuel associé est remplacée par la couleur spécifiée par le *clr* paramètre.  
  
##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID  
 Définit la couleur du bouton de menu couleur spécifiée.  
  
```  
static void SetColorByCmdID(
    UINT uiCmdID,  
    COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmdID*  
 L’ID de ressource d’un bouton de menu de couleur.  
  
 [in] *couleur*  
 Une valeur de couleur RVB.  
  
##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName  
 Définit un nouveau nom pour la couleur spécifiée.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *couleur*  
 La valeur RVB de la couleur dont le nom change.  
  
 [in] *strName*  
 Le nouveau nom de la couleur.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber  
 Définit le nombre de colonnes à afficher dans un contrôle de sélection de couleur ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) objet).  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nColumns*  
 Le nombre de colonnes à afficher.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [Classe de CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Classe de CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [CMFCColorButton, classe](../../mfc/reference/cmfccolorbutton-class.md)
