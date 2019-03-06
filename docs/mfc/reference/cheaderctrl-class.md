---
title: CHeaderCtrl (classe)
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
ms.openlocfilehash: 51cdfb481892ba5057d4ca26ff4d6e51665557e5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415615"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl (classe)

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
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Efface tous les filtres pour un contrôle header.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Efface le filtre pour un contrôle header.|
|[CHeaderCtrl::Create](#create)|Crée un contrôle header et l’attache à un `CHeaderCtrl` objet.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Crée une version transparente de l’image d’un élément au sein d’un contrôle header.|
|[CHeaderCtrl::CreateEx](#createex)|Crée un contrôle header avec les styles étendus Windows spécifiés et l’attache à un `CListCtrl` objet.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Supprime un élément d’un contrôle header.|
|[CHeaderCtrl::DrawItem](#drawitem)|Dessine l’élément spécifié d’un contrôle d’en-tête.|
|[CHeaderCtrl::EditFilter](#editfilter)|Commence à modifier le filtre spécifié d’un contrôle d’en-tête.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Récupère la largeur de la marge d’une image bitmap dans un contrôle header.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Obtient l’identificateur de l’élément dans le contrôle header actuel qui a le focus.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Récupère le handle d’une liste d’images utilisée pour les éléments d’en-tête dessin dans un contrôle header.|
|[CHeaderCtrl::GetItem](#getitem)|Récupère des informations sur un élément dans un contrôle header.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Récupère un nombre d’éléments dans un contrôle header.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Obtient les informations de rectangle englobant pour le bouton de liste déroulante spécifié dans un contrôle header.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Récupère le rectangle englobant pour un élément donné dans un contrôle header.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Récupère l’ordre de gauche à droite des éléments dans un contrôle header.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Obtient le rectangle englobant du bouton de dépassement de capacité pour le contrôle d’en-tête actuel.|
|[CHeaderCtrl::HitTest](#hittest)|Détermine quel élément d’en-tête, le cas échéant, se trouve à un point spécifié.|
|[CHeaderCtrl::InsertItem](#insertitem)|Insère un nouvel élément dans un contrôle header.|
|[CHeaderCtrl::Layout](#layout)|Récupère la taille et la position d’un contrôle d’en-tête dans un rectangle donné.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Récupère la valeur d’index pour un élément selon son ordre dans le contrôle header.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Définit la largeur de la marge d’une image bitmap dans un contrôle header.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Définit l’intervalle de délai d’attente entre l’heure une modification a lieu dans les attributs de filtre et de la validation d’une `HDN_FILTERCHANGE` notification.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Définit le focus à un élément d’en-tête spécifié dans le contrôle d’en-tête actuel.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Faites glisser le séparateur entre les éléments d’en-tête pour indiquer un manuel des modifications et supprimer d’un élément d’en-tête.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Affecte une liste d’images à un contrôle header.|
|[CHeaderCtrl::SetItem](#setitem)|Définit les attributs de l’élément spécifié dans un contrôle header.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Définit l’ordre de gauche à droite des éléments dans un contrôle header.|

## <a name="remarks"></a>Notes

Un contrôle header est une fenêtre qui est généralement positionnée au-dessus d’un ensemble de colonnes de texte ou des nombres. Il contient un titre pour chaque colonne, et il peut être divisé en parties. L’utilisateur peut faire glisser les séparateurs qui séparent les parties pour définir la largeur de chaque colonne. Pour obtenir une illustration d’un contrôle d’en-tête, consultez [contrôles Header](/windows/desktop/Controls/header-controls).

Ce contrôle (et par conséquent la `CHeaderCtrl` classe) est disponible uniquement pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT version 3.51 et ultérieures.

Fonctionnalités ont été ajoutées pour les contrôles communs Windows 95/Internet Explorer 4.0 incluent les éléments suivants :

- En-tête personnalisé classement des éléments.

- Élément d’en-tête le glisser- déposer, pour la réorganisation des éléments d’en-tête. Utiliser le style HDS_DRAGDROP lorsque vous créez le `CHeaderCtrl` objet.

- Texte de colonne en-tête constamment visible lors du redimensionnement de colonne. Utiliser le style HDS_FULLDRAG lorsque vous créez un `CHeaderCtrl` objet.

- En-tête réactive, qui met en surbrillance l’élément d’en-tête lorsque le pointeur passe sur celui-ci. Utilisez le style HDS_HOTTRACK lorsque vous créez le `CHeaderCtrl` objet.

- Prise en charge de la liste des images. Éléments d’en-tête peuvent contenir des images stockées dans un `CImageList` texte ou l’objet.

Pour plus d’informations sur l’utilisation de `CHeaderCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="cheaderctrl"></a>  CHeaderCtrl::CHeaderCtrl

Construit un objet `CHeaderCtrl`.

```
CHeaderCtrl();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>  CHeaderCtrl::ClearAllFilters

Efface tous les filtres pour un contrôle header.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement du message Win32 [HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter) avec une valeur de colonne,-1, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

Efface le filtre pour un contrôle header.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Paramètres

*nColumn*<br/>
Valeur de colonne indiquant le filtre à effacer.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement du message Win32 [HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>  CHeaderCtrl::Create

Crée un contrôle header et l’attache à un `CHeaderCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle d’en-tête. Pour obtenir une description de styles d’en-tête de contrôle, consultez [Styles d’en-tête de contrôle](/windows/desktop/Controls/header-control-styles) dans le SDK Windows.

*rect*<br/>
Spécifie la taille et la position du contrôle d’en-tête. Il peut s’agir un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure.

*pParentWnd*<br/>
Spécifie l’en-tête fenêtre du contrôle parent, généralement un `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID. du contrôle de l’en-tête

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’initialisation a abouti ; Sinon, zéro.

### <a name="remarks"></a>Notes

Vous construisez un `CHeaderCtrl` objet en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, ce qui crée le contrôle header et l’attache à la `CHeaderCtrl` objet.

Outre les styles de contrôle d’en-tête, vous pouvez utiliser les styles de contrôle courants suivants pour déterminer comment le contrôle header positionne et redimensionne (consultez [des Styles de contrôle courants](/windows/desktop/Controls/common-control-styles) pour plus d’informations) :

- CCS_BOTTOM, le contrôle se positionne au bas de la zone cliente de la fenêtre parente et la largeur pour être le même que le parent largeur de la fenêtre.

- CCS_NODIVIDER empêche un pixel de deux surbrillance dessiné en haut du contrôle.

- CCS_NOMOVEY, le contrôle redimensionner et déplacer lui-même horizontalement, mais pas verticalement, en réponse à un message WM_SIZE. Si le style CCS_NORESIZE est utilisé, ce style ne s’applique pas. Les contrôles header ont ce style par défaut.

- CCS_NOPARENTALIGN empêche le déplacement automatique vers le haut ou le bas de la fenêtre parent du contrôle. Au lieu de cela, le contrôle conserve sa position dans la fenêtre parente en dépit des modifications à la taille de la fenêtre parente. Si le style CCS_TOP ou CCS_BOTTOM est également utilisé, la hauteur est ajustée à la valeur par défaut, mais la position et la largeur restent inchangés.

- CCS_NORESIZE empêche le contrôle de l’aide de la largeur par défaut et la hauteur lors de la définition de sa taille initiale ou une nouvelle taille. Au lieu de cela, le contrôle utilise la largeur et la hauteur spécifiée dans la demande de création ou de dimensionnement.

- CCS_TOP, le contrôle se positionner en haut de la zone cliente de la fenêtre parente et la largeur pour être le même que le parent largeur de la fenêtre.

Vous pouvez également appliquer les styles de fenêtre suivant à un contrôle header (consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) pour plus d’informations) :

- WS_CHILD crée une fenêtre enfant. Ne peut pas être utilisé avec le style WS_POPUP.

- WS_VISIBLE crée une fenêtre est visible initialement.

- WS_DISABLED crée une fenêtre qui est initialement désactivée.

- WS_GROUP Spécifie le premier contrôle d’un groupe de contrôles dans lesquels l’utilisateur peut se déplacer d’un contrôle à l’autre avec les touches de direction. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le prochain contrôle avec le style WS_GROUP termine le groupe de styles et démarre le prochain groupe (autrement dit, un groupe se termine dans lequel la suivante ne commence).

- WS_TABSTOP spécifie un d’un nombre quelconque de contrôles par le biais duquel l’utilisateur peut se déplacer à l’aide de la touche TAB. La touche TAB déplace l’utilisateur sur le contrôle suivant spécifié par le style WS_TABSTOP.

Si vous souhaitez utiliser des styles étendus windows avec votre contrôle, appelez [CreateEx](#createex) au lieu de `Create`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>  CHeaderCtrl::CreateEx

Crée un contrôle (une fenêtre enfant), puis associez-la à la `CHeaderCtrl` objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le *dwExStyle* paramètre pour [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.

*dwStyle*<br/>
En-tête style du contrôle. Pour obtenir une description de styles d’en-tête de contrôle, consultez [Styles d’en-tête de contrôle](/windows/desktop/Controls/header-control-styles) dans le SDK Windows. Consultez [créer](#create) pour obtenir la liste des styles supplémentaires.

*rect*<br/>
Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure décrivant la taille et la position de la fenêtre doit être créée, dans les coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de fenêtre enfant. du contrôle

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de `Create` pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows **WS_EX_**.

##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage

Crée une version transparente de l’image d’un élément au sein d’un contrôle header.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro de l’élément dans le contrôle header. L’image attribuée à cet élément est la base de l’image transparente.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CImageList](../../mfc/reference/cimagelist-class.md) objet en cas de réussite ; sinon, NULL. La liste retournée contient uniquement une image.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [HDM_CREATEDRAGIMAGE](/windows/desktop/Controls/hdm-createdragimage), comme décrit dans le SDK Windows. Il est fourni pour prendre en charge d’en-tête élément glisser -déplacer.

Le `CImageList` objet auquel le pointeur retourné pointe est un objet temporaire et est supprimé dans le prochain traitement de la durée d’inactivité.

##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem

Supprime un élément d’un contrôle header.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Spécifie l’index de base zéro de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem

Appelé par le framework lorsqu’un aspect visuel d’une change de contrôle d’en-tête en mode owner-draw.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur vers un [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) structure qui décrit l’élément à peindre.

### <a name="remarks"></a>Notes

Le `itemAction` membre de la `DRAWITEMSTRUCT` structure définit l’action de dessin qui doit être effectuée.

Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre pour implémenter le dessin pour un mode owner-draw `CHeaderCtrl` objet.

L’application doit restaurer tous les objets interface (GDI) périphérique graphique sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant ce membre de fonction se termine.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter

Commence à modifier le filtre spécifié d’un contrôle d’en-tête.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Paramètres

*nColumn*<br/>
La colonne à modifier.

*bDiscardChanges*<br/>
Une valeur qui spécifie comment gérer l’utilisateur d’édition des modifications si l’utilisateur est en train de modifier le filtre lorsque le [HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter) message est envoyé.

Spécifiez TRUE pour ignorer les modifications apportées par l’utilisateur, ou FALSE pour accepter les modifications apportées par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement du message Win32 [HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin

Récupère la largeur de la marge d’une image bitmap dans un contrôle header.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la marge d’image bitmap en pixels.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [HDM_GETBITMAPMARGIN](/windows/desktop/Controls/hdm-getbitmapmargin), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem

Obtient l’index de l’élément qui a le focus dans le contrôle d’en-tête actuel.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément d’en-tête qui a le focus.

### <a name="remarks"></a>Notes

Cette méthode envoie le [HDM_GETFOCUSEDITEM](/windows/desktop/Controls/hdm-getfocuseditem) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisé pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant montre le `SetFocusedItem` et `GetFocusedItem` méthodes. Dans une section précédente du code, nous avons créé un contrôle header avec cinq colonnes. Toutefois, vous pouvez faire glisser un séparateur de colonne afin que la colonne n’est pas visible. L’exemple suivant définit, puis confirme le dernier en-tête de colonne en tant que l’élément le focus.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList

Récupère le handle d’une liste d’images utilisée pour les éléments d’en-tête dessin dans un contrôle header.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CImageList](../../mfc/reference/cimagelist-class.md) objet.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [HDM_GETIMAGELIST](/windows/desktop/Controls/hdm-getimagelist), comme décrit dans le SDK Windows. Le `CImageList` objet auquel le pointeur retourné pointe est un objet temporaire et est supprimé dans le prochain traitement de la durée d’inactivité.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>  CHeaderCtrl::GetItem

Récupère des informations sur un élément de contrôle d’en-tête.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Spécifie l’index de base zéro de l’élément à récupérer.

*pHeaderItem*<br/>
Pointeur vers un [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) structure qui reçoit le nouvel élément. Cette structure est utilisée avec la `InsertItem` et `SetItem` fonctions membres. Les indicateurs définis dans le `mask` élément vous assurer que les valeurs dans les éléments correspondants sont correctement renseignés au moment du retour. Si le `mask` élément est défini sur zéro, les valeurs dans les autres éléments de structure n’ont aucune signification.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount

Récupère un nombre d’éléments dans un contrôle header.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments de contrôle d’en-tête en cas de réussite ; Sinon, - 1.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CHeaderCtrl::DeleteItem](#deleteitem).

##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect

Obtient le rectangle englobant du bouton de liste déroulante pour un élément d’en-tête dans le contrôle d’en-tête actuel.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iItem*|[in] Index de base zéro d’un élément d’en-tête dont le style est HDF_SPLITBUTTON. Pour plus d’informations, consultez le `fmt` membre de la [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) structure.|
|*lpRect*|[out] Pointeur vers un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure qui doit recevoir les informations de rectangle englobant.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette fonction a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [HDM_GETITEMDROPDOWNRECT](/windows/desktop/Controls/hdm-getitemdropdownrect) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisé pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant montre le `GetItemDropDownRect` (méthode). Dans une section précédente du code, nous avons créé un contrôle header avec cinq colonnes. L’exemple de code suivant dessine un rectangle 3D autour de l’emplacement sur la première colonne est réservée pour le bouton d’en-tête de liste déroulante.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect

Récupère le rectangle englobant pour un élément donné dans un contrôle header.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro de l’élément de contrôle d’en-tête.

*lpRect*<br/>
Un pointeur vers l’adresse d’un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure qui reçoit les informations de rectangle englobant.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement du message Win32 [HDM_GETITEMRECT](/windows/desktop/Controls/hdm-getitemrect), comme décrit dans le SDK Windows.

##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray

Récupère l’ordre de gauche à droite des éléments dans un contrôle header.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Paramètres

*piArray*<br/>
Pointeur vers l’adresse d’une mémoire tampon qui reçoit les valeurs d’index des éléments dans le contrôle header, dans l’ordre dans lequel ils figurent, de gauche à droite.

*iCount*<br/>
Le nombre d’éléments de contrôle d’en-tête. Doit être non négatif.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [HDM_GETORDERARRAY](/windows/desktop/Controls/hdm-getorderarray), comme décrit dans le SDK Windows. Il est fourni pour prendre en charge le classement des éléments d’en-tête.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect

Obtient le rectangle englobant du bouton de dépassement de capacité du contrôle d’en-tête actuel.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpRect*|[out] Pointeur vers un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure qui reçoit les informations de rectangle englobant.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette fonction a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Si le contrôle header contient plus d’éléments peuvent être affichés simultanément, le contrôle peut afficher un bouton de dépassement de capacité qui fait défiler pour les éléments qui ne sont pas visibles. Le contrôle de l’en-tête doit avoir les styles HDS_OVERFLOW et HDF_SPLITBUTTON pour afficher le bouton de dépassement de capacité. Le rectangle englobant englobe le bouton de dépassement de capacité et existe uniquement lorsque le bouton de dépassement de capacité est affiché. Pour plus d’informations, consultez [Styles d’en-tête de contrôle](/windows/desktop/Controls/header-control-styles).

Cette méthode envoie le [HDM_GETOVERFLOWRECT](/windows/desktop/Controls/hdm-getoverflowrect) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisé pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant montre le `GetOverflowRect` (méthode). Dans une section précédente du code, nous avons créé un contrôle header avec cinq colonnes. Toutefois, vous pouvez faire glisser un séparateur de colonne afin que la colonne n’est pas visible. Si certaines colonnes ne sont pas visibles, le contrôle header Dessine un bouton de dépassement de capacité. L’exemple de code suivant dessine un rectangle 3D autour de l’emplacement du bouton de dépassement de capacité.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>  CHeaderCtrl::HitTest

Détermine quel élément d’en-tête, le cas échéant, se trouve à un point spécifié.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*phdhti*|[in, out] Pointeur vers un [HDHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_hd_hittestinfo) structure qui spécifie le point à tester et reçoit les résultats du test.|

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément d’en-tête, le cas échéant, la position spécifiée ; Sinon, -1.

### <a name="remarks"></a>Notes

Cette méthode envoie le [HDM_HITTEST](/windows/desktop/Controls/hdm-hittest) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisé pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant montre le `HitTest` (méthode). Dans la section précédente de cet exemple de code, nous avons créé un contrôle header avec cinq colonnes. Toutefois, vous pouvez faire glisser un séparateur de colonne afin que la colonne n’est pas visible. Cet exemple signale l’index de la colonne si elle est visible et -1 si la colonne n’est pas visible.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>  CHeaderCtrl::InsertItem

Insère un nouvel élément dans un contrôle d’en-tête à l’index spécifié.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Index de base zéro de l'élément à insérer. Si la valeur est zéro, l’élément est inséré au début du contrôle header. Si la valeur est supérieure à la valeur maximale, l’élément est inséré à la fin du contrôle header.

*phdi*<br/>
Pointeur vers un [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) structure qui contient des informations sur l’élément à insérer.

### <a name="return-value"></a>Valeur de retour

Index du nouvel élément en cas de réussite ; Sinon, - 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>  CHeaderCtrl::Layout

Récupère la taille et la position d’un contrôle d’en-tête dans un rectangle donné.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Paramètres

*pHeaderLayout*<br/>
Pointeur vers un [HDLAYOUT](/windows/desktop/api/commctrl/ns-commctrl-_hd_layout) structure qui contient les informations utilisées pour définir la taille et la position d’un contrôle d’en-tête.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour déterminer les dimensions appropriées pour un nouveau contrôle d’en-tête qui doit occuper le rectangle donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

Récupère la valeur d’index pour un élément selon son ordre dans le contrôle header.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Paramètres

*nOrder*<br/>
L’ordre de base zéro qui l’élément s’affiche dans le contrôle header, de gauche à droite.

### <a name="return-value"></a>Valeur de retour

Index de l’élément, en fonction de sa position dans le contrôle header. L’index de compte de gauche à droite, en commençant par 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la macro Win32 [HDM_ORDERTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb775355), comme décrit dans le SDK Windows. Il est fourni pour prendre en charge le classement des éléments d’en-tête.

##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin

Définit la largeur de la marge d’une image bitmap dans un contrôle header.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
Largeur, en pixels de la marge qui entoure une image bitmap dans un contrôle d’en-tête existant.

### <a name="return-value"></a>Valeur de retour

La largeur de la marge d’image bitmap en pixels.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [HDM_SETBITMAPMARGIN](/windows/desktop/Controls/hdm-setbitmapmargin), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout

Définit l’intervalle de délai d’attente entre l’heure une modification a lieu dans les attributs de filtre et de la validation d’une [HDN_FILTERCHANGE](/windows/desktop/Controls/hdn-filterchange) notification.

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Paramètres

*dwTimeOut*<br/>
Valeur de délai d’attente, en millisecondes.

### <a name="return-value"></a>Valeur de retour

L’index du contrôle de filtre en cours de modification.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [HDM_SETFILTERCHANGETIMEOUT](/windows/desktop/Controls/hdm-setfilterchangetimeout), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem

Définit le focus à un élément d’en-tête spécifié dans le contrôle d’en-tête actuel.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iItem*|[in] Index de base zéro d’un élément d’en-tête.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [HDM_SETFOCUSEDITEM](/windows/desktop/Controls/hdm-setfocuseditem) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisé pour accéder au contrôle d’en-tête actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant montre le `SetFocusedItem` et `GetFocusedItem` méthodes. Dans une section précédente du code, nous avons créé un contrôle header avec cinq colonnes. Toutefois, vous pouvez faire glisser un séparateur de colonne afin que la colonne n’est pas visible. L’exemple suivant définit, puis confirme le dernier en-tête de colonne en tant que l’élément le focus.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider

Faites glisser le séparateur entre les éléments d’en-tête pour indiquer un manuel des modifications et supprimer d’un élément d’en-tête.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
La position du pointeur. Le contrôle header met en surbrillance la ligne de séparation approprié en fonction de la position du pointeur.

*nIndex*<br/>
Index de la ligne de séparation en surbrillance.

### <a name="return-value"></a>Valeur de retour

Index de la ligne de séparation en surbrillance.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [HDM_SETHOTDIVIDER](/windows/desktop/Controls/hdm-sethotdivider), comme décrit dans le SDK Windows. Il est fourni pour prendre en charge d’en-tête élément glisser -déplacer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList

Affecte une liste d’images à un contrôle header.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList*<br/>
Un pointeur vers un `CImageList` objet contenant la liste d’images à assigner au contrôle header.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le [CImageList](../../mfc/reference/cimagelist-class.md) objet précédemment affecté au contrôle header.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [HDM_SETIMAGELIST](/windows/desktop/Controls/hdm-setimagelist), comme décrit dans le SDK Windows. Le `CImageList` objet auquel le pointeur retourné pointe est un objet temporaire et est supprimé dans le prochain traitement de la durée d’inactivité.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CHeaderCtrl::GetImageList](#getimagelist).

##  <a name="setitem"></a>  CHeaderCtrl::SetItem

Définit les attributs de l’élément spécifié dans un contrôle header.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Index de base zéro de l’élément à être manipulé.

*pHeaderItem*<br/>
Pointeur vers un [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) structure qui contient des informations sur le nouvel élément.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [appelant CHeaderCtrl::GetItem](#getitem).

##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray

Définit l’ordre de gauche à droite des éléments dans un contrôle header.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Paramètres

*iCount*<br/>
Le nombre d’éléments de contrôle d’en-tête.

*piArray*<br/>
Pointeur vers l’adresse d’une mémoire tampon qui reçoit les valeurs d’index des éléments dans le contrôle header, dans l’ordre dans lequel ils figurent, de gauche à droite.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la macro Win32 [HDM_SETORDERARRAY](/windows/desktop/Controls/hdm-setorderarray), comme décrit dans le SDK Windows. Il est fourni pour prendre en charge le classement des éléments d’en-tête.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CHeaderCtrl::GetOrderArray](#getorderarray).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl, classe](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList, classe](../../mfc/reference/cimagelist-class.md)
