---
title: Classe CDrawingManager
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
ms.openlocfilehash: 73c5775c2cb83dea79401615b31f2194094fac8e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753238"
---
# <a name="cdrawingmanager-class"></a>Classe CDrawingManager

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
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Crée un bit-bit indépendant de l’appareil (DIB) que les applications peuvent écrire directement.|
|[CDrawingManager::DRawAlpha](#drawalpha)|Affiche des bitmaps qui ont des pixels transparents ou semi-transparents.|
|[CDrawingManager::DrawRotated](#drawrotated)|Tourne un contenu DC source à l’intérieur du rectangle donné par 90 degrés|
|[CDrawingManager::DrawEllipse](#drawellipse)|Dessine une ellipse avec le remplissage fourni et les couleurs de bordure.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Dessine une bague et la remplit d’un gradient de couleur.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Trace une ligne.|
|[CDrawingManager::DrawRect](#drawrect)|Dessine un rectangle avec le remplissage fourni et les couleurs de bordure.|
|[CDrawingManager::DrawShadow](#drawshadow)|Dessine une ombre pour une zone rectangulaire.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Remplit une zone rectangulaire avec deux gradients de couleur.|
|[CDrawingManager::FillGradient](#fillgradient)|Remplit une zone rectangulaire avec un gradient de couleur spécifié.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Remplit une zone rectangulaire avec un gradient de couleur spécifié. La direction du changement de couleur du gradient est également spécifiée.|
|[CDrawingManager::GrayRect](#grayrect)|Remplit un rectangle d’une couleur grise spécifiée.|
|[CDrawingManager::HighlightRect](#highlightrect)|Met en évidence une zone rectangulaire.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Convertit une couleur d’une représentation HLS à une représentation RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Convertit une couleur d’une représentation HLS à une représentation RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Convertit une couleur d’une représentation HSV à une représentation RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Méthode d’aide qui convertit une valeur de teinte en un composant rouge, vert ou bleu.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Retourne une zone rectangulaire.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Méthode d’aide qui détermine la couleur finale pour un pixel semi-transparent.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Crée un bitmap qui peut être utilisé comme une ombre.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Convertit une couleur d’une représentation RGB à une représentation HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Convertit une couleur d’une représentation RGB à une représentation HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Méthode d’aide qui colore un pixel partiellement transparent dans un bitmap.|
|[CDrawingManager::SetPixel](#setpixel)|Méthode d’aide qui change un seul pixel dans une bitmap à la couleur spécifiée.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combine deux couleurs basées sur un rapport pondéré.|

## <a name="remarks"></a>Notes

La `CDrawingManager` classe fournit des fonctions pour dessiner des ombres, des dégradés de couleur et des rectangles surlignés. Il effectue également l’alpha-mélange. Vous pouvez utiliser cette classe pour modifier directement l’interface utilisateur de votre application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdrawmanager.h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

Construit un objet [CDrawingManager.](../../mfc/reference/cdrawingmanager-class.md)

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Paramètres

*Dc*<br/>
[dans] Une référence au contexte d’un appareil. L’utilisation `CDrawingManager` de ce contexte pour le dessin.

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32

Crée un bit-bit indépendant de l’appareil (DIB) que les applications peuvent écrire directement.

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
|*size*|[dans] Un [paramètre CSize](../../atl-mfc-shared/reference/csize-class.md) qui indique la taille de la bitmap.|
|*pBits (en)*|[out] Un pointeur à un pointeur de données qui reçoit l’emplacement des valeurs bits de la DIB.|
|*Bitmap*|Une poignée à la bitmap d’origine|
|*clrTransparent*|Une valeur RGB spécifiant la couleur transparente de la bitmap d’origine.|

### <a name="return-value"></a>Valeur de retour

Une poignée à la bitmap nouvellement créée DIB si cette méthode est réussie; autrement NULL.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la façon de créer un bitmap DIB, voir [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a>CDrawingManager::DRawAlpha

Affiche des bitmaps qui ont des pixels transparents ou semi-transparents.

```cpp
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Paramètres

*pDstDC (en)*<br/>
[dans] Un pointeur vers le contexte de l’appareil pour la destination.

*rectDst*<br/>
[dans] Le rectangle de destination.

*pSrcDC (en)*<br/>
[dans] Un pointeur sur le contexte de l’appareil pour la source.

*rectSrc*<br/>
[dans] Le rectangle source.

### <a name="remarks"></a>Notes

Cette méthode effectue l’alpha-mélange pour deux bitmaps. Pour plus d’informations sur le mélange d’alpha, voir [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) dans le SDK Windows.

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a>CDrawingManager::DrawEllipse

Dessine une ellipse avec le remplissage fourni et les couleurs de bordure.

```cpp
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[dans] Le rectangle de délimitation pour l’ellipse.

*clrFill*<br/>
[dans] La couleur que cette méthode utilise pour remplir l’ellipse.

*clrLine*<br/>
[dans] La couleur que cette méthode utilise comme bordure de l’ellipse.

### <a name="remarks"></a>Notes

Cette méthode revient sans dessiner une ellipse si l’une ou l’autre couleur est réglée à -1. Il revient également sans tirer une ellipse si l’une ou l’autre dimension du rectangle de délimitation est de 0.

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a>CDrawingManager::DrawGradientRing

Dessine une bague et la remplit d’un gradient de couleur.

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

*Rect*<br/>
[dans] Un [paramètre CRect](../../atl-mfc-shared/reference/crect-class.md) qui spécifie la limite de l’anneau de gradient.

*colorStart*<br/>
[dans] La première couleur pour le gradient.

*colorFinish*<br/>
[dans] La dernière couleur pour le gradient.

*colorBorder*<br/>
[dans] La couleur de la frontière.

*nAngle (en)*<br/>
[dans] Un paramètre qui spécifie l’angle de dessin initial. Cette valeur devrait être comprise entre 0 et 360.

*nWidth (en)*<br/>
[dans] La largeur de la bordure pour l’anneau.

*clrFace*<br/>
[dans] La couleur de l’intérieur de l’anneau.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le rectangle défini par *rect* doit être d’au moins 5 pixels de large et 5 pixels de haut.

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Trace une ligne.

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

|||
|-|-|
|Paramètre|Description|
|*x1*|[dans] La coordonnées x où la ligne commence.|
|*y1 (en)*|[dans] La coordonnées y où la ligne commence.|
|*x2*|[dans] La coordonnées x où la ligne se termine.|
|*y2*|[dans] La coordonnées y où la ligne se termine.|
|*clrLine*|[dans] La couleur de la ligne.|

### <a name="remarks"></a>Notes

Cette méthode échoue si *clrLine* équivaut à -1.

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a>CDrawingManager::DrawRect

Dessine un rectangle avec le remplissage fourni et les couleurs de bordure.

```cpp
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[dans] Les limites du rectangle.

*clrFill*<br/>
[dans] La couleur que cette méthode utilise pour remplir le rectangle.

*clrLine*<br/>
[dans] La couleur que cette méthode utilise pour la bordure du rectangle.

### <a name="remarks"></a>Notes

Cette méthode revient sans dessiner un rectangle si l’une ou l’autre couleur est réglée à -1. Il revient également si l’une ou l’autre dimension du rectangle est de 0.

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a>CDrawingManager::DrawShadow

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

*Rect*<br/>
[dans] Une zone rectangulaire dans votre application. Le directeur du dessin dessiner dessinera une ombre sous cette zone.

*nDepth*<br/>
[dans] La largeur et la hauteur de l’ombre.

*iMinBrightness iMinBrightness iMinBrightness iMin*<br/>
[dans] La luminosité minimale de l’ombre.

*iMaxBrightness (en)*<br/>
[dans] La luminosité maximale de l’ombre.

*pBmpSaveBottom*<br/>
[dans] Un pointeur à un bitmap qui contient l’image pour la partie inférieure de l’ombre.

*pBmpSaveRight*<br/>
[dans] Un pointeur à un bitmap qui contient l’image pour l’ombre qui est dessiné sur le côté droit du rectangle.

*clrBase (en)*<br/>
[dans] La couleur de l’ombre.

*bRightShadow*<br/>
[dans] Un paramètre Boolean qui indique comment l’ombre est dessinée. Si *bRightShadow* est `TRUE`, `DrawShadow` dessine une ombre sur le côté droit du rectangle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez fournir deux bitmaps valides pour les ombres inférieures et droites en utilisant les paramètres *pBmpSaveBottom* et *pBmpSaveRight*. Si ces objets [CBitmap](../../mfc/reference/cbitmap-class.md) ont un `DrawShadow` objet GDI attaché, utilisera ces bitmaps comme ombres. Si `CBitmap` les paramètres n’ont pas d’objet GDI attaché, `DrawShadow` dessine l’ombre et attache les bitmaps aux paramètres. Dans les `DrawShadow`appels futurs à , vous pouvez fournir ces bitmaps pour accélérer le processus de dessin. Pour plus d’informations sur la classe et les `CBitmap` objets GDI, voir Objets [graphiques](../../mfc/graphic-objects.md).

Si l’un de `NULL` `DrawShadow` ces paramètres est, va automatiquement dessiner l’ombre.

Si vous définissez *bRightShadow* à FALSE, l’ombre sera dessinée en dessous et à gauche de la zone rectangulaire.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `DrawShadow` utiliser `CDrawingManager` la méthode de la classe. Cet extrait de code fait partie de [l’échantillon Demo Prop Sheet](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient

Remplit une zone rectangulaire avec deux gradients de couleur.

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

*Rect*<br/>
[dans] Le rectangle à remplir.

*colorStart1 (en)*<br/>
[dans] La couleur initiale pour le premier gradient de couleur.

*colorFinish1*<br/>
[dans] La couleur finale pour le premier gradient de couleur.

*colorStart2 (en)*<br/>
[dans] La couleur initiale pour le deuxième gradient de couleur.

*colorFinish2*<br/>
[dans] La couleur finale pour le deuxième gradient de couleur.

*bHorz (en)*<br/>
[dans] Un paramètre Boolean `Fill4ColorsGradient` qui indique si les couleurs d’un gradient horizontal ou vertical. TRUE indique un gradient horizontal.

*nPercentage (en)*<br/>
[dans] Un integer de 0-100. Cette valeur indique le pourcentage du rectangle à remplir avec le premier gradient de couleur.

### <a name="remarks"></a>Notes

Quand un rectangle est rempli de deux gradients de couleur, ils sont soit situés au-dessus de l’autre ou à côté de l’autre, selon la valeur de *bHorz*. Chaque gradient de couleur est calculé indépendamment avec la méthode [CDrawingManager::FillGradient](#fillgradient).

Cette méthode génère un échec d’affirmation si *nPercentage* est inférieur à 0 ou plus de 100.

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a>CDrawingManager::FillGradient

Remplit une zone rectangulaire avec le gradient de couleur spécifié.

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

*Rect*<br/>
[dans] La zone rectangulaire à remplir.

*colorStart*<br/>
[dans] La première couleur pour le gradient.

*colorFinish*<br/>
[dans] La couleur finale pour le gradient.

*bHorz (en)*<br/>
[dans] Un paramètre Boolean qui `FillGradient` précise s’il doit dessiner un gradient horizontal ou vertical.

*nStartFlatPercentage*<br/>
[dans] Le pourcentage du `FillGradient` rectangle qui se remplit de *couleurStart* avant qu’il ne commence le gradient.

*nEndFlatPercentage*<br/>
[dans] Le pourcentage du `FillGradient` rectangle qui se remplit de *couleurFinish* après qu’il termine le gradient.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `FillGradient` utiliser `CDrawingManager` la méthode de la classe. Cet extrait de code fait partie de [l’échantillon de démonstration ms Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a>CDrawingManager::FillGradient2

Remplit une zone rectangulaire avec un gradient de couleur spécifié.

```cpp
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[dans] La zone rectangulaire à remplir.

*colorStart*<br/>
[dans] La première couleur du gradient.

*colorFinish*<br/>
[dans] La dernière couleur du gradient.

*nAngle (en)*<br/>
[dans] Un intégrant entre 0 et 360. Ce paramètre spécifie la direction du gradient de couleur.

### <a name="remarks"></a>Notes

Utilisez *nAngle* pour spécifier la direction du gradient de couleur. Lorsque vous spécifiez la direction du gradient de couleur, vous spécifiez également où le gradient de couleur commence. Une valeur de 0 pour *nAngle* indique que le gradient commence par le haut du rectangle. Comme *nAngle* augmente, l’emplacement de départ pour le gradient se déplace dans une direction dans le sens inverse des aiguilles d’une montre en fonction de l’angle.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `FillGradient2` utiliser `CDrawingManager` la méthode de la classe. Cet extrait de code fait partie de [l’échantillon De Nouveaux Contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a>CDrawingManager::GrayRect

Remplit un rectangle d’une couleur grise spécifiée.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[dans] La zone rectangulaire à remplir.

*nPercentage (en)*<br/>
[dans] Le pourcentage de gris que vous voulez dans le rectangle.

*clrTransparent*<br/>
[dans] La couleur transparente.

*clrDisable*<br/>
[dans] La couleur que cette méthode utilise pour la désétaturation si *nPercentage* est réglé à -1.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Pour le paramètre *nPercentage*, une valeur inférieure indique une couleur plus foncée.

La valeur maximale pour *nPercentage* est de 200. Une valeur supérieure à 200 ne change pas l’apparence du rectangle. Si la valeur est de -1, cette méthode utilise *clrDisabled* pour limiter la saturation du rectangle.

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a>CDrawingManager::HighlightRect

Met en évidence une zone rectangulaire.

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[dans] Une zone rectangulaire à mettre en évidence.

*nPercentage (en)*<br/>
[dans] Un pourcentage qui indique la transparence du point culminant.

*clrTransparent*<br/>
[dans] La couleur transparente.

*nTolerance (en)*<br/>
[dans] Un intégrier entre 0 et 255 qui indique la tolérance aux couleurs.

*clrBlend*<br/>
[dans] La couleur de base pour le mélange.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode est réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Si *nPercentage* se situe entre 0 et 99, `HighlightRect` utilise l’algorithme de mélange alpha. Pour plus d’informations sur le mélange alpha, voir [Alpha Blending Lines and Fills](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Si *nPercentage* est de -1, cette méthode utilise le niveau de surbrillance par défaut. Si *nPercentage* est de 100, cette méthode ne fait rien et retourne VRAI.

La méthode utilise le paramètre *nTolerance* pour déterminer s’il faut mettre en évidence la zone rectangulaire. Pour mettre en évidence le rectangle, la différence entre la couleur de fond de votre application et *clrTransparent* doit être inférieure à *nTolerance* dans chaque composant de couleur (rouge, vert et bleu).

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

Convertit une couleur d’une représentation HLS à une représentation RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Paramètres

*H (en)*<br/>
[dans] Un nombre entre 0 et 1 qui représente la teinte pour la couleur.

*L*<br/>
[dans] Un nombre entre 0 et 1 qui indique la luminosité de la couleur.

*S*<br/>
[dans] Un nombre entre 0 et 1 qui indique la saturation de la couleur.

### <a name="return-value"></a>Valeur de retour

La représentation RGB de la couleur HLS fourni.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous le titre HSV (hue, saturation et valeur), HSL (teinte, saturation et luminosité), ou RGB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, voir [Couleur](/windows/win32/uxguide/vis-color).

Cette méthode `CDrawingManager::HLStoRGB_TWO` et la méthode effectuent la même opération, mais nécessitent des valeurs différentes pour le paramètre *H.* Dans cette méthode, *H* est un pourcentage du cercle. Dans `CDrawingManager::HLStoRGB_TWO` la méthode, *H* est une valeur de degré entre 0 et 360, qui représentent tous deux le rouge. Par exemple, `HLStoRGB_ONE`avec , une valeur de 0,25 pour *H* `HLStoRGB_TWO`est équivalent à une valeur de 90 avec .

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

Convertit une couleur d’une représentation HLS à une représentation RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Paramètres

*H (en)*<br/>
[dans] Un nombre entre 0 et 360 qui représente la teinte pour la couleur.

*L*<br/>
[dans] Un nombre entre 0 et 1 qui indique la luminosité de la couleur.

*S*<br/>
[dans] Un nombre entre 0 et 1 qui indique la saturation de la couleur.

### <a name="return-value"></a>Valeur de retour

La représentation RGB de la couleur HLS fourni.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous le titre HSV (hue, saturation et valeur), HSL (teinte, saturation et luminosité), ou RGB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, voir [Couleur](/windows/win32/uxguide/vis-color).

Cette méthode et le [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) méthode effectuent la même opération, mais nécessitent des valeurs différentes pour le paramètre *H.* Dans cette méthode, *H* est une valeur de degré entre 0 et 360, qui représentent tous deux le rouge. Dans le [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) méthode, *H* est un pourcentage du cercle. Par exemple, `HLStoRGB_ONE`avec , une valeur de 0,25 pour *H* `HLStoRGB_TWO`est équivalent à une valeur de 90 avec .

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

Convertit une couleur d’une représentation HSV à une représentation RGB.

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
|*H (en)*|[dans] Un nombre entre 0 et 360 qui indique la teinte pour la couleur.|
|*S*|[dans] Un nombre entre 0 et 1 qui indique la saturation de la couleur.|
|*C*|[dans] Un nombre entre 0 et 1 qui indique la valeur de la couleur.|

### <a name="return-value"></a>Valeur de retour

La représentation RGB de la couleur HSV fourni.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous le titre HSV (hue, saturation et valeur), HSL (teinte, saturation et luminosité), ou RGB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, voir [Couleur](/windows/win32/uxguide/vis-color).

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a>CDrawingManager::HuetoRGB

Convertit une valeur de teinte en un composant rouge, vert ou bleu.

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
[dans] Voir Remarques.

*m2*<br/>
[dans] Voir Remarques.

*h*<br/>
[dans] Voir Remarques.

*rm1*<br/>
[dans] Voir Remarques.

*rm2*<br/>
[dans] Voir Remarques.

*rh rh*<br/>
[dans] Voir Remarques.

### <a name="return-value"></a>Valeur de retour

Le composant rouge, vert ou bleu individuel pour la teinte fournie.

### <a name="remarks"></a>Notes

Cette méthode est une méthode `CDrawingManager` d’aide que la classe utilise pour calculer les différents composants rouges, verts et bleus d’une couleur dans une représentation HSV ou HSL. Cette méthode n’est pas conçue pour être appelée directement par le programmeur. Les paramètres d’entrée sont des valeurs qui dépendent de l’algorithme de conversion.

Pour convertir une couleur HSV ou HSL en une représentation RGB, appelez l’une des méthodes suivantes :

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a>CDrawingManager::MirrorRect

Retourne une zone rectangulaire.

```cpp
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[dans] Le rectangle de délimitation de la zone à retourner.

*bHorz (en)*<br/>
[dans] Un paramètre Boolean qui indique si le rectangle se retourne horizontalement ou verticalement.

### <a name="remarks"></a>Notes

Cette méthode peut retourner n’importe quelle `CDrawingManager` zone du contexte de l’appareil appartenant à la classe. Si *bHorz* est réglé sur TRUE, cette méthode retourne la zone horizontalement. Sinon, il retourne la zone verticalement.

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a>CDrawingManager::PixelAlpha

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
[dans] La couleur initiale pour le pixel.

*pour cent*<br/>
[dans] Un nombre entre 0 et 100 qui représente le pourcentage de transparence. Une valeur de 100 indique que la couleur initiale est complètement transparente.

*percentR (en anglais)*<br/>
[dans] Un nombre entre 0 et 100 qui représente le pourcentage de transparence pour la composante rouge.

*percentG*<br/>
[dans] Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour la composante verte.

*percentB (en anglais)*<br/>
[dans] Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour la composante bleue.

*dstPixel*<br/>
[dans] La couleur de base pour le pixel.

### <a name="return-value"></a>Valeur de retour

La couleur finale pour le pixel semi-transparent.

### <a name="remarks"></a>Notes

Il s’agit d’une classe d’aide pour la coloration des bitmaps semi-transparents et n’est pas conçu pour être appelé directement par le programmeur.

Lorsque vous utilisez la version de la méthode qui a *dstPixel*, la couleur finale est une combinaison de *dstPixel* et *srcPixel*. La couleur *srcPixel* est la couleur partiellement transparente sur la couleur de base de *dstPixel*.

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask

Crée un bitmap qui peut être utilisé comme une ombre.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Paramètres

*nDepth*<br/>
[dans] La largeur et la hauteur de l’ombre.

*clrBase (en)*<br/>
[dans] La couleur de l’ombre.

*iMinBrightness iMinBrightness iMinBrightness iMin*<br/>
[dans] La luminosité minimale de l’ombre.

*iMaxBrightness (en)*<br/>
[dans] La luminosité maximale de l’ombre.

### <a name="return-value"></a>Valeur de retour

Une poignée à la bitmap créée si cette méthode est réussie; autrement NULL.

### <a name="remarks"></a>Notes

Si *nDepth* est réglé à 0, cette méthode sort et renvoie NULL. Si *nDepth* est inférieur à 3, la largeur et la hauteur de l’ombre sont réglées à 3 pixels.

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL

Convertit une couleur d’une représentation rouge, verte et bleue (RGB) à une représentation de teinte, de saturation et de légèreté (HSL).

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
|*Rvb*|[dans] La couleur dans les valeurs RGB.|
|*H (en)*|[out] Un pointeur à un double où la méthode stocke la teinte pour la couleur.|
|*S*|[out] Un pointeur à un double où la méthode stocke la saturation pour la couleur.|
|*L*|[out] Un pointeur à un double où la méthode stocke la légèreté pour la couleur.|

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous le titre HSV (hue, saturation et valeur), HSL (teinte, saturation et luminosité), ou RGB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, voir [Couleur](/windows/win32/uxguide/vis-color).

La valeur retournée pour *H* est représentée comme une fraction entre 0 et 1 où les deux 0 et 1 représentent rouge. Les valeurs retournées pour *S* et *L* sont des nombres compris entre 0 et 1.

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

Convertit une couleur d’une représentation RGB à une représentation HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Paramètres

*Rvb*<br/>
[dans] La couleur à convertir dans une représentation RGB.

*H (en)*<br/>
[out] Un pointeur à un double où cette méthode stocke la teinte résultante pour la couleur.

*S*<br/>
[out] Un pointeur à un double où cette méthode stocke la saturation résultante pour la couleur.

*C*<br/>
[out] Un pointeur à un double où cette méthode stocke la valeur résultante pour la couleur.

### <a name="remarks"></a>Notes

Une couleur peut être représentée sous le titre HSV (hue, saturation et valeur), HSL (teinte, saturation et luminosité), ou RGB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations de couleur, voir [Couleur](/windows/win32/uxguide/vis-color).

La valeur retournée pour *H* est un nombre entre 0 et 360 où les deux 0 et 360 indiquent rouge. Les valeurs *de* rendement pour S et *V* sont des nombres compris entre 0 et 1.

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel

Couleurs d’un pixel transparent dans un bitmap.

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

*pBits (en)*<br/>
[dans] Un pointeur sur les valeurs de bits pour la bitmap.

*Rect*<br/>
[dans] Une zone rectangulaire dans votre application. Le dessinateur dessine une ombre en dessous et à droite de cette zone.

*x*<br/>
[dans] La coordonnées horizontales du pixel à la couleur.

*y*<br/>
[dans] La coordonnées verticales du pixel à la couleur.

*pour cent*<br/>
[dans] Le pourcentage de transparence.

*iShadowSize*<br/>
[dans] La largeur et la hauteur de l’ombre.

*clrBase (en)*<br/>
[dans] La couleur de l’ombre.

*bIsRight (En)*<br/>
[dans] Un paramètre Boolean qui indique quel pixel à colorier. Pour plus d'informations, consultez la section Remarques.

### <a name="remarks"></a>Notes

Cette méthode est une méthode d’aide qui est utilisée par la méthode [CDrawingManager::DrawShadow.](#drawshadow) Nous vous recommandons que si vous `CDrawingManager::DrawShadow` voulez dessiner une ombre, appelez plutôt.

Si *bIsRight* est réglé sur TRUE, le pixel à la couleur est mesuré *x* pixels à partir du bord droit de *rect*. Si c’est FALSE, le pixel à la couleur est mesuré *x* pixels à partir du bord gauche de *rect*.

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a>CDrawingManager::SetPixel

Change un seul pixel dans un bitmap à la couleur spécifiée.

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
|*pBits (en)*|[dans] Un pointeur sur les valeurs bits de la bitmap.|
|*Cx*|[dans] La largeur totale de la bitmap.|
|*Cy*|[dans] La hauteur totale de la bitmap.|
|*x*|[dans] La x-coordonner le pixel dans la bitmap pour changer.|
|*y*|[dans] La y-coordinate du pixel dans la bitmap pour changer.|
|*Couleur*|[dans] La nouvelle couleur du pixel identifiée par les coordonnées fournies.|

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a>CDrawingManager::SmartMixColors

Combine deux couleurs basées sur un rapport pondéré.

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
|*color1*|[dans] La première couleur à mélanger.|
|*couleur2*|[dans] La deuxième couleur à mélanger.|
|*dblLumRatio*|[dans] Le rapport pour la luminosité de la nouvelle couleur. `SmartMixColors`multiplie la luminosité de la couleur mixte par ce rapport avant de déterminer une couleur finale.|
|*k1*|[dans] Le rapport pondéré pour la première couleur.|
|*k2*|[dans] Le rapport pondéré pour la deuxième couleur.|

### <a name="return-value"></a>Valeur de retour

Une couleur qui représente un mélange pondéré des couleurs fournies.

### <a name="remarks"></a>Notes

Cette méthode échoue avec une erreur si *k1* ou *k2* est inférieur à zéro. Si ces deux paramètres sont réglés à `RGB(0, 0, 0)`0, la méthode revient .

Le rapport pondéré est calculé avec la \* formule suivante : \* (couleur1 k1 - color2 k2)/(k1 k2). Une fois le rapport pondéré déterminé, la méthode calcule la luminosité de la couleur mixte. Il multiplie ensuite la luminosité par *dblLumRatio*. Si la valeur est supérieure à 1.0, la méthode définit la luminosité de la couleur mixte à la nouvelle valeur. Dans le cas contraire, la luminosité est réglée à 1,0.

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a>CDrawingManager::DrawRotated

Tourne un contenu DC source à l’intérieur du rectangle donné de 90 degrés.

```cpp
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Paramètres

*rectDest*<br/>
Rectangle de destination.

*dcSrc (en)*<br/>
Le contexte de l’appareil source.

*bClockWise (enchevêtrement)*<br/>
TRUE indique la rotation de 90 degrés; FALSE indique une rotation de -90 degrés.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
