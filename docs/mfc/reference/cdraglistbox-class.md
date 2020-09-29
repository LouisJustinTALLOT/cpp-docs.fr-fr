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
ms.openlocfilehash: b260d3a88fc8c3f2d341005c1e47cfd9ab668e1e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500359"
---
# <a name="cdraglistbox-class"></a>CDragListBox, classe

En plus de fournir les fonctionnalités d’une zone de liste Windows, la `CDragListBox` classe permet à l’utilisateur de déplacer des éléments de zone de liste, tels que des noms de fichiers, dans la zone de liste.

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
|[CDragListBox :: BeginDrag](#begindrag)|Appelé par le Framework lorsqu’une opération glisser commence.|
|[CDragListBox::CancelDrag](#canceldrag)|Appelé par le Framework lorsqu’une opération glisser a été annulée.|
|[CDragListBox ::D ragging](#dragging)|Appelée par l’infrastructure pendant une opération glisser.|
|[CDragListBox ::D rawInsert](#drawinsert)|Dessine le Guide d’insertion de la zone de liste de glissement.|
|[CDragListBox ::D ropped](#dropped)|Appelé par le Framework après que l’élément a été supprimé.|
|[CDragListBox::ItemFromPt](#itemfrompt)|Retourne les coordonnées de l’élément déplacé.|

## <a name="remarks"></a>Remarques

Les zones de liste avec cette fonctionnalité permettent aux utilisateurs de classer les éléments d’une liste de la manière la plus utile. Par défaut, la zone de liste déplace l’élément vers le nouvel emplacement dans la liste. Toutefois, `CDragListBox` les objets peuvent être personnalisés pour copier des éléments au lieu de les déplacer.

Le contrôle de zone de liste associé à la `CDragListBox` classe ne doit pas avoir le LBS_SORT ou le style de LBS_MULTIPLESELECT. Pour obtenir une description des styles de zone de liste, consultez [styles de zone de liste](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Pour utiliser une zone de liste de glissement dans une boîte de dialogue existante de votre application, ajoutez un contrôle de zone de liste à votre modèle de boîte de dialogue à l’aide de l’éditeur de boîtes de dialogue, puis assignez une variable membre (de catégorie `Control` et de type de variable `CDragListBox` ) correspondant au contrôle de zone de liste dans votre modèle de boîte de dialogue.

Pour plus d’informations sur l’assignation de contrôles à des variables membres, consultez [raccourci pour la définition de variables membres pour les contrôles de boîte de dialogue](../../windows/adding-editing-or-deleting-controls.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a> CDragListBox :: BeginDrag

Appelée par l’infrastructure quand un événement qui peut commencer une opération glisser, par exemple en appuyant sur le bouton gauche de la souris.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) qui contient les coordonnées de l’élément déplacé.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si le glissement est autorisé ; sinon, 0.

### <a name="remarks"></a>Remarques

Substituez cette fonction si vous souhaitez contrôler ce qui se passe au démarrage d’une opération glisser. L’implémentation par défaut capture la souris et reste en mode glisser jusqu’à ce que l’utilisateur clique sur le bouton gauche ou droit de la souris ou appuie sur ÉCHAP, moment auquel l’opération glisser est annulée.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a> CDragListBox::CancelDrag

Appelé par le Framework lorsqu’une opération glisser a été annulée.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) qui contient les coordonnées de l’élément déplacé.

### <a name="remarks"></a>Remarques

Substituez cette fonction pour gérer tout traitement spécial pour votre contrôle de zone de liste.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a> CDragListBox::CDragListBox

Construit un objet `CDragListBox`.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a> CDragListBox ::D ragging

Appelé par le Framework lorsqu’un élément de zone de liste est glissé dans l' `CDragListBox` objet.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) qui contient les coordonnées d’écran x et y du curseur.

### <a name="return-value"></a>Valeur renvoyée

ID de ressource du curseur à afficher. Les valeurs suivantes sont possibles :

- DL_COPYCURSOR indique que l’élément sera copié.

- DL_MOVECURSOR indique que l’élément sera déplacé.

- DL_STOPCURSOR indique que la cible de déplacement actuelle n’est pas acceptable.

### <a name="remarks"></a>Remarques

Le comportement par défaut retourne DL_MOVECURSOR. Remplacez cette fonction si vous souhaitez fournir des fonctionnalités supplémentaires.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a> CDragListBox ::D rawInsert

Appelé par l’infrastructure pour dessiner le Guide d’insertion avant l’élément avec l’index spécifié.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro du point d’insertion.

### <a name="remarks"></a>Remarques

La valeur-1 efface le Guide d’insertion. Substituez cette fonction pour modifier l’apparence ou le comportement du Guide d’insertion.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a> CDragListBox ::D ropped

Appelé par le Framework lorsqu’un élément est supprimé dans un `CDragListBox` objet.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Paramètres

*nSrcIndex*<br/>
Spécifie l’index de base zéro de la chaîne supprimée.

*pt*<br/>
Objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) qui contient les coordonnées du site cible.

### <a name="remarks"></a>Remarques

Le comportement par défaut copie l’élément de zone de liste et ses données vers le nouvel emplacement, puis supprime l’élément d’origine. Substituez cette fonction pour personnaliser le comportement par défaut, par exemple l’activation de copies d’éléments de zone de liste à déplacer vers d’autres emplacements de la liste.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a> CDragListBox::ItemFromPt

Appelez cette fonction pour récupérer l’index de base zéro de l’élément de zone de liste situé à *PT*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Objet [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) contenant les coordonnées d’un point dans la zone de liste.

*bAutoScroll*<br/>
Valeur différente de zéro si le défilement est autorisé ; sinon, 0.

### <a name="return-value"></a>Valeur renvoyée

Index de base zéro de l’élément de zone de liste de glissement.

## <a name="see-also"></a>Voir aussi

[Exemple MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)
