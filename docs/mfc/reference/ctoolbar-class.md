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
ms.openlocfilehash: 4977cbe0b749724f999d6d7089d46f12d1e2963e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421484"
---
# <a name="ctoolbar-class"></a>CToolBar (classe)

Barres de contrôles contenant une ligne de boutons bitmap et des séparateurs facultatifs.

## <a name="syntax"></a>Syntaxe

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CToolBar :: CToolBar](#ctoolbar)|Construit un objet `CToolBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CToolBar :: CommandToIndex](#commandtoindex)|Retourne l’index d’un bouton avec l’ID de commande donné.|
|[CToolBar :: Create](#create)|Crée la barre d’outils Windows et l’attache à l’objet `CToolBar`.|
|[CToolBar :: CreateEx](#createex)|Crée un objet `CToolBar` avec des styles supplémentaires pour l’objet `CToolBarCtrl` incorporé.|
|[CToolBar :: GetButtonInfo](#getbuttoninfo)|Récupère l’ID, le style et le numéro d’image d’un bouton.|
|[CToolBar :: GetButtonStyle](#getbuttonstyle)|Récupère le style d’un bouton.|
|[CToolBar :: GetButtonText](#getbuttontext)|Récupère le texte qui s’affichera sur un bouton.|
|[CToolBar :: GetItemID](#getitemid)|Retourne l’ID de commande d’un bouton ou d’un séparateur au niveau de l’index donné.|
|[CToolBar :: GetItemRect](#getitemrect)|Récupère le rectangle d’affichage de l’élément à l’index donné.|
|[CToolBar :: GetToolBarCtrl](#gettoolbarctrl)|Autorise l’accès direct au contrôle commun sous-jacent.|
|[CToolBar :: LoadBitmap](#loadbitmap)|Charge l’image bitmap contenant les images de bouton bitmap.|
|[CToolBar :: LoadToolBar](#loadtoolbar)|Charge une ressource de barre d’outils créée à l’aide de l’éditeur de ressources.|
|[CToolBar :: SetBitmap](#setbitmap)|Définit une image bitmap.|
|[CToolBar :: SetButtonInfo](#setbuttoninfo)|Définit l’ID, le style et le numéro d’image d’un bouton.|
|[CToolBar :: SetButtons](#setbuttons)|Définit des styles de bouton et un index d’images de bouton dans l’image bitmap.|
|[CToolBar :: SetButtonStyle](#setbuttonstyle)|Définit le style d’un bouton.|
|[CToolBar :: SetButtonText](#setbuttontext)|Définit le texte qui s’affichera sur un bouton.|
|[CToolBar :: SetHeight](#setheight)|Définit la hauteur de la barre d’outils.|
|[CToolBar :: SetSizes](#setsizes)|Définit la taille des boutons et leurs bitmaps.|

## <a name="remarks"></a>Notes

Les boutons peuvent agir comme des boutons de bouton, des boutons de case à cocher ou des cases d’option. les objets `CToolBar` sont généralement des membres incorporés d’objets de fenêtre frame dérivés de la classe [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar :: GetToolBarCtrl](#gettoolbarctrl), une fonction membre qui est une nouveauté de MFC 4,0, vous permet de tirer parti de la prise en charge par le contrôle commun Windows de la personnalisation de la barre d’outils et des fonctionnalités supplémentaires. `CToolBar` fonctions membres vous offrent la plupart des fonctionnalités des contrôles communs Windows. Toutefois, lorsque vous appelez `GetToolBarCtrl`, vous pouvez faire en sorte que vos barres d’outils soient encore plus caractéristiques des barres d’outils de Windows 95/98. Quand vous appelez `GetToolBarCtrl`, elle retourne une référence à un objet `CToolBarCtrl`. Pour plus d’informations sur la conception de barres d’outils à l’aide des contrôles communs Windows, consultez [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) . Pour plus d’informations générales sur les contrôles communs, consultez [contrôles communs](/windows/win32/Controls/common-controls-intro) dans le SDK Windows.

Visual C++ vous offre deux méthodes pour créer une barre d’outils. Pour créer une ressource de barre d’outils à l’aide de l’éditeur de ressources, procédez comme suit :

1. Créez une ressource de barre d’outils.

1. Construisez l’objet `CToolBar`.

1. Appelez la fonction [Create](#create) (ou [CreateEx](#createex)) pour créer la barre d’outils Windows et l’attacher à l’objet `CToolBar`.

1. Appelez [LoadToolBar](#loadtoolbar) pour charger la ressource de barre d’outils.

Dans le cas contraire, procédez comme suit :

1. Construisez l’objet `CToolBar`.

1. Appelez la fonction [Create](#create) (ou [CreateEx](#createex)) pour créer la barre d’outils Windows et l’attacher à l’objet `CToolBar`.

1. Appelez [LoadBitmap](#loadbitmap) pour charger l’image bitmap qui contient les images du bouton de barre d’outils.

1. Appelez [SetButtons](#setbuttons) pour définir le style du bouton et associer chaque bouton à une image de l’image bitmap.

Toutes les images de bouton dans la barre d’outils sont extraites d’une image bitmap, qui doit contenir une image pour chaque bouton. Toutes les images doivent avoir la même taille ; la valeur par défaut est de 16 pixels de large et de 15 pixels de haut. Les images doivent être côte à côte dans la bitmap.

La fonction `SetButtons` prend un pointeur vers un tableau d’ID de contrôle et un entier qui spécifie le nombre d’éléments dans le tableau. La fonction affecte à l’ID de chaque bouton la valeur de l’élément correspondant du tableau et assigne à chaque bouton un index d’image, qui spécifie la position de l’image du bouton dans l’image bitmap. Si un élément de tableau a la valeur ID_SEPARATOR, aucun index d’image n’est assigné.

L’ordre des images dans la bitmap est généralement l’ordre dans lequel elles sont dessinées à l’écran, mais vous pouvez utiliser la fonction [SetButtonInfo](#setbuttoninfo) pour modifier la relation entre l’ordre des images et l’ordre de dessin.

Tous les boutons d’une barre d’outils ont la même taille. La valeur par défaut est 24 x 22 pixels, conformément aux *instructions de l’interface Windows pour la conception de logiciels*. Tout espace supplémentaire entre les dimensions de l’image et du bouton est utilisé pour former une bordure autour de l’image.

Chaque bouton a une image. Les différents États et styles des boutons (appuyés, vers le haut, désactivé, désactivé, désactivé et indéterminé) sont générés à partir de cette image. Bien que les bitmaps puissent être de toute couleur, vous pouvez obtenir les meilleurs résultats avec des images en noir et en nuances de gris.

> [!WARNING]
> `CToolBar` prend en charge les bitmaps avec un maximum de 16 couleurs. Lorsque vous chargez une image dans un éditeur de barres d’outils, Visual Studio convertit automatiquement l’image en bitmap 16 couleurs, si nécessaire, et affiche un message d’avertissement si l’image a été convertie. Si vous utilisez une image avec plus de 16 couleurs (à l’aide d’un éditeur externe pour modifier l’image), l’application peut se comporter de façon inattendue.

Les boutons de la barre d’outils imitent les PUSHBUTTON par défaut. Toutefois, les boutons de la barre d’outils peuvent également imiter les boutons de case à cocher ou les cases d’option. Les boutons de case à cocher ont trois États : activé, désactivé et indéterminé. Les cases d’option n’ont que deux États : activée et désactivée.

Pour définir un bouton ou un style de séparateur individuel sans pointer vers un tableau, appelez [GetButtonStyle](#getbuttonstyle) pour récupérer le style, puis appelez [SetButtonStyle](#setbuttonstyle) au lieu de `SetButtons`. `SetButtonStyle` est très utile lorsque vous souhaitez modifier le style d’un bouton au moment de l’exécution.

Pour assigner du texte à un bouton, appelez [GetButtonText](#getbuttontext) pour récupérer le texte à afficher sur le bouton, puis appelez [SetButtonText](#setbuttontext) pour définir le texte.

Pour créer un bouton de case à cocher, affectez-lui le style TBBS_CHECKBOX ou utilisez la fonction membre `SetCheck` d’un objet `CCmdUI` dans un gestionnaire de ON_UPDATE_COMMAND_UI. L’appel de `SetCheck` transforme un bouton de contrôle en case à cocher. Transmettez `SetCheck` un argument égal à 0 pour non coché, 1 pour activé ou 2 pour indéterminé.

Pour créer une case d’option, appelez la fonction membre [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) d’un objet [CCmdUI](../../mfc/reference/ccmdui-class.md) à partir d’un gestionnaire de ON_UPDATE_COMMAND_UI. Passe `SetRadio` un argument de 0 pour une valeur non vérifiée ou différente de zéro pour la vérification. Pour fournir le comportement mutuellement exclusif d’un groupe de cases d’option, vous devez avoir des gestionnaires de ON_UPDATE_COMMAND_UI pour tous les boutons du groupe.

Pour plus d’informations sur l’utilisation de `CToolBar`, consultez l’article implémentation de la [barre d’outils MFC](../../mfc/mfc-toolbar-implementation.md) et [Technical Note 31 : barres de contrôles](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

##  <a name="commandtoindex"></a>CToolBar :: CommandToIndex

Cette fonction membre retourne l’index du premier bouton de barre d’outils, en commençant à la position 0, dont l’ID de commande correspond à `nIDFind`.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Paramètres

*nIDFind*<br/>
ID de commande d’un bouton de barre d’outils.

### <a name="return-value"></a>Valeur de retour

Index du bouton, ou-1 si aucun bouton n’a l’ID de commande donné.

##  <a name="create"></a>CToolBar :: Create

Cette fonction membre crée une barre d’outils Windows (une fenêtre enfant) et l’associe à l’objet `CToolBar`.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent de la barre d’outils.

*dwStyle*<br/>
Style de la barre d’outils. Les autres styles de barres d’outils pris en charge sont les suivants :

- CBRS_TOP barre de contrôle est en haut de la fenêtre frame.

- CBRS_BOTTOM barre de contrôle est en bas de la fenêtre frame.

- CBRS_NOALIGN barre de contrôle n’est pas repositionnée lorsque le parent est redimensionné.

- CBRS_TOOLTIPS barre de contrôle affiche des info-bulles.

- CBRS_SIZE_DYNAMIC barre de contrôle est dynamique.

- CBRS_SIZE_FIXED barre de contrôle est fixe.

- CBRS_FLOATING barre de contrôle est flottante.

- CBRS_FLYBY barre d’état affiche des informations sur le bouton.

- CBRS_HIDE_INPLACE barre de contrôle n’est pas affichée à l’utilisateur.

*nID*<br/>
ID de la fenêtre enfant de la barre d’outils.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Elle affecte également une valeur par défaut à la hauteur de la barre d’outils.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>CToolBar :: CreateEx

Appelez cette fonction pour créer une barre d’outils Windows (une fenêtre enfant) et l’associer à l’objet `CToolBar`.

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
Pointeur vers la fenêtre qui est le parent de la barre d’outils.

*dwCtrlStyle*<br/>
Styles supplémentaires pour la création de l’objet [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) incorporé. Par défaut, cette valeur est définie sur TBSTYLE_FLAT. Pour obtenir la liste complète des styles de barre d’outils, consultez *dwStyle*.

*dwStyle*<br/>
Style de la barre d’outils. Consultez les [styles de contrôle et de bouton de barre d’outils](/windows/win32/Controls/toolbar-control-and-button-styles) dans la SDK Windows pour obtenir la liste des styles appropriés.

*rcBorders*<br/>
Objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui définit les largeurs des bordures de la fenêtre de la barre d’outils. Ces bordures ont la valeur 0, 0, 0, 0 par défaut, ce qui génère une fenêtre de barre d’outils sans bordure.

*nID*<br/>
ID de la fenêtre enfant de la barre d’outils.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Elle affecte également une valeur par défaut à la hauteur de la barre d’outils.

Utilisez `CreateEx`, au lieu de [créer](#create), lorsque certains styles doivent être présents pendant la création du contrôle de barre d’outils incorporé. Par exemple, définissez *dwCtrlStyle* sur TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT pour créer une barre d’outils qui ressemble aux barres d’outils d’Internet Explorer 4.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>CToolBar :: CToolBar

Cette fonction membre construit un objet `CToolBar` et définit les tailles par défaut.

```
CToolBar();
```

### <a name="remarks"></a>Notes

Appelez la fonction membre [Create](#create) pour créer la fenêtre de barre d’outils.

##  <a name="getbuttoninfo"></a>CToolBar :: GetButtonInfo

Cette fonction membre récupère l’ID de contrôle, le style et l’index d’image du bouton ou du séparateur de barre d’outils à l’emplacement spécifié par *nIndex.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton ou du séparateur de barre d’outils dont les informations doivent être récupérées.

*nID*<br/>
Référence à un UINT qui a pour valeur l’ID de commande du bouton.

*nStyle*<br/>
Référence à un UINT qui a pour valeur le style du bouton.

*iImage*<br/>
Référence à un entier qui a pour valeur l’index de l’image du bouton dans la bitmap.

### <a name="remarks"></a>Notes

Ces valeurs sont affectées aux variables référencées par *nid*, *nStyle*et *IImage*. L’index d’image correspond à la position de l’image dans la bitmap qui contient des images pour tous les boutons de la barre d’outils. La première image se trouve à la position 0.

Si *nIndex* spécifie un séparateur, *IImage* est défini sur la largeur de séparateur en pixels.

##  <a name="getbuttonstyle"></a>CToolBar :: GetButtonStyle

Appelez cette fonction membre pour récupérer le style d’un bouton ou d’un séparateur dans la barre d’outils.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton de barre d’outils ou du style de séparateur à récupérer.

### <a name="return-value"></a>Valeur de retour

Style du bouton ou du séparateur spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Le style d’un bouton détermine la façon dont le bouton apparaît et comment il répond aux entrées d’utilisateur. Consultez [SetButtonStyle](#setbuttonstyle) pour obtenir des exemples de styles de bouton.

##  <a name="getbuttontext"></a>CToolBar :: GetButtonText

Appelez cette fonction membre pour récupérer le texte qui apparaît sur un bouton.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du texte à récupérer.

*rString*<br/>
Référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contiendra le texte à récupérer.

### <a name="return-value"></a>Valeur de retour

Objet `CString` contenant le texte du bouton.

### <a name="remarks"></a>Notes

La deuxième forme de cette fonction membre remplit un objet `CString` avec le texte de chaîne.

##  <a name="getitemid"></a>CToolBar :: GetItemID

Cette fonction membre retourne l’ID de commande du bouton ou du séparateur spécifié par *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément dont l’ID doit être récupéré.

### <a name="return-value"></a>Valeur de retour

ID de commande du bouton ou du séparateur spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Les séparateurs retournent ID_SEPARATOR.

##  <a name="getitemrect"></a>CToolBar :: GetItemRect

Cette fonction membre remplit la structure `RECT` dont l’adresse est contenue dans *lpRect* avec les coordonnées du bouton ou du séparateur spécifié par *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément (bouton ou séparateur) dont les coordonnées de rectangle doivent être récupérées.

*lpRect*<br/>
Adresse de la structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui contiendra les coordonnées de l’élément.

### <a name="remarks"></a>Notes

Les coordonnées sont exprimées en pixels par rapport à l’angle supérieur gauche de la barre d’outils.

Utilisez `GetItemRect` pour obtenir les coordonnées d’un séparateur que vous souhaitez remplacer par une zone de liste déroulante ou un autre contrôle.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CToolBar :: SetSizes](#setsizes).

##  <a name="gettoolbarctrl"></a>CToolBar :: GetToolBarCtrl

Cette fonction membre autorise un accès direct au contrôle commun sous-jacent.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à un objet `CToolBarCtrl`.

### <a name="remarks"></a>Notes

Utilisez `GetToolBarCtrl` pour tirer parti des fonctionnalités du contrôle commun de barre d’outils Windows et tirer parti de la prise en charge de l’outil [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) pour la personnalisation de la barre d’outils.

Pour plus d’informations sur l’utilisation des contrôles communs, consultez les [contrôles](../../mfc/controls-mfc.md) et les [contrôles communs](/windows/win32/Controls/common-controls-intro) dans la SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>CToolBar :: LoadBitmap

Appelez cette fonction membre pour charger l’image bitmap spécifiée par `lpszResourceName` ou `nIDResource`.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName*<br/>
Pointeur vers le nom de ressource de l’image bitmap à charger.

*nIDResource*<br/>
ID de ressource de l’image bitmap à charger.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le bitmap doit contenir une image pour chaque bouton de la barre d’outils. Si les images ne sont pas de la taille standard (16 pixels de large et 15 pixels de haut), appelez [SetSizes](#setsizes) pour définir les tailles de bouton et leurs images.

> [!WARNING]
> `CToolBar` prend en charge les bitmaps avec un maximum de 16 couleurs. Lorsque vous chargez une image dans un éditeur de barres d’outils, Visual Studio convertit automatiquement l’image en bitmap 16 couleurs, si nécessaire, et affiche un message d’avertissement si l’image a été convertie. Si vous utilisez une image avec plus de 16 couleurs (à l’aide d’un éditeur externe pour modifier l’image), l’application peut se comporter de façon inattendue.

##  <a name="loadtoolbar"></a>CToolBar :: LoadToolBar

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

Pour plus d’informations sur la création d’une ressource de barre d’outils, consultez [éditeur de barres](../../windows/toolbar-editor.md) d’outils.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CToolBar :: CreateEx](#createex).

##  <a name="setbitmap"></a>CToolBar :: SetBitmap

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

Par exemple, appelez `SetBitmap` pour modifier l’image bitmap une fois que l’utilisateur a effectué une action sur un document qui modifie l’action d’un bouton.

##  <a name="setbuttoninfo"></a>CToolBar :: SetButtonInfo

Appelez cette fonction membre pour définir l’ID de commande, le style et le numéro d’image du bouton.

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro du bouton ou du séparateur pour lequel les informations doivent être définies.

*nID*<br/>
Valeur à laquelle l’ID de commande du bouton est défini.

*nStyle*<br/>
Nouveau style de bouton. Les styles de bouton suivants sont pris en charge :

- TBBS_BUTTON bouton de bouton standard (par défaut)

- Séparateur de TBBS_SEPARATOR

- Bouton de case à cocher TBBS_CHECKBOX automatique

- TBBS_GROUP marque le début d’un groupe de boutons

- TBBS_CHECKGROUP marque le début d’un groupe de boutons de case à cocher

- TBBS_DROPDOWN crée un bouton de liste déroulante.

- TBBS_AUTOSIZE la largeur du bouton sera calculée en fonction du texte du bouton, et non de la taille de l’image.

- TBBS_NOPREFIX le texte du bouton n’a pas de préfixe d’accélérateur associé.

*iImage*<br/>
Nouvel index pour l’image du bouton dans l’image bitmap.

### <a name="remarks"></a>Notes

Pour les séparateurs, qui ont le style TBBS_SEPARATOR, cette fonction définit la largeur du séparateur en pixels sur la valeur stockée dans *IImage*.

> [!NOTE]
>  Vous pouvez également définir des États de bouton à l’aide du paramètre *nStyle* ; Toutefois, étant donné que les États de bouton sont contrôlés par le gestionnaire de [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) , tout état que vous définissez à l’aide de `SetButtonInfo` sera perdu lors du prochain traitement inactif. Pour plus d’informations, consultez [mise à jour des objets d’interface utilisateur](../../mfc/how-to-update-user-interface-objects.md) et [TN031 : barres de contrôles](../../mfc/tn031-control-bars.md) .

Pour plus d’informations sur les images et les boutons bitmap, consultez vue d’ensemble de [CToolBar](../../mfc/reference/ctoolbar-class.md) et [CToolBar :: LoadBitmap](#loadbitmap).

##  <a name="setbuttons"></a>CToolBar :: SetButtons

Cette fonction membre définit l’ID de commande de chaque bouton de barre d’outils à la valeur spécifiée par l’élément correspondant du tableau *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Paramètres

*lpIDArray*<br/>
Pointeur vers un tableau d’ID de commande. Il peut s’agir d’une valeur NULL pour allouer des boutons vides.

*nIDCount*<br/>
Nombre d’éléments dans le tableau pointé par *lpIDArray*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si un élément du tableau a la valeur ID_SEPARATOR, un séparateur est créé dans la position correspondante de la barre d’outils. Cette fonction définit également le style de chaque bouton sur TBBS_BUTTON et le style de chaque séparateur sur TBBS_SEPARATOR, et assigne un index d’image à chaque bouton. L’index d’image spécifie la position de l’image du bouton dans l’image bitmap.

Vous n’avez pas besoin de tenir compte des séparateurs dans la bitmap, car cette fonction n’affecte pas d’index d’images pour les séparateurs. Si votre barre d’outils contient des boutons aux positions 0, 1 et 3 et un séparateur à la position 2, les images aux positions 0, 1 et 2 de votre bitmap sont affectées aux boutons aux positions 0, 1 et 3, respectivement.

Si *lpIDArray* a la valeur null, cette fonction alloue de l’espace pour le nombre d’éléments spécifié par *nIDCount*. Utilisez [SetButtonInfo](#setbuttoninfo) pour définir les attributs de chaque élément.

##  <a name="setbuttonstyle"></a>CToolBar :: SetButtonStyle

Appelez cette fonction membre pour définir le style d’un bouton ou d’un séparateur, ou pour regrouper des boutons.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton ou du séparateur dont les informations doivent être définies.

*nStyle*<br/>
Style du bouton. Les styles de bouton suivants sont pris en charge :

- TBBS_BUTTON bouton de bouton standard (par défaut)

- Séparateur de TBBS_SEPARATOR

- Bouton de case à cocher TBBS_CHECKBOX automatique

- TBBS_GROUP marque le début d’un groupe de boutons

- TBBS_CHECKGROUP marque le début d’un groupe de boutons de case à cocher

- TBBS_DROPDOWN crée un bouton de liste déroulante

- TBBS_AUTOSIZE la largeur du bouton sera calculée en fonction du texte du bouton, et non de la taille de l’image

- TBBS_NOPREFIX le texte du bouton n’a pas de préfixe d’accélérateur associé

### <a name="remarks"></a>Notes

Le style d’un bouton détermine la façon dont le bouton apparaît et comment il répond aux entrées d’utilisateur.

Avant d’appeler `SetButtonStyle`, appelez la fonction membre [GetButtonStyle](#getbuttonstyle) pour récupérer le style du bouton ou du séparateur.

> [!NOTE]
>  Vous pouvez également définir des États de bouton à l’aide du paramètre *nStyle* ; Toutefois, étant donné que les États de bouton sont contrôlés par le gestionnaire de [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) , tout état que vous définissez à l’aide de `SetButtonStyle` sera perdu lors du prochain traitement inactif. Pour plus d’informations, consultez [mise à jour des objets d’interface utilisateur](../../mfc/how-to-update-user-interface-objects.md) et [TN031 : barres de contrôles](../../mfc/tn031-control-bars.md) .

##  <a name="setbuttontext"></a>CToolBar :: SetButtonText

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

  Consultez l’exemple de [CToolBar :: GetToolBarCtrl](#gettoolbarctrl).

##  <a name="setheight"></a>CToolBar :: SetHeight

Cette fonction membre définit la hauteur de la barre d’outils à la valeur, en pixels, spécifiée dans *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Paramètres

*cyHeight*<br/>
Hauteur en pixels de la barre d’outils.

### <a name="remarks"></a>Notes

Après avoir appelé [SetSizes](#setsizes), utilisez cette fonction membre pour remplacer la hauteur standard de la barre d’outils. Si la hauteur est trop petite, les boutons sont découpés en bas.

Si cette fonction n’est pas appelée, l’infrastructure utilise la taille du bouton pour déterminer la hauteur de la barre d’outils.

##  <a name="setsizes"></a>CToolBar :: SetSizes

Appelez cette fonction membre pour définir les boutons de la barre d’outils sur la taille, en pixels, spécifiée dans *sizeButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Paramètres

*sizeButton*<br/>
Taille en pixels de chaque bouton.

*sizeImage*<br/>
Taille en pixels de chaque image.

### <a name="remarks"></a>Notes

Le paramètre *sizeImage* doit contenir la taille, en pixels, des images dans l’image bitmap de la barre d’outils. Les dimensions dans *sizeButton* doivent être suffisantes pour contenir l’image plus 7 pixels de largeur supplémentaire et de 6 pixels de hauteur supplémentaire. Cette fonction définit également la hauteur de la barre d’outils pour s’ajuster aux boutons.

Appelez cette fonction membre uniquement pour les barres d’outils qui ne suivent pas les recommandations de l' *interface Windows pour* les recommandations relatives à la conception de logiciels pour les tailles de bouton et d’image.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl, classe](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
