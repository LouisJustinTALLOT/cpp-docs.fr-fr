---
title: Classe CMFCRibbonSlider
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
ms.openlocfilehash: f2a05ca1433ca3a44b0459360e3f09fe7a274c68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368831"
---
# <a name="cmfcribbonslider-class"></a>Classe CMFCRibbonSlider

La `CMFCRibbonSlider` classe implémente un contrôle de curseur que vous pouvez ajouter à une barre de ruban ou une barre d’état de ruban. Le contrôle Slider de ruban ressemble aux curseurs de zoom présents dans les applications Office 2007.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Construit et initialise un contrôle de curseur ruban.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Retourne la position actuelle du contrôle du curseur.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Retourne la valeur maximale du curseur.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Retourne la valeur minimale du curseur.|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Retourne la taille normale de l'élément de ruban. (Overrides [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Retourne la taille de l’incrément de zoom pour le contrôle du curseur.|
|[CMFCRibbonSlider:HasZoomButtons](#haszoombuttons)|Précise si le curseur a des boutons de zoom.|
|[CMFCRibbonSlider::OnDraw](#ondraw)|Appelé par l'infrastructure pour dessiner l'élément de ruban. (Overrides [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Définit la position actuelle du contrôle du curseur.|
|[CMFCRibbonSlider::SetRange](#setrange)|Spécifie la plage du contrôle du curseur en définissant les valeurs minimales et maximales.|
|[CMFCRibbonSlider:SetZoomButtons](#setzoombuttons)|Affiche ou cache les boutons de zoom.|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Définit la taille de l’incrément de zoom pour le contrôle du curseur.|

## <a name="remarks"></a>Notes

Vous pouvez `SetRange` utiliser la méthode pour configurer la plage d’incréments de zoom pour le curseur. Vous pouvez définir la position actuelle `SetPos` du curseur en utilisant la méthode.

Vous pouvez afficher des boutons de zoom circulaires sur le `SetZoomButtons` côté gauche et droit du contrôle du curseur en utilisant la méthode. Par défaut, le curseur est horizontal, le bouton zoom gauche affiche un signe moins et le bouton de zoom droit affiche un signe plus.

La `SetZoomIncrement` méthode définit l’incrément à ajouter ou à soustraire à la position actuelle lorsqu’un utilisateur clique sur les boutons de zoom.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `CMFCRibbonSlider` diverses méthodes dans la classe pour définir les propriétés du curseur. L’exemple montre comment `CMFCRibbonSlider` construire un objet, afficher les boutons de zoom, définir la position actuelle du contrôle du curseur et définir la gamme de valeurs pour le contrôle du curseur.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribbonslider.h

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a>CMFCRibbonSlider::CMFCRibbonSlider

Construire un curseur de ruban.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[dans] Id curseur.

[in]. *nWidth (en)* Largeur de curseur en pixels.

### <a name="remarks"></a>Notes

Construit un curseur ruban qui est *nWidth* pixels large dans la catégorie panneau où le curseur est ajouté. Par défaut, le curseur est horizontal.

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a>CMFCRibbonSlider::GetPos

Retourne la position actuelle du contrôle du curseur.

```
int GetPos() const;
```

### <a name="return-value"></a>Valeur de retour

La position actuelle du contrôle du curseur, qui est une position par rapport au début du curseur.

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a>CMFCRibbonSlider::GetRangeMax

Obtient l’incrément maximal du curseur que le curseur peut voyager sur le contrôle du curseur.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valeur de retour

L’incrément maximal du curseur que le curseur peut voyager sur le contrôle du curseur.

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a>CMFCRibbonSlider::GetRangeMin

Retourne l’augmentation minimale que le curseur peut voyager sur le contrôle du curseur.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valeur de retour

L’augmentation minimale que le curseur peut voyager sur le contrôle du curseur.

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSlider::GetRegularSize

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[dans] *pDC (pDC)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a>CMFCRibbonSlider::GetZoomIncrement

Obtenez l’incrément de zoom pour le contrôle du curseur.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Valeur de retour

L’incrément du zoom pour le contrôle du curseur.

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a>CMFCRibbonSlider:HasZoomButtons

Précise si le curseur a des boutons de zoom.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le curseur a des boutons de zoom; FALSE autrement.

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a>CMFCRibbonSlider::OnDraw

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[dans] *pDC (pDC)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a>CMFCRibbonSlider::SetPos

Définissez la position actuelle du contrôle du curseur.

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
[dans] Spécifie la position à définir pour le curseur. La position est relative au début du curseur.

*bRedraw (en)*<br/>
[dans] Si VRAI, le curseur sera redessiné.

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a>CMFCRibbonSlider::SetRange

Définissez la gamme de valeurs pour le contrôle du curseur.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
[dans] Spécifie la valeur minimale du contrôle du curseur.

*Nmax*<br/>
[dans] Spécifie la valeur maximale du contrôle du curseur.

### <a name="remarks"></a>Notes

Spécifie la gamme de valeurs pour le contrôle du curseur en définissant les valeurs minimales et maximales.

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a>CMFCRibbonSlider:SetZoomButtons

Afficher ou masquer les boutons de zoom.

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Paramètres

[in]. *bSet (en anglais)* VRAI pour afficher les boutons de zoom; FALSE pour les cacher.

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a>CMFCRibbonSlider::SetZoomIncrement

Réglez l’incrément du zoom pour le contrôle du curseur.

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Paramètres

*nZoomIncrément*<br/>
[dans] Spécifie l’incrément du zoom du contrôle du curseur.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)
