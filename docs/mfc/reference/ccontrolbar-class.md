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
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773240"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

La classe de base pour les classes de barre de contrôle [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md), et [ COleResizeBar](../../mfc/reference/coleresizebar-class.md).

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
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Retourne la taille d’une barre de contrôle dynamique comme un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Retourne la taille de la barre de contrôle comme un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.|
|[CControlBar::CalcInsideRect](#calcinsiderect)|Retourne les dimensions de la zone de barre de contrôle ; y compris les bordures.|
|[CControlBar::DoPaint](#dopaint)|Restitue les bordures et la barre de redimensionnement de la barre de contrôle.|
|[CControlBar::DrawBorders](#drawborders)|Restitue les bordures de la barre de contrôle.|
|[CControlBar::DrawGripper](#drawgripper)|Affiche la barre de redimensionnement de la barre de contrôle.|
|[CControlBar::EnableDocking](#enabledocking)|Permet à une barre de contrôle doit être ancré ou flottant.|
|[CControlBar::GetBarStyle](#getbarstyle)|Récupère les paramètres de style de barre de contrôle.|
|[CControlBar::GetBorders](#getborders)|Récupère les valeurs de la bordure de la barre de contrôle.|
|[CControlBar::GetCount](#getcount)|Retourne le nombre d’éléments de non HWND dans la barre de contrôle.|
|[CControlBar::GetDockingFrame](#getdockingframe)|Retourne un pointeur vers le frame auquel une barre de contrôle est ancrée.|
|[CControlBar::IsFloating](#isfloating)|Retourne une valeur différente de zéro si la barre de contrôle en question est une barre de contrôle flottante.|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Appelle les gestionnaires d’interface utilisateur de commande.|
|[CControlBar::SetBarStyle](#setbarstyle)|Modifie les paramètres de style de barre de contrôle.|
|[CControlBar::SetBorders](#setborders)|Définit les valeurs de la bordure de la barre de contrôle.|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Modifie le propriétaire de la place d’une barre de contrôle.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Si elle est différente de zéro, le `CControlBar` objet est supprimé lorsque la barre de contrôle de Windows est détruite.|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Le propriétaire de la place de la barre de contrôle.|

## <a name="remarks"></a>Notes

Une barre de contrôle est une fenêtre qui est généralement alignée à gauche ou à droite d’une fenêtre frame. Il peut contenir des éléments enfants qui sont des contrôles basés sur HWND, qui sont des fenêtres qui génèrent et répondent aux messages de Windows, ou les éléments non basés sur HWND, qui ne sont pas des fenêtres et sont gérés par le code d’application ou le code du framework. Zones de liste et les contrôles d’édition sont des exemples de contrôles basés sur HWND ; volets de barre d’état et des boutons de bitmap sont des exemples de contrôles non basés sur HWND.

Windows de la barre de contrôle sont généralement les fenêtres enfants d’une fenêtre frame parente et sont généralement frères de la vue du client ou du client MDI de la fenêtre frame. Un `CControlBar` objet utilise les informations sur le rectangle de client de la fenêtre parente pour se positionner. Il informe ensuite la fenêtre parente quant à la quantité d’espace reste non alloué dans la zone cliente de la fenêtre parente.

Pour plus d’informations sur `CControlBar`, consultez :

- [Barres de contrôles](../../mfc/control-bars.md)

- [Note technique 31 : Barres de contrôles](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxext.h

##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout

L’infrastructure appelle cette fonction membre pour calculer les dimensions d’une barre d’outils dynamique.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Paramètres

*nLength*<br/>
La dimension demandée de la barre de contrôle, horizontale ou verticale, en fonction de *dwMode*.

*nMode*<br/>
Les indicateurs prédéfinis suivants sont utilisés pour déterminer la hauteur et la largeur de la barre de contrôle dynamique. Utilisez l’opération de bits OR (&#124;) opérateur pour combiner les indicateurs.

|Indicateurs de mode de disposition|Cela signifie que|
|-----------------------|-------------------|
|LM_STRETCH|Indique si la barre de contrôle doit être étirée pour la taille de l’image. Définir si la barre n’est pas une barre d’ancrage (non disponible pour l’ancrage). Pas définie si la barre est ancré ou flottant (disponible d’ancrage). Si la valeur, LM_STRETCH ignore *nLength* et retourne les dimensions basées sur l’état LM_HORZ. LM_STRETCH fonctionne de manière similaire à la *bStretch* paramètre utilisé dans [CalcFixedLayout](#calcfixedlayout); consultez cette fonction membre pour plus d’informations sur la relation entre l’étirement et l’orientation.|
|LM_HORZ|Indique que la barre est orientée horizontalement ou verticalement. Définit si la barre est orientée horizontalement, et s’il est orienté verticalement, elle n’est pas définie. LM_HORZ fonctionne de manière similaire à la *bHorz* paramètre utilisé dans [CalcFixedLayout](#calcfixedlayout); consultez cette fonction membre pour plus d’informations sur la relation entre l’étirement et l’orientation.|
|LM_MRUWIDTH|Utilisés le plus récemment largeur dynamique. Ignore *nLength* paramètre et utilise le mémorisés utilisés le plus récemment la largeur.|
|LM_HORZDOCK|Horizontal ancré Dimensions. Ignore *nLength* paramètre et retourne la taille dynamique avec la plus grande largeur.|
|LM_VERTDOCK|Vertical ancré Dimensions. Ignore *nLength* paramètre et retourne la taille dynamique avec la plus grande hauteur.|
|LM_LENGTHY|Définir si *nLength* indique la hauteur (axe Y) au lieu de la largeur.|
|LM_COMMIT|Réinitialise LM_MRUWIDTH à la largeur actuelle de la barre de contrôle flottante.|

### <a name="return-value"></a>Valeur de retour

La barre de contrôle de taille, en pixels, d’un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour fournir votre propre disposition dynamique dans les classes que vous dérivez de `CControlBar`. Les classes MFC dérivées de `CControlBar`, tel que [CToolbar](../../mfc/reference/ctoolbar-class.md), remplacez cette fonction membre et de fournir leur propre implémentation.

##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout

Appelez cette fonction membre pour calculer la taille horizontale d’une barre de contrôle.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*bStretch*<br/>
Indique si la barre doit être étirée pour la taille de l’image. Le *bStretch* paramètre est différent de zéro lorsque la barre n’est pas une barre d’ancrage (non disponible pour la station d’accueil) et 0 lorsqu’il est ancré ou flottant (disponible d’ancrage).

*bHorz*<br/>
Indique que la barre est orientée horizontalement ou verticalement. Le *bHorz* paramètre est différent de zéro si la barre est orientée horizontalement et 0 s’il est orienté verticalement.

### <a name="return-value"></a>Valeur de retour

La barre de contrôle de taille, en pixels, d’un `CSize` objet.

### <a name="remarks"></a>Notes

Barres de contrôles tels que des barres d’outils peuvent d’étendre horizontalement ou verticalement, pour prendre en compte les boutons contenues dans la barre de contrôle.

Si *bStretch* a la valeur TRUE, étirer la dimension le long de l’orientation, fournie par *bHorz*. En d’autres termes, si *bHorz* est FALSE, la barre de contrôle est étirée verticalement. Si *bStretch* est FALSE, aucun étirement se produit. Le tableau suivant présente les permutations possibles et les styles de barre de contrôle résultante, de *bStretch* et *bHorz*.

|bStretch|bHorz|Étirement|Orientation|Ancrage de la station d’accueil/non|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Étirement horizontal|Orienté horizontalement|Pas d’ancrage|
|TRUE|FALSE|Étirement vertical|Orienté verticalement|Pas d’ancrage|
|FALSE|TRUE|Aucun étirement disponibles|Orienté horizontalement|Ancrage|
|FALSE|FALSE|Aucun étirement disponibles|Orienté verticalement|Ancrage|

##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect

L’infrastructure appelle cette fonction pour calculer la zone cliente de la barre de contrôle.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
Contient les dimensions de la barre de contrôle. y compris les bordures.

*bHorz*<br/>
Indique que la barre est orientée horizontalement ou verticalement. Le *bHorz* paramètre est différent de zéro si la barre est orientée horizontalement et 0 s’il est orienté verticalement.

### <a name="remarks"></a>Notes

Cette fonction est appelée avant que la barre de contrôle est peint.

Remplacez cette fonction pour personnaliser le rendu de la bordure et la barre de redimensionnement de la barre de contrôle.

##  <a name="ccontrolbar"></a>  CControlBar::CControlBar

Construit un objet `CControlBar`.

```
CControlBar();
```

##  <a name="dopaint"></a>  CControlBar::DoPaint

Appelé par l’infrastructure pour afficher les bordures et la barre de redimensionnement de la barre de contrôle.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de périphérique à utiliser pour le rendu de la bordure et la barre de redimensionnement de la barre de contrôle.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser le comportement de dessin de la barre de contrôle.

Une autre méthode de personnalisation consiste à substituer la `DrawBorders` et `DrawGripper` fonctionne et ajouter du code de dessin personnalisé pour les bordures et la barre de redimensionnement. Étant donné que ces méthodes sont appelées par la valeur par défaut `DoPaint` (méthode), une substitution de `DoPaint` n’est pas nécessaire.

##  <a name="drawborders"></a>  CControlBar::DrawBorders

Appelé par l’infrastructure pour afficher les bordures de la barre de contrôle.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de périphérique à utiliser pour restituer les bordures de la barre de contrôle.

*rect*<br/>
Un `CRect` objet qui contient les dimensions de la barre de contrôle.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser l’apparence des bordures de barre de contrôle.

##  <a name="drawgripper"></a>  CControlBar::DrawGripper

Appelé par l’infrastructure pour afficher la barre de redimensionnement de la barre de contrôle.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de périphérique à utiliser pour le rendu de la barre de redimensionnement de barre de contrôle.

*rect*<br/>
Un `CRect` objet qui contient les dimensions de la barre de redimensionnement de barre de contrôle.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser l’apparence de la barre de redimensionnement de barre de contrôle.

##  <a name="enabledocking"></a>  CControlBar::EnableDocking

Appelez cette fonction pour activer une barre de contrôle d’être ancrée.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Paramètres

*dwDockStyle*<br/>
Spécifie si la barre de contrôle prend en charge d’ancrage et les côtés de sa fenêtre parente à laquelle la barre de contrôle peut être ancrée, si pris en charge. Peut être une ou plusieurs des opérations suivantes :

- CBRS_ALIGN_TOP permet d’ancrage en haut de la zone cliente.

- CBRS_ALIGN_BOTTOM permet d’ancrage en bas de la zone cliente.

- CBRS_ALIGN_LEFT permet d’ancrage sur le côté gauche de la zone cliente.

- CBRS_ALIGN_RIGHT permet d’ancrage sur le côté droit de la zone cliente.

- CBRS_ALIGN_ANY permet d’ancrage sur n’importe quel côté de la zone cliente.

- CBRS_FLOAT_MULTI permet plusieurs barres de contrôles à flotter dans une fenêtre mini-frame unique.

Si 0 (autrement dit, ce qui indique aucun indicateur), la barre de contrôle ne sera pas ancrer.

### <a name="remarks"></a>Notes

Les côtés spécifiées doivent correspondre à un des côtés activées pour l’ancrage dans la fenêtre frame de destination, ou la barre de contrôle ne peut pas être ancrée à cette fenêtre frame.

##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle

Appelez cette fonction pour déterminer quel **CBRS_** (styles de barre de contrôle) paramètres sont actuellement définis pour la barre de contrôle.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Valeur de retour

Actuel **CBRS_** (styles de barre de contrôle) des paramètres de la barre de contrôle. Consultez [fonctions CControlBar::SetBarStyle](#setbarstyle) pour la liste complète des styles disponibles.

### <a name="remarks"></a>Notes

Ne gère pas **WS_** (fenêtre) de style.

##  <a name="getborders"></a>  CControlBar::GetBorders

Retourne les valeurs actuelles de la bordure de la barre de contrôle.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CRect` objet qui contient la largeur actuelle (en pixels) de chaque côté de l’objet de barre de contrôle. Par exemple, la valeur de la *gauche* membre, de [CRect](../../atl-mfc-shared/reference/crect-class.md) d’objet, la largeur de la bordure gauche.

##  <a name="getcount"></a>  CControlBar::GetCount

Retourne le nombre d’éléments de non HWND sur le `CControlBar` objet.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments non HWND sur le `CControlBar` objet. Cette fonction retourne 0 pour un [CDialogBar](../../mfc/reference/cdialogbar-class.md) objet.

### <a name="remarks"></a>Notes

Le type de l’élément dépend de l’objet dérivé : volets pour [CStatusBar](../../mfc/reference/cstatusbar-class.md) objets et des boutons et des séparateurs pour [CToolBar](../../mfc/reference/ctoolbar-class.md) objets.

##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame

Appelez cette fonction membre pour obtenir un pointeur vers la fenêtre frame actuelle à laquelle votre barre de contrôle est ancré.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une fenêtre frame en cas de réussite ; Sinon, NULL.

Si la barre de contrôle n’est ancrée à une fenêtre frame (autrement dit, si la barre de contrôle est flottant), cette fonction retourne un pointeur à son parent [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Notes

Pour plus d’informations à propos des barres de contrôle, consultez [CControlBar::EnableDocking](#enabledocking) et [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>  CControlBar::IsFloating

Appelez cette fonction membre pour déterminer si la barre de contrôle est flottant ou ancré.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la barre de contrôle est flottante. sinon 0.

### <a name="remarks"></a>Notes

Pour modifier l’état d’une barre de contrôle à partir de devenue flottante, appelez [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete

Si elle est différente de zéro, le `CControlBar` objet est supprimé lorsque la barre de contrôle de Windows est détruite.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Notes

*m_bAutoDelete* est une variable publique de type BOOL.

Un objet de barre de contrôle est généralement incorporé dans un objet de fenêtre frame. Dans ce cas, *m_bAutoDelete* est 0, car l’objet de barre de contrôle incorporé est détruit quand la fenêtre frame est détruite.

Définissez cette variable sur une valeur différente de zéro si vous allouez un `CControlBar` objet sur le tas et vous ne prévoyez pas d’appeler **supprimer**.

##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner

Le propriétaire de la place de la barre de contrôle.

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI

Cette fonction membre est appelée par l’infrastructure pour mettre à jour l’état de la barre d’outils ou barre d’état.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
Pointe vers la fenêtre frame principale de l’application. Ce pointeur est utilisé pour router des messages de mise à jour.

*bDisableIfNoHndler*<br/>
Indicateur qui indique si un contrôle qui ne possède aucun gestionnaire de mise à jour doit être affiché automatiquement comme étant désactivé.

### <a name="remarks"></a>Notes

Pour mettre à jour d’un bouton individuel ou un volet, utilisez la macro ON_UPDATE_COMMAND_UI dans votre table des messages pour définir un gestionnaire de mise à jour en conséquence. Consultez [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) pour plus d’informations sur l’utilisation de cette macro.

`OnUpdateCmdUI` est appelé par l’infrastructure lorsque l’application est inactive. La fenêtre frame à mettre à jour doit être au moins indirectement, une fenêtre enfant, d’une fenêtre frame visible. `OnUpdateCmdUI` est une avancée substituable.

##  <a name="setbarstyle"></a>  CControlBar::SetBarStyle

Appelez cette fonction pour définir le texte souhaité **CBRS_** styles pour la barre de contrôle.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Les styles de votre choisis pour la barre de contrôle. Peut être une ou plusieurs des opérations suivantes :

- CBRS_ALIGN_TOP permet la barre de contrôle pour être ancré en haut de la zone cliente d’une fenêtre frame.

- CBRS_ALIGN_BOTTOM permet la barre de contrôle pour être ancré en bas de la zone cliente d’une fenêtre frame.

- CBRS_ALIGN_LEFT permet la barre de contrôle pour être ancré sur le côté gauche de la zone cliente d’une fenêtre frame.

- CBRS_ALIGN_RIGHT permet la barre de contrôle pour être ancré à droite de la zone cliente d’une fenêtre frame.

- CBRS_ALIGN_ANY permet la barre de contrôle pour être ancré à n’importe quel côté de la zone cliente d’une fenêtre frame.

- CBRS_BORDER_TOP provoque une bordure à dessiner sur le bord supérieur du contrôle de barre quand il est visible.

- CBRS_BORDER_BOTTOM provoque une bordure à dessiner sur le bord inférieur du contrôle barre quand il est visible.

- CBRS_BORDER_LEFT provoque une bordure à dessiner sur le bord gauche du contrôle de barre quand il est visible.

- CBRS_BORDER_RIGHT provoque une bordure à dessiner sur le bord droit du contrôle barre quand il est visible.

- CBRS_FLOAT_MULTI permet plusieurs barres de contrôles à flotter dans une fenêtre mini-frame unique.

- CBRS_TOOLTIPS provoque info-bulles à afficher pour la barre de contrôle.

- Texte du message CBRS_FLYBY provoque à mettre à jour en même temps en tant qu’info-bulles.

- CBRS_GRIPPER provoque une barre de redimensionnement, similaire à celle utilisée sur les bandes dans un `CReBar` dessin d’objet, pour toute `CControlBar`-classe dérivée.

### <a name="remarks"></a>Notes

N’affecte pas la **WS_** les paramètres (style de fenêtre).

##  <a name="setborders"></a>  CControlBar::SetBorders

Appelez cette fonction pour définir la taille des bordures de la barre contrôle.

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

*cyTop*<br/>
La hauteur (en pixels) de la bordure supérieure de la barre de contrôle.

*cxRight*<br/>
La largeur (en pixels) de la bordure droite de la barre de contrôle.

*cyBottom*<br/>
La hauteur (en pixels) de la bordure inférieure de la barre contrôle.

*lpRect*<br/>
Un pointeur vers un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui contient la largeur actuelle (en pixels) de chaque bordure de l’objet de barre de contrôle.

### <a name="example"></a>Exemple

L’exemple de code suivant définit les bordures supérieure et inférieure de la barre de contrôle pour 5 pixels et les bordures gauche et droit à 2 pixels :

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner

Modifie le propriétaire de la place d’une barre de contrôle.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers un objet `CWnd` .

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBar, classe](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar, classe](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar, classe](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar, classe](../../mfc/reference/crebar-class.md)
