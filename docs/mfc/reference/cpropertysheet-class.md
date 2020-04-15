---
title: CPropertySheet, classe
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
ms.openlocfilehash: 167c99f734e4538ff2704e032a6ca98fb1d82004
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363946"
---
# <a name="cpropertysheet-class"></a>CPropertySheet, classe

Représente des feuilles de propriétés, également appelées boîtes de dialogue à onglets.

## <a name="syntax"></a>Syntaxe

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Feuille CProperty::CPropertySheet](#cpropertysheet)|Construit un objet `CPropertySheet`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Feuille CProperty::AddPage](#addpage)|Ajoute une page à la feuille de propriétés.|
|[Feuille CProperty::Construire](#construct)|Construit un objet `CPropertySheet`.|
|[Feuille CProperty::Créer](#create)|Affiche une feuille de propriété sans mode.|
|[Feuille CProperty::DoModal](#domodal)|Affiche une feuille de propriété modale.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Indique si la feuille de propriété utilise des onglets empilés ou défilants.|
|[Feuille CProperty::EndDialog](#enddialog)|Termine la feuille de propriété.|
|[Feuille CProperty::GetActiveIndex](#getactiveindex)|Récupère l’index de la page active de la feuille de propriété.|
|[Feuille CProperty::GetActivePage](#getactivepage)|Retourne l’objet de page actif.|
|[Feuille CProperty::GetPage](#getpage)|Récupère un pointeur sur la page spécifiée.|
|[Feuille CProperty::GetPageCount](#getpagecount)|Récupère le nombre de pages dans la feuille de propriété.|
|[Feuille CProperty::GetPageIndex](#getpageindex)|Récupère l’index de la page spécifiée de la feuille de propriété.|
|[Feuille CProperty::GetTabControl](#gettabcontrol)|Récupère un pointeur à un contrôle d’onglet.|
|[Feuille CProperty::MapDialogRect](#mapdialogrect)|Convertit les unités de boîte de dialogue d’un rectangle en unités d’écran.|
|[Feuille CProperty::OnInitDialog](#oninitdialog)|Remplacement pour augmenter l’initialisation de la feuille de propriété.|
|[Feuille CProperty::PressButton](#pressbutton)|Simule le choix du bouton spécifié dans une feuille de propriété.|
|[Feuille CProperty::RemovePage](#removepage)|Supprime une page de la feuille de propriété.|
|[Feuille CProperty::SetActivePage](#setactivepage)|Définit programmatiquement l’objet de page actif.|
|[Feuille CProperty::SetFinishText](#setfinishtext)|Définit le texte pour le bouton Finition.|
|[Feuille CProperty::SetTitle](#settitle)|Définit la légende de la feuille de propriété.|
|[Feuille CProperty::SetWizardButtons](#setwizardbuttons)|Permet les boutons de l’assistant.|
|[Feuille CProperty::SetWizardMode](#setwizardmode)|Permet le mode assistant.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[Feuille CProperty::m_psh](#m_psh)|La structure Windows [PROPSHEETHEADER.](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) Donne accès aux paramètres de base de la feuille de propriété.|

## <a name="remarks"></a>Notes

Une feuille de `CPropertySheet` propriété se compose d’un objet et d’un ou plusieurs objets [CPropertyPage.](../../mfc/reference/cpropertypage-class.md) Le cadre affiche une feuille de propriété comme une fenêtre avec un ensemble d’indices d’onglets et une zone qui contient la page actuellement sélectionnée. L’utilisateur navigue vers une page spécifique en utilisant l’onglet approprié.

`CPropertySheet`fournit une prise en charge de la structure [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) élargie introduite dans Windows 98 et Windows NT 2000. La structure contient des drapeaux supplémentaires et des membres qui prennent en charge à l’aide d’une bitmap de fond « filigrane ».

Pour afficher ces nouvelles images automatiquement dans votre objet de feuille de propriété, passez des valeurs valides pour les images de bitmap et de palette dans l’appel à [CPropertySheet::Construction](#construct) ou [CPropertySheet::CPropertySheet](#cpropertysheet).

Même `CPropertySheet` si n’est pas dérivé de [CDialog](../../mfc/reference/cdialog-class.md), la gestion d’un `CPropertySheet` objet est comme la gestion d’un `CDialog` objet. Par exemple, la création d’une feuille de propriété nécessite une construction en deux parties : appelez le constructeur, puis appelez [DoModal](#domodal) pour une feuille de propriété modale ou [créez](#create) pour une feuille de propriété sans mode. `CPropertySheet`a deux types de constructeurs: [CPropertySheet::Construct](#construct) et [CPropertySheet::CPropertySheet](#cpropertysheet).

Lorsque vous `CPropertySheet` construisez un objet, certains [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) peuvent provoquer une exception de première chance. Cela résulte du système en essayant de changer le style de la feuille de propriété avant la création de la feuille. Pour éviter cette exception, assurez-vous de définir `CPropertySheet`les styles suivants lorsque vous créez votre :

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- Ws_tabstop

Les styles suivants sont facultatifs et ne causeront pas l’exception de la première chance :

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Tout `Window Styles` autre est interdit et vous ne devriez pas les activer.

L’échange de `CPropertySheet` données entre un objet et un objet `CDialog` externe est similaire à l’échange de données avec un objet. La différence importante est que les paramètres d’une `CPropertyPage` feuille de `CPropertySheet` propriété sont généralement des variables membres des objets plutôt que de l’objet lui-même.

Vous pouvez créer un type de boîte de dialogue d’onglet appelé un assistant, qui se compose d’une feuille de propriété avec une séquence de pages de propriété qui guident l’utilisateur à travers les étapes d’une opération, comme la mise en place d’un appareil ou la création d’un bulletin. Dans une boîte de dialogue d’onglet de type sorcier, les pages de propriété n’ont pas d’onglets, et une seule page de propriété est visible à la fois. En outre, au lieu d’avoir **OK** et **Appliquer maintenant** boutons, une boîte de dialogue onglet de type assistant a un bouton **arrière,** un bouton **Suivant** ou **Finition,** un bouton **Annuler,** et un bouton **d’aide.**

Pour créer une boîte de dialogue de type assistant, suivez les mêmes étapes que vous suivrez pour créer une feuille de propriété standard, mais appelez [SetWizardMode](#setwizardmode) avant d’appeler [DoModal](#domodal). Pour activer les boutons de l’assistant, appelez [SetWizardButtons](#setwizardbuttons), en utilisant des drapeaux pour personnaliser leur fonction et leur apparence. Pour activer le bouton **Finition,** appelez [SetFinishText](#setfinishtext) après que l’utilisateur a pris des mesures sur la dernière page de l’assistant.

Pour plus d’informations `CPropertySheet` sur la façon d’utiliser des objets, voir l’article [Feuilles de propriété et pages de propriété](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdlgs.h

## <a name="cpropertysheetaddpage"></a><a name="addpage"></a>Feuille CProperty::AddPage

Ajoute la page fournie avec l’onglet le plus droit dans la feuille de propriété.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
Points à la page à ajouter à la feuille de propriété. Ne peut pas avoir la valeur NULL.

### <a name="remarks"></a>Notes

Ajoutez des pages à la feuille de propriété dans l’ordre de gauche à droite que vous souhaitez qu’elles apparaissent.

`AddPage`ajoute l’objet [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) à la liste des pages de l’objet, `CPropertySheet` mais ne crée pas réellement la fenêtre pour la page. Le cadre reporte la création de la fenêtre pour la page jusqu’à ce que l’utilisateur sélectionne cette page.

Lorsque vous ajoutez une `AddPage`page `CPropertySheet` de propriété `CPropertyPage`en utilisant , le est le parent de la . Pour accéder à la feuille de propriété de la page de propriété, appelez [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).

Il n’est pas nécessaire d’attendre la `AddPage`création de la fenêtre de feuille de propriété pour appeler . Typiquement, vous `AddPage` appelez avant d’appeler [DoModal](#domodal) ou [Créer](#create).

Si vous `AddPage` appelez après avoir affiché la page de propriété, la ligne d’onglet reflétera la page nouvellement ajoutée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

## <a name="cpropertysheetconstruct"></a><a name="construct"></a>Feuille CProperty::Construire

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

*nIDCaption (en)*<br/>
ID de la légende à utiliser pour la feuille de propriété.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente de la feuille de propriété. Si NULL, la fenêtre parente sera la fenêtre principale de la demande.

*iSelectPage*<br/>
L’index de la page qui sera initialement en tête. Par défaut est la première page ajoutée à la feuille.

*pszCaption*<br/>
Pointeur à une chaîne contenant la légende à utiliser pour la feuille de propriété. Ne peut pas avoir la valeur NULL.

*hbmWatermark*<br/>
Manipuler à la bitmap filigrane de la page de propriété.

*hpalWatermark (en)*<br/>
Poignée à la palette de la bitmap de filigrane et / ou bitmap en-tête.

*hbmHeader*<br/>
Poignée à la bitmap d’en-tête de la page de propriété.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre si l’un des constructeurs de classe n’a pas déjà été appelé. Par exemple, `Construct` appelez lorsque vous déclarez `CPropertySheet` ou allouez des tableaux d’objets. Dans le cas des tableaux, `Construct` vous devez appeler pour chaque membre dans le tableau.

Pour afficher la feuille de propriété, appelez [DoModal](#domodal) ou [Créez](#create). La chaîne contenue dans le premier paramètre sera placée dans la barre de légende de la feuille de propriété.

Vous pouvez afficher automatiquement des images de filigrane et/ou d’en-tête si vous utilisez les troisième ou `Construct`quatrième prototypes de , énumérés ci-dessus, et que vous passez des valeurs valides pour les paramètres *hbmWatermark*, *hpalWatermark*et/ou *hbmHeader.*

### <a name="example"></a>Exemple

L’exemple suivant montre dans quelles `Construct`circonstances vous appelleriez .

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

## <a name="cpropertysheetcpropertysheet"></a><a name="cpropertysheet"></a>Feuille CProperty::CPropertySheet

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

*nIDCaption (en)*<br/>
ID de la légende à utiliser pour la feuille de propriété.

*pParentWnd*<br/>
Indique la fenêtre parente de la feuille de propriété. Si NULL, la fenêtre parente sera la fenêtre principale de la demande.

*iSelectPage*<br/>
L’index de la page qui sera initialement en tête. Par défaut est la première page ajoutée à la feuille.

*pszCaption*<br/>
Indique une chaîne contenant la légende à utiliser pour la feuille de propriété. Ne peut pas avoir la valeur NULL.

*hbmWatermark*<br/>
Une poignée à la bitmap de fond de la feuille de propriété.

*hpalWatermark (en)*<br/>
Une poignée à la palette de la bitmap de filigrane et/ou de bitmap d’en-tête.

*hbmHeader*<br/>
Une poignée à la bitmap d’en-tête de la page de propriété.

### <a name="remarks"></a>Notes

Pour afficher la feuille de propriété, appelez [DoModal](#domodal) ou [Créez](#create). La chaîne contenue dans le premier paramètre sera placée dans la barre de légende de la feuille de propriété.

Si vous avez plusieurs paramètres (par exemple, si [Construct](#construct) vous utilisez `CPropertySheet`un tableau), utilisez Construct au lieu de .

Vous pouvez afficher des images de filigrane et/ou `CPropertySheet`d’en-tête automatiquement si vous utilisez les troisième ou quatrième prototypes de , ci-dessus, et que vous passez des valeurs valides pour les paramètres *hbmWatermark*, *hpalWatermark*et/ou *hbmHeader.*

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

## <a name="cpropertysheetcreate"></a><a name="create"></a>Feuille CProperty::Créer

Affiche une feuille de propriété sans mode.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Points à la fenêtre des parents. Si NULL, le parent est le bureau.

*dwStyle (en)*<br/>
Styles de fenêtre pour la feuille de propriété. Pour une liste complète des styles disponibles, voir [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle (en anglais)*<br/>
Styles de fenêtre étendus pour la feuille de propriété. Pour une liste complète des styles disponibles, voir [Extended Window Styles](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Valeur de retour

Nonzero si la feuille de propriété est créée avec succès; sinon 0.

### <a name="remarks"></a>Notes

L’appel `Create` à peut être à l’intérieur du constructeur, ou vous pouvez l’appeler après que le constructeur est invoqué.

Le style par défaut, exprimé par le passage de -1 comme *dwStyle*, est en fait WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. Le style de fenêtre étendue par défaut, exprimé en passant 0 comme *dwExStyle*, est en fait WS_EX_DLGMODALFRAME.

La `Create` fonction membre revient immédiatement après la création de la feuille de propriété. Pour détruire la feuille de propriété, appelez [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).

Feuilles de propriété sans mode `Create` affichées avec un appel pour ne pas avoir OK, Annuler, appliquer maintenant, et boutons d’aide que les feuilles de propriété modale ne. Les boutons souhaités doivent être créés par l’utilisateur.

Pour afficher une feuille de propriété modale, appelez [DoModal](#domodal) à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

## <a name="cpropertysheetdomodal"></a><a name="domodal"></a>Feuille CProperty::DoModal

Affiche une feuille de propriété modale.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL si la fonction a été couronnée de succès; autrement 0 ou -1. Si la feuille de propriété a été établie comme `DoModal` un assistant (voir [SetWizardMode](#setwizardmode)), retourne soit ID_WIZFINISH ou IDCANCEL.

### <a name="remarks"></a>Notes

La valeur de retour correspond à l’ID du contrôle qui a fermé la feuille de propriété. Après le retour de cette fonction, les fenêtres correspondant à la feuille de propriété et toutes les pages auront été détruites. Les objets eux-mêmes existeront toujours. En règle générale, vous récupérerez des données `DoModal` des objets [CPropertyPage](../../mfc/reference/cpropertypage-class.md) après les retours DE l’IDOK.

Pour afficher une feuille de propriété sans mode, appelez [Créer à](#create) la place.

Lorsqu’une page de propriété est créée à partir de sa ressource de dialogue correspondante, elle peut provoquer une exception de première chance. Cela résulte de la page de propriété changeant le style de la ressource de dialogue au style requis avant que la page soit créée. Étant donné que les ressources sont généralement lues uniquement, cela provoque une exception. Le système gère l’exception et fait une copie de la ressource modifiée. L’exception de la première chance peut donc être ignorée.

> [!NOTE]
> Cette exception doit être traitée par le système d’exploitation si vous compilez avec le modèle asynchrone de manutention d’exception. Pour plus d’informations sur les modèles de traitement des exceptions, voir [/EH (Modèle de manutention d’exception)](../../build/reference/eh-exception-handling-model.md). Dans ce cas, n’enveloppez pas les appels avec `CPropertySheet::DoModal` un bloc d’essai-catch `catch (...)`CMD dans lequel la capture gère toutes les exceptions, par exemple, . Ce bloc gérerait l’exception destinée au système d’exploitation et provoquerait un comportement imprévisible. Toutefois, vous pouvez utiliser en toute sécurité le traitement d’exception de CMD avec des types d’exception spécifiques ou un traitement d’exception structuré lorsque l’exception de violation d’accès est transmise au système d’exploitation.

Pour éviter de générer cette exception de première chance, vous pouvez garantir manuellement que la feuille de propriété a les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles)corrects . Vous devez définir les styles suivants pour une feuille de propriété :

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- Ws_tabstop

Vous pouvez utiliser les styles optionnels suivants sans provoquer une exception de première chance :

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Désactiver tous les autres styles Windows parce qu’ils ne sont pas compatibles avec les feuilles de propriété. Ce conseil ne s’applique pas aux styles étendus. L’établissement de ces styles standard de manière appropriée garantira que la feuille de propriété n’a pas à être modifiée et évitera de générer l’exception de la première chance.

### <a name="example"></a>Exemple

Voir l’exemple pour [CPropertySheet:AddPage](#addpage).

## <a name="cpropertysheetenablestackedtabs"></a><a name="enablestackedtabs"></a>CPropertySheet::EnableStackedTabs

Indique s’il faut empiler des rangées d’onglets dans une feuille de propriété.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Paramètres

*bStacked (en)*<br/>
Indique si les onglets empilés sont activés dans la feuille de propriété. Désactiver les rangées empilées d’étiquettes en définissant *bStacked* à FALSE.

### <a name="remarks"></a>Notes

Par défaut, si une feuille de propriété a plus d’onglets que s’insérera dans une seule rangée dans la largeur de la feuille de propriété, les onglets s’empileront en plusieurs rangées. Pour utiliser des onglets défilants au `EnableStackedTabs` lieu d’empiler les onglets, appelez avec *bStacked* set à FALSE avant d’appeler [DoModal](#domodal) ou [Créer](#create).

Vous devez `EnableStackedTabs` appeler lorsque vous créez une feuille de propriété modale ou sans mode. Pour intégrer ce `CPropertySheet`style dans une classe dérivée, écrivez un gestionnaire de message pour WM_CREATE. Dans la version prépondérer de [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), appelez `EnableStackedTabs( FALSE )` avant d’appeler la mise en œuvre de la classe de base.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

## <a name="cpropertysheetenddialog"></a><a name="enddialog"></a>Feuille CProperty::EndDialog

Termine la feuille de propriété.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Paramètres

*nEndID (nEndID)*<br/>
Identifiant à utiliser comme valeur de retour de la feuille de propriété.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le cadre lorsque le bouton OK, Annuler ou Fermer est appuyé. Appelez cette fonction de membre si un événement se produit qui devrait fermer la feuille de propriété.

Cette fonction de membre n’est utilisée qu’avec une boîte de dialogue modal.

### <a name="example"></a>Exemple

Voir l’exemple pour [CPropertySheet::PressButton](#pressbutton).

## <a name="cpropertysheetgetactiveindex"></a><a name="getactiveindex"></a>Feuille CProperty::GetActiveIndex

Obtient le numéro d’index de la page active de la fenêtre `GetPage`de la feuille de propriété, puis utilise le numéro d’index retourné comme paramètre pour .

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Le numéro d’index de la page active.

### <a name="example"></a>Exemple

Voir l’exemple pour [CPropertySheet:GetActivePage](#getactivepage).

## <a name="cpropertysheetgetactivepage"></a><a name="getactivepage"></a>Feuille CProperty::GetActivePage

Récupère la page active de la fenêtre de la feuille de propriété.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Valeur de retour

Le pointeur de la page active.

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre pour effectuer une certaine action sur la page active.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

## <a name="cpropertysheetgetpage"></a><a name="getpage"></a>Feuille CProperty::GetPage

Retourne un pointeur à la page spécifiée dans cette feuille de propriété.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
Index de la page désirée, à partir de 0. Doit être entre 0 et un de moins que le nombre de pages dans la feuille de propriété, inclusivement.

### <a name="return-value"></a>Valeur de retour

Le pointeur de la page correspondant au *paramètre nPage.*

### <a name="example"></a>Exemple

Voir l’exemple pour [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpagecount"></a><a name="getpagecount"></a>Feuille CProperty::GetPageCount

Détermine le nombre de pages actuellement dans la feuille de propriété.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de pages dans la feuille de propriété.

### <a name="example"></a>Exemple

Voir l’exemple pour [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpageindex"></a><a name="getpageindex"></a>Feuille CProperty::GetPageIndex

Récupère le numéro d’index de la page spécifiée dans la feuille de propriété.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
Points à la page avec l’index à trouver. Ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Le numéro d’index d’une page.

### <a name="remarks"></a>Notes

Par exemple, vous `GetPageIndex` utiliseriez pour obtenir l’index de la page afin d’utiliser [SetActivePage](#setactivepage) ou [GetPage](#getpage).

### <a name="example"></a>Exemple

Voir l’exemple pour [CPropertySheet:GetActivePage](#getactivepage).

## <a name="cpropertysheetgettabcontrol"></a><a name="gettabcontrol"></a>Feuille CProperty::GetTabControl

Récupère un pointeur à un contrôle d’onglet pour faire quelque chose de spécifique au contrôle de l’onglet (c’est-à-dire, pour utiliser l’une des API dans [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un contrôle d’onglet.

### <a name="remarks"></a>Notes

Par exemple, appelez cette fonction de membre si vous voulez ajouter des bitmaps à chacun des onglets pendant l’initialisation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

## <a name="cpropertysheetm_psh"></a><a name="m_psh"></a>Feuille CProperty::m_psh

Une structure dont les membres stockent les caractéristiques de [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2).

### <a name="remarks"></a>Notes

Utilisez cette structure pour initialiser l’apparence de la feuille de propriété après sa construction, mais avant qu’elle ne soit affichée avec la fonction membre [DoModal.](#domodal) Par exemple, définissez le membre `m_psh` *dwSize* de la taille que vous voulez que la feuille de propriété ait.

Pour plus d’informations sur cette structure, y compris une liste de ses membres, voir PROPSHEETHEADER dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

## <a name="cpropertysheetmapdialogrect"></a><a name="mapdialogrect"></a>Feuille CProperty::MapDialogRect

Convertit les unités de boîte de dialogue d’un rectangle en unités d’écran.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient les coordonnées de la boîte de dialogue à convertir.

### <a name="remarks"></a>Notes

Les unités de la boîte de dialogue sont indiquées en termes d’unité de base actuelle de boîte de dialogue dérivée de la largeur moyenne et de la hauteur des caractères dans la police utilisée pour le texte de la boîte de dialogue. Une unité horizontale est un quart de l’unité de largeur de base de boîte de dialogue, et une unité verticale est un huitième de l’unité de hauteur de base de boîte de dialogue.

La fonction [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows renvoie des informations de taille pour la police système, mais vous pouvez spécifier une police différente pour chaque feuille de propriété si vous utilisez le style DS_SETFONT dans le fichier de définition des ressources. La fonction [MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) Windows, décrite dans le Windows SDK, utilise la police appropriée pour cette boîte de dialogue.

La `MapDialogRect` fonction membre remplace les unités de boîte de dialogue en *lpRect* par des unités d’écran (pixels) de sorte que le rectangle peut être utilisé pour créer une boîte de dialogue ou positionner un contrôle dans une boîte.

## <a name="cpropertysheetoninitdialog"></a><a name="oninitdialog"></a>Feuille CProperty::OnInitDialog

Remplacements pour augmenter l’initialisation des feuilles de propriété.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Précise si l’application a défini l’accent sur l’entrée à l’un des contrôles de la feuille de propriété. Si `OnInitDialog` les retours nonzero, Windows définit la mise au point des entrées au premier contrôle de la feuille de propriété. L’application ne peut retourner 0 que si elle a explicitement défini l’accent sur l’entrée à l’un des contrôles de la feuille de propriété.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée en réponse au message WM_INITDIALOG. Ce message est envoyé à la feuille de propriété pendant les appels [Créer](#create) ou [DoModal,](#domodal) qui se produisent immédiatement avant que la feuille de propriété est affichée.

Remplacer cette fonction de membre si vous avez besoin d’effectuer un traitement spécial lorsque la feuille de propriété est paralysée. Dans la version prépondérer, `OnInitDialog` appelez d’abord la classe de base, mais ignorez sa valeur de retour. Vous retournerez normalement VRAI de votre fonction de membre prépondérer.

Vous n’avez pas besoin d’une entrée de carte de message pour cette fonction de membre.

## <a name="cpropertysheetpressbutton"></a><a name="pressbutton"></a>Feuille CProperty::PressButton

Simule le choix du bouton spécifié dans une feuille de propriété.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Paramètres

*nButton (en)*<br/>
nButton : Identifie le bouton à appuyer. Ce paramètre peut être l’une des valeurs suivantes :

- PSBTN_BACK choisit le bouton Back.

- PSBTN_NEXT choisit le bouton Suivant.

- PSBTN_FINISH choisit le bouton Finition.

- PSBTN_OK choisit le bouton OK.

- PSBTN_APPLYNOW choisit le bouton Apply Now.

- PSBTN_CANCEL choisit le bouton Annuler.

- PSBTN_HELP choisit le bouton Aide.

### <a name="remarks"></a>Notes

Consultez [PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) pour plus d’informations sur le message Windows SDK Pressbutton.

Un appel `PressButton` à ne pas envoyer la notification [PSN_APPLY](/windows/win32/Controls/psn-apply) à partir d’une page de propriété au cadre. Pour envoyer cette notification, appelez [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

## <a name="cpropertysheetremovepage"></a><a name="removepage"></a>Feuille CProperty::RemovePage

Supprime une page de la feuille de propriété et détruit la fenêtre associée.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
Points à la page à supprimer de la feuille de propriété. Ne peut pas avoir la valeur NULL.

*nPage*<br/>
Index de la page à supprimer. Doit être entre 0 et un de moins que le nombre de pages dans la feuille de propriété, inclusivement.

### <a name="remarks"></a>Notes

[L’objet CPropertyPage](../../mfc/reference/cpropertypage-class.md) lui-même n’est pas détruit tant que le propriétaire de la `CPropertySheet` fenêtre n’est pas fermé.

## <a name="cpropertysheetsetactivepage"></a><a name="setactivepage"></a>Feuille CProperty::SetActivePage

Modifie la page active.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
Index de la page à définir. Il doit être entre 0 et un de moins que le nombre de pages dans la feuille de propriété, inclusivement.

*pPage*<br/>
Points à la page à définir dans la feuille de propriété. Elle ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Nonzero si la feuille de propriété est activée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Par exemple, `SetActivePage` utilisez si l’action d’un utilisateur sur une page doit faire en sorte qu’une autre page devienne la page active.

### <a name="example"></a>Exemple

Voir l’exemple pour [CPropertySheet:GetActivePage](#getactivepage).

## <a name="cpropertysheetsetfinishtext"></a><a name="setfinishtext"></a>Feuille CProperty::SetFinishText

Définit le texte dans le bouton de commande De finition.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Points au texte à afficher sur le bouton de commande Finition.

### <a name="remarks"></a>Notes

Appelez `SetFinishText` pour afficher le texte sur le bouton de commande De finition et masquer les boutons Suivant et Arrière après que l’utilisateur a terminé l’action sur la dernière page de l’assistant.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsettitle"></a><a name="settitle"></a>Feuille CProperty::SetTitle

Spécifie la légende de la feuille de propriété (le texte affiché dans la barre de titre d’une fenêtre de cadre).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
Spécifie le style du titre de la feuille de propriété. Le style doit être spécifié à 0 ou comme PSH_PROPTITLE. Si le style est défini comme PSH_PROPTITLE, le mot "Propriétés" apparaît après le texte spécifié comme la légende. Par exemple, `SetTitle`l’appel (« Simple », PSH_PROPTITLE) donnera lieu à une légende de feuille de propriété de « Propriétés simples ».

*lpszText*<br/>
Points au texte à utiliser comme légende dans la barre de titre de la feuille de propriété.

### <a name="remarks"></a>Notes

Par défaut, une feuille de propriété utilise le paramètre de légende dans le constructeur de la feuille de propriété.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

## <a name="cpropertysheetsetwizardbuttons"></a><a name="setwizardbuttons"></a>Feuille CProperty::SetWizardButtons

Permet ou désactive le bouton Dos, Suivant ou Finition dans une feuille de propriété de sorcier.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Un ensemble de drapeaux qui personnalisent la fonction et l’apparence des boutons de l’assistant. Ce paramètre peut être une combinaison des valeurs suivantes :

- bouton PSWIZB_BACK Dos

- PSWIZB_NEXT prochain bouton

- bouton finition PSWIZB_FINISH

- bouton PSWIZB_DISABLEDFINISH finition désactivée

### <a name="remarks"></a>Notes

Appelez `SetWizardButtons` seulement après que le dialogue soit ouvert ; vous ne pouvez `SetWizardButtons` pas appeler avant d’appeler [DoModal](#domodal). Typiquement, vous `SetWizardButtons` devriez appeler à partir de [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Si vous souhaitez modifier le texte sur le bouton Finition ou masquer les boutons Suivant et Retour une fois que l’utilisateur a terminé l’assistant, appelez [SetFinishText](#setfinishtext). Notez que le même bouton est partagé pour Finish and Next. Vous pouvez afficher un bouton Finition ou un bouton Suivant en même temps, mais pas les deux.

### <a name="example"></a>Exemple

A `CPropertySheet` a trois pages `CStylePage` `CColorPage`de `CShapePage`propriété wizard: , , et .  Le fragment de code ci-dessous montre comment activer et désactiver les boutons **Back** and **Next** sur la page de propriété de l’assistant.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsetwizardmode"></a><a name="setwizardmode"></a>Feuille CProperty::SetWizardMode

Établit une page de propriété en tant que magicien.

```
void SetWizardMode();
```

### <a name="remarks"></a>Notes

Une caractéristique clé d’une page de propriété de sorcier est que l’utilisateur navigue en utilisant Next ou Finish, Back, et Annuler les boutons au lieu d’onglets.

Appelez `SetWizardMode` avant d’appeler [DoModal](#domodal). Après votre `SetWizardMode` `DoModal` appel, vous retournerez soit ID_WIZFINISH (si l’utilisateur se ferme avec le bouton Finition) ou IDCANCEL.

`SetWizardMode`pose le drapeau PSH_WIZARD.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC Échantillon PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
