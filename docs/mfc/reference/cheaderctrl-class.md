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
ms.openlocfilehash: 62915da703e1c938e65643ab389999b83c72d459
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78871585"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl (classe)

Fournit les fonctionnalités du contrôle commun d'en-tête Windows.

## <a name="syntax"></a>Syntaxe

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CHeaderCtrl :: CHeaderCtrl](#cheaderctrl)|Construit un objet `CHeaderCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CHeaderCtrl :: ClearAllFilters](#clearallfilters)|Efface tous les filtres pour un contrôle header.|
|[CHeaderCtrl :: ClearFilter](#clearfilter)|Efface le filtre pour un contrôle header.|
|[CHeaderCtrl :: Create](#create)|Crée un contrôle header et l’attache à un objet `CHeaderCtrl`.|
|[CHeaderCtrl :: CreateDragImage](#createdragimage)|Crée une version transparente de l’image d’un élément dans un contrôle header.|
|[CHeaderCtrl :: CreateEx](#createex)|Crée un contrôle header avec les styles étendus Windows spécifiés et l’attache à un objet `CListCtrl`.|
|[CHeaderCtrl ::D eleteItem](#deleteitem)|Supprime un élément d’un contrôle header.|
|[CHeaderCtrl ::D rawItem](#drawitem)|Dessine l’élément spécifié d’un contrôle header.|
|[CHeaderCtrl :: EditFilter](#editfilter)|Commence à modifier le filtre spécifié d’un contrôle header.|
|[CHeaderCtrl :: GetBitmapMargin](#getbitmapmargin)|Récupère la largeur de la marge d’une image bitmap dans un contrôle header.|
|[CHeaderCtrl :: GetFocusedItem](#getfocuseditem)|Obtient l’identificateur de l’élément dans le contrôle header actuel qui a le focus.|
|[CHeaderCtrl :: GetImageList](#getimagelist)|Récupère le handle d’une liste d’images utilisée pour dessiner des éléments d’en-tête dans un contrôle header.|
|[CHeaderCtrl :: GetItem](#getitem)|Récupère des informations sur un élément dans un contrôle header.|
|[CHeaderCtrl :: GetItemCount](#getitemcount)|Récupère le nombre d’éléments dans un contrôle header.|
|[CHeaderCtrl :: GetItemDropDownRect](#getitemdropdownrect)|Obtient les informations de rectangle englobant pour le bouton déroulant spécifié dans un contrôle header.|
|[CHeaderCtrl :: GetItemRect](#getitemrect)|Récupère le rectangle englobant pour un élément donné dans un contrôle header.|
|[CHeaderCtrl :: GetOrderArray](#getorderarray)|Récupère l’ordre de gauche à droite des éléments dans un contrôle header.|
|[CHeaderCtrl :: GetOverflowRect](#getoverflowrect)|Obtient le rectangle englobant du bouton de dépassement de capacité pour le contrôle d’en-tête actuel.|
|[CHeaderCtrl :: HitTest](#hittest)|Détermine l’élément d’en-tête, le cas échéant, situé à un point spécifié.|
|[CHeaderCtrl :: InsertItem](#insertitem)|Insère un nouvel élément dans un contrôle header.|
|[CHeaderCtrl :: Layout](#layout)|Récupère la taille et la position d’un contrôle d’en-tête dans un rectangle donné.|
|[CHeaderCtrl :: OrderToIndex](#ordertoindex)|Récupère la valeur d’index d’un élément en fonction de son ordre dans le contrôle d’en-tête.|
|[CHeaderCtrl :: SetBitmapMargin](#setbitmapmargin)|Définit la largeur de la marge d’une image bitmap dans un contrôle header.|
|[CHeaderCtrl :: SetFilterChangeTimeout](#setfilterchangetimeout)|Définit l’intervalle de délai d’attente entre le moment où une modification est effectuée dans les attributs de filtre et la publication d’une notification de `HDN_FILTERCHANGE`.|
|[CHeaderCtrl :: SetFocusedItem](#setfocuseditem)|Définit le focus sur un élément d’en-tête spécifié dans le contrôle d’en-tête actuel.|
|[CHeaderCtrl :: SetHotDivider](#sethotdivider)|Modifie le séparateur entre les éléments d’en-tête pour indiquer un glisser-déplacer manuel d’un élément d’en-tête.|
|[CHeaderCtrl :: SetImageList](#setimagelist)|Assigne une liste d’images à un contrôle header.|
|[CHeaderCtrl :: SetItem](#setitem)|Définit les attributs de l’élément spécifié dans un contrôle header.|
|[CHeaderCtrl :: SetOrderArray](#setorderarray)|Définit l’ordre de gauche à droite des éléments dans un contrôle header.|

## <a name="remarks"></a>Notes

Un contrôle header est une fenêtre généralement placée au-dessus d’un ensemble de colonnes de texte ou de nombres. Elle contient un titre pour chaque colonne et peut être divisée en plusieurs parties. L’utilisateur peut faire glisser les séparateurs qui séparent les parties pour définir la largeur de chaque colonne. Pour obtenir une illustration d’un contrôle header, consultez [contrôles Header](/windows/win32/Controls/header-controls).

Ce contrôle (et par conséquent la classe `CHeaderCtrl`) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT version 3,51 et versions ultérieures.

La fonctionnalité ajoutée pour les contrôles communs Windows 95/Internet Explorer 4,0 comprend les éléments suivants :

- Classement personnalisé de l’élément d’en-tête.

- Glisser-déplacer des éléments d’en-tête pour réorganiser les éléments d’en-tête. Utilisez le style HDS_DRAGDROP lorsque vous créez l’objet `CHeaderCtrl`.

- Texte de colonne d’en-tête visible en permanence pendant le redimensionnement de colonne. Utilisez le style HDS_FULLDRAG lorsque vous créez un objet `CHeaderCtrl`.

- Suivi réactif d’en-tête, qui met en surbrillance l’élément d’en-tête lorsque le pointeur pointe dessus. Utilisez le style HDS_HOTTRACK lorsque vous créez l’objet `CHeaderCtrl`.

- Prise en charge de la liste d’images. Les éléments d’en-tête peuvent contenir des images stockées dans un objet `CImageList` ou du texte.

Pour plus d’informations sur l’utilisation de `CHeaderCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="cheaderctrl"></a>CHeaderCtrl :: CHeaderCtrl

Construit un objet `CHeaderCtrl`.

```
CHeaderCtrl();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>CHeaderCtrl :: ClearAllFilters

Efface tous les filtres pour un contrôle header.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement de la [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) de message Win32 avec une valeur de colonne de-1, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>CHeaderCtrl :: ClearFilter

Efface le filtre pour un contrôle header.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Paramètres

*nColumn*<br/>
Valeur de colonne indiquant le filtre à effacer.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement de la [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>CHeaderCtrl :: Create

Crée un contrôle header et l’attache à un objet `CHeaderCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle d’en-tête. Pour obtenir une description des styles de contrôle d’en-tête, consultez [styles de contrôle d’en-tête](/windows/win32/Controls/header-control-styles) dans le SDK Windows.

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle d’en-tête. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle d’en-tête, généralement un `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle d’en-tête.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’initialisation a réussi ; Sinon, zéro.

### <a name="remarks"></a>Notes

Vous construisez un objet `CHeaderCtrl` en deux étapes. Tout d’abord, appelez le constructeur, puis appelez `Create`, qui crée le contrôle header et l’attache à l’objet `CHeaderCtrl`.

Outre les styles de contrôle d’en-tête, vous pouvez utiliser les styles de contrôle communs suivants pour déterminer comment le contrôle d’en-tête se positionne et se redimensionne lui-même (voir les [styles de contrôle courants](/windows/win32/Controls/common-control-styles) pour plus d’informations) :

- CCS_BOTTOM force le contrôle à se positionner en bas de la zone cliente de la fenêtre parente et définit la largeur de manière à ce qu’elle soit identique à la largeur de la fenêtre parente.

- CCS_NODIVIDER empêche le dessin d’une surbrillance à deux pixels en haut du contrôle.

- CCS_NOMOVEY fait en sorte que le contrôle se redimensionne et se déplace horizontalement, mais pas verticalement, en réponse à un message WM_SIZE. Si le style de CCS_NORESIZE est utilisé, ce style ne s’applique pas. Par défaut, les contrôles Header ont ce style.

- CCS_NOPARENTALIGN empêche le contrôle de se déplacer automatiquement en haut ou en bas de la fenêtre parente. Au lieu de cela, le contrôle conserve sa position dans la fenêtre parente malgré les modifications apportées à la taille de la fenêtre parente. Si le style de CCS_TOP ou de CCS_BOTTOM est également utilisé, la hauteur est ajustée à la valeur par défaut, mais la position et la largeur restent inchangées.

- CCS_NORESIZE empêche le contrôle d’utiliser la largeur et la hauteur par défaut lors de la définition de sa taille initiale ou d’une nouvelle taille. Au lieu de cela, le contrôle utilise la largeur et la hauteur spécifiées dans la demande de création ou de dimensionnement.

- CCS_TOP force le contrôle à se positionner en haut de la zone cliente de la fenêtre parente et définit la largeur de manière à ce qu’elle soit identique à la largeur de la fenêtre parente.

Vous pouvez également appliquer les styles de fenêtre suivants à un contrôle header (consultez [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) pour plus d’informations) :

- WS_CHILD crée une fenêtre enfant. Ne peut pas être utilisé avec le style WS_POPUP.

- WS_VISIBLE crée une fenêtre qui est initialement visible.

- WS_DISABLED crée une fenêtre qui est initialement désactivée.

- WS_GROUP spécifie le premier contrôle d’un groupe de contrôles dans lequel l’utilisateur peut passer d’un contrôle à l’autre à l’aide des touches de direction. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le contrôle suivant avec le style de WS_GROUP met fin au groupe de styles et démarre le groupe suivant (autrement dit, un groupe se termine à l’emplacement où commence le prochain).

- WS_TABSTOP spécifie un nombre quelconque de contrôles par le biais desquels l’utilisateur peut se déplacer à l’aide de la touche TAB. La touche TAB déplace l’utilisateur vers le contrôle suivant spécifié par le style de WS_TABSTOP.

Si vous souhaitez utiliser des styles Windows étendus avec votre contrôle, appelez [CreateEx](#createex) au lieu de `Create`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>CHeaderCtrl :: CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à l’objet `CHeaderCtrl`.

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
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*dwStyle*<br/>
Style du contrôle d’en-tête. Pour obtenir une description des styles de contrôle d’en-tête, consultez [styles de contrôle d’en-tête](/windows/win32/Controls/header-control-styles) dans le SDK Windows. Pour obtenir la liste des styles supplémentaires, consultez [créer](#create) .

*rectangulaire*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de `Create` pour appliquer des styles Windows étendus, spécifiés par la préversion de style étendu Windows **WS_EX_** .

##  <a name="createdragimage"></a>CHeaderCtrl :: CreateDragImage

Crée une version transparente de l’image d’un élément dans un contrôle header.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro de l’élément dans le contrôle header. L’image assignée à cet élément est la base de l’image transparente.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) en cas de réussite ; Sinon, NULL. La liste retournée contient une seule image.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)de message Win32, comme décrit dans le SDK Windows. Elle est fournie pour prendre en charge le glisser-déplacer des éléments d’en-tête.

`CImageList` objet vers lequel pointe le pointeur retourné est un objet temporaire et est supprimé dans le traitement suivant de l’heure d’inactivité.

##  <a name="deleteitem"></a>CHeaderCtrl ::D eleteItem

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

##  <a name="drawitem"></a>CHeaderCtrl ::D rawItem

Appelée par l’infrastructure quand un aspect visuel d’un contrôle header-Draw est modifié.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) décrivant l’élément à peindre.

### <a name="remarks"></a>Notes

Le membre `itemAction` de la structure `DRAWITEMSTRUCT` définit l’action de dessin à effectuer.

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre pour implémenter le dessin pour un objet `CHeaderCtrl` owner-draw.

L’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>CHeaderCtrl :: EditFilter

Commence à modifier le filtre spécifié d’un contrôle header.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Paramètres

*nColumn*<br/>
Colonne à modifier.

*bDiscardChanges*<br/>
Valeur qui spécifie comment gérer les modifications de modification de l’utilisateur si l’utilisateur est en train de modifier le filtre lorsque le message d' [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) est envoyé.

Spécifiez TRUE pour ignorer les modifications apportées par l’utilisateur ou FALSe pour accepter les modifications apportées par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement de la [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>CHeaderCtrl :: GetBitmapMargin

Récupère la largeur de la marge d’une image bitmap dans un contrôle header.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur de la marge de la bitmap en pixels.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>CHeaderCtrl :: GetFocusedItem

Obtient l’index de l’élément qui a le focus dans le contrôle d’en-tête actuel.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément d’en-tête qui a le focus.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisée pour accéder au contrôle header actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant illustre les méthodes `SetFocusedItem` et `GetFocusedItem`. Dans une section précédente du code, nous avons créé un contrôle header avec cinq colonnes. Toutefois, vous pouvez faire glisser un séparateur de colonne pour que la colonne ne soit pas visible. L’exemple suivant définit puis confirme le dernier en-tête de colonne comme élément de focus.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>CHeaderCtrl :: GetImageList

Récupère le handle d’une liste d’images utilisée pour dessiner des éléments d’en-tête dans un contrôle header.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)de message Win32, comme décrit dans le SDK Windows. `CImageList` objet vers lequel pointe le pointeur retourné est un objet temporaire et est supprimé dans le traitement suivant de l’heure d’inactivité.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>CHeaderCtrl :: GetItem

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
Pointeur vers une structure [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) qui reçoit le nouvel élément. Cette structure est utilisée avec les fonctions membres `InsertItem` et `SetItem`. Tous les indicateurs définis dans l’élément `mask` garantissent que les valeurs des éléments correspondants sont correctement remplies lors du retour. Si l’élément `mask` a la valeur zéro, les valeurs des autres éléments de structure sont sans signification.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>CHeaderCtrl :: GetItemCount

Récupère le nombre d’éléments dans un contrôle header.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments de contrôle d’en-tête en cas de réussite ; sinon-1.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CHeaderCtrl ::D eleteitem](#deleteitem).

##  <a name="getitemdropdownrect"></a>CHeaderCtrl :: GetItemDropDownRect

Obtient le rectangle englobant du bouton déroulant pour un élément d’en-tête dans le contrôle d’en-tête actuel.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iItem*|dans Index de base zéro d’un élément d’en-tête dont le style est HDF_SPLITBUTTON. Pour plus d’informations, consultez le membre `fmt` de la structure [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) .|
|*lpRect*|à Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) pour recevoir les informations de rectangle englobant.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette fonction est réussie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisée pour accéder au contrôle header actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant illustre la méthode `GetItemDropDownRect`. Dans une section précédente du code, nous avons créé un contrôle header avec cinq colonnes. L’exemple de code suivant dessine un rectangle 3D autour de l’emplacement sur la première colonne réservée pour le bouton déroulant d’en-tête.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>CHeaderCtrl :: GetItemRect

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
Pointeur vers l’adresse d’une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui reçoit les informations de rectangle englobant.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode implémente le comportement de la [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)de message Win32, comme décrit dans le SDK Windows.

##  <a name="getorderarray"></a>CHeaderCtrl :: GetOrderArray

Récupère l’ordre de gauche à droite des éléments dans un contrôle header.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Paramètres

*piArray*<br/>
Pointeur vers l’adresse d’une mémoire tampon qui reçoit les valeurs d’index des éléments du contrôle d’en-tête, dans l’ordre dans lequel ils apparaissent de gauche à droite.

*iCount*<br/>
Nombre d’éléments de contrôle d’en-tête. Ne doit pas être négatif.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)de message Win32, comme décrit dans le SDK Windows. Elle est fournie pour prendre en charge le classement des éléments d’en-tête.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>CHeaderCtrl :: GetOverflowRect

Obtient le rectangle englobant du bouton de dépassement de capacité du contrôle d’en-tête actuel.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpRect*|à Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui reçoit les informations de rectangle englobant.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette fonction est réussie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si le contrôle header contient plus d’éléments que ce qui peut être affiché simultanément, le contrôle peut afficher un bouton de dépassement de capacité qui fait défiler les éléments qui ne sont pas visibles. Le contrôle header doit avoir les styles HDS_OVERFLOW et HDF_SPLITBUTTON pour afficher le bouton de dépassement de capacité. Le rectangle englobant englobe le bouton de dépassement de capacité et existe uniquement lorsque le bouton de dépassement de capacité est affiché. Pour plus d’informations, consultez [styles de contrôle d’en-tête](/windows/win32/Controls/header-control-styles).

Cette méthode envoie le message [HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisée pour accéder au contrôle header actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant illustre la méthode `GetOverflowRect`. Dans une section précédente du code, nous avons créé un contrôle header avec cinq colonnes. Toutefois, vous pouvez faire glisser un séparateur de colonne pour que la colonne ne soit pas visible. Si certaines colonnes ne sont pas visibles, le contrôle d’en-tête dessine un bouton de dépassement de capacité. L’exemple de code suivant dessine un rectangle 3D autour de l’emplacement du bouton de dépassement de capacité.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>CHeaderCtrl :: HitTest

Détermine l’élément d’en-tête, le cas échéant, situé à un point spécifié.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*phdhti*|[in, out] Pointeur vers une structure [HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) qui spécifie le point à tester et reçoit les résultats du test.|

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément d’en-tête, le cas échéant, à la position spécifiée ; Sinon,-1.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [HDM_HITTEST](/windows/win32/Controls/hdm-hittest) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisée pour accéder au contrôle header actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant illustre la méthode `HitTest`. Dans une section précédente de cet exemple de code, nous avons créé un contrôle header avec cinq colonnes. Toutefois, vous pouvez faire glisser un séparateur de colonne pour que la colonne ne soit pas visible. Cet exemple signale l’index de la colonne s’il est visible et-1 si la colonne n’est pas visible.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>CHeaderCtrl :: InsertItem

Insère un nouvel élément dans un contrôle header au niveau de l’index spécifié.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Index de base zéro de l'élément à insérer. Si la valeur est égale à zéro, l’élément est inséré au début du contrôle d’en-tête. Si la valeur est supérieure à la valeur maximale, l’élément est inséré à la fin du contrôle d’en-tête.

*phdi*<br/>
Pointeur vers une structure [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) qui contient des informations sur l’élément à insérer.

### <a name="return-value"></a>Valeur de retour

Index du nouvel élément en cas de réussite ; sinon-1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>CHeaderCtrl :: Layout

Récupère la taille et la position d’un contrôle d’en-tête dans un rectangle donné.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Paramètres

*pHeaderLayout*<br/>
Pointeur vers une structure [HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout) , qui contient des informations utilisées pour définir la taille et la position d’un contrôle header.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour déterminer les dimensions appropriées pour un nouveau contrôle d’en-tête qui doit occuper le rectangle donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>CHeaderCtrl :: OrderToIndex

Récupère la valeur d’index d’un élément en fonction de son ordre dans le contrôle d’en-tête.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Paramètres

*nOrder*<br/>
Ordre de base zéro dans lequel l’élément apparaît dans le contrôle header, de gauche à droite.

### <a name="return-value"></a>Valeur de retour

Index de l’élément, en fonction de son ordre dans le contrôle d’en-tête. L’index est compté de gauche à droite, en commençant par 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la macro Win32 [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex), comme décrit dans le SDK Windows. Elle est fournie pour prendre en charge le classement des éléments d’en-tête.

##  <a name="setbitmapmargin"></a>CHeaderCtrl :: SetBitmapMargin

Définit la largeur de la marge d’une image bitmap dans un contrôle header.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
Largeur, spécifiée en pixels, de la marge qui entoure une bitmap dans un contrôle d’en-tête existant.

### <a name="return-value"></a>Valeur de retour

Largeur de la marge de la bitmap en pixels.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>CHeaderCtrl :: SetFilterChangeTimeout

Définit l’intervalle de délai d’attente entre le moment où une modification est effectuée dans les attributs de filtre et la publication d’une notification de [HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange) .

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Paramètres

*dwTimeOut*<br/>
Valeur du délai d’attente, en millisecondes.

### <a name="return-value"></a>Valeur de retour

Index du contrôle de filtre en cours de modification.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>CHeaderCtrl :: SetFocusedItem

Définit le focus sur un élément d’en-tête spécifié dans le contrôle d’en-tête actuel.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iItem*|dans Index de base zéro d’un élément d’en-tête.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_headerCtrl`, qui est utilisée pour accéder au contrôle header actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant illustre les méthodes `SetFocusedItem` et `GetFocusedItem`. Dans une section précédente du code, nous avons créé un contrôle header avec cinq colonnes. Toutefois, vous pouvez faire glisser un séparateur de colonne pour que la colonne ne soit pas visible. L’exemple suivant définit puis confirme le dernier en-tête de colonne comme élément de focus.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>CHeaderCtrl :: SetHotDivider

Modifie le séparateur entre les éléments d’en-tête pour indiquer un glisser-déplacer manuel d’un élément d’en-tête.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Position du pointeur. Le contrôle header met en surbrillance le séparateur approprié en fonction de la position du pointeur.

*nIndex*<br/>
Index du séparateur en surbrillance.

### <a name="return-value"></a>Valeur de retour

Index du séparateur en surbrillance.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider)de message Win32, comme décrit dans le SDK Windows. Elle est fournie pour prendre en charge le glisser-déplacer des éléments d’en-tête.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>CHeaderCtrl :: SetImageList

Assigne une liste d’images à un contrôle header.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList*<br/>
Pointeur vers un objet `CImageList` contenant la liste d’images à assigner au contrôle header.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet [CImageList](../../mfc/reference/cimagelist-class.md) précédemment assigné au contrôle header.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)de message Win32, comme décrit dans le SDK Windows. `CImageList` objet vers lequel pointe le pointeur retourné est un objet temporaire et est supprimé dans le traitement suivant de l’heure d’inactivité.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CHeaderCtrl :: GetImageList](#getimagelist).

##  <a name="setitem"></a>CHeaderCtrl :: SetItem

Définit les attributs de l’élément spécifié dans un contrôle header.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Index de base zéro de l’élément à manipuler.

*pHeaderItem*<br/>
Pointeur vers une structure [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) qui contient des informations sur le nouvel élément.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CHeaderCtrl :: GetItem](#getitem).

##  <a name="setorderarray"></a>CHeaderCtrl :: SetOrderArray

Définit l’ordre de gauche à droite des éléments dans un contrôle header.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Paramètres

*iCount*<br/>
Nombre d’éléments de contrôle d’en-tête.

*piArray*<br/>
Pointeur vers l’adresse d’une mémoire tampon qui reçoit les valeurs d’index des éléments du contrôle d’en-tête, dans l’ordre dans lequel ils apparaissent de gauche à droite.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la macro Win32 [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray), comme décrit dans le SDK Windows. Elle est fournie pour prendre en charge le classement des éléments d’en-tête.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CHeaderCtrl :: GetOrderArray](#getorderarray).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl, classe](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList, classe](../../mfc/reference/cimagelist-class.md)
