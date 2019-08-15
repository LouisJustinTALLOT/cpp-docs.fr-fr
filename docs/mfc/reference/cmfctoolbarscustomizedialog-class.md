---
title: CMFCToolBarsCustomizeDialog, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 239532c78491f121423ca42a2c3dfc306997c841
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504689"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog, classe

Boîte de dialogue à onglets non modale ( [classe CPropertySheet](../../mfc/reference/cpropertysheet-class.md)) qui permet à l’utilisateur de personnaliser les barres d’outils, les menus, les raccourcis clavier, les outils définis par l’utilisateur et le style visuel dans une application. En général, l'utilisateur accède à cette boîte de dialogue en sélectionnant **Personnaliser** dans le menu **Outils** .

La boîte de dialogue **personnaliser** contient six onglets: **Commandes**, **barres d’outils**, **Outils**, **clavier**, **menu**et **options**.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog:: CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Construit un objet `CMFCToolBarsCustomizeDialog`.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)|Insère un bouton de barre d’outils dans la liste des commandes de la page **commandes** .|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AjouterMenu](#addmenu)|Charge un menu à partir des ressources et appelle [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste de commandes sur la page **commandes** .|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands)|Charge un menu à partir des ressources et appelle [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste de commandes sur la page **commandes** .|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddToolBar](#addtoolbar)|Charge une barre d’outils à partir des ressources. Ensuite, pour chaque commande du menu appelle la méthode [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) pour insérer un bouton dans la liste des commandes de la page **commandes** , sous la catégorie spécifiée.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: Create](#create)|Affiche la boîte de dialogue **personnalisation** .|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Réservé à un usage ultérieur.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Active ou désactive la création de nouvelles barres d’outils à l’aide de la boîte de dialogue **personnaliser** .|
|[CMFCToolBarsCustomizeDialog:: FillAllCommandsList](#fillallcommandslist)|Remplit l’objet fourni `CListBox` avec les commandes de la catégorie **toutes les commandes** .|
|[CMFCToolBarsCustomizeDialog:: FillCategoriesComboBox](#fillcategoriescombobox)|Remplit l’objet fourni `CComboBox` avec le nom de chaque catégorie de commande dans la boîte de dialogue **personnaliser** .|
|[CMFCToolBarsCustomizeDialog:: FillCategoriesListBox](#fillcategorieslistbox)|Remplit l’objet fourni `CListBox` avec le nom de chaque catégorie de commande dans la boîte de dialogue **personnaliser** .|
|[CMFCToolBarsCustomizeDialog:: GetCommandName](#getcommandname)|Récupère le nom associé à l’ID de commande donné.|
|[CMFCToolBarsCustomizeDialog:: GetCountInCategory](#getcountincategory)|Récupère le nombre d’éléments dans la liste fournie qui ont une étiquette de texte donnée.|
|[CMFCToolBarsCustomizeDialog:: GetFlags](#getflags)|Récupère le jeu d’indicateurs qui affectent le comportement de la boîte de dialogue.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Démarre un éditeur d’images pour qu’un utilisateur puisse personnaliser un bouton de barre d’outils ou une icône d’élément de menu.|
|[CMFCToolBarsCustomizeDialog:: OnInitDialog](#oninitdialog)|Substitue pour augmenter l’initialisation de la feuille de propriétés. (Substitue [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::P ostNcDestroy](#postncdestroy)|Appelé par le Framework après la destruction de la fenêtre. (Substitue `CPropertySheet::PostNcDestroy`.)|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: removeButton](#removebutton)|Supprime le bouton avec l’ID de commande spécifié de la catégorie spécifiée ou de toutes les catégories.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory)|Renomme une catégorie dans la zone de liste des catégories de l’onglet **commandes** .|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton)|Remplace un bouton dans la liste de commandes sous l’onglet **commandes** par un nouvel objet bouton de barre d’outils.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: SetUserCategory](#setusercategory)|Ajoute une catégorie à la liste des catégories qui seront affichées sous l’onglet **commandes** .|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity)|Appelée par l’infrastructure pour déterminer si la liste des outils définis par l’utilisateur est valide.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnAfterChangeTool](#onafterchangetool)|Appelée par l’infrastructure lorsque les propriétés d’un outil défini par l’utilisateur sont modifiées.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnAssignKey](#onassignkey)|Détermine si un raccourci clavier spécifié peut être assigné à une action.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnBeforeChangeTool](#onbeforechangetool)|Détermine si un outil défini par l’utilisateur peut être modifié.|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnInitToolsPage](#oninittoolspage)|Appelée par l’infrastructure quand l’utilisateur choisit l’onglet **Outils** est demandé.|

## <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue **personnaliser** , créez `CMFCToolBarsCustomizeDialog` un objet et appelez la méthode [CMFCToolBarsCustomizeDialog:: Create](#create) .

Lorsque la boîte de dialogue **personnaliser** est active, l’application fonctionne dans un mode spécial qui limite l’utilisateur aux tâches de personnalisation.

## <a name="example"></a>Exemples

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCToolBarsCustomizeDialog` . L’exemple montre comment remplacer un bouton de barre d’outils dans la zone de liste de commandes de la page **commandes** , comment activer la création de nouvelles barres d’outils à l’aide de la boîte de dialogue **personnaliser** et comment afficher la boîte de dialogue **personnalisation** . Cet extrait de code fait partie de l' [exemple de démonstration IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxToolBarsCustomizeDialog. h

##  <a name="addbutton"></a>CMFCToolBarsCustomizeDialog:: AddButton

Insère un bouton de barre d’outils dans la liste des commandes de la page **commandes** .

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

*uiCategoryId*<br/>
dans Spécifie l’ID de catégorie dans lequel insérer le bouton.

*button*<br/>
dans Spécifie le bouton à insérer.

*iInsertBefore*<br/>
dans Spécifie l’index de base zéro d’un bouton de barre d’outils avant lequel le bouton est inséré.

*lpszCategory*<br/>
dans Spécifie la chaîne de catégorie dans laquelle insérer le bouton.

### <a name="remarks"></a>Notes

La `AddButton` méthode ignore les boutons qui ont les ID de commande standard (tels que ID_FILE_MRU_FILE1), les commandes qui ne sont pas autorisées (voir [CMFCToolBar:: IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) et les boutons factices.

Cette méthode crée un nouvel objet du même type que `button` (généralement une [classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)) à l’aide de la classe Runtime du bouton. Il appelle ensuite [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) pour copier les données membres du bouton et insère la copie dans la catégorie spécifiée.

Lorsque le bouton nouveau est inséré, il reçoit la `OnAddToCustomizePage` notification.

Si `iInsertBefore` a la valeur-1, le bouton est ajouté à la liste des catégories; sinon, il est inséré avant l’élément avec l’index spécifié.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `AddButton` méthode de la `CMFCToolBarsCustomizeDialog` classe. Cet extrait de code fait partie de l' [exemple Slider](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>CMFCToolBarsCustomizeDialog:: AjouterMenu

Charge un menu à partir des ressources et appelle [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste de commandes sur la page **commandes** .

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Paramètres

*uiMenuResId*<br/>
dans Spécifie l’ID de ressource d’un menu à charger.

### <a name="return-value"></a>Valeur de retour

TRUE si un menu a été ajouté avec succès; Sinon, FALSe.

### <a name="remarks"></a>Notes

Dans l’appel à `AddMenuCommands`, *bPopup* a la valeur false. Par conséquent, cette méthode n’ajoute pas d’éléments de menu qui contiennent des sous-menus à la liste de commandes. Cette méthode ajoute les éléments de menu dans les sous-menus à la liste de commandes.

##  <a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog:: AddMenuCommands

Ajoute des éléments à la liste des commandes de la page **commandes** pour représenter tous les éléments du menu spécifié.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Paramètres

*pMenu*<br/>
dans Pointeur vers l’objet CMenu à ajouter.

*bPopup*<br/>
dans Spécifie s’il faut insérer les éléments de menu contextuel dans la liste des commandes.

*lpszCategory*<br/>
dans Nom de la catégorie dans laquelle insérer le menu.

*lpszMenuPath*<br/>
dans Préfixe qui est ajouté au nom lorsque la commande est affichée dans la liste **toutes les catégories** .

### <a name="remarks"></a>Notes

La `AddMenuCommands` méthode effectue une boucle sur tous les éléments de menu de *pMenu*. Pour chaque élément de menu qui ne contient pas de sous-menu, cette méthode crée un objet de [classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) et appelle la méthode [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) pour ajouter l’élément de menu sous la forme d’un bouton de barre d’outils à la liste des commandes **du Page commandes** . Les séparateurs sont ignorés dans ce processus.

Si *bPopup* a la valeur true, pour chaque élément de menu qui contient un sous-menu, cette méthode crée un objet de [classe CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) et l’insère dans la `AddButton`liste de commandes en appelant. Sinon, les éléments de menu qui contiennent des sous-menus ne sont pas affichés dans la liste de commandes. Dans les deux cas, `AddMenuCommands` lorsque rencontre un élément de menu avec un sous-menu, il s’appelle de manière récursive, en passant un pointeur vers le sous-menu comme paramètre *pMenu* et en ajoutant l’étiquette du sous-menu à *lpszMenuPath*.

##  <a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog:: AddToolBar

Charge une barre d’outils à partir des ressources. Ensuite, pour chaque commande du menu appelle la méthode [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) pour insérer un bouton dans la liste des commandes de la page **commandes** , sous la catégorie spécifiée.

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>Paramètres

*uiCategoryId*<br/>
dans Spécifie l’ID de ressource de la catégorie à laquelle ajouter la barre d’outils.

*uiToolbarResId*<br/>
dans Spécifie l’ID de ressource d’une barre d’outils dont les commandes sont insérées dans la liste de commandes.

*lpszCategory*<br/>
dans Spécifie le nom de la catégorie à laquelle ajouter la barre d’outils.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode réussit; Sinon, FALSe.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `AddToolBar` méthode dans la `CMFCToolBarsCustomizeDialog` classe. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Notes

Le contrôle utilisé pour représenter chaque commande est un objet de [classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) . Après avoir ajouté la barre d’outils, vous pouvez remplacer le bouton par un contrôle d’un type dérivé en appelant [CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton).

##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity

Vérifie la validité de la liste des outils utilisateur.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Paramètres

*lstTools*<br/>
dans Liste des outils définis par l’utilisateur à vérifier.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la liste des outils définis par l’utilisateur est valide; Sinon, FALSe. L’implémentation par défaut retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode pour vérifier la validité des objets qui représentent les outils définis par l’utilisateur retournés par [CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity).

Substituez la `CheckToolsValidity` méthode dans une classe dérivée `CMFCToolBarsCustomizeDialog` de si vous souhaitez valider les outils de l’utilisateur avant que l’utilisateur ferme la boîte de dialogue. Si cette méthode retourne la valeur FALSe lorsque l’utilisateur clique sur le bouton **Fermer** dans le coin supérieur droit de la boîte de dialogue ou sur le bouton intitulé **Fermer** dans le coin inférieur droit de la boîte de dialogue, la boîte de dialogue affiche l’onglet **Outils** au lieu de fermés. Si cette méthode retourne la valeur FALSe lorsque l’utilisateur clique sur un onglet pour quitter l’onglet **Outils** , la navigation n’a pas lieu. Vous devez afficher une boîte de message appropriée pour informer l’utilisateur du problème qui a provoqué l’échec de la validation.

##  <a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog:: CMFCToolBarsCustomizeDialog

Construit un objet `CMFCToolBarsCustomizeDialog`.

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>Paramètres

*pWndParentFrame*<br/>
dans Pointeur vers le frame parent. Ce paramètre ne doit pas avoir la valeur NULL.

*bAutoSetFromMenus*<br/>
dans Valeur booléenne qui spécifie s’il faut ajouter les commandes de menu de tous les menus à la liste de commandes de la page **commandes** . Si ce paramètre a la valeur TRUE, les commandes de menu sont ajoutées. Dans le cas contraire, les commandes de menu ne sont pas ajoutées.

*uiFlags*<br/>
dans Combinaison d’indicateurs qui affectent le comportement de la boîte de dialogue. Ce paramètre peut être une ou plusieurs des valeurs suivantes:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
dans Pointeur vers une liste d' `CRuntimeClass` objets qui spécifient des pages personnalisées supplémentaires.

### <a name="remarks"></a>Notes

Le paramètre *plistCustomPages* fait référence à la liste `CRuntimeClass` des objets qui spécifient des pages personnalisées supplémentaires. Le constructeur ajoute d’autres pages à la boîte de dialogue à l’aide de la méthode [CRuntimeClass:: CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) . Consultez l’exemple CustomPages pour obtenir un exemple qui ajoute d’autres pages à la boîte de dialogue **personnaliser** .

Pour plus d’informations sur les valeurs que vous pouvez passer dans le paramètre *uiFlags* , consultez [CMFCToolBarsCustomizeDialog:: GetFlags](#getflags).

### <a name="example"></a>Exemples

L’exemple suivant montre comment construire un objet de la `CMFCToolBarsCustomizeDialog` classe. Cet extrait de code fait partie de l' [exemple de pages personnalisées](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create

Affiche la boîte de dialogue **personnalisation** .

```
virtual BOOL Create();
```

### <a name="return-value"></a>Valeur de retour

TRUE si la feuille de propriétés de personnalisation est créée avec succès; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez la `Create` méthode uniquement après l’initialisation complète de la classe.

##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Active ou désactive la création de nouvelles barres d’outils à l’aide de la boîte de dialogue **personnaliser** .

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour activer les barres d’outils définies par l’utilisateur; FALSe pour désactiver les barres d’outils.

### <a name="remarks"></a>Notes

Si *bEnable* a la valeur true, les boutons **nouveau**, renommer et **supprimer** s’affichent sur la page **barres d’outils** .

Par défaut, ou si *bEnable* a la valeur false, ces boutons ne sont pas affichés et l’utilisateur ne peut pas définir de nouvelles barres d’outils.

##  <a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog:: FillAllCommandsList

Remplit l’objet fourni `CListBox` avec les commandes de la catégorie **toutes les commandes** .

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Paramètres

*wndListOfCommands*<br/>
à Référence à l' `CListBox` objet à remplir.

### <a name="remarks"></a>Notes

La catégorie **toutes les commandes** contient les commandes de toutes les catégories. La méthode [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) ajoute la commande associée au bouton fourni à la catégorie toutes les **commandes** .

Cette méthode efface le contenu de l’objet `CListBox` fourni avant de le remplir avec les commandes de la catégorie **toutes les commandes** .

La `CMFCMousePropertyPage` classe utilise cette méthode pour remplir la zone de liste des événements de double-clic.

##  <a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog:: FillCategoriesComboBox

Remplit l’objet fourni `CComboBox` avec le nom de chaque catégorie de commande dans la boîte de dialogue **personnaliser** .

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*wndCategory*<br/>
à Référence à l' `CComboBox` objet à remplir.

*bAddEmpty*<br/>
dans Valeur booléenne qui spécifie s’il faut ajouter des catégories à la zone de liste déroulante qui n’ont pas de commandes. Si ce paramètre a la valeur TRUE, les catégories vides sont ajoutées à la zone de liste déroulante. Sinon, les catégories vides ne sont pas ajoutées.

### <a name="remarks"></a>Notes

Cette méthode est similaire à la méthode [CMFCToolBarsCustomizeDialog:: FillCategoriesListBox](#fillcategorieslistbox) , à ceci près que cette `CComboBox` méthode fonctionne avec un objet.

Cette méthode n’efface pas le contenu de `CComboBox` l’objet avant de le remplir. Elle garantit que la catégorie **toutes les commandes** est le dernier élément de la zone de liste déroulante.

Vous pouvez ajouter de nouvelles catégories de commande à l’aide de la méthode [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) . Vous pouvez modifier le nom d’une catégorie existante à l’aide de la méthode [CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory) .

Les `CMFCToolBarsKeyboardPropertyPage` classes `CMFCKeyMapDialog` et utilisent cette méthode pour catégoriser les mappages du clavier.

##  <a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog:: FillCategoriesListBox

Remplit l’objet fourni `CListBox` avec le nom de chaque catégorie de commande dans la boîte de dialogue **personnaliser** .

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*wndCategory*<br/>
à Référence à l' `CListBox` objet à remplir.

*bAddEmpty*<br/>
dans Valeur booléenne qui spécifie s’il faut ajouter des catégories à la zone de liste qui n’ont pas de commandes. Si ce paramètre a la valeur TRUE, les catégories vides sont ajoutées à la zone de liste. Sinon, les catégories vides ne sont pas ajoutées.

### <a name="remarks"></a>Notes

Cette méthode est similaire à la méthode [CMFCToolBarsCustomizeDialog:: FillCategoriesComboBox](#fillcategoriescombobox) , à ceci près que cette `CListBox` méthode fonctionne avec un objet.

Cette méthode n’efface pas le contenu de `CListBox` l’objet avant de le remplir. Elle garantit que la catégorie **toutes les commandes** est le dernier élément de la zone de liste.

Vous pouvez ajouter de nouvelles catégories de commande à l’aide de la méthode [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton) . Vous pouvez modifier le nom d’une catégorie existante à l’aide de la méthode [CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory) .

La `CMFCToolBarsCommandsPropertyPage` classe utilise cette méthode pour afficher la liste des commandes associées à chaque catégorie de commande.

##  <a name="getcommandname"></a>CMFCToolBarsCustomizeDialog:: GetCommandName

Récupère le nom associé à l’ID de commande donné.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de la commande à récupérer.

### <a name="return-value"></a>Valeur de retour

Nom associé à l’ID de commande donné, ou valeur NULL si la commande n’existe pas.

##  <a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog:: GetCountInCategory

Récupère le nombre d’éléments dans la liste fournie qui ont une étiquette de texte donnée.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Paramètres

*lpszItemName*<br/>
dans Étiquette de texte à faire correspondre.

*lstCommands*<br/>
dans Référence à une liste qui contient `CMFCToolBarButton` des objets.

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans la liste fournie dont l’étiquette de texte est égale à *lpszItemName*.

### <a name="remarks"></a>Notes

Chaque élément de la liste d’objets fournie doit être de `CMFCToolBarButton`type. Cette méthode compare *lpszItemName* avec le membre de données [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) .

##  <a name="getflags"></a>CMFCToolBarsCustomizeDialog:: GetFlags

Récupère le jeu d’indicateurs qui affectent le comportement de la boîte de dialogue.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Valeur de retour

Ensemble d’indicateurs qui affectent le comportement de la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette méthode récupère la valeur du paramètre *uiFlags* qui est passé au constructeur. La valeur de retour peut être une ou plusieurs des valeurs suivantes:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Permet à l’utilisateur de spécifier l’apparence de l’ombre du menu.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Permet à l’utilisateur de spécifier si les étiquettes de texte sont affichées sous les images du bouton de barre d’outils.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Permet à l’utilisateur de spécifier le style d’animation de menu.  |
|AFX_CUSTOMIZE_NOHELP|Supprime le bouton aide de la boîte de dialogue Personnalisation.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Active le style visuel WS_EX_CONTEXTHELP.  |
|AFX_CUSTOMIZE_NOTOOLS|Supprime la page **Outils** de la boîte de dialogue Personnalisation. Cet indicateur est valide si votre application utilise la `CUserToolsManager` classe.  |
|AFX_CUSTOMIZE_MENUAMPERS|Autorise les légendes de bouton à contenir le caractère **&** perluète ().  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Supprime l’option **grandes icônes** de la boîte de dialogue Personnalisation.  |

Pour plus d’informations sur le style visuel WS_EX_CONTEXTHELP, consultez [styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Répond à une modification dans un outil utilisateur immédiatement après qu’il a eu lieu.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Paramètres

*pSelTool*<br/>
[in, out] Pointeur vers l’objet d’outil utilisateur qui a été modifié.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure quand un utilisateur modifie les propriétés d’un outil défini par l’utilisateur. L'implémentation par défaut n'exécute aucune opération. Substituez cette méthode dans une classe dérivée `CMFCToolBarsCustomizeDialog` de pour effectuer le traitement après qu’une modification apportée à un outil utilisateur s’est produite.

##  <a name="onassignkey"></a>CMFCToolBarsCustomizeDialog:: OnAssignKey

Valide les raccourcis clavier au fur et à mesure qu’un utilisateur les définit.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Paramètres

*pAccel*<br/>
[in, out] Pointeur vers le attribution de clavier proposé, exprimé sous la forme d’une structure d' [accélération](/windows/win32/api/winuser/ns-winuser-accel) .

### <a name="return-value"></a>Valeur de retour

TRUE si la clé peut être assignée, ou FALSe si la clé ne peut pas être assignée. L’implémentation par défaut retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour effectuer un traitement supplémentaire lorsqu’un utilisateur affecte un nouveau raccourci clavier ou pour valider des raccourcis clavier lorsque l’utilisateur les définit. Pour empêcher l’attribution d’un raccourci, retournez la valeur FALSe. Vous devez également afficher une boîte de message ou informer l’utilisateur de la raison pour laquelle le raccourci clavier a été rejeté.

##  <a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog:: OnBeforeChangeTool

Effectue un traitement personnalisé lorsqu’une modification est apportée à un outil utilisateur lorsque l’utilisateur est sur le paragraphe d’appliquer une modification.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Paramètres

*pSelTool*<br/>
[in, out] Pointeur vers l’objet outil utilisateur sur le point d’être remplacé.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure lorsque les propriétés d’un outil défini par l’utilisateur sont sur le paragraphe de la modification. L'implémentation par défaut n'exécute aucune opération. Substituez la `OnBeforeChangeTool` méthode dans une classe dérivée `CMFCToolBarsCustomizeDialog` de si vous souhaitez effectuer un traitement avant qu’une modification apportée à un outil utilisateur se produise, par exemple libérer des ressources utilisées par *pSelTool* .

##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Démarre un éditeur d’images pour qu’un utilisateur puisse personnaliser un bouton de barre d’outils ou une icône d’élément de menu.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la fenêtre parente.

*bitmap*<br/>
dans Référence à un objet bitmap à modifier.

*nBitsPerPixel*<br/>
dans Résolution des couleurs bitmap, en bits par pixel.

### <a name="return-value"></a>Valeur de retour

TRUE si une modification est validée; Sinon, FALSe. L’implémentation par défaut affiche une boîte de dialogue et retourne la valeur TRUE si l’utilisateur clique sur **OK**, ou false si l’utilisateur clique sur **Annuler** ou sur le bouton **Fermer** .

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure lorsque l’utilisateur exécute l’éditeur d’images. L’implémentation par défaut affiche la boîte de dialogue [classe CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md) . Substituez `OnEditToolbarMenuImage` dans une classe dérivée pour utiliser un éditeur d’images personnalisé.

##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog

Substitue pour augmenter l’initialisation de la feuille de propriétés.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Résultat de l’appel de la méthode [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) .

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), en affichant le bouton **Fermer** , en s’assurant que la boîte de dialogue correspond à la taille d’écran actuelle et en déplaçant le bouton **aide** dans le coin inférieur gauche de la boîte de dialogue.

##  <a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog:: OnInitToolsPage

Gère la notification de l’infrastructure sur le point d’être initialisée par la page **Outils** .

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Substituez cette méthode dans une classe dérivée pour traiter cette notification.

##  <a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::P ostNcDestroy

Appelé par le Framework après la destruction de la fenêtre.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe `CPropertySheet::PostNcDestroy`de base,, en restaurant l’application sur le mode précédent.

La méthode [CMFCToolBarsCustomizeDialog:: Create](#create) met l’application en mode spécial qui limite l’utilisateur aux tâches de personnalisation.

##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton

Supprime le bouton avec l’ID de commande spécifié de la catégorie spécifiée ou de toutes les catégories.

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>Paramètres

*uiCategoryId*<br/>
dans Spécifie l’ID de catégorie à partir duquel supprimer le bouton.

*uiCmdId*<br/>
dans Spécifie l’ID de commande du bouton.

*lpszCategory*<br/>
dans Spécifie le nom de la catégorie à partir de laquelle supprimer le bouton.

### <a name="return-value"></a>Valeur de retour

Index de base zéro du bouton supprimé, ou-1 si l’ID de commande spécifié est introuvable dans la catégorie spécifiée. Si *uiCategoryId* a la valeur-1, la valeur de retour est 0.

### <a name="remarks"></a>Notes

Pour supprimer un bouton de toutes les catégories, appelez la première surcharge de cette méthode et affectez la valeur-1 à *uiCategoryId* .

##  <a name="renamecategory"></a>CMFCToolBarsCustomizeDialog:: RenameCategory

Renomme une catégorie dans la zone de liste des catégories de la page **commandes** .

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Paramètres

*lpszCategoryOld*<br/>
dans Nom de la catégorie à modifier.

*lpszCategoryNew*<br/>
dans Nom de la nouvelle catégorie.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le nom de la catégorie doit être unique.

##  <a name="replacebutton"></a>CMFCToolBarsCustomizeDialog:: ReplaceButton

Remplace un bouton de barre d’outils dans la zone de liste des commandes de la page **commandes** .

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans Spécifie la commande du bouton à remplacer.

*button*<br/>
dans Référence **const** à l’objet bouton de barre d’outils qui remplace l’ancien bouton.

### <a name="remarks"></a>Notes

Quand [CMFCToolBarsCustomizeDialog:: AjouterMenu](#addmenu), [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands)ou [CMFCToolBarsCustomizeDialog:: AddToolBar](#addtoolbar) ajoute une commande à la page **commandes** , cette commande est sous la forme d’un [ Objet de classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) (ou objet de [classe CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) pour un élément de menu qui contient un sous- `AddMenuCommands`menu ajouté par). L’infrastructure appelle également ces trois méthodes pour ajouter automatiquement des commandes. Si vous souhaitez qu’une commande soit représentée par un type dérivé à la place `ReplaceButton` , appelez et transmettez un bouton du type dérivé.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `ReplaceButton` méthode dans la `CMFCToolBarsCustomizeDialog` classe. Cet extrait de code fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory

Spécifie quelle catégorie dans la liste des catégories de la page **commandes** est la catégorie utilisateur. Vous devez appeler cette fonction avant d’appeler [CMFCToolBarsCustomizeDialog:: Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Paramètres

*lpszCategory*<br/>
dans Nom de la catégorie.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode réussit; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le paramètre de catégorie d’utilisateur n’est pas utilisé actuellement par le Framework.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet, classe](../../mfc/reference/cpropertysheet-class.md)
