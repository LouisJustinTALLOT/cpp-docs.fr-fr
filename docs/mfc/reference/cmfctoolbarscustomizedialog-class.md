---
title: Classe de CMFCToolBarsCustomizeDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7015e3be189bce8745777ef7353e1f2788a6f6be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378179"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>Classe de CMFCToolBarsCustomizeDialog
Une boîte de dialogue non modale onglet ( [CPropertySheet (classe)](../../mfc/reference/cpropertysheet-class.md)) qui permet à l’utilisateur personnaliser les barres d’outils, les menus, les raccourcis clavier, les outils définis par l’utilisateur et les style visuel dans une application. En général, l'utilisateur accède à cette boîte de dialogue en sélectionnant **Personnaliser** dans le menu **Outils** .  
  
 Le **personnaliser** boîte de dialogue comporte six onglets : **commandes**, **barres d’outils**, **outils**, **clavier**,  **Menu**, et **Options**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarsCustomizeDialog : public CPropertySheet  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Construit un objet `CMFCToolBarsCustomizeDialog`.|  
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Insère un bouton de barre d’outils dans la liste des commandes sur le **commandes** page|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Charge un menu dans les ressources et les appels [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste des commandes sur le **commandes** page.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Charge un menu dans les ressources et les appels [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste des commandes sur le **commandes** page.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Charge une barre d’outils à partir des ressources. Ensuite, pour chaque commande dans les appels de menu le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode pour insérer un bouton dans la liste des commandes sur le **commandes** page sous la catégorie spécifiée.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](#create)|Affiche la **personnalisation** boîte de dialogue.|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|Réservé à un usage ultérieur.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Active ou désactive la création de nouvelles barres d’outils à l’aide de la **personnaliser** boîte de dialogue.|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Remplit le `CListBox` objet avec les commandes dans le **toutes les commandes** catégorie.|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Remplit le `CComboBox` objet portant le nom de chaque catégorie de la commande dans le **personnaliser** boîte de dialogue.|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Remplit le `CListBox` objet portant le nom de chaque catégorie de la commande dans le **personnaliser** boîte de dialogue.|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Récupère le nom qui est associé à l’ID de commande donné.|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Récupère le nombre d’éléments dans la liste fournie qui ont une étiquette de texte donné.|  
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Récupère le jeu d’indicateurs qui affectent le comportement de la boîte de dialogue.|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Démarre un éditeur d’images afin qu’un utilisateur peut personnaliser une icône d’élément de bouton ou menu barre d’outils.|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Les remplacements pour augmenter l’initialisation feuille des propriétés. (Substitue [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Appelé par l’infrastructure une fois que la fenêtre a été détruite. (Substitue `CPropertySheet::PostNcDestroy`.)|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Supprime le bouton avec l’ID de commande spécifié à partir de la catégorie spécifiée ou toutes les catégories.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Renomme une catégorie dans la zone de liste de catégories sur le **commandes** onglet.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Remplace un bouton dans la liste des commandes sur le **commandes** onglet avec un nouvel objet de bouton de barre d’outils.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Ajoute une catégorie à la liste des catégories qui sera affiché sur le **commandes** onglet.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Appelé par l’infrastructure pour déterminer si la liste des outils définis par l’utilisateur est valide.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Appelé par le framework lorsque les propriétés d’un outil défini par l’utilisateur changent.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Détermine si un raccourci clavier spécifié peut être affecté à une action.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Détermine si un outil défini par l’utilisateur peut être modifié.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Appelé par le framework lorsque l’utilisateur choisit le **outils** onglet est demandé.|  
  
## <a name="remarks"></a>Notes  
 Pour afficher le **personnaliser** boîte de dialogue zone, créez un `CMFCToolBarsCustomizeDialog` objet et appelez le [CMFCToolBarsCustomizeDialog::Create](#create) (méthode).  
  
 Alors que le **personnaliser** boîte de dialogue est active, l’application fonctionne dans un mode spécial qui limite l’utilisateur à des tâches de personnalisation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCToolBarsCustomizeDialog` classe. L’exemple montre comment remplacer un bouton de barre d’outils dans la zone de liste de commandes sur le **commandes** page, activer la création de nouvelles barres d’outils à l’aide de la **personnaliser** boîte de dialogue et afficher les  **Personnalisation** boîte de dialogue. Cet extrait de code fait partie de la [exemple de démonstration d’insertion/éjection](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 `CMFCToolBarsCustomizeDialog`   
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxToolBarsCustomizeDialog.h  
  
##  <a name="addbutton"></a>  CMFCToolBarsCustomizeDialog::AddButton  
 Insère un bouton de barre d’outils dans la liste des commandes sur le **commandes** page.  
  
```  
void AddButton(
    UINT uiCategoryId,  
    const CMFCToolBarButton& button,  
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,  
    const CMFCToolBarButton& button,  
    int iInsertBefore=-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCategoryId`  
 Spécifie l’ID de catégorie dans laquelle insérer le bouton.  
  
 [in] `button`  
 Spécifie le bouton à insérer.  
  
 [in] `iInsertBefore`  
 Spécifie l’index de base zéro d’un bouton de barre d’outils avant laquelle le bouton est inséré.  
  
 [in] `lpszCategory`  
 Spécifie la chaîne de catégorie pour le bouton Insérer.  
  
### <a name="remarks"></a>Notes  
 Le `AddButton` méthode ignore les boutons qui ont les ID de commande standard (par exemple, ID_FILE_MRU_FILE1), les commandes qui ne sont pas autorisées (voir [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) et factice de boutons.  
  
 Cette méthode crée un nouvel objet du même type que `button` (généralement un [CMFCToolBarButton classe](../../mfc/reference/cmfctoolbarbutton-class.md)) à l’aide du bouton de la classe d’exécution. Il appelle ensuite [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) pour copier les données membres d’un bouton et insère la copie dans la catégorie spécifiée.  
  
 Lorsque le bouton Nouveau est inséré, il reçoit le `OnAddToCustomizePage` notification.  
  
 Si `iInsertBefore` est -1, le bouton est ajouté à la liste des catégories ; sinon, il est inséré avant l’élément avec l’index spécifié.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `AddButton` méthode de la `CMFCToolBarsCustomizeDialog` classe. Cet extrait de code fait partie de la [exemple Slider](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]  
  
##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu  
 Charge un menu dans les ressources et les appels [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste des commandes sur le **commandes** page.  
  
```  
BOOL AddMenu(UINT uiMenuResId);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiMenuResId`  
 Spécifie l’ID de ressource d’un menu à charger.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si un menu a été ajouté avec succès ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Dans l’appel à `AddMenuCommands`, `bPopup` est `FALSE`. Par conséquent, cette méthode n’ajoute pas d’éléments de menu qui contiennent des sous-menus à la liste des commandes. Cette méthode ajoute les éléments de menu dans les sous-menus à la liste des commandes.  
  
##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands  
 Ajoute des éléments à la liste des commandes dans le **commandes** page pour représenter tous les éléments dans le menu spécifié.  
  
```  
void AddMenuCommands(
    const CMenu* pMenu,  
    BOOL bPopup,  
    LPCTSTR lpszCategory=NULL,  
    LPCTSTR lpszMenuPath=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pMenu`  
 Pointeur vers l’objet CMenu à ajouter.  
  
 [in] `bPopup`  
 Spécifie s’il faut insérer les éléments de menu contextuel à la liste de commandes.  
  
 [in] `lpszCategory`  
 Le nom de la catégorie à insérer le menu.  
  
 [in] `lpszMenuPath`  
 Un préfixe qui est ajouté au nom lors de la commande est indiquée dans le **toutes les catégories** liste.  
  
### <a name="remarks"></a>Notes  
 Le `AddMenuCommands` méthode des boucles sur tous les éléments de menu de `pMenu`. Pour chaque élément de menu qui ne contient-elle pas un sous-menu, cette méthode crée un [CMFCToolBarButton classe](../../mfc/reference/cmfctoolbarbutton-class.md) objet et appelle le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode pour ajouter l’élément de menu en tant qu’une barre d’outils bouton à la liste des commandes sur le **commandes** page. Séparateurs de fin sont ignorés dans ce processus.  
  
 Si `bPopup` est `TRUE`, pour chaque élément de menu qui contient un sous-menu, cette méthode crée un [CMFCToolBarMenuButton classe](../../mfc/reference/cmfctoolbarmenubutton-class.md) de l’objet et l’insère dans la liste des commandes en appelant `AddButton`. Sinon, les éléments de menu qui contiennent des sous-menus ne sont pas affichés dans la liste des commandes. Dans les deux cas, lorsque `AddMenuCommands` rencontre un élément de menu avec un sous-menu il appelle de manière récursive, en passant un pointeur vers le sous-menu comme le `pMenu` paramètre et l’ajout de l’étiquette du sous-menu à `lpszMenuPath`.  
  
##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar  
 Charge une barre d’outils à partir des ressources. Ensuite, pour chaque commande dans les appels de menu le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode pour insérer un bouton dans la liste des commandes sur le **commandes** page sous la catégorie spécifiée.  
  
```  
BOOL AddToolBar(
    UINT uiCategoryId,  
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,  
    UINT uiToolbarResId);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCategoryId`  
 Spécifie l’ID de ressource de la catégorie pour ajouter la barre d’outils.  
  
 [in] `uiToolbarResId`  
 Spécifie l’ID de ressource d’une barre d’outils dont les commandes sont insérées dans la liste des commandes.  
  
 [in] `lpszCategory`  
 Spécifie le nom de la catégorie à laquelle ajouter la barre d’outils.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `AddToolBar` méthode dans la `CMFCToolBarsCustomizeDialog` classe. Cet extrait de code fait partie de l’ [exemple Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]  
  
### <a name="remarks"></a>Notes  
 Le contrôle est utilisé pour représenter chaque commande est une [CMFCToolBarButton classe](../../mfc/reference/cmfctoolbarbutton-class.md) objet. Après avoir ajouté la barre d’outils, vous pouvez remplacer le bouton avec un contrôle d’un type dérivé en appelant [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).  
  
##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity  
 Vérifie la validité de la liste des outils de l’utilisateur.  
  
```  
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lstTools`  
 La liste des outils définis par l’utilisateur à vérifier.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` si la liste des outils définis par l’utilisateur est valide ; sinon `FALSE`. L’implémentation par défaut toujours retourne `TRUE`.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode pour vérifier la validité des objets qui représentent des outils définis par l’utilisateur retournés par [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).  
  
 Remplacer la `CheckToolsValidity` méthode dans une classe dérivée `CMFCToolBarsCustomizeDialog` si vous souhaitez valider les outils utilisateur avant que l’utilisateur ferme la boîte de dialogue. Si cette méthode retourne `FALSE` lorsque l’utilisateur clique sur le **fermer** situé dans l’angle supérieur droit de la boîte de dialogue ou le bouton **fermer** dans le coin inférieur droit de la boîte de dialogue, la boîte de dialogue affiche le **outils** onglet au lieu de fermeture. Si cette méthode retourne `FALSE` lorsque l’utilisateur clique sur un onglet pour accéder à la **outils** onglet, le volet de navigation n’a pas lieu. Vous devez afficher une boîte de message approprié pour informer l’utilisateur du problème qui a provoqué la validation échoue.  
  
##  <a name="cmfctoolbarscustomizedialog"></a>  CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog  
 Construit un objet `CMFCToolBarsCustomizeDialog`.  
  
```  
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bAutoSetFromMenus = FALSE,  
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),  
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParentFrame`  
 Pointeur vers le frame parent. Ce paramètre ne doit pas être `NULL`.  
  
 [in] `bAutoSetFromMenus`  
 Valeur booléenne qui spécifie s’il faut ajouter les commandes de menu à partir de tous les menus à la liste des commandes sur le **commandes** page. Si ce paramètre est `TRUE`, les commandes de menu sont ajoutés. Dans le cas contraire, les commandes de menu ne sont pas ajoutés.  
  
 [in] `uiFlags`  
 Une combinaison d’indicateurs qui affectent le comportement de la boîte de dialogue. Ce paramètre peut être une ou plusieurs des valeurs suivantes :  
  
- `AFX_CUSTOMIZE_MENU_SHADOWS`  
  
- `AFX_CUSTOMIZE_TEXT_LABELS`  
  
- `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
  
- `AFX_CUSTOMIZE_NOHELP`  
  
- `AFX_CUSTOMIZE_CONTEXT_HELP`  
  
- `AFX_CUSTOMIZE_NOTOOLS`  
  
- `AFX_CUSTOMIZE_MENUAMPERS`  
  
- `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
  
 [in] `plistCustomPages`  
 Un pointeur désignant une liste de `CRuntimeClass` objets qui spécifient des pages personnalisées supplémentaires.  
  
### <a name="remarks"></a>Notes  
 Le `plistCustomPages` paramètre fait référence à la liste des `CRuntimeClass` objets qui spécifient des pages personnalisées supplémentaires. Le constructeur ajoute plus de pages à la boîte de dialogue à l’aide de la [CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) (méthode). Consultez l’exemple CustomPages pour obtenir un exemple qui ajoute plus de pages à la **personnaliser** boîte de dialogue.  
  
 Pour plus d’informations sur les valeurs que vous pouvez passer dans le `uiFlags` paramètre, consultez [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCToolBarsCustomizeDialog` classe. Cet extrait de code fait partie de la [exemple des Pages personnalisées](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]  
  
##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create  
 Affiche la **personnalisation** boîte de dialogue.  
  
```  
virtual BOOL Create();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la feuille de propriétés de personnalisation est créée avec succès ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Appelez le `Create` méthode uniquement après l’initialisation complète la classe.  
  
##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars  
 Active ou désactive la création de nouvelles barres d’outils à l’aide de la **personnaliser** boîte de dialogue.  
  
```  
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE` Pour activer les barres d’outils définies par l’utilisateur ; `FALSE` pour désactiver les barres d’outils.  
  
### <a name="remarks"></a>Notes  
 Si `bEnable` est `TRUE`, le **nouveau**, **renommer** et **supprimer** boutons sont affichés sur la **barres d’outils** page.  
  
 Par défaut, ou si `bEnable` est `FALSE`, ces boutons ne sont pas affichés et l’utilisateur ne peut pas définir de nouvelles barres d’outils.  
  
##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList  
 Remplit le `CListBox` objet avec les commandes dans le **toutes les commandes** catégorie.  
  
```  
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `wndListOfCommands`  
 Une référence à la `CListBox` objet à remplir.  
  
### <a name="remarks"></a>Notes  
 Le **toutes les commandes** catégorie contient les commandes de toutes les catégories. Le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode ajoute la commande qui est associée au bouton fourni pour le **toutes les commandes** catégorie pour vous.  
  
 Cette méthode efface le contenu de l’élément fourni `CListBox` objet avant de le remplir avec les commandes dans le **toutes les commandes** catégorie.  
  
 La `CMFCMousePropertyPage` classe utilise cette méthode pour remplir la zone de liste des événements de double-clic.  
  
##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox  
 Remplit le `CComboBox` objet portant le nom de chaque catégorie de la commande dans le **personnaliser** boîte de dialogue.  
  
```  
void FillCategoriesComboBox(
    CComboBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `wndCategory`  
 Une référence à la `CComboBox` objet à remplir.  
  
 [in] `bAddEmpty`  
 Valeur booléenne qui spécifie s’il faut ajouter des catégories à la zone de liste modifiable qui n’ont pas de commandes. Si ce paramètre est `TRUE`, catégories vides sont ajoutés à la zone de liste déroulante. Dans le cas contraire, les catégories vides ne sont pas ajoutés.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est comparable à la [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) (méthode), sauf que cette méthode fonctionne avec un `CComboBox` objet.  
  
 Cette méthode n’efface pas le contenu de la `CComboBox` objet avant de remplir. Il garantit que le **toutes les commandes** catégorie est le dernier élément dans la zone de liste déroulante.  
  
 Vous pouvez ajouter de nouvelles catégories de commande à l’aide de la [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) (méthode). Vous pouvez modifier le nom d’une catégorie existante à l’aide de la [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) (méthode).  
  
 Le `CMFCToolBarsKeyboardPropertyPage` et `CMFCKeyMapDialog` classes utilisent cette méthode pour classer les mappages du clavier.  
  
##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox  
 Remplit le `CListBox` objet portant le nom de chaque catégorie de la commande dans le **personnaliser** boîte de dialogue.  
  
```  
void FillCategoriesListBox(
    CListBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `wndCategory`  
 Une référence à la `CListBox` objet à remplir.  
  
 [in] `bAddEmpty`  
 Valeur booléenne qui spécifie s’il faut ajouter des catégories à la zone de liste qui n’ont pas de commandes. Si ce paramètre est `TRUE`, catégories vides sont ajoutés à la zone de liste. Dans le cas contraire, les catégories vides ne sont pas ajoutés.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est comparable à la [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) (méthode), sauf que cette méthode fonctionne avec un `CListBox` objet.  
  
 Cette méthode n’efface pas le contenu de la `CListBox` objet avant de remplir. Il garantit que le **toutes les commandes** catégorie est le dernier élément dans la zone de liste.  
  
 Vous pouvez ajouter de nouvelles catégories de commande à l’aide de la [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) (méthode). Vous pouvez modifier le nom d’une catégorie existante à l’aide de la [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) (méthode).  
  
 La `CMFCToolBarsCommandsPropertyPage` classe utilise cette méthode pour afficher la liste des commandes qui est associée à chaque catégorie de la commande.  
  
##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName  
 Récupère le nom qui est associé à l’ID de commande donné.  
  
```  
LPCTSTR GetCommandName(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 L’ID de la commande à récupérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom associé à l’ID de commande donné, ou `NULL` si la commande n’existe pas.  
  
##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory  
 Récupère le nombre d’éléments dans la liste fournie qui ont une étiquette de texte donné.  
  
```  
int GetCountInCategory(
    LPCTSTR lpszItemName,  
    const CObList& lstCommands) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszItemName`  
 L’étiquette de texte pour faire correspondre.  
  
 [in] `lstCommands`  
 Une référence à une liste qui contient `CMFCToolBarButton` objets.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans la liste dont égal d’étiquette de texte `lpszItemName`.  
  
### <a name="remarks"></a>Notes  
 Chaque élément dans la liste de l’objet fourni doit être de type `CMFCToolBarButton`. Cette méthode compare `lpszItemName` avec la [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) membre de données.  
  
##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags  
 Récupère le jeu d’indicateurs qui affectent le comportement de la boîte de dialogue.  
  
```  
UINT GetFlags() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le jeu d’indicateurs qui affectent le comportement de la boîte de dialogue.  
  
### <a name="remarks"></a>Notes  
 Cette méthode récupère la valeur de le `uiFlags` paramètre est passé au constructeur. La valeur de retour peut être une ou plusieurs des valeurs suivantes :  
  
 `AFX_CUSTOMIZE_MENU_SHADOWS`  
 Permet à l’utilisateur de spécifier l’apparence de l’ombre du menu.  
  
 `AFX_CUSTOMIZE_TEXT_LABELS`  
 Permet à l’utilisateur de spécifier si les étiquettes de texte s’affichent sous les images de boutons de barre d’outils.  
  
 `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
 Permet à l’utilisateur spécifier le style d’animation de menu.  
  
 `AFX_CUSTOMIZE_NOHELP`  
 Supprime le bouton aide de la boîte de dialogue de personnalisation.  
  
 `AFX_CUSTOMIZE_CONTEXT_HELP`  
 Permet la `WS_EX_CONTEXTHELP` style visuel.  
  
 `AFX_CUSTOMIZE_NOTOOLS`  
 Supprime la **outils** page à partir de la boîte de dialogue de personnalisation. Cet indicateur n’est valide que si votre application utilise le `CUserToolsManager` classe.  
  
 `AFX_CUSTOMIZE_MENUAMPERS`  
 Permet les légendes des boutons contenir l’esperluette ( **&**) caractères.  
  
 `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
 Supprime la **grandes icônes** option à partir de la boîte de dialogue de personnalisation.  
  
 Pour plus d’informations sur la `WS_EX_CONTEXTHELP` style visuel, consultez [Styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool  
 Répond à une modification dans un outil utilisateur dès qu’il se produit.  
  
```  
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>Paramètres  
 [in, out] `pSelTool`  
 Pointeur vers l’objet de l’outil utilisateur qui a été modifié.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par l’infrastructure lorsqu’un utilisateur modifie les propriétés d’un outil défini par l’utilisateur. L'implémentation par défaut n'exécute aucune opération. Substituez cette méthode dans une classe dérivée de `CMFCToolBarsCustomizeDialog` pour effectuer le traitement après une modification apportée à un outil utilisateur.  
  
##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey  
 Valide les raccourcis clavier comme un utilisateur les définit.  
  
```  
virtual BOOL OnAssignKey(ACCEL* pAccel);
```  
  
### <a name="parameters"></a>Paramètres  
 [in, out] `pAccel`  
 Pointeur vers l’attribution de clavier proposé est exprimée comme une [accélération](http://msdn.microsoft.com/library/windows/desktop/ms646340) struct.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la clé peut être assignée, ou `FALSE` si la clé ne peut pas être assignée. L’implémentation par défaut toujours retourne `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour effectuer un traitement supplémentaire lorsqu’un utilisateur affecte un nouveau raccourci clavier, ou pour valider les raccourcis clavier que l’utilisateur définit les. Pour empêcher l’attribution de raccourci, retourner `FALSE`. Vous devez également afficher une boîte de message ou sinon informer l’utilisateur de la raison du rejet du raccourci clavier.  
  
##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool  
 Effectue un traitement personnalisé lorsqu’une modification à un outil utilisateur lorsque l’utilisateur est sur le point d’appliquer une modification.  
  
```  
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>Paramètres  
 [in, out] `pSelTool`  
 Pointeur vers l’objet de l’outil utilisateur qui doit être remplacé.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par l’infrastructure lorsque les propriétés d’un outil défini par l’utilisateur est sur le point de changer. L'implémentation par défaut n'exécute aucune opération. Remplacer la `OnBeforeChangeTool` méthode dans une classe dérivée de `CMFCToolBarsCustomizeDialog` si vous souhaitez effectuer un traitement avant une modification apportée à un outil utilisateur, telles que la libération des ressources qui `pSelTool` utilise.  
  
##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage  
 Démarre un éditeur d’images afin qu’un utilisateur peut personnaliser une icône d’élément de bouton ou menu barre d’outils.  
  
```  
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,  
    CBitmap& bitmap,  
    int nBitsPerPixel);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParent`  
 Pointeur vers la fenêtre parente.  
  
 [in] `bitmap`  
 Une référence à un objet bitmap à modifier.  
  
 [in] `nBitsPerPixel`  
 Résolution de couleur, en bits par pixel de la bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si une modification est validée ; dans le cas contraire `FALSE`. L’implémentation par défaut affiche une boîte de dialogue et retourne `TRUE` si l’utilisateur clique sur **OK**, ou `FALSE` si l’utilisateur clique sur **Annuler** ou **fermer** bouton.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par l’infrastructure quand l’utilisateur exécute l’éditeur d’images. Les affichages de mise en œuvre par défaut [CMFCImageEditorDialog classe](../../mfc/reference/cmfcimageeditordialog-class.md) boîte de dialogue. Substituer `OnEditToolbarMenuImage` dans une classe dérivée à utiliser un éditeur d’images personnalisées.  
  
##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog  
 Les remplacements pour augmenter l’initialisation feuille des propriétés.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le résultat de l’appel de la [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) (méthode).  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de la classe de base, [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), en affichant le **fermer** bouton, en vous assurant que la boîte de dialogue correspond à la taille d’écran actuelle et en déplaçant le **Aide** bouton à l’angle inférieur gauche de la boîte de dialogue.  
  
##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage  
 Gère la notification de l’infrastructure qui les **outils** page est sur le point d’être initialisé.  
  
```  
virtual void OnInitToolsPage();
```  
  
### <a name="remarks"></a>Notes  
 L'implémentation par défaut n'exécute aucune opération. Substituez cette méthode dans une classe dérivée pour traiter cette notification.  
  
##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy  
 Appelé par l’infrastructure une fois que la fenêtre a été détruite.  
  
```  
virtual void PostNcDestroy();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de la classe de base, `CPropertySheet::PostNcDestroy`, en restaurant l’application pour le mode précédent.  
  
 Le [CMFCToolBarsCustomizeDialog::Create](#create) méthode met l’application dans un mode spécial qui limite l’utilisateur à des tâches de personnalisation.  
  
##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton  
 Supprime le bouton avec l’ID de commande spécifié à partir de la catégorie spécifiée ou toutes les catégories.  
  
```  
int RemoveButton(
    UINT uiCategoryId,  
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,  
    UINT uiCmdId);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCategoryId`  
 Spécifie l’ID de catégorie à partir de laquelle supprimer le bouton.  
  
 [in] `uiCmdId`  
 Spécifie l’ID de commande du bouton.  
  
 [in] `lpszCategory`  
 Spécifie le nom de la catégorie à partir de laquelle supprimer le bouton.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro du bouton supprimé, ou -1 si l’ID de commande spécifié est introuvable dans la catégorie spécifiée. Si `uiCategoryId` est -1, la valeur de retour est 0.  
  
### <a name="remarks"></a>Notes  
 Pour supprimer un bouton de toutes les catégories, appelez la première surcharge de cette méthode et le jeu de `uiCategoryId` -1.  
  
##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory  
 Renomme une catégorie dans la zone de liste de catégories sur le **commandes** page.  
  
```  
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,  
    LPCTSTR lpszCategoryNew);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszCategoryOld`  
 Le nom de la catégorie à modifier.  
  
 [in] `lpszCategoryNew`  
 Le nouveau nom de catégorie.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Le nom de catégorie doit être unique.  
  
##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton  
 Remplace un bouton de barre d’outils dans la zone de liste de commandes sur le **commandes** page.  
  
```  
void ReplaceButton(
    UINT uiCmd,  
    const CMFCToolBarButton& button);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmd`  
 Spécifie la commande du bouton doit être remplacée.  
  
 [in] `button`  
 A `const` référence à l’objet de bouton de barre d’outils qui remplace l’ancien bouton.  
  
### <a name="remarks"></a>Notes  
 Lorsque [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands), ou [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) ajoute un commande à la **commandes** page, que la commande est sous la forme d’un [CMFCToolBarButton classe](../../mfc/reference/cmfctoolbarbutton-class.md) objet (ou un [CMFCToolBarMenuButton classe](../../mfc/reference/cmfctoolbarmenubutton-class.md) objet pour un menu élément qui contient un sous-menu ajouté par `AddMenuCommands`). L’infrastructure appelle également ces trois méthodes pour ajouter automatiquement des commandes. Si vous souhaitez une commande pour être représentée par un type dérivé, au lieu de cela, appelez `ReplaceButton` et le passer à un bouton du type dérivé.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `ReplaceButton` méthode dans la `CMFCToolBarsCustomizeDialog` classe. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]  
  
##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory  
 Spécifie la catégorie dans la liste des catégories sur le **commandes** page est la catégorie d’utilisateur. Vous devez appeler cette fonction avant d’appeler [CMFCToolBarsCustomizeDialog::Create](#create).  
  
```  
BOOL SetUserCategory(LPCTSTR lpszCategory);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszCategory`  
 Nom de la catégorie.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Le paramètre de catégorie d’utilisateur n’est pas actuellement utilisé par l’infrastructure.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CPropertySheet, classe](../../mfc/reference/cpropertysheet-class.md)
