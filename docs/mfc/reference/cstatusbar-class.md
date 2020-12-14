---
description: 'En savoir plus sur : CStatusBar, classe'
title: CStatusBar (classe)
ms.date: 11/04/2016
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: 61f3c920c1607862ad0ddc1329293b7b67dcde90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345080"
---
# <a name="cstatusbar-class"></a>CStatusBar (classe)

Barre de contrôles avec une ligne de volets de sortie de texte ou « indicateurs ».

## <a name="syntax"></a>Syntaxe

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStatusBar :: CStatusBar](#cstatusbar)|Construit un objet `CStatusBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStatusBar :: CommandToIndex](#commandtoindex)|Obtient l’index d’un ID d’indicateur donné.|
|[CStatusBar :: Create](#create)|Crée la barre d’État, l’attache à l' `CStatusBar` objet et définit la police initiale et la hauteur de la barre.|
|[CStatusBar :: CreateEx](#createex)|Crée un `CStatusBar` objet avec des styles supplémentaires pour l' `CStatusBarCtrl` objet incorporé.|
|[CStatusBar ::D rawItem](#drawitem)|Appelé en cas de modification de l’aspect visuel d’un contrôle de barre d’État owner-draw.|
|[CStatusBar :: GetItemID](#getitemid)|Obtient l’ID d’indicateur pour un index donné.|
|[CStatusBar :: GetItemRect](#getitemrect)|Obtient le rectangle d’affichage pour un index donné.|
|[CStatusBar :: GetPaneInfo](#getpaneinfo)|Obtient l’ID, le style et la largeur de l’indicateur pour un index donné.|
|[CStatusBar :: GetPaneStyle](#getpanestyle)|Obtient le style d’indicateur pour un index donné.|
|[CStatusBar :: GetPaneText](#getpanetext)|Obtient le texte d’indicateur pour un index donné.|
|[CStatusBar :: GetStatusBarCtrl](#getstatusbarctrl)|Autorise l’accès direct au contrôle commun sous-jacent.|
|[CStatusBar :: SetIndicators](#setindicators)|Définit des ID d’indicateur.|
|[CStatusBar :: SetPaneInfo](#setpaneinfo)|Définit l’ID, le style et la largeur de l’indicateur pour un index donné.|
|[CStatusBar :: SetPaneStyle](#setpanestyle)|Définit le style d’indicateur pour un index donné.|
|[CStatusBar :: SetPaneText](#setpanetext)|Définit le texte d’indicateur pour un index donné.|

## <a name="remarks"></a>Notes

Les volets de sortie sont couramment utilisés comme lignes de message et indicateurs d’État. Par exemple, les lignes de message d’aide du menu décrivent brièvement la commande de menu sélectionnée et les indicateurs qui indiquent l’état du verrou de défilement, Verr. NUM et autres clés.

[CStatusBar :: GetStatusBarCtrl](#getstatusbarctrl), une fonction membre nouvelle dans MFC 4,0, vous permet de tirer parti de la prise en charge par le contrôle commun Windows de la personnalisation de la barre d’État et des fonctionnalités supplémentaires. `CStatusBar` les fonctions membres vous offrent la plupart des fonctionnalités des contrôles communs Windows. Toutefois, lorsque vous appelez `GetStatusBarCtrl` , vous pouvez affecter à vos barres d’État une plus grande partie des caractéristiques d’une barre d’État Windows 95/98. Quand vous appelez `GetStatusBarCtrl` , une référence à un objet est retournée `CStatusBarCtrl` . Pour plus d’informations sur la conception de barres d’outils à l’aide des contrôles communs Windows, consultez [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) . Pour plus d’informations générales sur les contrôles communs, consultez [contrôles communs](/windows/win32/Controls/common-controls-intro) dans le SDK Windows.

Le Framework stocke les informations d’indicateur dans un tableau avec l’indicateur le plus à gauche à la position 0. Lorsque vous créez une barre d’État, vous utilisez un tableau d’ID de chaîne que l’infrastructure associe aux indicateurs correspondants. Vous pouvez ensuite utiliser un ID de chaîne ou un index pour accéder à un indicateur.

Par défaut, le premier indicateur est « élastique » : la longueur de la barre d’État n’est pas utilisée par les autres volets d’indicateur, de sorte que les autres volets sont alignés à droite.

Pour créer une barre d’État, procédez comme suit :

1. Construisez l' `CStatusBar` objet.

1. Appelez la fonction [Create](#create) (ou [CreateEx](#createex)) pour créer la fenêtre de la barre d’État et l’attacher à l' `CStatusBar` objet.

1. Appelez [SetIndicators](#setindicators) pour associer un ID de chaîne à chaque indicateur.

Il existe trois façons de mettre à jour le texte dans un volet de barre d’État :

1. Appelez [CWnd :: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) pour mettre à jour le texte dans le volet 0 uniquement.

1. Appelez [CCmdUI :: SetText](../../mfc/reference/ccmdui-class.md#settext) dans le gestionnaire de ON_UPDATE_COMMAND_UI de la barre d’État.

1. Appelez [SetPaneText](#setpanetext) pour mettre à jour le texte de n’importe quel volet.

Appelez [SetPaneStyle](#setpanestyle) pour mettre à jour le style d’un volet de barre d’État.

Pour plus d’informations sur l’utilisation de `CStatusBar` , consultez l’article [implémentation de la barre d’État dans MFC](../../mfc/status-bar-implementation-in-mfc.md) et [Technical Note 31 : barres de contrôles](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a> CStatusBar :: CommandToIndex

Obtient l’index de l’indicateur pour un ID donné.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Paramètres

*nIDFind*<br/>
ID de chaîne de l’indicateur dont l’index doit être récupéré.

### <a name="return-value"></a>Valeur renvoyée

Index de l’indicateur en cas de réussite ; -1 en cas d’échec.

### <a name="remarks"></a>Notes

L’index du premier indicateur est 0.

## <a name="cstatusbarcreate"></a><a name="create"></a> CStatusBar :: Create

Crée une barre d’État (une fenêtre enfant) et l’associe à l' `CStatusBar` objet.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers l’objet [CWnd](../../mfc/reference/cwnd-class.md) dont la fenêtre Windows est le parent de la barre d’État.

*dwStyle*<br/>
Style de barre d’État. Outre les [styles](../../mfc/reference/styles-used-by-mfc.md#window-styles)Windows standard, ces styles sont pris en charge.

- CBRS_TOP barre de contrôle est en haut de la fenêtre frame.

- CBRS_BOTTOM barre de contrôle est en bas de la fenêtre frame.

- CBRS_NOALIGN barre de contrôle n’est pas repositionnée lorsque le parent est redimensionné.

*nID*<br/>
ID de la fenêtre enfant de la barre d’outils.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Définit également la police initiale et définit la hauteur de la barre d’État sur une valeur par défaut.

## <a name="cstatusbarcreateex"></a><a name="createex"></a> CStatusBar :: CreateEx

Appelez cette fonction pour créer une barre d’État (une fenêtre enfant) et l’associer à l' `CStatusBar` objet.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers l’objet [CWnd](../../mfc/reference/cwnd-class.md) dont la fenêtre Windows est le parent de la barre d’État.

*dwCtrlStyle*<br/>
Styles supplémentaires pour la création de l’objet [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) incorporé. La valeur par défaut spécifie une barre d’État sans poignée de redimensionnement ni prise en charge d’info-bulle. Les styles de barre d’État pris en charge sont les suivants :

- SBARS_SIZEGRIP le contrôle de barre d’État comprend une poignée de dimensionnement à l’extrémité droite de la barre d’État. Une poignée de dimensionnement est semblable à une bordure de redimensionnement ; Il s’agit d’une zone rectangulaire sur laquelle l’utilisateur peut cliquer et faire glisser pour redimensionner la fenêtre parente.

- SBT_TOOLTIPS la barre d’État prend en charge les info-bulles.

Pour plus d’informations sur ces styles, consultez [paramètres pour CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
Style de barre d’État. La valeur par défaut spécifie qu’une barre d’état visible doit être créée en bas de la fenêtre frame. Appliquez n’importe quelle combinaison de styles de contrôle de barre d’État listés dans les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [CDialogBar :: Create](../../mfc/reference/cdialogbar-class.md#create). Toutefois, ce paramètre doit toujours inclure les styles WS_CHILD et WS_VISIBLE.

*nID*<br/>
ID de la fenêtre enfant de la barre d’État.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction définit également la police initiale et définit la hauteur de la barre d’État sur une valeur par défaut.

Utilisez `CreateEx` , au lieu de [Create](#create), lorsque certains styles doivent être présents pendant la création du contrôle de barre d’État incorporé. Par exemple, affectez à *dwCtrlStyle* la valeur SBT_TOOLTIPS pour afficher les info-bulles dans un objet de barre d’État.

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a> CStatusBar :: CStatusBar

Construit un `CStatusBar` objet, crée une police de la barre d’État par défaut si nécessaire, et définit les caractéristiques de police sur les valeurs par défaut.

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a> CStatusBar ::D rawItem

Cette fonction membre est appelée par l’infrastructure quand un aspect visuel d’une barre d’État owner-drawn change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` membre de la `DRAWITEMSTRUCT` structure définit l’action de dessin à effectuer. Substituez cette fonction membre pour implémenter le dessin pour un objet owner-draw `CStatusBar` . L’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant l’arrêt de cette fonction membre.

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a> CStatusBar :: GetItemID

Retourne l’ID de l’indicateur spécifié par *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’indicateur dont l’ID doit être récupéré.

### <a name="return-value"></a>Valeur renvoyée

ID de l’indicateur spécifié par *nIndex*.

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a> CStatusBar :: GetItemRect

Copie les coordonnées de l’indicateur spécifié par *nIndex* dans la structure vers laquelle pointe *lpRect*.

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’indicateur dont les coordonnées de rectangle doivent être récupérées.

*lpRect*<br/>
Pointe vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui reçoit les coordonnées de l’indicateur spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Les coordonnées sont exprimées en pixels par rapport à l’angle supérieur gauche de la barre d’État.

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a> CStatusBar :: GetPaneInfo

Définit *nid*, *nStyle* et *cxWidth* sur l’ID, le style et la largeur du volet d’indicateur à l’emplacement spécifié par *nIndex*.

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du volet dont les informations doivent être récupérées.

*nID*<br/>
Référence à un UINT qui a pour valeur l’ID du volet.

*nStyle*<br/>
Référence à un UINT qui a pour valeur le style du volet.

*cxWidth*<br/>
Référence à un entier défini sur la largeur du volet.

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a> CStatusBar :: GetPaneStyle

Appelez cette fonction membre pour récupérer le style du volet d’une barre d’État.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du volet dont le style doit être récupéré.

### <a name="return-value"></a>Valeur renvoyée

Style du volet de la barre d’état spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Le style d’un volet détermine le mode d’affichage du volet.

Pour obtenir la liste des styles disponibles pour les barres d’État, consultez [créer](#create).

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a> CStatusBar :: GetPaneText

Appelez cette fonction membre pour récupérer le texte qui s’affiche dans un volet de barre d’État.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du volet dont le texte doit être récupéré.

*rString*<br/>
Référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient le texte à récupérer.

### <a name="return-value"></a>Valeur renvoyée

`CString`Objet contenant le texte du volet.

### <a name="remarks"></a>Notes

La deuxième forme de cette fonction membre remplit un `CString` objet avec le texte de chaîne.

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a> CStatusBar :: GetStatusBarCtrl

Cette fonction membre autorise un accès direct au contrôle commun sous-jacent.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Valeur renvoyée

Contient une référence à un objet [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) .

### <a name="remarks"></a>Notes

Utilisez `GetStatusBarCtrl` pour tirer parti des fonctionnalités du contrôle commun de barre d’État Windows et tirer parti de la prise en charge de la personnalisation de la barre d’État par [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) . Par exemple, en utilisant le contrôle commun, vous pouvez spécifier un style qui comprend une poignée de dimensionnement sur la barre d’État, ou vous pouvez spécifier un style pour que la barre d’État apparaisse en haut de la zone cliente de la fenêtre parente.

Pour plus d’informations générales sur les contrôles communs, consultez [contrôles communs](/windows/win32/Controls/common-controls-intro) dans le SDK Windows.

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a> CStatusBar :: SetIndicators

Définit l’ID de chaque indicateur sur la valeur spécifiée par l’élément correspondant du tableau *lpIDArray*, charge la ressource de type chaîne spécifiée par chaque ID et définit le texte de l’indicateur sur la chaîne.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Paramètres

*lpIDArray*<br/>
Pointeur vers un tableau d’ID.

*nIDCount*<br/>
Nombre d’éléments dans le tableau pointé par *lpIDArray*.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a> CStatusBar :: SetPaneInfo

Définit le volet d’indicateur spécifié sur un nouvel ID, un nouveau style et une nouvelle largeur.

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du volet d’indicateur dont le style doit être défini.

*nID*<br/>
Nouvel ID du volet d’indicateur.

*nStyle*<br/>
Nouveau style pour le volet d’indicateur.

*cxWidth*<br/>
Nouvelle largeur du volet d’indicateur.

### <a name="remarks"></a>Notes

Les styles d’indicateur suivants sont pris en charge :

- SBPS_NOBORDERS aucune bordure 3D autour du volet.

- SBPS_POPOUT bordure inverse pour que le texte « s’affiche ».

- SBPS_DISABLED ne pas dessiner du texte.

- SBPS_STRETCH volet Stretch pour remplir l’espace inutilisé. Un seul volet par barre d’État peut avoir ce style.

- SBPS_NORMAL aucune extension, bordures ou pop-out.

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a> CStatusBar :: SetPaneStyle

Appelez cette fonction membre pour définir le style du volet d’une barre d’État.

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du volet dont le style doit être défini.

*nStyle*<br/>
Style du volet dont le style doit être défini.

### <a name="remarks"></a>Notes

Le style d’un volet détermine le mode d’affichage du volet.

Pour obtenir la liste des styles disponibles pour les barres d’État, consultez [SetPaneInfo](#setpaneinfo).

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a> CStatusBar :: SetPaneText

Appelez cette fonction membre pour définir le texte du volet en fonction de la chaîne pointée par *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index du volet dont le texte doit être défini.

*lpszNewText*<br/>
Pointeur vers le nouveau texte du volet.

*bUpdate*<br/>
Si la valeur est TRUE, le volet est invalidé une fois que le texte est défini.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Après avoir appelé `SetPaneText` , vous devez ajouter un gestionnaire de mise à jour de l’interface utilisateur pour afficher le nouveau texte dans la barre d’État.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl (classe)](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)
