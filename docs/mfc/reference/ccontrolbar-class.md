---
title: CControlBar Class
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: deb95d76e6d68ba5b9fad82bca1d88fd71c5a547
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369392"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

La classe de base pour les classes de barres de contrôle [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md), et [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Syntaxe

```
class CControlBar : public CWnd
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|Construit un objet `CControlBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Retourne la taille d’une barre de contrôle dynamique comme objet [CSize.](../../atl-mfc-shared/reference/csize-class.md)|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Retourne la taille de la barre de contrôle comme un objet [CSize.](../../atl-mfc-shared/reference/csize-class.md)|
|[CControlBar::CalcInsideRect](#calcinsiderect)|Retourne les dimensions actuelles de la zone de la barre de commande; y compris les frontières.|
|[CControlBar::DoPaint](#dopaint)|Rend les bordures et la pince de la barre de contrôle.|
|[CControlBar::DrawBorders](#drawborders)|Rend les bordures de la barre de contrôle.|
|[CControlBar::DrawGripper](#drawgripper)|Rend la pince de la barre de contrôle.|
|[CControlBar::EnableDocking](#enabledocking)|Permet d’amarrer ou de flotter une barre de commande.|
|[CControlBar::GetBarStyle](#getbarstyle)|Récupère les paramètres de style barre de contrôle.|
|[CControlBar::GetBorders](#getborders)|Récupère les valeurs frontalières de la barre de contrôle.|
|[CControlBar::GetCount](#getcount)|Retourne le nombre d’éléments non HWND dans la barre de contrôle.|
|[CControlBar::GetDockingFrame](#getdockingframe)|Retourne un pointeur sur le cadre auquel une barre de commande est amarré.|
|[CControlBar::IsFloating](#isfloating)|Retourne une valeur non zéro si la barre de contrôle en question est une barre de contrôle flottante.|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Appelle les gestionnaires d’interface utilisateur de commande.|
|[CControlBar::SetBarStyle](#setbarstyle)|Modifie les paramètres de style barre de contrôle.|
|[CControlBar::SetBorders](#setborders)|Définit les valeurs frontalières de la barre de contrôle.|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Change le propriétaire sur place d’une barre de contrôle.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CControlBar:m_bAutoDelete](#m_bautodelete)|Si non zéro, `CControlBar` l’objet est supprimé lorsque la barre de contrôle Windows est détruite.|
|[CControlBar:m_pInPlaceOwner](#m_pinplaceowner)|Le propriétaire sur place de la barre de contrôle.|

## <a name="remarks"></a>Notes

Une barre de contrôle est une fenêtre qui est généralement alignée à gauche ou à droite d’une fenêtre de cadre. Il peut contenir des articles pour enfants qui sont soit des contrôles basés sur HWND, qui sont des fenêtres qui génèrent et répondent aux messages Windows, ou des éléments non basés sur HWND, qui ne sont pas des fenêtres et sont gérés par le code d’application ou le code-cadre. Les boîtes de liste et les contrôles de modification sont des exemples de contrôles basés sur le HWND; les vitres de barre d’état et les boutons de bitmap sont des exemples de contrôles non basés sur le HWND.

Les fenêtres de contrôle-bar sont habituellement des fenêtres d’enfant d’une fenêtre de cadre parent et sont habituellement des frères et sœurs à la vue du client ou client MDI de la fenêtre de cadre. Un `CControlBar` objet utilise des informations sur le rectangle du client de la fenêtre parente pour se positionner. Il informe ensuite la fenêtre parente de la quantité d’espace qui n’est pas allouée dans la zone cliente de la fenêtre mère.

Pour plus `CControlBar`d’informations sur , voir:

- [Barres de contrôles](../../mfc/control-bars.md)

- [Note technique 31: Barres de contrôle](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout

Le cadre appelle cette fonction membre à calculer les dimensions d’une barre d’outils dynamique.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Paramètres

*nLength (en)*<br/>
La dimension demandée de la barre de contrôle, horizontale ou verticale, selon *dwMode*.

*nMode*<br/>
Les drapeaux prédéfinis suivants sont utilisés pour déterminer la hauteur et la largeur de la barre de commande dynamique. Utilisez l’opérateur bitwise-OR (&#124;) pour combiner les drapeaux.

|Drapeaux de mode de mise en page|Signification|
|-----------------------|-------------------|
|LM_STRETCH|Indique si la barre de commande doit être étirée jusqu’à la taille du cadre. Définissez si la barre n’est pas une barre d’amarrage (non disponible pour l’amarrage). Non réglé lorsque la barre est amarré ou flottante (disponible pour l’amarrage). Si elle est définie, LM_STRETCH ignore *nLength* et renvoie les dimensions en fonction de l’état LM_HORZ. LM_STRETCH fonctionne de la même manière que le paramètre *bStretch* utilisé dans [CalcFixedLayout;](#calcfixedlayout) voir que le membre fonctionne pour plus d’informations sur la relation entre l’étirement et l’orientation.|
|LM_HORZ|Indique que la barre est orientée horizontalement ou verticalement. Définissez si la barre est orientée horizontalement, et si elle est orientée verticalement, elle n’est pas définie. LM_HORZ fonctionne de la même manière que le *paramètre bHorz* utilisé dans [CalcFixedLayout](#calcfixedlayout); voir que le membre fonctionne pour plus d’informations sur la relation entre l’étirement et l’orientation.|
|LM_MRUWIDTH|Plus récemment utilisé largeur dynamique. Ignore *le paramètre nLength* et utilise la largeur la plus récemment utilisée.|
|LM_HORZDOCK|Dimensions horizontales à quai. Ignore *le paramètre nLength* et retourne la taille dynamique avec la plus grande largeur.|
|LM_VERTDOCK|Dimensions verticales à quai. Ignore *le paramètre nLength* et retourne la taille dynamique avec la plus grande hauteur.|
|LM_LENGTHY|Définir si *nLength* indique la hauteur (direction Y) au lieu de la largeur.|
|LM_COMMIT|Réinitialisations LM_MRUWIDTH à la largeur actuelle de la barre de commande flottante.|

### <a name="return-value"></a>Valeur de retour

La taille de la barre de contrôle, en pixels, d’un objet [CSize.](../../atl-mfc-shared/reference/csize-class.md)

### <a name="remarks"></a>Notes

Remplacez cette fonction de membre pour fournir votre `CControlBar`propre mise en page dynamique dans les classes que vous dérivez de . Les classes MFC dérivées de `CControlBar`, telles que [CToolbar](../../mfc/reference/ctoolbar-class.md), remplacent cette fonction de membre et fournissent leur propre mise en œuvre.

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout

Appelez cette fonction de membre pour calculer la taille horizontale d’une barre de commande.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*bStretch*<br/>
Indique si la barre doit être étirée jusqu’à la taille du cadre. Le paramètre *bStretch* est nonzero lorsque la barre n’est pas une barre d’amarrage (non disponible pour l’amarrage) et est de 0 quand il est amarré ou flottant (disponible pour l’amarrage).

*bHorz (en)*<br/>
Indique que la barre est orientée horizontalement ou verticalement. Le *paramètre bHorz* est nonzero si la barre est orientée horizontalement et est 0 si elle est orientée verticalement.

### <a name="return-value"></a>Valeur de retour

La taille de la barre de `CSize` contrôle, en pixels, d’un objet.

### <a name="remarks"></a>Notes

Les barres de commande telles que les barres à outils peuvent s’étirer horizontalement ou verticalement pour accueillir les boutons contenus dans la barre de contrôle.

Si *bStretch* est VRAI, étirer la dimension le long de l’orientation fournie par *bHorz*. En d’autres termes, si *bHorz* est FALSE, la barre de commande est étirée verticalement. Si *bStretch* est FALSE, aucun étirement ne se produit. Le tableau suivant montre les permutations possibles, et les styles de barres de contrôle résultant, de *bStretch* et *bHorz*.

|bStretch|bHorz (en)|Étirement|Orientation|Docking/Pas amarrage|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Étirement horizontal|Orienté horizontalement|Ne pas accoster|
|TRUE|FALSE|Étirement vertical|Orienté verticalement|Ne pas accoster|
|FALSE|TRUE|Aucun étirement disponible|Orienté horizontalement|Ancrage|
|FALSE|FALSE|Aucun étirement disponible|Orienté verticalement|Ancrage|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>CControlBar::CalcInsideRect

Le cadre appelle cette fonction pour calculer la zone client de la barre de contrôle.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Contient les dimensions actuelles de la barre de contrôle; y compris les frontières.

*bHorz (en)*<br/>
Indique que la barre est orientée horizontalement ou verticalement. Le *paramètre bHorz* est nonzero si la barre est orientée horizontalement et est 0 si elle est orientée verticalement.

### <a name="remarks"></a>Notes

Cette fonction est appelée avant que la barre de contrôle ne soit peinte.

Remplacer cette fonction pour personnaliser le rendu des bordures et la barre de saisie de la barre de contrôle.

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>CControlBar::CControlBar

Construit un objet `CControlBar`.

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>CControlBar::DoPaint

Appelé par le cadre pour rendre les frontières et la barre de saisie de la barre de contrôle.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Indique le contexte de l’appareil à utiliser pour rendre les bordures et la saisie de la barre de contrôle.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour personnaliser le comportement de dessin de la barre de contrôle.

Une autre méthode de personnalisation consiste à remplacer les `DrawBorders` fonctions et à `DrawGripper` les ajouter et à ajouter du code de dessin personnalisé pour les frontières et la pince. Étant donné que ces `DoPaint` méthodes sont appelées `DoPaint` par la méthode par défaut, un remplacement n’est pas nécessaire.

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>CControlBar::DrawBorders

Appelé par le cadre pour rendre les frontières de la barre de contrôle.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Indique le contexte de l’appareil à utiliser pour rendre les bordures de la barre de contrôle.

*Rect*<br/>
Un `CRect` objet contenant les dimensions de la barre de contrôle.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour personnaliser l’apparence des bordures de la barre de contrôle.

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>CControlBar::DrawGripper

Appelé par le cadre pour rendre la pince de la barre de contrôle.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Indique le contexte de l’appareil à utiliser pour rendre la pince de barre de commande.

*Rect*<br/>
Un `CRect` objet contenant les dimensions de la pince de barre de commande.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour personnaliser l’apparence de la pince de barre de commande.

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>CControlBar::EnableDocking

Appelez cette fonction pour permettre l’amarrage d’une barre de contrôle.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Paramètres

*dwDockStyle (en)*<br/>
Précise si la barre de contrôle prend en charge l’amarrage et les côtés de sa fenêtre parente auxquels la barre de commande peut être amarrée, si elle est appuyée. Peut être un ou plusieurs des éléments suivants :

- CBRS_ALIGN_TOP permet l’amarrage au sommet de la zone client.

- CBRS_ALIGN_BOTTOM permet l’amarrage au bas de la zone client.

- CBRS_ALIGN_LEFT permet l’amarrage sur le côté gauche de la zone client.

- CBRS_ALIGN_RIGHT permet l’amarrage sur le côté droit de la zone client.

- CBRS_ALIGN_ANY permet l’amarrage de n’importe quel côté de la zone client.

- CBRS_FLOAT_MULTI permet de flotter plusieurs barres de commande dans une seule fenêtre à mini-cadre.

Si 0 (c’est-à-dire, indiquant aucun drapeau), la barre de commande ne s’amarrera pas.

### <a name="remarks"></a>Notes

Les côtés spécifiés doivent correspondre à l’un des côtés activés pour l’amarrage dans la fenêtre du cadre de destination, ou la barre de commande ne peut pas être amarrée à cette fenêtre de cadre.

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>CControlBar::GetBarStyle

Appelez cette fonction pour déterminer quels **CBRS_** (styles de barres de contrôle) sont actuellement définis pour la barre de contrôle.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Valeur de retour

Les **réglages** actuels CBRS_ (style de barre de contrôle) pour la barre de contrôle. Voir [CControlBar:SetBarStyle](#setbarstyle) pour la liste complète des styles disponibles.

### <a name="remarks"></a>Notes

Ne gère pas **WS_** styles (style fenêtre).

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>CControlBar::GetBorders

Retourne les valeurs frontalières actuelles de la barre de contrôle.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CRect` objet qui contient la largeur actuelle (en pixels) de chaque côté de l’objet de barre de commande. Par exemple, la valeur du membre *gauche,* de l’objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) est la largeur de la bordure de la main gauche.

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>CControlBar::GetCount

Retourne le nombre d’éléments non `CControlBar` HWND sur l’objet.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments non HWND `CControlBar` sur l’objet. Cette fonction renvoie 0 pour un objet [CDialogBar.](../../mfc/reference/cdialogbar-class.md)

### <a name="remarks"></a>Notes

Le type de l’élément dépend de l’objet dérivé : des vitres pour les objets [CStatusBar,](../../mfc/reference/cstatusbar-class.md) des boutons et des séparateurs pour les objets [CToolBar.](../../mfc/reference/ctoolbar-class.md)

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>CControlBar::GetDockingFrame

Appelez cette fonction de membre pour obtenir un pointeur à la fenêtre de cadre actuelle à laquelle votre barre de commande est amarrée.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une fenêtre de cadre en cas de succès; autrement NULL.

Si la barre de contrôle n’est pas amarrée à une fenêtre de cadre (c’est-à-dire si la barre de contrôle flotte), cette fonction retournera un pointeur à son parent [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Notes

Pour plus d’informations sur les barres de contrôle amarrées, voir [CControlBar::EnableDocking](#enabledocking) et [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>CControlBar::IsFloating

Appelez cette fonction de membre pour déterminer si la barre de commande flotte ou amarré.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la barre de contrôle flotte; sinon 0.

### <a name="remarks"></a>Notes

Pour changer l’état d’une barre de contrôle de amarré à flottant, appelez [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>CControlBar:m_bAutoDelete

Si non zéro, `CControlBar` l’objet est supprimé lorsque la barre de contrôle Windows est détruite.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Notes

*m_bAutoDelete* est une variable publique de type BOOL.

Un objet de barre de contrôle est généralement intégré dans un objet de fenêtre de cadre. Dans ce cas, *m_bAutoDelete* est de 0 parce que l’objet intégré de barre de contrôle est détruit lorsque la fenêtre de cadre est détruite.

Définissez cette variable à une valeur non `CControlBar` zéro si vous allouez un objet sur le tas et que vous n’avez pas l’intention d’appeler **supprimer**.

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>CControlBar:m_pInPlaceOwner

Le propriétaire sur place de la barre de contrôle.

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI

Cette fonction de membre est appelée par le cadre pour mettre à jour l’état de la barre d’outils ou de la barre d’état.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Points à la fenêtre de cadre principale de l’application. Ce pointeur est utilisé pour l’acheminement des messages de mise à jour.

*bDisableIfNoHndler*<br/>
Indicateur indiquant si un contrôle qui n’a pas de gestionnaire de mise à jour doit être automatiquement affiché comme désactivé.

### <a name="remarks"></a>Notes

Pour mettre à jour un bouton ou une vitre individuel, utilisez la ON_UPDATE_COMMAND_UI macro dans votre carte de message pour définir un gestionnaire de mise à jour de manière appropriée. Voir [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) pour plus d’informations sur l’utilisation de cette macro.

`OnUpdateCmdUI`est appelé par le cadre lorsque l’application est inactive. La fenêtre de cadre à mettre à jour doit être une fenêtre d’enfant, au moins indirectement, d’une fenêtre de cadre visible. `OnUpdateCmdUI`est un avancé primordial.

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>CControlBar::SetBarStyle

Appelez cette fonction pour définir les styles **CBRS_** souhaités pour la barre de contrôle.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Les styles souhaités pour la barre de contrôle. Peut être un ou plusieurs des éléments suivants :

- CBRS_ALIGN_TOP permet d’amarrer la barre de contrôle au sommet de la zone cliente d’une fenêtre de cadre.

- CBRS_ALIGN_BOTTOM permet d’amarrer la barre de contrôle au bas de la zone cliente d’une fenêtre de cadre.

- CBRS_ALIGN_LEFT permet d’amarrer la barre de contrôle sur le côté gauche de la zone cliente d’une fenêtre de cadre.

- CBRS_ALIGN_RIGHT permet d’amarrer la barre de contrôle sur le côté droit de la zone cliente d’une fenêtre de cadre.

- CBRS_ALIGN_ANY permet d’amarrer la barre de contrôle de n’importe quel côté de la zone client d’une fenêtre de cadre.

- CBRS_BORDER_TOP provoque un dessin d’une bordure sur le bord supérieur de la barre de contrôle lorsqu’elle serait visible.

- CBRS_BORDER_BOTTOM provoque le dessin d’une bordure sur le bord inférieur de la barre de contrôle lorsqu’elle serait visible.

- CBRS_BORDER_LEFT provoque un dessin de frontière sur le bord gauche de la barre de contrôle lorsqu’elle serait visible.

- CBRS_BORDER_RIGHT provoque le dessin d’une bordure sur le bord droit de la barre de contrôle lorsqu’elle serait visible.

- CBRS_FLOAT_MULTI permet de flotter plusieurs barres de commande dans une seule fenêtre à mini-cadre.

- CBRS_TOOLTIPS provoque des conseils d’outils à afficher pour la barre de contrôle.

- CBRS_FLYBY provoque la mise à jour du texte du message en même temps que les conseils d’outils.

- CBRS_GRIPPER provoque une pince, semblable à celle utilisée `CReBar` sur les bandes d’un objet, à tirer pour toute `CControlBar`classe dérivée.

### <a name="remarks"></a>Notes

N’affecte pas les **paramètres WS_** (style fenêtre).

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>CControlBar::SetBorders

Appelez cette fonction pour définir la taille des bordures de la barre de contrôle.

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*cxLeft*<br/>
La largeur (en pixels) de la bordure gauche de la barre de contrôle.

*cyTop (en)*<br/>
La hauteur (en pixels) de la bordure supérieure de la barre de contrôle.

*cxRight*<br/>
La largeur (en pixels) de la bordure droite de la barre de contrôle.

*cyBottom (en)*<br/>
La hauteur (en pixels) de la bordure inférieure de la barre de contrôle.

*lpRect*<br/>
Pointeur d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient la largeur actuelle (en pixels) de chaque bordure de l’objet de barre de commande.

### <a name="example"></a>Exemple

L’exemple de code suivant définit les bordures supérieures et inférieures de la barre de contrôle à 5 pixels, et les bordures gauche et droite à 2 pixels :

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>CControlBar::SetInPlaceOwner

Change le propriétaire sur place d’une barre de contrôle.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Pointeur vers un objet `CWnd`.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBar, classe](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar, classe](../../mfc/reference/cdialogbar-class.md)<br/>
[Classe CStatusBar](../../mfc/reference/cstatusbar-class.md)<br/>
[Classe CReBar](../../mfc/reference/crebar-class.md)
