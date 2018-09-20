---
title: CPropertySheet, classe | Microsoft Docs
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
ms.openlocfilehash: 6ec12275291321751c539d095c60fa9dabffa2b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445176"
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
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Indique si la feuille de propriétés utilise des onglets empilées ou de faire défiler.|
|[CPropertySheet::EndDialog](#enddialog)|Met fin à la feuille de propriétés.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Récupère l’index de la page active de la feuille de propriétés.|
|[CPropertySheet::GetActivePage](#getactivepage)|Retourne l’objet de la page active.|
|[CPropertySheet::GetPage](#getpage)|Récupère un pointeur vers la page spécifiée.|
|[CPropertySheet::GetPageCount](#getpagecount)|Récupère le nombre de pages dans la feuille de propriétés.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Récupère l’index de la page spécifiée de la feuille de propriétés.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Récupère un pointeur vers un contrôle onglet.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Convertit les unités de boîte de dialogue d’un rectangle en unités de l’écran.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Méthode override pour augmenter l’initialisation feuille des propriétés.|
|[CPropertySheet::PressButton](#pressbutton)|Simule le choix du bouton spécifié dans une feuille de propriétés.|
|[CPropertySheet::RemovePage](#removepage)|Supprime une page de la feuille de propriétés.|
|[CPropertySheet::SetActivePage](#setactivepage)|Définit par programmation l’objet de la page active.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Définit le texte pour le bouton Terminer.|
|[CPropertySheet::SetTitle](#settitle)|Définit la légende de la feuille de propriétés.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Active les boutons de l’Assistant.|
|[Fonction CPropertySheet::SetWizardMode](#setwizardmode)|Active le mode de l’Assistant.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Le Windows [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) structure. Fournit l’accès aux paramètres de feuille de propriétés de base.|

## <a name="remarks"></a>Notes

Une feuille de propriétés se compose d’un `CPropertySheet` objet et un ou plusieurs [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objets. L’infrastructure affiche une feuille de propriétés sous la forme d’une fenêtre avec un ensemble d’index de l’onglet et une zone qui contient la page actuellement sélectionnée. L’utilisateur navigue vers une page spécifique à l’aide de l’onglet approprié.

`CPropertySheet` prend en charge le texte développé [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) structure introduite dans Windows 98 et Windows NT 2000. La structure contient des indicateurs supplémentaires et les membres qui prennent en charge à l’aide d’une image bitmap d’arrière-plan de « filigrane ».

Pour afficher ces nouvelles images automatiquement dans votre objet de feuille de propriétés, passer des valeurs valides pour les images bitmap et palette dans l’appel à [CPropertySheet::Construct](#construct) ou [CPropertySheet::CPropertySheet](#cpropertysheet).

Même si `CPropertySheet` n’est pas dérivé [CDialog](../../mfc/reference/cdialog-class.md), la gestion d’un `CPropertySheet` objet est similaire à la gestion un `CDialog` objet. Par exemple, la création d’une feuille de propriétés requiert la construction de deux parties : appelez le constructeur, puis appelez [DoModal](#domodal) pour une feuille de propriétés modale ou [créer](#create) pour une feuille de propriétés non modale. `CPropertySheet` propose deux types de constructeurs : [CPropertySheet::Construct](#construct) et [CPropertySheet::CPropertySheet](#cpropertysheet).

Lorsque vous construisez un `CPropertySheet` de l’objet, certaines [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) peuvent provoquer une exception de première chance de se produire. Ainsi, à partir du système essaie de modifier le style de la feuille de propriétés avant la création de la feuille. Pour éviter cette exception, assurez-vous que vous définissez les styles suivants lorsque vous créez votre `CPropertySheet`:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Les styles suivants sont facultatifs et n’entraîne pas l’exception de première chance :

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

N’importe quel autre `Window Styles` sont interdites et vous ne devez pas activer les.

Échange de données entre un `CPropertySheet` objet et un objet externe est similaire à échanger des données avec un `CDialog` objet. La différence importante est que les paramètres d’une feuille de propriétés sont généralement des variables de membre de la `CPropertyPage` objets plutôt que du `CPropertySheet` objet lui-même.

Vous pouvez créer un type de boîte de dialogue d’onglet appelé Assistant, ce qui se compose d’une feuille de propriétés avec une séquence de pages de propriétés qui guident les utilisateurs à travers les étapes d’une opération, telles que la configuration d’un appareil ou un bulletin d’informations. Dans une boîte de dialogue type d’Assistant onglet, les pages de propriétés n’ont pas de tabulations, et uniquement une page de propriété est visible à la fois. En outre, au lieu d’avoir **OK** et **appliquer maintenant** boutons, une boîte de dialogue type d’Assistant onglet a un **retour** bouton, un **suivant** ou  **Terminer** bouton, un **Annuler** bouton et un **aide** bouton.

Pour créer une boîte de dialogue de type de l’Assistant, suivez les mêmes étapes que vous suivriez pour créer une feuille de propriétés standard, mais appelle [SetWizardMode](#setwizardmode) avant d’appeler [DoModal](#domodal). Pour activer les boutons de l’Assistant, appelez [SetWizardButtons](#setwizardbuttons), à l’aide des indicateurs pour personnaliser leur fonction et leur apparence. Pour activer la **Terminer** bouton, appelez [SetFinishText](#setfinishtext) une fois que l’utilisateur a entrepris aucune action sur la dernière page de l’Assistant.

Pour plus d’informations sur l’utilisation `CPropertySheet` objets, consultez l’article [feuilles de propriétés et Pages de propriétés](../../mfc/property-sheets-and-property-pages-in-mfc.md). En outre, consultez l’article de la Base de connaissances Q146916 : faire : créer un CPropertySheet non modal avec des boutons Standard et que l’article Q300606 : faire : concevoir une feuille de propriétés MFC redimensionnable.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdlgs.h

##  <a name="addpage"></a>  CPropertySheet::AddPage

Ajoute la page fournie avec l’onglet plus à droite dans la feuille de propriétés.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*pPage*<br/>
Pointe vers la page à ajouter à la feuille de propriétés. Ne peut pas être Null.

### <a name="remarks"></a>Notes

Ajouter des pages à la feuille de propriétés dans l’ordre de gauche à droite que vous souhaitez faire apparaître.

`AddPage` Ajoute le [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) de l’objet à le `CPropertySheet` objet de liste de pages, mais ne crée pas réellement la fenêtre de la page. Le framework diffère la création de la fenêtre de la page jusqu'à ce que l’utilisateur sélectionne cette page.

Lorsque vous ajoutez un à l’aide de la page de propriété `AddPage`, le `CPropertySheet` est le parent de la `CPropertyPage`. Pour accéder à la feuille de propriétés à partir de la page de propriétés, appelez [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).

Il n’est pas nécessaire d’attendre jusqu'à ce que la création de la fenêtre de feuille de propriétés pour appeler `AddPage`. En règle générale, vous appellerez `AddPage` avant d’appeler [DoModal](#domodal) ou [créer](#create).

Si vous appelez `AddPage` après avoir affiché la page de propriétés, la ligne d’onglets reflètent la page nouvellement ajoutée.

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

*nIDCaption*<br/>
ID de la légende à utiliser pour la feuille de propriétés.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente de la feuille de propriétés. Si NULL, la fenêtre parente sera la fenêtre principale de l’application.

*iSelectPage*<br/>
L’index de la page qui sera initialement en haut. Valeur par défaut est la première page ajoutée à la feuille.

*pszCaption*<br/>
Pointeur vers une chaîne qui contient la légende à utiliser pour la feuille de propriétés. Ne peut pas être Null.

*hbmWatermark*<br/>
Handle de la bitmap de filigrane de la page de propriétés.

*hpalWatermark*<br/>
Handle vers la palette de la bitmap de filigrane et/ou le bitmap de l’en-tête.

*hbmHeader*<br/>
Handle de la bitmap de l’en-tête de la page de propriétés.

### <a name="remarks"></a>Notes

Appelez cette fonction membre, si un des constructeurs de classe n’a pas déjà été appelé. Par exemple, appeler `Construct` lorsque vous déclarez ou allouer des tableaux de `CPropertySheet` objets. Dans le cas de tableaux, vous devez appeler `Construct` pour chaque membre du tableau.

Pour afficher la feuille de propriétés, appelez [DoModal](#domodal) ou [créer](#create). La chaîne contenue dans le premier paramètre sera placée dans la barre de légende pour la feuille de propriétés.

Vous pouvez afficher des images de filigrane et/ou d’en-tête automatiquement si vous utilisez les prototypes troisième ou au quatrième de `Construct`, répertoriés ci-dessus et que vous transmettez des valeurs valides pour le *hbmWatermark*, *hpalWatermark* , et/ou *hbmHeader* paramètres.

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

*nIDCaption*<br/>
ID de la légende à utiliser pour la feuille de propriétés.

*pParentWnd*<br/>
Pointe vers la fenêtre parente de la feuille de propriétés. Si NULL, la fenêtre parente sera la fenêtre principale de l’application.

*iSelectPage*<br/>
L’index de la page qui sera initialement en haut. Valeur par défaut est la première page ajoutée à la feuille.

*pszCaption*<br/>
Pointe vers une chaîne qui contient la légende à utiliser pour la feuille de propriétés. Ne peut pas être Null.

*hbmWatermark*<br/>
Handle vers la bitmap d’arrière-plan de la feuille de propriétés.

*hpalWatermark*<br/>
Un handle vers la palette de la bitmap de filigrane et/ou le bitmap de l’en-tête.

*hbmHeader*<br/>
Handle vers la bitmap de l’en-tête de la page de propriétés.

### <a name="remarks"></a>Notes

Pour afficher la feuille de propriétés, appelez [DoModal](#domodal) ou [créer](#create). La chaîne contenue dans le premier paramètre sera placée dans la barre de légende pour la feuille de propriétés.

Si vous avez plusieurs paramètres (par exemple, si vous utilisez un tableau), utilisez [construire](#construct) au lieu de `CPropertySheet`.

Vous pouvez afficher des images de filigrane et/ou d’en-tête automatiquement si vous utilisez les prototypes troisième ou au quatrième de `CPropertySheet`, ci-dessus, et vous transmettez des valeurs valides pour le *hbmWatermark*, *hpalWatermark*, et / ou *hbmHeader* paramètres.

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
Pointe vers la fenêtre parente. Si NULL, le bureau est parent.

*dwStyle*<br/>
Styles de fenêtre pour la feuille de propriétés. Pour obtenir une liste complète des styles disponibles, consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Styles de fenêtre étendus pour la feuille de propriétés. Pour obtenir une liste complète des styles disponibles, consultez [Styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la feuille de propriétés est créée avec succès ; sinon 0.

### <a name="remarks"></a>Notes

L’appel à `Create` peut se trouver dans le constructeur, ou vous pouvez l’appeler une fois que le constructeur est appelé.

Le style par défaut, exprimé en passant de -1 en tant que *dwStyle*, est en fait WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. La valeur par défaut extended style de fenêtre, exprimée en passant 0 comme *dwExStyle*, est en fait WS_EX_DLGMODALFRAME.

Le `Create` fonction membre retourne immédiatement après la création de la feuille de propriétés. Pour détruire la feuille de propriétés, appelez [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).

Feuilles de propriétés non modale affichées par un appel à `Create` n’ont pas de boutons OK, Annuler, appliquer et aide comme des feuilles de propriétés modale. Boutons de votre choix doit être créé par l’utilisateur.

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

IDOK ou IDCANCEL, si la fonction a réussi ; Sinon, 0 ou -1. Si la feuille de propriétés a été établie en tant qu’un Assistant (consultez [SetWizardMode](#setwizardmode)), `DoModal` retourne ID_WIZFINISH ou IDCANCEL.

### <a name="remarks"></a>Notes

La valeur de retour correspond à l’ID du contrôle qui a fermé la feuille de propriétés. Après le retour de cette fonction, les fenêtres correspondant à la feuille de propriétés et toutes les pages sont détruits. Les objets eux-mêmes continuent d’exister. En règle générale, vous allez récupérer des données à partir de la [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objets après `DoModal` retourne IDOK.

Pour afficher une feuille de propriétés non modale, appelez [créer](#create) à la place.

Lorsqu’une page de propriétés est créée à partir de la ressource de boîte de dialogue correspondante, il peut provoquer une exception de première chance. Cela résulte de la page de propriétés affectant le style de la ressource de boîte de dialogue le style requis avant la création de la page. Étant donné que les ressources sont généralement en lecture seule, cela provoque une exception. Le système gère l’exception et effectue une copie de la ressource modifiée. L’exception de première chance peut donc être ignorée.

> [!NOTE]
>  Cette exception doit être gérée par le système d’exploitation si vous compilez avec le modèle de gestion des exceptions asynchrones. Pour plus d’informations sur les modèles de gestion des exceptions, consultez [/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md). Dans ce cas, n’imbriquez pas les appels à `CPropertySheet::DoModal` avec un bloc try-catch C++ dont catch gère toutes les exceptions, par exemple, `catch (...)`. Ce bloc traiterait l’exception destinée au système d’exploitation et la cause un comportement imprévisible. Toutefois, vous pouvez en toute sécurité utiliser C++ de gestion des exceptions avec les types d’exceptions spécifiques ou de la gestion structurée des exceptions où l’exception de Violation d’accès est passée par le biais du système d’exploitation.

Pour éviter de générer cette exception de première chance, vous pouvez manuellement garantir que la feuille de propriétés a la bonne [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles). Vous devez définir les styles suivants pour une feuille de propriétés :

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Vous pouvez utiliser les styles suivants facultatifs sans provoquer une exception de première chance :

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Désactiver tous les autres styles de Windows, car elles ne sont pas compatibles avec les feuilles de propriétés. Ce Conseil ne s’applique pas aux styles étendus. La définition appropriée de ces styles standards garantit que la feuille de propriétés ne doive pas être modifiées et permet d’éviter la génération de l’exception de première chance.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet::AddPage](#addpage).

##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs

Indique s’il faut lignes d’onglets dans une feuille de propriétés de la pile.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Paramètres

*bStacked*<br/>
Indique si les onglets empilées sont activées dans la feuille de propriétés. Désactiver les lignes empilées de balises en définissant *bStacked* sur FALSE.

### <a name="remarks"></a>Notes

Par défaut, si une feuille de propriétés compte plus d’onglets que ceux qui tiennent dans une ligne unique de la largeur de la feuille de propriétés, les onglets seront empileront sur plusieurs lignes. Pour utiliser les onglets de défilement au lieu d’onglets empilement, appelez `EnableStackedTabs` avec *bStacked* définie sur FALSE avant d’appeler [DoModal](#domodal) ou [créer](#create).

Vous devez appeler `EnableStackedTabs` lorsque vous créez une modale ou une feuille de propriétés non modale. Pour incorporer ce style dans un `CPropertySheet`-classe dérivée, écrire un gestionnaire de messages pour WM_CREATE. Dans la version substituée de [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), appelez `EnableStackedTabs( FALSE )` avant d’appeler l’implémentation de classe de base.

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

Cette fonction membre est appelée par le framework lorsque le OK, annuler ou le bouton Fermer est activé. Appel de cette fonction membre, si un événement produit doit fermer la feuille de propriétés.

Cette fonction membre est utilisée uniquement avec une boîte de dialogue modale.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet::PressButton](#pressbutton).

##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex

Obtient le numéro d’index de la page active de la fenêtre de feuille de propriété, puis utilise le numéro d’index retourné comme paramètre pour `GetPage`.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Le numéro d’index de la page active.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage

Récupère la page active de la fenêtre de feuille de propriété.

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
Index de la page souhaitée, en commençant à 0. Doit être entre 0 et inférieur au nombre de pages dans la feuille de propriétés, inclusive.

### <a name="return-value"></a>Valeur de retour

Le pointeur vers la page correspondant à la *nPage* paramètre.

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

*pPage*<br/>
Pointe vers la page avec l’index doit être recherché. Ne peut pas être Null.

### <a name="return-value"></a>Valeur de retour

Le numéro d’index d’une page.

### <a name="remarks"></a>Notes

Par exemple, vous utiliseriez `GetPageIndex` pour obtenir l’index de page pour pouvoir utiliser [SetActivePage](#setactivepage) ou [GetPage](#getpage).

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl

Récupère un pointeur vers un contrôle onglet pour effectuer une tâche spécifique au contrôle onglet (autrement dit, pour utiliser une des API dans [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

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

Une structure dont les membres stockent les caractéristiques de [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2).

### <a name="remarks"></a>Notes

Cette structure permet d’initialiser l’apparence de la feuille de propriétés une fois qu’il est construit mais avant qu’il est affiché avec la [DoModal](#domodal) fonction membre. Par exemple, définissez la *dwSize* membre `m_psh` à la taille souhaitée pour que la feuille de propriétés.

Pour plus d’informations sur cette structure, y compris une liste de ses membres, consultez PROPSHEETHEADER dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect

Convertit les unités de boîte de dialogue d’un rectangle en unités de l’écran.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure ou [CRect](../../atl-mfc-shared/reference/crect-class.md) coordonne d’objet qui contient la boîte de dialogue à convertir.

### <a name="remarks"></a>Notes

Unités de boîte de dialogue sont exprimées dans l’unité de base de la boîte de dialogue actuel dérivée de la largeur moyenne et la hauteur des caractères de la police utilisée pour le texte de la boîte de dialogue. Une unité horizontale correspond à un quart de l’unité de la largeur de la base de la boîte de dialogue et une unité verticale est un huitième de l’unité de base de hauteur de la boîte de dialogue.

Le [GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) (fonction) Windows retourne des informations sur la taille de la police système, mais vous pouvez spécifier une autre police pour chaque feuille de propriétés si vous utilisez le style DS_SETFONT dans le fichier de définition de ressource. Le [MapDialogRect](/windows/desktop/api/winuser/nf-winuser-mapdialogrect) fonction Windows, décrite dans le SDK Windows, utilise la police appropriée pour cette boîte de dialogue.

Le `MapDialogRect` fonction membre remplace les unités de boîte de dialogue dans *lpRect* avec écran unités (pixels) afin que le rectangle peut être utilisé pour créer une boîte de dialogue ou positionner un contrôle dans une zone.

##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog

Les remplacements pour augmenter l’initialisation feuille des propriétés.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Spécifie si l’application a défini le focus d’entrée à un des contrôles dans la feuille de propriétés. Si `OnInitDialog` retourne une valeur différente de zéro, Windows définit le focus d’entrée vers le premier contrôle dans la feuille de propriétés. L’application peut retourner 0 uniquement si elle a explicitement définir le focus d’entrée à un des contrôles dans la feuille de propriétés.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée en réponse au message WM_INITDIALOG. Ce message est envoyé à la feuille de propriétés lors de la [créer](#create) ou [DoModal](#domodal) appels, qui se produisent immédiatement avant l’affichage de la feuille de propriétés.

Remplacez cette fonction membre, si vous avez besoin effectuer un traitement spécial lors de l’initialisation de la feuille de propriétés. Dans la version substituée, tout d’abord appeler la classe de base `OnInitDialog` mais ne pas tenir compte de sa valeur de retour. Vous renvoie normalement la valeur TRUE à partir de votre fonction membre substitué.

Il est inutile une entrée de table des messages pour cette fonction membre.

##  <a name="pressbutton"></a>  CPropertySheet::PressButton

Simule le choix du bouton spécifié dans une feuille de propriétés.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Paramètres

*Nbouton*<br/>
Nbouton : identifie du bouton. Ce paramètre peut être une des valeurs suivantes :

- PSBTN_BACK choisit le bouton précédent.

- PSBTN_NEXT choisit le bouton suivant.

- PSBTN_FINISH choisit le bouton Terminer.

- PSBTN_OK choisit le bouton OK.

- PSBTN_APPLYNOW choisit le bouton Appliquer.

- PSBTN_CANCEL choisit le bouton Annuler.

- PSBTN_HELP choisit le bouton aide.

### <a name="remarks"></a>Notes

Consultez [PSM_PRESSBUTTON](/windows/desktop/Controls/psm-pressbutton) pour plus d’informations sur le message Pressbutton du Kit de développement logiciel Windows.

Un appel à `PressButton` n’envoie pas le [PSN_APPLY](/windows/desktop/Controls/psn-apply) notification à partir d’une page de propriétés à l’infrastructure. Pour envoyer cette notification, appelez [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).

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
Index de la page à supprimer. Doit être entre 0 et inférieur au nombre de pages dans la feuille de propriétés, inclusive.

### <a name="remarks"></a>Notes

Le [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objet lui-même n’est pas détruit tant que le propriétaire de la `CPropertySheet` fenêtre est fermée.

##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage

Modifie la page active.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Paramètres

*nPage*<br/>
Index de la page à définir. Doit être comprise entre 0 et un de moins que le nombre de pages dans la feuille de propriétés, inclusive.

*pPage*<br/>
Pointe vers la page pour définir dans la feuille de propriétés. Il ne peut pas être NULL.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la feuille de propriétés est activée avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Par exemple, utilisez `SetActivePage` si l’action d’un utilisateur sur une page doit provoquer une autre page devient la page active.

### <a name="example"></a>Exemple

Consultez l’exemple de [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText

Définit le texte dans le bouton de commande de terminer.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Pointe vers le texte à afficher sur le bouton de commande de terminer.

### <a name="remarks"></a>Notes

Appelez `SetFinishText` pour afficher le texte sur le bouton de commande de terminer et masquer les boutons suivant et précédent, une fois que l’utilisateur a terminé l’action sur la dernière page de l’Assistant.

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
Spécifie le style de titre de la feuille de propriété. Le style doit être spécifié à 0 ou en tant que PSH_PROPTITLE. Si le style est défini en tant que PSH_PROPTITLE, le mot « Propriétés » s’affiche après le texte spécifié en tant que la légende. Par exemple, l’appel `SetTitle`(« Simple », PSH_PROPTITLE) entraîne une légende de feuille de propriété de « Propriétés Simple ».

*lpszText*<br/>
Pointe vers le texte à utiliser comme la légende dans la barre de titre de la feuille de propriétés.

### <a name="remarks"></a>Notes

Par défaut, une feuille de propriétés utilise le paramètre de la légende dans le constructeur de feuille de propriété.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons

Active ou désactive le bouton précédent, suivant ou terminer dans une feuille de propriétés d’Assistant.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Un jeu d’indicateurs qui personnalisent la fonction et l’apparence des boutons d’Assistant. Ce paramètre peut être une combinaison des valeurs suivantes :

- Bouton PSWIZB_BACK précédent

- Bouton PSWIZB_NEXT suivant

- Bouton Terminer PSWIZB_FINISH

- Bouton Terminer désactivé PSWIZB_DISABLEDFINISH

### <a name="remarks"></a>Notes

Appelez `SetWizardButtons` uniquement une fois que la boîte de dialogue est ouverte ; vous ne pouvez pas appeler `SetWizardButtons` avant d’appeler [DoModal](#domodal). En règle générale, vous devez appeler `SetWizardButtons` de [notifications CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Si vous souhaitez modifier le texte sur le bouton Terminer ou masquer la prochaine arrière des boutons et une fois l’utilisateur a terminé l’Assistant, appel [SetFinishText](#setfinishtext). Notez que le même bouton est partagé pour terminer et suivant. Vous pouvez afficher une finition ou un bouton suivant en même temps, mais pas les deux.

### <a name="example"></a>Exemple

Un `CPropertySheet` a trois pages de propriétés d’Assistant : `CStylePage`, `CColorPage`, et `CShapePage`.  Le fragment de code ci-dessous montre comment activer et désactiver la **retour** et **suivant** boutons sur la page de propriétés d’Assistant.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>  Fonction CPropertySheet::SetWizardMode

Établit une page de propriétés en tant qu’un Assistant.

```
void SetWizardMode();
```

### <a name="remarks"></a>Notes

Une caractéristique clé d’une page de propriété de l’Assistant est que l’utilisateur accède à l’aide regard ou terminer, sauvegarder et annuler des boutons au lieu d’onglets.

Appelez `SetWizardMode` avant d’appeler [DoModal](#domodal). Après avoir appelé `SetWizardMode`, `DoModal` retournera ID_WIZFINISH (si l’utilisateur ferme avec le bouton Terminer) ou IDCANCEL.

`SetWizardMode` définit l’indicateur PSH_WIZARD.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC exemple CMNCTRL1](../../visual-cpp-samples.md)<br/>
[MFC exemple CMNCTRL2](../../visual-cpp-samples.md)<br/>
[Exemple MFC PROPDLG](../../visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
