---
title: CDragListBox, classe
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: 0d1ae94948e1143a5bac17985423c4bd1bfbaf65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374031"
---
# <a name="cdraglistbox-class"></a>CDragListBox, classe

En plus de fournir la fonctionnalité d’une boîte de liste Windows, la `CDragListBox` classe permet à l’utilisateur de déplacer des éléments de boîte de liste, tels que des noms de fichiers, dans la boîte de liste.

## <a name="syntax"></a>Syntaxe

```
class CDragListBox : public CListBox
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|Construit un objet `CDragListBox`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|Appelé par le cadre quand une opération de traînée commence.|
|[CDragListBox::CancelDrag](#canceldrag)|Appelé par le cadre quand une opération de traînée a été annulée.|
|[CDragListBox::Dragging](#dragging)|Appelé par le cadre lors d’une opération de traînée.|
|[CDragListBox::DrawInsert](#drawinsert)|Dessine le guide d’insertion de la boîte de liste de drag.|
|[CDragListBox::Dropped](#dropped)|Appelé par le cadre après que l’article a été abandonné.|
|[CDragListBox::ItemDePt](#itemfrompt)|Retourne les coordonnées de l’élément traîné.|

## <a name="remarks"></a>Notes

Liste des cases avec cette capacité permettent aux utilisateurs de commander les éléments dans une liste de quelque manière que ce soit est le plus utile pour eux. Par défaut, la boîte de liste déplacera l’élément vers le nouvel emplacement de la liste. Cependant, `CDragListBox` les objets peuvent être personnalisés pour copier des éléments au lieu de les déplacer.

Le contrôle de la `CDragListBox` boîte de liste associé à la classe ne doit pas avoir la LBS_SORT ou le style LBS_MULTIPLESELECT. Pour une description des styles de boîte de liste, voir [List-Box Styles](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Pour utiliser une boîte de liste de drag dans une boîte de dialogue existante de votre application, ajoutez un contrôle `Control` de `CDragListBox`boîte de liste à votre modèle de dialogue à l’aide de l’éditeur de dialogue, puis attribuez une variable de membre (de catégorie et de type variable ) correspondant au contrôle de la boîte de liste dans votre modèle de dialogue.

Pour plus d’informations sur l’attribution des contrôles aux variables des membres, voir [Shortcut pour définir les variables des membres pour les contrôles de dialogue](../../windows/defining-member-variables-for-dialog-controls.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a>CDragListBox::BeginDrag

Appelé par le cadre quand un événement se produit qui pourrait commencer une opération de traînée, comme appuyer sur le bouton de la souris gauche.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) qui contient les coordonnées de l’élément étant traîné.

### <a name="return-value"></a>Valeur de retour

Nonzero si le dragage est autorisé, sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction si vous voulez contrôler ce qui se passe lorsqu’une opération de traînée commence. L’implémentation par défaut capture la souris et reste en mode traîné jusqu’à ce que l’utilisateur clique sur le bouton de la souris gauche ou droite ou appuie ESC, date à laquelle l’opération de traînée est annulée.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a>CDragListBox::CancelDrag

Appelé par le cadre quand une opération de traînée a été annulée.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) qui contient les coordonnées de l’élément étant traîné.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour gérer tout traitement spécial pour votre contrôle de boîte de liste.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a>CDragListBox::CDragListBox

Construit un objet `CDragListBox`.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a>CDragListBox::Dragging

Appelé par le cadre quand un élément `CDragListBox` de boîte de liste est traîné dans l’objet.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) qui contient les coordonnées d’écran x et y du curseur.

### <a name="return-value"></a>Valeur de retour

L’ID de ressource du curseur à afficher. Les valeurs suivantes sont possibles :

- DL_COPYCURSOR indique que l’article sera copié.

- DL_MOVECURSOR indique que l’article sera déplacé.

- DL_STOPCURSOR indique que la cible de baisse actuelle n’est pas acceptable.

### <a name="remarks"></a>Notes

Le comportement par défaut renvoie DL_MOVECURSOR. Remplacez cette fonction si vous souhaitez fournir des fonctionnalités supplémentaires.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a>CDragListBox::DrawInsert

Appelé par le cadre pour dessiner le guide d’insertion avant l’élément avec l’index indiqué.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Indice zéro du point d’insertion.

### <a name="remarks"></a>Notes

Une valeur de - 1 efface le guide d’insertion. Remplacer cette fonction pour modifier l’apparence ou le comportement du guide d’insertion.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a>CDragListBox::Dropped

Appelé par le cadre quand un `CDragListBox` élément est abandonné dans un objet.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Paramètres

*nSrcIndex (en)*<br/>
Spécifie l’indice zéro de la chaîne abandonnée.

*Pt*<br/>
Un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) qui contient les coordonnées du site de largage.

### <a name="remarks"></a>Notes

Le comportement par défaut copie l’élément de la boîte de liste et ses données au nouvel emplacement, puis supprime l’élément d’origine. Remplacer cette fonction pour personnaliser le comportement par défaut, comme permettre de faire en sorte que des copies d’éléments de la boîte de liste soient traînés vers d’autres endroits de la liste.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a>CDragListBox::ItemDePt

Appelez cette fonction pour récupérer l’index zéro de l’élément de la boîte de liste situé à *pt*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Un objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) contenant les coordonnées d’un point dans la boîte de liste.

*bAutoScroll*<br/>
Nonzero si le défilement est autorisé, sinon 0.

### <a name="return-value"></a>Valeur de retour

Index basé à zéro de l’élément de la boîte de liste de drag.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)
