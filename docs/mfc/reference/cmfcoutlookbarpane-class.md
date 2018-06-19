---
title: Classe de CMFCOutlookBarPane | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe72b43d8930e77bea274e20e5f150cc93617c20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374082"
---
# <a name="cmfcoutlookbarpane-class"></a>Classe de CMFCOutlookBarPane
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Un contrôle dérivé [CMFCToolBar classe](../../mfc/reference/cmfctoolbar-class.md) qui peuvent être insérées dans une barre Outlook ( [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)). Le volet de barre Outlook contient une colonne de grands boutons. L'utilisateur peut faire défiler vers le haut ou vers le bas la liste des boutons si elle est plus grande que le volet. Lorsque l'utilisateur détache un volet de barre Outlook de la barre Outlook, il peut flotter ou s'ancrer à la fenêtre frame principale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Constructeur par défaut.|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](#addbutton)|Ajoute un bouton dans le volet de barre Outlook.|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Détermine si le volet peut être ancré à un autre volet ou une fenêtre frame. (Substitue [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|  
|`CMFCOutlookBarPane::CanBeRestored`|Détermine si le système peut restaurer une barre d’outils à son état d’origine après la personnalisation. (Substitue [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|Libère les ressources utilisées par les images dans le volet de barre Outlook.|  
|[CMFCOutlookBarPane::Create](#create)|Crée le volet de barre Outlook.|  
|`CMFCOutlookBarPane::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|`CMFCOutlookBarPane::Dock`|Appelé par l’infrastructure pour ancrer le volet de barre Outlook. (Substitue `CPane::Dock`.)|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Spécifie si les flèches de défilement dans le volet de barre Outlook passer de la liste des boutons de page, ou par le bouton.|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Retourne la couleur de texte normal de (non sélectionnées) du volet de barre Outlook.|  
|`CMFCOutlookBarPane::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Détermine s’il existe une image d’arrière-plan chargée pour le volet de barre Outlook.|  
|`CMFCOutlookBarPane::IsChangeState`|Détermine si un volet flottant peut être ancré. (Substitue `CPane::IsChangeState`.)|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Détermine si la bordure du bouton est grisée lorsqu’un bouton est mis en surbrillance et une image d’arrière-plan est affichée.|  
|`CMFCOutlookBarPane::OnBeforeFloat`|Appelé par l’infrastructure lorsqu’un volet est sur float. (Substitue [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Supprime le bouton qui a un ID de commande spécifiée.|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaure l'état initial d'une barre d'outils. (Substitue [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Définit la couleur d’arrière-plan.|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Définit l’image d’arrière-plan.|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Réinitialise le volet de barre Outlook à l’ensemble d’origine des boutons.|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Définit le nombre de pixels de la marge intérieure qui entoure les boutons dans le volet de barre Outlook.|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Définit les couleurs de texte standard et mis en surbrillance dans le volet de barre Outlook.|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Définit la couleur transparente pour le volet de barre Outlook.|  
|`CMFCOutlookBarPane::SmartUpdate`|Utilisé en interne pour mettre à jour de la barre Outlook. (Substitue `CMFCToolBar::SmartUpdate`.)|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Spécifie les éléments de menu contextuel sont affichées dans le mode de personnalisation.|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Supprime tous les boutons du volet de barre Outlook. (Substitue [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la façon d’implémenter une barre Outlook, consultez [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Pour obtenir un exemple d’une barre Outlook, consultez l’exemple de projet OutlookDemo.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCOutlookBarPane` classe. L’exemple montre comment créer un volet de barre Outlook, activer le mode de défilement de la page, activez l’ancrage et définir la couleur d’arrière-plan de la barre Outlook. Cet extrait de code fait partie de la [Outlook plusieurs vues, exemple](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxoutlookbarpane.h  
  
##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton  
 Ajoute un bouton dans le volet de barre Outlook.  
  
```  
BOOL AddButton(
    UINT uiImage,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    UINT uiImage,  
    UINT uiLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    LPCTSTR szBmpFileName,  
    LPCTSTR szLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HBITMAP hBmp,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HICON hIcon,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiImage`  
 Spécifie l’identificateur de ressource d’une image bitmap.  
  
 [in] `lpszLabel`  
 Spécifie le texte du bouton.  
  
 [in] `iIdCommand`  
 Spécifie l’ID. du contrôle de bouton  
  
 [in] `iInsertAt`  
 Spécifie l’index de base zéro dans la page de la barre outlook au niveau duquel insérer le bouton.  
  
 [in] `uiLabel`  
 Un ID de ressource de chaîne.  
  
 [in] `szBmpFileName`  
 Spécifie le nom du fichier d’image de disque à charger.  
  
 [in] `szLabel`  
 Spécifie le texte du bouton.  
  
 [in] `hBmp`  
 Un descripteur de bitmap d’un bouton.  
  
 [in] `hIcon`  
 Handle vers l’icône d’un boutons.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si un bouton a été ajouté avec succès ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour insérer un nouveau bouton dans la page d’une barre Outlook. L’image du bouton peut être chargé à partir des ressources d’application ou à partir d’un fichier de disque.  
  
 Si l’ID de page spécifiée par `uiPageID` est -1, le bouton est inséré dans la première page.  
  
 Si l’index spécifié par `iInsertAt` est -1, le bouton est ajouté à la fin de la page.  
  
##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll  
 Libère les ressources utilisées par les images dans le volet de barre Outlook.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle directement [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), qui est appelée sur les images qui sont utilisées par le volet de barre Outlook.  
  
##  <a name="create"></a>  CMFCOutlookBarPane::Create  
 Crée le volet de barre Outlook.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pParentWnd`  
 Spécifie la fenêtre parente du contrôle de volet de barre Outlook. Ne doit pas être `NULL`.  
  
 [in] `dwStyle`  
 Style de fenêtre.  Pour obtenir la liste des styles de fenêtre, consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] `uiID`  
 L’ID du contrôle. Doit être unique pour activer l’enregistrement de l’état du contrôle.  
  
 [in] `dwControlBarStyle`  
 Spécifie les styles spéciaux qui définissent le comportement du contrôle de volet de barre Outlook lorsqu’elle est détachée de la barre Outlook.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Pour construire un `CMFCOutlookBarPane` de l’objet, d’abord appeler le constructeur, puis appelez `Create`, qui crée le contrôle de volet de barre Outlook et l’attache à le `CMFCOutlookBarPane` objet.  
  
 Pour plus d’informations sur `dwControlBarStyle` consultez [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems  
 Spécifie les éléments de menu contextuel sont affichées dans le mode de personnalisation.  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pButton`  
 Pointeur vers un bouton de barre d’outils sur lequel un utilisateur a cliqué.  
  
 [in] `pPopup`  
 Pointeur vers le menu contextuel.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` si le menu contextuel doit être affichée ; sinon `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour modifier le menu contextuel standard framework affichée par l’infrastructure dans le mode de personnalisation.  
  
 L’implémentation par défaut vérifie le mode de personnalisation ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) et si elle est définie sur `TRUE`, désactive tous les éléments de menu de raccourci, à l’exception **supprimer**. Ensuite, il le transmet simplement les paramètres d’entrée `CMFCToolBar::EnableContextMenuItems`.  
  
> [!NOTE]
> *Menu contextuel* est un synonyme de menu contextuel.  
  
##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode  
 Spécifie si les flèches de défilement dans le volet de barre Outlook passer à la liste des boutons de page par page, ou en bouton.  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bPageScroll`  
 Si `TRUE`, activer le mode de défilement de la page. Si `FALSE`, désactiver le mode de défilement de la page.  
  
##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor  
 Retourne la mise à jour (autrement dit, non sélectionnées) couleur du texte du volet de barre Outlook.  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur de texte actuelle avec une valeur de couleur RVB.  
  
### <a name="remarks"></a>Notes  
 Utilisez [CMFCOutlookBarPane::SetTextColor](#settextcolor) pour définir la couleur de texte (régulière et sélectionné) en cours de la barre Outlook. Vous pouvez obtenir la couleur du texte par défaut en appelant le [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) fonctionne avec le `COLOR_WINDOW` index.  
  
##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture  
 Détermine s’il existe une image d’arrière-plan chargée pour le volet de barre Outlook.  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` s’il existe image d’arrière-plan à afficher ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez ajouter une image d’arrière-plan en appelant [CMFCOutlookBarPane::SetBackImage](#setbackimage) (fonction).  
  
 S’il n’existe aucune image d’arrière-plan, l’arrière-plan est peint avec une couleur spécifiée à l’aide de [CMFCOutlookBarPane::SetBackColor](#setbackcolor).  
  
##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight  
 Détermine si la bordure du bouton est grisée lorsqu’un bouton est mis en surbrillance et une image d’arrière-plan est affichée.  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si les bordures du bouton sont grisées ; dans le cas contraire `FALSE`.  
  
##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons  
 Supprime tous les boutons du volet de barre Outlook.  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton  
 Supprime le bouton qui a un ID de commande spécifiée.  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIdCommand`  
 Spécifie l’ID de commande d’un bouton à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le bouton a été supprimé avec succès ; `FALSE` si l’ID de commande spécifié n’est pas valide.  
  
##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor  
 Définit la couleur d’arrière-plan de la barre Outlook.  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `color`  
 Spécifie la couleur d’arrière-plan.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour définir la couleur d’arrière-plan actuelle de la barre Outlook. La couleur d’arrière-plan est utilisée uniquement si aucune image d’arrière-plan.  
  
##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage  
 Définit l’image d’arrière-plan.  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiImageID`  
 Spécifie l’ID de ressource d’image.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour définir l’Outlook image d’arrière-plan de la barre. La liste des images d’arrière-plan est gérée par l’embedded [CMFCToolBarImages classe](../../mfc/reference/cmfctoolbarimages-class.md) objet.  
  
##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState  
 Réinitialise le volet de barre Outlook à l’ensemble d’origine des boutons.  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode restaure les boutons de barre Outlook dans le jeu d’origine. Cette méthode est comparable à `CMFCOutlookBarPane::RestoreOriginalstate`, mais elle ne déclenche pas d’un nouveau dessin du volet de barre Outlook.  
  
##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace  
 Définit le nombre de pixels de la marge intérieure qui entoure les boutons dans le volet de barre Outlook.  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor  
 Définit les couleurs de texte standard et mis en surbrillance dans le volet de barre Outlook.  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `clrRegText`  
 Spécifie la nouvelle couleur non sélectionné.  
  
 [in] `clrSelText`  
 Spécifie la nouvelle couleur pour le texte sélectionné.  
  
##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor  
 Définit la couleur transparente pour le volet de barre Outlook.  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 `color`  
 Spécifie la nouvelle couleur transparente.  
  
### <a name="remarks"></a>Notes  
 Couleur transparente est nécessaire pour afficher des images transparentes. Toute occurrence de cette couleur dans une image est peint avec la couleur d’arrière-plan à la place.  Il n’existe aucune fusion des images d’arrière-plan et de premier plan.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
