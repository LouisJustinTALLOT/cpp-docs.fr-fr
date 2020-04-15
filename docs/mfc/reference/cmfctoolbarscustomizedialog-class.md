---
title: CMFCToolBarsCustomizeDialog Classe
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
ms.openlocfilehash: d47ecf45a7bbfc563be0c05cd15ee84d430f502f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377363"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog Classe

Une boîte de dialogue d’onglets sans mode [(CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)) qui permet à l’utilisateur de personnaliser les barres d’outils, les menus, les raccourcis clavier, les outils définis par l’utilisateur et le style visuel dans une application. En général, l'utilisateur accède à cette boîte de dialogue en sélectionnant **Personnaliser** dans le menu **Outils** .

La boîte de dialogue **personnaliser** a six onglets: **Commandes**, **Toolbars**, **Outils**, **Clavier**, **Menu**, et **Options**.

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
|[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Insère un bouton de barre d’outils dans la liste des commandes sur la page **Commandes**|
|[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Charge un menu à partir des ressources et appelle [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste des commandes sur la page **Commandes.**|
|[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Charge un menu à partir des ressources et appelle [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste des commandes sur la page **Commandes.**|
|[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Charge une barre d’outils à partir des ressources. Ensuite, pour chaque commande dans le menu appelle le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode pour insérer un bouton dans la liste des commandes sur la page **Commandes** dans la catégorie spécifiée.|
|[CMFCToolBarsCustomizeDialog::Créer](#create)|Affiche la boîte de dialogue **de personnalisation.**|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Réservé pour un usage futur.|
|[CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Permet ou désactive la création de nouvelles barres d’outils en utilisant la boîte de dialogue **Customize.**|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Remplit l’objet fourni `CListBox` avec les commandes dans la catégorie All **Commands.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Remplit l’objet fourni `CComboBox` avec le nom de chaque catégorie de commande dans la boîte de dialogue **Customize.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Remplit l’objet fourni `CListBox` avec le nom de chaque catégorie de commande dans la boîte de dialogue **Customize.**|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Récupère le nom associé à l’ID de commande donné.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Récupère le nombre d’articles dans la liste fournie qui ont une étiquette de texte donnée.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Récupère l’ensemble des drapeaux qui affectent le comportement de la boîte de dialogue.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Démarre un éditeur d’images afin qu’un utilisateur puisse personnaliser un bouton de barre d’outils ou une icône d’élément de menu.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Remplacements pour augmenter l’initialisation des feuilles de propriété. (Overrides [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Appelé par le cadre après la fenêtre a été détruite. (Substitue `CPropertySheet::PostNcDestroy`.)|
|[CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Supprime le bouton avec l’ID de commande spécifié de la catégorie spécifiée, ou de toutes les catégories.|
|[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Renomme une catégorie dans la boîte de liste des catégories sur **l’onglet Commandes.**|
|[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Remplace un bouton dans la liste des commandes de **l’onglet Commandes** par un nouvel objet bouton de barre d’outils.|
|[CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Ajoute une catégorie à la liste des catégories qui seront affichées sur **l’onglet Commandes.**|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Appelé par le cadre pour déterminer si la liste des outils définis par l’utilisateur est valide.|
|[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Appelé par le cadre lorsque les propriétés d’un outil défini par l’utilisateur changent.|
|[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Détermine si un raccourci de clavier spécifié peut être affecté à une action.|
|[CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Détermine si un outil défini par l’utilisateur peut être modifié.|
|[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Appelé par le cadre lorsque l’utilisateur choisit l’onglet **Outils** est demandé.|

## <a name="remarks"></a>Notes

Pour afficher la boîte de dialogue `CMFCToolBarsCustomizeDialog` **Personnaliser,** créez un objet et appelez le [CMFCToolBarsCustomizeDialog::Créer la](#create) méthode.

Bien que la boîte de dialogue **Customize** soit active, l’application fonctionne dans un mode spécial qui limite l’utilisateur aux tâches de personnalisation.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCToolBarsCustomizeDialog` . L’exemple montre comment remplacer un bouton de barre d’outils dans la boîte de commande des commandes sur la page **Commandes,** activer la création de nouvelles barres d’outils en utilisant la boîte de dialogue **Personnaliser,** et afficher la boîte de dialogue **Customization.** Cet extrait de code fait partie de [l’échantillon de démonstration IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxToolBarsCustomizeDialog.h

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a>CMFCToolBarsCustomizeDialog::AddButton

Insère un bouton de barre d’outils dans la liste des commandes sur la page **Commandes.**

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
[dans] Spécifie l’ID de catégorie dans lequel insérer le bouton.

*Bouton*<br/>
[dans] Spécifie le bouton à insérer.

*iInsertBefore*<br/>
[dans] Spécifie l’index zéro d’un bouton de barre d’outils avant lequel le bouton est inséré.

*lpszCategory*<br/>
[dans] Spécifie la chaîne de catégorie pour insérer le bouton.

### <a name="remarks"></a>Notes

La `AddButton` méthode ignore les boutons qui ont les adresses d’adresse standard (comme ID_FILE_MRU_FILE1), les commandes qui ne sont pas autorisées (voir [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) et les boutons factices.

Cette méthode crée un nouvel objet `button` du même type que (généralement une [classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)) en utilisant la classe de temps d’exécution du bouton. Il appelle ensuite [CMFCToolBarButton::CopyDe](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) pour copier les membres de données du bouton, et insère la copie dans la catégorie spécifiée.

Lorsque le nouveau bouton est inséré, il reçoit la `OnAddToCustomizePage` notification.

S’il `iInsertBefore` s’agit de -1, le bouton est annexé à la liste des catégories; sinon il est inséré avant l’élément avec l’index spécifié.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `AddButton` utiliser `CMFCToolBarsCustomizeDialog` la méthode de la classe. Cet extrait de code fait partie de [l’échantillon Slider](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a>CMFCToolBarsCustomizeDialog::AddMenu

Charge un menu à partir des ressources et appelle [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) pour ajouter ce menu à la liste des commandes sur la page **Commandes.**

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Paramètres

*uiMenuResId*<br/>
[dans] Spécifie l’ID de ressources d’un menu à charger.

### <a name="return-value"></a>Valeur de retour

VRAI si un menu a été ajouté avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Dans l’appel à `AddMenuCommands`, *bPopup* est FALSE. Par conséquent, cette méthode n’ajoute pas d’éléments de menu qui contiennent des sous-ensembles à la liste des commandes. Cette méthode ajoute les éléments de menu dans le sous-genre à la liste des commandes.

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands

Ajoute des éléments à la liste des commandes de la page **Commandes** pour représenter tous les éléments du menu spécifié.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Paramètres

*pMenu*<br/>
[dans] Un pointeur à l’objet CMenu à ajouter.

*bPopup (en)*<br/>
[dans] Précise s’il faut insérer les éléments du menu popup à la liste des commandes.

*lpszCategory*<br/>
[dans] Le nom de la catégorie pour insérer le menu.

*lpszMenuPath*<br/>
[dans] Un préfixe qui est ajouté au nom lorsque la commande est affichée dans la liste **Toutes catégories.**

### <a name="remarks"></a>Notes

La `AddMenuCommands` méthode boucles sur tous les éléments de menu de *pMenu*. Pour chaque élément de menu qui ne contient pas de sous-ménue, cette méthode crée un objet [cmFCToolBarButton Classe](../../mfc/reference/cmfctoolbarbutton-class.md) et appelle le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode pour ajouter l’élément de menu comme un bouton de barre d’outils à la liste des commandes sur la page **commandes.** Les séparateurs sont ignorés dans ce processus.

Si *bPopup* est VRAI, pour chaque élément de menu qui contient un sous-mois cette méthode crée un objet [cmFCToolBarMenuButton Classe](../../mfc/reference/cmfctoolbarmenubutton-class.md) et l’insère dans la liste des commandes en appelant `AddButton`. Sinon, les éléments de menu qui contiennent sous-genre ne sont pas affichés dans la liste des commandes. Dans les deux `AddMenuCommands` cas, lorsque rencontre un élément de menu avec un sous-mois, il s’appelle de façon récursive, en passant un pointeur sur le sous-mois comme le paramètre *pMenu* et en passant l’étiquette du sous-mois à *lpszMenuPath*.

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar

Charge une barre d’outils à partir des ressources. Ensuite, pour chaque commande dans le menu appelle le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode pour insérer un bouton dans la liste des commandes sur la page **Commandes** dans la catégorie spécifiée.

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
[dans] Spécifie l’ID de ressource de la catégorie pour ajouter la barre d’outils à.

*uiToolbarResId*<br/>
[dans] Précise l’id de ressource d’une barre d’outils dont les commandes sont insérées dans la liste des commandes.

*lpszCategory*<br/>
[dans] Spécifie le nom de la catégorie à laquelle ajouter la barre d’outils.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode est réussie; autrement FALSE.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `AddToolBar` utiliser `CMFCToolBarsCustomizeDialog` la méthode dans la classe. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Notes

Le contrôle utilisé pour représenter chaque commande est un objet [cmFCToolBarButton Class.](../../mfc/reference/cmfctoolbarbutton-class.md) Après avoir ajouté la barre d’outils, vous pouvez remplacer le bouton par un contrôle d’un type dérivé en appelant [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsValidity

Vérifie la validité de la liste des outils utilisateur.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Paramètres

*lstTools*<br/>
[dans] La liste des outils définis par l’utilisateur à vérifier.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la liste des outils définis par l’utilisateur est valide; autrement FALSE. L’implémentation par défaut renvoie toujours TRUE.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode pour vérifier la validité des objets qui représentent des outils définis par l’utilisateur retournés par [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).

Remplacer la `CheckToolsValidity` méthode dans une `CMFCToolBarsCustomizeDialog` classe dérivée si vous souhaitez valider les outils utilisateur avant que l’utilisateur ferme la boîte de dialogue. Si cette méthode renvoie FALSE lorsque l’utilisateur clique soit sur le bouton **Close** dans le coin supérieur droit de la boîte de dialogue ou le bouton étiqueté **Close** dans le coin inférieur droit de la boîte de dialogue, la boîte de dialogue affiche l’onglet **Outils** au lieu de se fermer. Si cette méthode renvoie FALSE lorsque l’utilisateur clique sur un onglet pour naviguer loin de l’onglet **Outils,** la navigation ne se produit pas. Vous devez afficher une boîte de message appropriée pour informer l’utilisateur du problème qui a causé l’échec de la validation.

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

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
[dans] Un pointeur sur le cadre parent. Ce paramètre ne doit pas être NULL.

*bAutoSetDeMenus*<br/>
[dans] Une valeur Boolean qui précise s’il faut ajouter les commandes de menu de tous les menus à la liste des commandes sur la page **Commandes.** Si ce paramètre est VRAI, les commandes du menu sont ajoutées. Sinon, les commandes de menu ne sont pas ajoutées.

*uiFlags uiFlags*<br/>
[dans] Une combinaison de drapeaux qui affectent le comportement de la boîte de dialogue. Ce paramètre peut être une ou plusieurs des valeurs suivantes :

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[dans] Un pointeur vers `CRuntimeClass` une liste d’objets qui spécifient des pages personnalisées supplémentaires.

### <a name="remarks"></a>Notes

Le *paramètre plistCustomPages* fait `CRuntimeClass` référence à la liste des objets qui spécifient des pages personnalisées supplémentaires. Le constructeur ajoute plus de pages à la boîte de dialogue en utilisant la méthode [CRuntimeClass::CreateObject.](../../mfc/reference/cruntimeclass-structure.md#createobject) Consultez l’échantillon CustomPages par exemple qui ajoute plus de pages à la boîte de dialogue **Customize.**

Pour plus d’informations sur les valeurs que vous pouvez passer dans le paramètre *uiFlags,* voir [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCToolBarsCustomizeDialog` un objet de la classe. Cet extrait de code fait partie de [l’échantillon de pages personnalisées](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a>CMFCToolBarsCustomizeDialog::Créer

Affiche la boîte de dialogue **de personnalisation.**

```
virtual BOOL Create();
```

### <a name="return-value"></a>Valeur de retour

VRAI si la feuille de propriété de personnalisation est créée avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez `Create` la méthode seulement après avoir complètement initialisé la classe.

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Permet ou désactive la création de nouvelles barres d’outils en utilisant la boîte de dialogue **Customize.**

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour permettre les barres d’outils définies par l’utilisateur; FALSE pour désactiver les barres d’outils.

### <a name="remarks"></a>Notes

Si *bEnable* est VRAI, les boutons **New**, **Rename** et **Supprimer** s’affichent sur la page **Toolbars.**

Par défaut, ou si *bEnable* est FALSE, ces boutons ne sont pas affichés et l’utilisateur ne peut pas définir de nouvelles barres d’outils.

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList

Remplit l’objet fourni `CListBox` avec les commandes dans la catégorie All **Commands.**

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Paramètres

*wndListOfCommands (wndListOfCommands)*<br/>
[out] Une référence `CListBox` à l’objet de peuplement.

### <a name="remarks"></a>Notes

La catégorie **All Commands** contient les commandes de toutes les catégories. Le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode ajoute la commande qui est associée au bouton fourni à la catégorie **Toutes les commandes** pour vous.

Cette méthode efface le contenu `CListBox` de l’objet fourni avant de le remplir avec les commandes dans la catégorie **All Commands.**

La `CMFCMousePropertyPage` classe utilise cette méthode pour remplir la case de liste d’événements en double clic.

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Remplit l’objet fourni `CComboBox` avec le nom de chaque catégorie de commande dans la boîte de dialogue **Customize.**

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*wndCategory wndCategory*<br/>
[out] Une référence `CComboBox` à l’objet de peuplement.

*bAddEmpty (en)*<br/>
[dans] Une valeur Boolean qui spécifie s’il faut ajouter des catégories à la boîte combo qui n’ont pas de commandes. Si ce paramètre est VRAI, des catégories vides sont ajoutées à la boîte combo. Sinon, les catégories vides ne sont pas ajoutées.

### <a name="remarks"></a>Notes

Cette méthode est comme le [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) méthode `CComboBox` sauf que cette méthode fonctionne avec un objet.

Cette méthode n’efface pas `CComboBox` le contenu de l’objet avant de le peupler. Il garantit que la catégorie **All Commands** est l’élément final de la boîte combo.

Vous pouvez ajouter de nouvelles catégories de commandes en utilisant le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode. Vous pouvez changer le nom d’une catégorie existante en utilisant le [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) méthode.

Les `CMFCToolBarsKeyboardPropertyPage` `CMFCKeyMapDialog` classes et les classes utilisent cette méthode pour catégoriser les cartes du clavier.

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Remplit l’objet fourni `CListBox` avec le nom de chaque catégorie de commande dans la boîte de dialogue **Customize.**

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*wndCategory wndCategory*<br/>
[out] Une référence `CListBox` à l’objet de peuplement.

*bAddEmpty (en)*<br/>
[dans] Une valeur Boolean qui spécifie s’il faut ajouter des catégories à la boîte de liste qui n’ont pas de commandes. Si ce paramètre est VRAI, des catégories vides sont ajoutées à la case liste. Sinon, les catégories vides ne sont pas ajoutées.

### <a name="remarks"></a>Notes

Cette méthode est comme le [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) méthode, `CListBox` sauf que cette méthode fonctionne avec un objet.

Cette méthode n’efface pas `CListBox` le contenu de l’objet avant de le peupler. Il garantit que la catégorie **All Commands** est l’élément final de la case.

Vous pouvez ajouter de nouvelles catégories de commandes en utilisant le [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) méthode. Vous pouvez changer le nom d’une catégorie existante en utilisant le [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) méthode.

La `CMFCToolBarsCommandsPropertyPage` classe utilise cette méthode pour afficher la liste des commandes associées à chaque catégorie de commande.

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a>CMFCToolBarsCustomizeDialog::GetCommandName

Récupère le nom associé à l’ID de commande donné.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’identification de la commande à récupérer.

### <a name="return-value"></a>Valeur de retour

Le nom associé à l’ID de commande donné, ou NULL si la commande n’existe pas.

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory

Récupère le nombre d’articles dans la liste fournie qui ont une étiquette de texte donnée.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Paramètres

*lpszItemName (en)*<br/>
[dans] L’étiquette de texte pour correspondre.

*lstCommands*<br/>
[dans] Une référence à une `CMFCToolBarButton` liste qui contient des objets.

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments de la liste fournie dont l’étiquette de texte équivaut *à lpszItemName*.

### <a name="remarks"></a>Notes

Chaque élément de la liste d’objets fournis doit être de type `CMFCToolBarButton`. Cette méthode compare *lpszItemName* avec le [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) membre des données.

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a>CMFCToolBarsCustomizeDialog::GetFlags

Récupère l’ensemble des drapeaux qui affectent le comportement de la boîte de dialogue.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Valeur de retour

L’ensemble des drapeaux qui affectent le comportement de la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette méthode récupère la valeur du paramètre *uiFlags* qui est transmis au constructeur. La valeur de rendement peut être une ou plusieurs des valeurs suivantes :

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Permet à l’utilisateur de spécifier l’apparence de l’ombre du menu.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Permet à l’utilisateur de spécifier si des étiquettes de texte sont affichées sous les images du bouton de la barre d’outils.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Permet à l’utilisateur de spécifier le style d’animation du menu.  |
|AFX_CUSTOMIZE_NOHELP|Supprime le bouton d’aide de la boîte de dialogue de personnalisation.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Permet le style visuel WS_EX_CONTEXTHELP.  |
|AFX_CUSTOMIZE_NOTOOLS|Supprime la page **Outils** de la boîte de dialogue de personnalisation. Ce drapeau est valide si `CUserToolsManager` votre application utilise la classe.  |
|AFX_CUSTOMIZE_MENUAMPERS|Permet aux sous-légendes de **&** bouton de contenir le caractère ampersand .  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Supprime l’option **Grandes Icônes** de la boîte de dialogue de personnalisation.  |

Pour plus d’informations sur le style visuel WS_EX_CONTEXTHELP, voir [Extended Window Styles](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Réagit à un changement d’outil utilisateur immédiatement après qu’il se produise.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Paramètres

*pSelTool (en)*<br/>
[dans, dehors] Un pointeur vers l’objet de l’outil utilisateur qui a été changé.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre lorsqu’un utilisateur modifie les propriétés d’un outil défini par l’utilisateur. L'implémentation par défaut n'exécute aucune opération. Remplacer cette méthode dans une `CMFCToolBarsCustomizeDialog` classe dérivée de l’exécution du traitement après une modification à un outil utilisateur se produit.

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey

Valide les raccourcis clavier comme un utilisateur les définit.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Paramètres

*pAccel (en)*<br/>
[dans, dehors] Pointeur de l’assigment de clavier proposé qui est exprimé comme une struct [ACCEL.](/windows/win32/api/winuser/ns-winuser-accel)

### <a name="return-value"></a>Valeur de retour

VRAI si la clé peut être assignée, ou FALSE si la clé ne peut pas être assignée. L’implémentation par défaut renvoie toujours TRUE.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour effectuer un traitement supplémentaire lorsqu’un utilisateur assigne un nouveau raccourci clavier, ou pour valider les raccourcis clavier tel que l’utilisateur les définit. Pour éviter qu’un raccourci ne soit attribué, retournez FALSE. Vous devez également afficher une boîte de message ou informer l’utilisateur de la raison pour laquelle le raccourci clavier a été rejeté.

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Effectue un traitement personnalisé lorsqu’une modification est apportée à un outil utilisateur lorsque l’utilisateur est sur le point d’appliquer une modification.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Paramètres

*pSelTool (en)*<br/>
[dans, dehors] Un pointeur à l’objet d’outil utilisateur qui est sur le point d’être remplacé.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre lorsque les propriétés d’un outil défini par l’utilisateur est sur le point de changer. L'implémentation par défaut n'exécute aucune opération. Remplacer la `OnBeforeChangeTool` méthode dans une `CMFCToolBarsCustomizeDialog` classe dérivée de si vous voulez effectuer le traitement avant qu’une modification à un outil utilisateur se produise, comme la libération des ressources que *pSelTool* utilise.

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Démarre un éditeur d’images afin qu’un utilisateur puisse personnaliser un bouton de barre d’outils ou une icône d’élément de menu.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Un pointeur à la fenêtre parente.

*Bitmap*<br/>
[dans] Une référence à un objet bitmap à modifier.

*nBitsPerPixel*<br/>
[dans] Résolution de couleur De Bitmap, en bits par pixel.

### <a name="return-value"></a>Valeur de retour

VRAI si un changement est engagé; autrement FALSE. L’implémentation par défaut affiche une boîte de dialogue et renvoie TRUE si l’utilisateur clique **sur OK,** ou FALSE si l’utilisateur clique **Annuler** ou le bouton **Close.**

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre lorsque l’utilisateur exécute l’éditeur d’images. L’implémentation par défaut affiche la boîte de dialogue [cmFCImageEditorDialog Class.](../../mfc/reference/cmfcimageeditordialog-class.md) Remplacer `OnEditToolbarMenuImage` dans une classe dérivée pour utiliser un éditeur d’images personnalisé.

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog::OnInitDialog

Remplacements pour augmenter l’initialisation des feuilles de propriété.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Le résultat de l’appel de la [feuille CProperty::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) méthode.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base, [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), en affichant le bouton **Close,** en s’assurant que la boîte de dialogue correspond à la taille actuelle de l’écran, et en déplaçant le bouton **d’aide** vers le coin inférieur gauche de la boîte de dialogue.

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage

Gère la notification à partir du cadre que la page **Tools** est sur le point d’être parasémentée.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Remplacer cette méthode dans une classe dérivée pour traiter cette notification.

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::PostNcDestroy

Appelé par le cadre après la fenêtre a été détruite.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Notes

Cette méthode étend la `CPropertySheet::PostNcDestroy`mise en œuvre de la classe de base, en rétablissant l’application au mode précédent.

Le [CMFCToolBarsCustomizeDialog: :Créer](#create) la méthode met l’application dans un mode spécial qui limite l’utilisateur aux tâches de personnalisation.

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a>CMFCToolBarsCustomizeDialog::RemoveButton

Supprime le bouton avec l’ID de commande spécifié de la catégorie spécifiée, ou de toutes les catégories.

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
[dans] Spécifie l’ID de catégorie à partir duquel supprimer le bouton.

*uiCmdId*<br/>
[dans] Spécifie l’ID de commande du bouton.

*lpszCategory*<br/>
[dans] Spécifie le nom de la catégorie à partir de laquelle supprimer le bouton.

### <a name="return-value"></a>Valeur de retour

L’index à base nulle du bouton supprimé, ou -1 si l’ID de commande spécifié n’a pas été trouvé dans la catégorie spécifiée. Si *uiCategoryId* est de -1, la valeur de retour est de 0.

### <a name="remarks"></a>Notes

Pour supprimer un bouton de toutes les catégories, appelez la première surcharge de cette méthode et définissez *uiCategoryId* à -1.

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::RenameCategory

Renomme une catégorie dans la liste des catégories sur la page **Commandes.**

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Paramètres

*lpszCategoryOld*<br/>
[dans] Le nom de catégorie à changer.

*lpszCategoryNouvelle*<br/>
[dans] Le nouveau nom de catégorie.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Le nom de la catégorie doit être unique.

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a>CMFCToolBarsCustomizeDialog::ReplaceButton

Remplace un bouton de barre d’outils dans la boîte de commande des commandes sur la page **Commandes.**

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] Spécifie la commande du bouton à remplacer.

*Bouton*<br/>
[dans] Une référence **const** à l’objet bouton de barre d’outils qui remplace l’ancien bouton.

### <a name="remarks"></a>Notes

Quand [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands), ou [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) ajoute une commande à la page **Commandes,** cette commande est sous la forme d’un objet [cmFCToolBarButton Classe](../../mfc/reference/cmfctoolbarbutton-class.md) (ou `AddMenuCommands`un objet [cmFCToolBarMenuButton Classe](../../mfc/reference/cmfctoolbarmenubutton-class.md) pour un élément de menu qui contient un sous-mois ajouté par ). Le cadre appelle également ces trois méthodes pour ajouter automatiquement des commandes. Si vous voulez qu’une commande soit représentée `ReplaceButton` par un type dérivé à la place, appelez et passez sur un bouton du type dérivé.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `ReplaceButton` utiliser `CMFCToolBarsCustomizeDialog` la méthode dans la classe. Cet extrait de code fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUserCategory

Précise quelle catégorie dans la liste des catégories sur la page **Commandes** est la catégorie utilisateur. Vous devez appeler cette fonction avant d’appeler [CMFCToolBarsCustomizeDialog::Créer](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Paramètres

*lpszCategory*<br/>
[dans] Le nom de la catégorie.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode est réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Le paramètre de la catégorie utilisateur n’est pas actuellement utilisé par le cadre.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet, classe](../../mfc/reference/cpropertysheet-class.md)
