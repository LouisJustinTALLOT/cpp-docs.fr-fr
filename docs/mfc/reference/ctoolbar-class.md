---
title: CToolBar (classe)
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: aa49ebed2d48d9818c2d39ae4894d8caf1fbbf81
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773136"
---
# <a name="ctoolbar-class"></a>CToolBar (classe)

Barres de contrôles contenant une ligne de boutons bitmap et des séparateurs facultatifs.

## <a name="syntax"></a>Syntaxe

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|Construit un objet `CToolBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Retourne l’index d’un bouton avec l’ID de commande donné.|
|[CToolBar::Create](#create)|Crée la barre d’outils Windows et l’attache à la `CToolBar` objet.|
|[CToolBar::CreateEx](#createex)|Crée un `CToolBar` objet avec des styles supplémentaires pour l’embedded `CToolBarCtrl` objet.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Récupère l’ID, le style et le numéro de l’image d’un bouton.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Récupère le style pour un bouton.|
|[CToolBar::GetButtonText](#getbuttontext)|Récupère le texte qui apparaît sur un bouton.|
|[CToolBar::GetItemID](#getitemid)|Retourne l’ID de commande d’un bouton ou un séparateur à l’index donné.|
|[CToolBar::GetItemRect](#getitemrect)|Récupère le rectangle d’affichage pour l’élément à l’index donné.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Permet d’accéder directement au contrôle commun sous-jacent.|
|[CToolBar::LoadBitmap](#loadbitmap)|Charge la bitmap contenant les images des boutons de bitmap.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Charge une ressource de barre d’outils créée avec l’éditeur de ressources.|
|[CToolBar::SetBitmap](#setbitmap)|Définit une image bitmap.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Définit l’ID, le style et le numéro de l’image d’un bouton.|
|[CToolBar::SetButtons](#setbuttons)|Jeux de bouton styles et un index d’images de bouton dans l’image bitmap.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Définit le style d’un bouton.|
|[CToolBar::SetButtonText](#setbuttontext)|Définit le texte qui apparaît sur un bouton.|
|[CToolBar::SetHeight](#setheight)|Définit la hauteur de la barre d’outils.|
|[CToolBar::SetSizes](#setsizes)|Définit la taille des boutons et leurs images.|

## <a name="remarks"></a>Notes

Les boutons peuvent fonctionner comme des boutons de commande, des boutons de case à cocher ou des cases d’option. `CToolBar` les objets sont généralement incorporés membres des objets de fenêtre frame dérivées de la classe [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar::GetToolBarCtrl](#gettoolbarctrl), une fonction membre new 4.0 de MFC, vous permet de tirer parti de la prise en charge du contrôle commun Windows pour la personnalisation de la barre d’outils et des fonctionnalités supplémentaires. `CToolBar` fonctions membres vous donnent la plupart des fonctionnalités des contrôles communs Windows ; Toutefois, lorsque vous appelez `GetToolBarCtrl`, vous pouvez donner à vos barres d’outils encore plus les caractéristiques des barres d’outils de Windows 95/98. Lorsque vous appelez `GetToolBarCtrl`, elle retournera une référence à un `CToolBarCtrl` objet. Consultez [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) pour plus d’informations sur la conception de barres d’outils à l’aide de contrôles communs Windows. Pour obtenir des informations plus générales sur les contrôles communs, consultez [contrôles communs](/windows/desktop/Controls/common-controls-intro) dans le SDK Windows.

Visual C++ vous offre deux méthodes pour créer une barre d’outils. Pour créer une ressource de barre d’outils à l’aide de l’éditeur de ressources, procédez comme suit :

1. Créer une ressource de barre d’outils.

1. Construire la `CToolBar` objet.

1. Appelez le [créer](#create) (ou [CreateEx](#createex)) fonction pour créer la barre d’outils Windows et l’attacher à la `CToolBar` objet.

1. Appelez [LoadToolBar](#loadtoolbar) pour charger la ressource de barre d’outils.

Sinon, procédez comme suit :

1. Construire la `CToolBar` objet.

1. Appelez le [créer](#create) (ou [CreateEx](#createex)) fonction pour créer la barre d’outils Windows et l’attacher à la `CToolBar` objet.

1. Appelez [LoadBitmap](#loadbitmap) pour charger l’image bitmap qui contient les images de bouton de barre d’outils.

1. Appelez [SetButtons](#setbuttons) pour définir le style de bouton et associer chaque bouton avec une image dans l’image bitmap.

Toutes les images de bouton dans la barre d’outils sont effectuées à partir d’une bitmap, qui doit contenir une seule image pour chaque bouton. Toutes les images doivent être la même taille ; la valeur par défaut est 16 pixels de large et 15 pixels de haut. Images doivent être côte à côte dans l’image bitmap.

Le `SetButtons` fonction accepte un pointeur vers un tableau d’ID de contrôle et un entier qui spécifie le nombre d’éléments dans le tableau. La fonction définit l’ID de chaque bouton à la valeur de l’élément correspondant du tableau et attribue à chaque bouton un index d’image, qui spécifie la position de l’image du bouton dans l’image bitmap. Si un élément de tableau a la valeur ID_SEPARATOR, aucun index de l’image n’est attribué.

L’ordre des images dans l’image bitmap est généralement l’ordre dans lequel elles sont dessinées sur l’écran, mais vous pouvez utiliser la [SetButtonInfo](#setbuttoninfo) (fonction) pour modifier la relation entre l’ordre de l’image et l’ordre de dessin.

Tous les boutons dans une barre d’outils ont la même taille. La valeur par défaut est 24 x 22 pixels, conformément aux *Windows Interface Guidelines for Software Design*. L’espace supplémentaire entre les dimensions de l’image et un bouton est utilisé pour former une bordure autour de l’image.

Chaque bouton a une seule image. Les différents bouton États et styles (enfoncé, vers le bas, désactivé, désactivé vers le bas et indéterminé) sont générés à partir d’une image. Bien que les images bitmap peuvent être n’importe quelle couleur, vous pouvez obtenir les meilleurs résultats avec des images en noir et nuances de gris.

> [!WARNING]
> `CToolBar` prend en charge les images bitmap avec un maximum de 16 couleurs. Lorsque vous chargez une image dans un éditeur de la barre d’outils, Visual Studio automatiquement convertit l’image dans un bitmap de 16 couleurs, si nécessaire et affiche un message d’avertissement si l’image a été converti. Si vous utilisez une image avec plus de 16 couleurs (à l’aide d’un éditeur externe pour modifier l’image), l’application peut se comporter de façon inattendue.

Boutons de barre d’outils imitant les boutons de commande par défaut. Toutefois, les boutons de barre d’outils peuvent imiter également les boutons de case à cocher ou des cases d’option. Boutons de case à cocher ont trois états : activé, effacés et indéterminé. Cases d’option ont uniquement deux états : activée et désactivée.

Pour définir un bouton individuel ou un style de séparateur sans pointant vers un tableau, appelez [GetButtonStyle](#getbuttonstyle) pour récupérer le style, puis appelez [SetButtonStyle](#setbuttonstyle) au lieu de `SetButtons`. `SetButtonStyle` est particulièrement utile lorsque vous souhaitez modifier le style d’un bouton en cours d’exécution.

Pour affecter le texte à afficher sur un bouton, appelez [GetButtonText](#getbuttontext) pour récupérer le texte pour figurer sur le bouton, puis appeler [SetButtonText](#setbuttontext) pour définir le texte.

Pour créer un bouton de case à cocher, attribuez-lui le style TBBS_CHECKBOX ou utilisez un `CCmdUI` l’objet `SetCheck` fonction membre dans un gestionnaire ON_UPDATE_COMMAND_UI. Appel `SetCheck` transforme un bouton de commande en un bouton de case à cocher. Passer `SetCheck` un argument de 0 pour désactivé, 1 pour activé, ou 2 pour indéterminé.

Pour créer un bouton radio, appelez un [CCmdUI](../../mfc/reference/ccmdui-class.md) l’objet [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) fonction membre à partir d’un gestionnaire ON_UPDATE_COMMAND_UI. Passer `SetRadio` un argument de 0 pour non contrôlé ou différente de zéro pour archivage. Pour fournir un comportement qui s’excluent mutuellement d’un groupe de cases d’option, vous devez disposer des gestionnaires ON_UPDATE_COMMAND_UI pour tous les boutons dans le groupe.

Pour plus d’informations sur l’utilisation de `CToolBar`, consultez l’article [implémentation de barre d’outils MFC](../../mfc/mfc-toolbar-implementation.md) et [Technical Note 31 : Barres de contrôles](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxext.h

##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex

Cette fonction membre retourne l’index de la première barre d’outils bouton, en commençant à la position 0, dont l’ID de commande correspond à `nIDFind`.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Paramètres

*nIDFind*<br/>
ID de commande d’un bouton de barre d’outils.

### <a name="return-value"></a>Valeur de retour

L’index du bouton, ou -1 si aucun bouton n’a l’ID de commande donné.

##  <a name="create"></a>  CToolBar::Create

Cette fonction membre crée une barre d’outils de Windows (une fenêtre enfant) et l’associe le `CToolBar` objet.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est parent de la barre d’outils.

*dwStyle*<br/>
Le style de la barre d’outils. Styles de barre d’outils supplémentaires pris en charge sont :

- Barre de contrôle de CBRS_TOP est en haut de la fenêtre frame.

- Barre de contrôle de CBRS_BOTTOM est en bas de la fenêtre frame.

- Barre de contrôle de CBRS_NOALIGN n’est pas repositionné lorsque le parent est redimensionné.

- Barre de contrôle de CBRS_TOOLTIPS affiche des info-bulles.

- Barre de contrôle de CBRS_SIZE_DYNAMIC est dynamique.

- Barre de contrôle de CBRS_SIZE_FIXED est fixe.

- Barre de contrôle de CBRS_FLOATING est flottant.

- Barre d’état de CBRS_FLYBY affiche des informations sur le bouton.

- Barre de contrôle de CBRS_HIDE_INPLACE n’est pas affichée à l’utilisateur.

*nID*<br/>
ID de fenêtre enfant. de la barre d’outils

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Il définit également la hauteur de la barre d’outils sur une valeur par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>  CToolBar::CreateEx

Appelez cette fonction pour créer une barre d’outils de Windows (une fenêtre enfant) et l’associer avec le `CToolBar` objet.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est parent de la barre d’outils.

*dwCtrlStyle*<br/>
Styles supplémentaires pour la création de l’embedded [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) objet. Par défaut, cette valeur est définie à TBSTYLE_FLAT. Pour obtenir une liste complète des styles de barre d’outils, consultez *dwStyle*.

*dwStyle*<br/>
Le style de la barre d’outils. Consultez [contrôle de barre d’outils et les Styles de boutons](/windows/desktop/Controls/toolbar-control-and-button-styles) dans le SDK Windows pour obtenir la liste des styles appropriés.

*rcBorders*<br/>
Un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui définit la largeur des bordures de la fenêtre de barre d’outils. Ces bordures sont définies sur 0,0,0,0 par défaut, ce qui entraîne une fenêtre de la barre d’outils avec aucune bordure.

*nID*<br/>
ID de fenêtre enfant. de la barre d’outils

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Il définit également la hauteur de la barre d’outils sur une valeur par défaut.

Utilisez `CreateEx`, au lieu de [créer](#create), lorsque certains styles doivent être présents lors de la création du contrôle de barre d’outil embedded. Par exemple, définissez *dwCtrlStyle* à TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT pour créer une barre d’outils qui ressemble aux barres d’outils Internet Explorer 4.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>  CToolBar::CToolBar

Cette fonction membre construit un `CToolBar` de l’objet et définit les tailles par défaut.

```
CToolBar();
```

### <a name="remarks"></a>Notes

Appelez le [créer](#create) fonction membre pour créer la fenêtre de la barre d’outils.

##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo

Cette fonction membre récupère l’ID de contrôle, le style et l’index de l’image du bouton de barre d’outils ou de séparateur à l’emplacement spécifié par *nIndex.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton de barre d’outils ou du séparateur dont les informations sont à récupérer.

*nID*<br/>
Référence à un UINT est défini sur l’ID de commande du bouton.

*nStyle*<br/>
Référence à un UINT est défini sur le style du bouton.

*iImage*<br/>
Référence à un entier qui est défini à l’index de l’image du bouton dans l’image bitmap.

### <a name="remarks"></a>Notes

Ces valeurs sont affectées aux variables référencées par *nID*, *nStyle*, et *iImage*. L’index d’image est la position de l’image dans la bitmap qui contient des images pour tous les boutons de barre d’outils. La première image est à la position 0.

Si *nIndex* spécifie un séparateur, *iImage* a la valeur de la largeur du séparateur en pixels.

##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle

Appelez cette fonction membre pour récupérer le style d’un bouton ou un séparateur de la barre d’outils.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index du style de bouton ou un séparateur de barre d’outils à récupérer.

### <a name="return-value"></a>Valeur de retour

Le style du bouton ou du séparateur spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Style d’un bouton détermine comment le bouton s’affiche et comment il répond aux entrées d’utilisateur. Consultez [SetButtonStyle](#setbuttonstyle) pour obtenir des exemples de styles de boutons.

##  <a name="getbuttontext"></a>  CToolBar::GetButtonText

Appelez cette fonction membre pour récupérer le texte qui apparaît sur un bouton.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de texte à récupérer.

*rString*<br/>
Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet qui contient le texte à récupérer.

### <a name="return-value"></a>Valeur de retour

Un `CString` objet contenant le texte du bouton.

### <a name="remarks"></a>Notes

La deuxième forme de ce membre de fonction remplit un `CString` objet avec le texte de la chaîne.

##  <a name="getitemid"></a>  CToolBar::GetItemID

Cette fonction membre retourne l’ID de commande du bouton ou du séparateur spécifié par *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément dont l’ID doit être récupéré.

### <a name="return-value"></a>Valeur de retour

L’ID de commande du bouton ou du séparateur spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Séparateurs retournent ID_SEPARATOR.

##  <a name="getitemrect"></a>  CToolBar::GetItemRect

Cette fonction membre remplit le `RECT` structure dont l’adresse est contenue dans *lpRect* avec les coordonnées du bouton ou du séparateur spécifié par *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément (bouton ou un séparateur) dont les coordonnées rectangle doivent être récupérés.

*lpRect*<br/>
Adresse de la [RECT](/windows/desktop/api/windef/ns-windef-tagrect) structure qui contient les coordonnées de l’élément.

### <a name="remarks"></a>Notes

Coordonnées sont exprimées en pixels par rapport à l’angle supérieur gauche de la barre d’outils.

Utilisez `GetItemRect` pour obtenir les coordonnées d’un séparateur que vous souhaitez remplacer par une zone de liste modifiable ou un autre contrôle.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CToolBar::SetSizes](#setsizes).

##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl

Cette fonction membre permet un accès direct au contrôle commun sous-jacent.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à un objet `CToolBarCtrl`.

### <a name="remarks"></a>Notes

Utilisez `GetToolBarCtrl` pour tirer parti des fonctionnalités du contrôle commun de barre d’outils de Windows et pour tirer parti de la prise en charge [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) fournit pour la personnalisation de la barre d’outils.

Pour plus d’informations sur l’utilisation de contrôles communs, consultez l’article [contrôles](../../mfc/controls-mfc.md) et [contrôles communs](/windows/desktop/Controls/common-controls-intro) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap

Appelez cette fonction membre pour charger l’image bitmap spécifiée par `lpszResourceName` ou `nIDResource`.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName*<br/>
Pointeur vers le nom de ressource de la bitmap à charger.

*nIDResource*<br/>
ID de ressource de la bitmap à charger.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

L’image bitmap doit contenir une seule image pour chaque bouton de barre d’outils. Si les images ne sont pas de la taille standard (16 pixels de large et 15 pixels de haut), appel [SetSizes](#setsizes) pour définir les tailles de bouton et de leurs images.

> [!WARNING]
> `CToolBar` prend en charge les images bitmap avec un maximum de 16 couleurs. Lorsque vous chargez une image dans un éditeur de la barre d’outils, Visual Studio automatiquement convertit l’image dans un bitmap de 16 couleurs, si nécessaire et affiche un message d’avertissement si l’image a été converti. Si vous utilisez une image avec plus de 16 couleurs (à l’aide d’un éditeur externe pour modifier l’image), l’application peut se comporter de façon inattendue.

##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar

Appelez cette fonction membre pour charger la barre d’outils spécifiée par *lpszResourceName* ou *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName*<br/>
Pointeur vers le nom de ressource de la barre d’outils à charger.

*nIDResource*<br/>
ID de ressource de la barre d’outils à charger.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Consultez [éditeur de la barre d’outils](../../windows/toolbar-editor.md) dans pour plus d’informations sur la création d’une ressource de barre d’outils.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CToolBar::CreateEx](#createex).

##  <a name="setbitmap"></a>  CToolBar::SetBitmap

Appelez cette fonction membre pour définir l’image bitmap de la barre d’outils.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Paramètres

*hbmImageWell*<br/>
Handle d’une image bitmap associée à une barre d’outils.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Par exemple, appeler `SetBitmap` pour modifier l’image bitmap, une fois que l’utilisateur effectue une action sur un document qui modifie l’action d’un bouton.

##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo

Appelez cette fonction membre pour définir l’ID de commande du bouton, le style et numéro de l’image.

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro du bouton ou du séparateur pour lequel les informations sont à définir.

*nID*<br/>
La valeur à laquelle l’ID de commande du bouton est définie.

*nStyle*<br/>
Le nouveau style de bouton. Les styles de bouton suivants sont pris en charge :

- Bouton de commande TBBS_BUTTON Standard (valeur par défaut)

- Séparateur TBBS_SEPARATOR

- Bouton de case à cocher TBBS_CHECKBOX automatique

- TBBS_GROUP marque le début d’un groupe de boutons

- TBBS_CHECKGROUP marque le début d’un groupe de boutons de case à cocher

- TBBS_DROPDOWN crée un bouton de liste déroulante.

- TBBS_AUTOSIZE la largeur du bouton est calculée en fonction du texte du bouton, pas sur la taille de l’image.

- TBBS_NOPREFIX le texte du bouton aura pas un préfixe de l’accélérateur associé.

*iImage*<br/>
Nouvel index pour l’image du bouton dans l’image bitmap.

### <a name="remarks"></a>Notes

Pour les séparateurs, qui ont le style TBBS_SEPARATOR, cette fonction définit la largeur du séparateur en pixels à la valeur stockée dans *iImage*.

> [!NOTE]
>  Vous pouvez également définir des États de bouton à l’aide de la *nStyle* paramètre ; Toutefois, étant donné que les États de bouton sont contrôlées par le [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) gestionnaire, tout état vous définissez à l’aide de `SetButtonInfo` seront perdues lors du prochain traitement inactif. Consultez [comment mettre à jour des objets d’Interface utilisateur](../../mfc/how-to-update-user-interface-objects.md) et [TN031 : Barres de contrôles](../../mfc/tn031-control-bars.md) pour plus d’informations.

Pour plus d’informations sur les boutons et des images bitmap, consultez le [CToolBar](../../mfc/reference/ctoolbar-class.md) vue d’ensemble et [CToolBar::LoadBitmap](#loadbitmap).

##  <a name="setbuttons"></a>  CToolBar::SetButtons

Cette fonction membre définit l’ID de commande de chaque bouton de barre d’outils à la valeur spécifiée par l’élément correspondant du tableau *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Paramètres

*lpIDArray*<br/>
Pointeur vers un tableau d’ID de commande. Il peut être NULL pour allouer des boutons vide.

*nIDCount*<br/>
Nombre d’éléments dans le tableau vers lequel pointe *lpIDArray*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si un élément du tableau a la valeur ID_SEPARATOR, un séparateur est créé dans la position correspondante de la barre d’outils. Cette fonction définit le style de chaque bouton TBBS_BUTTON et le style de chaque séparateur à TBBS_SEPARATOR et assigne un index d’image pour chaque bouton. L’index d’image Spécifie la position de l’image du bouton dans l’image bitmap.

Vous n’avez pas besoin pour prendre en compte pour les séparateurs dans l’image bitmap, car cette fonction n’affecte pas les index d’image pour les séparateurs. Si votre barre d’outils comporte des boutons aux positions 0, 1, 3 et un séparateur à la position 2, les images à des positions 0, 1 et 2 dans votre bitmap associés aux boutons aux positions 0, 1 et 3, respectivement.

Si *lpIDArray* est NULL, cette fonction alloue de l’espace pour le nombre d’éléments spécifié par *nIDCount*. Utilisez [SetButtonInfo](#setbuttoninfo) pour définir les attributs de chaque élément.

##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle

Appelez cette fonction membre pour définir le style d’un bouton ou un séparateur, ou à des boutons du groupe.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton ou séparateur dont les informations sont à définir.

*nStyle*<br/>
Le style de bouton. Les styles de bouton suivants sont pris en charge :

- Bouton de commande TBBS_BUTTON Standard (valeur par défaut)

- Séparateur TBBS_SEPARATOR

- Bouton de case à cocher TBBS_CHECKBOX automatique

- TBBS_GROUP marque le début d’un groupe de boutons

- TBBS_CHECKGROUP marque le début d’un groupe de boutons de case à cocher

- TBBS_DROPDOWN crée un bouton de liste déroulante

- TBBS_AUTOSIZE la largeur du bouton est calculée en fonction du texte du bouton, pas sur la taille de l’image

- TBBS_NOPREFIX le texte du bouton n’aura pas un préfixe de l’accélérateur associé

### <a name="remarks"></a>Notes

Style d’un bouton détermine comment le bouton s’affiche et comment il répond aux entrées d’utilisateur.

Avant d’appeler `SetButtonStyle`, appelez le [GetButtonStyle](#getbuttonstyle) fonction membre pour récupérer le style de bouton ou un séparateur.

> [!NOTE]
>  Vous pouvez également définir des États de bouton à l’aide de la *nStyle* paramètre ; Toutefois, étant donné que les États de bouton sont contrôlées par le [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) gestionnaire, tout état vous définissez à l’aide de `SetButtonStyle` seront perdues lors du prochain traitement inactif. Consultez [comment mettre à jour des objets d’Interface utilisateur](../../mfc/how-to-update-user-interface-objects.md) et [TN031 : Barres de contrôles](../../mfc/tn031-control-bars.md) pour plus d’informations.

##  <a name="setbuttontext"></a>  CToolBar::SetButtonText

Appelez cette fonction pour définir le texte sur un bouton.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton dont le texte doit être défini.

*lpszText*<br/>
Pointe vers le texte à définir sur un bouton.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CToolBar::GetToolBarCtrl](#gettoolbarctrl).

##  <a name="setheight"></a>  CToolBar::SetHeight

Cette fonction membre définit la hauteur de la barre d’outils à la valeur, en pixels, spécifiées dans *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Paramètres

*cyHeight*<br/>
Hauteur en pixels de la barre d’outils.

### <a name="remarks"></a>Notes

Après avoir appelé [SetSizes](#setsizes), utiliser cette fonction membre pour remplacer la hauteur de la barre d’outils standard. Si la hauteur est trop petite, les boutons seront découpés en bas.

Si cette fonction n’est pas appelée, le framework utilise la taille du bouton pour déterminer la hauteur de la barre d’outils.

##  <a name="setsizes"></a>  CToolBar::SetSizes

Appelez cette fonction membre pour définir les boutons de la barre d’outils à la taille, en pixels, spécifiées dans *sizeButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Paramètres

*sizeButton*<br/>
La taille en pixels de chaque bouton.

*sizeImage*<br/>
La taille en pixels de chaque image.

### <a name="remarks"></a>Notes

Le *sizeImage* paramètre doit contenir la taille, en pixels, des images dans l’image bitmap de la barre d’outils. Les dimensions dans *sizeButton* doit être suffisante pour contenir l’image plus 7 pixels supplémentaires dans la largeur et 6 pixels supplémentaires en hauteur. Cette fonction définit également la hauteur de la barre d’outils pour tenir les boutons.

Appelez cette fonction membre uniquement pour les barres d’outils qui ne suivent pas *Windows Interface Guidelines for Software Design* recommandations pour les tailles de bouton et l’image.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC exemple DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl, classe](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)
