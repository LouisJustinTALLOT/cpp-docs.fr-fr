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
ms.openlocfilehash: 41e40b3da7b4a294fe396a9d93f7c6a93593ff95
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420532"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

Classe de base pour les classes de barre de contrôle [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md)et [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Syntaxe

```
class CControlBar : public CWnd
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Name|Description|
|----------|-----------------|
|[CControlBar :: CControlBar](#ccontrolbar)|Construit un objet `CControlBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CControlBar :: CalcDynamicLayout](#calcdynamiclayout)|Retourne la taille d’une barre de contrôle dynamique sous la forme d’un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .|
|[CControlBar :: CalcFixedLayout](#calcfixedlayout)|Retourne la taille de la barre de contrôle sous la forme d’un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .|
|[CControlBar :: CalcInsideRect](#calcinsiderect)|Retourne les dimensions actuelles de la zone de la barre de contrôle ; y compris les bordures.|
|[CControlBar ::D oPaint](#dopaint)|Restitue les bordures et la pince de la barre de contrôle.|
|[CControlBar ::D rawBorders](#drawborders)|Restitue les bordures de la barre de contrôle.|
|[CControlBar ::D rawGripper](#drawgripper)|Restitue la pince de la barre de contrôle.|
|[CControlBar :: EnableDocking](#enabledocking)|Permet à une barre de contrôle d’être ancrée ou flottante.|
|[CControlBar :: GetBarStyle](#getbarstyle)|Récupère les paramètres de style de barre de contrôle.|
|[CControlBar :: GetBorders](#getborders)|Récupère les valeurs de bordure de la barre de contrôle.|
|[CControlBar :: GetCount](#getcount)|Retourne le nombre d’éléments non HWND dans la barre de contrôle.|
|[CControlBar :: GetDockingFrame](#getdockingframe)|Retourne un pointeur vers le frame auquel une barre de contrôle est ancrée.|
|[CControlBar :: IsFloating](#isfloating)|Retourne une valeur différente de zéro si la barre de contrôle en question est une barre de contrôle flottante.|
|[CControlBar :: OnUpdateCmdUI](#onupdatecmdui)|Appelle les gestionnaires de l’interface utilisateur de la commande.|
|[CControlBar :: SetBarStyle](#setbarstyle)|Modifie les paramètres de style de barre de contrôle.|
|[CControlBar :: SetBorders](#setborders)|Définit les valeurs de bordure de la barre de contrôle.|
|[CControlBar :: SetInPlaceOwner](#setinplaceowner)|Modifie le propriétaire sur place d’une barre de contrôle.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CControlBar :: m_bAutoDelete](#m_bautodelete)|Si la valeur est différente de zéro, l’objet `CControlBar` est supprimé lorsque la barre de contrôle Windows est détruite.|
|[CControlBar :: m_pInPlaceOwner](#m_pinplaceowner)|Propriétaire sur place de la barre de contrôle.|

## <a name="remarks"></a>Notes

Une barre de contrôle est une fenêtre qui est généralement alignée à gauche ou à droite d’une fenêtre frame. Il peut contenir des éléments enfants qui sont soit des contrôles basés sur HWND, qui sont des fenêtres qui génèrent et répondent à des messages Windows, ou des éléments non basés sur HWND, qui ne sont pas Windows et sont gérés par le code d’application ou le code d’infrastructure. Les zones de liste et les contrôles d’édition sont des exemples de contrôles basés sur HWND. les volets de barre d’État et les boutons bitmap sont des exemples de contrôles non basés sur HWND.

Les fenêtres de la barre de contrôle sont généralement des fenêtres enfants d’une fenêtre frame parente et sont généralement des frères de la vue cliente ou du client MDI de la fenêtre frame. Un objet `CControlBar` utilise des informations sur le rectangle client de la fenêtre parente pour se positionner lui-même. Il informe ensuite la fenêtre parente de la quantité d’espace restant non allouée dans la zone cliente de la fenêtre parente.

Pour plus d’informations sur `CControlBar`, consultez :

- [Barres de contrôles](../../mfc/control-bars.md)

- [Note technique 31 : barres de contrôles](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

##  <a name="calcdynamiclayout"></a>CControlBar :: CalcDynamicLayout

L’infrastructure appelle cette fonction membre pour calculer les dimensions d’une barre d’outils dynamique.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Paramètres

*nLength*<br/>
Dimension demandée de la barre de contrôle, horizontale ou verticale, en fonction de *dwMode*.

*nMode*<br/>
Les indicateurs prédéfinis suivants sont utilisés pour déterminer la hauteur et la largeur de la barre de contrôle dynamique. Utilisez l’opérateur de bits or&#124;() pour combiner les indicateurs.

|Indicateurs du mode de disposition|Signification|
|-----------------------|-------------------|
|LM_STRETCH|Indique si la barre de contrôle doit être étirée à la taille du frame. Définit si la barre n’est pas une barre d’ancrage (non disponible pour l’ancrage). Non défini lorsque la barre est ancrée ou flottante (disponible pour l’ancrage). Si cette option est définie, LM_STRETCH ignore *nLength* et retourne les dimensions en fonction de l’état de LM_HORZ. LM_STRETCH fonctionne de la même façon que le paramètre *bStretch* utilisé dans [CalcFixedLayout](#calcfixedlayout); Pour plus d’informations sur la relation entre l’étirement et l’orientation, consultez la fonction membre.|
|LM_HORZ|Indique que la barre est orientée horizontalement ou verticalement. Défini si la barre est orientée horizontalement et si elle est orientée verticalement, elle n’est pas définie. LM_HORZ fonctionne de la même façon que le paramètre *bHorz* utilisé dans [CalcFixedLayout](#calcfixedlayout); Pour plus d’informations sur la relation entre l’étirement et l’orientation, consultez la fonction membre.|
|LM_MRUWIDTH|Dernière largeur dynamique utilisée. Ignore le paramètre *nLength* et utilise la largeur utilisée la plus récemment mémorisée.|
|LM_HORZDOCK|Dimensions ancrées horizontales. Ignore le paramètre *nLength* et retourne la taille dynamique avec la largeur la plus grande.|
|LM_VERTDOCK|Dimensions ancrées verticales. Ignore le paramètre *nLength* et retourne la taille dynamique avec la plus grande hauteur.|
|LM_LENGTHY|Définit si *nLength* indique Height (direction Y) au lieu de Width.|
|LM_COMMIT|Réinitialise LM_MRUWIDTH à la largeur actuelle de la barre de contrôle flottante.|

### <a name="return-value"></a>Valeur de retour

Taille de la barre de contrôle, en pixels, d’un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) .

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour fournir votre propre disposition dynamique dans les classes que vous dérivez de `CControlBar`. Les classes MFC dérivées de `CControlBar`, telles que [CToolBar](../../mfc/reference/ctoolbar-class.md), remplacent cette fonction membre et fournissent leur propre implémentation.

##  <a name="calcfixedlayout"></a>CControlBar :: CalcFixedLayout

Appelez cette fonction membre pour calculer la taille horizontale d’une barre de contrôle.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*bStretch*<br/>
Indique si la barre doit être étirée à la taille du frame. Le paramètre *bStretch* est différent de zéro lorsque la barre n’est pas une barre d’ancrage (non disponible pour l’ancrage) et est égal à 0 lorsqu’il est ancré ou flottant (disponible pour l’ancrage).

*bHorz*<br/>
Indique que la barre est orientée horizontalement ou verticalement. Le paramètre *bHorz* est différent de zéro si la barre est orientée horizontalement et est égal à 0 s’il est orienté verticalement.

### <a name="return-value"></a>Valeur de retour

Taille de la barre de contrôle, en pixels, d’un objet `CSize`.

### <a name="remarks"></a>Notes

Les barres de contrôle telles que les barres d’outils peuvent être étirées horizontalement ou verticalement pour s’adapter aux boutons contenus dans la barre de contrôle.

Si *bStretch* a la valeur true, étire la dimension le long de l’orientation fournie par *bHorz*. En d’autres termes, si *bHorz* a la valeur false, la barre de contrôle est étirée verticalement. Si *bStretch* a la valeur false, aucun étirement ne se produit. Le tableau suivant indique les permutations possibles et les styles de barre de contrôle résultants de *bStretch* et *bHorz*.

|bStretch|bHorz|Étirement|Orientation|Ancrage/non-ancrage|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Étirement horizontal|Orienté horizontalement|Pas d’ancrage|
|TRUE|FALSE|Étirement vertical|Orienté verticalement|Pas d’ancrage|
|FALSE|TRUE|Aucun étirement disponible|Orienté horizontalement|Ancrage|
|FALSE|FALSE|Aucun étirement disponible|Orienté verticalement|Ancrage|

##  <a name="calcinsiderect"></a>CControlBar :: CalcInsideRect

L’infrastructure appelle cette fonction pour calculer la zone cliente de la barre de contrôle.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Contient les dimensions actuelles de la barre de contrôle ; y compris les bordures.

*bHorz*<br/>
Indique que la barre est orientée horizontalement ou verticalement. Le paramètre *bHorz* est différent de zéro si la barre est orientée horizontalement et est égal à 0 s’il est orienté verticalement.

### <a name="remarks"></a>Notes

Cette fonction est appelée avant que la barre de contrôle ne soit peinte.

Substituez cette fonction pour personnaliser le rendu des bordures et de la barre de redimensionnement de la barre de contrôle.

##  <a name="ccontrolbar"></a>CControlBar :: CControlBar

Construit un objet `CControlBar`.

```
CControlBar();
```

##  <a name="dopaint"></a>CControlBar ::D oPaint

Appelé par l’infrastructure pour restituer les bordures et la barre de redimensionnement de la barre de contrôle.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de périphérique à utiliser pour restituer les bordures et la pince de la barre de contrôle.

### <a name="remarks"></a>Notes

Substituez cette fonction pour personnaliser le comportement de dessin de la barre de contrôle.

Une autre méthode de personnalisation consiste à substituer les fonctions `DrawBorders` et `DrawGripper` et à ajouter du code de dessin personnalisé pour les bordures et les pinceaux. Étant donné que ces méthodes sont appelées par la méthode `DoPaint` par défaut, une substitution de `DoPaint` n’est pas nécessaire.

##  <a name="drawborders"></a>CControlBar ::D rawBorders

Appelé par l’infrastructure pour restituer les bordures de la barre de contrôle.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de périphérique à utiliser pour restituer les bordures de la barre de contrôle.

*rectangulaire*<br/>
Objet `CRect` contenant les dimensions de la barre de contrôle.

### <a name="remarks"></a>Notes

Substituez cette fonction pour personnaliser l’apparence des bordures de la barre de contrôle.

##  <a name="drawgripper"></a>CControlBar ::D rawGripper

Appelé par l’infrastructure pour restituer la pince de la barre de contrôle.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de périphérique à utiliser pour restituer le pince de barre de contrôle.

*rectangulaire*<br/>
Objet `CRect` contenant les dimensions du pince-barre de contrôle.

### <a name="remarks"></a>Notes

Substituez cette fonction pour personnaliser l’apparence du pince-barre de contrôle.

##  <a name="enabledocking"></a>CControlBar :: EnableDocking

Appelez cette fonction pour permettre à une barre de contrôle d’être ancrée.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Paramètres

*dwDockStyle*<br/>
Spécifie si la barre de contrôles prend en charge l’ancrage et les côtés de sa fenêtre parente dans laquelle la barre de contrôle peut être ancrée, si elle est prise en charge. Il peut s’agir d’un ou plusieurs des éléments suivants :

- CBRS_ALIGN_TOP permet l’ancrage en haut de la zone cliente.

- CBRS_ALIGN_BOTTOM permet l’ancrage en bas de la zone cliente.

- CBRS_ALIGN_LEFT autorise l’ancrage sur le côté gauche de la zone cliente.

- CBRS_ALIGN_RIGHT autorise l’ancrage sur le côté droit de la zone cliente.

- CBRS_ALIGN_ANY autorise l’ancrage de n’importe quel côté de la zone cliente.

- CBRS_FLOAT_MULTI permet de flotter plusieurs barres de contrôle dans une seule fenêtre mini-frame.

Si la valeur est 0 (c’est-à-dire qu’il n’indique aucun indicateur), la barre de contrôle n’est pas ancrée.

### <a name="remarks"></a>Notes

Les côtés spécifiés doivent correspondre à l’un des côtés activés pour l’ancrage dans la fenêtre frame de destination, ou la barre de contrôle ne peut pas être ancrée à cette fenêtre frame.

##  <a name="getbarstyle"></a>CControlBar :: GetBarStyle

Appelez cette fonction pour déterminer les paramètres de **CBRS_** (styles de barre de contrôle) actuellement définis pour la barre de contrôle.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Valeur de retour

Les paramètres de **CBRS_** (styles de barre de contrôle) actuels pour la barre de contrôle. Pour obtenir la liste complète des styles disponibles, consultez [CControlBar :: SetBarStyle](#setbarstyle) .

### <a name="remarks"></a>Notes

Ne gère pas les styles **WS_** (style de fenêtre).

##  <a name="getborders"></a>CControlBar :: GetBorders

Retourne les valeurs de bordure actuelles pour la barre de contrôle.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Valeur de retour

Objet `CRect` qui contient la largeur actuelle (en pixels) de chaque côté de l’objet de barre de contrôle. Par exemple, la valeur du membre de *gauche* , de l’objet [CRect](../../atl-mfc-shared/reference/crect-class.md) , est la largeur de la bordure gauche.

##  <a name="getcount"></a>CControlBar :: GetCount

Retourne le nombre d’éléments non HWND sur l’objet `CControlBar`.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments non HWND sur l’objet `CControlBar`. Cette fonction retourne 0 pour un objet [CDialogBar](../../mfc/reference/cdialogbar-class.md) .

### <a name="remarks"></a>Notes

Le type de l’élément dépend de l’objet dérivé : les volets pour les objets [CStatusBar](../../mfc/reference/cstatusbar-class.md) , les boutons et les séparateurs pour les objets [CToolBar](../../mfc/reference/ctoolbar-class.md) .

##  <a name="getdockingframe"></a>CControlBar :: GetDockingFrame

Appelez cette fonction membre pour obtenir un pointeur vers la fenêtre frame active à laquelle votre barre de contrôle est ancrée.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une fenêtre frame en cas de réussite ; Sinon, NULL.

Si la barre de contrôle n’est pas ancrée à une fenêtre frame (autrement dit, si la barre de contrôle est flottante), cette fonction retourne un pointeur vers son [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)parent.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les barres de contrôles ancrables, consultez [CControlBar :: EnableDocking](#enabledocking) et [CFrameWnd ::D ockcontrolbar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>CControlBar :: IsFloating

Appelez cette fonction membre pour déterminer si la barre de contrôle est flottante ou ancrée.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la barre de contrôle est flottante ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour modifier l’état d’une barre de contrôle ancrée à flottante, appelez [CFrameWnd :: FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>CControlBar :: m_bAutoDelete

Si la valeur est différente de zéro, l’objet `CControlBar` est supprimé lorsque la barre de contrôle Windows est détruite.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Notes

*m_bAutoDelete* est une variable publique de type bool.

Un objet de barre de contrôle est généralement incorporé dans un objet de fenêtre frame. Dans ce cas, *m_bAutoDelete* est égal à 0, car l’objet de barre de contrôle incorporé est détruit lorsque la fenêtre frame est détruite.

Affectez à cette variable une valeur différente de zéro si vous allouez un objet `CControlBar` sur le segment de mémoire et que vous n’envisagez pas d’appeler **Delete**.

##  <a name="m_pinplaceowner"></a>CControlBar :: m_pInPlaceOwner

Propriétaire sur place de la barre de contrôle.

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>CControlBar :: OnUpdateCmdUI

Cette fonction membre est appelée par l’infrastructure pour mettre à jour l’état de la barre d’outils ou de la barre d’État.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Pointe vers la fenêtre frame principale de l’application. Ce pointeur est utilisé pour router les messages de mise à jour.

*bDisableIfNoHndler*<br/>
Indicateur qui signale si un contrôle qui n’a pas de gestionnaire de mise à jour doit être automatiquement affiché comme étant désactivé.

### <a name="remarks"></a>Notes

Pour mettre à jour un bouton ou un volet individuel, utilisez la macro ON_UPDATE_COMMAND_UI dans votre table des messages pour définir un gestionnaire de mise à jour de manière appropriée. Pour plus d’informations sur l’utilisation de cette macro, consultez [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) .

`OnUpdateCmdUI` est appelée par le Framework lorsque l’application est inactive. La fenêtre frame à mettre à jour doit être une fenêtre enfant, au moins indirectement, d’une fenêtre frame visible. `OnUpdateCmdUI` est un substituable avancé.

##  <a name="setbarstyle"></a>CControlBar :: SetBarStyle

Appelez cette fonction pour définir les styles de **CBRS_** souhaités pour la barre de contrôle.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Styles souhaités pour la barre de contrôle. Il peut s’agir d’un ou plusieurs des éléments suivants :

- CBRS_ALIGN_TOP permet à la barre de contrôle d’être ancrée en haut de la zone cliente d’une fenêtre frame.

- CBRS_ALIGN_BOTTOM permet à la barre de contrôle d’être ancrée au bas de la zone cliente d’une fenêtre frame.

- CBRS_ALIGN_LEFT permet à la barre de contrôle d’être ancrée sur le côté gauche de la zone cliente d’une fenêtre frame.

- CBRS_ALIGN_RIGHT permet à la barre de contrôle d’être ancrée sur le côté droit de la zone cliente d’une fenêtre frame.

- CBRS_ALIGN_ANY permet à la barre de contrôle d’être ancrée à n’importe quel côté de la zone cliente d’une fenêtre frame.

- CBRS_BORDER_TOP provoque le dessin d’une bordure sur le bord supérieur de la barre de contrôle lorsqu’elle est visible.

- CBRS_BORDER_BOTTOM provoque le dessin d’une bordure sur le bord inférieur de la barre de contrôle lorsqu’elle est visible.

- CBRS_BORDER_LEFT provoque le dessin d’une bordure sur le bord gauche de la barre de contrôle lorsqu’elle est visible.

- CBRS_BORDER_RIGHT provoque le dessin d’une bordure sur le bord droit de la barre de contrôle lorsqu’elle est visible.

- CBRS_FLOAT_MULTI permet de flotter plusieurs barres de contrôle dans une seule fenêtre mini-frame.

- CBRS_TOOLTIPS provoque l’affichage des info-bulles pour la barre de contrôle.

- CBRS_FLYBY fait en sorte que le texte du message soit mis à jour en même temps que les info-bulles.

- CBRS_GRIPPER provoque un redimensionnement, semblable à celui utilisé sur les bandes dans un objet `CReBar`, à dessiner pour toute classe dérivée de `CControlBar`.

### <a name="remarks"></a>Notes

N’affecte pas les paramètres **WS_** (style de fenêtre).

##  <a name="setborders"></a>CControlBar :: SetBorders

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
Largeur (en pixels) de la bordure gauche de la barre de contrôle.

*cyTop*<br/>
Hauteur (en pixels) de la bordure supérieure de la barre de contrôle.

*cxRight*<br/>
Largeur (en pixels) de la bordure droite de la barre de contrôle.

*cyBottom*<br/>
Hauteur (en pixels) de la bordure inférieure de la barre de contrôle.

*lpRect*<br/>
Pointeur vers un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient la largeur actuelle (en pixels) de chaque bordure de l’objet de barre de contrôle.

### <a name="example"></a>Exemple

L’exemple de code suivant définit les bordures supérieure et inférieure de la barre de contrôle à 5 pixels, et les bordures gauche et droite sur 2 pixels :

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>CControlBar :: SetInPlaceOwner

Modifie le propriétaire sur place d’une barre de contrôle.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers un objet `CWnd`.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBar, classe](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar, classe](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar, classe](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar, classe](../../mfc/reference/crebar-class.md)
