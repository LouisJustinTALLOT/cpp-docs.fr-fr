---
description: 'En savoir plus sur : CImage (classe)'
title: CImage (classe)
ms.date: 08/19/2019
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
ms.openlocfilehash: a094aecfae57a678f306d00e0998247000361822
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166823"
---
# <a name="cimage-class"></a>CImage (classe)

`CImage` offre une prise en charge améliorée des bitmaps, notamment la possibilité de charger et d’enregistrer des images au format JPEG, GIF, BMP et PNG (Portable Network Graphics).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CImage
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CImage :: CImage](#cimage)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CImage :: AlphaBlend](#alphablend)|Affiche les bitmaps qui ont des pixels transparents ou translucides.|
|[CImage :: Attach](#attach)|Attache un HBITMAP à un `CImage` objet. Peut être utilisé avec des bitmaps de section non-DIB ou des bitmaps de section DIB.|
|[CImage :: BitBlt](#bitblt)|Copie une image bitmap du contexte de périphérique source vers ce contexte de périphérique actuel.|
|[CImage :: Create](#create)|Crée une bitmap de section DIB et l’attache à l’objet précédemment construit `CImage` .|
|[CImage :: CreateEx](#createex)|Crée une bitmap de section DIB (avec des paramètres supplémentaires) et l’attache à l’objet construit précédemment `CImage` .|
|[CImage ::D estroy](#destroy)|Détache l’image bitmap de l' `CImage` objet et détruit la bitmap.|
|[CImage ::D Etach](#detach)|Détache l’image bitmap d’un `CImage` objet.|
|[CImage ::D RAW](#draw)|Copie une image bitmap à partir d’un rectangle source dans un rectangle de destination. `Draw` étire ou compresse l’image bitmap pour l’ajuster aux dimensions du rectangle de destination, si nécessaire, et gère la fusion alpha et les couleurs transparentes.|
|[CImage :: GetBits](#getbits)|Récupère un pointeur vers les valeurs de pixel réelles de la bitmap.|
|[CImage :: GetBPP](#getbpp)|Récupère les bits par pixel.|
|[CImage :: GetColorTable](#getcolortable)|Récupère les valeurs de couleur rouge, vert et bleu (RVB) à partir d’une plage d’entrées de la table des couleurs.|
|[CImage :: GetDC](#getdc)|Récupère le contexte de périphérique dans lequel la bitmap actuelle est sélectionnée.|
|[CImage :: GetExporterFilterString](#getexporterfilterstring)|Recherche les formats d’image disponibles et leurs descriptions.|
|[CImage :: GetHeight](#getheight)|Récupère, en pixels, la hauteur de l’image actuelle.|
|[CImage :: GetImporterFilterString](#getimporterfilterstring)|Recherche les formats d’image disponibles et leurs descriptions.|
|[CImage :: GetMaxColorTableEntries](#getmaxcolortableentries)|Récupère le nombre maximal d’entrées dans la table des couleurs.|
|[CImage :: GetPitch](#getpitch)|Récupère l’espacement de l’image actuelle, en octets.|
|[CImage :: GetPixel](#getpixel)|Récupère la couleur du pixel spécifié par *x* et *y*.|
|[CImage :: GetPixelAddress](#getpixeladdress)|Récupère l’adresse d’un pixel donné.|
|[CImage :: GetTransparentColor](#gettransparentcolor)|Récupère la position de la couleur transparente dans la table des couleurs.|
|[CImage :: GetWidth](#getwidth)|Récupère la largeur de l’image actuelle, en pixels.|
|[CImage :: IsDIBSection](#isdibsection)|Détermine si la bitmap attachée est une section DIB.|
|[CImage :: IsIndexed](#isindexed)|Indique que les couleurs d’une image bitmap sont mappées à une palette indexée.|
|[CImage :: IsNull](#isnull)|Indique si une bitmap source est actuellement chargée.|
|[CImage :: IsTransparencySupported](#istransparencysupported)|Indique si l’application prend en charge les bitmaps transparentes.|
|[CImage :: Load](#load)|Charge une image à partir du fichier spécifié.|
|[CImage :: LoadFromResource](#loadfromresource)|Charge une image à partir de la ressource spécifiée.|
|[CImage :: MaskBlt](#maskblt)|Combine les données de couleur pour les bitmaps sources et de destination à l’aide du masque et de l’opération Raster spécifiés.|
|[CImage ::P lgBlt](#plgblt)|Effectue un transfert de bloc de bits à partir d’un rectangle dans un contexte de périphérique source dans un parallélogramme dans un contexte de périphérique de destination.|
|[CImage :: ReleaseDC](#releasedc)|Libère le contexte de périphérique qui a été récupéré avec [CImage :: GetDC](#getdc).|
|[CImage :: ReleaseGDIPlus](#releasegdiplus)|Libère les ressources utilisées par GDI+. Doit être appelé pour libérer les ressources créées par un `CImage` objet global.|
|[CImage :: Save](#save)|Enregistre une image en tant que type spécifié. `Save` Impossible de spécifier des options d’image.|
|[CImage :: SetColorTable](#setcolortable)|Définit les valeurs de couleur rouge, vert, bleu, RVB) dans une plage d’entrées de la table des couleurs de la section DIB.|
|[CImage :: SetPixel](#setpixel)|Affecte la couleur spécifiée au pixel situé aux coordonnées spécifiées.|
|[CImage :: SetPixelIndexed](#setpixelindexed)|Définit le pixel aux coordonnées spécifiées sur la couleur à l’index spécifié de la palette.|
|[CImage :: SetPixelRGB](#setpixelrgb)|Affecte la valeur rouge, vert, bleu (RVB) spécifiée au pixel aux coordonnées spécifiées.|
|[CImage :: SetTransparentColor](#settransparentcolor)|Définit l’index de la couleur à traiter comme transparente. Une seule couleur dans une palette peut être transparente.|
|[CImage :: StretchBlt](#stretchblt)|Copie une image bitmap d’un rectangle source dans un rectangle de destination, en étirant ou en compressant l’image bitmap pour l’ajuster aux dimensions du rectangle de destination, si nécessaire.|
|[CImage :: TransparentBlt](#transparentblt)|Copie une image bitmap avec une couleur transparente du contexte de périphérique source vers ce contexte de périphérique actuel.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CImage :: Operator HBITMAP](#operator_hbitmap)|Retourne le handle Windows attaché à l' `CImage` objet.|

## <a name="remarks"></a>Notes

`CImage` prend ou non des bitmaps qui sont des sections DIB (Device-Independent Bitmap). Toutefois, vous pouvez utiliser [Create](#create) ou [CImage :: Load](#load) avec uniquement les sections dib. Vous pouvez attacher une image bitmap de section non-DIB à un `CImage` objet à l’aide de l' [attachement](#attach), mais vous ne pouvez pas utiliser les `CImage` méthodes suivantes, qui prennent en charge uniquement les bitmaps de section DIB :

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Pour déterminer si une bitmap attachée est une section DIB, appelez [IsDibSection](#isdibsection).

> [!NOTE]
> Dans Visual Studio .NET 2003, cette classe conserve le nombre d' `CImage` objets créés. Chaque fois que le nombre atteint 0, la fonction `GdiplusShutdown` est automatiquement appelée pour libérer les ressources utilisées par GDI+. Cela garantit que tous les `CImage` objets créés directement ou indirectement par les dll sont toujours détruits correctement et que n' `GdiplusShutdown` est pas appelé à partir de `DllMain` .

> [!NOTE]
> L’utilisation `CImage` d’objets globaux dans une dll n’est pas recommandée. Si vous devez utiliser un objet global `CImage` dans une dll, appelez [CImage :: ReleaseGDIPlus](#releasegdiplus) pour libérer explicitement les ressources utilisées par GDI+.

`CImage` ne peut pas être sélectionné dans un nouveau [CDC](../../mfc/reference/cdc-class.md). `CImage` crée son propre HDC pour l’image. Comme un HBITMAP ne peut être sélectionné que dans un seul HDC à la fois, l’HBITMAP associé au `CImage` ne peut pas être sélectionné dans un autre HDC. Si vous avez besoin d’un CDC, récupérez le HDC à partir du `CImage` et donnez-lui la valeur [CDC :: FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="examples"></a>Exemples

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Quand vous utilisez `CImage` dans un projet MFC, notez les fonctions membres de votre projet qui attendent un pointeur vers un objet [CBitmap](../../mfc/reference/cbitmap-class.md) . Si vous souhaitez utiliser `CImage` avec une telle fonction, comme [CMenu :: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), utilisez [CBitmap :: FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), transmettez-lui votre `CImage` HBITMAP et utilisez le retourné `CBitmap*` .

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

À `CImage` , vous avez accès aux bits réels d’une section dib. Vous pouvez utiliser un `CImage` objet partout où vous avez utilisé précédemment une section Win32 HBITMAP ou dib.

Vous pouvez utiliser `CImage` l’une des classes MFC ou ATL.

> [!NOTE]
> Lorsque vous créez un projet à l’aide `CImage` de, vous devez définir `CString` avant d’inclure *atlimage. h*. Si votre projet utilise ATL sans MFC, incluez *atlstr. h* avant d’inclure *atlimage. h*. Si votre projet utilise MFC (ou s’il s’agit d’un projet ATL avec prise en charge MFC), incluez *afxstr. h* avant d’inclure *atlimage. h*.
>
> De même, vous devez inclure *atlimage. h* avant d’inclure *Atlimpl. cpp*. Pour y parvenir facilement, incluez *atlimage. h* dans le *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures).

## <a name="requirements"></a>Spécifications

**En-tête :** atlimage. h

## <a name="cimagealphablend"></a><a name="alphablend"></a> CImage :: AlphaBlend

Affiche les bitmaps qui ont des pixels transparents ou translucides.

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

*hDestDC*<br/>
Handle vers le contexte de périphérique de destination.

*xDest*<br/>
Coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle de destination.

*bSrcAlpha*<br/>
Valeur de transparence alpha à utiliser sur l’intégralité de la bitmap source. La valeur par défaut 0xFF (255) suppose que votre image est opaque et que vous souhaitez utiliser uniquement des valeurs alpha par pixel.

*bBlendOp*<br/>
Fonction de fusion alpha pour les bitmaps sources et de destination, valeur alpha globale à appliquer à l’ensemble de la bitmap source et informations de mise en forme pour l’image bitmap source. Les fonctions Blend source et destination sont actuellement limitées à AC_SRC_OVER.

*pointDest*<br/>
Référence à une structure de [points](/windows/win32/api/windef/ns-windef-point) qui identifie l’angle supérieur gauche du rectangle de destination, en unités logiques.

*nDestWidth*<br/>
Largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
Hauteur, en unités logiques, du rectangle de destination.

*xSrc*<br/>
Coordonnée x logique de l’angle supérieur gauche du rectangle source.

*ySrc*<br/>
Coordonnée y logique de l’angle supérieur gauche du rectangle source.

*nSrcWidth*<br/>
Largeur, en unités logiques, du rectangle source.

*nSrcHeight*<br/>
Hauteur, en unités logiques, du rectangle source.

*rectDest*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) , identifiant la destination.

*rectSrc*<br/>
Référence à une `RECT` structure, identifiant la source.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les bitmaps de fusion alpha prennent en charge la fusion de couleurs par pixel.

Lorsque *bBlendOp* est défini sur la valeur par défaut de AC_SRC_OVER, la bitmap source est placée sur le bitmap de destination en fonction des valeurs alpha des pixels source.

## <a name="cimageattach"></a><a name="attach"></a> CImage :: Attach

Joint *HBITMAP* à un `CImage` objet.

```cpp
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Paramètres

*hBitmap*<br/>
Handle d’un HBITMAP.

*eOrientation*<br/>
Spécifie l’orientation de l’image bitmap. Il peut s'agir d'une des méthodes suivantes :

- DIBOR_DEFAULT l’orientation de la bitmap est déterminée par le système d’exploitation.

- DIBOR_BOTTOMUP les lignes de la bitmap sont dans l’ordre inverse. [CImage :: GetBits](#getbits) retourne alors un pointeur vers la fin de la mémoire tampon bitmap et [CImage :: GetPitch](#getpitch) pour retourner un nombre négatif.

- DIBOR_TOPDOWN les lignes de l’image bitmap sont dans l’ordre de haut en bas. [CImage :: GetBits](#getbits) retourne alors un pointeur vers le premier octet de la mémoire tampon bitmap et [CImage :: GetPitch](#getpitch) pour retourner un nombre positif.

### <a name="remarks"></a>Notes

La bitmap peut être une bitmap de section non DIB ou une bitmap de section DIB. Consultez [IsDIBSection](#isdibsection) pour obtenir la liste des méthodes que vous pouvez utiliser uniquement avec les bitmaps de section dib.

## <a name="cimagebitblt"></a><a name="bitblt"></a> CImage :: BitBlt

Copie une image bitmap du contexte de périphérique source vers ce contexte de périphérique actuel.

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

*hDestDC*<br/>
HDC de destination.

*xDest*<br/>
Coordonnée x logique de l’angle supérieur gauche du rectangle de destination.

*yDest*<br/>
Coordonnée y logique de l’angle supérieur gauche du rectangle de destination.

*dwROP*<br/>
Opération Raster à effectuer. Les codes d’opération Raster définissent exactement comment combiner les bits de la source, la destination et le modèle (comme défini par le pinceau actuellement sélectionné) pour former la destination. Pour obtenir la liste des autres codes d’opération Raster et leurs descriptions, consultez [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) dans le SDK Windows.

*pointDest*<br/>
Structure de [points](/windows/win32/api/windef/ns-windef-point) indiquant l’angle supérieur gauche du rectangle de destination.

*nDestWidth*<br/>
Largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
Hauteur, en unités logiques, du rectangle de destination.

*xSrc*<br/>
Coordonnée x logique de l’angle supérieur gauche du rectangle source.

*ySrc*<br/>
Coordonnée y logique de l’angle supérieur gauche du rectangle source.

*rectDest*<br/>
Structure [Rect](/windows/win32/api/windef/ns-windef-rect) indiquant le rectangle de destination.

*pointSrc*<br/>
`POINT`Structure qui indique l’angle supérieur gauche du rectangle source.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) dans le SDK Windows.

## <a name="cimagecimage"></a><a name="cimage"></a> CImage :: CImage

Construit un objet `CImage`.

```
CImage() throw();
```

### <a name="remarks"></a>Notes

Une fois que vous avez construit l’objet, appelez [Create](#create), [Load](#load), [LoadFromResource](#loadfromresource)ou [Attach](#attach) pour attacher une image bitmap à l’objet.

**Remarque** Dans Visual Studio, cette classe conserve le nombre d' `CImage` objets créés. Chaque fois que le nombre atteint 0, la fonction `GdiplusShutdown` est automatiquement appelée pour libérer les ressources utilisées par GDI+. Cela garantit que tous les `CImage` objets créés directement ou indirectement par les dll sont toujours détruits correctement et qu’ils `GdiplusShutdown` ne sont pas appelés depuis DllMain.

L’utilisation `CImage` d’objets globaux dans une dll n’est pas recommandée. Si vous devez utiliser un objet global `CImage` dans une dll, appelez [CImage :: ReleaseGDIPlus](#releasegdiplus) pour libérer explicitement les ressources utilisées par GDI+.

## <a name="cimagecreate"></a><a name="create"></a> CImage :: Create

Crée une `CImage` bitmap et l’attache à l’objet précédemment construit `CImage` .

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
Largeur de la `CImage` bitmap, en pixels.

*nHeight*<br/>
Hauteur de la `CImage` bitmap, en pixels. Si *nHeight* est positif, la bitmap est un DIB ascendant et son origine est l’angle inférieur gauche. Si *nHeight* est négatif, l’image bitmap est un DIB descendant et son origine est l’angle supérieur gauche.

*nBPP*<br/>
Nombre de bits par pixel dans la bitmap. Généralement 4, 8, 16, 24 ou 32. Peut être 1 pour des bitmaps ou des masques monochrome.

*dwFlags*<br/>
Spécifie si l’objet Bitmap a un canal alpha. Peut être une combinaison de zéro ou plusieurs des valeurs suivantes :

- *createAlphaChannel* Ne peut être utilisé que si *nBPP* est 32 et *eCompression* est BI_RGB. S’il est spécifié, l’image créée a une valeur alpha (transparence) pour chaque pixel, stockée dans le 4e octet de chaque pixel (inutilisé dans une image non alpha 32 bits). Ce canal alpha est utilisé automatiquement lors de l’appel de [CImage :: AlphaBlend](#alphablend).

> [!NOTE]
> Dans les appels à [CImage ::D RAW](#draw), les images avec un canal alpha sont automatiquement fusionnées dans la destination.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="cimagecreateex"></a><a name="createex"></a> CImage :: CreateEx

Crée une `CImage` bitmap et l’attache à l’objet précédemment construit `CImage` .

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

*nWidth*<br/>
Largeur de la `CImage` bitmap, en pixels.

*nHeight*<br/>
Hauteur de la `CImage` bitmap, en pixels. Si *nHeight* est positif, la bitmap est un DIB ascendant et son origine est l’angle inférieur gauche. Si *nHeight* est négatif, l’image bitmap est un DIB descendant et son origine est l’angle supérieur gauche.

*nBPP*<br/>
Nombre de bits par pixel dans la bitmap. Généralement 4, 8, 16, 24 ou 32. Peut être 1 pour des bitmaps ou des masques monochrome.

*eCompression*<br/>
Spécifie le type de compression d’une image bitmap ascendante compressée (les DIB descendants ne peuvent pas être compressés). Il peut s'agir de l'une des valeurs suivantes :

- BI_RGB le format n’est pas compressé. La spécification de cette valeur lors de l’appel `CImage::CreateEx` de équivaut à appeler `CImage::Create` .

- BI_BITFIELDS le format n’est pas compressé et la table des couleurs se compose de trois masques de couleur DWORD qui spécifient respectivement les composants rouge, vert et bleu de chaque pixel. Cela est valide lorsqu’il est utilisé avec des bitmaps 16 et 32-BPP.

*pdwBitfields*<br/>
Utilisé uniquement si *eCompression* a la valeur BI_BITFIELDS, sinon, il doit avoir la valeur null. Pointeur vers un tableau de trois masques de bits DWORD, spécifiant les bits de chaque pixel utilisés respectivement pour les composants rouge, vert et bleu de la couleur. Pour plus d’informations sur les restrictions pour les champs de données binaires, consultez [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) dans le SDK Windows.

*dwFlags*<br/>
Spécifie si l’objet Bitmap a un canal alpha. Peut être une combinaison de zéro ou plusieurs des valeurs suivantes :

- *createAlphaChannel* Ne peut être utilisé que si *nBPP* est 32 et *eCompression* est BI_RGB. S’il est spécifié, l’image créée a une valeur alpha (transparence) pour chaque pixel, stockée dans le 4e octet de chaque pixel (inutilisé dans une image non alpha 32 bits). Ce canal alpha est utilisé automatiquement lors de l’appel de [CImage :: AlphaBlend](#alphablend).

   > [!NOTE]
   > Dans les appels à [CImage ::D RAW](#draw), les images avec un canal alpha sont automatiquement fusionnées dans la destination.

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite. Sinon, FALSe.

### <a name="example"></a>Exemple

L’exemple suivant crée une image bitmap de pixel 100x100 à l’aide de 16 bits pour encoder chaque pixel. Dans un pixel 16 bits donné, bits 0-3 encode le composant rouge, bits 4-7 encode le vert et bits 8-11 encode le bleu. Les 4 bits restants ne sont pas utilisés.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a> CImage ::D estroy

Détache l’image bitmap de l' `CImage` objet et détruit la bitmap.

```cpp
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a> CImage ::D Etach

Détache une image bitmap d’un `CImage` objet.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Handle vers la bitmap détachée, ou NULL si aucune bitmap n’est attachée.

## <a name="cimagedraw"></a><a name="draw"></a> CImage ::D RAW

Copie une image bitmap du contexte de périphérique source vers le contexte de périphérique actuel.

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

*hDestDC*<br/>
Handle vers le contexte de périphérique de destination.

*xDest*<br/>
Coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle de destination.

*nDestWidth*<br/>
Largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
Hauteur, en unités logiques, du rectangle de destination.

*xSrc*<br/>
Coordonnée x, en unités logiques, de l’angle supérieur gauche du rectangle source.

*ySrc*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle source.

*nSrcWidth*<br/>
Largeur, en unités logiques, du rectangle source.

*nSrcHeight*<br/>
Hauteur, en unités logiques, du rectangle source.

*rectDest*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) , identifiant la destination.

*rectSrc*<br/>
Référence à une `RECT` structure, identifiant la source.

*pointDest*<br/>
Référence à une structure de [points](/windows/win32/api/windef/ns-windef-point) qui identifie l’angle supérieur gauche du rectangle de destination, en unités logiques.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`Draw` effectue la même opération que [StretchBlt](#stretchblt), sauf si l’image contient une couleur transparente ou un canal alpha. Dans ce cas, `Draw` effectue la même opération que [TransparentBlt](#transparentblt) ou [AlphaBlend](#alphablend) en fonction des besoins.

Pour les versions de `Draw` qui ne spécifient pas de rectangle source, l’ensemble de l’image source est la valeur par défaut. Pour la version de `Draw` qui ne spécifie pas de taille pour le rectangle de destination, la taille de l’image source est la valeur par défaut et aucun étirement ou rétrécissement ne se produit.

## <a name="cimagegetbits"></a><a name="getbits"></a> CImage :: GetBits

Récupère un pointeur vers les valeurs de bit réelles d’un pixel donné dans une bitmap.

```cpp
void* GetBits() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la mémoire tampon bitmap. Si la bitmap est un DIB ascendant, le pointeur pointe vers la fin de la mémoire tampon. Si la bitmap est un DIB descendant, le pointeur pointe vers le premier octet de la mémoire tampon.

### <a name="remarks"></a>Notes

À l’aide de ce pointeur, avec la valeur retournée par [GetPitch](#getpitch), vous pouvez rechercher et modifier des pixels individuels dans une image.

> [!NOTE]
> Cette méthode prend en charge uniquement les bitmaps de section DIB ; par conséquent, vous accédez aux pixels d’un `CImage` objet de la même façon que les pixels d’une section dib. Le pointeur retourné pointe vers le pixel à l’emplacement (0, 0).

## <a name="cimagegetbpp"></a><a name="getbpp"></a> CImage :: GetBPP

Récupère la valeur en bits par pixel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de bits par pixel.

### <a name="remarks"></a>Notes

Cette valeur détermine le nombre de bits qui définissent chaque pixel et le nombre maximal de couleurs dans l’image bitmap.

Les bits par pixel sont généralement 1, 4, 8, 16, 24 ou 32. `biBitCount`Pour plus d’informations sur cette valeur, consultez le membre de [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) dans la SDK Windows.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a> CImage :: GetColorTable

Récupère les valeurs de couleur rouge, vert et bleu (RVB) à partir d’une plage d’entrées dans la palette de la section DIB.

```cpp
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Paramètres

*iFirstColor*<br/>
Index de la table des couleurs de la première entrée à récupérer.

*nColors*<br/>
Nombre d’entrées de table des couleurs à récupérer.

*prgbColors*<br/>
Pointeur vers le tableau de structures [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) pour récupérer les entrées de la table des couleurs.

## <a name="cimagegetdc"></a><a name="getdc"></a> CImage :: GetDC

Récupère le contexte de périphérique sur lequel l’image est actuellement sélectionnée.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Handle d'un contexte de périphérique.

### <a name="remarks"></a>Notes

Pour chaque appel à `GetDC` , vous devez avoir un appel ultérieur à [ReleaseDC](#releasedc).

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a> CImage :: GetExporterFilterString

Recherche les formats d’image disponibles pour l’enregistrement des images.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Paramètres

*strExporters*<br/>
Référence à un objet `CSimpleString`. Pour plus d’informations, consultez la **section Notes** .

*aguidFileTypes*<br/>
Tableau de GUID, avec chaque élément correspondant à l’un des types de fichiers dans la chaîne. Dans l’exemple de *pszAllFilesDescription* ci-dessous, *aguidFileTypes*[0] est GUID_NULL et les valeurs restantes du tableau sont les formats de fichier image pris en charge par le système d’exploitation actuel.

> [!NOTE]
> Pour obtenir la liste complète des constantes, consultez **constantes de format de fichier image** dans le SDK Windows.

*pszAllFilesDescription*<br/>
Si ce paramètre n’est pas NULL, la chaîne de filtrage aura un filtre supplémentaire au début de la liste. Ce filtre aura la valeur actuelle de *pszAllFilesDescription* pour sa description et acceptera les fichiers de n’importe quelle extension prise en charge par tout autre exportateur de la liste.

Par exemple :

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Jeu d’indicateurs de bits spécifiant les types de fichiers à exclure de la liste. Les indicateurs autorisés sont les suivants :

- `excludeGIF` = 0x01 exclut les fichiers GIF.

- `excludeBMP` = 0x02 exclut les fichiers BMP (bitmap Windows).

- `excludeEMF` = 0x04 exclut les fichiers EMF (métafichier amélioré).

- `excludeWMF` = 0x08 exclut les fichiers WMF (Windows Metafile).

- `excludeJPEG` = 0x10 exclut les fichiers JPEG.

- `excludePNG` = 0x20 exclut les fichiers PNG.

- `excludeTIFF` = 0x40 exclut les fichiers TIFF.

- `excludeIcon` = 0x80 exclut les fichiers ICO (icône Windows).

- `excludeOther` = 0x80000000 exclut tout autre type de fichier non listé ci-dessus.

- `excludeDefaultLoad` = 0 pour le chargement, tous les types de fichiers sont inclus par défaut

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Pour l’enregistrement, ces fichiers sont exclus par défaut, car ils ont généralement des exigences particulières.

*chSeparator*<br/>
Séparateur utilisé entre les formats d’image. Pour plus d’informations, consultez la **section Notes** .

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez passer la chaîne de format obtenue à votre objet [CFILEDIALOG](../../mfc/reference/cfiledialog-class.md) MFC pour exposer les extensions de fichier des formats d’image disponibles dans la boîte de dialogue fichier enregistrer sous.

Le paramètre *strExporter* a le format suivant :

fichier description0&#124;\* . ext0&#124;filedescription1&#124;\* . EXT1&#124;... Description du fichier *n*&#124;\* . ext *n*&#124;&#124;

où' &#124; 'est le caractère de séparation spécifié par `chSeparator` . Par exemple :

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Utilisez le séparateur par défaut' &#124; 'si vous transmettez cette chaîne à un `CFileDialog` objet MFC. Utilisez le séparateur null « \ 0 » si vous transmettez cette chaîne à une boîte de dialogue d’enregistrement de fichiers communs.

## <a name="cimagegetheight"></a><a name="getheight"></a> CImage :: GetHeight

Récupère la hauteur, en pixels, d’une image.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Hauteur, en pixels, d’une image.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a> CImage :: GetImporterFilterString

Recherche les formats d’image disponibles pour le chargement des images.

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Paramètres

*strImporters*<br/>
Référence à un objet `CSimpleString`. Pour plus d’informations, consultez la **section Notes** .

*aguidFileTypes*<br/>
Tableau de GUID, avec chaque élément correspondant à l’un des types de fichiers dans la chaîne. Dans l’exemple de *pszAllFilesDescription* ci-dessous, *aguidFileTypes*[0] est GUID_NULL avec les valeurs restantes du tableau sont les formats de fichier image pris en charge par le système d’exploitation actuel.

> [!NOTE]
> Pour obtenir la liste complète des constantes, consultez **constantes de format de fichier image** dans le SDK Windows.

*pszAllFilesDescription*<br/>
Si ce paramètre n’est pas NULL, la chaîne de filtrage aura un filtre supplémentaire au début de la liste. Ce filtre aura la valeur actuelle de *pszAllFilesDescription* pour sa description et acceptera les fichiers de n’importe quelle extension prise en charge par tout autre exportateur de la liste.

Par exemple :

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Jeu d’indicateurs de bits spécifiant les types de fichiers à exclure de la liste. Les indicateurs autorisés sont les suivants :

- `excludeGIF` = 0x01 exclut les fichiers GIF.

- `excludeBMP` = 0x02 exclut les fichiers BMP (bitmap Windows).

- `excludeEMF` = 0x04 exclut les fichiers EMF (métafichier amélioré).

- `excludeWMF` = 0x08 exclut les fichiers WMF (Windows Metafile).

- `excludeJPEG` = 0x10 exclut les fichiers JPEG.

- `excludePNG` = 0x20 exclut les fichiers PNG.

- `excludeTIFF` = 0x40 exclut les fichiers TIFF.

- `excludeIcon` = 0x80 exclut les fichiers ICO (icône Windows).

- `excludeOther` = 0x80000000 exclut tout autre type de fichier non listé ci-dessus.

- `excludeDefaultLoad` = 0 pour le chargement, tous les types de fichiers sont inclus par défaut

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Pour l’enregistrement, ces fichiers sont exclus par défaut, car ils ont généralement des exigences particulières.

*chSeparator*<br/>
Séparateur utilisé entre les formats d’image. Pour plus d’informations, consultez la **section Notes** .

### <a name="remarks"></a>Notes

Vous pouvez passer la chaîne de format obtenue à votre objet [CFILEDIALOG](../../mfc/reference/cfiledialog-class.md) MFC pour exposer les extensions de fichier des formats d’image disponibles dans la boîte de dialogue **ouvrir un fichier** .

Le paramètre *strImporter* a le format suivant :

fichier description0&#124;\* . ext0&#124;filedescription1&#124;\* . EXT1&#124;... Description du fichier *n*&#124;\* . ext *n*&#124;&#124;

où' &#124; 'est le caractère de séparation spécifié par *chSeparator*. Par exemple :

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Utilisez le séparateur par défaut' &#124; 'si vous transmettez cette chaîne à un `CFileDialog` objet MFC. Utilisez le séparateur null « \ 0 » si vous transmettez cette chaîne à une boîte de dialogue d' **ouverture de fichier** commune.

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a> CImage :: GetMaxColorTableEntries

Récupère le nombre maximal d’entrées dans la table des couleurs.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’entrées dans la table des couleurs.

### <a name="remarks"></a>Notes

Cette méthode prend en charge uniquement les bitmaps de section DIB.

## <a name="cimagegetpitch"></a><a name="getpitch"></a> CImage :: GetPitch

Récupère le pas d’une image.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Hauteur de l’image. Si la valeur de retour est négative, l’image bitmap est un DIB ascendant et son origine est l’angle inférieur gauche. Si la valeur de retour est positive, le bitmap est un DIB descendant et son origine est l’angle supérieur gauche.

### <a name="remarks"></a>Notes

Le pas est la distance, en octets, entre deux adresses mémoire qui représentent le début d’une ligne bitmap et le début de la ligne bitmap suivante. Étant donné que la hauteur tonale est mesurée en octets, le pas d’une image vous aide à déterminer le format de pixel. Le pas peut également inclure de la mémoire supplémentaire, réservée à la bitmap.

Utilisez `GetPitch` with [GetBits](#getbits) pour rechercher des pixels individuels d’une image.

> [!NOTE]
> Cette méthode prend en charge uniquement les bitmaps de section DIB.

## <a name="cimagegetpixel"></a><a name="getpixel"></a> CImage :: GetPixel

Récupère la couleur du pixel à l’emplacement spécifié par *x* et *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Coordonnée x du pixel.

*y*<br/>
Coordonnée y du pixel.

### <a name="return-value"></a>Valeur renvoyée

Valeur rouge, verte, bleue (RVB) du pixel. Si le pixel est en dehors de la zone de découpage actuelle, la valeur de retour est CLR_INVALID.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a> CImage :: GetPixelAddress

Récupère l’adresse exacte d’un pixel.

```cpp
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Coordonnée x du pixel.

*y*<br/>
Coordonnée y du pixel.

### <a name="remarks"></a>Notes

L’adresse est déterminée en fonction des coordonnées d’un pixel, du pas de la bitmap et des bits par pixel.

Pour les formats qui ont moins de 8 bits par pixel, cette méthode retourne l’adresse de l’octet contenant le pixel. Par exemple, si votre format d’image contient 4 bits par pixel, `GetPixelAddress` retourne l’adresse du premier pixel de l’octet et vous devez calculer pour 2 pixels par octet.

> [!NOTE]
> Cette méthode prend en charge uniquement les bitmaps de section DIB.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a> CImage :: GetTransparentColor

Récupère l’emplacement indexé de la couleur transparente dans la palette de couleurs.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Index de la couleur transparente.

## <a name="cimagegetwidth"></a><a name="getwidth"></a> CImage :: GetWidth

Récupère la largeur, en pixels, d’une image.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Largeur de la bitmap, en pixels.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a> CImage :: IsDIBSection

Détermine si la bitmap attachée est une section DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la bitmap attachée est une section DIB. Sinon, FALSe.

### <a name="remarks"></a>Notes

Si la bitmap n’est pas une section DIB, vous ne pouvez pas utiliser les `CImage` méthodes suivantes, qui ne prennent en charge que les bitmaps de section DIB :

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a> CImage :: IsIndexed

Détermine si les pixels d’une bitmap sont mappés à une palette de couleurs.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si indexé ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode retourne TRUE uniquement si la bitmap est de 8 bits (256 couleurs) ou moins.

> [!NOTE]
> Cette méthode prend en charge uniquement les bitmaps de section DIB.

## <a name="cimageisnull"></a><a name="isnull"></a> CImage :: IsNull

Détermine si une bitmap est actuellement chargée.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur TRUE si une bitmap n’est pas actuellement chargée ; Sinon, FALSe.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a> CImage :: IsTransparencySupported

Indique si l’application prend en charge les bitmaps transparentes.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la plateforme actuelle prend en charge la transparence. Sinon, 0.

### <a name="remarks"></a>Notes

Si la valeur de retour est différente de zéro et que la transparence est prise en charge, un appel à [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)ou [Draw](#draw) gérera les couleurs transparentes.

## <a name="cimageload"></a><a name="load"></a> CImage :: Load

Charge une image.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pszFileName*<br/>
Pointeur vers une chaîne contenant le nom du fichier image à charger.

*pStream*<br/>
Pointeur vers un flux contenant le nom du fichier image à charger.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Charge l’image spécifiée par *pszFileName* ou *pStream*.

Les types d’images valides sont BMP, GIF, JPEG, PNG et TIFF.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a> CImage :: LoadFromResource

Charge une image à partir d’une ressource BITMAP.

```cpp
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
Handle vers une instance du module qui contient l’image à charger.

*pszResourceName*<br/>
Pointeur vers la chaîne contenant le nom de la ressource contenant l’image à charger.

*nIDResource*<br/>
ID de la ressource à charger.

### <a name="remarks"></a>Notes

La ressource doit être de type BITMAP.

## <a name="cimagemaskblt"></a><a name="maskblt"></a> CImage :: MaskBlt

Combine les données de couleur pour les bitmaps sources et de destination à l’aide du masque et de l’opération Raster spécifiés.

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

*hDestDC*<br/>
Handle du module dont l’exécutable contient la ressource.

*xDest*<br/>
Coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle de destination.

*nDestWidth*<br/>
Largeur, en unités logiques, du rectangle de destination et de la bitmap source.

*nDestHeight*<br/>
Hauteur, en unités logiques, du rectangle de destination et de la bitmap source.

*xSrc*<br/>
Coordonnée x logique de l’angle supérieur gauche de l’image bitmap source.

*ySrc*<br/>
Coordonnée y logique de l’angle supérieur gauche de la bitmap source.

*hbmMask*<br/>
Handle vers la bitmap de masque monochrome associée à la bitmap de couleur dans le contexte de périphérique source.

*xMask*<br/>
Décalage de pixel horizontal pour la bitmap de masque spécifiée par le paramètre *hbmMask* .

*yMask*<br/>
Décalage vertical en pixels de la bitmap de masque spécifiée par le paramètre *hbmMask* .

*dwROP*<br/>
Spécifie les codes d’opération Raster ternaire de premier plan et d’arrière-plan que la méthode utilise pour contrôler la combinaison des données source et de destination. Le code d’opération Raster d’arrière-plan est stocké dans l’octet de poids fort du mot de poids fort de cette valeur ; le code d’opération Raster de premier plan est stocké dans l’octet de poids faible du mot de poids fort de cette valeur ; le mot de poids faible de cette valeur est ignoré et doit être égal à zéro. Pour une description du premier plan et de l’arrière-plan dans le contexte de cette méthode, consultez `MaskBlt` dans la SDK Windows. Pour obtenir la liste des codes d’opération raster courants, consultez `BitBlt` dans la SDK Windows.

*rectDest*<br/>
Référence à une `RECT` structure, identifiant la destination.

*pointSrc*<br/>
`POINT`Structure qui indique l’angle supérieur gauche du rectangle source.

*pointMask*<br/>
`POINT`Structure qui indique l’angle supérieur gauche de la bitmap du masque.

*pointDest*<br/>
Référence à une `POINT` structure qui identifie l’angle supérieur gauche du rectangle de destination, en unités logiques.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Cette méthode s’applique uniquement à Windows NT, versions 4,0 et ultérieures.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a> CImage :: Operator HBITMAP

Utilisez cet opérateur pour récupérer le handle Windows GDI attaché de l' `CImage` objet. Cet opérateur est un opérateur de cast qui prend en charge l’utilisation directe d’un objet HBITMAP.

## <a name="cimageplgblt"></a><a name="plgblt"></a> CImage ::P lgBlt

Effectue un transfert de bloc de bits à partir d’un rectangle dans un contexte de périphérique source dans un parallélogramme dans un contexte de périphérique de destination.

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

*hDestDC*<br/>
Handle vers le contexte de périphérique de destination.

*pPoints*<br/>
Pointeur vers un tableau de trois points dans l’espace logique qui identifie trois angles du parallélogramme de destination. L’angle supérieur gauche du rectangle source est mappé au premier point de ce tableau, le coin supérieur droit au deuxième point de ce tableau, et le coin inférieur gauche au troisième point. L’angle inférieur droit du rectangle source est mappé au quatrième point implicite du parallélogramme.

*hbmMask*<br/>
Handle vers une image bitmap monochrome facultative qui est utilisée pour masquer les couleurs du rectangle source.

*xSrc*<br/>
Coordonnée x, en unités logiques, de l’angle supérieur gauche du rectangle source.

*ySrc*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle source.

*nSrcWidth*<br/>
Largeur, en unités logiques, du rectangle source.

*nSrcHeight*<br/>
Hauteur, en unités logiques, du rectangle source.

*xMask*<br/>
Coordonnée x de l’angle supérieur gauche de l’image bitmap monochrome.

*yMask*<br/>
Coordonnée y de l’angle supérieur gauche de la bitmap monochrome.

*rectSrc*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) spécifiant les coordonnées du rectangle source.

*pointMask*<br/>
Structure de [points](/windows/win32/api/windef/ns-windef-point) indiquant l’angle supérieur gauche de la bitmap du masque.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Si *hbmMask* identifie une image bitmap monochrome valide, `PlgBit` utilise cette bitmap pour masquer les bits des données de couleur du rectangle source.

Cette méthode s’applique uniquement à Windows NT, versions 4,0 et ultérieures. Pour plus d’informations, consultez [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) dans le SDK Windows.

## <a name="cimagereleasedc"></a><a name="releasedc"></a> CImage :: ReleaseDC

Libère le contexte de périphérique.

```cpp
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Notes

Étant donné qu’une seule bitmap peut être sélectionnée dans un contexte de périphérique à la fois, vous devez appeler `ReleaseDC` pour chaque appel à [GetDC](#getdc).

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a> CImage :: ReleaseGDIPlus

Libère les ressources utilisées par GDI+.

```cpp
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Notes

Cette méthode doit être appelée pour libérer des ressources allouées par un `CImage` objet global. Consultez [CImage :: CImage](#cimage).

## <a name="cimagesave"></a><a name="save"></a> CImage :: Save

Enregistre une image dans le flux ou le fichier spécifié sur le disque.

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
Pointeur vers un objet COM IStream contenant les données d’image de fichier.

*pszFileName*<br/>
Pointeur vers le nom de fichier de l’image.

*guidFileType*<br/>
Type de fichier dans lequel enregistrer l’image. Il peut s'agir d'une des méthodes suivantes :

- `ImageFormatBMP` Image bitmap non compressée.

- `ImageFormatPNG` Image compressée PNG (Portable Network Graphic).

- `ImageFormatJPEG` Image JPEG compressée.

- `ImageFormatGIF` Image GIF compressée.

> [!NOTE]
> Pour obtenir la liste complète des constantes, consultez **constantes de format de fichier image** dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Appelez cette fonction pour enregistrer l’image à l’aide d’un nom et d’un type spécifiés. Si le paramètre *guidFileType* n’est pas inclus, l’extension de fichier du nom de fichier est utilisée pour déterminer le format de l’image. Si aucune extension n’est fournie, l’image est enregistrée au format BMP.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a> CImage :: SetColorTable

Définit les valeurs de couleur rouge, vert et bleu (RVB) pour une plage d’entrées dans la palette de la section DIB.

```cpp
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Paramètres

*iFirstColor*<br/>
Index de la table des couleurs de la première entrée à définir.

*nColors*<br/>
Nombre d’entrées de table des couleurs à définir.

*prgbColors*<br/>
Pointeur vers le tableau de structures [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) pour définir les entrées de la table des couleurs.

### <a name="remarks"></a>Notes

Cette méthode prend en charge uniquement les bitmaps de section DIB.

## <a name="cimagesetpixel"></a><a name="setpixel"></a> CImage :: SetPixel

Définit la couleur d’un pixel à un emplacement donné dans l’image bitmap.

```cpp
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Emplacement horizontal du pixel à définir.

*y*<br/>
Emplacement vertical du pixel à définir.

*color*<br/>
Couleur dans laquelle vous définissez le pixel.

### <a name="remarks"></a>Notes

Cette méthode échoue si les coordonnées en pixels se trouvent en dehors de la zone de découpage sélectionnée.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a> CImage :: SetPixelIndexed

Définit la couleur du pixel sur la couleur située dans *iIndex* dans la palette de couleurs.

```cpp
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Emplacement horizontal du pixel à définir.

*y*<br/>
Emplacement vertical du pixel à définir.

*iIndex*<br/>
Index d’une couleur dans la palette de couleurs.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a> CImage :: SetPixelRGB

Définit le pixel aux emplacements spécifiés par *x* et *y* sur les couleurs indiquées par *r*, *v* et *b*, dans une image rouge, verte, bleue (RVB).

```cpp
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Emplacement horizontal du pixel à définir.

*y*<br/>
Emplacement vertical du pixel à définir.

*r*<br/>
Intensité de la couleur rouge.

*activée*<br/>
Intensité de la couleur verte.

*b*<br/>
Intensité de la couleur bleue.

### <a name="remarks"></a>Notes

Les paramètres rouge, vert et bleu sont représentés par un nombre compris entre 0 et 255. Si vous définissez les trois paramètres sur zéro, la couleur résultante combinée est noire. Si vous définissez les trois paramètres sur 255, la couleur résultante combinée est blanche.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a> CImage :: SetTransparentColor

Définit une couleur à un emplacement d’index donné comme transparente.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Paramètres

*iTransparentColor*<br/>
Index, dans une palette de couleurs, de la couleur à définir comme transparente. Si-1, aucune couleur n’est définie sur transparent.

### <a name="return-value"></a>Valeur renvoyée

L’index de la couleur précédemment défini comme transparent.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a> CImage :: StretchBlt

Copie une image bitmap du contexte de périphérique source vers ce contexte de périphérique actuel.

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

*hDestDC*<br/>
Handle vers le contexte de périphérique de destination.

*xDest*<br/>
Coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle de destination.

*nDestWidth*<br/>
Largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
Hauteur, en unités logiques, du rectangle de destination.

*dwROP*<br/>
Opération Raster à effectuer. Les codes d’opération Raster définissent exactement comment combiner les bits de la source, la destination et le modèle (comme défini par le pinceau actuellement sélectionné) pour former la destination. Pour obtenir la liste des autres codes d’opération Raster et leurs descriptions, consultez [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) dans le SDK Windows.

*rectDest*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) , identifiant la destination.

*xSrc*<br/>
Coordonnée x, en unités logiques, de l’angle supérieur gauche du rectangle source.

*ySrc*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle source.

*nSrcWidth*<br/>
Largeur, en unités logiques, du rectangle source.

*nSrcHeight*<br/>
Hauteur, en unités logiques, du rectangle source.

*rectSrc*<br/>
Référence à une `RECT` structure, identifiant la source.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite, sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) dans le SDK Windows.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a> CImage :: TransparentBlt

Copie une image bitmap du contexte de périphérique source vers ce contexte de périphérique actuel.

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

*hDestDC*<br/>
Handle vers le contexte de périphérique de destination.

*xDest*<br/>
Coordonnée x, en unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle de destination.

*nDestWidth*<br/>
Largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
Hauteur, en unités logiques, du rectangle de destination.

*crTransparent*<br/>
Couleur de la bitmap source à traiter comme transparente. Par défaut, CLR_INVALID, indiquant que la couleur actuellement définie en tant que couleur transparente de l’image doit être utilisée.

*rectDest*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) , identifiant la destination.

*xSrc*<br/>
Coordonnée x, en unités logiques, de l’angle supérieur gauche du rectangle source.

*ySrc*<br/>
Coordonnée y, en unités logiques, de l’angle supérieur gauche du rectangle source.

*nSrcWidth*<br/>
Largeur, en unités logiques, du rectangle source.

*nSrcHeight*<br/>
Hauteur, en unités logiques, du rectangle source.

*rectSrc*<br/>
Référence à une `RECT` structure, identifiant la source.

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite ; sinon, FALSe.

### <a name="remarks"></a>Notes

`TransparentBlt` est pris en charge pour les bitmaps sources de 4 bits par pixel et 8 bits par pixel. Utilisez [CImage :: AlphaBlend](#alphablend) pour spécifier des bitmaps 32 bits par pixel avec transparence.

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

[Exemple MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[SimpleImage, exemple](../../overview/visual-cpp-samples.md)<br/>
[Bitmaps indépendantes du périphérique](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)<br/>
[Bitmaps indépendantes du périphérique](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
