---
title: Classe de CMFCColorPickerCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3d4c8af6373f2b526c07ee570f4be878bd073d4
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042041"
---
# <a name="cmfccolorpickerctrl-class"></a>Classe de CMFCColorPickerCtrl
La `CMFCColorPickerCtrl` classe fournit une fonctionnalité pour un contrôle qui est utilisé pour sélectionner des couleurs.  
  
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
|[CMFCColorPickerCtrl::GetHue](#gethue)|Récupère le composant de teinte de la couleur que l’utilisateur sélectionne.|  
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Récupère le composant de luminance de la couleur que l’utilisateur sélectionne.|  
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Récupère le composant de saturation de la couleur que l’utilisateur sélectionne.|  
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Définit la couleur actuelle de la couleur définie par les composants de couleur RVB spécifiés ou hexagone de la cellule spécifiée.|  
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Définit la couleur actuelle à la valeur de couleur RVB spécifiée.|  
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Définit la couleur actuelle à la valeur de couleur TSL spécifiée.|  
|[CMFCColorPickerCtrl::SetHue](#sethue)|Modifie le composant teinte de la couleur actuellement sélectionnée.|  
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Modifie le composant de luminance de la couleur actuellement sélectionnée.|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Définit la largeur de la barre de luminance dans le contrôle de sélecteur de couleurs.|  
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Définit la couleur sélectionnée initiale.|  
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Définit la palette de couleurs.|  
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Modifie le composant saturation de la couleur actuellement sélectionnée.|  
|[CMFCColorPickerCtrl::SetType](#settype)|Définit le type de contrôle de sélecteur de couleurs à afficher.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Appelé par l’infrastructure avant l’affichage d’un curseur qui pointe vers la couleur sélectionnée.|  
  
## <a name="remarks"></a>Notes  
 Couleurs standard sont sélectionnées à partir d’une palette de couleurs hexagonal et couleurs personnalisées sont sélectionnés à partir d’une barre de luminance où les couleurs sont spécifiées à l’aide de la notation rouge/vert/bleu ou notation de teinte/satuaration/luminance.  
  
 L’illustration suivante représente plusieurs `CMFCColorPickerCtrl` objets.  
  
 ![Boîte de dialogue CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "colorpicker")  
  
 Le `CMFCColorPickerCtrl` prend en charge deux paires de styles. Les styles HEX_GREYSCALE et HEX conviennent pour la sélection de couleurs standard. Les styles de sélecteur et LUMINANCE sont appropriés pour la sélection de couleur personnalisée.  
  
 Les étapes suivantes pour intégrer la `CMFCColorPickerCtrl` contrôle dans votre boîte de dialogue :  
  
1.  Si vous utilisez le **ClassWizard**, insérer un nouveau contrôle de bouton dans le modèle de boîte de dialogue (étant donné que la `CMFCColorPickerCtrl` classe est héritée de la `CButton` classe).  
  
2.  Insérer une variable de membre qui est associée au contrôle bouton Nouveau dans votre classe de boîte de dialogue. Puis modifiez le type de variable à partir de `CButton` à `CMFCColorPickerCtrl`.  
  
3.  Insérer le `WM_INITDIALOG` Gestionnaire de messages pour la classe de boîte de dialogue. Dans le Gestionnaire de définir le type, la palette et la couleur de sélectionné initiale de la `CMFCColorPickerCtrl` contrôle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer un `CMFCColorPickerCtrl` objet à l’aide de différentes méthodes de la `CMFCColorPickerCtrl` classe. L’exemple montre comment définir le type du contrôle de sélecteur et comment définir sa couleur de teinte, luminance et saturation. L’exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcolorpickerctrl.h  
  
##  <a name="cmfccolorpickerctrl"></a>  CMFCColorPickerCtrl::CMFCColorPickerCtrl  
 Construit un objet `CMFCColorPickerCtrl`.  
  
```  
CMFCColorPickerCtrl();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="drawcursor"></a>  CMFCColorPickerCtrl::DrawCursor  
 Appelé par l’infrastructure avant l’affichage d’un curseur qui pointe vers la couleur sélectionnée.  
  
```  
virtual void DrawCursor(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *rect*  
 Spécifie une zone rectangulaire autour de la couleur sélectionnée.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode lorsque vous avez besoin modifier la forme du curseur qui pointe vers la couleur sélectionnée.  
  
##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor  
 Récupère la couleur que l’utilisateur sélectionne.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur RVB de la couleur sélectionnée.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS  
 Récupère les valeurs de teinte, de luminance et de saturation de la couleur que l’utilisateur sélectionne.  
  
```  
void GetHLS(
    double* hue,  
    double* luminance,  
    double* saturation);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *teinte*  
 Pointeur vers une variable de type double qui reçoit des informations de la teinte.  
  
 [out] *luminance*  
 Pointeur vers une variable de type double qui reçoit des informations de luminance.  
  
 [out] *saturation*  
 Pointeur vers une variable de type double qui reçoit des informations de saturation.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue  
 Récupère le composant de teinte de la couleur que l’utilisateur sélectionne.  
  
```  
double GetHue() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le composant teinte de la couleur sélectionnée.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance  
 Récupère le composant de luminance de la couleur que l’utilisateur sélectionne.  
  
```  
double GetLuminance() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le composant de luminance de la couleur sélectionnée.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation  
 Récupère la valeur de saturation de la couleur que l’utilisateur sélectionne.  
  
```  
double GetSaturation() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le composant de saturation de la couleur sélectionnée.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon  
 Définit la couleur actuelle de la couleur définie par les composants de couleur RVB spécifiés ou hexagone de la cellule spécifiée.  
  
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
 [in] *R*  
 Le composant de couleur rouge.  
  
 [in] *G*  
 Le composant de couleur verte.  
  
 [in] *B*  
 Le composant bleu.  
  
 [in] *x*  
 Coordonnée x du curseur, qui pointe vers un hexagone de cellule.  
  
 [in] *y*  
 Coordonnée y du curseur, qui pointe vers un hexagone de cellule.  
  
### <a name="return-value"></a>Valeur de retour  
 La deuxième surcharge de cette méthode retourne toujours `FALSE`.  
  
### <a name="remarks"></a>Notes  
 La première surcharge de cette méthode définit la couleur qui correspond au contrôle de sélection de couleur couleur actuel spécifiée de composants de couleur rouge, vert et bleu.  
  
 La deuxième surcharge de cette méthode définit la couleur actuelle de la couleur de l’Hexagone de cellule est désigné par l’emplacement du curseur spécifié.  
  
##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor  
 Définit la couleur actuelle à la valeur de couleur RVB spécifiée.  
  
```  
void SetColor(COLORREF Color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *Couleur*  
 Une valeur de couleur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS  
 Définit la couleur actuelle à la valeur de couleur TSL spécifiée.  
  
```  
void SetHLS(
    double hue,  
    double luminance,  
    double saturation,  
    BOOL bInvalidate=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *teinte*  
 Une valeur de teinte.  
  
 [in] *luminance*  
 Une valeur de luminance.  
  
 [in] *saturation*  
 Une valeur de saturation.  
  
 [in] *bInvalidate*  
 `TRUE` Pour forcer la fenêtre à mettre à jour immédiatement la nouvelle couleur ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue  
 Modifie la teinte de la couleur actuellement sélectionnée.  
  
```  
void SetHue(double Hue);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *Teinte*  
 Une valeur de teinte.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance  
 Modifie la luminance de la couleur actuellement sélectionnée.  
  
```  
void SetLuminance(double Luminance);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *Luminance*  
 Une valeur de luminance.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth  
 Définit la largeur de la barre de luminance dans le contrôle de sélecteur de couleurs.  
  
```  
void SetLuminanceBarWidth(int w);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *w*  
 La largeur de la barre de luminance en pixels.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour redimensionner la barre de luminance, qui se trouve sur le **personnalisé** onglet de contrôle de sélecteur de couleurs. Le *w* paramètre spécifie la nouvelle largeur de la barre de luminance. La valeur de la largeur est ignorée si elle dépasse trois quarts de la largeur de la zone cliente.  
  
##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor  
 Définit la couleur sélectionnée initiale.  
  
```  
void SetOriginalColor(COLORREF ref);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *ref*  
 Une valeur de couleur RVB.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode lorsque le contrôle de sélecteur de couleurs est initialisé.  
  
##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette  
 Définit la palette de couleurs.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pPalette*  
 Pointeur vers une palette de couleurs.  
  
### <a name="remarks"></a>Notes  
 La palette de couleurs définit le tableau de couleurs qui s’affiche dans le contrôle de sélecteur de couleurs.  
  
##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation  
 Modifie la saturation de la couleur actuellement sélectionnée.  
  
```  
void SetSaturation(double Saturation);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *Saturation*  
 Une valeur de saturation.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType  
 Définit le type de contrôle de sélecteur de couleurs à afficher.  
  
```  
void SetType(COLORTYPE colorType);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *colorType*  
 Un type de contrôle de sélecteur de couleurs.  
  
 Les types sont définis par le `CMFCColorPickerCtrl::COLORTYPE` énumération. Les types possibles sont `LUMINANCE`, `PICKER`, `HEX` et `HEX_GREYSCALE`. Le type par défaut est `PICKER`.  
  
### <a name="remarks"></a>Notes  
 Pour spécifier un type de contrôle de sélecteur de couleur, appelez cette méthode avant la création du contrôle Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md)
