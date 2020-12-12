---
description: 'En savoir plus sur : classe CMFCColorPickerCtrl'
title: CMFCColorPickerCtrl, classe
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: e4363c08af86dee96df1492e9a029414d9902435
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313071"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl, classe

La `CMFCColorPickerCtrl` classe fournit des fonctionnalités pour un contrôle utilisé pour sélectionner des couleurs.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCColorPickerCtrl :: CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Construit un objet `CMFCColorPickerCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCColorPickerCtrl :: GetColor](#getcolor)|Récupère la couleur sélectionnée par l’utilisateur.|
|[CMFCColorPickerCtrl :: GetHLS](#gethls)|Récupère les valeurs de teinte, de luminance et de saturation de la couleur sélectionnée par l’utilisateur.|
|[CMFCColorPickerCtrl :: GetHue](#gethue)|Récupère le composant teinte de la couleur sélectionnée par l’utilisateur.|
|[CMFCColorPickerCtrl :: GetLuminance](#getluminance)|Récupère le composant luminance de la couleur sélectionnée par l’utilisateur.|
|[CMFCColorPickerCtrl :: GetSaturation](#getsaturation)|Récupère le composant de saturation de la couleur sélectionnée par l’utilisateur.|
|[CMFCColorPickerCtrl :: SelectCellHexagon](#selectcellhexagon)|Définit la couleur actuelle sur la couleur définie par les composants de couleur RVB spécifiés ou l’hexagone de cellule spécifié.|
|[CMFCColorPickerCtrl :: SetColor](#setcolor)|Définit la couleur actuelle sur la valeur de couleur RVB spécifiée.|
|[CMFCColorPickerCtrl :: SetHLS](#sethls)|Définit la couleur actuelle sur la valeur de couleur TLS spécifiée.|
|[CMFCColorPickerCtrl :: SetHue](#sethue)|Modifie le composant teinte de la couleur actuellement sélectionnée.|
|[CMFCColorPickerCtrl :: SetLuminance](#setluminance)|Modifie le composant luminance de la couleur actuellement sélectionnée.|
|[CMFCColorPickerCtrl :: SetLuminanceBarWidth](#setluminancebarwidth)|Définit la largeur de la barre de luminance dans le contrôle de sélecteur de couleurs.|
|[CMFCColorPickerCtrl :: SetOriginalColor](#setoriginalcolor)|Définit la couleur sélectionnée initiale.|
|[CMFCColorPickerCtrl :: SetPalette](#setpalette)|Définit la palette de couleurs actuelle.|
|[CMFCColorPickerCtrl :: SetSaturation](#setsaturation)|Modifie le composant de saturation de la couleur actuellement sélectionnée.|
|[CMFCColorPickerCtrl :: SetType](#settype)|Définit le type de contrôle de sélecteur de couleurs à afficher.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorPickerCtrl ::D rawCursor](#drawcursor)|Appelé par le Framework avant qu’un curseur qui pointe vers la couleur sélectionnée ne soit affiché.|

## <a name="remarks"></a>Notes

Les couleurs standard sont sélectionnées dans une palette de couleurs hexagonales, et les couleurs personnalisées sont sélectionnées à partir d’une barre de luminance dans laquelle les couleurs sont spécifiées en utilisant la notation rouge, verte/bleue ou la notation teinte/satuaration/luminance.

L’illustration suivante représente plusieurs `CMFCColorPickerCtrl` objets.

![Boîte de dialogue CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "Boîte de dialogue CMFCColorPickerCtrl")

Le `CMFCColorPickerCtrl` prend en charge deux paires de styles. Les styles HEX et HEX_GREYSCALE sont appropriés pour la sélection de couleurs standard. Les styles du sélecteur et de la LUMINANCE sont appropriés pour la sélection des couleurs personnalisées.

Procédez comme suit pour incorporer le `CMFCColorPickerCtrl` contrôle dans votre boîte de dialogue :

1. Si vous utilisez l' **Assistant ClassWizard**, insérez un nouveau contrôle bouton dans votre modèle de boîte de dialogue (car la `CMFCColorPickerCtrl` classe est héritée de la `CButton` classe).

1. Insérez une variable membre associée au nouveau contrôle Button dans votre classe de boîte de dialogue. Modifiez ensuite le type de variable de `CButton` en `CMFCColorPickerCtrl` .

1. Insérez le `WM_INITDIALOG` Gestionnaire de messages pour la classe de boîte de dialogue. Dans le gestionnaire, définissez le type, la palette et la couleur sélectionnée initiale du `CMFCColorPickerCtrl` contrôle.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer un `CMFCColorPickerCtrl` objet à l’aide de diverses méthodes de la `CMFCColorPickerCtrl` classe. L’exemple montre comment définir le type du contrôle sélecteur et comment définir sa couleur, sa teinte, sa luminance et sa saturation. L’exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxcolorpickerctrl. h

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a> CMFCColorPickerCtrl :: CMFCColorPickerCtrl

Construit un objet `CMFCColorPickerCtrl`.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a> CMFCColorPickerCtrl ::D rawCursor

Appelé par le Framework avant qu’un curseur qui pointe vers la couleur sélectionnée ne soit affiché.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectangulaire*<br/>
dans Spécifie une zone rectangulaire autour de la couleur sélectionnée.

### <a name="remarks"></a>Notes

Substituez cette méthode lorsque vous devez modifier la forme du curseur qui pointe vers la couleur sélectionnée.

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a> CMFCColorPickerCtrl :: GetColor

Récupère la couleur sélectionnée par l’utilisateur.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur RVB de la couleur sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a> CMFCColorPickerCtrl :: GetHLS

Récupère les valeurs de teinte, de luminance et de saturation de la couleur sélectionnée par l’utilisateur.

```cpp
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>Paramètres

*Hue*<br/>
à Pointeur vers une variable de type double qui reçoit les informations de teinte.

*luminance*<br/>
à Pointeur vers une variable de type double qui reçoit des informations de luminance.

*saturation*<br/>
à Pointeur vers une variable de type double qui reçoit les informations de saturation.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a> CMFCColorPickerCtrl :: GetHue

Récupère le composant teinte de la couleur sélectionnée par l’utilisateur.

```
double GetHue() const;
```

### <a name="return-value"></a>Valeur renvoyée

Composant teinte de la couleur sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a> CMFCColorPickerCtrl :: GetLuminance

Récupère le composant luminance de la couleur sélectionnée par l’utilisateur.

```
double GetLuminance() const;
```

### <a name="return-value"></a>Valeur renvoyée

Composant luminance de la couleur sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a> CMFCColorPickerCtrl :: GetSaturation

Récupère la valeur de saturation de la couleur sélectionnée par l’utilisateur.

```
double GetSaturation() const;
```

### <a name="return-value"></a>Valeur renvoyée

Composant de saturation de la couleur sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a> CMFCColorPickerCtrl :: SelectCellHexagon

Définit la couleur actuelle sur la couleur définie par les composants de couleur RVB spécifiés ou l’hexagone de cellule spécifié.

```cpp
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>Paramètres

*R*<br/>
dans Composant de couleur rouge.

*G*<br/>
dans Composant de couleur verte.

*B*<br/>
dans Composant de couleur bleu.

*x*<br/>
dans Coordonnée x du curseur, qui pointe vers un hexagone de cellule.

*y*<br/>
dans Coordonnée y du curseur, qui pointe vers un hexagone de cellule.

### <a name="return-value"></a>Valeur renvoyée

La deuxième surcharge de cette méthode retourne toujours FALSe.

### <a name="remarks"></a>Notes

La première surcharge de cette méthode affecte à la couleur actuelle la couleur qui correspond aux composants de couleur rouge, vert et bleu spécifiés pour le contrôle de sélection de couleurs.

La deuxième surcharge de cette méthode affecte à la couleur actuelle la couleur de l’hexagone de cellule vers lequel pointe l’emplacement du curseur spécifié.

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a> CMFCColorPickerCtrl :: SetColor

Définit la couleur actuelle sur la valeur de couleur RVB spécifiée.

```cpp
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
dans Valeur de couleur RVB.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a> CMFCColorPickerCtrl :: SetHLS

Définit la couleur actuelle sur la valeur de couleur TLS spécifiée.

```cpp
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>Paramètres

*Hue*<br/>
dans Valeur de teinte.

*luminance*<br/>
dans Valeur de luminance.

*saturation*<br/>
dans Valeur de saturation.

*bInvalidate*<br/>
dans TRUE pour forcer la fenêtre à se mettre immédiatement à jour vers la nouvelle couleur ; Sinon, FALSe. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a> CMFCColorPickerCtrl :: SetHue

Modifie la teinte de la couleur actuellement sélectionnée.

```cpp
void SetHue(double Hue);
```

### <a name="parameters"></a>Paramètres

*Teinte*<br/>
dans Valeur de teinte.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a> CMFCColorPickerCtrl :: SetLuminance

Modifie la luminance de la couleur actuellement sélectionnée.

```cpp
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>Paramètres

*Luminance*<br/>
dans Valeur de luminance.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a> CMFCColorPickerCtrl :: SetLuminanceBarWidth

Définit la largeur de la barre de luminance dans le contrôle de sélecteur de couleurs.

```cpp
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>Paramètres

*w*<br/>
dans Largeur de la barre de luminance mesurée en pixels.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour redimensionner la barre de luminance, qui se trouve sous l’onglet **personnalisé** du contrôle sélecteur de couleurs. Le paramètre *w* spécifie la nouvelle largeur de la barre de luminance. La valeur Width est ignorée si elle dépasse trois-quarts de la largeur de la zone cliente.

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a> CMFCColorPickerCtrl :: SetOriginalColor

Définit la couleur sélectionnée initiale.

```cpp
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>Paramètres

*ref*<br/>
dans Valeur de couleur RVB.

### <a name="remarks"></a>Notes

Appelez cette méthode lorsque le contrôle de sélecteur de couleurs est initialisé.

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a> CMFCColorPickerCtrl :: SetPalette

Définit la palette de couleurs actuelle.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Paramètres

*pPalette*<br/>
dans Pointeur vers une palette de couleurs.

### <a name="remarks"></a>Notes

La palette de couleurs définit le tableau de couleurs présenté dans le contrôle de sélecteur de couleurs.

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a> CMFCColorPickerCtrl :: SetSaturation

Modifie la saturation de la couleur actuellement sélectionnée.

```cpp
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>Paramètres

*Saturation*<br/>
dans Valeur de saturation.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a> CMFCColorPickerCtrl :: SetType

Définit le type de contrôle de sélecteur de couleurs à afficher.

```cpp
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>Paramètres

*colorType*<br/>
dans Type de contrôle de sélecteur de couleurs.

Les types sont définis par l' `CMFCColorPickerCtrl::COLORTYPE` énumération. Les types possibles sont LUMINANCE, PICKER, HEX et HEX_GREYSCALE. Le type par défaut est PICKER.

### <a name="remarks"></a>Notes

Pour spécifier un type de contrôle de sélecteur de couleurs, appelez cette méthode avant la création du contrôle Windows.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md)
