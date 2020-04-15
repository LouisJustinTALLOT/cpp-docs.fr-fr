---
title: CToolBar, classe
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
ms.openlocfilehash: fdbf343c91725783afd79bbebd73f66fdb1d67e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364278"
---
# <a name="ctoolbar-class"></a>CToolBar, classe

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
|[CToolBar::Créer](#create)|Crée la barre d’outils Windows `CToolBar` et la fixe à l’objet.|
|[CToolBar::CreateEx](#createex)|Crée `CToolBar` un objet avec des `CToolBarCtrl` styles supplémentaires pour l’objet intégré.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Récupère l’ID, le style et le numéro d’image d’un bouton.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Récupère le style pour un bouton.|
|[CToolBar::GetButtonText](#getbuttontext)|Récupère le texte qui apparaîtra sur un bouton.|
|[CToolBar::GetItemID](#getitemid)|Renvoie l’ID de commande d’un bouton ou d’un séparateur à l’index donné.|
|[CToolBar::GetItemRect](#getitemrect)|Récupère le rectangle d’affichage pour l’élément à l’index donné.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Permet un accès direct au contrôle commun sous-jacent.|
|[CToolBar::LoadBitmap](#loadbitmap)|Charge la bitmap contenant des images bitmap-bouton.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Charge une ressource de barre d’outils créée avec l’éditeur de ressources.|
|[CToolBar::SetBitmap](#setbitmap)|Définit une image bitmapped.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Définit l’ID, le style et le numéro d’image d’un bouton.|
|[CToolBar::SetButtons](#setbuttons)|Définit des styles de boutons et un index d’images boutonnées dans la bitmap.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Définit le style pour un bouton.|
|[CToolBar::SetButtonText](#setbuttontext)|Définit le texte qui apparaîtra sur un bouton.|
|[CToolBar::SetHeight](#setheight)|Définit la hauteur de la barre d’outils.|
|[CToolBar::SetSizes](#setsizes)|Définit la taille des boutons et leurs bitmaps.|

## <a name="remarks"></a>Notes

Les boutons peuvent agir comme des pushbuttons, des boutons de case à cocher ou des boutons radio. `CToolBar`les objets sont généralement des membres intégrés d’objets de fenêtre de cadre dérivés de la classe [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar:GetToolBarCtrl](#gettoolbarctrl), une fonction membre nouvelle pour MFC 4.0, vous permet de profiter du support du contrôle commun Windows pour la personnalisation des barres d’outils et des fonctionnalités supplémentaires. `CToolBar`fonctions des membres vous donnent la plupart des fonctionnalités des contrôles communs Windows; cependant, lorsque `GetToolBarCtrl`vous appelez, vous pouvez donner à vos barres d’outils encore plus des caractéristiques des barres d’outils Windows 95/98. Lorsque vous `GetToolBarCtrl`appelez, il retournera `CToolBarCtrl` une référence à un objet. Voir [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) pour plus d’informations sur la conception des barres d’outils à l’aide de contrôles communs Windows. Pour plus d’informations générales sur les contrôles courants, voir [contrôles communs](/windows/win32/Controls/common-controls-intro) dans le SDK Windows.

Visual CMMD vous fournit deux méthodes pour créer une barre d’outils. Pour créer une ressource de barre d’outils à l’aide de l’éditeur de ressources, suivez ces étapes :

1. Créez une ressource de barre d’outils.

1. Construisez `CToolBar` l’objet.

1. Appelez la fonction [Créer](#create) (ou [CréerEx](#createex)) pour créer `CToolBar` la barre d’outils Windows et l’attacher à l’objet.

1. Appelez [LoadToolBar](#loadtoolbar) pour charger la ressource de la barre d’outils.

Dans le cas contraire, procédez comme suit :

1. Construisez `CToolBar` l’objet.

1. Appelez la fonction [Créer](#create) (ou [CréerEx](#createex)) pour créer `CToolBar` la barre d’outils Windows et l’attacher à l’objet.

1. Appelez [LoadBitmap](#loadbitmap) pour charger la bitmap qui contient les images bouton de la barre d’outils.

1. Appelez [SetButtons](#setbuttons) pour définir le style bouton et associer chaque bouton à une image dans la bitmap.

Toutes les images de bouton dans la barre d’outils sont prises à partir d’une bitmap, qui doit contenir une image pour chaque bouton. Toutes les images doivent être de la même taille; la valeur par défaut est de 16 pixels de large et 15 pixels de haut. Les images doivent être côte à côte dans la bitmap.

La `SetButtons` fonction prend un pointeur à un tableau de contrôle des ID et un intégreur qui spécifie le nombre d’éléments dans le tableau. La fonction définit l’ID de chaque bouton à la valeur de l’élément correspondant de la gamme et attribue à chaque bouton un index d’image, qui spécifie la position de l’image du bouton dans la bitmap. Si un élément de tableau a la valeur ID_SEPARATOR, aucun indice d’image n’est attribué.

L’ordre des images dans la bitmap est généralement l’ordre dans lequel ils sont dessinés sur l’écran, mais vous pouvez utiliser la fonction [SetButtonInfo](#setbuttoninfo) pour changer la relation entre l’ordre d’image et l’ordre de dessin.

Tous les boutons d’une barre d’outils sont de la même taille. La valeur par défaut est de 24 x 22 pixels, conformément aux *directives d’interface Windows pour la conception de logiciels*. Tout espace supplémentaire entre les dimensions de l’image et du bouton est utilisé pour former une bordure autour de l’image.

Chaque bouton a une image. Les différents états et styles de bouton (pressés, haut, bas, désactivés, désactivés vers le bas, et indéterminés) sont générés à partir de cette image. Bien que les bitmaps peuvent être n’importe quelle couleur, vous pouvez obtenir les meilleurs résultats avec des images en noir et des nuances de gris.

> [!WARNING]
> `CToolBar`prend en charge les bitmaps avec un maximum de 16 couleurs. Lorsque vous chargez une image dans un éditeur de barre d’outils, Visual Studio convertit automatiquement l’image en une bitmap 16 couleurs, si nécessaire, et affiche un message d’avertissement si l’image a été convertie. Si vous utilisez une image avec plus de 16 couleurs (à l’aide d’un éditeur externe pour modifier l’image), l’application peut se comporter de façon inattendue.

Les boutons de barre d’outils imitent les couttons par défaut. Cependant, les boutons de barre d’outils peuvent également imiter les boutons de la case à cocher ou les boutons radio. Les boutons de la case à cocher ont trois états : cochés, effacés et indéterminés. Les boutons radio n’ont que deux états : vérifiés et effacés.

Pour définir un bouton individuel ou un style séparateur sans pointer vers un tableau, appelez `SetButtons` [GetButtonStyle](#getbuttonstyle) pour récupérer le style, puis appelez [SetButtonStyle](#setbuttonstyle) au lieu de . `SetButtonStyle`est plus utile lorsque vous voulez changer le style d’un bouton au moment de l’exécution.

Pour attribuer du texte pour apparaître sur un bouton, appelez [GetButtonText](#getbuttontext) pour récupérer le texte pour apparaître sur le bouton, puis appelez [SetButtonText](#setbuttontext) pour définir le texte.

Pour créer un bouton de case à cocher, attribuez-lui `SetCheck` le style TBBS_CHECKBOX ou utilisez la fonction de membre d’un `CCmdUI` objet dans un gestionnaire de ON_UPDATE_COMMAND_UI. L’appel `SetCheck` transforme un bouton pushbutton en une case à cocher. Passez `SetCheck` un argument de 0 pour non vérifié, 1 pour vérifié, ou 2 pour une durée indéterminée.

Pour créer un bouton radio, appelez la fonction de membre [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) d’un objet [CCmdUI](../../mfc/reference/ccmdui-class.md) à partir d’un gestionnaire de ON_UPDATE_COMMAND_UI. Passez `SetRadio` un argument de 0 pour non contrôlé ou nonzero pour vérifié. Afin de fournir le comportement mutuellement exclusif d’un groupe de radio, vous devez avoir ON_UPDATE_COMMAND_UI gestionnaires pour tous les boutons du groupe.

Pour plus d’informations sur l’utilisation `CToolBar`, voir l’article [MFC Toolbar Implementation](../../mfc/mfc-toolbar-implementation.md) et Technical Note [31: Control Bars](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar (en)](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CToolBar::CommandToIndex

Cette fonction membre renvoie l’index du premier bouton de barre `nIDFind`d’outils, à partir de la position 0, dont l’ID de commande correspond .

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Paramètres

*nIDFind (en)*<br/>
Commandez l’identification d’un bouton de barre d’outils.

### <a name="return-value"></a>Valeur de retour

L’index du bouton, ou -1 si aucun bouton n’a l’ID de commande donné.

## <a name="ctoolbarcreate"></a><a name="create"></a>CToolBar::Créer

Cette fonction de membre crée une barre d’outils `CToolBar` Windows (une fenêtre pour enfant) et l’associe à l’objet.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent de la barre d’outils.

*dwStyle (en)*<br/>
Le style barre d’outils. D’autres modèles de barres d’outils pris en charge sont les :

- CBRS_TOP barre de contrôle est en haut de la fenêtre du cadre.

- CBRS_BOTTOM barre de contrôle se trouve au bas de la fenêtre du cadre.

- CBRS_NOALIGN barre de contrôle n’est pas repositionnée lorsque le parent est resized.

- CBRS_TOOLTIPS la barre de contrôle affiche des conseils d’outil.

- CBRS_SIZE_DYNAMIC barre de contrôle est dynamique.

- CBRS_SIZE_FIXED barre de contrôle est fixe.

- CBRS_FLOATING barre de contrôle flotte.

- CBRS_FLYBY barre de statut affiche des informations sur le bouton.

- CBRS_HIDE_INPLACE barre de contrôle n’est pas affichée à l’utilisateur.

*nID*<br/>
L’id de la fenêtre pour enfants de la barre d’outils.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Il définit également la hauteur de la barre d’outils à une valeur par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a>CToolBar::CreateEx

Appelez cette fonction pour créer une barre d’outils Windows `CToolBar` (une fenêtre pour enfant) et l’associer à l’objet.

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

*dwCtrlStyle (en)*<br/>
Styles supplémentaires pour la création de l’objet [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) intégré. Par défaut, cette valeur est définie pour TBSTYLE_FLAT. Pour une liste complète des styles de barres d’outils, voir *dwStyle*.

*dwStyle (en)*<br/>
Le style barre d’outils. Consultez [Toolbar Control et Button Styles](/windows/win32/Controls/toolbar-control-and-button-styles) dans le Windows SDK pour une liste de styles appropriés.

*rcBorders*<br/>
Un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui définit les largeurs des bordures de la fenêtre de la barre d’outils. Ces frontières sont fixées à 0,0,0,0 par défaut, ce qui se traduit par une fenêtre de barre d’outils sans frontières.

*nID*<br/>
L’id de la fenêtre pour enfants de la barre d’outils.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Il définit également la hauteur de la barre d’outils à une valeur par défaut.

Utilisez `CreateEx`, au lieu de [créer](#create), lorsque certains styles doivent être présents lors de la création de la barre d’outil intégrée. Par exemple, définissez *dwCtrlStyle* pour TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT pour créer une barre d’outils qui ressemble à la barre d’outils Internet Explorer 4.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a>CToolBar::CToolBar

Cette fonction de `CToolBar` membre construit un objet et définit les tailles par défaut.

```
CToolBar();
```

### <a name="remarks"></a>Notes

Appelez la fonction [membre Créer](#create) pour créer la fenêtre de barre d’outils.

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBar::GetButtonInfo

Cette fonction de membre récupère l’ID de contrôle, le style et l’index d’image du bouton ou du séparateur de la barre d’outils à l’emplacement spécifié par *nIndex.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton de la barre d’outils ou du séparateur dont les informations doivent être récupérées.

*nID*<br/>
Référence à un UINT qui est réglé sur l’ID de commande du bouton.

*nStyle*<br/>
Référence à un UINT qui est réglé sur le style du bouton.

*iImage (en)*<br/>
Référence à un intégrant qui est réglé à l’index de l’image du bouton dans la bitmap.

### <a name="remarks"></a>Notes

Ces valeurs sont attribuées aux variables référencées par *nID*, *nStyle*, et *iImage*. L’indice d’image est la position de l’image dans la bitmap qui contient des images pour tous les boutons de la barre d’outils. La première image est à la position 0.

Si *nIndex* spécifie un séparateur, *iImage* est réglé sur la largeur du séparateur en pixels.

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CToolBar::GetButtonStyle

Appelez cette fonction de membre pour récupérer le style d’un bouton ou d’un séparateur sur la barre d’outils.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index du bouton de la barre d’outils ou du style séparateur à récupérer.

### <a name="return-value"></a>Valeur de retour

Le style du bouton ou du séparateur spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Le style d’un bouton détermine comment le bouton apparaît et comment il répond à l’entrée de l’utilisateur. Voir [SetButtonStyle](#setbuttonstyle) pour des exemples de styles de boutons.

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a>CToolBar::GetButtonText

Appelez cette fonction de membre pour récupérer le texte qui apparaît sur un bouton.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du texte à récupérer.

*rString (en)*<br/>
Une référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contiendra le texte à récupérer.

### <a name="return-value"></a>Valeur de retour

Un `CString` objet contenant le texte du bouton.

### <a name="remarks"></a>Notes

La deuxième forme de cette `CString` fonction de membre remplit un objet avec le texte de chaîne.

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a>CToolBar::GetItemID

Cette fonction membre renvoie l’ID de commande du bouton ou du séparateur spécifié par *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément dont l’ID doit être récupéré.

### <a name="return-value"></a>Valeur de retour

L’ID de commande du bouton ou du séparateur spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Les séparateurs retournent ID_SEPARATOR.

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a>CToolBar::GetItemRect

Cette fonction membre `RECT` remplit la structure dont l’adresse est contenue dans *lpRect* avec les coordonnées du bouton ou du séparateur spécifié par *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément (bouton ou séparateur) dont les coordonnées de rectangle doivent être récupérées.

*lpRect*<br/>
Adresse de la structure [RECT](/windows/win32/api/windef/ns-windef-rect) qui contiendra les coordonnées de l’élément.

### <a name="remarks"></a>Notes

Les coordonnées sont en pixels par rapport au coin supérieur gauche de la barre d’outils.

Utilisez `GetItemRect` pour obtenir les coordonnées d’un séparateur que vous souhaitez remplacer par une boîte combo ou un autre contrôle.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CToolBar:SetSizes](#setsizes).

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl

Cette fonction de membre permet un accès direct au contrôle commun sous-jacent.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à un objet `CToolBarCtrl`.

### <a name="remarks"></a>Notes

Utilisez `GetToolBarCtrl` pour tirer parti de la fonctionnalité du contrôle commun de la barre d’outils Windows, et de profiter du support [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) fournit la personnalisation des barres d’outils.

Pour plus d’informations sur l’utilisation de contrôles communs, voir l’article [Contrôles](../../mfc/controls-mfc.md) et [contrôles communs](/windows/win32/Controls/common-controls-intro) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a>CToolBar::LoadBitmap

Appelez cette fonction de membre pour `lpszResourceName` charger `nIDResource`la bitmap spécifiée par ou .

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName (en)*<br/>
Pointeur sur le nom de ressource de la bitmap à charger.

*nIDResource (en)*<br/>
Id de ressource de la bitmap à charger.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le bitmap doit contenir une image pour chaque bouton de barre d’outils. Si les images ne sont pas de la taille standard (16 pixels de large et 15 pixels de haut), appelez [SetSizes](#setsizes) pour définir la taille des boutons et leurs images.

> [!WARNING]
> `CToolBar`prend en charge les bitmaps avec un maximum de 16 couleurs. Lorsque vous chargez une image dans un éditeur de barre d’outils, Visual Studio convertit automatiquement l’image en une bitmap 16 couleurs, si nécessaire, et affiche un message d’avertissement si l’image a été convertie. Si vous utilisez une image avec plus de 16 couleurs (à l’aide d’un éditeur externe pour modifier l’image), l’application peut se comporter de façon inattendue.

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CToolBar::LoadToolBar

Appelez cette fonction de membre pour charger la barre d’outils spécifiée par *lpszResourceName* ou *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName (en)*<br/>
Pointeur sur le nom de ressource de la barre d’outils à charger.

*nIDResource (en)*<br/>
Id de ressources de la barre d’outils à charger.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Consultez [l’éditeur de la barre d’outils](../../windows/toolbar-editor.md) pour plus d’informations sur la création d’une ressource de barre d’outils.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CToolBar:CreateEx](#createex).

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a>CToolBar::SetBitmap

Appelez cette fonction de membre pour définir l’image de bitmap pour la barre d’outils.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Paramètres

*hbmImageWell*<br/>
Poignée d’une image bitmap qui est associée à une barre d’outils.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Par exemple, `SetBitmap` appelez pour modifier l’image bitmapped après que l’utilisateur prenne une action sur un document qui modifie l’action d’un bouton.

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBar::SetButtonInfo

Appelez cette fonction de membre pour définir l’ID de commande, le style et le numéro d’image du bouton.

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index à base zéro du bouton ou du séparateur pour lequel des informations doivent être définies.

*nID*<br/>
La valeur à laquelle l’ID de commande du bouton est réglé.

*nStyle*<br/>
Le nouveau style de bouton. Les styles de bouton suivants sont pris en charge :

- TBBS_BUTTON Standard pushbutton (par défaut)

- Séparateur TBBS_SEPARATOR

- TBBS_CHECKBOX Bouton auto-coche

- TBBS_GROUP marque le début d’un groupe de boutons

- TBBS_CHECKGROUP marque le début d’un groupe de boutons de case à cocher

- TBBS_DROPDOWN crée un bouton de liste d’abandon.

- TBBS_AUTOSIZE La largeur du bouton sera calculée en fonction du texte du bouton, et non de la taille de l’image.

- TBBS_NOPREFIX Le texte du bouton n’aura pas de préfixe d’accélérateur associé à celui-ci.

*iImage (en)*<br/>
Nouvel index pour l’image du bouton dans la bitmap.

### <a name="remarks"></a>Notes

Pour les séparateurs, qui ont le style TBBS_SEPARATOR, cette fonction définit la largeur du séparateur en pixels à la valeur stockée dans *iImage*.

> [!NOTE]
> Vous pouvez également définir des états de bouton à l’aide du paramètre *nStyle* ; cependant, parce que les états de bouton sont contrôlés par `SetButtonInfo` le gestionnaire [de ON_UPDATE_COMMAND_UI,](message-map-macros-mfc.md#on_update_command_ui) n’importe quel état que vous avez mis en utilisant sera perdu pendant le prochain traitement au ralenti. Voir [comment mettre à jour les objets utilisateur-interface](../../mfc/how-to-update-user-interface-objects.md) et [TN031: Control Bars](../../mfc/tn031-control-bars.md) pour plus d’informations.

Pour plus d’informations sur les images et les boutons bitmap, voir le [CToolBar](../../mfc/reference/ctoolbar-class.md) Overview et [CToolBar:LoadBitmap](#loadbitmap).

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a>CToolBar::SetButtons

Cette fonction de membre définit l’ID de commande de chaque bouton de barre d’outils à la valeur spécifiée par l’élément correspondant de la *lpIDArray*de tableau .

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Paramètres

*lpIDArray*<br/>
Pointeur vers un tableau d’ids de commande. Il peut être NULL d’allouer des boutons vides.

*nIDCompte*<br/>
Nombre d’éléments dans le tableau pointé par *lpIDArray*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si un élément du tableau a la valeur ID_SEPARATOR, un séparateur est créé dans la position correspondante de la barre d’outils. Cette fonction définit également le style de chaque bouton pour TBBS_BUTTON et le style de chaque séparateur à TBBS_SEPARATOR, et attribue un index d’image à chaque bouton. L’indice d’image spécifie la position de l’image du bouton dans la bitmap.

Vous n’avez pas besoin de tenir compte des séparateurs dans la bitmap parce que cette fonction n’attribue pas d’index d’image pour les séparateurs. Si votre barre d’outils a des boutons aux positions 0, 1 et 3 et un séparateur à la position 2, les images aux positions 0, 1 et 2 dans votre bitmap sont attribuées aux boutons aux positions 0, 1 et 3, respectivement.

Si *lpIDArray* est NULL, cette fonction alloue de l’espace pour le nombre d’articles spécifiés par *nIDCount*. Utilisez [SetButtonInfo](#setbuttoninfo) pour définir les attributs de chaque élément.

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CToolBar::SetButtonStyle

Appelez cette fonction de membre pour définir le style d’un bouton ou d’un séparateur, ou pour regrouper les boutons.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton ou du séparateur dont les informations doivent être définies.

*nStyle*<br/>
Le style bouton. Les styles de bouton suivants sont pris en charge :

- TBBS_BUTTON Standard pushbutton (par défaut)

- Séparateur TBBS_SEPARATOR

- TBBS_CHECKBOX Bouton auto-coche

- TBBS_GROUP marque le début d’un groupe de boutons

- TBBS_CHECKGROUP marque le début d’un groupe de boutons de case à cocher

- TBBS_DROPDOWN crée un bouton de liste d’abandon

- TBBS_AUTOSIZE La largeur du bouton sera calculée en fonction du texte du bouton, et non sur la taille de l’image

- TBBS_NOPREFIX Le texte bouton ne sera pas un préfixe d’accélérateur associé à celui-ci

### <a name="remarks"></a>Notes

Le style d’un bouton détermine comment le bouton apparaît et comment il répond à l’entrée de l’utilisateur.

Avant `SetButtonStyle`d’appeler, appelez la fonction membre [GetButtonStyle](#getbuttonstyle) pour récupérer le bouton ou le style séparateur.

> [!NOTE]
> Vous pouvez également définir des états de bouton à l’aide du paramètre *nStyle* ; cependant, parce que les états de bouton sont contrôlés par `SetButtonStyle` le gestionnaire [de ON_UPDATE_COMMAND_UI,](message-map-macros-mfc.md#on_update_command_ui) n’importe quel état que vous avez mis en utilisant sera perdu pendant le prochain traitement au ralenti. Voir [comment mettre à jour les objets utilisateur-interface](../../mfc/how-to-update-user-interface-objects.md) et [TN031: Control Bars](../../mfc/tn031-control-bars.md) pour plus d’informations.

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CToolBar::SetButtonText

Appelez cette fonction pour régler le texte sur un bouton.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du bouton dont le texte doit être réglé.

*lpszText*<br/>
Points au texte à régler sur un bouton.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CToolBar:GetToolBarCtrl](#gettoolbarctrl).

## <a name="ctoolbarsetheight"></a><a name="setheight"></a>CToolBar::SetHeight

Cette fonction de membre définit la hauteur de la barre d’outils à la valeur, en pixels, spécifiée en *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Paramètres

*cyHeight*<br/>
La hauteur en pixels de la barre d’outils.

### <a name="remarks"></a>Notes

Après avoir appelé [SetSizes](#setsizes), utilisez cette fonction de membre pour remplacer la hauteur standard de la barre d’outils. Si la hauteur est trop petite, les boutons seront coupés en bas.

Si cette fonction n’est pas appelée, le cadre utilise la taille du bouton pour déterminer la hauteur de la barre d’outils.

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a>CToolBar::SetSizes

Appelez cette fonction de membre pour définir les boutons de la barre d’outils à la taille, en pixels, spécifiés dans *la tailleButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Paramètres

*tailleButton*<br/>
La taille en pixels de chaque bouton.

*tailleImage*<br/>
La taille en pixels de chaque image.

### <a name="remarks"></a>Notes

Le *paramètre SizeImage* doit contenir la taille, en pixels, des images dans la bitmap de la barre d’outils. Les dimensions de *tailleButton* doit être suffisante pour tenir l’image plus 7 pixels supplémentaires en largeur et 6 pixels supplémentaires en hauteur. Cette fonction définit également la hauteur de la barre d’outils pour s’adapter aux boutons.

Appelez cette fonction de membre uniquement pour les barres d’outils qui ne suivent pas *les directives d’interface Windows pour les* recommandations de conception de logiciels pour les tailles de boutons et d’images.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC Échantillon DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl, classe](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)
