---
description: 'En savoir plus sur : classe CMFCRibbonProgressBar'
title: CMFCRibbonProgressBar, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: b4e91a604386a57aa7cac59294c569635583304c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321759"
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar, classe

Implémente un contrôle qui affiche l'avancement d'une opération de longue durée.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Construit et initialise un objet `CMFCRibbonProgressBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonProgressBar::GetPos](#getpos)|Retourne la progression actuelle.|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Retourne la valeur maximale de la plage actuelle.|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Retourne la valeur minimale de la plage actuelle.|
|[CMFCRibbonProgressBar :: GetRegularSize](#getregularsize)|Retourne la taille normale de l'élément de ruban. (Substitue [CMFCRibbonBaseElement :: GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Spécifie si la barre de progression fonctionne en mode infini.|
|[CMFCRibbonProgressBar :: OnDraw](#ondraw)|Appelé par l'infrastructure pour dessiner l'élément de ruban. (Substitue [CMFCRibbonBaseElement :: OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Définit la barre de progression pour qu’elle fonctionne en mode infini.|
|[CMFCRibbonProgressBar::SetPos](#setpos)|Définit la progression actuelle.|
|[CMFCRibbonProgressBar :: SetRange](#setrange)|Définit les valeurs minimale et maximale.|

## <a name="remarks"></a>Notes

Un `CMFCRibbonProgressBar` peut fonctionner dans deux modes : normal et infini. En mode normal, la barre de progression est remplie de gauche à droite et s’arrête lorsqu’elle atteint la valeur maximale. En mode infini, la barre de progression est remplie à plusieurs reprises, de la valeur minimale à la valeur maximale. Vous pouvez utiliser le mode infini pour indiquer qu’une opération est en cours, mais que l’heure d’achèvement est inconnue.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonProgressBar` . L’exemple montre comment définir la barre de progression pour qu’elle fonctionne en mode infini (où l’heure d’achèvement d’une opération est inconnue), définir les valeurs minimale et maximale de la barre de progression et définir la position actuelle de la barre de progression. Cet extrait de code fait partie de l' [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxRibbonProgressBar. h

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a> CMFCRibbonProgressBar::CMFCRibbonProgressBar

Construit et initialise un objet [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) .

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
dans Spécifie l’ID de commande pour la barre de progression du ruban.

*nWidth*<br/>
dans Spécifie la largeur, en pixels, de la barre de progression du ruban.

*nHeight*<br/>
dans Spécifie la hauteur, en pixels, de la barre de progression du ruban.

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a> CMFCRibbonProgressBar::GetPos

Retourne la position actuelle de la barre de progression.

```
int GetPos () const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur représentant la position actuelle de la barre de progression.

### <a name="remarks"></a>Notes

La plage définie doit être comprise dans la plage spécifiée par la méthode [CMFCRibbonProgressBar :: SetRange](#setrange) .

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a> CMFCRibbonProgressBar::GetRangeMax

Retourne la valeur maximale actuelle de la barre de progression.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur maximale de la plage actuelle.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a> CMFCRibbonProgressBar::GetRangeMin

Retourne la valeur de plage minimale actuelle de la barre de progression.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur minimale de la plage actuelle.

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a> CMFCRibbonProgressBar :: GetRegularSize

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a> CMFCRibbonProgressBar::IsInfiniteMode

Spécifie si la barre de progression fonctionne en mode infini.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la barre de progression est en mode infini ; Sinon, FALSe.

### <a name="remarks"></a>Notes

En mode infini, la barre de progression se remplit à plusieurs reprises de la valeur minimale à la valeur maximale. Vous pouvez utiliser le mode infini pour indiquer qu’une opération est en cours, mais que l’heure d’achèvement est inconnue.

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a> CMFCRibbonProgressBar :: OnDraw

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a> CMFCRibbonProgressBar::SetInfiniteMode

Définit la barre de progression pour qu’elle fonctionne en mode infini.

```cpp
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSet*<br/>
dans TRUE pour spécifier que la barre de progression est en mode infini ; Sinon, FALSe.

### <a name="remarks"></a>Notes

En règle générale, si la barre de progression est en mode infini, elle indique à l’utilisateur qu’une opération est en cours, mais que l’heure d’achèvement est inconnue. Ainsi, la barre de progression se remplit à plusieurs reprises de la valeur minimale à la valeur maximale.

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a> CMFCRibbonProgressBar::SetPos

Définit la position actuelle de la barre de progression.

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
dans Spécifie la position à laquelle la barre de progression est définie.

*bRedraw*<br/>
dans Spécifie si la barre de progression doit être redessinée.

### <a name="remarks"></a>Notes

La plage définie doit être comprise dans la plage spécifiée par la méthode [CMFCRibbonProgressBar :: SetRange](#setrange) .

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a> CMFCRibbonProgressBar :: SetRange

Définit les valeurs minimale et maximale de la barre de progression.

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
dans Spécifie la valeur minimale de la plage.

*nMax*<br/>
dans Spécifie la valeur maximale de la plage.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir la plage de la barre de progression en définissant les valeurs minimales et maximales.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement, classe](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)
