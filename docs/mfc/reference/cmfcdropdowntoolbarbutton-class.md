---
title: Classe de CMFCDropDownToolbarButton | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c65cf3070f199b013a0e85c1ae56764174fdc33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372532"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Classe de CMFCDropDownToolbarButton
Type de bouton de barre d'outils qui se comporte comme un bouton normal lorsque l'utilisateur clique dessus. Toutefois, il ouvre une barre d’outils déroulante ( [CMFCDropDownToolBar classe](../../mfc/reference/cmfcdropdowntoolbar-class.md) si l’utilisateur appuie et appuie sur le bouton de barre d’outils.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Construit un objet `CMFCDropDownToolbarButton`.|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils sur le bouton en cours. (Substitue [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCDropDownToolbarButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Ouvre une barre d’outils de la liste déroulante.|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Copie le texte à partir du bouton de barre d’outils à un menu. (Substitue [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Récupère la barre d’outils de liste déroulante qui est associé au bouton.|  
|`CMFCDropDownToolbarButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Détermine si la barre d’outils de la liste déroulante est actuellement ouverte.|  
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Détermine si le bouton peut être affiché avec une bordure étendue. (Substitue [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|  
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique spécifié et l’état d’ancrage. (Substitue [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|`CMFCDropDownToolbarButton::OnCancelMode`|Appelé par l’infrastructure pour gérer la [WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) message. (Substitue `CMCToolBarButton::OnCancelMode`.)|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le framework lorsque le bouton est inséré dans une barre d’outils. (Substitue [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Appelé par le framework lorsque l’utilisateur clique sur le bouton de la souris. (Substitue [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Appelé par le framework lorsque l’utilisateur relâche le bouton de la souris. (Substitue [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|  
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Appelé par l’infrastructure lors de la barre d’outils parent gère un `WM_HELPHITTEST` message. (Substitue [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modifie le menu fourni lors de l’application affiche un menu contextuel dans la barre d’outils parente. (Substitue [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|  
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner le bouton en utilisant les options et les styles spécifiés. (Substitue [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Appelé par l’infrastructure pour dessiner le bouton dans le **commandes** volet de la **personnaliser** boîte de dialogue. (Substitue [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Lit de cet objet à partir d’une archive ou écrit dans une archive. (Substitue [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Définit la commande par défaut par le framework lorsqu’un utilisateur clique sur le bouton.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Spécifie la durée pendant laquelle un utilisateur doit maintenez le bouton de la souris avant que la barre d’outils de la liste déroulante s’affiche.|  
  
## <a name="remarks"></a>Notes  
 A `CMFCDropDownToolBarButton` diffère d’un bouton ordinaire car il a une petite flèche dans le coin inférieur droit du bouton. Une fois que l’utilisateur sélectionne un bouton dans la barre d’outils de la liste déroulante, l’infrastructure affiche son icône sur le bouton de barre d’outils de niveau supérieur (le bouton avec la flèche située dans le coin inférieur droit).  
  
 Pour plus d’informations sur la façon d’implémenter une barre d’outils de la liste déroulante, consultez [CMFCDropDownToolBar classe](../../mfc/reference/cmfcdropdowntoolbar-class.md).  
  
 Le `CMFCDropDownToolBarButton` objet peut être exporté vers un [CMFCToolBarMenuButton classe](../../mfc/reference/cmfctoolbarmenubutton-class.md) de l’objet et affiché sous la forme d’un bouton de menu avec un menu contextuel.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdropdowntoolbar.h  
  
##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom  
 Copie les propriétés d’un autre bouton de barre d’outils sur le bouton en cours.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `src`  
 Une référence au bouton source à partir duquel copier.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour copier un autre bouton de barre d’outils pour ce bouton de barre d’outils. `src` doit être de type `CMFCDropDownToolbarButton`.  
  
##  <a name="cmfcdropdowntoolbarbutton"></a>  CMFCDropDownToolbarButton::CMFCDropDownToolbarButton  
 Construit un objet `CMFCDropDownToolbarButton`.  
  
```  
CMFCDropDownToolbarButton();

 
CMFCDropDownToolbarButton(
    LPCTSTR lpszName,  
    CMFCDropDownToolBar* pToolBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszName`  
 Texte du bouton par défaut.  
  
 [in] `pToolBar`  
 Un pointeur vers le `CMFCDropDownToolBar` objet s’affiche lorsque l’utilisateur appuie sur le bouton.  
  
### <a name="remarks"></a>Notes  
 La deuxième surcharge du constructeur de copie sur le bouton de liste déroulante le premier bouton à partir de la barre d’outils qui `pToolBar` spécifie.  
  
 En règle générale, un bouton de barre d’outils de la liste déroulante utilise le texte à partir du bouton des derniers fichiers utilisé dans la barre d’outils qui `pToolBar` spécifie. Elle utilise le texte spécifié par `lpszName` lorsque le bouton est converti en un bouton de menu ou s’affiche dans le **commandes** onglet de la **personnaliser** boîte de dialogue. Pour plus d’informations sur la **personnaliser** boîte de dialogue, consultez [CMFCToolBarsCustomizeDialog classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCDropDownToolbarButton` classe. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]  
  
##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar  
 Ouvre une barre d’outils de la liste déroulante.  
  
```  
BOOL DropDownToolbar(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWnd`  
 La fenêtre parente de l’image de la liste déroulante, ou `NULL` à utiliser la fenêtre parente du bouton de barre d’outils de la liste déroulante.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le [CMFCDropDownToolbarButton::OnClick](#onclick) appelle cette méthode pour ouvrir la barre d’outils de la liste déroulante lorsque l’utilisateur appuie sur et appuie sur le bouton de barre d’outils.  
  
 Cette méthode crée la barre d’outils de la liste déroulante à l’aide de la [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) (méthode). Si la barre d’outils parent est ancré verticalement, cette méthode positionne la barre d’outils de la liste déroulante soit vers le côté gauche ou droit de la barre d’outils parent, en fonction de l’ajustement. Sinon, cette méthode positionne la barre d’outils de la liste déroulante située sous la barre d’outils parent.  
  
 Cette méthode échoue si `pWnd` est `NULL` et le bouton de barre d’outils de la liste déroulante n’est pas une fenêtre parente.  
  
##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton  
 Copie le texte à partir du bouton de barre d’outils à un menu.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `menuButton`  
 Une référence au bouton de menu cible.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle l’implémentation de classe de base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), puis les ajoute au bouton de menu cible un menu contextuel qui contient chaque élément de menu de barre d’outils de ce bouton. Cette méthode n’ajoute pas les sous-menus dans le menu contextuel.  
  
 Cette méthode échoue si la barre d’outils parent, `m_pToolBar`, est `NULL` ou l’implémentation de classe de base retourne `FALSE`.  
  
##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar  
 Récupère la barre d’outils de liste déroulante qui est associé au bouton.  
  
```  
CMFCToolBar* GetDropDownToolBar() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La barre d’outils de liste déroulante qui est associé au bouton.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne le `m_pToolBar` membre de données.  
  
##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown  
 Détermine si la barre d’outils de la liste déroulante est actuellement ouverte.  
  
```  
BOOL IsDropDown() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la barre d’outils de la liste déroulante est actuellement ouvert ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure ouvre la barre d’outils de la liste déroulante à l’aide de la [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) (méthode). Le framework ferme la barre d’outils de la liste déroulante lorsque l’utilisateur appuie sur le bouton gauche de la souris dans la zone non cliente de la barre d’outils de la liste déroulante.  
  
##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize  
 Détermine si le bouton peut être affiché avec une bordure étendue.  
  
```  
virtual BOOL IsExtraSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bouton de barre d’outils peut être affiché avec une bordure étendue ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les bordures étendus, consultez [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).  
  
##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay  
 Spécifie la durée pendant laquelle un utilisateur doit maintenez le bouton de la souris avant que la barre d’outils de la liste déroulante s’affiche.  
  
```  
static UINT m_uiShowBarDelay;  
```  
  
### <a name="remarks"></a>Notes  
 Délai d’attente est mesuré en millisecondes. La valeur par défaut est de 500 ms. Vous pouvez définir un autre délai en modifiant la valeur de ce membre de données partagée.  
  
##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize  
 Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique spécifié et l’état d’ancrage.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Le contexte de périphérique qui affiche le bouton.  
  
 [in] `sizeDefault`  
 La taille par défaut du bouton.  
  
 [in] `bHorz`  
 L’état d’ancrage de la barre d’outils parente. Ce paramètre est `TRUE` si la barre d’outils est ancré horizontalement ou est flottant, ou `FALSE` si la barre d’outils est ancré verticalement.  
  
### <a name="return-value"></a>Valeur de retour  
 A `SIZE` structure qui contient les dimensions du bouton, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) en ajoutant la largeur de la flèche déroulante à la dimension horizontale de la taille du bouton.  
  
##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd  
 Appelé par le framework lorsque le bouton est inséré dans une barre d’outils.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParent`  
 La nouvelle fenêtre parent.  
  
### <a name="remarks"></a>Notes  
 Cette méthode substitue l’implémentation de classe de base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en désactivant l’étiquette de texte ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) et en définissant le [ CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) et [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) membres de données `FALSE`.  
  
##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick  
 Appelé par le framework lorsque l’utilisateur clique sur le bouton de la souris.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWnd`  
 La fenêtre parente de la barre d’outils.  
  
 [in] `bDelay`  
 `TRUE` Si le message doit être géré avec un délai.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bouton traite le message de clic. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), en mettant à jour l’état de la barre d’outils de la liste déroulante.  
  
 Lorsqu’un utilisateur clique sur le bouton de barre d’outils, cette méthode crée un minuteur qui attend le délai spécifié par le [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) membre de données, puis de barre d’outils s’ouvre la liste déroulante à l’aide de la [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) (méthode). Cette méthode ferme la barre d’outils de la liste déroulante de la deuxième fois que l’utilisateur clique sur le bouton de barre d’outils.  
  
##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp  
 Appelé par le framework lorsque l’utilisateur relâche le bouton de la souris.  
  
```  
virtual BOOL OnClickUp();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bouton traite le message de clic. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), en mettant à jour l’état de la barre d’outils de la liste déroulante.  
  
 Cette méthode arrête la minuterie de la barre d’outils de la liste déroulante si elle est active. Il ferme la barre d’outils de la liste déroulante si elle est ouverte.  
  
 Pour plus d’informations sur la barre d’outils de la liste déroulante et le minuteur de la barre d’outils de la liste déroulante, consultez [CMFCDropDownToolbarButton::OnClick](#onclick).  
  
##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp  
 Appelé par l’infrastructure lors de la barre d’outils parent gère un `WM_HELPHITTEST` message.  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWnd`  
 La fenêtre parente de la barre d’outils.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bouton traite le message d’aide ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) en appelant le [CMFCDropDownToolbarButton::OnClick](#onclick) méthode avec `bDelay` la valeur `FALSE` . Cette méthode retourne la valeur retournée par [CMFCDropDownToolbarButton::OnClick](#onclick).  
  
 Pour plus d’informations sur la `WM_HELPHITTEST message, see` [TN028 : prise en charge d’aide contextuelle](../../mfc/tn028-context-sensitive-help-support.md).  
  
##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu  
 Modifie le menu fourni lors de l’application affiche un menu contextuel dans la barre d’outils parente.  
  
```  
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pMenu`  
 Le menu à personnaliser.  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) en désactivant les éléments suivants :  
  
- **Copier l’Image du bouton**  
  
- **Apparence du bouton**  
  
- **Image**  
  
- **Text**  
  
- **Image et texte**  
  
 Substituez cette méthode pour modifier le menu contextuel affichée par l’infrastructure dans le mode de personnalisation.  
  
##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw  
 Appelé par l’infrastructure pour dessiner le bouton en utilisant les options et les styles spécifiés.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Le contexte de périphérique qui affiche le bouton.  
  
 [in] `rect`  
 Le rectangle englobant du bouton.  
  
 [in] `pImages`  
 La collection d’images de barre d’outils qui est associée au bouton.  
  
 [in] `bHorz`  
 L’état d’ancrage de la barre d’outils parente. Ce paramètre est `TRUE` lorsque le bouton est ancré horizontalement et `FALSE` lorsque le bouton est ancré verticalement.  
  
 [in] `bCustomizeMode`  
 Spécifie si la barre d’outils est en mode de personnalisation. Ce paramètre est `TRUE` lorsque la barre d’outils est en mode de personnalisation et `FALSE` lorsque la barre d’outils n’est pas en mode de personnalisation.  
  
 [in] `bHighlight`  
 Spécifie si le bouton est mis en surbrillance. Ce paramètre est `TRUE` lorsque le bouton est mis en surbrillance et `FALSE` lorsque le bouton n’est pas mis en surbrillance.  
  
 [in] `bDrawBorder`  
 Spécifie si le bouton doit afficher sa bordure. Ce paramètre est `TRUE` lorsque le bouton doit afficher sa bordure et `FALSE` lorsque le bouton ne doit pas afficher sa bordure.  
  
 [in] `bGrayDisabledButtons`  
 Spécifie s’il faut assombrissent boutons désactivés ou utiliser la collection d’images désactivé. Ce paramètre est `TRUE` lorsque les boutons désactivés doit être grisé et `FALSE` lorsque cette méthode doit utiliser la collection d’images désactivé.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour personnaliser le dessin de bouton de barre d’outils.  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList  
 Appelé par l’infrastructure pour dessiner le bouton dans le **commandes** volet de la **personnaliser** boîte de dialogue.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Le contexte de périphérique qui affiche le bouton.  
  
 [in] `rect`  
 Le rectangle englobant du bouton.  
  
 [in] `bSelected`  
 Indique si le bouton est sélectionné. Si ce paramètre est `TRUE`, le bouton est sélectionné. Si ce paramètre est `FALSE`, le bouton n’est pas sélectionné.  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur, en pixels, du bouton sur le contexte de périphérique spécifié.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par la boîte de dialogue de personnalisation ( **commandes** onglet) lorsque le bouton doit s’afficher sur la zone de liste owner-draw.  
  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) en modifiant l’étiquette de texte du bouton pour le nom du bouton (autrement dit, la valeur de le `lpszName` paramètre que vous avez transmise le constructeur).  
  
##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize  
 Lit de cet objet à partir d’une archive ou écrit dans une archive.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `ar`  
 Le `CArchive` objet à partir duquel ou auquel vous souhaitez sérialiser.  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) par la sérialisation de l’ID de ressource de la barre d’outils parente. Lorsque l’archive est le chargement ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) retourne une valeur différente de zéro), cette méthode définit le `m_pToolBar` membre de données pour la barre d’outils qui contient l’ID de ressource sérialisé.  
  
##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand  
 Définit la commande par défaut par le framework lorsqu’un utilisateur clique sur le bouton.  
  
```  
void SetDefaultCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 ID de la commande par défaut.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour spécifier une commande par défaut exécutée par l’infrastructure lorsque l’utilisateur clique sur le bouton. Un élément avec l’ID de commande spécifié par `uiCmd` doit se trouver dans la barre d’outils de la liste déroulante parente.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [Classe de CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Classe de CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [Procédure pas à pas : placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)



