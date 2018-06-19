---
title: CPropertySheet (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
dev_langs:
- C++
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7b49aba6ea5d2397baa0dc72f36b2693810fbeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377460"
---
# <a name="cpropertysheet-class"></a>CPropertySheet (classe)
Représente des feuilles de propriétés, également appelées boîtes de dialogue à onglets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPropertySheet : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Construit un objet `CPropertySheet`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CPropertySheet::AddPage](#addpage)|Ajoute une page à la feuille de propriétés.|  
|[CPropertySheet::Construct](#construct)|Construit un objet `CPropertySheet`.|  
|[CPropertySheet::Create](#create)|Affiche une feuille de propriétés non modale.|  
|[CPropertySheet::DoModal](#domodal)|Affiche une feuille de propriétés modale.|  
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Indique si la feuille de propriétés utilise des onglets empilées ou de défilement.|  
|[CPropertySheet::EndDialog](#enddialog)|Met fin à la feuille de propriétés.|  
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Récupère l’index de la page active de la feuille de propriétés.|  
|[CPropertySheet::GetActivePage](#getactivepage)|Retourne l’objet de la page active.|  
|[CPropertySheet::GetPage](#getpage)|Récupère un pointeur vers la page spécifiée.|  
|[CPropertySheet::GetPageCount](#getpagecount)|Récupère le nombre de pages dans la feuille de propriétés.|  
|[CPropertySheet::GetPageIndex](#getpageindex)|Récupère l’index de la page spécifiée de la feuille de propriétés.|  
|[CPropertySheet::GetTabControl](#gettabcontrol)|Récupère un pointeur vers un contrôle onglet.|  
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Convertit les unités de boîte de dialogue d’un rectangle en unités de l’écran.|  
|[CPropertySheet::OnInitDialog](#oninitdialog)|Substituez pour augmenter l’initialisation feuille des propriétés.|  
|[CPropertySheet::PressButton](#pressbutton)|Simule le choix du bouton spécifié dans une feuille de propriétés.|  
|[CPropertySheet::RemovePage](#removepage)|Supprime une page de la feuille de propriétés.|  
|[CPropertySheet::SetActivePage](#setactivepage)|Définit par programmation l’objet de la page active.|  
|[CPropertySheet::SetFinishText](#setfinishtext)|Définit le texte du bouton Terminer.|  
|[CPropertySheet::SetTitle](#settitle)|Définit la légende de la feuille de propriétés.|  
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Active les boutons de l’Assistant.|  
|[Fonction CPropertySheet::SetWizardMode](#setwizardmode)|Active le mode de l’Assistant.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPropertySheet::m_psh](#m_psh)|Les fenêtres [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) structure. Fournit l’accès aux paramètres de feuille de propriétés de base.|  
  
## <a name="remarks"></a>Notes  
 Une feuille de propriétés se compose d’un `CPropertySheet` objet et un ou plusieurs [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objets. L’infrastructure affiche une feuille de propriétés sous la forme d’une fenêtre avec un ensemble d’index de l’onglet et une zone qui contient la page actuellement sélectionnée. L’utilisateur navigue vers une page spécifique à l’aide de l’onglet approprié.  
  
 `CPropertySheet` prend en charge les [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) structure introduite dans [!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)] et NT de Windows 2000. La structure contient des indicateurs supplémentaires et les membres qui prennent en charge l’à l’aide d’une image d’arrière-plan « filigrane ».  
  
 Pour afficher ces nouvelles images automatiquement dans votre objet de feuille de propriétés, passer les valeurs valides pour les images bitmap et la palette dans l’appel à [CPropertySheet::Construct](#construct) ou [CPropertySheet::CPropertySheet](#cpropertysheet).  
  
 Même si `CPropertySheet` n’est pas dérivé [CDialog](../../mfc/reference/cdialog-class.md), gestion un `CPropertySheet` objet est similaire à la gestion un `CDialog` objet. Par exemple, la création d’une feuille de propriétés requiert la construction de deux parties : appelez le constructeur, puis appelez [DoModal](#domodal) d’une feuille de propriétés modale ou [créer](#create) pour une feuille de propriétés non modale. `CPropertySheet` a deux types de constructeurs : [CPropertySheet::Construct](#construct) et [CPropertySheet::CPropertySheet](#cpropertysheet).  
  
 Lorsque vous construisez un `CPropertySheet` de l’objet, certaines [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) peuvent provoquer une exception de première chance de se produire. Ainsi, à partir du système lors de la tentative de modification du style de la feuille de propriétés avant la création de la feuille. Pour éviter cette exception, assurez-vous que vous définissez les styles suivants lorsque vous créez votre `CPropertySheet`:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 Les styles suivants sont facultatifs et n’entraîne pas l’exception de première chance :  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 N’importe quel autre `Window Styles` sont interdites et vous ne devez pas activer les.  
  
 Échanger des données entre un `CPropertySheet` objet et un objet externe est similaire à échanger des données avec un `CDialog` objet. La différence importante est que les paramètres d’une feuille de propriétés sont en général, les variables de membre de la `CPropertyPage` objets plutôt que du `CPropertySheet` objet lui-même.  
  
 Vous pouvez créer un type de boîte de dialogue onglet appelé un Assistant qui se compose d’une feuille de propriétés avec une séquence de pages de propriétés qui guide l’utilisateur à travers les étapes d’une opération, comme la définition d’un périphérique ou la création d’un bulletin d’informations. Dans une boîte de dialogue Assistant-onglet, les pages de propriétés n’ont pas de tabulations, et uniquement une page de propriété est visible à la fois. En outre, au lieu d’avoir **OK** et **appliquer maintenant** a de boutons, une boîte de dialogue Assistant-onglet un **précédent** bouton, un **suivant** ou  **Terminer** bouton, un **Annuler** bouton et un **aide** bouton.  
  
 Pour créer une boîte de dialogue du type de l’Assistant, suivez les mêmes étapes que vous suivez pour créer une feuille de propriétés standard, mais appelle [SetWizardMode](#setwizardmode) avant d’appeler [DoModal](#domodal). Pour activer les boutons de l’Assistant, appelez [SetWizardButtons](#setwizardbuttons), à l’aide des indicateurs pour personnaliser leur fonction et l’apparence. Pour activer la **Terminer** bouton, appelez [SetFinishText](#setfinishtext) une fois que l’utilisateur a une incidence sur la dernière page de l’Assistant.  
  
 Pour plus d’informations sur l’utilisation de `CPropertySheet` , consultez l’article [feuilles de propriétés et Pages de propriétés](../../mfc/property-sheets-and-property-pages-in-mfc.md). En outre, consultez l’article de la Base de connaissances Q146916 : comment faire : créer un CPropertySheet non modale avec les boutons Standard et que l’article Q300606 : comment faire : concevoir une feuille de propriétés MFC redimensionnable.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdlgs.h  
  
##  <a name="addpage"></a>  CPropertySheet::AddPage  
 Ajoute la page fournie avec la plus à droite de l’onglet dans la feuille de propriétés.  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Paramètres  
 `pPage`  
 Pointe vers la page à ajouter à la feuille de propriétés. Ne peut pas être **NULL**.  
  
### <a name="remarks"></a>Notes  
 Ajouter des pages à la feuille de propriétés dans l’ordre de gauche à droite que vous souhaitez qu’ils apparaissent.  
  
 `AddPage` Ajoute le [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) de l’objet à le `CPropertySheet` objet de la liste des pages, mais ne crée pas réellement de la fenêtre de la page. Le framework diffère la création de la fenêtre de la page jusqu'à ce que l’utilisateur sélectionne cette page.  
  
 Lorsque vous ajoutez une page de propriété à l’aide de `AddPage`, le `CPropertySheet` est le parent de la `CPropertyPage`. Pour accéder à la feuille de propriétés à partir de la page de propriétés, appelez [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).  
  
 Il n’est pas nécessaire d’attendre la création de la fenêtre de feuille de propriétés pour appeler `AddPage`. En règle générale, vous appellerez `AddPage` avant d’appeler [DoModal](#domodal) ou [créer](#create).  
  
 Si vous appelez `AddPage` après l’affichage de la page de propriétés, la ligne d’onglets reflètent la page qui vient d’être ajoutée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]  
  
##  <a name="construct"></a>  CPropertySheet::Construct  
 Construit un objet `CPropertySheet`.  
  
```  
void Construct(
    UINT nIDCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
void Construct(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
void Construct(
    UINT nIDCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);

 
void Construct(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDCaption`  
 ID de la légende à utiliser pour la feuille de propriétés.  
  
 `pParentWnd`  
 Pointeur vers la fenêtre parente de la feuille de propriétés. Si **NULL**, la fenêtre parente sera la fenêtre principale de l’application.  
  
 `iSelectPage`  
 L’index de la page qui sera initialement le premier. Valeur par défaut est la première page ajoutée à la feuille.  
  
 `pszCaption`  
 Pointeur vers une chaîne qui contient la légende à utiliser pour la feuille de propriétés. Ne peut pas être **NULL**.  
  
 `hbmWatermark`  
 Handle vers le bitmap de la limite de la page de propriétés.  
  
 `hpalWatermark`  
 Handle vers la palette de la bitmap de filigrane et/ou la bitmap de l’en-tête.  
  
 `hbmHeader`  
 Handle vers le bitmap de l’en-tête de la page de propriétés.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre si un des constructeurs de classe n’a pas déjà été appelé. Par exemple, appeler `Construct` lorsque vous déclarez ou allouer des tableaux de `CPropertySheet` objets. Dans le cas de tableaux, vous devez appeler `Construct` pour chaque membre du tableau.  
  
 Pour afficher la feuille de propriétés, appelez [DoModal](#domodal) ou [créer](#create). La chaîne contenue dans le premier paramètre sera placée dans la barre de légende pour la feuille de propriétés.  
  
 Vous pouvez afficher des images en filigrane et/ou d’en-tête automatiquement si vous utilisez les prototypes troisième ou quatrième de `Construct`, répertoriés ci-dessus et que vous transmettez les valeurs valides pour le `hbmWatermark`, `hpalWatermark`, et/ou `hbmHeader` paramètres.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre dans quelles circonstances vous appelleriez `Construct`.  
  
 [!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]  
  
##  <a name="cpropertysheet"></a>  CPropertySheet::CPropertySheet  
 Construit un objet `CPropertySheet`.  
  
```  
CPropertySheet();

 
explicit CPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
explicit CPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
CPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);

 
CPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDCaption`  
 ID de la légende à utiliser pour la feuille de propriétés.  
  
 `pParentWnd`  
 Pointe vers la fenêtre parente de la feuille de propriétés. Si **NULL**, la fenêtre parente sera la fenêtre principale de l’application.  
  
 `iSelectPage`  
 L’index de la page qui sera initialement le premier. Valeur par défaut est la première page ajoutée à la feuille.  
  
 `pszCaption`  
 Pointe vers une chaîne qui contient la légende à utiliser pour la feuille de propriétés. Ne peut pas être **NULL**.  
  
 `hbmWatermark`  
 Handle vers l’image d’arrière-plan de la feuille de propriétés.  
  
 `hpalWatermark`  
 Handle vers la palette de la bitmap de filigrane et/ou la bitmap de l’en-tête.  
  
 `hbmHeader`  
 Handle vers le bitmap de l’en-tête de la page de propriétés.  
  
### <a name="remarks"></a>Notes  
 Pour afficher la feuille de propriétés, appelez [DoModal](#domodal) ou [créer](#create). La chaîne contenue dans le premier paramètre sera placée dans la barre de légende pour la feuille de propriétés.  
  
 Si vous avez plusieurs paramètres (par exemple, si vous utilisez un tableau), utilisez [construire](#construct) au lieu de `CPropertySheet`.  
  
 Vous pouvez afficher des images en filigrane et/ou d’en-tête automatiquement si vous utilisez les prototypes troisième ou quatrième de `CPropertySheet`ci-dessus, et vous transmettez les valeurs valides pour le `hbmWatermark`, `hpalWatermark`, et/ou `hbmHeader` paramètres.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]  
  
##  <a name="create"></a>  CPropertySheet::Create  
 Affiche une feuille de propriétés non modale.  
  
```  
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pParentWnd`  
 Pointe vers la fenêtre parente. Si **NULL**, le bureau est le parent.  
  
 `dwStyle`  
 Styles de fenêtre pour la feuille de propriétés. Pour obtenir une liste complète des styles disponibles, consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 `dwExStyle`  
 Styles de fenêtre étendus pour la feuille de propriétés. Pour obtenir une liste complète des styles disponibles, consultez [Styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la feuille de propriétés est créée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’appel à **créer** peut se trouver dans le constructeur, ou vous pouvez l’appeler une fois que le constructeur est appelé.  
  
 Le style par défaut, exprimé en passant la valeur -1 comme `dwStyle`, est en réalité **WS_SYSMENU&#124;**`WS_POPUP`**&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_ VISIBLE**. La valeur par défaut extended style de fenêtre, exprimée en passant 0 comme `dwExStyle`, est en réalité **WS_EX_DLGMODALFRAME**.  
  
 Le **créer** fonction membre retourne immédiatement après la création de la feuille de propriétés. Pour détruire la feuille de propriétés, appelez [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).  
  
 Feuilles de propriétés non modale affichées par un appel à **créer** n’ont pas de boutons OK, Annuler, appliquer et aide comme des feuilles de propriétés modale. Boutons de votre choix doit être créé par l’utilisateur.  
  
 Pour afficher une feuille de propriétés modale, appelez [DoModal](#domodal) à la place.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]  
  
##  <a name="domodal"></a>  CPropertySheet::DoModal  
 Affiche une feuille de propriétés modale.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `IDOK` ou `IDCANCEL` si la fonction a réussi ; sinon, 0 ou de-1. Si la feuille de propriétés a été établie comme un Assistant (consultez [SetWizardMode](#setwizardmode)), `DoModal` retourne `ID_WIZFINISH` ou `IDCANCEL`.  
  
### <a name="remarks"></a>Notes  
 La valeur de retour correspond à l’ID du contrôle qui a fermé la feuille de propriétés. Une fois que cette fonction retourne, le windows correspondant à la feuille de propriétés et toutes les pages seront détruit. Les objets eux-mêmes existe toujours. En règle générale, vous allez extraire des données à partir de la [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objets après `DoModal` retourne `IDOK`.  
  
 Pour afficher une feuille de propriétés non modale, appelez [créer](#create) à la place.  
  
 Lorsqu’une page de propriétés est créée à partir de la ressource de boîte de dialogue correspondante, cela peut provoquer une exception de première chance. Cela résulte de la page de propriétés modifier le style de la ressource de boîte de dialogue du style requis avant la création de la page. Étant donné que les ressources sont généralement en lecture seule, cela provoque une exception. Le système gère l’exception et effectue une copie de la ressource modifiée. L’exception de première chance peut donc être ignorée.  
  
> [!NOTE]
>  Cette exception doit être gérée par le système d’exploitation si vous compilez avec le modèle de gestion des exceptions asynchrones. Pour plus d’informations sur les modèles de gestion des exceptions, consultez [/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md). Dans ce cas, n’imbriquez pas les appels à `CPropertySheet::DoModal` avec un bloc try-catch de C++ dans lequel catch gère toutes les exceptions, par exemple, `catch (...)`. Ce bloc ne gère pas l’exception destinée au système d’exploitation et un comportement imprévisible cause. Toutefois, vous pouvez utiliser sans risque C++ de gestion des exceptions avec les types d’exceptions spécifiques ou de la gestion structurée des exceptions dans lequel l’exception de Violation d’accès est passée par le biais du système d’exploitation.  
  
 Pour éviter de générer cette exception de première chance, vous pouvez manuellement garantit que la feuille de propriétés dispose de la bonne [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles). Vous devez définir les styles suivants pour une feuille de propriétés :  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 Vous pouvez utiliser les styles facultatifs suivants sans provoquer une exception de première chance :  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 Désactiver tous les autres styles de Windows, car ils ne sont pas compatibles avec les feuilles de propriétés. Ce Conseil ne s’applique pas aux styles étendus. La définition appropriée de ces styles standards garantit que la feuille de propriétés ne dispose pas être modifiés et permet d’éviter la génération de l’exception de première chance.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::AddPage](#addpage).  
  
##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs  
 Indique si les lignes d’onglets dans une feuille de propriétés de la pile.  
  
```  
void EnableStackedTabs(BOOL bStacked);
```  
  
### <a name="parameters"></a>Paramètres  
 `bStacked`  
 Indique si les onglets empilées sont activés dans la feuille de propriétés. Désactiver des lignes empilées de balises en définissant `bStacked` à **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Par défaut, si une feuille de propriétés comporte plusieurs onglets que ceux qui tiennent dans une ligne unique de la largeur de la feuille de propriétés, les onglets seront empileront sur plusieurs lignes. Pour utiliser le défilement des onglets plutôt que des onglets empilement, appelez `EnableStackedTabs` avec `bStacked` la valeur **FALSE** avant d’appeler [DoModal](#domodal) ou [créer](#create).  
  
 Vous devez appeler `EnableStackedTabs` lorsque vous créez une modale ou une feuille de propriétés non modale. Pour intégrer ce style dans un `CPropertySheet`-la classe dérivée, écrivez un gestionnaire de messages pour `WM_CREATE`. Dans la version substituée de [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), appelez **EnableStackedTabs (FALSE)** avant d’appeler l’implémentation de classe de base.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]  
  
##  <a name="enddialog"></a>  CPropertySheet::EndDialog  
 Met fin à la feuille de propriétés.  
  
```  
void EndDialog(int nEndID);
```  
  
### <a name="parameters"></a>Paramètres  
 *nEndID*  
 Identificateur à utiliser comme valeur de retour de la feuille de propriétés.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par le framework lorsque le OK, annuler ou le bouton Fermer est activé. Appel de cette fonction membre, si un événement produit, qui doit fermer la feuille de propriétés.  
  
 Cette fonction membre est utilisée uniquement avec une boîte de dialogue modale.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::PressButton](#pressbutton).  
  
##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex  
 Obtient le numéro d’index de la page active de la fenêtre feuille de propriétés, puis utilise le numéro d’index retourné comme paramètre pour `GetPage`.  
  
```  
int GetActiveIndex() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le numéro d’index de la page active.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage  
 Récupère la page active de la fenêtre feuille de propriétés.  
  
```  
CPropertyPage* GetActivePage() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la page active.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction membre pour effectuer une action sur la page active.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]  
  
##  <a name="getpage"></a>  CPropertySheet::GetPage  
 Retourne un pointeur vers la page spécifiée dans cette feuille de propriétés.  
  
```  
CPropertyPage* GetPage(int nPage) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nPage`  
 Index de la page souhaitée, en commençant à 0. Doit être entre 0 et inférieur au nombre de pages dans la feuille de propriétés, incluse.  
  
### <a name="return-value"></a>Valeur de retour  
 Le pointeur vers la page correspondant à la `nPage` paramètre.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).  
  
##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount  
 Détermine le nombre de pages actuellement dans la feuille de propriétés.  
  
```  
int GetPageCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de pages dans la feuille de propriétés.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).  
  
##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex  
 Récupère le numéro d’index de la page spécifiée dans la feuille de propriétés.  
  
```  
int GetPageIndex(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Paramètres  
 `pPage`  
 Pointe vers la page avec l’index doit être recherché. Ne peut pas être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Le numéro d’index d’une page.  
  
### <a name="remarks"></a>Notes  
 Par exemple, vous utiliseriez `GetPageIndex` pour obtenir l’index de page pour pouvoir utiliser [SetActivePage](#setactivepage) ou [GetPage](#getpage).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl  
 Récupère un pointeur vers un contrôle onglet d’effectuer une action spécifique au contrôle onglet (autrement dit, pour utiliser une des API dans [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).  
  
```  
CTabCtrl* GetTabControl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un contrôle onglet.  
  
### <a name="remarks"></a>Notes  
 Par exemple, appelez cette fonction membre si vous souhaitez ajouter des images bitmap à chacun des onglets lors de l’initialisation.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]  
  
##  <a name="m_psh"></a>  CPropertySheet::m_psh  
 Une structure dont les membres stockent les caractéristiques de [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546).  
  
### <a name="remarks"></a>Notes  
 Utiliser cette structure pour initialiser l’apparence de la feuille de propriétés une fois qu’il est construit mais avant qu’il est affiché avec la [DoModal](#domodal) fonction membre. Par exemple, définissez la `dwSize` membre `m_psh` à la taille souhaitée pour que la feuille de propriétés.  
  
 Pour plus d’informations sur cette structure, y compris une liste de ses membres, consultez **PROPSHEETHEADER** dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]  
  
##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect  
 Convertit les unités de boîte de dialogue d’un rectangle en unités de l’écran.  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `lpRect`  
 Pointe vers un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure ou [CRect](../../atl-mfc-shared/reference/crect-class.md) coordonne l’objet qui contient la boîte de dialogue à convertir.  
  
### <a name="remarks"></a>Notes  
 Unités de boîte de dialogue sont exprimées dans l’unité de base de la boîte de dialogue actuelle dérivée de la largeur moyenne et la hauteur des caractères de la police utilisée pour le texte de la boîte de dialogue. Une unité horizontale est un quart de l’unité de largeur de la base de la boîte de dialogue et une unité verticale est un huitième de l’unité de base de hauteur de la boîte de dialogue.  
  
 Le [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) fonction Windows retourne des informations sur la taille de la police système, mais vous pouvez spécifier une police différente pour chaque feuille de propriétés si vous utilisez la **DS_SETFONT** de style dans le fichier de définition de ressource. Le [MapDialogRect](http://msdn.microsoft.com/library/windows/desktop/ms645502) fonction Windows, décrite dans le SDK Windows et utilise la police appropriée pour cette boîte de dialogue.  
  
 Le `MapDialogRect` fonction membre remplace les unités de boîte de dialogue de `lpRect` avec écran unités (pixels) afin que le rectangle peut être utilisé pour créer une boîte de dialogue ou de positionner un contrôle dans une zone.  
  
##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog  
 Les remplacements pour augmenter l’initialisation feuille des propriétés.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Spécifie si l’application a défini le focus d’entrée à un des contrôles dans la feuille de propriétés. Si **OnInitDialog** retourne différente de zéro, Windows définit le focus d’entrée sur le premier contrôle dans la feuille de propriétés. L’application peut retourner 0 uniquement si elle a défini explicitement le focus d’entrée à un des contrôles dans la feuille de propriétés.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée en réponse à la **WM_INITDIALOG** message. Ce message est envoyé à la feuille de propriétés lors de la [créer](#create) ou [DoModal](#domodal) appels, qui se produisent immédiatement avant l’affichage de la feuille de propriétés.  
  
 Remplacez cette fonction membre, si vous avez besoin effectuer un traitement spécial lors de l’initialisation de la feuille de propriétés. Dans la version substituée, commencer par appeler la classe de base `OnInitDialog` mais ne pas tenir compte de sa valeur de retour. Vous allez normalement retourner **TRUE** à partir de votre fonction membre substitué.  
  
 Vous n’avez pas besoin d’une entrée de table des messages pour cette fonction membre.  
  
##  <a name="pressbutton"></a>  CPropertySheet::PressButton  
 Simule le choix du bouton spécifié dans une feuille de propriétés.  
  
```  
void PressButton(int nButton);
```  
  
### <a name="parameters"></a>Paramètres  
 `nButton`  
 nButton : identifie le bouton. Ce paramètre peut être une des valeurs suivantes :  
  
- **PSBTN_BACK** choisit le bouton précédent.  
  
- **PSBTN_NEXT** choisit le bouton suivant.  
  
- **PSBTN_FINISH** choisit le bouton Terminer.  
  
- **PSBTN_OK** choisit le bouton OK.  
  
- **PSBTN_APPLYNOW** choisit le bouton Appliquer.  
  
- **PSBTN_CANCEL** choisit le bouton Annuler.  
  
- **PSBTN_HELP** choisit le bouton aide.  
  
### <a name="remarks"></a>Notes  
 Consultez [PSM_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb774597) pour plus d’informations sur le message Pressbutton du Kit de développement logiciel Windows.  
  
 Un appel à `PressButton` n’envoie pas le [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) notification à partir d’une page de propriétés à l’infrastructure. Pour envoyer cette notification, appelez [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]  
  
##  <a name="removepage"></a>  CPropertySheet::RemovePage  
 Supprime une page de la feuille de propriétés et détruit la fenêtre associée.  
  
```  
void RemovePage(CPropertyPage* pPage);  
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>Paramètres  
 `pPage`  
 Pointe vers la page à supprimer de la feuille de propriétés. Ne peut pas être `NULL`.  
  
 `nPage`  
 Index de la page à supprimer. Doit être entre 0 et inférieur au nombre de pages dans la feuille de propriétés, incluse.  
  
### <a name="remarks"></a>Notes  
 Le [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objet lui-même n’est pas détruit tant que le propriétaire de la `CPropertySheet` fenêtre est fermée.  
  
##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage  
 Modifie la page active.  
  
```  
BOOL SetActivePage(int nPage);  
BOOL SetActivePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Paramètres  
 `nPage`  
 Index de la page à définir. Doit être comprise entre 0 et inférieur au nombre de pages dans la feuille de propriétés, incluse.  
  
 `pPage`  
 Pointe vers la page pour définir dans la feuille de propriétés. Il ne peut pas être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la feuille de propriétés est activée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Par exemple, utilisez `SetActivePage` si l’action d’un utilisateur sur une page doit entraîner une autre page de devenir la page active.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText  
 Définit le texte du bouton de commande de terminer.  
  
```  
void SetFinishText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszText`  
 Pointe vers le texte à afficher sur le bouton de commande de fin.  
  
### <a name="remarks"></a>Notes  
 Appelez `SetFinishText` pour afficher le texte sur le bouton de commande de fin et de masquer les boutons suivant et précédent une fois que l’utilisateur a terminé l’action dans la dernière page de l’Assistant.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="settitle"></a>  CPropertySheet::SetTitle  
 Spécifie la légende de la feuille de propriétés (à savoir, le texte affiché dans la barre de titre d’une fenêtre frame).  
  
```  
void SetTitle(
    LPCTSTR lpszText,  
    UINT nStyle = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nStyle`  
 Spécifie le style de titre de la feuille de propriétés. Le style doit être spécifié à 0 ou en tant que **PSH_PROPTITLE**. Si le style est défini en tant que **PSH_PROPTITLE**, le mot « Propriétés » s’affiche après le texte spécifié comme légende. Par exemple, l’appel `SetTitle`(« Simple », **PSH_PROPTITLE**) entraîne une légende de feuille de propriétés de « Propriétés Simple ».  
  
 `lpszText`  
 Pointe vers le texte à utiliser en tant que la légende dans la barre de titre de la feuille de propriétés.  
  
### <a name="remarks"></a>Notes  
 Par défaut, une feuille de propriétés utilise le paramètre de la légende dans le constructeur de feuille de propriétés.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]  
  
##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons  
 Active ou désactive le bouton précédent, suivant ou terminer dans une feuille de propriétés d’Assistant.  
  
```  
void SetWizardButtons(DWORD dwFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 Un ensemble d’indicateurs permettant de personnaliser la fonction et l’apparence des boutons de l’Assistant. Ce paramètre peut être une combinaison des valeurs suivantes :  
  
- **PSWIZB_BACK** bouton précédent  
  
- **PSWIZB_NEXT** bouton suivant  
  
- **PSWIZB_FINISH** bouton Terminer  
  
- **PSWIZB_DISABLEDFINISH** bouton Terminer désactivé  
  
### <a name="remarks"></a>Notes  
 Appelez `SetWizardButtons` uniquement après que la boîte de dialogue est ouverte ; vous ne pouvez pas appeler `SetWizardButtons` avant d’appeler [DoModal](#domodal). En règle générale, vous devez appeler `SetWizardButtons` de [notifications CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).  
  
 Si vous souhaitez modifier le texte sur le bouton Terminer ou masquer la prochaine sauvegarde des boutons et une fois l’utilisateur a terminé l’Assistant, l’appel [SetFinishText](#setfinishtext). Notez que le même bouton est partagé pour terminer et suivant. Vous pouvez afficher une fin ou un bouton suivant à la fois, mais pas les deux.  
  
### <a name="example"></a>Exemple  
 A `CPropertySheet` a trois pages de propriétés d’Assistant : `CStylePage`, `CColorPage`, et `CShapePage`.  Le fragment de code ci-dessous montre comment activer et désactiver la **précédent** et **suivant** boutons de la page de propriété d’Assistant.  
  
 [!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="setwizardmode"></a>  Fonction CPropertySheet::SetWizardMode  
 Établit une page de propriétés d’Assistant.  
  
```  
void SetWizardMode();
```  
  
### <a name="remarks"></a>Notes  
 Une caractéristique clé d’une page de propriétés de l’Assistant est que l’utilisateur accède à l’aide de suivant ou terminer, sauvegarder et annuler des boutons à la place d’onglets.  
  
 Appelez `SetWizardMode` avant d’appeler [DoModal](#domodal). Après avoir appelé `SetWizardMode`, `DoModal` renvoie soit **ID_WIZFINISH** (si l’utilisateur ferme avec le bouton Terminer) ou **IDCANCEL**.  
  
 `SetWizardMode` définit l’indicateur PSH_WIZARD.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [MFC exemple CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC exemple CMNCTRL2](../../visual-cpp-samples.md)   
 [Exemple MFC PROPDLG](../../visual-cpp-samples.md)   
 [Exemple MFC SNAPVW](../../visual-cpp-samples.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



