---
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
ms.openlocfilehash: c3c11db448ab31324367b7f314cd6bfe44c2e96d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367685"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl, classe

La `CMFCColorPickerCtrl` classe fournit des fonctionnalités pour un contrôle qui est utilisé pour sélectionner les couleurs.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Construit un objet `CMFCColorPickerCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Récupère la couleur que l’utilisateur sélectionne.|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Récupère les valeurs de teinte, de luminance et de saturation de la couleur que l’utilisateur sélectionne.|
|[CMFCColorPickerCtrl::GetHue](#gethue)|Récupère le composant teinte de la couleur que l’utilisateur sélectionne.|
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Récupère le composant de luminance de la couleur que l’utilisateur sélectionne.|
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Récupère le composant de saturation de la couleur que l’utilisateur sélectionne.|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Définit la couleur actuelle à la couleur définie par les composants de couleur RGB spécifiés ou l’hexagone cellulaire spécifié.|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Définit la couleur actuelle à la valeur de couleur RGB spécifiée.|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Définit la couleur actuelle à la valeur de couleur spécifiée HLS.|
|[CMFCColorPickerCtrl::SetHue](#sethue)|Change le composant de teinte de la couleur actuellement sélectionnée.|
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Modifications du composant de luminance de la couleur actuellement sélectionnée.|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Définit la largeur de la barre de luminance dans le contrôle du cueilleur de couleurs.|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Définit la couleur sélectionnée initiale.|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Définit la palette de couleurs actuelle.|
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Modifie le composant de saturation de la couleur actuellement sélectionnée.|
|[CMFCColorPickerCtrl::SetType](#settype)|Définit le type de contrôle de cueilleur de couleur pour afficher.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Appelé par le cadre avant qu’un curseur qui indique la couleur sélectionnée est affiché.|

## <a name="remarks"></a>Notes

Les couleurs standard sont sélectionnées à partir d’une palette de couleurs hexagonales, et les couleurs personnalisées sont sélectionnées à partir d’une barre de luminance où les couleurs sont spécifiées en utilisant soit la notation rouge/vert/bleu ou la notation de teinte/satuaration/luminance.

L’illustration suivante `CMFCColorPickerCtrl` représente plusieurs objets.

![Boîte de dialogue CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "Boîte de dialogue CMFCColorPickerCtrl")

Le `CMFCColorPickerCtrl` supporte deux paires de styles. Les styles HEX et HEX_GREYSCALE sont appropriés pour la sélection des couleurs standard. Les styles PICKER et LUMINANCE conviennent à la sélection personnalisée des couleurs.

Effectuez les étapes `CMFCColorPickerCtrl` suivantes pour intégrer le contrôle dans votre boîte de dialogue :

1. Si vous utilisez le **ClassWizard**, insérez un nouveau `CMFCColorPickerCtrl` contrôle de `CButton` bouton dans votre modèle de boîte de dialogue (parce que la classe est héritée de la classe).

1. Insérez une variable de membre associée au nouveau contrôle du bouton dans votre classe de boîte de dialogue. Ensuite, changez `CButton` le `CMFCColorPickerCtrl`type variable de .

1. Insérez le `WM_INITDIALOG` gestionnaire de message pour la classe de boîte de dialogue. Dans le gestionnaire, définissez le type, la `CMFCColorPickerCtrl` palette et la couleur choisie initiale du contrôle.

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCColorPickerCtrl` configurer un objet `CMFCColorPickerCtrl` en utilisant différentes méthodes dans la classe. L’exemple montre comment définir le type de contrôle du cueilleur, et comment définir sa couleur, sa teinte, sa luminance et sa saturation. L’exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxcolorpickerctrl.h

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a>CMFCColorPickerCtrl::CMFCColorPickerCtrl

Construit un objet `CMFCColorPickerCtrl`.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a>CMFCColorPickerCtrl::DrawCursor

Appelé par le cadre avant qu’un curseur qui indique la couleur sélectionnée est affiché.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Spécifie une zone rectangulaire autour de la couleur sélectionnée.

### <a name="remarks"></a>Notes

Remplacer cette méthode lorsque vous avez besoin de changer la forme du curseur qui pointe vers la couleur sélectionnée.

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a>CMFCColorPickerCtrl::GetColor

Récupère la couleur que l’utilisateur sélectionne.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur RGB de la couleur sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a>CMFCColorPickerCtrl::GetHLS

Récupère les valeurs de teinte, de luminance et de saturation de la couleur que l’utilisateur sélectionne.

```
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>Paramètres

*Teinte*<br/>
[out] Pointeur vers une variable de type double qui reçoit des informations de teinte.

*Luminance*<br/>
[out] Pointeur vers une variable de type double qui reçoit des informations de luminance.

*Saturation*<br/>
[out] Pointeur vers une variable de type double qui reçoit des informations de saturation.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a>CMFCColorPickerCtrl::GetHue

Récupère le composant teinte de la couleur que l’utilisateur sélectionne.

```
double GetHue() const;
```

### <a name="return-value"></a>Valeur de retour

Le composant de teinte de la couleur sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a>CMFCColorPickerCtrl::GetLuminance

Récupère le composant de luminance de la couleur que l’utilisateur sélectionne.

```
double GetLuminance() const;
```

### <a name="return-value"></a>Valeur de retour

Le composant de luminance de la couleur sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a>CMFCColorPickerCtrl::GetSaturation

Récupère la valeur de saturation de la couleur que l’utilisateur sélectionne.

```
double GetSaturation() const;
```

### <a name="return-value"></a>Valeur de retour

Le composant de saturation de la couleur sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a>CMFCColorPickerCtrl::SelectCellHexagon

Définit la couleur actuelle à la couleur définie par les composants de couleur RGB spécifiés ou l’hexagone cellulaire spécifié.

```
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
[dans] Le composant de couleur rouge.

*G*<br/>
[dans] Le composant de couleur verte.

*B*<br/>
[dans] Le composant de couleur bleue.

*X*<br/>
[dans] Le x-coordonner le curseur, qui pointe vers un hexagone cellulaire.

*y*<br/>
[dans] Le y-coordinate du curseur, qui pointe vers un hexagone cellulaire.

### <a name="return-value"></a>Valeur de retour

La deuxième surcharge de cette méthode renvoie toujours FALSE.

### <a name="remarks"></a>Notes

La première surcharge de cette méthode définit la couleur actuelle à la couleur qui correspond aux composants spécifiés de couleur rouge, verte et bleue spécifiés du contrôle de sélection des couleurs.

La deuxième surcharge de cette méthode définit la couleur actuelle à la couleur de l’hexagone cellulaire qui est pointée vers l’emplacement spécifié du curseur.

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a>CMFCColorPickerCtrl::SetColor

Définit la couleur actuelle à la valeur de couleur RGB spécifiée.

```
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>Paramètres

*Color*<br/>
[dans] Une valeur de couleur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a>CMFCColorPickerCtrl::SetHLS

Définit la couleur actuelle à la valeur de couleur spécifiée HLS.

```
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>Paramètres

*Teinte*<br/>
[dans] Une valeur de teinte.

*Luminance*<br/>
[dans] Une valeur de luminance.

*Saturation*<br/>
[dans] Une valeur de saturation.

*bInvalidate*<br/>
[dans] VRAI pour forcer la fenêtre à mettre immédiatement à jour à la nouvelle couleur; autrement, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a>CMFCColorPickerCtrl::SetHue

Change la teinte de la couleur actuellement sélectionnée.

```
void SetHue(double Hue);
```

### <a name="parameters"></a>Paramètres

*Teinte*<br/>
[dans] Une valeur de teinte.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a>CMFCColorPickerCtrl::SetLuminance

Modifie la luminosité de la couleur actuellement sélectionnée.

```
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>Paramètres

*Luminance*<br/>
[dans] Une valeur de luminance.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a>CMFCColorPickerCtrl::SetLuminanceBarWidth

Définit la largeur de la barre de luminance dans le contrôle du cueilleur de couleurs.

```
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>Paramètres

*W*<br/>
[dans] La largeur de la barre de luminance mesurée en pixels.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour resize la barre de luminance, qui est sur **l’onglet Personnalisé** du contrôle de cueilleur de couleur. Le paramètre *w* spécifie la nouvelle largeur de la barre de luminance. La valeur de largeur est ignorée si elle dépasse les trois quarts de la largeur de la zone client.

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a>CMFCColorPickerCtrl::SetOriginalColor

Définit la couleur sélectionnée initiale.

```
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>Paramètres

*ref*<br/>
[dans] Une valeur de couleur RGB.

### <a name="remarks"></a>Notes

Appelez cette méthode lorsque le contrôle du cueilleur de couleurs est initialisé.

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a>CMFCColorPickerCtrl::SetPalette

Définit la palette de couleurs actuelle.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Paramètres

*pPalette (pPalette)*<br/>
[dans] Pointeur vers une palette de couleurs.

### <a name="remarks"></a>Notes

La palette de couleurs définit la gamme de couleurs qui est présentée dans le contrôle de cueilleur de couleurs.

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a>CMFCColorPickerCtrl::SetSaturation

Modifie la saturation de la couleur actuellement sélectionnée.

```
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>Paramètres

*Saturation*<br/>
[dans] Une valeur de saturation.

### <a name="remarks"></a>Notes

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a>CMFCColorPickerCtrl::SetType

Définit le type de contrôle de cueilleur de couleur pour afficher.

```
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>Paramètres

*Colortype*<br/>
[dans] Un type de contrôle de cueilleur de couleur.

Les types sont `CMFCColorPickerCtrl::COLORTYPE` définis par l’énumération. Les types possibles sont LUMINANCE, PICKER, HEX et HEX_GREYSCALE. Le type par défaut est PICKER.

### <a name="remarks"></a>Notes

Pour spécifier un type de contrôle de cueilleur de couleur, appelez cette méthode avant la création du contrôle Windows.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md)
