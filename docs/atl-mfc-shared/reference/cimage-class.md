---
title: CImage, classe | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
dev_langs:
- C++
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e98bfb2922f95e75ef54f45c153f9ea80eb7d80e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758259"
---
# <a name="cimage-class"></a>CImage (classe)

`CImage` Fournit une prise en charge améliorée des images bitmap, y compris la possibilité de charger et enregistrer des images dans les formats JPEG, GIF, BMP et PNG Portable Network Graphics ().

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CImage
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CImage::CImage](#cimage)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|Affiche les bitmaps qui ont des pixels transparents ou semi-transparent.|
|[CImage::Attach](#attach)|Attache un HBITMAP pour un `CImage` objet. Utilisable avec les bitmaps de section non DIB ou DIB section bitmaps.|
|[CImage::BitBlt](#bitblt)|Copie une image bitmap à partir du contexte de périphérique source vers ce contexte de périphérique en cours.|
|[CImage::Create](#create)|Crée une bitmap de section DIB et l’attache à précédemment construit `CImage` objet.|
|[CImage::CreateEx](#createex)|Crée une image bitmap à la section DIB (avec des paramètres supplémentaires) et l’attache à précédemment construit `CImage` objet.|
|[CImage::Destroy](#destroy)|Détache la bitmap à partir de la `CImage` de l’objet et détruit la bitmap.|
|[CImage::Detach](#detach)|Détache la bitmap à partir d’un `CImage` objet.|
|[CImage::Draw](#draw)|Copie une image bitmap à partir d’un rectangle source vers un rectangle de destination. `Draw` étire ou compresse le bitmap pour adopter les dimensions du rectangle de destination, si nécessaire et gère la fusion alpha et couleurs transparents.|
|[CImage::GetBits](#getbits)|Récupère un pointeur vers les valeurs de pixel de la bitmap.|
|[CImage::GetBPP](#getbpp)|Récupère les bits par pixel.|
|[CImage::GetColorTable](#getcolortable)|Récupère les valeurs de couleur (RVB) rouge, verts et bleus à partir d’une plage d’entrées dans la table des couleurs.|
|[CImage::GetDC](#getdc)|Récupère le contexte de périphérique dans lequel l’image bitmap active est sélectionnée.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Recherche les formats d’image disponibles et leurs descriptions.|
|[CImage::GetHeight](#getheight)|Récupère la hauteur de l’image en pixels.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Recherche les formats d’image disponibles et leurs descriptions.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Récupère le nombre maximal d’entrées dans la table des couleurs.|
|[CImage::GetPitch](#getpitch)|Récupère la hauteur de l’image actuelle, en octets.|
|[CImage::GetPixel](#getpixel)|Récupère la couleur du pixel spécifié par *x* et *y*.|
|[CImage::GetPixelAddress](#getpixeladdress)|Récupère l’adresse d’un pixel donné.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Récupère la position de la couleur transparente dans la table des couleurs.|
|[CImage::GetWidth](#getwidth)|Récupère la largeur de l’image en pixels.|
|[CImage::IsDIBSection](#isdibsection)|Détermine si la bitmap attachée est une section DIB.|
|[CImage::IsIndexed](#isindexed)|Indique que les couleurs d’une image bitmap sont mappées à une palette indexée.|
|[CImage::IsNull](#isnull)|Indique si une image bitmap source est actuellement chargée.|
|[CImage::IsTransparencySupported](#istransparencysupported)|Indique si l’application prend en charge les bitmaps transparentes.|
|[CImage::Load](#load)|Charge une image à partir du fichier spécifié.|
|[CImage::LoadFromResource](#loadfromresource)|Charge une image à partir de la ressource spécifiée.|
|[CImage::MaskBlt](#maskblt)|Combine les données de couleur pour les bitmaps de source et de destination à l’aide de l’opération de rastérisation et du masque spécifié.|
|[CImage::PlgBlt](#plgblt)|Effectue un transfert de bloc de bits d’un rectangle dans un contexte de périphérique source dans un parallélogramme dans un contexte de périphérique de destination.|
|[CImage::ReleaseDC](#releasedc)|Libère le contexte de périphérique qui a été récupéré avec [CImage::GetDC](#getdc).|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Libère les ressources utilisées par GDI +. Doit être appelée pour libérer des ressources créées par un global `CImage` objet.|
|[CImage::Save](#save)|Enregistre une image en tant que type spécifié. `Save` Impossible de spécifier les options d’image.|
|[CImage::SetColorTable](#setcolortable)|Définit RVB de rouge, vert et bleu) valeurs dans une plage d’entrées dans la table des couleurs de la section DIB de couleur.|
|[CImage::SetPixel](#setpixel)|Définit le pixel aux coordonnées spécifiées à la couleur spécifiée.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Définit le pixel aux coordonnées spécifiées sur la couleur à l’index spécifié de la palette.|
|[CImage::SetPixelRGB](#setpixelrgb)|Définit le pixel aux coordonnées spécifiées à spécifié rouge, vert, bleu (RVB) celle.|
|[CImage::SetTransparentColor](#settransparentcolor)|Définit l’index de la couleur à traiter comme transparente. Qu’une seule couleur dans une palette peut être transparente.|
|[CImage::StretchBlt](#stretchblt)|Copie une image bitmap à partir d’un rectangle source vers un rectangle de destination, étirant ou en compressant le bitmap pour adopter les dimensions du rectangle de destination, si nécessaire.|
|[CImage::TransparentBlt](#transparentblt)|Copie une image bitmap avec une couleur transparente à partir du contexte de périphérique source dans ce contexte de périphérique en cours.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CImage::operator HBITMAP](#operator_hbitmap)|Retourne le handle Windows associé à la `CImage` objet.|

## <a name="remarks"></a>Notes

`CImage` prend les bitmaps qui sont les deux sections de bitmap indépendante du périphérique (DIB) ou non ; Toutefois, vous pouvez utiliser [créer](#create) ou [CImage::Load](#load) avec uniquement les sections DIB. Vous pouvez attacher une image bitmap à la section non DIB à un `CImage` à l’aide de l’objet [Attach](#attach), mais vous ne pouvez pas utiliser ce qui suit `CImage` méthodes qui prennent en charge uniquement les bitmaps de section DIB :

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Pour déterminer si une bitmap attaché est une section DIB, appelez [IsDibSection](#isdibsection).

> [!NOTE]
> **Remarque** dans Visual Studio .NET 2003, cette classe conserve un décompte du nombre de `CImage` objets créés. Chaque fois que le décompte atteint 0, la fonction `GdiplusShutdown` est automatiquement appelée pour libérer les ressources utilisées par GDI +. Cela garantit que les `CImage` objets créés directement ou indirectement par les DLL sont détruits toujours correctement et que `GdiplusShutdown` n’est pas appelée à partir de `DllMain`.

> [!NOTE]
>  À l’aide de global `CImage` objets dans une DLL n’est pas recommandée. Si vous devez utiliser un global `CImage` objet dans une DLL, l’appel [CImage::ReleaseGDIPlus](#releasegdiplus) libérer explicitement les ressources utilisées par GDI +.

`CImage` ne peut pas être sélectionné dans un nouveau [CDC](../../mfc/reference/cdc-class.md). `CImage` crée son propre HDC pour l’image. Car un HBITMAP peut uniquement être sélectionné dans un seul HDC à la fois, HBITMAP associé à le `CImage` ne peuvent pas être sélectionnés dans un autre HDC. Si vous avez besoin d’une capture de données modifiées, récupérer le HDC à partir de la `CImage` et lui donner à [CDC::FromHandle] (.. /.. /MFC/Reference/CDC-Class.MD#cdc__fromhandle.

## <a name="example"></a>Exemple

```cpp  
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Lorsque vous utilisez `CImage` dans un projet MFC, notez les fonctions membres dans votre projet attendant un pointeur vers un [CBitmap](../../mfc/reference/cbitmap-class.md) objet. Si vous souhaitez utiliser `CImage` avec une telle fonction, comme [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), utilisez [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), passez-le votre `CImage` HBITMAP et utiliser retourné `CBitmap*`.  


## <a name="example"></a>Exemple

```cpp  
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
    UNREFERENCED_PARAMETER(nFlags);
    
    CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
    m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
    ClientToScreen(&point);
    m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x, 
    point.y, this);
}
```


Via `CImage`, vous avez accès aux bits réelles d’une section DIB. Vous pouvez utiliser un `CImage` de l’objet n’importe où vous avez déjà utilisé une section Win32 HBITMAP ou DIB.

Vous pouvez utiliser `CImage` à partir de MFC ou ATL.

> [!NOTE]
>  Lorsque vous créez un projet à l’aide `CImage`, vous devez définir `CString` avant d’inclure `atlimage.h`. Si votre projet utilise ATL sans MFC, incluez `atlstr.h` avant d’inclure `atlimage.h`. Si votre projet utilise les MFC (ou si elle est un projet ATL avec prise en charge MFC), incluez `afxstr.h` avant d’inclure `atlimage.h`.  
>   
>  De même, vous devez inclure `atlimage.h` avant d’inclure `atlimpl.cpp`. Pour ce faire facilement, inclure `atlimage.h` dans votre `stdafx.h`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlimage.h

##  <a name="alphablend"></a>  CImage::AlphaBlend

Affiche les bitmaps qui ont des pixels transparents ou semi-transparent.

```
BOOL AlphaBlend(
HDC hDestDC,
int xDest,
int yDest,
BYTE bSrcAlpha = 0xff,
BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
HDC hDestDC,
const POINT& pointDest,
BYTE bSrcAlpha = 0xff,
BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight,
int xSrc,
int ySrc,
int nSrcWidth,
int nSrcHeight,
BYTE bSrcAlpha = 0xff,
BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
HDC hDestDC,
const RECT& rectDest,
const RECT& rectSrc,
BYTE bSrcAlpha = 0xff,
BYTE bBlendOp = AC_SRC_OVER);
```

### <a name="parameters"></a>Paramètres

*hDestDC*  
Handle vers le contexte de périphérique de destination.

*xDest*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle de destination.

*bSrcAlpha*  
Une valeur de transparence alpha à utiliser sur l’image bitmap source entière. La valeur par défaut 0xff (255) suppose que votre image est opaque, et que vous souhaitez utiliser uniquement les valeurs alpha par pixel.

*bBlendOp*  
La fonction de simulation de transparence pour les sources et les bitmaps de destination, une valeur alpha globale à appliquer à l’image bitmap source entière, les informations de format pour l’image bitmap source. Les fonctions de blend source et destination sont actuellement limitées aux AC_SRC_OVER.

*pointDest*  
Une référence à un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure qui identifie le coin supérieur gauche du rectangle de destination, en unités logiques.

*nDestWidth*  
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*  
La hauteur, en unités logiques, du rectangle de destination.

*xSrc*  
La logique coordonnée x du coin supérieur gauche du rectangle source.

*ySrc*  
La logique coordonnée y du coin supérieur gauche du rectangle source.

*nSrcWidth*  
La largeur, en unités logiques, du rectangle source.

*nSrcHeight*  
La hauteur, en unités logiques, du rectangle source.

*rectDest*  
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure, identifiant la destination.

*rectSrc*  
Une référence à un `RECT` structure, identifier la source.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les bitmaps alpha-blend prend en charge la fusion de couleur sur une base par pixel.

Lorsque *bBlendOp* a la valeur par défaut de AC_SRC_OVER, le bitmap source est placé sur le bitmap de destination en fonction des valeurs alphabétiques des pixels source.  

##  <a name="attach"></a>  CImage::Attach

Attache *hBitmap* à un `CImage` objet.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Paramètres

*hBitmap*  
Handle vers un HBITMAP.

*eOrientation*  
Spécifie l’orientation de l’image bitmap. Il peut s'agir d'une des valeurs suivantes :

- DIBOR_DEFAULT l’orientation de l’image bitmap est déterminée par le système d’exploitation. Toutefois, cela n’avez pas toujours les résultats prévus sur tous les systèmes d’exploitation. Pour plus d’informations, consultez l’article suivant de la Base de connaissances (**Q186586**) : PRB : GetObject() toujours retourne positif hauteur pour DIB Sections.

- DIBOR_BOTTOMUP les lignes de la bitmap sont dans l’ordre inverse. Cela entraîne [CImage::GetBits](#getbits) pour retourner un pointeur vers la fin de la mémoire tampon de bitmap et [CImage::GetPitch](#getpitch) pour retourner un nombre négatif.

- DIBOR_TOPDOWN les lignes de la bitmap sont de haut en bas. Cela entraîne [CImage::GetBits](#getbits) pour retourner un pointeur vers le premier octet de la mémoire tampon de bitmap et [CImage::GetPitch](#getpitch) pour retourner un nombre positif.

### <a name="remarks"></a>Notes

L’image bitmap peut être une bitmap de section non DIB ou une bitmap de section DIB. Consultez [IsDIBSection](#isdibsection) pour obtenir la liste des méthodes que vous pouvez utiliser uniquement avec DIB section bitmaps.

##  <a name="bitblt"></a>  CImage::BitBlt

Copie une image bitmap à partir du contexte de périphérique source vers ce contexte de périphérique en cours.

```
BOOL BitBlt(
HDC hDestDC,
int xDest,
int yDest,
DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
HDC hDestDC,
const POINT& pointDest,
DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight,
int xSrc,
int ySrc,
DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
HDC hDestDC,
const RECT& rectDest,
const POINT& pointSrc,
DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Paramètres

*hDestDC*  
La destination HDC.

*xDest*  
La logique coordonnée x du coin supérieur gauche du rectangle de destination.

*yDest*  
La logique coordonnée y du coin supérieur gauche du rectangle de destination.

*dwROP*  
L’opération de rastérisation à effectuer. Codes d’opération de rastérisation définissent exactement comment combiner les bits de la source, la destination et le modèle (tel que défini par le pinceau actuellement sélectionné) pour former la destination. Consultez [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) dans le SDK Windows pour obtenir la liste des autres codes d’opération de rastérisation et leurs descriptions.

*pointDest*  
Un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure indiquant le coin supérieur gauche du rectangle de destination.

*nDestWidth*  
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*  
La hauteur, en unités logiques, du rectangle de destination.

*xSrc*  
La logique coordonnée x du coin supérieur gauche du rectangle source.

*ySrc*  
La logique coordonnée y du coin supérieur gauche du rectangle source.

*rectDest*  
Un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure indiquant le rectangle de destination.

*pointSrc*  
Un `POINT` structure indiquant le coin supérieur gauche du rectangle source.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) dans le SDK Windows.

##  <a name="cimage"></a>  CImage::CImage

Construit un objet `CImage`.

```
CImage() throw();
```

### <a name="remarks"></a>Notes

Une fois que vous avez construit l’objet, appelez [créer](#create), [charge](#load), [LoadFromResource](#loadfromresource), ou [attacher](#attach) pour attacher une image bitmap à l’objet.

**Remarque** dans Visual Studio, cette classe conserve un décompte du nombre de `CImage` objets créés. Chaque fois que le décompte atteint 0, la fonction `GdiplusShutdown` est automatiquement appelée pour libérer les ressources utilisées par GDI +. Cela garantit que les `CImage` objets créés directement ou indirectement par les DLL sont détruits toujours correctement et que `GdiplusShutdown` n’est pas appelée à partir de DllMain.

À l’aide de global `CImage` objets dans une DLL n’est pas recommandée. Si vous devez utiliser un global `CImage` objet dans une DLL, l’appel [CImage::ReleaseGDIPlus](#releasegdiplus) libérer explicitement les ressources utilisées par GDI +.

##  <a name="create"></a>  CImage::Create

Crée un `CImage` bitmap et l’attacher à précédemment construit `CImage` objet.

```
BOOL Create(
int nWidth,
int nHeight,
int nBPP,
DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*nWidth*  
La largeur de la `CImage` bitmap, en pixels.

*nHeight*  
La hauteur de la `CImage` bitmap, en pixels. Si *nHeight* est un nombre positif, la bitmap est un DIB de bas en haut et son origine est l’angle inférieur gauche. Si *nHeight* est négatif, la bitmap est un DIB de haut en bas et son origine est l’angle supérieur gauche.

*nBPP*  
Le nombre de bits par pixel de la bitmap. Généralement 4, 8, 16, 24 ou 32. Peut être 1 pour les images bitmap monochromes ou masques.

*dwFlags*  
Spécifie si l’objet bitmap a un canal alpha. Peut être une combinaison de zéro ou plusieurs des valeurs suivantes :

- *createAlphaChannel* peut uniquement être utilisée si *nBPP* est 32, et *eCompression* est BI_RGB. Si spécifié, l’image créée a une valeur alpha (transparence) pour chaque pixel, stockée dans la 4e octet de chaque pixel (non utilisé dans une image de 32 bits non alphanumériques). Ce canal alpha est automatiquement utilisé lors de l’appel [CImage::AlphaBlend](#alphablend).

> [!NOTE]
>  Dans les appels à [CImage::Draw](#draw), avec un canal alpha, les images sont automatiquement alpha mélangée à la destination.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="createex"></a>  CImage::CreateEx

Crée un `CImage` bitmap et l’attacher à précédemment construit `CImage` objet.

```
BOOL CreateEx(
int nWidth,
int nHeight,
int nBPP,
DWORD eCompression,
const DWORD* pdwBitmasks = NULL,
DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*nWidth*  
La largeur de la `CImage` bitmap, en pixels.

*nHeight*  
La hauteur de la `CImage` bitmap, en pixels. Si *nHeight* est un nombre positif, la bitmap est un DIB de bas en haut et son origine est l’angle inférieur gauche. Si *nHeight* est négatif, la bitmap est un DIB de haut en bas et son origine est l’angle supérieur gauche.

*nBPP*  
Le nombre de bits par pixel de la bitmap. Généralement 4, 8, 16, 24 ou 32. Peut être 1 pour les images bitmap monochromes ou masques.

*eCompression*  
Spécifie le type de compression d’une bitmap compressée de bas en haut (ne peut pas être compressé DIB de haut en bas). Peut avoir l'une des valeurs suivantes :

- BI_RGB le format ne sont pas compressées. En spécifiant cette valeur lors de l’appel `CImage::CreateEx` équivaut à appeler `CImage::Create`.

- BI_BITFIELDS le format n’est pas compressé et la table des couleurs se compose de trois masques de couleur DWORD qui spécifient les composants rouges, vert et bleus, respectivement, de chaque pixel. Cela n’est valide que lorsqu’il est utilisé avec des bitmaps de 16 et 32 bpp.

*pdwBitfields*  
Utilisé uniquement si *eCompression* est définie à BI_BITFIELDS, sinon il doit être NULL. Un pointeur vers un tableau de trois masques de bits DWORD, en spécifiant les bits de chaque pixel sont utilisés pour les composants rouges, vert et bleus de la couleur, respectivement. Pour plus d’informations sur les restrictions pour les champs de bits, consultez [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) dans le SDK Windows.

*dwFlags*  
Spécifie si l’objet bitmap a un canal alpha. Peut être une combinaison de zéro ou plusieurs des valeurs suivantes :

- *createAlphaChannel* peut uniquement être utilisée si *nBPP* est 32, et *eCompression* est BI_RGB. Si spécifié, l’image créée a une valeur alpha (transparence) pour chaque pixel, stockée dans la 4e octet de chaque pixel (non utilisé dans une image de 32 bits non alphanumériques). Ce canal alpha est automatiquement utilisé lors de l’appel [CImage::AlphaBlend](#alphablend).

   > [!NOTE]
   > Dans les appels à [CImage::Draw](#draw), avec un canal alpha, les images sont automatiquement alpha mélangée à la destination.

### <a name="return-value"></a>Valeur de retour

TRUE si l’opération réussit. Sinon, FALSE.

### <a name="example"></a>Exemple

L’exemple suivant crée une image bitmap de 100 x 100 pixels, à l’aide de 16 bits pour encoder chaque pixel. Dans un pixel donné de 16 bits, le composant rouge encoder des bits 0-3, bits 4-7 Encoder vert et le codage du bleu bits 8-11. Les 4 bits restants ne sont pas utilisés.  

```cpp  
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>  CImage::Destroy

Détache la bitmap à partir de la `CImage` de l’objet et détruit la bitmap.

```
void Destroy() throw();
```

##  <a name="detach"></a>  CImage::Detach

Détache une image bitmap à partir d’un `CImage` objet.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Un handle de bitmap détachée, ou NULL si aucune bitmap n’est attaché.

##  <a name="draw"></a>  CImage::Draw

Copie une image bitmap à partir du contexte de périphérique source vers le contexte de périphérique en cours.

```
BOOL Draw(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight,
int xSrc,
int ySrc,
int nSrcWidth,
int nSrcHeight) const throw();

BOOL Draw(
HDC hDestDC,
const RECT& rectDest,
const RECT& rectSrc) const throw();

BOOL Draw(
HDC hDestDC,
int xDest,
int yDest) const throw();

BOOL Draw(
HDC hDestDC,
const POINT& pointDest) const throw();

BOOL Draw(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight) const throw();

BOOL Draw(
HDC hDestDC,
const RECT& rectDest) const throw();
```

### <a name="parameters"></a>Paramètres

*hDestDC*  
Handle vers le contexte de périphérique de destination.

*xDest*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle de destination.

*nDestWidth*  
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*  
La hauteur, en unités logiques, du rectangle de destination.

*xSrc*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle source.

*ySrc*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle source.

*nSrcWidth*  
La largeur, en unités logiques, du rectangle source.

*nSrcHeight*  
La hauteur, en unités logiques, du rectangle source.

*rectDest*  
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure, identifiant la destination.

*rectSrc*  
Une référence à un `RECT` structure, identifier la source.

*pointDest*  
Une référence à un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure qui identifie le coin supérieur gauche du rectangle de destination, en unités logiques.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`Draw` effectue la même opération que [StretchBlt](#stretchblt), sauf si l’image contient une couleur transparente ou le canal alpha. Dans ce cas, `Draw` effectue la même opération, soit comme [TransparentBlt](#transparentblt) ou [AlphaBlend](#alphablend) en fonction des besoins.

Pour les versions de `Draw` qui ne spécifient pas un rectangle source, l’image source entière est la valeur par défaut. Pour la version de `Draw` qui ne spécifie pas une taille pour le rectangle de destination, la taille de l’image source est la valeur par défaut, aucun étirement ou la réduction se produit.

##  <a name="getbits"></a>  CImage::GetBits

Récupère un pointeur vers les valeurs de bit réelle d’un pixel donné dans une image bitmap.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la mémoire tampon de bitmap. Si la bitmap est un DIB de bas en haut, le pointeur pointe vers la fin de la mémoire tampon. Si la bitmap est un DIB de haut en bas, le pointeur pointe vers le premier octet de la mémoire tampon.

### <a name="remarks"></a>Notes

À l’aide de ce pointeur, ainsi que la valeur retournée par [GetPitch](#getpitch), vous pouvez rechercher et modifier des pixels individuels dans une image.

> [!NOTE]
>  Cette méthode prend en charge uniquement les bitmaps de section DIB ; Par conséquent, vous accédez à pixels d’un `CImage` l’objet de la même façon que les pixels d’une section DIB. Le pointeur retourné pointe vers le pixel à l’emplacement (0, 0).

##  <a name="getbpp"></a>  CImage::GetBPP

Récupère la valeur de bits par pixel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de bits par pixel.

### <a name="remarks"></a>Notes

Cette valeur détermine le nombre de bits qui définissent chaque pixel et le nombre maximal de couleurs de la bitmap.

Les bits par pixel est généralement 1, 4, 8, 16, 24 ou 32. Consultez le `biBitCount` membre [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) dans le SDK Windows pour plus d’informations sur cette valeur.

##  <a name="getcolortable"></a>  CImage::GetColorTable

Récupère les valeurs de couleur (RVB) rouge, verts et bleus à partir d’une plage d’entrées dans la palette de la section DIB.

```
void GetColorTable(UINT iFirstColor,
UINT nColors,
RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Paramètres

*iFirstColor*  
L’index de table de couleur de la première entrée à récupérer.

*nColors*  
Le nombre d’entrées de table de couleur à récupérer.

*prgbColors*  
Un pointeur vers le tableau de [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) structures pour récupérer la couleur des entrées de table.

##  <a name="getdc"></a>  CImage::GetDC

Récupère le contexte de périphérique qui a actuellement l’image sélectionnée dedans.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Valeur de retour

Handle d'un contexte de périphérique.

### <a name="remarks"></a>Notes

Pour chaque appel à `GetDC`, vous devez disposer d’un appel ultérieur à [ReleaseDC](#releasedc).

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

Recherche des formats d’image disponibles pour l’enregistrement des images.

```
static HRESULT GetExporterFilterString(CSimpleString& strExporters,
CSimpleArray<GUID>& aguidFileTypes,
LPCTSTR pszAllFilesDescription = NULL,
DWORD dwExclude = excludeDefaultSave,
TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Paramètres

*strExporters*  
Référence à un objet `CSimpleString`. Consultez **remarques** pour plus d’informations.

*aguidFileTypes*  
Un tableau de GUID, avec chaque élément qui correspond à un des types de fichiers dans la chaîne. Dans l’exemple de *pszAllFilesDescription* ci-dessous, *aguidFileTypes*[0] est GUID_NULL et les valeurs de tableau restants sont les formats de fichier image pris en charge par le système d’exploitation actuel.

> [!NOTE]
>  Pour obtenir une liste complète des constantes, consultez **constantes de Format de fichier Image** dans le SDK Windows.

*pszAllFilesDescription*  
Si ce paramètre n’est pas NULL, la chaîne de filtrage aura un filtre supplémentaire au début de la liste. Ce filtre a la valeur actuelle de *pszAllFilesDescription* pour sa description et accepte les fichiers de n’importe quelle extension pris en charge par n’importe quel autre exportateur dans la liste.

Exemple :  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes, 
_T("All Image Files"));
```


*dwExclude*  
Ensemble d’indicateurs de bits spécifiant les types de fichiers à exclure de la liste. Indicateurs autorisés sont :

- `excludeGIF` = fichiers GIF exclut de 0 x 01.

- `excludeBMP` = 0 x 02 de fichiers d’exclut BMP (Bitmap Windows).

- `excludeEMF` = 0 x 04 les fichiers exclut EMF (Enhanced Metafile).

- `excludeWMF` = 0 x 08 les fichiers exclut WMF (Windows Metafile).

- `excludeJPEG` = fichiers JPEG exclut de 0 x 10.

- `excludePNG` = fichiers PNG exclut de 0 x 20.

- `excludeTIFF` = 0 x 40 exclut le format TIFF.

- `excludeIcon` = 0 x 80 les fichiers ICO exclut (icône de Windows).

- `excludeOther` = 0 x 80000000 exclut tout autre type de fichier non répertoriée ci-dessus.

- `excludeDefaultLoad` = 0 pour la charge, tous les types de fichiers sont inclus par défaut

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Pour l’enregistrement, ces fichiers sont exclus par défaut, car elles ont généralement des exigences particulières.

*chSeparator*  
Le séparateur utilisé entre les formats d’image. Consultez **remarques** pour plus d’informations.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez passer la chaîne de format résultant à votre MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) met en forme objet d’exposer les extensions de fichier de l’image disponible dans la boîte de dialogue Enregistrer sous.

Le paramètre *strExporter* a le format :

fichier description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;.. .file description *n*&#124;\*.ext *n*&#124;&#124;

où «&#124;» est le caractère de séparation spécifié par `chSeparator`. Exemple :

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Utiliser le séparateur par défaut '&#124;' Si vous passez cette chaîne à une MFC `CFileDialog` objet. Utilisez le séparateur null « \0 » si vous passez cette chaîne à une boîte de dialogue d’enregistrement du fichier.

##  <a name="getheight"></a>  CImage::GetHeight

Récupère la hauteur, en pixels, d’une image.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Valeur de retour

La hauteur, en pixels, d’une image.

##  <a name="getimporterfilterstring"></a>  CImage::GetImporterFilterString

Recherche des formats d’image disponible pour le chargement des images.

```
static HRESULT GetImporterFilterString(CSimpleString& strImporters,
CSimpleArray<GUID>& aguidFileTypes,
LPCTSTR pszAllFilesDescription = NULL,
DWORD dwExclude = excludeDefaultLoad,
TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Paramètres

*strImporters*  
Référence à un objet `CSimpleString`. Consultez **remarques** pour plus d’informations.

*aguidFileTypes*  
Un tableau de GUID, avec chaque élément qui correspond à un des types de fichiers dans la chaîne. Dans l’exemple de *pszAllFilesDescription* ci-dessous, *aguidFileTypes*[0] est GUID_NULL avec les valeurs de tableau restants sont les formats de fichier image pris en charge par le système d’exploitation actuel.

> [!NOTE]
>  Pour obtenir une liste complète des constantes, consultez **constantes de Format de fichier Image** dans le SDK Windows.

*pszAllFilesDescription*  
Si ce paramètre n’est pas NULL, la chaîne de filtrage aura un filtre supplémentaire au début de la liste. Ce filtre a la valeur actuelle de *pszAllFilesDescription* pour sa description et accepte les fichiers de n’importe quelle extension pris en charge par n’importe quel autre exportateur dans la liste.

Exemple :  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes, 
_T("All Image Files"));
```


*dwExclude*  
Ensemble d’indicateurs de bits spécifiant les types de fichiers à exclure de la liste. Indicateurs autorisés sont :

- `excludeGIF` = fichiers GIF exclut de 0 x 01.

- `excludeBMP` = 0 x 02 de fichiers d’exclut BMP (Bitmap Windows).

- `excludeEMF` = 0 x 04 les fichiers exclut EMF (Enhanced Metafile).

- `excludeWMF` = 0 x 08 les fichiers exclut WMF (Windows Metafile).

- `excludeJPEG` = fichiers JPEG exclut de 0 x 10.

- `excludePNG` = fichiers PNG exclut de 0 x 20.

- `excludeTIFF` = 0 x 40 exclut le format TIFF.

- `excludeIcon` = 0 x 80 les fichiers ICO exclut (icône de Windows).

- `excludeOther` = 0 x 80000000 exclut tout autre type de fichier non répertoriée ci-dessus.

- `excludeDefaultLoad` = 0 pour la charge, tous les types de fichiers sont inclus par défaut

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Pour l’enregistrement, ces fichiers sont exclus par défaut, car elles ont généralement des exigences particulières.

*chSeparator*  
Le séparateur utilisé entre les formats d’image. Consultez **remarques** pour plus d’informations.

### <a name="remarks"></a>Notes

Vous pouvez passer la chaîne de format résultant à votre MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) formats de l’objet d’exposer les extensions de fichier de l’image disponible dans le **ouvrir le fichier** boîte de dialogue.

Le paramètre *strImporter* a le format :

fichier description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;.. .file description *n*&#124;\*.ext *n*&#124;&#124;

où «&#124;» est spécifié par le caractère de séparation *chSeparator*. Exemple :

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Utiliser le séparateur par défaut '&#124;' Si vous passez cette chaîne à une MFC `CFileDialog` objet. Utiliser le séparateur null « \0 » si vous passez cette chaîne vers un courant **ouvrir le fichier** boîte de dialogue.

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

Récupère le nombre maximal d’entrées dans la table des couleurs.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’entrées dans la table des couleurs.

### <a name="remarks"></a>Notes

Cette méthode prend en charge uniquement les bitmaps de section DIB.

##  <a name="getpitch"></a>  CImage::GetPitch

Récupère la hauteur d’une image.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Valeur de retour

La hauteur de l’image. Si la valeur de retour est négative, la bitmap est un DIB de bas en haut et son origine est l’angle inférieur gauche. Si la valeur de retour est un nombre positive, la bitmap est un DIB de haut en bas et de son origine est l’angle supérieur gauche.

### <a name="remarks"></a>Notes

Le tangage est la distance, en octets, entre deux adresses mémoire qui représentent le début d’une ligne de bitmap et le début de la ligne suivante de la bitmap. Étant donné que la tonalité est mesurée en octets, la hauteur d’une image vous aide à déterminer le format de pixel. La tonalité peut également inclure la mémoire supplémentaire, réservée à la bitmap.

Utilisez `GetPitch` avec [GetBits](#getbits) pour rechercher des pixels individuels d’une image.

> [!NOTE]
>  Cette méthode prend en charge uniquement les bitmaps de section DIB.

##  <a name="getpixel"></a>  CImage::GetPixel

Récupère la couleur du pixel à l’emplacement spécifié par *x* et *y*.

```
COLORREF GetPixel(int x,int y) const throw();
```

### <a name="parameters"></a>Paramètres

*x*  
Coordonnée x du pixel.

*y*  
Coordonnée y du pixel.

### <a name="return-value"></a>Valeur de retour

Rouge, vert et bleu (RVB) celle du pixel. Si le pixel est en dehors de la zone de découpage en cours, la valeur de retour est CLR_INVALID.

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

Récupère l’adresse exacte d’un pixel.

```
void* GetPixelAddress(int x,int y) throw();
```

### <a name="parameters"></a>Paramètres

*x*  
Coordonnée x du pixel.

*y*  
Coordonnée y du pixel.

### <a name="remarks"></a>Notes

L’adresse est déterminée selon les coordonnées d’un pixel, la hauteur de la bitmap et les bits par pixel.

Pour les formats qui ont moins de 8 bits par pixel, cette méthode retourne l’adresse de l’octet qui contient le pixel. Par exemple, si votre format d’image a 4 bits par pixel, `GetPixelAddress` retourne l’adresse du premier pixel dans l’octet et que vous devez calculer pour 2 pixels par octet.

> [!NOTE]
>  Cette méthode prend en charge uniquement les bitmaps de section DIB.

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

Récupère la position d’index de la couleur transparente dans la palette de couleurs.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Valeur de retour

Index de la couleur transparente.

##  <a name="getwidth"></a>  CImage::GetWidth

Récupère la largeur, en pixels, d’une image.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Valeur de retour

Largeur de l’image bitmap, en pixels.

##  <a name="isdibsection"></a>  CImage::IsDIBSection

Détermine si la bitmap attachée est une section DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Valeur de retour

TRUE si la bitmap attachée est une section DIB. Sinon, FALSE.

### <a name="remarks"></a>Notes

Si l’image bitmap n’est pas une section DIB, vous ne pouvez pas utiliser ce qui suit `CImage` méthodes qui prennent en charge uniquement les bitmaps de section DIB :

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>  CImage::IsIndexed

Détermine si les pixels d’une image bitmap sont mappées à une palette de couleurs.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Valeur de retour

TRUE si indexée ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur TRUE uniquement si la bitmap est 8 bits (256 couleurs) ou moins.

> [!NOTE]
>  Cette méthode prend en charge uniquement les bitmaps de section DIB.

##  <a name="isnull"></a>  CImage::IsNull

Détermine si une image bitmap est actuellement chargée.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur TRUE si une image bitmap n’est pas actuellement chargée ; Sinon, FALSE.

##  <a name="istransparencysupported"></a>  CImage::IsTransparencySupported

Indique si l’application prend en charge les bitmaps transparentes.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la plateforme actuelle prend en charge la transparence. Sinon 0.

### <a name="remarks"></a>Notes

Si la valeur de retour est différent de zéro, et la transparence est pris en charge, un appel à [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt), ou [dessiner](#draw) gérera couleurs transparents.

##  <a name="load"></a>  CImage::Load

Charge une image.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pszFileName*  
Un pointeur vers une chaîne contenant le nom du fichier image à charger.

*pStream*  
Pointeur vers un flux contenant le nom du fichier image à charger.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Charge l’image spécifiée par *pszFileName* ou *pStream*.

Types d’images valides sont BMP, GIF, JPEG, PNG et TIFF.

##  <a name="loadfromresource"></a>  CImage::LoadFromResource

Charge une image à partir d’une ressource BITMAP.

```
void LoadFromResource(
HINSTANCE hInstance,
LPCTSTR pszResourceName) throw();

void LoadFromResource(
HINSTANCE hInstance,
UINT nIDResource) throw();
```

### <a name="parameters"></a>Paramètres

*hInstance*  
Handle vers une instance du module qui contient l’image à charger.

*pszResourceName*  
Pointeur vers la chaîne contenant le nom de la ressource qui contient l’image à charger.

*nIDResource*  
ID de la ressource à charger.

### <a name="remarks"></a>Notes

La ressource doit être de type image BITMAP.

##  <a name="maskblt"></a>  CImage::MaskBlt

Combine les données de couleur pour les bitmaps de source et de destination à l’aide de l’opération de rastérisation et du masque spécifié.

```
BOOL MaskBlt(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight,
int xSrc,
int ySrc,
HBITMAP hbmMask,
int xMask,
int yMask,
DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
HDC hDestDC,
const RECT& rectDest,
const POINT& pointSrc,
HBITMAP hbmMask,
const POINT& pointMask,
DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
HDC hDestDC,
int xDest,
int yDest,
HBITMAP hbmMask,
DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
HDC hDestDC,
const POINT& pointDest,
HBITMAP hbmMask,
DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Paramètres

*hDestDC*  
Le handle du module dont exécutable contient la ressource.

*xDest*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle de destination.

*nDestWidth*  
La largeur, en unités logiques, de la bitmap source et le rectangle de destination.

*nDestHeight*  
La hauteur, en unités logiques, de la bitmap source et le rectangle de destination.

*xSrc*  
La logique coordonnée x du coin supérieur gauche de la bitmap source.

*ySrc*  
La logique coordonnée y du coin supérieur gauche de la bitmap source.

*hbmMask*  
Handle de la bitmap de masque monochrome combinée avec le bitmap de couleur dans le contexte du périphérique source.

*xMask*  
Le décalage horizontal de pixels pour la bitmap de masque spécifié par le *hbmMask* paramètre.

*yMask*  
Le décalage vertical pixel pour l’image bitmap de masque spécifié par le *hbmMask* paramètre.

*dwROP*  
Spécifie le premier plan et arrière-plan ternaire opération de rastérisation par la méthode pour contrôler la combinaison de données source et de destination. Le code d’opération d’arrière-plan raster est stocké dans l’octet de poids fort du mot de poids fort de cette valeur ; le code d’opération de premier plan raster est stocké dans l’octet de poids faible du mot de poids fort de cette valeur ; le mot de poids faible de cette valeur est ignoré et doit être égal à zéro. Pour une présentation de premier plan et d’arrière-plan dans le contexte de cette méthode, consultez `MaskBlt` dans le SDK Windows. Pour obtenir la liste des codes d’opération raster courants, consultez `BitBlt` dans le SDK Windows.

*rectDest*  
Une référence à un `RECT` structure, identifiant la destination.

*pointSrc*  
Un `POINT` structure indiquant le coin supérieur gauche du rectangle source.

*pointMask*  
Un `POINT` structure indiquant le coin supérieur gauche de la bitmap de masque.

*pointDest*  
Une référence à un `POINT` structure qui identifie le coin supérieur gauche du rectangle de destination, en unités logiques.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Cette méthode s’applique à Windows NT, versions 4.0 et versions ultérieures uniquement.

##  <a name="operator_hbitmap"></a>  CImage::operator HBITMAP

Utilisez cet opérateur pour obtenir le handle Windows GDI attaché de la `CImage` objet. Cet opérateur est un opérateur de cast, qui prend en charge l’utilisation directe d’un objet HBITMAP.

##  <a name="plgblt"></a>  CImage::PlgBlt

Effectue un transfert de bloc de bits d’un rectangle dans un contexte de périphérique source dans un parallélogramme dans un contexte de périphérique de destination.

```
BOOL PlgBlt(
HDC hDestDC,
const POINT* pPoints,
HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
HDC hDestDC,
const POINT* pPoints,
int xSrc,
int ySrc,
int nSrcWidth,
int nSrcHeight,
HBITMAP hbmMask = NULL,
int xMask = 0,
int yMask = 0) const throw();

BOOL PlgBlt(
HDC hDestDC,
const POINT* pPoints,
const RECT& rectSrc,
HBITMAP hbmMask = NULL,
const POINT& pointMask = CPoint(0, 0)) const throw();
```

### <a name="parameters"></a>Paramètres

*hDestDC*  
Handle vers le contexte de périphérique de destination.

*pPoints*  
Pointeur vers un tableau de trois points dans l’espace logique qui identifient les trois angles du parallélogramme de destination. Le coin supérieur gauche du rectangle source est mappé au premier point dans le coin inférieur gauche pour le troisième point ce tableau et le coin supérieur droit et le deuxième point de ce tableau. Le coin inférieur droit du rectangle source est mappé au quatrième point dans un parallélogramme implicit.

*hbmMask*  
Un handle vers une bitmap monochrome facultatif servant à masquer les couleurs du rectangle source.

*xSrc*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle source.

*ySrc*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle source.

*nSrcWidth*  
La largeur, en unités logiques, du rectangle source.

*nSrcHeight*  
La hauteur, en unités logiques, du rectangle source.

*xMask*  
Coordonnée x du coin supérieur gauche de l’image bitmap monochrome.

*yMask*  
Coordonnée y du coin supérieur gauche de l’image bitmap monochrome.

*rectSrc*  
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure spécifiant les coordonnées du rectangle source.

*pointMask*  
Un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure indiquant le coin supérieur gauche de la bitmap de masque.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Si *hbmMask* identifie un bitmap monochrome valide, `PlgBit` utilise cette image bitmap pour masquer les bits des données de couleur du rectangle source.

Cette méthode s’applique à Windows NT, versions 4.0 et versions ultérieures uniquement. Consultez [PlgBlt](/windows/desktop/api/wingdi/nf-wingdi-plgblt) dans le SDK Windows pour des informations plus détaillées.

##  <a name="releasedc"></a>  CImage::ReleaseDC

Libère le contexte de périphérique.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Notes

Étant donné que seul bitmap peut être sélectionnée dans un contexte de périphérique à la fois, vous devez appeler `ReleaseDC` pour chaque appel à [GetDC](#getdc).

##  <a name="releasegdiplus"></a>  CImage::ReleaseGDIPlus

Libère les ressources utilisées par GDI +.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Notes

Cette méthode doit être appelée pour libérer des ressources allouées par global `CImage` objet. Consultez [CImage::CImage](#cimage).

##  <a name="save"></a>  CImage::Save

Enregistre une image dans le fichier sur disque ou le flux spécifié.

```
HRESULT Save(IStream* pStream,
REFGUID guidFileType) const throw();

HRESULT Save(LPCTSTR pszFileName,
REFGUID guidFileType= GUID_NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*pStream*  
Pointeur vers un objet COM IStream contenant les données d’image de fichier.

*pszFileName*  
Pointeur vers le nom de fichier pour l’image.

*guidFileType*  
Le type de fichier pour enregistrer l’image en tant que. Il peut s'agir d'une des valeurs suivantes :

- `ImageFormatBMP` Une image bitmap non compressé.

- `ImageFormatPNG` Une image compressée du graphique PNG (Portable Network).

- `ImageFormatJPEG` Image JPEG compressée.

- `ImageFormatGIF` Image GIF compressée.

> [!NOTE]
>  Pour obtenir une liste complète des constantes, consultez **constantes de Format de fichier Image** dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Appelez cette fonction pour enregistrer l’image à l’aide d’un nom et type spécifiés. Si le *guidFileType* paramètre n’est pas inclus, l’extension de fichier du nom de fichier sera utilisée pour déterminer le format d’image. Si aucune extension n’est fournie, l’image sera enregistrée au format BMP.

##  <a name="setcolortable"></a>  CImage::SetColorTable

Définit les valeurs de rouge, verts et bleus (RVB) couleur pour une plage d’entrées dans la palette de la section DIB.

```
void SetColorTable(
    UINT iFirstColor, 
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Paramètres

*iFirstColor*  
L’index de table de couleur de la première entrée à définir.

*nColors*  
Le nombre d’entrées de table de couleur à définir.

*prgbColors*  
Un pointeur vers le tableau de [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) structures pour définir la couleur des entrées de table.

### <a name="remarks"></a>Notes

Cette méthode prend en charge uniquement les bitmaps de section DIB.

##  <a name="setpixel"></a>  CImage::SetPixel

Définit la couleur d’un pixel à un emplacement donné dans l’image bitmap.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Paramètres

*x*  
Emplacement horizontal du pixel à définir.

*y*  
Emplacement vertical du pixel à définir.

*Couleur*  
Le modèle de couleurs à laquelle vous le pixel.

### <a name="remarks"></a>Notes

Cette méthode échoue si le pixel des coordonnées se trouvent en dehors de la zone de découpage sélectionné.

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

Définit la couleur du pixel à la couleur à *iIndex* dans la palette de couleurs.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Paramètres

*x*  
Emplacement horizontal du pixel à définir.

*y*  
Emplacement vertical du pixel à définir.

*iIndex*  
L’index d’une couleur dans la palette de couleurs.

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

Définit le pixel aux emplacements spécifiés par *x* et *y* les couleurs indiqué par *r*, *g*, et *b*, de rouge, vert, bleu image (RVB).

```
void SetPixelRGB(  
int x,
int y,
BYTE r,
BYTE g,
BYTE b) throw();
```

### <a name="parameters"></a>Paramètres

*x*  
Emplacement horizontal du pixel à définir.

*y*  
Emplacement vertical du pixel à définir.

*r*  
L’intensité de la couleur rouge.

*g*  
L’intensité de la couleur verte.

*b*  
L’intensité de la couleur bleue.

### <a name="remarks"></a>Notes

Les paramètres de rouges, vert et bleus sont représentées par un nombre compris entre 0 et 255. Si vous définissez les trois paramètres à zéro, la couleur résultante combinée est noire. Si vous définissez les trois paramètres à 255, la couleur résultante combinée est le blanc.

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

Définit une couleur à un emplacement donné indexé comme étant transparents.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Paramètres

*iTransparentColor*  
L’index dans une palette de couleurs, de la couleur pour définir transparentes. Si-1, aucune couleur n’a transparent.

### <a name="return-value"></a>Valeur de retour

L’index de la couleur précédemment défini comme étant transparent.

##  <a name="stretchblt"></a>  CImage::StretchBlt

Copie une image bitmap à partir du contexte de périphérique source vers ce contexte de périphérique en cours.

```
BOOL StretchBlt(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight,
DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
HDC hDestDC,
const RECT& rectDest,
DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight,
int xSrc,
int ySrc,
int nSrcWidth,
int nSrcHeight,
DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
HDC hDestDC,
const RECT& rectDest,
const RECT& rectSrc,
DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Paramètres

*hDestDC*  
Handle vers le contexte de périphérique de destination.

*xDest*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle de destination.

*nDestWidth*  
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*  
La hauteur, en unités logiques, du rectangle de destination.

*dwROP*  
L’opération de rastérisation à effectuer. Codes d’opération de rastérisation définissent exactement comment combiner les bits de la source, la destination et le modèle (tel que défini par le pinceau actuellement sélectionné) pour former la destination. Consultez [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) dans le SDK Windows pour obtenir la liste des autres codes d’opération de rastérisation et leurs descriptions.

*rectDest*  
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure, identifiant la destination.

*xSrc*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle source.

*ySrc*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle source.

*nSrcWidth*  
La largeur, en unités logiques, du rectangle source.

*nSrcHeight*  
La hauteur, en unités logiques, du rectangle source.

*rectSrc*  
Une référence à un `RECT` structure, identifier la source.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [StretchBlt](/windows/desktop/api/wingdi/nf-wingdi-stretchblt) dans le SDK Windows.

##  <a name="transparentblt"></a>  CImage::TransparentBlt

Copie une image bitmap à partir du contexte de périphérique source vers ce contexte de périphérique en cours.

```
BOOL TransparentBlt(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight,
UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
HDC hDestDC,
const RECT& rectDest,
UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
HDC hDestDC,
int xDest,
int yDest,
int nDestWidth,
int nDestHeight,
int xSrc,
int ySrc,
int nSrcWidth,
int nSrcHeight,
UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
HDC hDestDC,
const RECT& rectDest,
const RECT& rectSrc,
UINT crTransparent = CLR_INVALID) const throw();
```

### <a name="parameters"></a>Paramètres

*hDestDC*  
Handle vers le contexte de périphérique de destination.

*xDest*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle de destination.

*nDestWidth*  
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*  
La hauteur, en unités logiques, du rectangle de destination.

*crTransparent*  
La couleur de la bitmap source à traiter comme transparente. Par défaut, CLR_INVALID, indiquant que la couleur actuellement définie comme couleur transparente de l’image doit être utilisée.

*rectDest*  
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure, identifiant la destination.

*xSrc*  
La coordonnée x, en unités logiques, du coin supérieur gauche du rectangle source.

*ySrc*  
La coordonnée y, en unités logiques, du coin supérieur gauche du rectangle source.

*nSrcWidth*  
La largeur, en unités logiques, du rectangle source.

*nSrcHeight*  
La hauteur, en unités logiques, du rectangle source.

*rectSrc*  
Une référence à un `RECT` structure, identifier la source.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon, FALSE.

### <a name="remarks"></a>Notes

`TransparentBlt` est pris en charge pour les bitmaps de source de 4 bits par pixel et de 8 bits par pixel. Utilisez [CImage::AlphaBlend](#alphablend) pour spécifier les bitmaps de 32 bits par pixel avec la transparence.


### <a name="example"></a>Exemple  

```cpp  
// Performs a transparent blit from the source image to the destination 
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage, 
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
    HDC hDstDC = NULL;
    BOOL bResult;

    if(pSrcImage == NULL || pDstImage == NULL)
    {
        // Invalid parameter
        return FALSE;
    }

    // Obtain a DC to the destination image
    hDstDC = pDstImage->GetDC();
    // Perform the blit
    bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

    // Release the destination DC
    pDstImage->ReleaseDC();

    return bResult;
}
```


## <a name="see-also"></a>Voir aussi

[MMXSwarm, exemple](../../visual-cpp-samples.md)   
[Exemple SimpleImage](../../visual-cpp-samples.md)   
[Bitmaps indépendantes du périphérique](/windows/desktop/gdi/device-independent-bitmaps)   
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)   
[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
[les Bitmaps indépendantes du périphérique](/windows/desktop/gdi/device-independent-bitmaps)   
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)   

