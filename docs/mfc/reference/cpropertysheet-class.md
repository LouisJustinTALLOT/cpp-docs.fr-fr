---
title: CPropertySheet (classe)
ms.date: 11/04/2016
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
ms.openlocfilehash: 23d17aee2aacbc1484c0f3e181bc824546ab49a2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502822"
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
|[CPropertySheet:: Construct](#construct)|Construit un objet `CPropertySheet`.|
|[CPropertySheet::Create](#create)|Affiche une feuille de propriétés non modale.|
|[CPropertySheet::DoModal](#domodal)|Affiche une feuille de propriétés modale.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Indique si la feuille de propriétés utilise des onglets empilés ou de défilement.|
|[CPropertySheet::EndDialog](#enddialog)|Met fin à la feuille de propriétés.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Récupère l’index de la page active de la feuille de propriétés.|
|[CPropertySheet:: GetActivePage](#getactivepage)|Retourne l’objet de la page active.|
|[CPropertySheet::GetPage](#getpage)|Récupère un pointeur vers la page spécifiée.|
|[CPropertySheet::GetPageCount](#getpagecount)|Récupère le nombre de pages dans la feuille de propriétés.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Récupère l’index de la page spécifiée de la feuille de propriétés.|
|[CPropertySheet:: GetTabControl](#gettabcontrol)|Récupère un pointeur vers un contrôle onglet.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Convertit les unités de boîte de dialogue d’un rectangle en unités d’écran.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Substituez pour augmenter l’initialisation de la feuille de propriétés.|
|[CPropertySheet::PressButton](#pressbutton)|Simule le choix du bouton spécifié dans une feuille de propriétés.|
|[CPropertySheet::RemovePage](#removepage)|Supprime une page de la feuille de propriétés.|
|[CPropertySheet::SetActivePage](#setactivepage)|Définit par programmation l’objet de la page active.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Définit le texte pour le bouton Terminer.|
|[CPropertySheet::SetTitle](#settitle)|Définit la légende de la feuille de propriétés.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Active les boutons de l’Assistant.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Active le mode Assistant.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Structure [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) de Windows. Fournit l’accès aux paramètres de la feuille de propriétés de base.|

## <a name="remarks"></a>Notes

Une feuille de propriétés se compose `CPropertySheet` d’un objet et d’un ou plusieurs objets [CPropertyPage](../../mfc/reference/cpropertypage-class.md) . L’infrastructure affiche une feuille de propriétés sous la forme d’une fenêtre avec un ensemble d’index de tabulation et une zone qui contient la page actuellement sélectionnée. L’utilisateur accède à une page spécifique à l’aide de l’onglet approprié.

`CPropertySheet`prend en charge la structure [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) développée introduite dans Windows 98 et windows NT 2000. La structure contient des indicateurs et des membres supplémentaires qui prennent en charge l’utilisation d’une image bitmap d’arrière-plan «Watermark».

Pour afficher automatiquement ces nouvelles images dans votre objet de feuille de propriétés, transmettez des valeurs valides pour les images bitmap et de palette dans l’appel à [CPropertySheet:: Construct](#construct) ou [CPropertySheet:: CPropertySheet](#cpropertysheet).

Même si `CPropertySheet` n’est pas dérivé de [CDialog](../../mfc/reference/cdialog-class.md), la `CPropertySheet` gestion d’un objet est `CDialog` semblable à la gestion d’un objet. Par exemple, la création d’une feuille de propriétés requiert une construction en deux parties: appeler le constructeur, puis appeler [DoModal](#domodal) pour une feuille de propriétés modale ou [Create](#create) pour une feuille de propriétés non modale. `CPropertySheet`a deux types de constructeurs: [CPropertySheet:: Construct](#construct) et [CPropertySheet:: CPropertySheet](#cpropertysheet).

Lorsque vous construisez `CPropertySheet` un objet, certains [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) peuvent provoquer une exception de première chance. Cela résulte du système tentant de modifier le style de la feuille de propriétés avant la création de la feuille. Pour éviter cette exception, veillez à définir les styles suivants lors de la création de `CPropertySheet`votre:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Les styles suivants sont facultatifs et ne provoquent pas l’exception de première chance:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Les autres `Window Styles` sont interdits et vous ne devez pas les activer.

L’échange de données entre `CPropertySheet` un objet et un objet externe est semblable à l’échange de données `CDialog` avec un objet. La différence importante réside dans le fait que les paramètres d’une feuille de propriétés sont généralement `CPropertyPage` des variables membres des objets `CPropertySheet` plutôt que de l’objet lui-même.

Vous pouvez créer un type de boîte de dialogue d’onglet appelé Assistant, qui se compose d’une feuille de propriétés avec une séquence de pages de propriétés qui guident l’utilisateur tout au long des étapes d’une opération, telles que la configuration d’un appareil ou la création d’un bulletin d’informations. Dans une boîte de dialogue d’onglets de type assistant, les pages de propriétés n’ont pas d’onglets et une seule page de propriétés est visible à la fois. En outre, au lieu d’avoir **OK** et **appliquer maintenant** boutons, une boîte de dialogue type d’Assistant onglet a un **retour** bouton, un **suivant** ou **Terminer** bouton, un **Annuler** bouton et un **aide** bouton.

Pour créer une boîte de dialogue de type assistant, suivez les mêmes étapes que celles que vous devez suivre pour créer une feuille de propriétés standard, mais appelez [SetWizardMode](#setwizardmode) avant d’appeler [DoModal](#domodal). Pour activer les boutons de l’Assistant, appelez [SetWizardButtons](#setwizardbuttons), en utilisant des indicateurs pour personnaliser leur fonction et leur apparence. Pour activer le bouton **Terminer** , appelez [SetFinishText](#setfinishtext) après que l’utilisateur a effectué une action sur la dernière page de l’Assistant.

Pour plus d’informations sur l’utilisation `CPropertySheet` des objets, consultez l’article [feuilles de propriétés et pages de propriétés](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxdlgs. h

##  <a name="addpage"></a>  CPropertySheet::AddPage

Ajoute la page fournie avec l’onglet le plus à droite dans la feuille de propriétés.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
Pointe vers la page à ajouter à la feuille de propriétés. Ne peut pas être Null.

### <a name="remarks"></a>Notes

Ajoutez des pages à la feuille de propriétés dans l’ordre de gauche à droite dans lequel vous souhaitez qu’elles apparaissent.

`AddPage`Ajoute l’objet [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) à la `CPropertySheet` liste des pages de l’objet, mais ne crée pas réellement la fenêtre pour la page. L’infrastructure diffère la création de la fenêtre pour la page jusqu’à ce que l’utilisateur sélectionne cette page.

Quand vous ajoutez une page de propriétés `AddPage`à l' `CPropertySheet` aide de, `CPropertyPage`est le parent de. Pour accéder à la feuille de propriétés à partir de la page de propriétés, appelez [CWnd:: GetParent](../../mfc/reference/cwnd-class.md#getparent).

Il n’est pas nécessaire d’attendre jusqu’à la création de la fenêtre de `AddPage`la feuille de propriétés pour appeler. En général, vous appelez `AddPage` avant d’appeler [DoModal](#domodal) ou [Create](#create).

Si vous appelez `AddPage` après avoir affiché la page de propriétés, la ligne de l’onglet reflète la page qui vient d’être ajoutée.

### <a name="example"></a>Exemples

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

*nIDCaption*<br/>
ID de la légende à utiliser pour la feuille de propriétés.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente de la feuille de propriétés. Si la valeur est NULL, la fenêtre parente est la fenêtre principale de l’application.

*iSelectPage*<br/>
Index de la page qui sera initialement en haut. La valeur par défaut est la première page ajoutée à la feuille.

*pszCaption*<br/>
Pointeur vers une chaîne contenant la légende à utiliser pour la feuille de propriétés. Ne peut pas être Null.

*hbmWatermark*<br/>
Handle de la bitmap de filigrane de la page de propriétés.

*hpalWatermark*<br/>
Handle vers la palette de la bitmap de filigrane et/ou de l’image bitmap d’en-tête.

*hbmHeader*<br/>
Handle vers l’image bitmap d’en-tête de la page de propriétés.

### <a name="remarks"></a>Notes

Appelez cette fonction membre si l’un des constructeurs de classe n’a pas déjà été appelé. Par exemple, appelez `Construct` lorsque vous déclarez ou allouez des `CPropertySheet` tableaux d’objets. Dans le cas de tableaux, vous devez appeler `Construct` pour chaque membre du tableau.

Pour afficher la feuille de propriétés, appelez [DoModal](#domodal) ou [Create](#create). La chaîne contenue dans le premier paramètre sera placée dans la barre de légende de la feuille de propriétés.

Vous pouvez afficher automatiquement les images de filigrane et/ou d’en-tête si vous utilisez le troisième `Construct`ou le quatrième prototypes de, répertorié ci-dessus, et que vous transmettez des valeurs valides pour les paramètres *hbmWatermark*, *hpalWatermark*et/ou *hbmHeader* .

### <a name="example"></a>Exemples

L’exemple suivant illustre les circonstances que vous appelez `Construct`.

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

*nIDCaption*<br/>
ID de la légende à utiliser pour la feuille de propriétés.

*pParentWnd*<br/>
Pointe vers la fenêtre parente de la feuille de propriétés. Si la valeur est NULL, la fenêtre parente est la fenêtre principale de l’application.

*iSelectPage*<br/>
Index de la page qui sera initialement en haut. La valeur par défaut est la première page ajoutée à la feuille.

*pszCaption*<br/>
Pointe vers une chaîne contenant la légende à utiliser pour la feuille de propriétés. Ne peut pas être Null.

*hbmWatermark*<br/>
Handle vers l’image bitmap d’arrière-plan de la feuille de propriétés.

*hpalWatermark*<br/>
Handle vers la palette de la bitmap de filigrane et/ou de l’image bitmap d’en-tête.

*hbmHeader*<br/>
Handle de la bitmap d’en-tête de la page de propriétés.

### <a name="remarks"></a>Notes

Pour afficher la feuille de propriétés, appelez [DoModal](#domodal) ou [Create](#create). La chaîne contenue dans le premier paramètre sera placée dans la barre de légende de la feuille de propriétés.

Si vous avez plusieurs paramètres (par exemple, si vous utilisez un tableau), utilisez [Construct](#construct) au lieu de `CPropertySheet`.

Vous pouvez afficher automatiquement les images de filigrane et/ou d’en-tête si vous utilisez le troisième `CPropertySheet`ou le quatrième prototypes de, ci-dessus, et que vous transmettez des valeurs valides pour les paramètres *hbmWatermark*, *hpalWatermark*et/ou *hbmHeader* .

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

*pParentWnd*<br/>
Pointe vers la fenêtre parente. Si la valeur est NULL, le parent est le bureau.

*dwStyle*<br/>
Styles de fenêtre pour la feuille de propriétés. Pour obtenir la liste complète des styles disponibles, consultez [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Styles de fenêtre étendus pour la feuille de propriétés. Pour obtenir la liste complète des styles disponibles, consultez [styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) .

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la feuille de propriétés est créée avec succès; Sinon, 0.

### <a name="remarks"></a>Notes

L’appel à `Create` peut se trouver à l’intérieur du constructeur, ou vous pouvez l’appeler une fois que le constructeur est appelé.

Le style par défaut, exprimé en passant-1 comme *dwStyle*, est en&#124;fait&#124;WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME DS_CONTEXTHELP WS_VISIBLE. Le style de fenêtre étendue par défaut, exprimé en passant 0 comme *dwExStyle*, est en fait WS_EX_DLGMODALFRAME.

La `Create` fonction membre retourne immédiatement après la création de la feuille de propriétés. Pour supprimer la feuille de propriétés, appelez [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow).

Les feuilles de propriétés non modales affichées avec `Create` un appel à n’ont pas les boutons OK, annuler, appliquer maintenant et aide comme les feuilles de propriétés modales. Les boutons souhaités doivent être créés par l’utilisateur.

Pour afficher une feuille de propriétés modale, appelez plutôt [DoModal](#domodal) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>  CPropertySheet::DoModal

Affiche une feuille de propriétés modale.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL si la fonction a réussi; Sinon, 0 ou-1. Si la feuille de propriétés a été établie en tant qu’Assistant (voir [SetWizardMode](#setwizardmode)), `DoModal` retourne ID_WIZFINISH ou IDCANCEL.

### <a name="remarks"></a>Notes

La valeur de retour correspond à l’ID du contrôle qui a fermé la feuille de propriétés. Une fois cette fonction retournée, les fenêtres correspondant à la feuille de propriétés et à toutes les pages ont été détruites. Les objets eux-mêmes existent toujours. En règle générale, vous récupérez des données à partir des objets [CPropertyPage](../../mfc/reference/cpropertypage-class.md) une fois que `DoModal` retourne IDOK.

Pour afficher une feuille de propriétés non modale, appelez [Create](#create) à la place.

Quand une page de propriétés est créée à partir de sa ressource de boîte de dialogue correspondante, elle peut provoquer une exception de première chance. Cela se produit à partir de la page de propriétés, en remplaçant le style de la ressource de boîte de dialogue par le style requis avant la création de la page. Étant donné que les ressources sont généralement en lecture seule, cela provoque une exception. Le système gère l’exception et effectue une copie de la ressource modifiée. L’exception de première chance peut donc être ignorée.

> [!NOTE]
>  Cette exception doit être gérée par le système d’exploitation si vous compilez avec le modèle de gestion des exceptions asynchrone. Pour plus d’informations sur les modèles de gestion des exceptions, consultez [/Eh (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md). Dans ce cas, n’encapsulez pas `CPropertySheet::DoModal` les appels C++ à avec un bloc try-catch dans lequel catch gère toutes les exceptions, `catch (...)`par exemple,. Ce bloc gère l’exception destinée au système d’exploitation et provoque un comportement imprévisible. Toutefois, vous pouvez utiliser C++ en toute sécurité la gestion des exceptions avec des types d’exceptions spécifiques ou une gestion structurée des exceptions où l’exception de violation d’accès est transmise au système d’exploitation.

Pour éviter de générer cette exception de première chance, vous pouvez vous assurer manuellement que la feuille de propriétés possède les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles)corrects. Vous devez définir les styles suivants pour une feuille de propriétés:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Vous pouvez utiliser les styles facultatifs suivants sans provoquer une exception de première chance:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Désactivez tous les autres styles Windows, car ils ne sont pas compatibles avec les feuilles de propriétés. Ce Conseil ne s’applique pas aux styles étendus. La définition appropriée de ces styles standard garantit que la feuille de propriétés ne doit pas être modifiée et évitera la génération de l’exception de première chance.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet:: AddPage](#addpage).

##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs

Indique s’il faut empiler des lignes d’onglets dans une feuille de propriétés.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Paramètres

*bStacked*<br/>
Indique si les onglets empilés sont activés dans la feuille de propriétés. Désactivez les lignes empilées de balises en affectant à *bStacked* la valeur false.

### <a name="remarks"></a>Notes

Par défaut, si une feuille de propriétés possède plus d’onglets que dans une seule ligne de la largeur de la feuille de propriétés, les onglets sont empilés en plusieurs lignes. Pour utiliser les onglets de défilement au lieu des onglets `EnableStackedTabs` d’empilement, appelez avec *bStacked* défini sur false avant d’appeler [DoModal](#domodal) ou [Create](#create).

Vous devez appeler `EnableStackedTabs` lorsque vous créez une feuille de propriétés modale ou non modale. Pour incorporer ce style dans `CPropertySheet`une classe dérivée de, écrivez un gestionnaire de messages pour WM_CREATE. Dans la version substituée de [CWnd:: OnCreate](../../mfc/reference/cwnd-class.md#oncreate), appelez `EnableStackedTabs( FALSE )` avant d’appeler l’implémentation de la classe de base.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>  CPropertySheet::EndDialog

Met fin à la feuille de propriétés.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Paramètres

*nEndID*<br/>
Identificateur à utiliser comme valeur de retour de la feuille de propriétés.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur appuie sur le bouton OK, annuler ou fermer. Appelez cette fonction membre si un événement qui doit fermer la feuille de propriétés se produit.

Cette fonction membre est utilisée uniquement avec une boîte de dialogue modale.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet::P ressbutton](#pressbutton).

##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex

Obtient le numéro d’index de la page active de la fenêtre de la feuille de propriétés, puis utilise le numéro d' `GetPage`index retourné comme paramètre pour.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro d’index de la page active.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage

Récupère la page active de la fenêtre de la feuille de propriétés.

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

*nPage*<br/>
Index de la page souhaitée, à partir de 0. Doit être compris entre 0 et un nombre inférieur de pages dans la feuille de propriétés, inclus.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la page correspondant au paramètre *nPage* .

### <a name="example"></a>Exemples

Consultez l’exemple de [CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount

Détermine le nombre de pages actuellement dans la feuille de propriétés.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de pages dans la feuille de propriétés.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex

Récupère le numéro d’index de la page spécifiée dans la feuille de propriétés.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
Pointe vers la page avec l’index à rechercher. Ne peut pas être Null.

### <a name="return-value"></a>Valeur de retour

Numéro d’index d’une page.

### <a name="remarks"></a>Notes

Par exemple, vous pouvez utiliser `GetPageIndex` pour obtenir l’index de page afin d’utiliser [SetActivePage](#setactivepage) ou [GetPage](#getpage).

### <a name="example"></a>Exemples

Consultez l’exemple de [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl

Récupère un pointeur désignant un contrôle onglet pour effectuer une opération spécifique au contrôle onglet (autrement dit, utiliser l’une des API dans [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un contrôle onglet.

### <a name="remarks"></a>Notes

Par exemple, appelez cette fonction membre si vous souhaitez ajouter des bitmaps à chacun des onglets lors de l’initialisation.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>  CPropertySheet::m_psh

Structure dont les membres stockent les caractéristiques de [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2).

### <a name="remarks"></a>Notes

Utilisez cette structure pour initialiser l’apparence de la feuille de propriétés une fois qu’elle a été construite mais avant qu’elle ne soit affichée avec la fonction membre [DoModal](#domodal) . Par exemple, définissez le membre *dwSize nul* de `m_psh` sur la taille que vous souhaitez attribuer à la feuille de propriétés.

Pour plus d’informations sur cette structure, y compris la liste de ses membres, consultez PROPSHEETHEADER dans le SDK Windows.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect

Convertit les unités de boîte de dialogue d’un rectangle en unités d’écran.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient les coordonnées de la boîte de dialogue à convertir.

### <a name="remarks"></a>Notes

Les unités de boîte de dialogue sont exprimées en termes de l’unité de base de boîte de dialogue actuelle dérivée de la largeur et de la hauteur moyennes des caractères de la police utilisée pour le texte de la boîte de dialogue. Une unité horizontale est un quart de l’unité de largeur de base de la boîte de dialogue, et une unité verticale est un huitième de l’unité de hauteur de base de la boîte de dialogue.

La fonction Windows [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) retourne des informations sur la taille de la police système, mais vous pouvez spécifier une police différente pour chaque feuille de propriétés si vous utilisez le style DS_SETFONT dans le fichier de définition de ressource. La fonction Windows [MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) , décrite dans la SDK Windows, utilise la police appropriée pour cette boîte de dialogue.

La `MapDialogRect` fonction membre remplace les unités de boîte de dialogue dans *lpRect* par des unités d’écran (pixels) afin que le rectangle puisse être utilisé pour créer une boîte de dialogue ou positionner un contrôle dans une zone.

##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog

Substitue pour augmenter l’initialisation de la feuille de propriétés.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Spécifie si l’application a défini le focus d’entrée sur l’un des contrôles de la feuille de propriétés. Si `OnInitDialog` retourne une valeur différente de zéro, Windows définit le focus d’entrée sur le premier contrôle de la feuille de propriétés. L’application peut retourner 0 uniquement si elle a explicitement défini le focus d’entrée sur l’un des contrôles de la feuille de propriétés.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée en réponse au message WM_INITDIALOG. Ce message est envoyé à la feuille de propriétés lors des appels [Create](#create) ou [DoModal](#domodal), qui se produisent immédiatement avant l’affichage de la feuille de propriétés.

Substituez cette fonction membre si vous devez effectuer un traitement spécial lorsque la feuille de propriétés est initialisée. Dans la version substituée, appelez d’abord la classe `OnInitDialog` de base, mais ignorez sa valeur de retour. Normalement, vous retournerez la valeur TRUE à partir de votre fonction membre remplacée.

Vous n’avez pas besoin d’une entrée de table des messages pour cette fonction membre.

##  <a name="pressbutton"></a>  CPropertySheet::PressButton

Simule le choix du bouton spécifié dans une feuille de propriétés.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Paramètres

*nButton*<br/>
Nbouton Identifie le bouton à enfoncer. Ce paramètre peut prendre l’une des valeurs suivantes:

- PSBTN_BACK choisit le bouton précédent.

- PSBTN_NEXT choisit le bouton suivant.

- PSBTN_FINISH choisit le bouton Terminer.

- PSBTN_OK choisit le bouton OK.

- PSBTN_APPLYNOW choisit le bouton Appliquer maintenant.

- PSBTN_CANCEL choisit le bouton Annuler.

- PSBTN_HELP choisit le bouton aide.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le message SDK Windows Pressbutton, consultez [PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) .

Un appel à `PressButton` n’enverra pas la notification [PSN_APPLY](/windows/win32/Controls/psn-apply) à partir d’une page de propriétés au Framework. Pour envoyer cette notification, appelez [CPropertyPage:: OnOK](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>  CPropertySheet::RemovePage

Supprime une page de la feuille de propriétés et détruit la fenêtre associée.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
Pointe vers la page à supprimer de la feuille de propriétés. Ne peut pas être Null.

*nPage*<br/>
Index de la page à supprimer. Doit être compris entre 0 et un nombre inférieur de pages dans la feuille de propriétés, inclus.

### <a name="remarks"></a>Notes

L’objet [CPropertyPage](../../mfc/reference/cpropertypage-class.md) proprement dit n’est pas détruit tant que `CPropertySheet` le propriétaire de la fenêtre n’est pas fermé.

##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage

Modifie la page active.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
Index de la page à définir. Elle doit être comprise entre 0 et un de moins que le nombre de pages de la feuille de propriétés, inclus.

*pPage*<br/>
Pointe vers la page à définir dans la feuille de propriétés. Elle ne peut pas être NULL.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la feuille de propriétés est correctement activée; Sinon, 0.

### <a name="remarks"></a>Notes

Par exemple, utilisez `SetActivePage` si l’action d’un utilisateur sur une page doit faire en sorte qu’une autre page devienne la page active.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText

Définit le texte dans le bouton de commande terminer.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Pointe vers le texte à afficher sur le bouton de commande terminer.

### <a name="remarks"></a>Notes

Appelez `SetFinishText` pour afficher le texte sur le bouton de commande terminer et masquer les boutons suivant et précédent une fois que l’utilisateur a effectué une action sur la dernière page de l’Assistant.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>  CPropertySheet::SetTitle

Spécifie la légende de la feuille de propriétés (le texte affiché dans la barre de titre d’une fenêtre frame).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
Spécifie le style du titre de la feuille de propriétés. Le style doit être spécifié à 0 ou en tant que PSH_PROPTITLE. Si le style est défini sur PSH_PROPTITLE, le mot «propriétés» apparaît après le texte spécifié comme légende. Par exemple, l' `SetTitle`appel de («simple», PSH_PROPTITLE) se traduira par une légende de feuille de propriétés «propriétés simples».

*lpszText*<br/>
Pointe vers le texte à utiliser comme légende dans la barre de titre de la feuille de propriétés.

### <a name="remarks"></a>Notes

Par défaut, une feuille de propriétés utilise le paramètre Caption dans le constructeur de la feuille de propriétés.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons

Active ou désactive le bouton précédent, suivant ou terminer dans une feuille de propriétés de l’Assistant.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Ensemble d’indicateurs qui personnalisent la fonction et l’apparence des boutons de l’Assistant. Ce paramètre peut être une combinaison des valeurs suivantes:

- PSWIZB_BACK bouton précédent

- Bouton suivant PSWIZB_NEXT

- PSWIZB_FINISH bouton Terminer

- PSWIZB_DISABLEDFINISH bouton Terminer désactivé

### <a name="remarks"></a>Notes

Appelez `SetWizardButtons` uniquement après l’ouverture de la boîte de dialogue; `SetWizardButtons` vous ne pouvez pas appeler avant d’appeler [DoModal](#domodal). En général, vous devez `SetWizardButtons` appeler à partir de [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Si vous souhaitez modifier le texte du bouton terminer ou masquer les boutons suivant et précédent une fois que l’utilisateur a terminé l’Assistant, appelez [SetFinishText](#setfinishtext). Notez que le même bouton est partagé pour terminer et suivant. Vous pouvez afficher un bouton terminer ou suivant à un moment donné, mais pas les deux.

### <a name="example"></a>Exemple

A comporte trois pages de propriétés de `CStylePage`l' `CColorPage`Assistant:, et `CShapePage`. `CPropertySheet`  Le fragment de code ci-dessous montre comment activer et désactiver les boutons **précédent** et **suivant** sur la page de propriétés de l’Assistant.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>  CPropertySheet::SetWizardMode

Établit une page de propriétés en tant qu’assistant.

```
void SetWizardMode();
```

### <a name="remarks"></a>Notes

Une caractéristique clé d’une page de propriétés de l’Assistant est que l’utilisateur navigue à l’aide des boutons suivant ou terminer, précédent et annuler au lieu de tabulations.

Appelez `SetWizardMode` avant d’appeler [DoModal](#domodal). Après l’appel `SetWizardMode`de `DoModal` , retourne soit ID_WIZFINISH (si l’utilisateur se ferme avec le bouton Terminer), soit IDCANCEL.

`SetWizardMode`définit l’indicateur PSH_WIZARD.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
