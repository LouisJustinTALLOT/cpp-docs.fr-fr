---
description: 'En savoir plus sur : classe CDrawingManager'
title: CDrawingManager, classe
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: b30218dd41e3591c4a39df078bb19e3ac653ba1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184788"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager, classe

La `CDrawingManager` classe implémente des algorithmes de dessin complexes.

## <a name="syntax"></a>Syntaxe

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Construit un objet `CDrawingManager`.|
|`CDrawingManager::~CDrawingManager`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDrawingManager :: CreateBitmap_32](#createbitmap_32)|Crée une image bitmap indépendante du périphérique 32 (DIB) que les applications peuvent écrire directement.|
|[CDrawingManager ::D rawAlpha](#drawalpha)|Affiche les bitmaps qui ont des pixels transparents ou translucides.|
|[CDrawingManager ::D rawRotated](#drawrotated)|Fait pivoter un contenu DC source à l’intérieur du rectangle donné par +/-90 degrés|
|[CDrawingManager ::D rawEllipse](#drawellipse)|Dessine une ellipse avec les couleurs de remplissage et de bordure fournies.|
|[CDrawingManager ::D rawGradientRing](#drawgradientring)|Dessine un anneau et le remplit avec un dégradé de couleur.|
|[CDrawingManager ::D rawLine, CDrawingManager ::D rawLineA](#drawline_cdrawingmanager__drawlinea)|Dessine une ligne.|
|[CDrawingManager ::D rawRect](#drawrect)|Dessine un rectangle avec les couleurs de remplissage et de bordure fournies.|
|[CDrawingManager ::D rawShadow](#drawshadow)|Dessine une ombre pour une zone rectangulaire.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Remplit une zone rectangulaire avec deux dégradés de couleur.|
|[CDrawingManager::FillGradient](#fillgradient)|Remplit une zone rectangulaire avec un dégradé de couleur spécifié.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Remplit une zone rectangulaire avec un dégradé de couleur spécifié. La direction de la modification de couleur du dégradé est également spécifiée.|
|[CDrawingManager::GrayRect](#grayrect)|Remplit un rectangle avec une couleur grise spécifiée.|
|[CDrawingManager::HighlightRect](#highlightrect)|Met en surbrillance une zone rectangulaire.|
|[CDrawingManager :: HLStoRGB_ONE](#hlstorgb_one)|Convertit une couleur d’une représentation TLS en une représentation RVB.|
|[CDrawingManager :: HLStoRGB_TWO](#hlstorgb_two)|Convertit une couleur d’une représentation TLS en une représentation RVB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Convertit une couleur d’une représentation HSV en une représentation RVB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Méthode d’assistance qui convertit une valeur de teinte en composant rouge, vert ou bleu.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Retourne une zone rectangulaire.|
|[CDrawingManager ::P ixelAlpha](#pixelalpha)|Méthode d’assistance qui détermine la couleur finale d’un pixel semi-transparent.|
|[CDrawingManager ::P repareShadowMask](#prepareshadowmask)|Crée une image bitmap qui peut être utilisée comme une ombre.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Convertit une couleur d’une représentation RVB en une représentation TSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Convertit une couleur d’une représentation RVB en représentation HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Méthode d’assistance qui colore un pixel partiellement transparent dans une bitmap.|
|[CDrawingManager :: SetPixel](#setpixel)|Méthode d’assistance qui modifie un seul pixel dans une image bitmap avec la couleur spécifiée.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combine deux couleurs en fonction d’un rapport pondéré.|

## <a name="remarks"></a>Notes

La `CDrawingManager` classe fournit des fonctions permettant de dessiner des ombres, des dégradés de couleur et des rectangles mis en surbrillance. Il effectue également la fusion alpha. Vous pouvez utiliser cette classe pour modifier directement l’interface utilisateur de votre application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdrawmanager. h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a> CDrawingManager::CDrawingManager

Construit un objet [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) .

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Paramètres

*métafichier*<br/>
dans Référence à un contexte de périphérique (Device Context). `CDrawingManager`Utilise ce contexte pour dessiner.

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a> CDrawingManager :: CreateBitmap_32

Crée une image bitmap indépendante du périphérique 32 (DIB) que les applications peuvent écrire directement.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>Paramètres

*corps*\
dans Paramètre [CSize](../../atl-mfc-shared/reference/csize-class.md) qui indique la taille de l’image bitmap.

*pBits*\
à Pointeur vers un pointeur de données qui reçoit l’emplacement des valeurs de bit du DIB.

*pixels*\
Handle vers la bitmap d’origine

*clrTransparent*\
Valeur RVB spécifiant la couleur transparente de l’image bitmap d’origine.

### <a name="return-value"></a>Valeur renvoyée

Handle vers l’image bitmap DIB nouvellement créée si cette méthode réussit ; Sinon, NULL.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la création d’une bitmap DIB, consultez [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a> CDrawingManager ::D rawAlpha

Affiche les bitmaps qui ont des pixels transparents ou translucides.

```cpp
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Paramètres

*pDstDC*<br/>
dans Pointeur vers le contexte de périphérique (Device Context) pour la destination.

*rectDst*<br/>
dans Rectangle de destination.

*pSrcDC*<br/>
dans Pointeur vers le contexte de périphérique pour la source.

*rectSrc*<br/>
dans Rectangle source.

### <a name="remarks"></a>Notes

Cette méthode effectue une fusion alpha pour deux bitmaps. Pour plus d’informations sur la fusion alpha, consultez [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) dans le SDK Windows.

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a> CDrawingManager ::D rawEllipse

Dessine une ellipse avec les couleurs de remplissage et de bordure fournies.

```cpp
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Rectangle englobant pour l’ellipse.

*clrFill*<br/>
dans Couleur utilisée par cette méthode pour remplir l’ellipse.

*clrLine*<br/>
dans Couleur utilisée par cette méthode comme bordure de l’ellipse.

### <a name="remarks"></a>Notes

Cette méthode retourne sans dessiner une ellipse si l’une des couleurs est définie sur-1. Elle retourne également sans dessiner une ellipse si l’une des dimensions du rectangle englobant est 0.

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a> CDrawingManager ::D rawGradientRing

Dessine un anneau et le remplit avec un dégradé de couleur.

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Paramètre [CRect](../../atl-mfc-shared/reference/crect-class.md) qui spécifie la limite du cycle de dégradé.

*colorStart*<br/>
dans Première couleur du dégradé.

*colorFinish*<br/>
dans Dernière couleur du dégradé.

*colorBorder*<br/>
dans Couleur de la bordure.

*nAngle*<br/>
dans Paramètre qui spécifie l’angle de dessin dégradé initial. Cette valeur doit être comprise entre 0 et 360.

*nWidth*<br/>
dans Largeur de la bordure de l’anneau.

*clrFace*<br/>
dans Couleur de l’intérieur de l’anneau.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le rectangle défini par *Rect* doit avoir une largeur d’au moins 5 pixels et une hauteur de 5 pixels.

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a> CDrawingManager ::D rawLine, CDrawingManager ::D rawLineA

Dessine une ligne.

```cpp
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*x1*\
dans Coordonnée x où commence la ligne.

*Y1*\
dans Coordonnée y où commence la ligne.

*x2*\
dans Coordonnée x où la ligne se termine.

*Y2*\
dans Coordonnée y où la ligne se termine.

*clrLine*\
dans Couleur de la ligne.

### <a name="remarks"></a>Notes

Cette méthode échoue si *clrLine* est égal à-1.

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a> CDrawingManager ::D rawRect

Dessine un rectangle avec les couleurs de remplissage et de bordure fournies.

```cpp
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Limites du rectangle.

*clrFill*<br/>
dans Couleur utilisée par cette méthode pour remplir le rectangle.

*clrLine*<br/>
dans Couleur utilisée par cette méthode pour la bordure du rectangle.

### <a name="remarks"></a>Notes

Cette méthode retourne sans dessiner de rectangle si l’une des couleurs est définie sur-1. Elle retourne également si l’une des dimensions du rectangle est égale à 0.

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a> CDrawingManager ::D rawShadow

Dessine une ombre pour une zone rectangulaire.

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Zone rectangulaire dans votre application. Le gestionnaire de dessins dessinera une ombre sous cette zone.

*nDepth*<br/>
dans Largeur et hauteur de l’ombre.

*iMinBrightness*<br/>
dans Luminosité minimale de l’ombre.

*iMaxBrightness*<br/>
dans Luminosité maximale de l’ombre.

*pBmpSaveBottom*<br/>
dans Pointeur vers une image bitmap qui contient l’image pour la partie inférieure de l’ombre.

*pBmpSaveRight*<br/>
dans Pointeur vers une bitmap qui contient l’image de l’ombre dessinée sur le côté droit du rectangle.

*clrBase*<br/>
dans Couleur de l’ombre.

*bRightShadow*<br/>
dans Paramètre booléen qui indique la façon dont l’ombre est dessinée. Si *bRightShadow* est `TRUE` , `DrawShadow` dessine une ombre sur le côté droit du rectangle.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez fournir deux bitmaps valides pour les ombres inférieures et droites à l’aide des paramètres *pBmpSaveBottom* et *pBmpSaveRight*. Si ces objets [CBitmap](../../mfc/reference/cbitmap-class.md) ont un objet GDI attaché, `DrawShadow` utilisera ces bitmaps comme ombres. Si les `CBitmap` paramètres n’ont pas d’objet GDI attaché, `DrawShadow` dessine l’ombre et joint les bitmaps aux paramètres. Dans les appels ultérieurs à `DrawShadow` , vous pouvez fournir ces bitmaps pour accélérer le processus de dessin. Pour plus d’informations sur la `CBitmap` classe et les objets GDI, consultez [objets graphiques](../../mfc/graphic-objects.md).

Si l’un de ces paramètres est `NULL` , `DrawShadow` dessine automatiquement l’ombre.

Si vous affectez à *bRightShadow* la valeur false, l’ombre est dessinée en dessous et à gauche de la zone rectangulaire.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `DrawShadow` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de l’exemple de démonstration de la [feuille prop](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a> CDrawingManager::Fill4ColorsGradient

Remplit une zone rectangulaire avec deux dégradés de couleur.

```cpp
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Rectangle à remplir.

*colorStart1*<br/>
dans Couleur initiale du dégradé de la première couleur.

*colorFinish1*<br/>
dans Couleur finale du dégradé de la première couleur.

*colorStart2*<br/>
dans Couleur initiale du deuxième dégradé de couleur.

*colorFinish2*<br/>
dans Couleur finale du deuxième dégradé de couleur.

*bHorz*<br/>
dans Paramètre booléen qui indique si `Fill4ColorsGradient` colore un dégradé horizontal ou vertical. TRUE indique un dégradé horizontal.

*nPercentage*<br/>
dans Entier de 0-100. Cette valeur indique le pourcentage du rectangle à remplir avec le premier dégradé de couleur.

### <a name="remarks"></a>Notes

Lorsqu’un rectangle est rempli avec deux dégradés de couleur, ils sont situés au-dessus l’un de l’autre ou l’un à côté de l’autre, en fonction de la valeur de *bHorz*. Chaque dégradé de couleur est calculé indépendamment avec la méthode [CDrawingManager :: FillGradient](#fillgradient).

Cette méthode génère un échec d’assertion si *nPercentage* est inférieur à 0 ou supérieur à 100.

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a> CDrawingManager::FillGradient

Remplit une zone rectangulaire avec le dégradé de couleur spécifié.

```cpp
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Zone rectangulaire à remplir.

*colorStart*<br/>
dans Première couleur du dégradé.

*colorFinish*<br/>
dans Couleur finale du dégradé.

*bHorz*<br/>
dans Paramètre booléen qui spécifie si `FillGradient` doit dessiner un dégradé horizontal ou vertical.

*nStartFlatPercentage*<br/>
dans Pourcentage du rectangle qui se `FillGradient` remplit avec *colorStart* avant de démarrer le dégradé.

*nEndFlatPercentage*<br/>
dans Pourcentage du rectangle qui se `FillGradient` remplit avec *colorFinish* après avoir terminé le dégradé.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `FillGradient` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de l' [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a> CDrawingManager::FillGradient2

Remplit une zone rectangulaire avec un dégradé de couleur spécifié.

```cpp
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Zone rectangulaire à remplir.

*colorStart*<br/>
dans Première couleur du dégradé.

*colorFinish*<br/>
dans Dernière couleur du dégradé.

*nAngle*<br/>
dans Entier compris entre 0 et 360. Ce paramètre spécifie le sens du dégradé de couleur.

### <a name="remarks"></a>Notes

Utilisez *nAngle* pour spécifier le sens du dégradé de couleur. Lorsque vous spécifiez la direction du dégradé de couleur, vous spécifiez également l’emplacement de départ du dégradé de couleur. La valeur 0 pour *nAngle* indique que le dégradé commence à partir du haut du rectangle. À mesure que *nAngle* augmente, l’emplacement de départ du dégradé se déplace dans un sens dans le sens inverse des aiguilles d’une montre en fonction de l’angle.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `FillGradient2` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a> CDrawingManager::GrayRect

Remplit un rectangle avec une couleur grise spécifiée.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Zone rectangulaire à remplir.

*nPercentage*<br/>
dans Pourcentage de gris souhaité dans le rectangle.

*clrTransparent*<br/>
dans Couleur transparente.

*clrDisabled*<br/>
dans Couleur utilisée par cette méthode pour la désaturation si *nPercentage* a la valeur-1.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Pour le paramètre *nPercentage*, une valeur inférieure indique une couleur plus sombre.

La valeur maximale de *nPercentage* est 200. Une valeur supérieure à 200 ne modifie pas l’apparence du rectangle. Si la valeur est-1, cette méthode utilise *clrDisabled* pour limiter la saturation du rectangle.

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a> CDrawingManager::HighlightRect

Met en surbrillance une zone rectangulaire.

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Zone rectangulaire à mettre en surbrillance.

*nPercentage*<br/>
dans Pourcentage qui indique la transparence de la mise en surbrillance.

*clrTransparent*<br/>
dans Couleur transparente.

*nTolerance*<br/>
dans Entier compris entre 0 et 255 qui indique la tolérance de couleurs.

*clrBlend*<br/>
dans Couleur de base pour la fusion.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si la valeur de *nPercentage* est comprise entre 0 et 99, `HighlightRect` utilise l’algorithme de fusion alpha. Pour plus d’informations sur la fusion alpha, consultez [couches et remplissages de fusion alpha](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Si *nPercentage* a la valeur-1, cette méthode utilise le niveau de surbrillance par défaut. Si *nPercentage* est 100, cette méthode ne fait rien et retourne true.

La méthode utilise le paramètre *nTolerance* pour déterminer si la zone rectangulaire doit être mise en surbrillance. Pour mettre en surbrillance le rectangle, la différence entre la couleur d’arrière-plan de votre application et *clrTransparent* doit être inférieure à *nTolerance* dans chaque composant de couleur (rouge, vert et bleu).

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a> CDrawingManager :: HLStoRGB_ONE

Convertit une couleur d’une représentation TLS en une représentation RVB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Paramètres

*H*<br/>
dans Nombre compris entre 0 et 1 qui représente la teinte de la couleur.

*Budget*<br/>
dans Nombre compris entre 0 et 1 qui indique la luminosité de la couleur.

*S*<br/>
dans Nombre compris entre 0 et 1 qui indique la saturation de la couleur.

### <a name="return-value"></a>Valeur renvoyée

Représentation RVB de la couleur TLS fournie.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous la forme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, consultez [Color](/windows/win32/uxguide/vis-color).

Cette méthode et la `CDrawingManager::HLStoRGB_TWO` méthode effectuent la même opération, mais requièrent des valeurs différentes pour le paramètre *H* . Dans cette méthode, *H* est un pourcentage du cercle. Dans la `CDrawingManager::HLStoRGB_TWO` méthode, *H* est une valeur de degré comprise entre 0 et 360, qui représentent toutes deux le rouge. Par exemple, avec `HLStoRGB_ONE` , la valeur 0,25 pour *H* équivaut à une valeur de 90 avec `HLStoRGB_TWO` .

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a> CDrawingManager :: HLStoRGB_TWO

Convertit une couleur d’une représentation TLS en une représentation RVB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Paramètres

*H*<br/>
dans Nombre compris entre 0 et 360 qui représente la teinte de la couleur.

*Budget*<br/>
dans Nombre compris entre 0 et 1 qui indique la luminosité de la couleur.

*S*<br/>
dans Nombre compris entre 0 et 1 qui indique la saturation de la couleur.

### <a name="return-value"></a>Valeur renvoyée

Représentation RVB de la couleur TLS fournie.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous la forme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, consultez [Color](/windows/win32/uxguide/vis-color).

Cette méthode et la méthode [CDrawingManager :: HLStoRGB_ONE](#hlstorgb_one) effectuent la même opération, mais requièrent des valeurs différentes pour le paramètre *H* . Dans cette méthode, *H* est une valeur de degré comprise entre 0 et 360, qui représentent toutes deux le rouge. Dans la méthode [CDrawingManager :: HLStoRGB_ONE](#hlstorgb_one) , *H* est un pourcentage du cercle. Par exemple, avec `HLStoRGB_ONE` , la valeur 0,25 pour *H* équivaut à une valeur de 90 avec `HLStoRGB_TWO` .

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a> CDrawingManager::HSVtoRGB

Convertit une couleur d’une représentation HSV en une représentation RVB.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>Paramètres

*Manutention*\
dans Nombre compris entre 0 et 360 qui indique la teinte de la couleur.

*X*\
dans Nombre compris entre 0 et 1 qui indique la saturation de la couleur.

*V*\
dans Nombre compris entre 0 et 1 qui indique la valeur de la couleur.

### <a name="return-value"></a>Valeur renvoyée

Représentation RVB de la couleur HSV fournie.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous la forme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, consultez [Color](/windows/win32/uxguide/vis-color).

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a> CDrawingManager::HuetoRGB

Convertit une valeur de teinte en composant rouge, vert ou bleu.

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>Paramètres

*M1*<br/>
dans Consultez la section Notes.

*carré*<br/>
dans Consultez la section Notes.

*h*<br/>
dans Consultez la section Notes.

*rm1*<br/>
dans Consultez la section Notes.

*rm2*<br/>
dans Consultez la section Notes.

*RH*<br/>
dans Consultez la section Notes.

### <a name="return-value"></a>Valeur renvoyée

Composant individuel rouge, vert ou bleu pour la teinte fournie.

### <a name="remarks"></a>Notes

Cette méthode est une méthode d’assistance utilisée par la `CDrawingManager` classe pour calculer les composants rouge, vert et bleu individuels d’une couleur dans une représentation HSV ou TSL. Cette méthode n’est pas conçue pour être appelée directement par le programmeur. Les paramètres d’entrée sont des valeurs qui dépendent de l’algorithme de conversion.

Pour convertir une couleur HSV ou TSL en une représentation RVB, appelez l’une des méthodes suivantes :

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager :: HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager :: HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a> CDrawingManager::MirrorRect

Retourne une zone rectangulaire.

```cpp
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Rectangle englobant de la zone à retourner.

*bHorz*<br/>
dans Paramètre booléen qui indique si le rectangle est inversé horizontalement ou verticalement.

### <a name="remarks"></a>Notes

Cette méthode peut retourner n’importe quelle zone du contexte de périphérique appartenant à la `CDrawingManager` classe. Si *bHorz* a la valeur true, cette méthode retourne la zone horizontalement. Sinon, elle retourne la zone verticalement.

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a> CDrawingManager ::P ixelAlpha

Calcule la couleur finale pour un pixel semi-transparent.

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>Paramètres

*srcPixel*<br/>
dans Couleur initiale du pixel.

*%*<br/>
dans Nombre compris entre 0 et 100 qui représente le pourcentage de transparence. Une valeur de 100 indique que la couleur initiale est complètement transparente.

*pourcentage*<br/>
dans Nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant rouge.

*percentG*<br/>
dans Nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant vert.

*percentB*<br/>
dans Nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant bleu.

*dstPixel*<br/>
dans Couleur de base du pixel.

### <a name="return-value"></a>Valeur renvoyée

Couleur finale du pixel semi-transparent.

### <a name="remarks"></a>Notes

Il s’agit d’une classe d’assistance pour la coloration des bitmaps translucides et n’est pas conçue pour être appelée directement par le programmeur.

Lorsque vous utilisez la version de la méthode avec *dstPixel*, la couleur finale est une combinaison de *dstPixel* et *srcPixel*. La couleur *srcPixel* est la couleur partiellement transparente sur la couleur de base de *dstPixel*.

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a> CDrawingManager ::P repareShadowMask

Crée une image bitmap qui peut être utilisée comme une ombre.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Paramètres

*nDepth*<br/>
dans Largeur et hauteur de l’ombre.

*clrBase*<br/>
dans Couleur de l’ombre.

*iMinBrightness*<br/>
dans Luminosité minimale de l’ombre.

*iMaxBrightness*<br/>
dans Luminosité maximale de l’ombre.

### <a name="return-value"></a>Valeur renvoyée

Handle vers l’image bitmap créée si cette méthode réussit ; Sinon, NULL.

### <a name="remarks"></a>Notes

Si *nDepth* a la valeur 0, cette méthode se termine et retourne la valeur null. Si *nDepth* est inférieur à 3, la largeur et la hauteur de l’ombre sont définies sur 3 pixels.

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a> CDrawingManager::RGBtoHSL

Convertit une couleur d’une représentation rouge, verte et bleue en une représentation de teinte, de saturation et de luminosité (TSL).

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>Paramètres

*composantes*\
dans Couleur des valeurs RVB.

*Manutention*\
à Pointeur vers un double où la méthode stocke la teinte de la couleur.

*X*\
à Pointeur vers un double dans lequel la méthode stocke la saturation de la couleur.

*Budget*\
à Pointeur vers un double dans lequel la méthode stocke la luminosité de la couleur.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous la forme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, consultez [Color](/windows/win32/uxguide/vis-color).

La valeur retournée pour *H* est représentée sous la forme d’une fraction comprise entre 0 et 1, où 0 et 1 représentent la couleur rouge. Les valeurs retournées pour *S* et *L* sont des nombres compris entre 0 et 1.

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a> CDrawingManager::RGBtoHSV

Convertit une couleur d’une représentation RVB en représentation HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Paramètres

*composantes*<br/>
dans Couleur à convertir dans une représentation RVB.

*H*<br/>
à Pointeur vers un double dans lequel cette méthode stocke la teinte résultante pour la couleur.

*S*<br/>
à Pointeur vers un double dans lequel cette méthode stocke la saturation résultante pour la couleur.

*V*<br/>
à Pointeur vers un double dans lequel cette méthode stocke la valeur résultante pour la couleur.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous la forme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, consultez [Color](/windows/win32/uxguide/vis-color).

La valeur retournée pour *H* est un nombre compris entre 0 et 360, où 0 et 360 indiquent rouge. Les valeurs de retour pour *S* et *V* sont des nombres compris entre 0 et 1.

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a> CDrawingManager::SetAlphaPixel

Colore un pixel transparent dans une bitmap.

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>Paramètres

*pBits*<br/>
dans Pointeur vers les valeurs de bit de l’image bitmap.

*rectangulaire*<br/>
dans Zone rectangulaire dans votre application. Le gestionnaire de dessins dessine une ombre sous et à droite de cette zone.

*x*<br/>
dans Coordonnée horizontale du pixel à colorier.

*y*<br/>
dans Coordonnée verticale du pixel à colorier.

*%*<br/>
dans Pourcentage de transparence.

*iShadowSize*<br/>
dans Largeur et hauteur de l’ombre.

*clrBase*<br/>
dans Couleur de l’ombre.

*bIsRight*<br/>
dans Paramètre booléen qui indique le pixel à colorier. Pour plus d'informations, consultez la section Notes.

### <a name="remarks"></a>Notes

Cette méthode est une méthode d’assistance utilisée par la méthode [CDrawingManager ::D rawshadow](#drawshadow) . Si vous souhaitez dessiner une ombre, nous vous recommandons d’appeler à la `CDrawingManager::DrawShadow` place.

Si *bIsRight* a la valeur true, le pixel en couleur est mesuré *x* pixels à partir du bord droit de *Rect*. Si la valeur est FALSe, le pixel de couleur est mesuré *x* pixels à partir du bord gauche de *Rect*.

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a> CDrawingManager :: SetPixel

Remplace un seul pixel d’une image bitmap par la couleur spécifiée.

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>Paramètres

*pBits*\
dans Pointeur vers les valeurs de bits de la bitmap.

*adéquat*\
dans Largeur totale de l’image bitmap.

*CY*\
dans Hauteur totale de l’image bitmap.

*x*\
dans Coordonnée x du pixel de la bitmap à modifier.

*y*\
dans Coordonnée y du pixel de la bitmap à modifier.

*Couleur*\
dans Nouvelle couleur du pixel identifié par les coordonnées fournies.

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a> CDrawingManager::SmartMixColors

Combine deux couleurs en fonction d’un rapport pondéré.

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>Paramètres

*color1*\
dans Première couleur à mélanger.

*color2*\
dans Deuxième couleur à mélanger.

*dblLumRatio*\
dans Rapport de la luminosité de la nouvelle couleur. `SmartMixColors` multiplie la luminosité de la couleur mixte par ce rapport avant de déterminer une couleur finale.

*KL*\
dans Le rapport pondéré pour la première couleur.

*K2*\
dans Le rapport pondéré pour la deuxième couleur.

### <a name="return-value"></a>Valeur renvoyée

Couleur qui représente un mélange pondéré des couleurs fournies.

### <a name="remarks"></a>Notes

Cette méthode échoue avec une erreur si *K1* ou *K2* est inférieur à zéro. Si ces deux paramètres ont la valeur 0, la méthode retourne `RGB(0, 0, 0)` .

Le rapport pondéré est calculé avec la formule suivante : (color1 \* K1 + color2 \* K2)/(K1 + K2). Une fois le rapport pondéré mesuré, la méthode calcule la luminosité de la couleur mixte. Il multiplie ensuite la luminosité par *dblLumRatio*. Si la valeur est supérieure à 1,0, la méthode définit la luminosité de la couleur mixte sur la nouvelle valeur. Dans le cas contraire, la luminosité est définie sur 1,0.

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a> CDrawingManager ::D rawRotated

Fait pivoter un contenu DC source à l’intérieur du rectangle donné de 90 degrés.

```cpp
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Paramètres

*rectDest*<br/>
Rectangle de destination.

*dcSrc*<br/>
Contexte de périphérique source.

*bClockWise*<br/>
TRUE indique pivoter + 90 degrés ; FALSe indique Rotate-90 degrés.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
