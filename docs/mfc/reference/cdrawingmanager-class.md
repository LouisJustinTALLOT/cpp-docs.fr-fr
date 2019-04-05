---
title: Cdrawingmanager, classe
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
ms.openlocfilehash: 506ab7a06653942ecff05043a7e7efabd535115f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781690"
---
# <a name="cdrawingmanager-class"></a>Cdrawingmanager, classe

Le `CDrawingManager` classe implémente les algorithmes de dessins complexes.

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
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Crée une bitmap indépendante du périphérique 32 bits (DIB) que les applications peuvent écrire directement.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Affiche les bitmaps qui ont des pixels transparents ou semi-transparent.|
|[CDrawingManager::DrawRotated](#drawrotated)|Fait pivoter une source de contenu de contrôleur de domaine à l’intérieur du rectangle donné par +/-90 degrés|
|[CDrawingManager::DrawEllipse](#drawellipse)|Dessine une ellipse avec les couleurs de remplissage et la bordure fournis.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Dessine un anneau et le remplit avec un dégradé de couleur.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Dessine une ligne.|
|[CDrawingManager::DrawRect](#drawrect)|Dessine un rectangle avec les couleurs de remplissage et la bordure fournis.|
|[CDrawingManager::DrawShadow](#drawshadow)|Dessine une ombre pour une zone rectangulaire.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Remplit une zone rectangulaire avec deux gradients de couleur.|
|[CDrawingManager::FillGradient](#fillgradient)|Remplit une zone rectangulaire avec un dégradé de couleur spécifié.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Remplit une zone rectangulaire avec un dégradé de couleur spécifié. La direction de modification de la couleur du dégradé est également spécifiée.|
|[CDrawingManager::GrayRect](#grayrect)|Remplit un rectangle avec une couleur grise spécifiée.|
|[CDrawingManager::HighlightRect](#highlightrect)|Met en surbrillance une zone rectangulaire.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Convertit une couleur à partir d’une représentation sous forme de HLS en une représentation RVB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Convertit une couleur à partir d’une représentation sous forme de HLS en une représentation RVB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Convertit une couleur à partir d’une représentation TSL en une représentation RVB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Méthode d’assistance qui convertit une valeur de teinte à un composant rouge, vert ou bleu.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Cette méthode retourne une zone rectangulaire.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Méthode d’assistance qui détermine la couleur finale d’un pixel translucide.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Crée une bitmap qui peut être utilisée comme une ombre.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Convertit une couleur à partir d’une représentation RVB en une représentation NSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Convertit une couleur à partir d’une représentation RVB en une représentation TSL.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Méthode d’assistance qui le colore un pixel partiellement transparent dans une image bitmap.|
|[CDrawingManager::SetPixel](#setpixel)|Méthode d’assistance qui modifie un seul pixel dans un bitmap de la couleur spécifiée.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combine deux couleurs selon un ratio pondéré.|

## <a name="remarks"></a>Notes

Le `CDrawingManager` classe fournit des fonctions de dessin des ombres, des dégradés de couleur et des rectangles en surbrillance. Il effectue également la fusion alpha. Vous pouvez utiliser cette classe pour modifier directement l’interface utilisateur de votre application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdrawmanager.h

##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager

Construit un [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) objet.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Paramètres

*dc*<br/>
[in] Une référence à un contexte de périphérique. Le `CDrawingManager` utilise ce contexte de dessin.

##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32

Crée une bitmap indépendante du périphérique 32 bits (DIB) que les applications peuvent écrire directement.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*size*|[in] Un [CSize](../../atl-mfc-shared/reference/csize-class.md) paramètre qui indique la taille de la bitmap.|
|*pBits*|[out] Un pointeur vers un pointeur qui reçoit l’emplacement de du fichier DIB bit des valeurs.|
|*bitmap*|Un handle de bitmap d’origine|
|*clrTransparent*|Une valeur RVB en spécifiant une couleur transparente de l’image bitmap d’origine.|

### <a name="return-value"></a>Valeur de retour

Un handle de bitmap DIB nouvellement créé si cette méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la création d’une image bitmap DIB, consultez [CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibitmap).

##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha

Affiche les bitmaps qui ont des pixels transparents ou semi-transparent.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Paramètres

*pDstDC*<br/>
[in] Pointeur vers le contexte de périphérique pour la destination.

*rectDst*<br/>
[in] Le rectangle de destination.

*pSrcDC*<br/>
[in] Pointeur vers le contexte de périphérique pour la source.

*rectSrc*<br/>
[in] Le rectangle source.

### <a name="remarks"></a>Notes

Cette méthode effectue la simulation de transparence pour les bitmaps de deux. Pour plus d’informations sur le blindage alpha, consultez [AlphaBlend](/windows/desktop/api/wingdi/nf-wingdi-alphablend) dans le SDK Windows.

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

Dessine une ellipse avec les couleurs de remplissage et la bordure fournis.

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
[in] Le rectangle englobant de l’ellipse.

*clrFill*<br/>
[in] La couleur de que cette méthode utilise pour remplir l’ellipse.

*clrLine*<br/>
[in] La couleur de cette méthode utilise en tant que la bordure de l’ellipse.

### <a name="remarks"></a>Notes

Cette méthode retourne sans dessiner une ellipse si une couleur est définie sur -1. Elle retourne également sans dessiner une ellipse, si une dimension du rectangle englobant est 0.

##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing

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

*rect*<br/>
[in] Un [CRect](../../atl-mfc-shared/reference/crect-class.md) paramètre qui spécifie la limite de l’anneau de dégradé.

*colorStart*<br/>
[in] La première couleur du dégradé.

*colorFinish*<br/>
[in] La dernière couleur du dégradé.

*colorBorder*<br/>
[in] La couleur de la bordure.

*nAngle*<br/>
[in] Un paramètre qui spécifie l’angle du dégradé de dessin initial. Cette valeur doit être comprise entre 0 et 360.

*nWidth*<br/>
[in] La largeur de la bordure de l’anneau.

*clrFace*<br/>
[in] Couleur de l’intérieur de l’anneau.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le rectangle défini par *rect* doivent être au moins 5 pixels larges et 5 pixels en hauteur.

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Dessine une ligne.

```
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

|||
|-|-|
|Paramètre|Description|
|*x1*|[in] Coordonnée x où la ligne commence.|
|*y1*|[in] Coordonnée y où la ligne commence.|
|*x2*|[in] Coordonnée x où la ligne se termine.|
|*y2*|[in] Coordonnée y où la ligne se termine.|
|*clrLine*|[in] La couleur de la ligne.|

### <a name="remarks"></a>Notes

Cette méthode échoue si *clrLine* est égal à -1.

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

Dessine un rectangle avec les couleurs de remplissage et la bordure fournis.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
[in] Les limites du rectangle.

*clrFill*<br/>
[in] La couleur de que cette méthode utilise pour remplir le rectangle.

*clrLine*<br/>
[in] La couleur de cette méthode utilise pour la bordure du rectangle.

### <a name="remarks"></a>Notes

Cette méthode retourne sans dessiner un rectangle, si une couleur est définie sur -1. Elle retourne également si une dimension du rectangle est 0.

##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow

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

*rect*<br/>
[in] Une zone rectangulaire dans votre application. Le Gestionnaire de dessin Dessine une ombre en dessous de cette zone.

*nDepth*<br/>
[in] La largeur et la hauteur de l’ombre.

*iMinBrightness*<br/>
[in] La luminosité minimale de l’ombre.

*iMaxBrightness*<br/>
[in] La luminosité maximale de l’ombre.

*pBmpSaveBottom*<br/>
[in] Pointeur vers une image bitmap qui contient l’image pour la partie inférieure de l’ombre.

*pBmpSaveRight*<br/>
[in] Pointeur vers une image bitmap qui contient l’image de l’ombre est dessinée sur le côté droit du rectangle.

*clrBase*<br/>
[in] La couleur de l’ombre.

*bRightShadow*<br/>
[in] Un paramètre booléen qui indique comment l’ombre est dessinée. Si *bRightShadow* est `TRUE`, `DrawShadow` Dessine une ombre sur le côté droit du rectangle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez fournir deux bitmaps valides pour le bas et les ombres de droite en utilisant les paramètres *pBmpSaveBottom* et *pBmpSaveRight*. Si ces [CBitmap](../../mfc/reference/cbitmap-class.md) objets ont un objet GDI attaché, `DrawShadow` utilisera ces bitmaps en tant que les ombres. Si le `CBitmap` paramètres n’ont pas d’un objet GDI attaché, `DrawShadow` Dessine l’ombre et attache les bitmaps pour les paramètres. Dans les futures les appels à `DrawShadow`, vous pouvez fournir ces bitmaps pour accélérer le processus de dessin. Pour plus d’informations sur la `CBitmap` classe et les objets GDI, consultez [objets graphiques](../../mfc/graphic-objects.md).

Si un de ces paramètres est `NULL`, `DrawShadow` automatiquement Dessine l’ombre.

Si vous définissez *bRightShadow* sur FALSE, l’ombre sera dessiné en dessous et à gauche de la zone rectangulaire.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `DrawShadow` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de la [exemple de démonstration de feuille de propriétés de l’abonnement](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient

Remplit une zone rectangulaire avec deux gradients de couleur.

```
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

*rect*<br/>
[in] Le rectangle à remplir.

*colorStart1*<br/>
[in] Couleur initiale du premier dégradé de couleur.

*colorFinish1*<br/>
[in] La couleur finale du premier dégradé de couleur.

*colorStart2*<br/>
[in] Couleur initiale du deuxième dégradé de couleur.

*colorFinish2*<br/>
[in] La couleur finale du deuxième dégradé de couleur.

*bHorz*<br/>
[in] Un paramètre booléen qui indique si `Fill4ColorsGradient` couleurs d’un dégradé horizontal ou vertical. TRUE indique un dégradé horizontal.

*nPercentage*<br/>
[in] Entier compris entre 0 et 100. Cette valeur indique le pourcentage du rectangle à remplir avec le dégradé de couleur de premier.

### <a name="remarks"></a>Notes

Lorsqu’un rectangle est rempli avec deux gradients de couleur, ils sont situés au-dessus de l’autre ou à côté de l’autre, selon la valeur de *bHorz*. Chaque dégradé de couleur est calculée indépendamment avec la méthode [CDrawingManager::FillGradient](#fillgradient).

Cette méthode génère un échec d’assertion si *nPercentage* est inférieur à 0 ou supérieur à 100.

##  <a name="fillgradient"></a>  CDrawingManager::FillGradient

Remplit une zone rectangulaire avec le dégradé de couleur spécifié.

```
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
[in] La zone rectangulaire à remplir.

*colorStart*<br/>
[in] La première couleur du dégradé.

*colorFinish*<br/>
[in] La couleur finale du dégradé.

*bHorz*<br/>
[in] Un paramètre booléen qui spécifie si `FillGradient` doit dessiner un dégradé horizontal ou vertical.

*nStartFlatPercentage*<br/>
[in] Le pourcentage du rectangle qui `FillGradient` remplit avec *colorStart* avant le début du dégradé.

*nEndFlatPercentage*<br/>
[in] Le pourcentage du rectangle qui `FillGradient` remplit avec *colorFinish* après avoir fini le dégradé.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `FillGradient` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de la [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2

Remplit une zone rectangulaire avec un dégradé de couleur spécifié.

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
[in] La zone rectangulaire à remplir.

*colorStart*<br/>
[in] La première couleur du dégradé.

*colorFinish*<br/>
[in] La dernière couleur du dégradé.

*nAngle*<br/>
[in] Entier compris entre 0 et 360. Ce paramètre spécifie le sens du dégradé de couleur.

### <a name="remarks"></a>Notes

Utilisez *nAngle* pour spécifier le sens du dégradé de couleur. Lorsque vous spécifiez le sens du dégradé de couleur, vous spécifiez également où le dégradé de couleur commence. La valeur 0 pour *nAngle* indique le dégradé démarre à partir du haut du rectangle. En tant que *nAngle* augmente, l’emplacement de départ pour le dégradé se déplace dans le sens inverse des aiguilles selon l’angle.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `FillGradient2` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>  CDrawingManager::GrayRect

Remplit un rectangle avec une couleur grise spécifiée.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
[in] La zone rectangulaire à remplir.

*nPercentage*<br/>
[in] Le pourcentage de votre choix dans le rectangle de gris.

*clrTransparent*<br/>
[in] Couleur transparente.

*clrDisabled*<br/>
[in] La couleur par cette méthode pour la saturation de la déduplication si *nPercentage* a la valeur -1.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Pour le paramètre *nPercentage*, une valeur inférieure indique une couleur plus sombre.

La valeur maximale pour *nPercentage* est 200. Une valeur supérieure à 200 ne modifie pas l’apparence du rectangle. Si la valeur est -1, cette méthode utilise *clrDisabled* pour limiter la saturation du rectangle.

##  <a name="highlightrect"></a>  CDrawingManager::HighlightRect

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

*rect*<br/>
[in] Une zone rectangulaire pour mettre en surbrillance.

*nPercentage*<br/>
[in] Un pourcentage qui indique le degré de transparence qui doit être à la mise en surbrillance.

*clrTransparent*<br/>
[in] Couleur transparente.

*nTolerance*<br/>
[in] Un entier compris entre 0 et 255 qui indique la tolérance de couleur.

*clrBlend*<br/>
[in] La couleur de base pour la fusion.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Si *nPercentage* est comprise entre 0 et 99, `HighlightRect` utilise l’algorithme contrôle alpha. Pour plus d’informations sur la fusion alpha, consultez [lignes de fusion Alpha et remplissages](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Si *nPercentage* est -1, cette méthode utilise le niveau de mise en surbrillance par défaut. Si *nPercentage* est 100, cette méthode ne fait rien et retourne la valeur TRUE.

La méthode utilise le paramètre *nTolerance* pour déterminer s’il faut mettre en surbrillance de la zone rectangulaire. Pour mettre en surbrillance le rectangle, la différence entre la couleur d’arrière-plan de votre application et *clrTransparent* doit être inférieur à *nTolerance* dans chaque composant de couleur (rouge, vert et bleu).

##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE

Convertit une couleur à partir d’une représentation sous forme de HLS en une représentation RVB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Paramètres

*H*<br/>
[in] Un nombre compris entre 0 et 1 qui représente la teinte de la couleur.

*L*<br/>
[in] Un nombre compris entre 0 et 1 qui indique la couleur de la luminosité.

*S*<br/>
[in] Un nombre compris entre 0 et 1 qui indique la saturation de la couleur.

### <a name="return-value"></a>Valeur de retour

La représentation RVB de la couleur TSL fournie.

### <a name="remarks"></a>Notes

Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](/windows/desktop/uxguide/vis-color).

Cette méthode et la `CDrawingManager::HLStoRGB_TWO` méthode effectuer la même opération, mais requièrent des valeurs différentes pour le *H* paramètre. Dans cette méthode, *H* est un pourcentage du cercle. Dans le `CDrawingManager::HLStoRGB_TWO` (méthode), *H* est une valeur de degré comprise entre 0 et 360, ce qui les deux représentent rouge. Par exemple, avec `HLStoRGB_ONE`, une valeur de 0,25 pour *H* équivaut à une valeur de 90 avec `HLStoRGB_TWO`.

##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO

Convertit une couleur à partir d’une représentation sous forme de HLS en une représentation RVB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Paramètres

*H*<br/>
[in] Un nombre compris entre 0 et 360 qui représente la teinte de la couleur.

*L*<br/>
[in] Un nombre compris entre 0 et 1 qui indique la couleur de la luminosité.

*S*<br/>
[in] Un nombre compris entre 0 et 1 qui indique la saturation de la couleur.

### <a name="return-value"></a>Valeur de retour

La représentation RVB de la couleur TSL fournie.

### <a name="remarks"></a>Notes

Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](/windows/desktop/uxguide/vis-color).

Cette méthode et la [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) méthode effectuer la même opération, mais requièrent des valeurs différentes pour le *H* paramètre. Dans cette méthode, *H* est une valeur de degré comprise entre 0 et 360, ce qui les deux représentent rouge. Dans le [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) (méthode), *H* est un pourcentage du cercle. Par exemple, avec `HLStoRGB_ONE`, une valeur de 0,25 pour *H* équivaut à une valeur de 90 avec `HLStoRGB_TWO`.

##  <a name="hsvtorgb"></a>  CDrawingManager::HSVtoRGB

Convertit une couleur à partir d’une représentation TSL en une représentation RVB.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*H*|[in] Un nombre compris entre 0 et 360 qui indique la teinte de la couleur.|
|*S*|[in] Un nombre compris entre 0 et 1 qui indique la saturation de la couleur.|
|*V*|[in] Un nombre compris entre 0 et 1 qui indique la valeur de la couleur.|

### <a name="return-value"></a>Valeur de retour

La représentation RVB de la couleur TSL fournie.

### <a name="remarks"></a>Notes

Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](/windows/desktop/uxguide/vis-color).

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

Convertit une valeur de teinte à un composant rouge, vert ou bleu.

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

*m1*<br/>
[in] Consultez la section Notes.

*m2*<br/>
[in] Consultez la section Notes.

*h*<br/>
[in] Consultez la section Notes.

*rm1*<br/>
[in] Consultez la section Notes.

*rm2*<br/>
[in] Consultez la section Notes.

*rh*<br/>
[in] Consultez la section Notes.

### <a name="return-value"></a>Valeur de retour

Le composant de rouge, vert ou bleu individuel pour la teinte fourni.

### <a name="remarks"></a>Notes

Cette méthode est une méthode d’assistance qui le `CDrawingManager` classe utilise pour calculer les composants rouges, vert et bleus individuels d’une couleur dans une représentation TSL ou TSL. Cette méthode n’est pas conçue pour être appelée directement par le programmeur. Les paramètres d’entrée sont des valeurs qui varient selon l’algorithme de conversion.

Pour convertir une couleur TSL ou HSL en représentation RVB, appelez l’une des méthodes suivantes :

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>  CDrawingManager::MirrorRect

Cette méthode retourne une zone rectangulaire.

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
[in] Le rectangle englobant de la zone à retourner.

*bHorz*<br/>
[in] Un paramètre booléen qui indique si le rectangle est retournée horizontalement ou verticalement.

### <a name="remarks"></a>Notes

Cette méthode peut retourner toute zone du contexte de périphérique appartenant à la `CDrawingManager` classe. Si *bHorz* est définie sur TRUE, cette méthode retourne la zone horizontalement. Sinon, elle retourne verticalement la zone.

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

Calcule la couleur finale d’un pixel translucide.

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
[in] Couleur initiale pour le pixel.

*percent*<br/>
[in] Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence. Une valeur de 100 indique que la couleur initiale est complètement transparente.

*percentR*<br/>
[in] Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant rouge.

*percentG*<br/>
[in] Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant vert.

*percentB*<br/>
[in] Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant bleu.

*dstPixel*<br/>
[in] La couleur de base pour le pixel.

### <a name="return-value"></a>Valeur de retour

La couleur finale du pixel translucide.

### <a name="remarks"></a>Notes

Ceci est une classe d’assistance pour colorer les bitmaps translucides et n’est pas conçu pour être appelée directement par le programmeur.

Lorsque vous utilisez la version de la méthode qui a *dstPixel*, la couleur finale est une combinaison de *dstPixel* et *srcPixel*. Le *srcPixel* la couleur est partiellement transparent sur la couleur de base de *dstPixel*.

##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask

Crée une bitmap qui peut être utilisée comme une ombre.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Paramètres

*nDepth*<br/>
[in] La largeur et la hauteur de l’ombre.

*clrBase*<br/>
[in] La couleur de l’ombre.

*iMinBrightness*<br/>
[in] La luminosité minimale de l’ombre.

*iMaxBrightness*<br/>
[in] La luminosité maximale de l’ombre.

### <a name="return-value"></a>Valeur de retour

Un handle de bitmap créée si cette méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

Si *nDepth* est définie sur 0, cette méthode se termine et retourne la valeur NULL. Si *nDepth* est inférieur à 3, la largeur et la hauteur de l’ombre sont définis pour 3 pixels.

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

Convertit une couleur à partir d’une représentation sous forme rouge, vert et bleue (RVB) une teinte, saturation et la représentation sous forme de la luminosité (TSL).

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*rgb*|[in] La couleur de valeurs RVB.|
|*H*|[out] Pointeur vers un double où la méthode stocke la teinte de la couleur.|
|*S*|[out] Pointeur vers un double où la méthode stocke la saturation de la couleur.|
|*L*|[out] Pointeur vers un double où la méthode stocke la luminosité de la couleur.|

### <a name="remarks"></a>Notes

Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](/windows/desktop/uxguide/vis-color).

La valeur retournée pour *H* est représenté sous forme de fraction comprise entre 0 et 1, où 0 et 1 représentent rouge. Les valeurs renvoyées pour *S* et *L* sont des nombres compris entre 0 et 1.

##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV

Convertit une couleur à partir d’une représentation RVB en une représentation TSL.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Paramètres

*rgb*<br/>
[in] Couleur à convertir en une représentation RVB.

*H*<br/>
[out] Pointeur vers un double où cette méthode stocke la teinte résultant pour la couleur.

*S*<br/>
[out] Pointeur vers un double où cette méthode stocke la saturation qui en résulte pour la couleur.

*V*<br/>
[out] Pointeur vers un double où cette méthode stocke la valeur obtenue pour la couleur.

### <a name="remarks"></a>Notes

Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](/windows/desktop/uxguide/vis-color).

La valeur retournée pour *H* est un nombre compris entre 0 et 360, où 0 et 360 indiquent rouge. Valeurs de retour pour *S* et *V* sont des nombres compris entre 0 et 1.

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

Couleurs d’un pixel transparent dans une image bitmap.

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
[in] Pointeur vers les valeurs de bits de l’image bitmap.

*rect*<br/>
[in] Une zone rectangulaire dans votre application. Le Gestionnaire de dessin Dessine une ombre en dessous et à droite de cette zone.

*x*<br/>
[in] La coordonnée horizontale du pixel de couleur.

*o*<br/>
[in] Coordonnée verticale du pixel de couleur.

*percent*<br/>
[in] Le pourcentage de transparence.

*iShadowSize*<br/>
[in] La largeur et la hauteur de l’ombre.

*clrBase*<br/>
[in] La couleur de l’ombre.

*bIsRight*<br/>
[in] Un paramètre booléen qui indique quel pixel de couleur. Pour plus d'informations, consultez la section Notes.

### <a name="remarks"></a>Notes

Cette méthode est une méthode d’assistance qui est utilisée par le [CDrawingManager::DrawShadow](#drawshadow) (méthode). Nous recommandons que si vous souhaitez ajouter une ombre, appelez `CDrawingManager::DrawShadow` à la place.

Si *bIsRight* est définie sur TRUE, le pixel de couleur est mesuré *x* pixels du bord droit de *rect*. Si la valeur est FALSE, le pixel de couleur est mesuré *x* pixels du bord gauche de *rect*.

##  <a name="setpixel"></a>  CDrawingManager::SetPixel

Modifie un seul pixel dans un bitmap de la couleur spécifiée.

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

|||
|-|-|
|Paramètre|Description|
|*pBits*|[in] Pointeur vers les valeurs de bits de l’image bitmap.|
|*cx*|[in] La largeur totale de l’image bitmap.|
|*cy*|[in] La hauteur totale de l’image bitmap.|
|*x*|[in] Coordonnée x du pixel de la bitmap à modifier.|
|*o*|[in] Coordonnée y du pixel de la bitmap à modifier.|
|*couleur*|[in] La nouvelle couleur du pixel identifié par les coordonnées fournies.|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

Combine deux couleurs selon un ratio pondéré.

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*color1*|[in] La première couleur à combiner.|
|*color2*|[in] La deuxième couleur à combiner.|
|*dblLumRatio*|[in] Le rapport pour la luminosité de la nouvelle couleur. `SmartMixColors` Multiplie la luminosité de la couleur mixte par ce rapport avant de déterminer la couleur finale.|
|*k1*|[in] Le taux pondéré pour la première couleur.|
|*k2*|[in] Le taux pondéré pour la deuxième couleur.|

### <a name="return-value"></a>Valeur de retour

Couleur qui représente une combinaison pondérée des couleurs fournis.

### <a name="remarks"></a>Notes

Cette méthode échoue avec une erreur si le *k1* ou *k2* est inférieur à zéro. Si ces deux paramètres sont définies sur 0, la méthode retourne `RGB(0, 0, 0)`.

Le ratio pondéré est calculé avec la formule suivante : (color1 \* k1 + color2 \* k2) /(k1 + k2). Une fois que le ratio pondéré est déterminé, la méthode calcule la luminosité de la couleur mixte. Il multiplie ensuite la luminosité par *dblLumRatio*. Si la valeur est supérieure à 1.0, la méthode définit la luminosité de la couleur mixte pour la nouvelle valeur. Sinon, la luminosité est définie sur 1.0.

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

Fait pivoter une source de contenu de contrôleur de domaine à l’intérieur du rectangle donné de 90 degrés.

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Paramètres

*rectDest*<br/>
Rectangle de destination.

*dcSrc*<br/>
Le contexte de périphérique source.

*bClockWise*<br/>
TRUE indique que Rotation + 90 degrés ; La valeur FALSE indique Rotation-90 degrés.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
