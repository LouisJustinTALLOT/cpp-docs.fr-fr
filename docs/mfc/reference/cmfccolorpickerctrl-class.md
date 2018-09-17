---
title: CMFCColorPickerCtrl, classe | Microsoft Docs
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
ms.openlocfilehash: 0ea0bf6ed8361419af3519a41edbe6bb3c4b4a77
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725658"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl, classe
Le `CMFCColorPickerCtrl` classe fournit des fonctionnalités pour un contrôle qui est utilisé pour sélectionner des couleurs.  
  
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
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Définit la couleur actuelle à la couleur définie par les composants de couleur RVB spécifiés ou hexagone de la cellule spécifiée.|  
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Définit la couleur actuelle à la valeur de couleur RVB spécifiée.|  
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Définit la couleur actuelle à la valeur de couleur HLS spécifiée.|  
|[CMFCColorPickerCtrl::SetHue](#sethue)|Modifie le composant de teinte de la couleur actuellement sélectionnée.|  
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Modifie le composant de luminance de la couleur actuellement sélectionnée.|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Définit la largeur de la barre de luminance dans le contrôle de sélecteur de couleur.|  
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Définit la couleur sélectionnée initiale.|  
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Définit la palette de couleurs actuelle.|  
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Modifie le composant de saturation de la couleur actuellement sélectionnée.|  
|[CMFCColorPickerCtrl::SetType](#settype)|Définit le type de contrôle de sélecteur de couleur à afficher.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Appelé par l’infrastructure avant un curseur qui pointe vers la couleur sélectionnée s’affiche.|  
  
## <a name="remarks"></a>Notes  
 Couleurs standard sont sélectionnées à partir d’une palette de couleurs hexagonale, et des couleurs personnalisées sont sélectionnées à partir d’une barre de luminance où les couleurs sont spécifiées à l’aide de la notation rouge/vert/bleu ou notation de teinte/satuaration/luminance.  
  
 L’illustration suivante représente plusieurs `CMFCColorPickerCtrl` objets.  
  
 ![Boîte de dialogue CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "colorpicker")  
  
 Le `CMFCColorPickerCtrl` prend en charge deux paires de styles. Les styles HEX et HEX_GREYSCALE sont appropriés pour la sélection de couleur standard. Les styles de sélecteur et la LUMINANCE sont appropriés pour la sélection de couleur personnalisée.  
  
 Procédez comme suit pour incorporer le `CMFCColorPickerCtrl` contrôle dans votre boîte de dialogue :  
  
1.  Si vous utilisez le **ClassWizard**, insérer un nouveau contrôle de bouton dans votre modèle de boîte de dialogue (étant donné que le `CMFCColorPickerCtrl` classe est héritée de la `CButton` classe).  
  
2.  Insérer une variable de membre qui est associée avec le nouveau contrôle de bouton dans votre classe de boîte de dialogue. Puis modifiez le type de variable à partir de `CButton` à `CMFCColorPickerCtrl`.  
  
3.  Insérer le `WM_INITDIALOG` Gestionnaire de messages pour la classe de boîte de dialogue. Dans le gestionnaire, définissez le type, la palette et la couleur sélectionnée initiale de la `CMFCColorPickerCtrl` contrôle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer un `CMFCColorPickerCtrl` objet à l’aide de différentes méthodes de la `CMFCColorPickerCtrl` classe. L’exemple montre comment définir le type du contrôle de sélecteur et comment définir sa couleur, la teinte, la luminance et la saturation. L’exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
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
 Appelé par l’infrastructure avant un curseur qui pointe vers la couleur sélectionnée s’affiche.  
  
```  
virtual void DrawCursor(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Paramètres  
*contrôleur de domaine principal*<br/>
[in] Pointeur vers un contexte de périphérique.  
  
*Rect*<br/>
[in] Spécifie une zone rectangulaire autour de la couleur sélectionnée.  
  
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
*HUE*<br/>
[out] Pointeur vers une variable de type double qui reçoit les informations de hue.  
  
*luminance*<br/>
[out] Pointeur vers une variable de type double qui reçoit les informations de luminance.  
  
*saturation*<br/>
[out] Pointeur vers une variable de type double qui reçoit les informations de saturation.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue  
 Récupère le composant de teinte de la couleur que l’utilisateur sélectionne.  
  
```  
double GetHue() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le composant de teinte de la couleur sélectionnée.  
  
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
 Définit la couleur actuelle à la couleur définie par les composants de couleur RVB spécifiés ou hexagone de la cellule spécifiée.  
  
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
[in] Le composant de couleur rouge.  
  
*G*<br/>
[in] Le composant de couleur verte.  
  
*B*<br/>
[in] Le composant de couleur bleue.  
  
*x*<br/>
[in] Coordonnée x du curseur, qui pointe vers un hexagone de cellule.  
  
*y*<br/>
[in] Coordonnée y du curseur, qui pointe vers un hexagone de cellule.  
  
### <a name="return-value"></a>Valeur de retour  
 La deuxième surcharge de cette méthode retourne toujours FALSE.  
  
### <a name="remarks"></a>Notes  
 La première surcharge de cette méthode définit la couleur qui correspond au contrôle de sélection de couleur couleur actuel spécifié du composants de couleur rouge, vert et bleu.  
  
 La deuxième surcharge de cette méthode définit la couleur actuelle de la couleur de l’Hexagone cellule désignée par l’emplacement du curseur spécifié.  
  
##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor  
 Définit la couleur actuelle à la valeur de couleur RVB spécifiée.  
  
```  
void SetColor(COLORREF Color);
```  
  
### <a name="parameters"></a>Paramètres  
*Couleur*<br/>
[in] Une valeur de couleur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS  
 Définit la couleur actuelle à la valeur de couleur HLS spécifiée.  
  
```  
void SetHLS(
    double hue,  
    double luminance,  
    double saturation,  
    BOOL bInvalidate=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
*HUE*<br/>
[in] Une valeur de teinte.  
  
*luminance*<br/>
[in] Une valeur de luminance.  
  
*saturation*<br/>
[in] Une valeur de saturation.  
  
*bInvalidate*<br/>
[in] TRUE pour forcer la fenêtre Mettre à jour immédiatement à la nouvelle couleur ; Sinon, FALSE. La valeur par défaut est TRUE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue  
 Modifie la teinte de la couleur actuellement sélectionnée.  
  
```  
void SetHue(double Hue);
```  
  
### <a name="parameters"></a>Paramètres  
*HUE*<br/>
[in] Une valeur de teinte.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance  
 Modifie la luminance de la couleur actuellement sélectionnée.  
  
```  
void SetLuminance(double Luminance);
```  
  
### <a name="parameters"></a>Paramètres  
*Luminance*<br/>
[in] Une valeur de luminance.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth  
 Définit la largeur de la barre de luminance dans le contrôle de sélecteur de couleur.  
  
```  
void SetLuminanceBarWidth(int w);
```  
  
### <a name="parameters"></a>Paramètres  
*w*<br/>
[in] Largeur de la barre de luminance mesurée en pixels.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour redimensionner la barre de luminance, ce qui se trouve sur le **personnalisé** onglet du contrôle de sélecteur de couleur. Le *w* paramètre spécifie la nouvelle largeur de la barre de luminance. La valeur de la largeur est ignorée si elle dépasse trois quarts de la largeur de la zone cliente.  
  
##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor  
 Définit la couleur sélectionnée initiale.  
  
```  
void SetOriginalColor(COLORREF ref);
```  
  
### <a name="parameters"></a>Paramètres  
*ref*<br/>
[in] Une valeur de couleur RVB.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode lorsque le contrôle de sélecteur de couleurs est initialisé.  
  
##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette  
 Définit la palette de couleurs actuelle.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Paramètres  
*pPalette*<br/>
[in] Pointeur vers une palette de couleurs.  
  
### <a name="remarks"></a>Notes  
 La palette de couleurs définit le tableau de couleurs qui est présenté dans le contrôle de sélecteur de couleur.  
  
##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation  
 Modifie la saturation de la couleur actuellement sélectionnée.  
  
```  
void SetSaturation(double Saturation);
```  
  
### <a name="parameters"></a>Paramètres  
*Saturation*<br/>
[in] Une valeur de saturation.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType  
 Définit le type de contrôle de sélecteur de couleur à afficher.  
  
```  
void SetType(COLORTYPE colorType);
```  
  
### <a name="parameters"></a>Paramètres  
*colorType*<br/>
[in] Un type de contrôle de sélecteur de couleur.  
  
 Les types sont définis par le `CMFCColorPickerCtrl::COLORTYPE` énumération. Les types possibles sont LUMINANCE, sélecteur, HEX et HEX_GREYSCALE. Le type par défaut est le sélecteur.  
  
### <a name="remarks"></a>Notes  
 Pour spécifier un type de contrôle de sélecteur de couleur, appelez cette méthode avant que le contrôle de Windows est créé.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md)
