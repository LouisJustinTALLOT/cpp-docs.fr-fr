---
description: 'En savoir plus sur : classe CMFCRibbonSlider'
title: CMFCRibbonSlider, classe
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
ms.openlocfilehash: d125afdf961d97c0501742acdc75d7802c7e104d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321732"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider, classe

La `CMFCRibbonSlider` classe implémente un contrôle Slider que vous pouvez ajouter à une barre de ruban ou une barre d’état de ruban. Le contrôle Slider de ruban ressemble aux curseurs de zoom présents dans les applications Office 2007.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Construit et initialise un contrôle Slider de ruban.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Retourne la position actuelle du contrôle Slider.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Retourne la valeur maximale du curseur.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Retourne la valeur minimale du curseur.|
|[CMFCRibbonSlider :: GetRegularSize](#getregularsize)|Retourne la taille normale de l'élément de ruban. (Substitue [CMFCRibbonBaseElement :: GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Retourne la taille de l’incrément de zoom du contrôle Slider.|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Spécifie si le curseur a des boutons de zoom.|
|[CMFCRibbonSlider :: OnDraw](#ondraw)|Appelé par l'infrastructure pour dessiner l'élément de ruban. (Substitue [CMFCRibbonBaseElement :: OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Définit la position actuelle du contrôle Slider.|
|[CMFCRibbonSlider :: SetRange](#setrange)|Spécifie la plage du contrôle Slider en définissant les valeurs minimale et maximale.|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Affiche ou masque les boutons de zoom.|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Définit la taille de l’incrément de zoom du contrôle Slider.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser la `SetRange` méthode pour configurer la plage d’incréments de zoom pour le curseur. Vous pouvez définir la position actuelle du curseur à l’aide de la `SetPos` méthode.

Vous pouvez afficher des boutons de zoom circulaires à gauche et à droite du contrôle Slider à l’aide de la `SetZoomButtons` méthode. Par défaut, le curseur est horizontal, le bouton de zoom gauche affiche un signe moins et le bouton de zoom droit affiche un signe plus.

La `SetZoomIncrement` méthode définit l’incrément à ajouter ou à soustraire de la position actuelle lorsqu’un utilisateur clique sur les boutons de zoom.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes dans la `CMFCRibbonSlider` classe pour définir les propriétés du curseur. L’exemple montre comment construire un `CMFCRibbonSlider` objet, afficher des boutons de zoom, définir la position actuelle du contrôle Slider et définir la plage de valeurs du contrôle Slider.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxribbonslider. h

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a> CMFCRibbonSlider::CMFCRibbonSlider

Construisez un curseur de ruban.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
dans ID de curseur.

[in]. *nWidth* Largeur du curseur en pixels.

### <a name="remarks"></a>Notes

Construit un curseur de ruban qui est *nWidth* pixels de largeur dans la catégorie du panneau où le curseur est ajouté. Par défaut, le curseur est horizontal.

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a> CMFCRibbonSlider::GetPos

Retourne la position actuelle du contrôle Slider.

```
int GetPos() const;
```

### <a name="return-value"></a>Valeur renvoyée

Position actuelle du contrôle Slider, qui est une position par rapport au début du curseur.

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a> CMFCRibbonSlider::GetRangeMax

Obtient l’incrément maximal du curseur que le curseur peut parcourir sur le contrôle Slider.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valeur renvoyée

Incrément maximal du curseur que le curseur peut parcourir sur le contrôle Slider.

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a> CMFCRibbonSlider::GetRangeMin

Retourne l’incrément minimal que le curseur peut parcourir sur le contrôle Slider.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Incrément minimal que le curseur peut parcourir sur le contrôle Slider.

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a> CMFCRibbonSlider :: GetRegularSize

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a> CMFCRibbonSlider::GetZoomIncrement

Obtenez l’incrément de zoom du contrôle Slider.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Valeur renvoyée

Incrément de zoom du contrôle Slider.

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a> CMFCRibbonSlider::HasZoomButtons

Spécifie si le curseur a des boutons de zoom.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le curseur a des boutons de zoom ; FALSe dans le cas contraire.

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a> CMFCRibbonSlider :: OnDraw

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a> CMFCRibbonSlider::SetPos

Définit la position actuelle du contrôle Slider.

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
dans Spécifie la position à définir pour le curseur. La position est relative au début du curseur.

*bRedraw*<br/>
dans Si la valeur est TRUE, le curseur est redessiné.

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a> CMFCRibbonSlider :: SetRange

Définissez la plage de valeurs du contrôle Slider.

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
dans Spécifie la valeur minimale du contrôle Slider.

*nMax*<br/>
dans Spécifie la valeur maximale du contrôle Slider.

### <a name="remarks"></a>Notes

Spécifie la plage de valeurs du contrôle Slider en définissant les valeurs minimale et maximale.

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a> CMFCRibbonSlider::SetZoomButtons

Afficher ou masquer les boutons de zoom.

```cpp
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Paramètres

[in]. *bset* TRUE pour afficher les boutons de zoom ; FALSe pour les masquer.

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a> CMFCRibbonSlider::SetZoomIncrement

Définissez l’incrément de zoom du contrôle Slider.

```cpp
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Paramètres

*nZoomIncrement*<br/>
dans Spécifie l’incrément de zoom du contrôle Slider.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement, classe](../../mfc/reference/cmfcribbonbaseelement-class.md)
