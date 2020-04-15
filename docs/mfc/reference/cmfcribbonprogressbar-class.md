---
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
ms.openlocfilehash: 063f8ce560af84d350abc0114644f6a63f969f95
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368862"
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
|[CMFCRibbonProgressBar::GetPos](#getpos)|Retourne les progrès actuels.|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Retourne la valeur maximale de la plage actuelle.|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Retourne la valeur minimale de la plage actuelle.|
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Retourne la taille normale de l'élément de ruban. (Overrides [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Précise si la barre de progression fonctionne en mode infini.|
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Appelé par l'infrastructure pour dessiner l'élément de ruban. (Overrides [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Définit la barre de progression pour fonctionner en mode infini.|
|[CMFCRibbonProgressBar::SetPos](#setpos)|Définit les progrès actuels.|
|[CMFCRibbonProgressBar::SetRange](#setrange)|Définit les valeurs minimales et maximales.|

## <a name="remarks"></a>Notes

A `CMFCRibbonProgressBar` peut fonctionner en deux modes : régulier et infini. En mode régulier, la barre de progression est remplie de gauche à droite et s’arrête lorsqu’elle atteint la valeur maximale. En mode infini, la barre de progression est remplie à plusieurs reprises de la valeur minimale à la valeur maximale. Vous pouvez utiliser le mode infini pour indiquer qu’une opération est en cours, mais que le temps d’achèvement est inconnu.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonProgressBar` . L’exemple montre comment mettre la barre de progression au travail en mode infini (où le temps d’achèvement d’une opération est inconnu), définir les valeurs minimales et maximales pour la barre de progression, et définir la position actuelle de la barre de progression. Cet extrait de code fait partie de [l’échantillon de démonstration ms Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxRibbonProgressBar.h

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar

Construit et initialise un objet [CMFCRibbonProgressBar.](../../mfc/reference/cmfcribbonprogressbar-class.md)

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[dans] Spécifie l’ID de commande de la barre de progression du ruban.

*nWidth (en)*<br/>
[dans] Spécifie la largeur, en pixels, de la barre de progression du ruban.

*nHeight (en)*<br/>
[dans] Spécifie la hauteur, en pixels, de la barre de progression du ruban.

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFCRibbonProgressBar::GetPos

Retourne la position actuelle de la barre de progression.

```
int GetPos () const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur représentant la position actuelle de la barre de progression.

### <a name="remarks"></a>Notes

La plage en cours d’ensemble doit se situer dans la plage spécifiée par la méthode [CMFCRibbonProgressBar::SetRange.](#setrange)

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax

Retourne la valeur maximale actuelle de la barre de progression.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur maximale de la plage actuelle.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin

Retourne la valeur minimale actuelle de la barre de progression.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur minimale de la plage actuelle.

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[dans] *pDC (pDC)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode

Précise si la barre de progression fonctionne en mode infini.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la barre de progression est en mode infini; autrement, FALSE.

### <a name="remarks"></a>Notes

En mode infini, la barre de progression se remplit à plusieurs reprises de la valeur minimale à la valeur maximale. Vous pouvez utiliser le mode infini pour indiquer qu’une opération est en cours, mais que le temps d’achèvement est inconnu.

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[dans] *pDC (pDC)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode

Définit la barre de progression pour fonctionner en mode infini.

```
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSet (en anglais)*<br/>
[dans] VRAI pour spécifier que la barre de progression est en mode infini; autrement, FALSE.

### <a name="remarks"></a>Notes

Habituellement, si la barre de progression est en mode infini, il est révélateur à l’utilisateur qu’une opération est en cours, mais que le temps d’achèvement est inconnu. Ainsi, la barre de progression se remplit à plusieurs reprises de la valeur minimale à la valeur maximale.

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFCRibbonProgressBar::SetPos

Définit la position actuelle de la barre de progression.

```
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
[dans] Précise la position à laquelle la barre de progression est fixée.

*bRedraw (en)*<br/>
[dans] Précise si la barre de progression doit être redessinée.

### <a name="remarks"></a>Notes

La plage en cours d’ensemble doit se situer dans la plage spécifiée par la méthode [CMFCRibbonProgressBar::SetRange.](#setrange)

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFCRibbonProgressBar::SetRange

Définit les valeurs minimales et maximales pour la barre de progression.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
[dans] Spécifie la valeur minimale de la plage.

*Nmax*<br/>
[dans] Spécifie la valeur maximale de la plage.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir la portée de la barre de progression en fixant des valeurs minimales et maximales.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
