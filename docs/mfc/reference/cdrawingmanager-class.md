---
title: Classe de CDrawingManager | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 689d538c03a35175040663aedb7bd6130aae10fd
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2018
---
# <a name="cdrawingmanager-class"></a>Classe de CDrawingManager
La `CDrawingManager` classe implémente les algorithmes de dessin complexes.  
  
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
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Crée une bitmap d’indépendants du périphérique (DIB) 32 bits qui les applications peuvent écrire directement dans.|  
|[CDrawingManager::DrawAlpha](#drawalpha)|Affiche les bitmaps qui ont des pixels transparents ou semi-transparent.|  
|[CDrawingManager::DrawRotated](#drawrotated)|Fait pivoter une source de contenu de contrôleur de domaine à l’intérieur du rectangle donné par + et-90 degrés|  
|[CDrawingManager::DrawEllipse](#drawellipse)|Dessine une ellipse avec les couleurs de remplissage et la bordure fournis.|  
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Dessine un anneau et la remplit avec un dégradé de couleur.|  
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Dessine une ligne.|  
|[CDrawingManager::DrawRect](#drawrect)|Dessine un rectangle avec les couleurs de remplissage et la bordure fournis.|  
|[CDrawingManager::DrawShadow](#drawshadow)|Dessine une ombre d’une zone rectangulaire.|  
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Remplit une zone rectangulaire avec deux dégradés de couleurs.|  
|[CDrawingManager::FillGradient](#fillgradient)|Remplit une zone rectangulaire avec un dégradé de couleur spécifié.|  
|[CDrawingManager::FillGradient2](#fillgradient2)|Remplit une zone rectangulaire avec un dégradé de couleur spécifié. La direction de la modification de la couleur du dégradé est également spécifiée.|  
|[CDrawingManager::GrayRect](#grayrect)|Remplit un rectangle avec une couleur grise spécifiée.|  
|[CDrawingManager::HighlightRect](#highlightrect)|Met en surbrillance une zone rectangulaire.|  
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Convertit une couleur à partir d’une représentation sous forme de TLS pour une représentation RVB.|  
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Convertit une couleur à partir d’une représentation sous forme de TLS pour une représentation RVB.|  
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Convertit une couleur à partir d’une représentation TSL en une représentation sous forme de RVB.|  
|[CDrawingManager::HuetoRGB](#huetorgb)|Méthode d’assistance qui convertit une valeur de teinte à un composant bleu, rouge ou vert.|  
|[CDrawingManager::MirrorRect](#mirrorrect)|Renverse une zone rectangulaire.|  
|[CDrawingManager::PixelAlpha](#pixelalpha)|Méthode d’assistance qui détermine la couleur finale d’un pixel translucide.|  
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Crée une image bitmap qui peut être utilisée comme une ombre.|  
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Convertit une couleur à partir d’une représentation RVB à la représentation TSL.|  
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Convertit une couleur à partir d’une représentation RVB à la représentation TSL.|  
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Méthode d’assistance qui le colore un pixel partiellement transparent dans une image bitmap.|  
|[CDrawingManager::SetPixel](#setpixel)|Méthode d’assistance qui modifie un seul pixel dans une image bitmap avec la couleur spécifiée.|  
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combine deux couleurs selon un ratio pondéré.|  
  
## <a name="remarks"></a>Notes  
 La `CDrawingManager` classe fournit des fonctions pour les ombres, les dégradés de couleurs et les rectangles en surbrillance. Il effectue également une fusion alpha. Vous pouvez utiliser cette classe pour modifier directement l’interface utilisateur de votre application.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
 `CDrawingManager`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdrawmanager.h  
  
##  <a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager  
 Construit un [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) objet.  
  
```  
CDrawingManager(CDC& dc);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dc`  
 Une référence à un contexte de périphérique. Le `CDrawingManager` utilise ce contexte pour le dessin.  
  
##  <a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32  
 Crée une bitmap d’indépendants du périphérique (DIB) 32 bits qui les applications peuvent écrire directement dans.  
  
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
|[in] `size`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) paramètre qui indique la taille de l’image bitmap.|  
|[out] `pBits`|Un pointeur vers un pointeur de données qui reçoit l’emplacement de du fichier DIB bit des valeurs.|  
|`bitmap`|Un handle vers l’image bitmap d’origine|  
|`clrTransparent`|Une valeur RVB en spécifiant une couleur transparente de l’image bitmap d’origine.|  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle de bitmap DIB nouvellement créé si cette méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur la création d’une image bitmap DIB, consultez [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183491).  
  
##  <a name="drawalpha"></a>CDrawingManager::DrawAlpha  
 Affiche les bitmaps qui ont des pixels transparents ou semi-transparent.  
  
```  
void DrawAlpha(
    CDC* pDstDC,  
    const CRect& rectDst,  
    CDC* pSrcDC,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDstDC`  
 Pointeur vers le contexte de périphérique pour la destination.  
  
 [in] `rectDst`  
 Le rectangle de destination.  
  
 [in] `pSrcDC`  
 Pointeur vers le contexte de périphérique pour la source.  
  
 [in] `rectSrc`  
 Le rectangle source.  
  
### <a name="remarks"></a>Notes  
 Cette méthode effectue une fusion alpha de deux images. Pour plus d’informations sur la fusion alpha, consultez [AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351) dans le Kit de développement logiciel Windows.  
  
##  <a name="drawellipse"></a>CDrawingManager::DrawEllipse  
 Dessine une ellipse avec les couleurs de remplissage et la bordure fournis.  
  
```  
void DrawEllipse(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rect`  
 Le rectangle englobant de l’ellipse.  
  
 [in] `clrFill`  
 La couleur de que cette méthode utilise pour remplir l’ellipse.  
  
 [in] `clrLine`  
 La couleur de cette méthode utilise comme la bordure de l’ellipse.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne sans dessiner une ellipse si une couleur est définie sur -1. Il renvoie également sans dessiner une ellipse si une dimension du rectangle englobant est 0.  
  
##  <a name="drawgradientring"></a>CDrawingManager::DrawGradientRing  
 Dessine un anneau et la remplit avec un dégradé de couleur.  
  
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
 [in] `rect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) paramètre qui spécifie la limite de l’anneau de dégradé.  
  
 [in] `colorStart`  
 La première couleur du dégradé.  
  
 [in] `colorFinish`  
 La dernière couleur du dégradé.  
  
 [in] `colorBorder`  
 La couleur de la bordure.  
  
 [in] `nAngle`  
 Un paramètre qui spécifie l’angle du dégradé de dessin initiale. Cette valeur doit être comprise entre 0 et 360.  
  
 [in] `nWidth`  
 La largeur de la bordure de l’anneau.  
  
 [in] `clrFace`  
 La couleur de l’intérieur de l’anneau.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le rectangle défini par `rect` doivent être au moins 5 pixels larges et à 5 pixels en hauteur.  
  
##  <a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine, CDrawingManager::DrawLineA  
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
|[in] `x1`|Coordonnée x où commence à la ligne.|  
|[in] `y1`|Coordonnée y où commence à la ligne.|  
|[in] `x2`|Coordonnée x où la ligne se termine.|  
|[in] `y2`|Coordonnée y où la ligne se termine.|  
|[in] `clrLine`|La couleur de la ligne.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode échoue si `clrLine` est égal à -1.  
  
##  <a name="drawrect"></a>CDrawingManager::DrawRect  
 Dessine un rectangle avec les couleurs de remplissage et la bordure fournis.  
  
```  
void DrawRect(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rect`  
 Les limites du rectangle.  
  
 [in] `clrFill`  
 Cette méthode utilise pour remplir le rectangle de couleur.  
  
 [in] `clrLine`  
 La couleur de cette méthode utilise pour la bordure du rectangle.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne sans dessiner un rectangle, si une couleur est définie sur -1. Il renvoie également si une dimension du rectangle est 0.  
  
##  <a name="drawshadow"></a>CDrawingManager::DrawShadow  
 Dessine une ombre d’une zone rectangulaire.  
  
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
 [in] `rect`  
 Une zone rectangulaire dans votre application. Le Gestionnaire de dessin Dessine une ombre sous cette zone.  
  
 [in] `nDepth`  
 La largeur et la hauteur de l’ombre.  
  
 [in] `iMinBrightness`  
 La luminosité minimale de l’ombre.  
  
 [in] `iMaxBrightness`  
 La luminosité maximale de l’ombre.  
  
 [in] `pBmpSaveBottom`  
 Pointeur vers une image bitmap qui contient l’image pour la partie inférieure de l’ombre.  
  
 [in] `pBmpSaveRight`  
 Pointeur vers une image bitmap qui contient l’image de l’ombre est dessiné sur le côté droit du rectangle.  
  
 [in] `clrBase`  
 Couleur de l’ombre.  
  
 [in] `bRightShadow`  
 Un paramètre booléen qui indique comment l’ombre est dessinée. Si `bRightShadow` est `TRUE`, `DrawShadow` Dessine une ombre sur le côté droit du rectangle.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez fournir deux bitmaps valides pour le bas et les ombres droite en utilisant les paramètres `pBmpSaveBottom` et `pBmpSaveRight`. Si ces [CBitmap](../../mfc/reference/cbitmap-class.md) objets ont un objet GDI attaché, `DrawShadow` utilisera ces bitmaps en tant que les ombres. Si le `CBitmap` paramètres n’ont pas un objet GDI attaché, `DrawShadow` Dessine l’ombre et attache les bitmaps pour les paramètres. Dans les futures les appels à `DrawShadow`, vous pouvez fournir ces bitmaps pour accélérer le processus de dessin. Pour plus d’informations sur la `CBitmap` classe et les objets GDI, consultez [objets graphiques](../../mfc/graphic-objects.md).  
  
 Si un de ces paramètres est `NULL`, `DrawShadow` dessinera automatiquement l’ombre.  
  
 Si vous définissez `bRightShadow` à `FALSE`, l’ombre sera dessiné en dessous et à gauche de la zone rectangulaire.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `DrawShadow` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de la [exemple de démonstration de feuille de propriétés de l’abonnement](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]  
  
##  <a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient  
 Remplit une zone rectangulaire avec deux dégradés de couleurs.  
  
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
 [in] `rect`  
 Le rectangle à remplir.  
  
 [in] `colorStart1`  
 La couleur initiale du premier dégradé de couleur.  
  
 [in] `colorFinish1`  
 La couleur finale du premier dégradé de couleur.  
  
 [in] `colorStart2`  
 La couleur initiale du deuxième dégradé de couleur.  
  
 [in] `colorFinish2`  
 La couleur finale du deuxième dégradé de couleur.  
  
 [in] `bHorz`  
 Un paramètre booléen qui indique si `Fill4ColorsGradient` couleurs d’un dégradé horizontal ou vertical. `TRUE`Indique un dégradé horizontal.  
  
 [in] `nPercentage`  
 Entier compris entre 0 et 100. Cette valeur indique le pourcentage du rectangle à remplir avec la première dégradé de couleur.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un rectangle est rempli avec deux dégradés de couleur, ils sont situés au-dessus de l’autre ou à côté de l’autre, selon la valeur de `bHorz`. Chaque dégradé de couleur est calculée indépendamment avec la méthode [CDrawingManager::FillGradient](#fillgradient).  
  
 Cette méthode génère un échec d’assertion si `nPercentage` est inférieur à 0 ou supérieur à 100.  
  
##  <a name="fillgradient"></a>CDrawingManager::FillGradient  
 Remplit une zone rectangulaire avec du dégradé de couleur spécifié.  
  
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
 [in] `rect`  
 La zone rectangulaire à remplir.  
  
 [in] `colorStart`  
 La première couleur du dégradé.  
  
 [in] `colorFinish`  
 La couleur finale du dégradé.  
  
 [in] `bHorz`  
 Un paramètre booléen qui indique si `FillGradient` doit dessiner un dégradé horizontal ou vertical.  
  
 [in] `nStartFlatPercentage`  
 Le pourcentage du rectangle qui `FillGradient` remplit avec `colorStart` avant le début du dégradé.  
  
 [in] `nEndFlatPercentage`  
 Le pourcentage du rectangle qui `FillGradient` remplit avec `colorFinish` fin du dégradé.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `FillGradient` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de la [exemple de démonstration de MS Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]  
  
##  <a name="fillgradient2"></a>CDrawingManager::FillGradient2  
 Remplit une zone rectangulaire avec un dégradé de couleur spécifié.  
  
```  
void FillGradient2 (
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    int nAngle = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rect`  
 La zone rectangulaire à remplir.  
  
 [in] `colorStart`  
 La première couleur du dégradé.  
  
 [in] `colorFinish`  
 La dernière couleur du dégradé.  
  
 [in] `nAngle`  
 Nombre entier compris entre 0 et 360. Ce paramètre spécifie la direction du dégradé de couleur.  
  
### <a name="remarks"></a>Notes  
 Utilisez `nAngle` pour spécifier la direction du dégradé de couleur. Lorsque vous spécifiez la direction du dégradé de couleur, vous spécifiez également le départ du dégradé de couleur. La valeur 0 pour `nAngle` indique le dégradé démarre à partir du haut du rectangle. En tant que `nAngle` augmente, l’emplacement de départ pour le dégradé se déplace dans un sens inverse des aiguilles en fonction de l’angle.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `FillGradient2` méthode de la `CDrawingManager` classe. Cet extrait de code fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]  
  
##  <a name="grayrect"></a>CDrawingManager::GrayRect  
 Remplit un rectangle avec une couleur grise spécifiée.  
  
```  
BOOL GrayRect(
    CRect rect,  
    int nPercentage = -1,  
    COLORREF clrTransparent = (COLORREF)-1,  
    COLORREF clrDisabled = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rect`  
 La zone rectangulaire à remplir.  
  
 [in] `nPercentage`  
 Le pourcentage de votre choix dans le rectangle de gris.  
  
 [in] `clrTransparent`  
 Couleur transparente.  
  
 [in] `clrDisabled`  
 La couleur par cette méthode pour la déduplication saturation si `nPercentage` a la valeur -1.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Pour le paramètre `nPercentage`, une valeur inférieure indique une couleur plus sombre.  
  
 La valeur maximale pour `nPercentage` est 200. Une valeur supérieure à 200 ne modifie pas l’apparence du rectangle. Si la valeur est -1, cette méthode utilise `clrDisabled` pour limiter la saturation du rectangle.  
  
##  <a name="highlightrect"></a>CDrawingManager::HighlightRect  
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
 [in] `rect`  
 Une zone rectangulaire pour mettre en surbrillance.  
  
 [in] `nPercentage`  
 Un pourcentage qui indique comment transparent en surbrillance.  
  
 [in] `clrTransparent`  
 Couleur transparente.  
  
 [in] `nTolerance`  
 Un entier compris entre 0 et 255 qui indique la tolérance de couleur.  
  
 [in] `clrBlend`  
 La couleur de base pour la fusion.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Si `nPercentage` est comprise entre 0 et 99, `HighlightRect` utilise l’algorithme contrôle alpha. Pour plus d’informations sur la fusion alpha, consultez [lignes de fusion Alpha et remplissages](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Si `nPercentage` est -1, cette méthode utilise le niveau de mise en surbrillance par défaut. Si `nPercentage` est 100, cette méthode ne fait rien et retourne `TRUE`.  
  
 La méthode utilise le paramètre `nTolerance` pour déterminer s’il faut mettre en surbrillance de la zone rectangulaire. Pour mettre en surbrillance le rectangle, la différence entre la couleur d’arrière-plan de votre application et `clrTransparent` doit être inférieur à `nTolerance` dans chaque composant de couleur (rouge, vert et bleu).  
  
##  <a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE  
 Convertit une couleur à partir d’une représentation sous forme de TLS pour une représentation RVB.  
  
```  
static COLORREF __stdcall HLStoRGB_ONE(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `H`  
 Un nombre compris entre 0 et 1 qui représente la teinte de la couleur.  
  
 [in] `L`  
 Un nombre compris entre 0 et 1 qui indique la luminosité de la couleur.  
  
 [in] `S`  
 Un nombre compris entre 0 et 1 qui indique la saturation de la couleur.  
  
### <a name="return-value"></a>Valeur de retour  
 La représentation sous forme de RVB de la couleur TSL fournie.  
  
### <a name="remarks"></a>Notes  
 Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Cette méthode et la `CDrawingManager::HLStoRGB_TWO` méthode exécutent la même opération, mais requièrent des valeurs différentes pour le `H` paramètre. Dans cette méthode, `H` est un pourcentage du cercle. Dans le `CDrawingManager::HLStoRGB_TWO` (méthode), `H` est une valeur comprise entre 0 et 360, qui représentent le rouge en degrés. Par exemple, avec `HLStoRGB_ONE`, une valeur de 0,25 pour `H` est équivalente à une valeur de 90 avec `HLStoRGB_TWO`.  
  
##  <a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO  
 Convertit une couleur à partir d’une représentation sous forme de TLS pour une représentation RVB.  
  
```  
static COLORREF __stdcall HLStoRGB_TWO(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `H`  
 Un nombre compris entre 0 et 360, qui représente la teinte de la couleur.  
  
 [in] `L`  
 Un nombre compris entre 0 et 1 qui indique la luminosité de la couleur.  
  
 [in] `S`  
 Un nombre compris entre 0 et 1 qui indique la saturation de la couleur.  
  
### <a name="return-value"></a>Valeur de retour  
 La représentation sous forme de RVB de la couleur TSL fournie.  
  
### <a name="remarks"></a>Notes  
 Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Cette méthode et la [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) méthode exécutent la même opération, mais requièrent des valeurs différentes pour le `H` paramètre. Dans cette méthode, `H` est une valeur comprise entre 0 et 360, qui représentent le rouge en degrés. Dans le [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) (méthode), `H` est un pourcentage du cercle. Par exemple, avec `HLStoRGB_ONE`, une valeur de 0,25 pour `H` est équivalente à une valeur de 90 avec `HLStoRGB_TWO`.  
  
##  <a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB  
 Convertit une couleur à partir d’une représentation TSL en une représentation sous forme de RVB.  
  
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
|[in] `H`|Un nombre compris entre 0 et 360, qui indique la teinte de la couleur.|  
|[in] `S`|Un nombre compris entre 0 et 1 qui indique la saturation de la couleur.|  
|[in] `V`|Un nombre compris entre 0 et 1 qui indique la valeur de la couleur.|  
  
### <a name="return-value"></a>Valeur de retour  
 La représentation sous forme de RVB de la couleur TSL fournie.  
  
### <a name="remarks"></a>Notes  
 Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
##  <a name="huetorgb"></a>CDrawingManager::HuetoRGB  
 Convertit une valeur de teinte à un composant bleu, rouge ou vert.  
  
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
 [in] `m1`  
 Consultez la section Notes.  
  
 [in] `m2`  
 Consultez la section Notes.  
  
 [in] `h`  
 Consultez la section Notes.  
  
 [in] `rm1`  
 Consultez la section Notes.  
  
 [in] `rm2`  
 Consultez la section Notes.  
  
 [in] `rh`  
 Consultez la section Notes.  
  
### <a name="return-value"></a>Valeur de retour  
 Le composant de rouge, vert ou bleu individuelles pour la teinte fourni.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est une méthode d’assistance qui la `CDrawingManager` classe utilise pour calculer les composants rouges, verts et bleus individuels d’une couleur dans une représentation TSL ou TSL. Cette méthode n’est pas conçue pour être appelée directement par le programmeur. Les paramètres d’entrée sont des valeurs qui varient selon l’algorithme de conversion.  
  
 Pour convertir une couleur TSL ou TSL en une représentation RVB, appelez l’une des méthodes suivantes :  
  
- [CDrawingManager::HSVtoRGB](#hsvtorgb)  
  
- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)  
  
- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)  
  
##  <a name="mirrorrect"></a>CDrawingManager::MirrorRect  
 Renverse une zone rectangulaire.  
  
```  
void MirrorRect(
    CRect rect,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rect`  
 Le rectangle englobant de la zone à retourner.  
  
 [in] `bHorz`  
 Un paramètre booléen qui indique si le rectangle est retournée horizontalement ou verticalement.  
  
### <a name="remarks"></a>Notes  
 Cette méthode peut retourner toute zone du contexte de périphérique détenu par le `CDrawingManager` classe. Si `bHorz` a la valeur `TRUE`, cette méthode retourne la zone horizontalement. Sinon, elle retourne verticalement la zone.  
  
##  <a name="pixelalpha"></a>CDrawingManager::PixelAlpha  
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
 [in] `srcPixel`  
 La couleur initiale du pixel.  
  
 [in] `percent`  
 Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence. Une valeur de 100 indique que la couleur initiale est totalement transparente.  
  
 [in] `percentR`  
 Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant rouge.  
  
 [in] `percentG`  
 Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant vert.  
  
 [in] `percentB`  
 Un nombre compris entre 0 et 100 qui représente le pourcentage de transparence pour le composant bleu.  
  
 [in] `dstPixel`  
 La couleur de base pour le pixel.  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur finale du pixel translucide.  
  
### <a name="remarks"></a>Notes  
 Ceci est une classe d’assistance pour la coloration des bitmaps translucides et n’est pas conçue pour être appelée directement par le programmeur.  
  
 Lorsque vous utilisez la version de la méthode qui a `dstPixel`, la couleur finale est une combinaison de `dstPixel` et `srcPixel`. Le `srcPixel` la couleur est partiellement transparente sur la couleur de base de `dstPixel`.  
  
##  <a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask  
 Crée une image bitmap qui peut être utilisée comme une ombre.  
  
```  
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,  
    COLORREF clrBase,  
    int iMinBrightness = 0,  
    int iMaxBrightness = 100);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nDepth`  
 La largeur et la hauteur de l’ombre.  
  
 [in] `clrBase`  
 Couleur de l’ombre.  
  
 [in] `iMinBrightness`  
 La luminosité minimale de l’ombre.  
  
 [in] `iMaxBrightness`  
 La luminosité maximale de l’ombre.  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle vers le bitmap créée si cette méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Notes  
 Si `nDepth` est définie sur 0, cette méthode se termine et retourne `NULL`. Si `nDepth` est inférieure à 3, la largeur et la hauteur de l’ombre sont définies de 3 pixels.  
  
##  <a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL  
 Convertit une couleur à partir d’une représentation sous forme rouge, verte et bleue (RVB) une teinte, saturation et de la représentation sous forme de luminosité (TSL).  
  
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
|[in] `rgb`|La couleur de valeurs RVB.|  
|[out] `H`|Pointeur vers un double où la méthode stocke la teinte de la couleur.|  
|[out] `S`|Pointeur vers un double où la méthode stocke la saturation de la couleur.|  
|[out] `L`|Pointeur vers un double où la méthode stocke la luminosité de la couleur.|  
  
### <a name="remarks"></a>Notes  
 Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 La valeur retournée pour `H` est représentée comme une fraction comprise entre 0 et 1, où 0 et 1 représentent rouge. Les valeurs renvoyées pour `S` et `L` sont des nombres compris entre 0 et 1.  
  
##  <a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV  
 Convertit une couleur à partir d’une représentation RVB à la représentation TSL.  
  
```  
static void __stdcall RGBtoHSV(
    COLORREF rgb,  
    double* H,  
    double* S,  
    double* V);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rgb`  
 La couleur à convertir en une représentation RVB.  
  
 [out] `H`  
 Pointeur vers un double où cette méthode stocke la teinte résultante de la couleur.  
  
 [out] `S`  
 Pointeur vers un double où cette méthode stocke la saturation obtenue pour la couleur.  
  
 [out] `V`  
 Pointeur vers un double où cette méthode stocke la valeur obtenue pour la couleur.  
  
### <a name="remarks"></a>Notes  
 Une couleur peut être représentée comme TSL (teinte, saturation et valeur), TSL (teinte, saturation et luminosité) ou RVB (rouge, vert et bleu). Pour plus d’informations sur les différentes représentations sous forme de couleur, consultez [couleur](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 La valeur retournée pour `H` est un nombre compris entre 0 et 360, où 0 et 360 indiquent rouge. Les valeurs de retour pour `S` et `V` sont des nombres compris entre 0 et 1.  
  
##  <a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel  
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
 [in] `pBits`  
 Pointeur vers les valeurs de bits de l’image bitmap.  
  
 [in] `rect`  
 Une zone rectangulaire dans votre application. Le Gestionnaire de dessin Dessine une ombre sous et à droite de cette zone.  
  
 [in] `x`  
 Coordonnée horizontale du pixel de couleur.  
  
 [in] `y`  
 Coordonnée verticale du pixel de couleur.  
  
 [in] `percent`  
 Le pourcentage de transparence.  
  
 [in] `iShadowSize`  
 La largeur et la hauteur de l’ombre.  
  
 [in] `clrBase`  
 Couleur de l’ombre.  
  
 [in] `bIsRight`  
 Un paramètre booléen qui indique les pixels de couleur. Pour plus d'informations, consultez la section Notes.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est une méthode d’assistance qui est utilisée par le [CDrawingManager::DrawShadow](#drawshadow) (méthode). Nous recommandons que si vous souhaitez ajouter une ombre, appelez `CDrawingManager::DrawShadow` à la place.  
  
 Si `bIsRight` a la valeur `TRUE`, le pixel de couleur est mesuré `x` pixels du bord droit de `rect`. S’il s’agit `FALSE`, le pixel de couleur est mesuré `x` pixels du bord gauche de `rect`.  
  
##  <a name="setpixel"></a>CDrawingManager::SetPixel  
 Modifie un seul pixel dans une image bitmap avec la couleur spécifiée.  
  
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
|[in] `pBits`|Pointeur vers les valeurs de bits de l’image bitmap.|  
|[in] `cx`|La largeur totale de l’image bitmap.|  
|[in] `cy`|La hauteur totale de l’image bitmap.|  
|[in] `x`|Coordonnée x du pixel dans l’image bitmap à modifier.|  
|[in] `y`|Coordonnée y du pixel dans l’image bitmap à modifier.|  
|[in] `color`|La nouvelle couleur du pixel identifié par les coordonnées fournies.|  
  
##  <a name="smartmixcolors"></a>CDrawingManager::SmartMixColors  
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
|[in] `color1`|La première couleur à combiner.|  
|[in] `color2`|La deuxième couleur à combiner.|  
|[in] `dblLumRatio`|Le rapport pour la luminosité de la nouvelle couleur. `SmartMixColors`Multiplie la luminosité de la couleur mixte par ce rapport avant de déterminer la couleur finale.|  
|[in] `k1`|Le taux pondéré pour la première couleur.|  
|[in] `k2`|Le taux pondéré pour la deuxième couleur.|  
  
### <a name="return-value"></a>Valeur de retour  
 Couleur qui représente un mélange pondéré des couleurs fournis.  
  
### <a name="remarks"></a>Notes  
 Cette méthode échoue avec une erreur si le `k1` ou `k2` est inférieur à zéro. Si ces deux paramètres sont définies sur 0, la méthode retourne `RGB(0, 0, 0)`.  
  
 Le rapport pondéré est calculé avec la formule suivante : (color1 * k1 + color2 \* k2) /(k1 + k2). Une fois le rapport pondéré est déterminé, la méthode calcule la luminosité de la couleur mixte. Il multiplie ensuite la luminosité par `dblLumRatio`. Si la valeur est supérieure à la version 1.0, la méthode définit la luminosité de la couleur mixte à la nouvelle valeur. Sinon, la luminosité est la valeur 1.0.  
  
##  <a name="drawrotated"></a>CDrawingManager::DrawRotated  
 Une source de contenu de contrôleur de domaine à l’intérieur du rectangle donné fait pivoter de 90 degrés.  
  
```  
void DrawRotated(
    CRect rectDest,  
    CDC& dcSrc,  
    BOOL bClockWise);
```  
  
### <a name="parameters"></a>Paramètres  
 `rectDest`  
 Rectangle de destination.  
  
 `dcSrc`  
 Le contexte du périphérique source.  
  
 `bClockWise`  
 `TRUE`Indique la rotation + 90 degrés ; `FALSE` indique la rotation-90 degrés.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
