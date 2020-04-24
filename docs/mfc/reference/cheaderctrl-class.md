---
title: Classe CHeaderCtrl
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: de1705d47c5692d3563bc7d9cb2646531819197a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750921"
---
# <a name="cheaderctrl-class"></a>Classe CHeaderCtrl

Fournit les fonctionnalités du contrôle commun d'en-tête Windows.

## <a name="syntax"></a>Syntaxe

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Construit un objet `CHeaderCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Efface tous les filtres pour un contrôle de l’en-tête.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Efface le filtre pour un contrôle de l’en-tête.|
|[CHeaderCtrl::Créer](#create)|Crée un contrôle d’en-tête et l’attache à un `CHeaderCtrl` objet.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Crée une version transparente de l’image d’un élément dans un contrôle d’en-tête.|
|[CHeaderCtrl::CreateEx](#createex)|Crée un contrôle d’en-tête avec les `CListCtrl` styles Windows étendus spécifiés et le fixe à un objet.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Supprime un élément d’un contrôle d’en-tête.|
|[CHeaderCtrl::DrawItem](#drawitem)|Dessine l’élément spécifié d’un contrôle d’en-tête.|
|[CHeaderCtrl::EditFilter](#editfilter)|Commence à modifier le filtre spécifié d’un contrôle d’en-tête.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Récupère la largeur de la marge d’une bitmap dans un contrôle d’en-tête.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Obtient l’identifiant de l’élément dans le contrôle d’en-tête actuel qui a la mise au point.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Récupère la poignée d’une liste d’images utilisée pour dessiner des éléments d’en-tête dans un contrôle d’en-tête.|
|[CHeaderCtrl::GetItem](#getitem)|Récupère des informations sur un élément dans un contrôle d’en-tête.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Récupère un compte des éléments dans un contrôle d’en-tête.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Obtient les informations de rectangle de délimitation pour le bouton de drop-down spécifié dans un contrôle d’en-tête.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Récupère le rectangle de délimitation pour un élément donné dans un contrôle d’en-tête.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Récupère l’ordre de gauche à droite des éléments dans un contrôle d’en-tête.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Obtient le rectangle de délimitation du bouton de débordement pour le contrôle actuel de la tête.|
|[CHeaderCtrl::HitTest](#hittest)|Détermine quel élément d’en-tête, le cas échéant, est situé à un point spécifié.|
|[CHeaderCtrl::InsertItem](#insertitem)|Insère un nouvel élément dans un contrôle d’en-tête.|
|[CHeaderCtrl::Layout](#layout)|Récupère la taille et la position d’un contrôle d’en-tête dans un rectangle donné.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Récupère la valeur de l’index pour un élément en fonction de sa commande dans le contrôle de l’en-tête.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Définit la largeur de la marge d’une bitmap dans un contrôle d’en-tête.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Définit l’intervalle de délai entre le moment où une modification `HDN_FILTERCHANGE` a lieu dans les attributs du filtre et l’affichage d’une notification.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Définit la mise au point vers un élément d’en-tête spécifié dans le contrôle d’en-tête actuel.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Modifie le diviseur entre les éléments d’en-tête pour indiquer une traînée manuelle et une chute d’un élément d’en-tête.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Assigne une liste d’images à un contrôle d’en-tête.|
|[CHeaderCtrl::SetItem](#setitem)|Définit les attributs de l’élément spécifié dans un contrôle d’en-tête.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Définit l’ordre de gauche à droite des éléments dans un contrôle d’en-tête.|

## <a name="remarks"></a>Notes

Un contrôle d’en-tête est une fenêtre qui est généralement positionnée au-dessus d’un ensemble de colonnes de texte ou de nombres. Il contient un titre pour chaque colonne, et il peut être divisé en parties. L’utilisateur peut faire glisser les diviseurs qui séparent les pièces pour définir la largeur de chaque colonne. Pour une illustration d’un contrôle d’en-tête, voir [contrôles d’en-tête](/windows/win32/Controls/header-controls).

Ce contrôle (et `CHeaderCtrl` donc la classe) n’est disponible que pour les programmes qui s’exécutent sous Windows 95/98 et Windows version NT 3.51 et plus tard.

La fonctionnalité ajoutée pour Windows 95/Internet Explorer 4.0 contrôles communs comprend ce qui suit:

- Commande personnalisée d’élément d’en-tête.

- En-tête de glisser et de laisser tomber, pour réorganiser les éléments d’en-tête. Utilisez le style HDS_DRAGDROP lorsque vous `CHeaderCtrl` créez l’objet.

- Texte de colonne d’en-tête constamment visible pendant la resizing de colonne. Utilisez le style HDS_FULLDRAG lorsque vous `CHeaderCtrl` créez un objet.

- Suivi en tête chaud, qui met en évidence l’élément d’en-tête lorsque le pointeur plane sur elle. Utilisez le style HDS_HOTTRACK lorsque vous `CHeaderCtrl` créez l’objet.

- Support de liste d’images. Les éléments d’en-tête peuvent contenir des images stockées dans un objet ou un `CImageList` texte.

Pour plus d’informations sur l’utilisation `CHeaderCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation de [CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a>CHeaderCtrl::CHeaderCtrl

Construit un objet `CHeaderCtrl`.

```
CHeaderCtrl();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a>CHeaderCtrl::ClearAllFilters

Efface tous les filtres pour un contrôle de l’en-tête.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement du message Win32 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) avec une valeur de colonne de -1, tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a>CHeaderCtrl::ClearFilter

Efface le filtre pour un contrôle de l’en-tête.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Paramètres

*nColumn (en)*<br/>
Valeur de colonne indiquant quel filtre effacer.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode met en œuvre le comportement du message Win32 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a>CHeaderCtrl::Créer

Crée un contrôle d’en-tête et l’attache à un `CHeaderCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du contrôle de l’en-tête. Pour une description des styles de contrôle de l’en-tête, voir Les styles de contrôle de [l’en-tête](/windows/win32/Controls/header-control-styles) dans le SDK Windows.

*Rect*<br/>
Spécifie la taille et la position du contrôle de l’en-tête. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Spécifie la fenêtre parente `CDialog`du contrôle de l’en-tête, généralement un . Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de l’en-tête.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation a été couronnée de succès; autrement zéro.

### <a name="remarks"></a>Notes

Vous construisez un `CHeaderCtrl` objet en deux étapes. Tout d’abord, appelez `Create`le constructeur, puis appelez , ce `CHeaderCtrl` qui crée le contrôle de l’en-tête et le fixe à l’objet.

En plus des styles de contrôle d’en-tête, vous pouvez utiliser les styles de contrôle communs suivants pour déterminer comment le contrôle de l’en-tête se positionne et se resize (voir [Styles de contrôle commun](/windows/win32/Controls/common-control-styles) pour plus d’informations):

- CCS_BOTTOM fait en partie le contrôle de se positionner au bas de la zone cliente de la fenêtre mère et définit la largeur pour être la même que la largeur de la fenêtre mère.

- CCS_NODIVIDER empêche un point culminant de deux pixels d’être dessiné en haut du contrôle.

- CCS_NOMOVEY provoque le contrôle de se resize et de se déplacer horizontalement, mais pas verticalement, en réponse à un message WM_SIZE. Si le style CCS_NORESIZE est utilisé, ce style ne s’applique pas. Les commandes d’en-tête ont ce style par défaut.

- CCS_NOPARENTALIGN empêche le contrôle de se déplacer automatiquement vers le haut ou le bas de la fenêtre parente. Au lieu de cela, le contrôle maintient sa position dans la fenêtre parente en dépit des changements à la taille de la fenêtre parente. Si le style CCS_TOP ou CCS_BOTTOM est également utilisé, la hauteur est ajustée à la valeur par défaut, mais la position et la largeur restent inchangées.

- CCS_NORESIZE empêche le contrôle d’utiliser la largeur et la hauteur par défaut lors de la définition de sa taille initiale ou d’une nouvelle taille. Au lieu de cela, le contrôle utilise la largeur et la hauteur spécifiées dans la demande de création ou de dimensionnement.

- CCS_TOP fait en partie le contrôle de se positionner au sommet de la zone cliente de la fenêtre mère et définit la largeur pour être la même que la largeur de la fenêtre mère.

Vous pouvez également appliquer les styles de fenêtre suivants à un contrôle d’en-tête (voir [Les styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) pour plus d’informations):

- WS_CHILD crée une fenêtre pour enfants. Impossible d’être utilisé avec le style WS_POPUP.

- WS_VISIBLE crée une fenêtre qui est initialement visible.

- WS_DISABLED crée une fenêtre qui est initialement désactivée.

- WS_GROUP précise le premier contrôle d’un groupe de contrôles dans lequel l’utilisateur peut passer d’un contrôle à l’autre avec les touches fléchées. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le prochain contrôle avec le style WS_GROUP se termine le groupe de style et commence le groupe suivant (c’est-à-dire, un groupe se termine là où le suivant commence).

- WS_TABSTOP précise l’un des nombreux contrôles par lesquels l’utilisateur peut se déplacer en utilisant la clé TAB. La clé TAB déplace l’utilisateur vers le contrôle suivant spécifié par le style WS_TABSTOP.

Si vous souhaitez utiliser des styles windows étendus `Create`avec votre contrôle, appelez [CreateEx](#createex) au lieu de .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a>CHeaderCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CHeaderCtrl` et l’associe à l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle (en anglais)*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour une liste de styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

*dwStyle (en)*<br/>
Le style du contrôle de l’en-tête. Pour une description des styles de contrôle de l’en-tête, voir Les styles de contrôle de [l’en-tête](/windows/win32/Controls/header-control-styles) dans le SDK Windows. Voir [Créer](#create) pour une liste de styles supplémentaires.

*Rect*<br/>
Une référence à une structure [RECT](/windows/win32/api/windef/ns-windef-rect) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au `Create` lieu d’appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a>CHeaderCtrl::CreateDragImage

Crée une version transparente de l’image d’un élément dans un contrôle d’en-tête.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index à base nulle de l’élément dans le contrôle de l’en-tête. L’image attribuée à cet élément est la base de l’image transparente.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) en cas de succès; autrement NULL. La liste retournée ne contient qu’une seule image.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage), tel que décrit dans le SDK Windows. Il est fourni pour soutenir la traînée et la baisse d’élément d’en-tête.

L’objet `CImageList` auquel les points de pointeur retournés est un objet temporaire et est supprimé dans le traitement suivant de temps d’inactivité.

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a>CHeaderCtrl::DeleteItem

Supprime un élément d’un contrôle d’en-tête.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Spécifie l’index zéro de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a>CHeaderCtrl::DrawItem

Appelé par le cadre quand un aspect visuel d’un contrôle d’en-tête propriétaire-tirage change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur d’une structure [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) décrivant l’élément à peindre.

### <a name="remarks"></a>Notes

Le `itemAction` membre `DRAWITEMSTRUCT` de la structure définit l’action de dessin qui doit être effectuée.

Par défaut, cette fonction de membre ne fait rien. Remplacer cette fonction de membre pour implémenter le dessin d’un objet de dessin du `CHeaderCtrl` propriétaire.

L’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction de membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a>CHeaderCtrl::EditFilter

Commence à modifier le filtre spécifié d’un contrôle d’en-tête.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Paramètres

*nColumn (en)*<br/>
La colonne à modifier.

*bDiscardChanges (en)*<br/>
Une valeur qui spécifie comment gérer les modifications d’édition de l’utilisateur si l’utilisateur est en train d’éditer le filtre lorsque le [message HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) est envoyé.

Spécifiez VRAI pour rejeter les modifications apportées par l’utilisateur, ou FALSE pour accepter les modifications apportées par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode met en œuvre le comportement du message Win32 [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a>CHeaderCtrl::GetBitmapMargin

Récupère la largeur de la marge d’une bitmap dans un contrôle d’en-tête.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la marge de la bitmap en pixels.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a>CHeaderCtrl::GetFocusedItem

Obtient l’index de l’élément qui a la mise au point dans le contrôle actuel de l’en-tête.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Valeur de retour

L’index à base zéro de l’élément d’en-tête qui a la mise au point.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message HDM_GETFOCUSEDITEM,](/windows/win32/Controls/hdm-getfocuseditem) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_headerCtrl`définit la variable, qui est utilisée pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code `SetFocusedItem` `GetFocusedItem` suivant montre les méthodes et les méthodes. Dans une section antérieure du code, nous avons créé un contrôle d’en-tête avec cinq colonnes. Cependant, vous pouvez faire glisser un séparateur de colonne de sorte que la colonne n’est pas visible. L’exemple suivant définit et confirme ensuite l’en-tête de dernière colonne comme élément de mise au point.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a>CHeaderCtrl::GetImageList

Récupère la poignée d’une liste d’images utilisée pour dessiner des éléments d’en-tête dans un contrôle d’en-tête.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CImageList.](../../mfc/reference/cimagelist-class.md)

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist), tel que décrit dans le SDK Windows. L’objet `CImageList` auquel les points de pointeur retournés est un objet temporaire et est supprimé dans le traitement suivant de temps d’inactivité.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a>CHeaderCtrl::GetItem

Récupère des informations sur un élément de contrôle de l’en-tête.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Spécifie l’index zéro de l’élément à récupérer.

*pHeaderItem*<br/>
Pointeur vers une structure [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) qui reçoit le nouvel article. Cette structure est `InsertItem` utilisée `SetItem` avec les fonctions et les fonctions des membres. Tous les drapeaux `mask` placés dans l’élément garantissent que les valeurs des éléments correspondants sont correctement remplies au retour. Si `mask` l’élément est réglé à zéro, les valeurs dans les autres éléments de structure n’ont aucun sens.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a>CHeaderCtrl::GetItemCount

Récupère un compte des éléments dans un contrôle d’en-tête.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments de contrôle d’en-tête en cas de succès; autrement - 1.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CHeaderCtrl::DeleteItem](#deleteitem).

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a>CHeaderCtrl::GetItemDropDownRect

Obtient le rectangle de délimitation du bouton de chute vers le bas pour un élément d’en-tête dans le contrôle actuel de la tête.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iItem*|[dans] Index à base zéro d’un élément d’en-tête dont le style est HDF_SPLITBUTTON. Pour plus d’informations, consultez le `fmt` membre de la structure [HDITEM.](/windows/win32/api/commctrl/ns-commctrl-hditemw)|
|*lpRect*|[out] Pointeur vers une structure [RECT](/windows/win32/api/windef/ns-windef-rect) pour recevoir les informations de rectangle de délimitation.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette fonction est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message HDM_GETITEMDROPDOWNRECT,](/windows/win32/Controls/hdm-getitemdropdownrect) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_headerCtrl`définit la variable, qui est utilisée pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code `GetItemDropDownRect` suivant montre la méthode. Dans une section antérieure du code, nous avons créé un contrôle d’en-tête avec cinq colonnes. L’exemple de code suivant dessine un rectangle 3D autour de l’emplacement sur la première colonne qui est réservée pour le bouton de drop-down de l’en-tête.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a>CHeaderCtrl::GetItemRect

Récupère le rectangle de délimitation pour un élément donné dans un contrôle d’en-tête.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index à base nulle de l’élément de contrôle de l’en-tête.

*lpRect*<br/>
Un pointeur à l’adresse d’une structure [RECT](/windows/win32/api/windef/ns-windef-rect) qui reçoit les informations de rectangle de délimitation.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode met en œuvre le comportement du message Win32 [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect), tel que décrit dans le SDK Windows.

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a>CHeaderCtrl::GetOrderArray

Récupère l’ordre de gauche à droite des éléments dans un contrôle d’en-tête.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Paramètres

*piArray piArray*<br/>
Un pointeur à l’adresse d’un tampon qui reçoit les valeurs indiciels des éléments dans le contrôle de l’en-tête, dans l’ordre dans lequel ils apparaissent de gauche à droite.

*iCompte*<br/>
Nombre d’éléments de contrôle de l’en-tête. Doit être non négatif.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray), tel que décrit dans le SDK Windows. Il est fourni pour prendre en charge la commande d’éléments d’en-tête.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a>CHeaderCtrl::GetOverflowRect

Obtient le rectangle de délimitation du bouton de débordement du contrôle actuel de la tête.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpRect*|[out] Pointeur vers une structure [RECT](/windows/win32/api/windef/ns-windef-rect) qui reçoit les informations de rectangle de délimitation.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette fonction est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Si le contrôle de l’en-tête contient plus d’éléments que ce qui peut être affiché simultanément, le contrôle peut afficher un bouton de débordement qui défile vers des éléments qui ne sont pas visibles. Le contrôle de l’en-tête doit avoir les styles HDS_OVERFLOW et HDF_SPLITBUTTON pour afficher le bouton de débordement. Le rectangle de délimitation entoure le bouton de débordement et n’existe que lorsque le bouton de débordement est affiché. Pour plus d’informations, voir [Header Control Styles](/windows/win32/Controls/header-control-styles).

Cette méthode envoie le [message HDM_GETOVERFLOWRECT,](/windows/win32/Controls/hdm-getoverflowrect) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_headerCtrl`définit la variable, qui est utilisée pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code `GetOverflowRect` suivant montre la méthode. Dans une section antérieure du code, nous avons créé un contrôle d’en-tête avec cinq colonnes. Cependant, vous pouvez faire glisser un séparateur de colonne de sorte que la colonne n’est pas visible. Si certaines colonnes ne sont pas visibles, le contrôle de l’en-tête tire un bouton de débordement. L’exemple de code suivant dessine un rectangle 3D autour de l’emplacement du bouton de débordement.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a>CHeaderCtrl::HitTest

Détermine quel élément d’en-tête, le cas échéant, est situé à un point spécifié.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*phdhti phdhti*|[dans, dehors] Pointeur vers une structure [HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) qui spécifie le point à tester et reçoit les résultats du test.|

### <a name="return-value"></a>Valeur de retour

L’index à base nulle de l’élément d’en-tête, le cas échéant, à la position spécifiée; sinon, -1.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message HDM_HITTEST,](/windows/win32/Controls/hdm-hittest) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_headerCtrl`définit la variable, qui est utilisée pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code `HitTest` suivant montre la méthode. Dans une section antérieure de cet exemple de code, nous avons créé un contrôle d’en-tête avec cinq colonnes. Cependant, vous pouvez faire glisser un séparateur de colonne de sorte que la colonne n’est pas visible. Cet exemple indique l’index de la colonne s’il est visible et -1 si la colonne n’est pas visible.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a>CHeaderCtrl::InsertItem

Insère un nouvel élément dans un contrôle d’en-tête à l’index spécifié.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Index de base zéro de l'élément à insérer. Si la valeur est nulle, l’élément est inséré au début du contrôle de l’en-tête. Si la valeur est supérieure à la valeur maximale, l’élément est inséré à l’extrémité du contrôle de l’en-tête.

*phdi phdi*<br/>
Pointeur vers une structure [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) qui contient des informations sur l’élément à insérer.

### <a name="return-value"></a>Valeur de retour

Index du nouvel élément en cas de succès; autrement - 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a>CHeaderCtrl::Layout

Récupère la taille et la position d’un contrôle d’en-tête dans un rectangle donné.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Paramètres

*pHeaderLayout (en)*<br/>
Pointeur vers une structure [HDLAYOUT,](/windows/win32/api/commctrl/ns-commctrl-hdlayout) qui contient des informations utilisées pour définir la taille et la position d’un contrôle d’en-tête.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour déterminer les dimensions appropriées pour un nouveau contrôle d’en-tête qui est d’occuper le rectangle donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a>CHeaderCtrl::OrderToIndex

Récupère la valeur de l’index pour un élément en fonction de sa commande dans le contrôle de l’en-tête.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Paramètres

*nOrder (en)*<br/>
L’ordre basé sur zéro que l’élément apparaît dans le contrôle de l’en-tête, de gauche à droite.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément, basé sur son ordre dans le contrôle de l’en-tête. L’indice compte de gauche à droite, à commencer par 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [macro HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)Win32 , tel que décrit dans le SDK Windows. Il est fourni pour prendre en charge la commande d’éléments d’en-tête.

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a>CHeaderCtrl::SetBitmapMargin

Définit la largeur de la marge d’une bitmap dans un contrôle d’en-tête.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Paramètres

*nWidth (en)*<br/>
Largeur, spécifiée en pixels, de la marge qui entoure une bitmap dans un contrôle d’en-tête existant.

### <a name="return-value"></a>Valeur de retour

La largeur de la marge de la bitmap en pixels.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a>CHeaderCtrl::SetFilterChangeTimeout

Définit l’intervalle de délai entre le moment où un changement a lieu dans les attributs du filtre et l’affichage d’une notification [HDN_FILTERCHANGE.](/windows/win32/Controls/hdn-filterchange)

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Paramètres

*dwTimeOut (en)*<br/>
Valeur de temps d’arrêt, en millisecondes.

### <a name="return-value"></a>Valeur de retour

L’index du contrôle du filtre en cours de modification.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a>CHeaderCtrl::SetFocusedItem

Définit la mise au point vers un élément d’en-tête spécifié dans le contrôle d’en-tête actuel.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iItem*|[dans] Indice à base zéro d’un élément d’en-tête.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message HDM_SETFOCUSEDITEM,](/windows/win32/Controls/hdm-setfocuseditem) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_headerCtrl`définit la variable, qui est utilisée pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code `SetFocusedItem` `GetFocusedItem` suivant montre les méthodes et les méthodes. Dans une section antérieure du code, nous avons créé un contrôle d’en-tête avec cinq colonnes. Cependant, vous pouvez faire glisser un séparateur de colonne de sorte que la colonne n’est pas visible. L’exemple suivant définit et confirme ensuite l’en-tête de dernière colonne comme élément de mise au point.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a>CHeaderCtrl::SetHotDivider

Modifie le diviseur entre les éléments d’en-tête pour indiquer une traînée manuelle et une chute d’un élément d’en-tête.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
La position du pointeur. Le contrôle de l’en-tête met en évidence le diviseur approprié en fonction de la position du pointeur.

*nIndex*<br/>
L’indice du diviseur mis en évidence.

### <a name="return-value"></a>Valeur de retour

L’indice du diviseur mis en évidence.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider), tel que décrit dans le SDK Windows. Il est fourni pour soutenir la traînée et la baisse d’élément d’en-tête.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a>CHeaderCtrl::SetImageList

Assigne une liste d’images à un contrôle d’en-tête.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList (en)*<br/>
Un pointeur `CImageList` vers un objet contenant la liste d’images à attribuer au contrôle de l’en-tête.

### <a name="return-value"></a>Valeur de retour

Un pointeur sur l’objet [CImageList](../../mfc/reference/cimagelist-class.md) précédemment assigné au contrôle de l’en-tête.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist), tel que décrit dans le SDK Windows. L’objet `CImageList` auquel les points de pointeur retournés est un objet temporaire et est supprimé dans le traitement suivant de temps d’inactivité.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CHeaderCtrl::GetImageList](#getimagelist).

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a>CHeaderCtrl::SetItem

Définit les attributs de l’élément spécifié dans un contrôle d’en-tête.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
L’index zéro de l’élément à manipuler.

*pHeaderItem*<br/>
Pointeur vers une structure [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) qui contient des informations sur le nouvel élément.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CHeaderCtrl::GetItem](#getitem).

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a>CHeaderCtrl::SetOrderArray

Définit l’ordre de gauche à droite des éléments dans un contrôle d’en-tête.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Paramètres

*iCompte*<br/>
Nombre d’éléments de contrôle de l’en-tête.

*piArray piArray*<br/>
Un pointeur à l’adresse d’un tampon qui reçoit les valeurs indiciels des éléments dans le contrôle de l’en-tête, dans l’ordre dans lequel ils apparaissent de gauche à droite.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la macro [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)Win32 , tel que décrit dans le SDK Windows. Il est fourni pour prendre en charge la commande d’éléments d’en-tête.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CHeaderCtrl::GetOrderArray](#getorderarray).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl, classe](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList, classe](../../mfc/reference/cimagelist-class.md)
