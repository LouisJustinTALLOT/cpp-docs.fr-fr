---
title: Cmfcribbonprogressbar, classe
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
ms.openlocfilehash: 7c16217378cb8825ca4605687770de177e720c1d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778167"
---
# <a name="cmfcribbonprogressbar-class"></a>Cmfcribbonprogressbar, classe

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
|[CMFCRibbonProgressBar::GetPos](#getpos)|Retourne l’état d’avancement.|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Retourne la valeur maximale de la plage actuelle.|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Retourne la valeur minimale de la plage actuelle.|
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Retourne la taille normale de l'élément de ruban. (Substitue [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Spécifie si la barre de progression fonctionne en mode infini.|
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Appelé par l'infrastructure pour dessiner l'élément de ruban. (Substitue [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Définit la barre de progression pour fonctionner en mode infini.|
|[CMFCRibbonProgressBar::SetPos](#setpos)|Définit la progression actuelle.|
|[CMFCRibbonProgressBar::SetRange](#setrange)|Définit les valeurs minimales et maximales.|

## <a name="remarks"></a>Notes

Un `CMFCRibbonProgressBar` peut fonctionner dans deux modes : normal et infinie. En mode normal, la barre de progression est remplie de gauche à droite et s’arrête lorsqu’il atteint la valeur maximale. En mode infini, la barre de progression est remplie à plusieurs reprises à partir de la valeur minimale à la valeur maximale. Vous pouvez utiliser le mode infini pour indiquer qu’une opération est en cours, mais que l’heure d’achèvement est inconnu.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonProgressBar` . L’exemple montre comment définir la barre de progression pour fonctionner en mode infini (où l’heure d’achèvement d’une opération est inconnu), définissez les valeurs minimales et maximales pour la barre de progression et définissez la position actuelle de la barre de progression. Cet extrait de code fait partie de la [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxRibbonProgressBar.h

##  <a name="cmfcribbonprogressbar"></a>  CMFCRibbonProgressBar::CMFCRibbonProgressBar

Crée et initialise un [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) objet.

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[in] Spécifie l’ID de commande pour la barre de progression du ruban.

*nWidth*<br/>
[in] Spécifie la largeur, en pixels, de la barre de progression du ruban.

*nHeight*<br/>
[in] Spécifie la hauteur, en pixels, de la barre de progression du ruban.

##  <a name="getpos"></a>  CMFCRibbonProgressBar::GetPos

Retourne la position actuelle de la barre de progression.

```
int GetPos () const;
```

### <a name="return-value"></a>Valeur de retour

Valeur représentant la position actuelle de la barre de progression.

### <a name="remarks"></a>Notes

La plage définie doit être dans la plage spécifiée par la [CMFCRibbonProgressBar::SetRange](#setrange) (méthode).

##  <a name="getrangemax"></a>  CMFCRibbonProgressBar::GetRangeMax

Retourne la barre de progression actuelle de le valeur maximale.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur maximale de la plage actuelle.

### <a name="remarks"></a>Notes

##  <a name="getrangemin"></a>  CMFCRibbonProgressBar::GetRangeMin

Retourne la barre de progression actuelle de le valeur de plage minimale.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur minimale de la plage actuelle.

##  <a name="getregularsize"></a>  CMFCRibbonProgressBar::GetRegularSize

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[in] *pDC*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="isinfinitemode"></a>  CMFCRibbonProgressBar::IsInfiniteMode

Spécifie si la barre de progression fonctionne en mode infini.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la barre de progression est en mode infini ; Sinon, FALSE.

### <a name="remarks"></a>Notes

En mode infini, la barre de progression se remplit à plusieurs reprises à partir de la valeur minimale à la valeur maximale. Vous pouvez utiliser le mode infini pour indiquer qu’une opération est en cours, mais que l’heure d’achèvement est inconnu.

##  <a name="ondraw"></a>  CMFCRibbonProgressBar::OnDraw

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[in] *pDC*<br/>

### <a name="remarks"></a>Notes

##  <a name="setinfinitemode"></a>  CMFCRibbonProgressBar::SetInfiniteMode

Définit la barre de progression pour fonctionner en mode infini.

```
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSet*<br/>
[in] TRUE pour spécifier que la barre de progression est en mode infini ; Sinon, FALSE.

### <a name="remarks"></a>Notes

En règle générale, si la barre de progression est en mode infini, il signale à l’utilisateur qu’une opération est en cours, mais que l’heure d’achèvement est inconnu. Par conséquent, la barre de progression se remplit à plusieurs reprises à partir de la valeur minimale à la valeur maximale.

##  <a name="setpos"></a>  CMFCRibbonProgressBar::SetPos

Définit la position actuelle de la barre de progression.

```
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
[in] Spécifie la position à laquelle la barre de progression est définie.

*bRedraw*<br/>
[in] Spécifie si la barre de progression doit être redessinée.

### <a name="remarks"></a>Notes

La plage définie doit être dans la plage spécifiée par la [CMFCRibbonProgressBar::SetRange](#setrange) (méthode).

##  <a name="setrange"></a>  CMFCRibbonProgressBar::SetRange

Définit les valeurs minimales et maximales pour la barre de progression.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
[in] Spécifie la valeur minimale de la plage.

*nombre maximal*<br/>
[in] Spécifie la valeur maximale de la plage.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir la plage de la barre de progression en définissant les valeurs minimales et maximales.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Cmfcribbonbaseelement, classe](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
