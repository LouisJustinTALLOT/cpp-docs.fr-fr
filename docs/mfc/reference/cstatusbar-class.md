---
title: Classe CStatusBar
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
ms.openlocfilehash: 0549ee10faa15b80b18a0bee2f115425002e1479
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376260"
---
# <a name="cstatusbar-class"></a>Classe CStatusBar

Barre de contrôles avec une ligne de volets de sortie de texte ou « indicateurs ».

## <a name="syntax"></a>Syntaxe

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|Construit un objet `CStatusBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Obtient l’index pour une pièce d’identité d’indicateur donné.|
|[CStatusBar::Créer](#create)|Crée la barre d’état, `CStatusBar` la fixe à l’objet et définit la police initiale et la hauteur de la barre.|
|[CStatusBar::CreateEx](#createex)|Crée `CStatusBar` un objet avec des `CStatusBarCtrl` styles supplémentaires pour l’objet intégré.|
|[CStatusBar::DrawItem](#drawitem)|Appelé lorsqu’un aspect visuel d’un contrôle de barre d’état propriétaire-tirage change.|
|[CStatusBar::GetItemID](#getitemid)|Obtient l’ID d’indicateur pour un index donné.|
|[CStatusBar::GetItemRect](#getitemrect)|Obtient le rectangle d’affichage pour un index donné.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Obtient l’ID d’indicateur, le modèle, et la largeur pour un index donné.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Obtient le style d’indicateur pour un indice donné.|
|[CStatusBar::GetPaneText](#getpanetext)|Obtient le texte d’indicateur pour un index donné.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Permet un accès direct au contrôle commun sous-jacent.|
|[CStatusBar::SetIndicators](#setindicators)|Définit les UDI d’indicateur.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Définit l’ID, le style et la largeur des indicateurs pour un index donné.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Définit le style d’indicateur pour un indice donné.|
|[CStatusBar::SetPaneText](#setpanetext)|Définit le texte de l’indicateur pour un indice donné.|

## <a name="remarks"></a>Notes

Les volets de sortie sont couramment utilisés comme lignes de messages et comme indicateurs d’état. Par exemple, les lignes de message d’assistance du menu qui expliquent brièvement la commande de menu sélectionnée et les indicateurs qui montrent l’état du VERROU SCROLL, NUM LOCK et d’autres touches.

[CStatusBar:GetStatusBarCtrl](#getstatusbarctrl), une fonction membre nouvelle pour MFC 4.0, vous permet de profiter du support du contrôle commun Windows pour la personnalisation de barre de statut et des fonctionnalités supplémentaires. `CStatusBar`fonctions des membres vous donnent la plupart des fonctionnalités des contrôles communs Windows; cependant, lorsque `GetStatusBarCtrl`vous appelez, vous pouvez donner à vos barres de statut encore plus des caractéristiques d’une barre de statut Windows 95/98. Lorsque vous `GetStatusBarCtrl`appelez, il retournera `CStatusBarCtrl` une référence à un objet. Voir [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) pour plus d’informations sur la conception des barres d’outils à l’aide de contrôles communs Windows. Pour plus d’informations générales sur les contrôles courants, voir [contrôles communs](/windows/win32/Controls/common-controls-intro) dans le SDK Windows.

Le cadre stocke l’information sur les indicateurs dans un tableau avec l’indicateur le plus à gauche à la position 0. Lorsque vous créez une barre de statut, vous utilisez une gamme d’ID de chaîne que le cadre associe aux indicateurs correspondants. Vous pouvez ensuite utiliser un ID de chaîne ou un index pour accéder à un indicateur.

Par défaut, le premier indicateur est « élastique » : il reprend la longueur de la barre d’état non utilisée par les autres volets indicateurs, de sorte que les autres volets sont alignés à droite.

Pour créer une barre de statut, suivez ces étapes :

1. Construisez `CStatusBar` l’objet.

1. Appelez la fonction [Créer](#create) (ou [CréerEx)](#createex)pour créer la `CStatusBar` fenêtre de barre d’état et l’attacher à l’objet.

1. Appelez [setIndicators](#setindicators) pour associer une pièce d’identité de chaîne à chaque indicateur.

Il existe trois façons de mettre à jour le texte dans un volet de barre de statut :

1. Appelez [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) pour mettre à jour le texte dans le volet 0 seulement.

1. Appelez [CCmdUI:SetText](../../mfc/reference/ccmdui-class.md#settext) dans le gestionnaire de ON_UPDATE_COMMAND_UI de la barre d’état.

1. Appelez [SetPaneText](#setpanetext) pour mettre à jour le texte pour n’importe quel volet.

Appelez [SetPaneStyle](#setpanestyle) pour mettre à jour le style d’une vitre de barre d’état.

Pour plus d’informations sur l’utilisation `CStatusBar`, voir [l’article Status Bar Implementation in MFC](../../mfc/status-bar-implementation-in-mfc.md) et Technical Note [31 : Control Bars](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar (en)](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CStatusBar::CommandToIndex

Obtient l’indice d’indicateur pour une pièce d’identité donnée.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Paramètres

*nIDFind (en)*<br/>
Id de chaîne de l’indicateur dont l’index doit être récupéré.

### <a name="return-value"></a>Valeur de retour

L’indice de l’indicateur en cas de succès; -1 si elle n’est pas réussie.

### <a name="remarks"></a>Notes

L’indice du premier indicateur est de 0.

## <a name="cstatusbarcreate"></a><a name="create"></a>CStatusBar::Créer

Crée une barre de statut (une fenêtre `CStatusBar` enfant) et l’associe à l’objet.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers [l’objet CWnd](../../mfc/reference/cwnd-class.md) dont la fenêtre Windows est le parent de la barre d’état.

*dwStyle (en)*<br/>
Le style statut-bar. En plus des [styles](../../mfc/reference/styles-used-by-mfc.md#window-styles)Windows standard, ces styles sont pris en charge.

- CBRS_TOP barre de contrôle est au sommet de la fenêtre du cadre.

- CBRS_BOTTOM barre de contrôle se trouve au bas de la fenêtre du cadre.

- CBRS_NOALIGN barre de contrôle n’est pas repositionnée lorsque le parent est resized.

*nID*<br/>
L’id de la fenêtre pour enfants de la barre d’outils.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Définit également la police initiale et définit la hauteur de la barre d’état à une valeur par défaut.

## <a name="cstatusbarcreateex"></a><a name="createex"></a>CStatusBar::CreateEx

Appelez cette fonction pour créer une barre de statut `CStatusBar` (une fenêtre d’enfant) et l’associer à l’objet.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers [l’objet CWnd](../../mfc/reference/cwnd-class.md) dont la fenêtre Windows est le parent de la barre d’état.

*dwCtrlStyle (en)*<br/>
Styles supplémentaires pour la création de l’objet [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) intégré. La valeur par défaut spécifie une barre de statut sans prise de contrôle ni support de pointe. Les styles de barre d’état pris en charge sont :

- SBARS_SIZEGRIP Le contrôle de la barre d’état comprend une poignée de dimensionnement à l’extrémité droite de la barre d’état. Une poignée de dimensionnement est semblable à une bordure de dimensionnement; il s’agit d’une zone rectangulaire que l’utilisateur peut cliquer et faire glisser pour resize la fenêtre parente.

- SBT_TOOLTIPS La barre d’état prend en charge les outils.

Pour plus de détails sur ces styles, voir [Paramètres pour le CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle (en)*<br/>
Le style de barre de statut. La valeur par défaut précise la création d’une barre d’état visible au bas de la fenêtre du cadre. Appliquer toute combinaison de styles de contrôle de barre d’état énumérés dans [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [CDialogBar::Créer](../../mfc/reference/cdialogbar-class.md#create). Cependant, ce paramètre doit toujours inclure les styles WS_CHILD et WS_VISIBLE.

*nID*<br/>
L’id de la fenêtre pour enfants de la barre d’état.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction définit également la police initiale et définit la hauteur de la barre d’état à une valeur par défaut.

Utilisez `CreateEx`, au lieu de [créer](#create), lorsque certains styles doivent être présents lors de la création du contrôle de barre d’état intégré. Par exemple, définissez *dwCtrlStyle* pour SBT_TOOLTIPS pour afficher des outils dans un objet de barre d’état.

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a>CStatusBar::CStatusBar

Construit un `CStatusBar` objet, crée une police par défaut de barre d’état si nécessaire, et définit les caractéristiques de la police aux valeurs par défaut.

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a>CStatusBar::DrawItem

Cette fonction de membre est appelée par le cadre quand un aspect visuel d’une barre de statut tirée par le propriétaire change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur vers une structure [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` membre `DRAWITEMSTRUCT` de la structure définit l’action de dessin qui doit être effectuée. Remplacer cette fonction de membre pour implémenter le dessin d’un objet de dessin du `CStatusBar` propriétaire. L’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction de membre.

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a>CStatusBar::GetItemID

Retourne l’ID de l’indicateur spécifié par *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’indicateur dont l’ID doit être récupéré.

### <a name="return-value"></a>Valeur de retour

L’ID de l’indicateur spécifié par *nIndex*.

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a>CStatusBar::GetItemRect

Copies des coordonnées de l’indicateur spécifiés par *nIndex* dans la structure pointée par *lpRect*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’indicateur dont les coordonnées de rectangle doivent être récupérées.

*lpRect*<br/>
Indique une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui recevra les coordonnées de l’indicateur spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Les coordonnées sont en pixels par rapport au coin supérieur gauche de la barre d’état.

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CStatusBar::GetPaneInfo

Définit *nID*, *nStyle*, et *cxWidth* à l’ID, le style et la largeur de la vitre de l’indicateur à l’emplacement spécifié par *nIndex*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la vitre dont l’information doit être récupérée.

*nID*<br/>
Référence à un UINT qui est réglé sur l’ID de la vitre.

*nStyle*<br/>
Référence à un UINT qui est réglé sur le style de la vitre.

*cxWidth (en)*<br/>
Référence à un intégreur qui est réglé sur la largeur de la vitre.

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a>CStatusBar::GetPaneStyle

Appelez cette fonction de membre pour récupérer le style de la vitre d’une barre d’état.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la vitre dont le style doit être récupéré.

### <a name="return-value"></a>Valeur de retour

Le style de la vitre statut-bar spécifié par *nIndex*.

### <a name="remarks"></a>Notes

Le style d’un volet détermine l’apparence de la vitre.

Pour une liste de styles disponibles pour les barres d’état, voir [Créer](#create).

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a>CStatusBar::GetPaneText

Appelez cette fonction de membre pour récupérer le texte qui apparaît dans une vitre de barre d’état.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la vitre dont le texte doit être récupéré.

*rString (en)*<br/>
Une référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient le texte à récupérer.

### <a name="return-value"></a>Valeur de retour

Un `CString` objet contenant le texte du volet.

### <a name="remarks"></a>Notes

La deuxième forme de cette `CString` fonction de membre remplit un objet avec le texte de chaîne.

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a>CStatusBar::GetStatusBarCtrl

Cette fonction de membre permet un accès direct au contrôle commun sous-jacent.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Contient une référence à un objet [CStatusBarCtrl.](../../mfc/reference/cstatusbarctrl-class.md)

### <a name="remarks"></a>Notes

Utilisez `GetStatusBarCtrl` pour tirer parti de la fonctionnalité du contrôle commun de la barre d’état Windows, et pour profiter du support [que CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) fournit pour la personnalisation de la barre de statut. Par exemple, en utilisant le contrôle commun, vous pouvez spécifier un style qui inclut une poignée de dimensionnement sur la barre d’état, ou vous pouvez spécifier un style pour que la barre d’état apparaisse en haut de la zone client de la fenêtre mère.

Pour plus d’informations générales sur les contrôles courants, voir [les contrôles communs](/windows/win32/Controls/common-controls-intro) dans le SDK Windows.

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a>CStatusBar::SetIndicators

Définit l’ID de chaque indicateur à la valeur spécifiée par l’élément correspondant de la *carte lpIDArray*, charge la ressource de chaîne spécifiée par chaque ID, et définit le texte de l’indicateur à la chaîne.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Paramètres

*lpIDArray*<br/>
Pointeur vers un tableau de d’IDs.

*nIDCompte*<br/>
Nombre d’éléments dans le tableau pointé par *lpIDArray*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CStatusBar::SetPaneInfo

Définit la vitre d’indicateur spécifiée à une nouvelle pièce d’identité, style et largeur.

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la vitre de l’indicateur dont le style doit être défini.

*nID*<br/>
Nouvelle pièce d’identité pour le volet indicateur.

*nStyle*<br/>
Nouveau style pour la vitre de l’indicateur.

*cxWidth (en)*<br/>
Nouvelle largeur pour la vitre de l’indicateur.

### <a name="remarks"></a>Notes

Les styles d’indicateurs suivants sont pris en charge :

- SBPS_NOBORDERS frontière 3D autour de la vitre.

- SBPS_POPOUT frontière inversée pour que le texte « s’évanouit ».

- SBPS_DISABLED Ne dessinez pas de texte.

- SBPS_STRETCH’étirement de la vitre pour remplir l’espace inutilisé. Une seule vitre par barre d’état peut avoir ce style.

- SBPS_NORMAL Pas d’étirement, de frontières ou de pop-out.

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CStatusBar::SetPaneStyle

Appelez cette fonction de membre pour définir le style de la vitre d’une barre de statut.

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la vitre dont le style doit être défini.

*nStyle*<br/>
Style de la vitre dont le style doit être défini.

### <a name="remarks"></a>Notes

Le style d’un volet détermine l’apparence de la vitre.

Pour une liste de styles disponibles pour les barres d’état, voir [SetPaneInfo](#setpaneinfo).

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a>CStatusBar::SetPaneText

Appelez cette fonction de membre pour régler le texte de la vitre à la chaîne pointée vers *le lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la vitre dont le texte doit être défini.

*lpszNewText*<br/>
Pointeur vers le nouveau texte de pane.

*bUpdate (en)*<br/>
Si VRAI, la vitre est invalidée après la mise en place du texte.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Après votre `SetPaneText`appel, vous devez ajouter un gestionnaire de mise à jour de l’interface utilisateur pour afficher le nouveau texte dans la barre d’état.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl, classe](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)
