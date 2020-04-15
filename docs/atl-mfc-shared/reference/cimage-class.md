---
title: Classe CImage
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
ms.openlocfilehash: 5b5ef833a3755b07e42a60b24464b1f260062d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317808"
---
# <a name="cimage-class"></a>Classe CImage

`CImage`fournit un support bitmap amélioré, y compris la possibilité de charger et d’enregistrer des images dans les formats JPEG, GIF, BMP et Portable Network Graphics (PNG).

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
|[CImage::CImage](#cimage)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|Affiche des bitmaps qui ont des pixels transparents ou semi-transparents.|
|[CImage::Attach](#attach)|Attache un HBITMAP `CImage` à un objet. Peut être utilisé avec des bitmaps de section non-DIB ou bitmaps section DIB.|
|[CImage::BitBlt](#bitblt)|Copies d’un bitmap du contexte de l’appareil source à ce contexte actuel de l’appareil.|
|[CImage::Créer](#create)|Crée une bitmap de section DIB et `CImage` l’attache à l’objet précédemment construit.|
|[CImage::CreateEx](#createex)|Crée une bitmap de section DIB (avec des paramètres `CImage` supplémentaires) et l’attache à l’objet précédemment construit.|
|[CImage::Destroy](#destroy)|Détache la bitmap de `CImage` l’objet et détruit la bitmap.|
|[CImage::Detach](#detach)|Détache la bitmap d’un `CImage` objet.|
|[CImage::Draw](#draw)|Copie d’un bitmap à partir d’un rectangle source dans un rectangle de destination. `Draw`étire ou comprime la bitmap pour s’adapter aux dimensions du rectangle de destination, si nécessaire, et gère le mélange alpha et les couleurs transparentes.|
|[CImage::GetBits](#getbits)|Récupère un pointeur sur les valeurs réelles de pixels de la bitmap.|
|[CImage::GetBPP](#getbpp)|Récupère les bits par pixel.|
|[CImage::GetColorTable](#getcolortable)|Récupère les valeurs de couleur rouge, verte, bleue (RGB) d’une gamme d’entrées dans la table de couleur.|
|[CImage::GetDC](#getdc)|Récupère le contexte de l’appareil dans lequel le bitmap actuel est sélectionné.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Trouve les formats d’image disponibles et leurs descriptions.|
|[CImage::GetHeight](#getheight)|Récupère la hauteur de l’image actuelle en pixels.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Trouve les formats d’image disponibles et leurs descriptions.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Récupère le nombre maximum d’entrées dans la table couleur.|
|[CImage::GetPitch](#getpitch)|Récupère la hauteur de l’image actuelle, dans les octets.|
|[CImage::GetPixel](#getpixel)|Récupère la couleur du pixel spécifié par *x* et *y*.|
|[CImage::GetPixelAddress](#getpixeladdress)|Récupère l’adresse d’un pixel donné.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Récupère la position de la couleur transparente dans la table de couleur.|
|[CImage::GetWidth](#getwidth)|Récupère la largeur de l’image actuelle en pixels.|
|[CImage::IsDIBSection](#isdibsection)|Détermine si le bitmap ci-joint est une section DIB.|
|[CImage::IsIndexed](#isindexed)|Indique que les couleurs d’un bitmap sont cartographiées à une palette indexée.|
|[CImage::IsNull](#isnull)|Indique si un bitmap source est actuellement chargé.|
|[CImage::IsTransparencySupported](#istransparencysupported)|Indique si l’application prend en charge les bitmaps transparents.|
|[CImage::Load](#load)|Charge une image à partir du fichier spécifié.|
|[CImage::LoadDeResource](#loadfromresource)|Charge une image à partir de la ressource spécifiée.|
|[CImage::MaskBlt](#maskblt)|Combine les données de couleur pour les bitmaps source et destination à l’aide du masque spécifié et de l’opération raster.|
|[CImage::PlgBlt](#plgblt)|Effectue un transfert de bit-bloc à partir d’un rectangle dans un contexte de périphérique source dans un parallélogramme dans un contexte de périphérique de destination.|
|[CImage::ReleaseDC](#releasedc)|Communiqués le contexte de l’appareil qui a été récupéré avec [CImage::GetDC](#getdc).|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Libère les ressources utilisées par GDIMD. Doit être appelé à libérer `CImage` les ressources créées par un objet global.|
|[CImage::Enregistrer](#save)|Enregistre une image comme type spécifié. `Save`ne peut pas spécifier les options d’image.|
|[CImage::SetColorTable](#setcolortable)|Définit les valeurs de couleur rouge, verte et bleue de RGB dans une gamme d’entrées dans la table couleur de la section DIB.|
|[CImage::SetPixel](#setpixel)|Définit le pixel aux coordonnées spécifiées à la couleur spécifiée.|
|[CImage::SetPixelIndexé](#setpixelindexed)|Définit le pixel aux coordonnées spécifiées à la couleur à l’index spécifié de la palette.|
|[CImage::SetPixelRGB](#setpixelrgb)|Définit le pixel aux coordonnées spécifiées à la valeur rouge, verte, bleue (RGB) spécifiée.|
|[CImage::SetTransparentColor](#settransparentcolor)|Définit l’index de la couleur à traiter comme transparent. Une seule couleur dans une palette peut être transparente.|
|[CImage::StretchBlt](#stretchblt)|Copie d’un bitmap à partir d’un rectangle source dans un rectangle de destination, en étirant ou comprimant la bitmap pour s’adapter aux dimensions du rectangle de destination, si nécessaire.|
|[CImage::TransparentBlt](#transparentblt)|Copies d’une bitmap avec une couleur transparente du contexte de l’appareil source à ce contexte actuel de l’appareil.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CImage::opérateur HBITMAP](#operator_hbitmap)|Retourne la poignée Windows `CImage` attachée à l’objet.|

## <a name="remarks"></a>Notes

`CImage`prend des bitmaps qui sont soit des sections de bitmap (DIB) indépendantes de l’appareil ou non; cependant, vous pouvez utiliser [Create](#create) ou [CImage::Load](#load) avec seulement les sections DIB. Vous pouvez joindre un bitmap section `CImage` non-DIB à un objet `CImage` en utilisant [Attach](#attach), mais alors vous ne pouvez pas utiliser les méthodes suivantes, qui ne prennent en charge que les bitmaps de section DIB:

- [GetBits (en)](#getbits)

- [GetColorTable (en)](#getcolortable)

- [GetMaxColorTableEntries (en)](#getmaxcolortableentries)

- [GetPitch GetPitch](#getpitch)

- [GetPixelAddress GetPixelAddress GetPixelAddress GetPix](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable (en)](#setcolortable)

Pour déterminer si un bitmap attaché est une section DIB, appelez [IsDibSection](#isdibsection).

> [!NOTE]
> Dans Visual Studio .NET 2003, cette classe `CImage` tient un compte du nombre d’objets créés. Chaque fois que le nombre `GdiplusShutdown` passe à 0, la fonction est automatiquement appelée pour libérer les ressources utilisées par GDI. Cela garantit que `CImage` tous les objets créés directement ou indirectement par `GdiplusShutdown` les DLL sont toujours détruits correctement et qui n’est pas appelé de `DllMain`.

> [!NOTE]
> L’utilisation d’objets globaux `CImage` dans un DLL n’est pas recommandée. Si vous avez besoin `CImage` d’utiliser un objet global dans un DLL, appelez [CImage::ReleaseGDIPlus](#releasegdiplus) pour libérer explicitement les ressources utilisées par GDI.

`CImage`ne peuvent pas être sélectionnés dans un nouveau [CDC](../../mfc/reference/cdc-class.md). `CImage`crée son propre HDC pour l’image. Étant donné qu’un HBITMAP ne peut être sélectionné qu’en un `CImage` seul HDC à la fois, le HBITMAP associé au HBITMAP ne peut pas être sélectionné dans un autre CDH. Si vous avez besoin d’un `CImage` CDC, récupérez le HDC de la CDC [et donnez-le à CDC::FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="example"></a>Exemple

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Lorsque vous `CImage` utilisez dans un projet MFC, notez quelles fonctions les membres de votre projet s’attendent à un pointeur à un objet [CBitmap.](../../mfc/reference/cbitmap-class.md) Si vous voulez `CImage` utiliser avec une telle fonction, comme [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), utilisez [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), passez-le votre `CImage` HBITMAP, et utilisez le retour `CBitmap*`.

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

Grâce `CImage`à , vous avez accès aux bits réels d’une section DIB. Vous pouvez `CImage` utiliser un objet n’importe où vous avez déjà utilisé une section Win32 HBITMAP ou DIB.

Vous pouvez `CImage` utiliser à partir de MFC ou ATL.

> [!NOTE]
> Lorsque vous créez `CImage`un projet `CString` à l’aide, vous devez définir avant d’inclure *atlimage.h*. Si votre projet utilise ATL sans MFC, incluez *atlstr.h* avant d’inclure *atlimage.h*. Si votre projet utilise MFC (ou s’il s’agit d’un projet ATL avec support MFC), incluez *afxstr.h* avant d’inclure *atlimage.h*.<br/>
> <br/>
> De même, vous devez inclure *atlimage.h* avant d’inclure *atlimpl.cpp*. Pour ce faire facilement, inclure *atlimage.h* dans votre *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt).

## <a name="requirements"></a>Spécifications

**En-tête:** atlimage.h

## <a name="cimagealphablend"></a><a name="alphablend"></a>CImage::AlphaBlend

Affiche des bitmaps qui ont des pixels transparents ou semi-transparents.

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
Gérer le contexte de l’appareil de destination.

*xDest*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*bSrcAlpha*<br/>
Une valeur de transparence alpha à utiliser sur l’ensemble de la bitmap source. La valeur 0xff par défaut (255) suppose que votre image est opaque, et que vous souhaitez utiliser des valeurs alpha par pixel seulement.

*bBlendOp (en)*<br/>
La fonction alpha-mélange pour les bitmaps source et destination, une valeur alpha globale à appliquer à l’ensemble de la bitmap source, et des informations de format pour la bitmap source. Les fonctions de mélange source et destination sont actuellement limitées à AC_SRC_OVER.

*pointDest*<br/>
Une référence à une structure [POINT](/previous-versions/dd162805\(v=vs.85\)) qui identifie le coin supérieur gauche du rectangle de destination, dans les unités logiques.

*nDestWidth (en)*<br/>
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
La hauteur, en unités logiques, du rectangle de destination.

*xSrc (en)*<br/>
La logique x-coordonner le coin supérieur gauche du rectangle source.

*ySrc (en)*<br/>
La logique y-coordinate du coin supérieur gauche du rectangle source.

*nSrcWidth (en)*<br/>
La largeur, en unités logiques, du rectangle source.

*nSrcHeight (en)*<br/>
La hauteur, en unités logiques, du rectangle source.

*rectDest*<br/>
Une référence à une structure [RECT,](/previous-versions/dd162897\(v=vs.85\)) l’identification de la destination.

*rectSrc*<br/>
Une référence `RECT` à une structure, l’identification de la source.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les bitmaps Alpha-blend soutiennent le mélange de couleur par pixel.

Lorsque *bBlendOp* est réglé à la valeur par défaut de AC_SRC_OVER, le bitmap source est placé sur la bitmap de destination en fonction des valeurs alpha des pixels source.

## <a name="cimageattach"></a><a name="attach"></a>CImage::Attach

Attache *hBitmap* à `CImage` un objet.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Paramètres

*hBitmap (en)*<br/>
Une poignée à un HBITMAP.

*e Orientation*<br/>
Spécifie l’orientation de la bitmap. Il peut s'agir d'une des méthodes suivantes :

- DIBOR_DEFAULT L’orientation de la bitmap est déterminée par le système d’exploitation.

- DIBOR_BOTTOMUP Les lignes de la bitmap sont en ordre inverse. Cela provoque [CImage::GetBits](#getbits) de retourner un pointeur vers la fin de la mémoire tampon bitmap et [CImage::GetPitch](#getpitch) pour retourner un nombre négatif.

- DIBOR_TOPDOWN Les lignes de la bitmap sont en ordre supérieur à inférieur. Cela provoque [CImage::GetBits](#getbits) de retourner un pointeur à la première byte de la tampon bitmap et [CImage::GetPitch](#getpitch) pour retourner un nombre positif.

### <a name="remarks"></a>Notes

Le bitmap peut être soit un bitmap section non-DIB ou un bitmap section DIB. Consultez [IsDIBSection](#isdibsection) pour une liste de méthodes que vous ne pouvez utiliser qu’avec les bitmaps de section DIB.

## <a name="cimagebitblt"></a><a name="bitblt"></a>CImage::BitBlt

Copies d’un bitmap du contexte de l’appareil source à ce contexte actuel de l’appareil.

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
La destination HDC.

*xDest*<br/>
La logique x-coordonner le coin supérieur gauche du rectangle de destination.

*yDest*<br/>
La logique y-coordinate du coin supérieur gauche du rectangle de destination.

*dwROP dwROP*<br/>
L’opération de raster à effectuer. Les codes d’exploitation raster définissent exactement comment combiner les bits de la source, la destination et le modèle (tel que défini par le pinceau actuellement sélectionné) pour former la destination. Voir [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) dans le Windows SDK pour une liste d’autres codes d’exploitation raster et leurs descriptions.

*pointDest*<br/>
Une structure [POINT](/previous-versions/dd162805\(v=vs.85\)) indiquant le coin supérieur gauche du rectangle de destination.

*nDestWidth (en)*<br/>
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
La hauteur, en unités logiques, du rectangle de destination.

*xSrc (en)*<br/>
La logique x-coordonner le coin supérieur gauche du rectangle source.

*ySrc (en)*<br/>
La logique y-coordinate du coin supérieur gauche du rectangle source.

*rectDest*<br/>
Une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) indiquant le rectangle de destination.

*pointSrc*<br/>
Une `POINT` structure indiquant le coin supérieur gauche du rectangle source.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) dans windows SDK.

## <a name="cimagecimage"></a><a name="cimage"></a>CImage::CImage

Construit un objet `CImage`.

```
CImage() throw();
```

### <a name="remarks"></a>Notes

Une fois que vous avez construit l’objet, appelez [Attach](#attach) [Créer,](#create) [Load](#load) [ChargerDeResource](#loadfromresource), ou attacher pour attacher une bitmap à l’objet.

**Note** Dans Visual Studio, cette classe tient `CImage` un compte du nombre d’objets créés. Chaque fois que le nombre `GdiplusShutdown` passe à 0, la fonction est automatiquement appelée pour libérer les ressources utilisées par GDI. Cela garantit que `CImage` tous les objets créés directement ou indirectement par `GdiplusShutdown` les DLL sont toujours détruits correctement et qui n’est pas appelé de DllMain.

L’utilisation d’objets globaux `CImage` dans un DLL n’est pas recommandée. Si vous avez besoin `CImage` d’utiliser un objet global dans un DLL, appelez [CImage::ReleaseGDIPlus](#releasegdiplus) pour libérer explicitement les ressources utilisées par GDI.

## <a name="cimagecreate"></a><a name="create"></a>CImage::Créer

Crée `CImage` une bitmap et l’attache à l’objet précédemment construit. `CImage`

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Paramètres

*nWidth (en)*<br/>
La largeur `CImage` de la bitmap, en pixels.

*nHeight (en)*<br/>
La hauteur `CImage` de la bitmap, en pixels. Si *nHeight* est positif, le bitmap est un DIB ascendant et son origine est le coin inférieur gauche. Si *nHeight* est négatif, le bitmap est un DIB haut de gamme et son origine est le coin supérieur gauche.

*nBPP (en)*<br/>
Les nombres de bits par pixel dans la bitmap. Habituellement 4, 8, 16, 24 ou 32. Peut être 1 pour les bitmaps monochromes ou des masques.

*dwFlags*<br/>
Précise si l’objet bitmap a un canal alpha. Peut être une combinaison de zéro ou plus des valeurs suivantes :

- *createAlphaChannel* Ne peut être utilisé que si *nBPP* est de 32, et *eCompression* est BI_RGB. Si spécifié, l’image créée a une valeur alpha (transparence) pour chaque pixel, stocké dans le 4ème byte de chaque pixel (inutilisé dans une image non-alpha 32 bits). Ce canal alpha est automatiquement utilisé lors de l’appel [CImage:AlphaBlend](#alphablend).

> [!NOTE]
> Dans les appels à [CImage::Draw](#draw), les images avec un canal alpha sont automatiquement alpha mélangés à la destination.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="cimagecreateex"></a><a name="createex"></a>CImage::CreateEx

Crée `CImage` une bitmap et l’attache à l’objet précédemment construit. `CImage`

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

*nWidth (en)*<br/>
La largeur `CImage` de la bitmap, en pixels.

*nHeight (en)*<br/>
La hauteur `CImage` de la bitmap, en pixels. Si *nHeight* est positif, le bitmap est un DIB ascendant et son origine est le coin inférieur gauche. Si *nHeight* est négatif, le bitmap est un DIB haut de gamme et son origine est le coin supérieur gauche.

*nBPP (en)*<br/>
Les nombres de bits par pixel dans la bitmap. Habituellement 4, 8, 16, 24 ou 32. Peut être 1 pour les bitmaps monochromes ou des masques.

*eCompression*<br/>
Specifie le type de compression d’une bitmap ascendante comprimée (les DIB descendants ne peuvent pas être comprimés). Il peut s'agir de l'une des valeurs suivantes :

- BI_RGB Le format n’est pas compressé. Spécifier cette `CImage::CreateEx` valeur lors `CImage::Create`de l’appel équivaut à appeler .

- BI_BITFIELDS Le format n’est pas compressé et la table couleur se compose de trois masques de couleur DWORD qui spécifient les composants rouges, verts et bleus, respectivement, de chaque pixel. Ceci est valable lorsqu’il est utilisé avec des bitmaps de 16 et 32 bpp.

*pdwBitfields*<br/>
Utilisé uniquement si *l’eCompression* est configuré pour BI_BITFIELDS, sinon il doit être NULL. Un pointeur à un tableau de trois bitmasks DWORD, spécifiant quels morceaux de chaque pixel sont utilisés pour les composants rouges, verts et bleus de la couleur, respectivement. Pour plus d’informations sur les restrictions pour les bitfields, voir [BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) dans le SDK Windows.

*dwFlags*<br/>
Précise si l’objet bitmap a un canal alpha. Peut être une combinaison de zéro ou plus des valeurs suivantes :

- *createAlphaChannel* Ne peut être utilisé que si *nBPP* est de 32, et *eCompression* est BI_RGB. Si spécifié, l’image créée a une valeur alpha (transparence) pour chaque pixel, stocké dans le 4ème byte de chaque pixel (inutilisé dans une image non-alpha 32 bits). Ce canal alpha est automatiquement utilisé lors de l’appel [CImage:AlphaBlend](#alphablend).

   > [!NOTE]
   > Dans les appels à [CImage::Draw](#draw), les images avec un canal alpha sont automatiquement alpha mélangés à la destination.

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès. Sinon FALSE.

### <a name="example"></a>Exemple

L’exemple suivant crée un bitmap de 100x100 pixels, en utilisant 16 bits pour encoder chaque pixel. Dans un pixel donné de 16 bits, les bits 0-3 codent le composant rouge, mord 4-7 encodé le vert, et les bits 8-11 coder bleu. Les 4 bits restants ne sont pas utilisés.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a>CImage::Destroy

Détache la bitmap de `CImage` l’objet et détruit la bitmap.

```
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a>CImage::Detach

Détache un bitmap d’un `CImage` objet.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Une poignée à la bitmap détaché, ou NULL si aucune bitmap n’est attaché.

## <a name="cimagedraw"></a><a name="draw"></a>CImage::Draw

Copies d’un bitmap du contexte de l’appareil source au contexte actuel de l’appareil.

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
Une poignée vers le contexte de l’appareil de destination.

*xDest*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*nDestWidth (en)*<br/>
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
La hauteur, en unités logiques, du rectangle de destination.

*xSrc (en)*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle source.

*ySrc (en)*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle source.

*nSrcWidth (en)*<br/>
La largeur, en unités logiques, du rectangle source.

*nSrcHeight (en)*<br/>
La hauteur, en unités logiques, du rectangle source.

*rectDest*<br/>
Une référence à une structure [RECT,](/previous-versions/dd162897\(v=vs.85\)) l’identification de la destination.

*rectSrc*<br/>
Une référence `RECT` à une structure, l’identification de la source.

*pointDest*<br/>
Une référence à une structure [POINT](/previous-versions/dd162805\(v=vs.85\)) qui identifie le coin supérieur gauche du rectangle de destination, dans les unités logiques.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`Draw`effectue la même opération que [StretchBlt](#stretchblt), à moins que l’image ne contienne une couleur transparente ou un canal alpha. Dans ce `Draw` cas, effectue la même opération que [TransparentBlt](#transparentblt) ou [AlphaBlend](#alphablend) que nécessaire.

Pour les `Draw` versions de ce ne spécifient pas un rectangle source, l’image source entière est la valeur par défaut. Pour la `Draw` version de qui ne spécifie pas une taille pour le rectangle de destination, la taille de l’image source est la valeur par défaut et aucun étirement ou rétrécissement se produit.

## <a name="cimagegetbits"></a><a name="getbits"></a>CImage::GetBits

Récupère un pointeur sur les valeurs réelles de bits d’un pixel donné dans un bitmap.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le tampon de bitmap. Si le bitmap est un DIB ascendant, le pointeur pointe vers la fin du tampon. Si le bitmap est un DIB haut de gamme, le pointeur pointe vers le premier byte du tampon.

### <a name="remarks"></a>Notes

En utilisant ce pointeur, avec la valeur retournée par [GetPitch](#getpitch), vous pouvez localiser et modifier les pixels individuels dans une image.

> [!NOTE]
> Cette méthode ne prend en charge que les bitmaps de section DIB; par conséquent, vous accédez `CImage` aux pixels d’un objet de la même façon que vous le feriez les pixels d’une section DIB. Le pointeur retourné pointe vers le pixel à l’emplacement (0, 0).

## <a name="cimagegetbpp"></a><a name="getbpp"></a>CImage::GetBPP

Récupère la valeur des bits par pixel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de bits par pixel.

### <a name="remarks"></a>Notes

Cette valeur détermine le nombre de bits qui définissent chaque pixel et le nombre maximum de couleurs dans la bitmap.

Les bits par pixel est généralement 1, 4, 8, 16, 24, ou 32. Consultez `biBitCount` le membre de [BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) dans le Windows SDK pour plus d’informations sur cette valeur.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a>CImage::GetColorTable

Récupère les valeurs de couleur rouge, verte, bleue (RGB) d’une gamme d’entrées dans la palette de la section DIB.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Paramètres

*iFirstColor (iFirstColor)*<br/>
L’index de table couleur de la première entrée à récupérer.

*nColors*<br/>
Le nombre d’entrées de table couleur à récupérer.

*prgbColors*<br/>
Un pointeur à la gamme de structures [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) pour récupérer les entrées de table de couleur.

## <a name="cimagegetdc"></a><a name="getdc"></a>CImage::GetDC

Récupère le contexte de l’appareil qui a actuellement l’image sélectionnée en elle.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Valeur de retour

Handle d'un contexte de périphérique.

### <a name="remarks"></a>Notes

Pour chaque `GetDC`appel à , vous devez avoir un appel ultérieur à [ReleaseDC](#releasedc).

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage::GetExporterFilterString

Trouve des formats d’images disponibles pour enregistrer des images.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Paramètres

*strExporters (en anglais)*<br/>
Référence à un objet `CSimpleString`. Voir **Remarques** pour plus d’informations.

*aguidFileTypes*<br/>
Un tableau de GUIDs, avec chaque élément correspondant à l’un des types de fichiers dans la chaîne. Dans l’exemple de *pszAllFilesDescription* ci-dessous, *aguidFileTypes*[0] est GUID_NULL et les valeurs de tableau restantes sont les formats de fichiers d’image pris en charge par le système d’exploitation actuel.

> [!NOTE]
> Pour une liste complète des constantes, voir **Image File Format Constants** dans le SDK Windows.

*pszAllFilesDescription*<br/>
Si ce paramètre n’est pas NULL, la chaîne de filtre aura un filtre supplémentaire au début de la liste. Ce filtre aura la valeur actuelle de *pszAllFilesDescription* pour sa description, et accepte les fichiers de toute extension prise en charge par tout autre exportateur dans la liste.

Par exemple :

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Ensemble de drapeaux bits spécifiant quels types de fichiers à exclure de la liste. Les drapeaux admissibles sont les :

- `excludeGIF`0x01 Exclut les fichiers GIF.

- `excludeBMP`0x02 Exclut les fichiers BMP (Windows Bitmap).

- `excludeEMF`0x04 Exclut les fichiers EMF (Enhanced Metafile).

- `excludeWMF`0x08 exclut les fichiers WMF (Windows Metafile).

- `excludeJPEG`0x10 Exclut les fichiers JPEG.

- `excludePNG`0x20 Exclut les fichiers PNG.

- `excludeTIFF`0x40 Exclut les fichiers TIFF.

- `excludeIcon`0x80 Exclut les fichiers ICO (Windows Icon).

- `excludeOther`0x80000000 Exclut tout autre type de fichier non répertorié ci-dessus.

- `excludeDefaultLoad`0 Pour la charge, tous les types de fichiers sont inclus par défaut

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Pour l’enregistrement, ces fichiers sont exclus par défaut parce qu’ils ont généralement des exigences spéciales.

*chSeparator (en)*<br/>
Le séparateur utilisé entre les formats d’image. Voir **Remarques** pour plus d’informations.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez transmettre la chaîne de format résultante à votre objet MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) pour exposer les extensions de fichiers des formats d’image disponibles dans la boîte de dialogue De Fichier Save As.

Le paramètre *strExporter* a le format:

description de dossier0 \*&#124;.ext0&#124;filedescription1 \*&#124;.ext1&#124;... description *de* fichier n \*&#124;.ext *n*&#124;&#124;

où '&#124;' est le caractère séparateur spécifié par `chSeparator`. Par exemple :

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Utilisez le séparateur par défaut '&#124;' si vous `CFileDialog` passez cette chaîne à un objet MFC. Utilisez le séparateur nul '0' si vous passez cette chaîne à une boîte commune de dialogue De Fichier Enregistrer.

## <a name="cimagegetheight"></a><a name="getheight"></a>CImage::GetHeight

Récupère la hauteur, en pixels, d’une image.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Valeur de retour

La hauteur, en pixels, d’une image.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage::GetImporterFilterString

Trouve des formats d’images disponibles pour le chargement des images.

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
Référence à un objet `CSimpleString`. Voir **Remarques** pour plus d’informations.

*aguidFileTypes*<br/>
Un tableau de GUIDs, avec chaque élément correspondant à l’un des types de fichiers dans la chaîne. Dans l’exemple de *pszAllFilesDescription* ci-dessous, *aguidFileTypes*[0] est GUID_NULL avec les valeurs de tableau restantes sont les formats de fichiers d’image pris en charge par le système d’exploitation actuel.

> [!NOTE]
> Pour une liste complète des constantes, voir **Image File Format Constants** dans le SDK Windows.

*pszAllFilesDescription*<br/>
Si ce paramètre n’est pas NULL, la chaîne de filtre aura un filtre supplémentaire au début de la liste. Ce filtre aura la valeur actuelle de *pszAllFilesDescription* pour sa description, et accepte les fichiers de toute extension prise en charge par tout autre exportateur dans la liste.

Par exemple :

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Ensemble de drapeaux bits spécifiant quels types de fichiers à exclure de la liste. Les drapeaux admissibles sont les :

- `excludeGIF`0x01 Exclut les fichiers GIF.

- `excludeBMP`0x02 Exclut les fichiers BMP (Windows Bitmap).

- `excludeEMF`0x04 Exclut les fichiers EMF (Enhanced Metafile).

- `excludeWMF`0x08 exclut les fichiers WMF (Windows Metafile).

- `excludeJPEG`0x10 Exclut les fichiers JPEG.

- `excludePNG`0x20 Exclut les fichiers PNG.

- `excludeTIFF`0x40 Exclut les fichiers TIFF.

- `excludeIcon`0x80 Exclut les fichiers ICO (Windows Icon).

- `excludeOther`0x80000000 Exclut tout autre type de fichier non répertorié ci-dessus.

- `excludeDefaultLoad`0 Pour la charge, tous les types de fichiers sont inclus par défaut

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Pour l’enregistrement, ces fichiers sont exclus par défaut parce qu’ils ont généralement des exigences spéciales.

*chSeparator (en)*<br/>
Le séparateur utilisé entre les formats d’image. Voir **Remarques** pour plus d’informations.

### <a name="remarks"></a>Notes

Vous pouvez transmettre la chaîne de format résultante à votre objet MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) pour exposer les extensions de fichiers des formats d’image disponibles dans la boîte de dialogue **File Open.**

Le paramètre *strImporter* a le format:

description de dossier0 \*&#124;.ext0&#124;filedescription1 \*&#124;.ext1&#124;... description *de* fichier n \*&#124;.ext *n*&#124;&#124;

où '&#124;' est le caractère séparateur spécifié par *chSeparator*. Par exemple :

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Utilisez le séparateur par défaut '&#124;' si vous `CFileDialog` passez cette chaîne à un objet MFC. Utilisez le séparateur nul '0' si vous passez cette chaîne à une boîte de dialogue commune **File Open.**

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage::GetMaxColorTableEntries

Récupère le nombre maximum d’entrées dans la table couleur.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’entrées dans la table de couleur.

### <a name="remarks"></a>Notes

Cette méthode ne prend en charge que les bitmaps de section DIB.

## <a name="cimagegetpitch"></a><a name="getpitch"></a>CImage::GetPitch

Récupère la hauteur d’une image.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Valeur de retour

La hauteur de l’image. Si la valeur de retour est négative, la bitmap est un DIB ascendant et son origine est le coin inférieur gauche. Si la valeur de retour est positive, la bitmap est un DIB haut de gamme et son origine est le coin supérieur gauche.

### <a name="remarks"></a>Notes

Le terrain est la distance, dans les octets, entre deux adresses mémoire qui représentent le début d’une ligne de bitmap et le début de la ligne suivante bitmap. Parce que la hauteur est mesurée en octets, la hauteur d’une image vous aide à déterminer le format pixel. Le pitch peut également inclure une mémoire supplémentaire, réservée à la bitmap.

Utilisez `GetPitch` avec [GetBits](#getbits) pour trouver des pixels individuels d’une image.

> [!NOTE]
> Cette méthode ne prend en charge que les bitmaps de section DIB.

## <a name="cimagegetpixel"></a><a name="getpixel"></a>CImage::GetPixel

Récupère la couleur du pixel à l’emplacement spécifié par *x* et *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Paramètres

*X*<br/>
La x-coordonnées du pixel.

*y*<br/>
Le y-coordinate du pixel.

### <a name="return-value"></a>Valeur de retour

La valeur rouge, verte, bleue (RGB) du pixel. Si le pixel est en dehors de la région de coupure actuelle, la valeur de retour est CLR_INVALID.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage::GetPixelAddress

Récupère l’adresse exacte d’un pixel.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Paramètres

*X*<br/>
La x-coordonnées du pixel.

*y*<br/>
Le y-coordinate du pixel.

### <a name="remarks"></a>Notes

L’adresse est déterminée en fonction des coordonnées d’un pixel, de la hauteur de la bitmap et des bits par pixel.

Pour les formats qui ont moins de 8 bits par pixel, cette méthode renvoie l’adresse du byte contenant le pixel. Par exemple, si votre format d’image `GetPixelAddress` a 4 bits par pixel, retourne l’adresse du premier pixel dans le byte, et vous devez calculer pour 2 pixels par byte.

> [!NOTE]
> Cette méthode ne prend en charge que les bitmaps de section DIB.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage::GetTransparentColor

Récupère l’emplacement indexé de la couleur transparente dans la palette de couleurs.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Valeur de retour

L’index de la couleur transparente.

## <a name="cimagegetwidth"></a><a name="getwidth"></a>CImage::GetWidth

Récupère la largeur, en pixels, d’une image.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Valeur de retour

La largeur de la bitmap, en pixels.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a>CImage::IsDIBSection

Détermine si le bitmap ci-joint est une section DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bitmap ci-joint est une section DIB. Sinon FALSE.

### <a name="remarks"></a>Notes

Si la bitmap n’est pas une section `CImage` DIB, vous ne pouvez pas utiliser les méthodes suivantes, qui ne prennent en charge que les bitmaps section DIB:

- [GetBits (en)](#getbits)

- [GetColorTable (en)](#getcolortable)

- [GetMaxColorTableEntries (en)](#getmaxcolortableentries)

- [GetPitch GetPitch](#getpitch)

- [GetPixelAddress GetPixelAddress GetPixelAddress GetPix](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable (en)](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a>CImage::IsIndexed

Détermine si les pixels d’un bitmap sont cartographiés à une palette de couleurs.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Valeur de retour

VRAI s’il est indexé; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode ne renvoie TRUE que si le bit est 8 bits (256 couleurs) ou moins.

> [!NOTE]
> Cette méthode ne prend en charge que les bitmaps de section DIB.

## <a name="cimageisnull"></a><a name="isnull"></a>CImage::IsNull

Détermine si une bitmap est actuellement chargée.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Notes

Cette méthode renvoie VRAI si un bitmap n’est pas actuellement chargé; autrement FALSE.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage::IsTransparencySupported

Indique si l’application prend en charge les bitmaps transparents.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la plate-forme actuelle prend en charge la transparence. Sinon, 0.

### <a name="remarks"></a>Notes

Si la valeur de retour est nonzero, et la transparence est prise en charge, un appel à [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt), ou [Draw](#draw) gérera des couleurs transparentes.

## <a name="cimageload"></a><a name="load"></a>CImage::Load

Charge une image.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Paramètres

*pszFileName*<br/>
Un pointeur à une chaîne contenant le nom du fichier d’image à charger.

*pStream*<br/>
Un pointeur à un flux contenant le nom du fichier d’image à charger.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Charge l’image *spécifiée par pszFileName* ou *pStream*.

Les types d’images valides sont BMP, GIF, JPEG, PNG et TIFF.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a>CImage::LoadDeResource

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

*hInstance*<br/>
Gérer à une instance du module qui contient l’image à charger.

*pszResourceName (en)*<br/>
Un pointeur à la chaîne contenant le nom de la ressource contenant l’image à charger.

*nIDResource (en)*<br/>
ID de la ressource à charger.

### <a name="remarks"></a>Notes

La ressource doit être de type BITMAP.

## <a name="cimagemaskblt"></a><a name="maskblt"></a>CImage::MaskBlt

Combine les données de couleur pour les bitmaps source et destination à l’aide du masque spécifié et de l’opération raster.

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
Le manche du module dont l’exécution contient la ressource.

*xDest*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*nDestWidth (en)*<br/>
La largeur, en unités logiques, du rectangle de destination et de la bitmap source.

*nDestHeight*<br/>
La hauteur, en unités logiques, du rectangle de destination et de la bitmap source.

*xSrc (en)*<br/>
La logique x-coordonner le coin supérieur gauche de la bitmap source.

*ySrc (en)*<br/>
La logique y-coordinate du coin supérieur gauche de la bitmap source.

*hbmMask*<br/>
Poignée au bitmap masque monochrome combiné avec la bitmap couleur dans le contexte de l’appareil source.

*xMask xMask*<br/>
Le décalage horizontal de pixel pour le bitmap de masque spécifié par le paramètre *hbmMask.*

*yMask yMask*<br/>
Le décalage de pixel vertical pour le bitmap de masque spécifié par le paramètre *hbmMask.*

*dwROP dwROP*<br/>
Spécifie à la fois les codes d’opération de raster ternaires au premier plan et de fond que la méthode utilise pour contrôler la combinaison des données de source et de destination. Le code d’opération raster de fond est stocké dans le sous-officier de haute commande du mot de haute commande de cette valeur ; le code d’opération raster au premier plan est stocké dans l’ordre réduit du mot de haute commande de cette valeur; le mot de faible ordre de cette valeur est ignoré, et doit être nul. Pour une discussion de premier plan et de fond `MaskBlt` dans le contexte de cette méthode, voir dans le SDK Windows. Pour une liste de codes d’opération de raster communs, voir `BitBlt` dans le SDK Windows.

*rectDest*<br/>
Une référence `RECT` à une structure, l’identification de la destination.

*pointSrc*<br/>
Une `POINT` structure indiquant le coin supérieur gauche du rectangle source.

*pointMask*<br/>
Une `POINT` structure indiquant le coin supérieur gauche de la bitmap masque.

*pointDest*<br/>
Une référence `POINT` à une structure qui identifie le coin supérieur gauche du rectangle de destination, dans les unités logiques.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès, sinon 0.

### <a name="remarks"></a>Notes

Cette méthode s’applique à Windows NT, versions 4.0 et plus tard seulement.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage::opérateur HBITMAP

Utilisez cet opérateur pour obtenir la poignée `CImage` Windows GDI attachée de l’objet. Cet opérateur est un opérateur de coulée, qui prend en charge l’utilisation directe d’un objet HBITMAP.

## <a name="cimageplgblt"></a><a name="plgblt"></a>CImage::PlgBlt

Effectue un transfert de bit-bloc à partir d’un rectangle dans un contexte de périphérique source dans un parallélogramme dans un contexte de périphérique de destination.

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
Une poignée vers le contexte de l’appareil de destination.

*pPoints (en)*<br/>
Un pointeur à un tableau de trois points dans l’espace logique qui identifient trois coins du parallélogramme de destination. Le coin supérieur gauche du rectangle source est cartographié au premier point de ce tableau, le coin supérieur droit au deuxième point de ce tableau, et le coin inférieur gauche au troisième point. Le coin inférieur droit du rectangle source est cartographié au quatrième point implicite du parallélogramme.

*hbmMask*<br/>
Une poignée à un bitmap monochrome en option qui est utilisé pour masquer les couleurs du rectangle source.

*xSrc (en)*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle source.

*ySrc (en)*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle source.

*nSrcWidth (en)*<br/>
La largeur, en unités logiques, du rectangle source.

*nSrcHeight (en)*<br/>
La hauteur, en unités logiques, du rectangle source.

*xMask xMask*<br/>
Le x-coordonner le coin supérieur gauche de la bitmap monochrome.

*yMask yMask*<br/>
Le y-coordinate du coin supérieur gauche de la bitmap monochrome.

*rectSrc*<br/>
Une référence à une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) spécifiant les coordonnées du rectangle source.

*pointMask*<br/>
Une structure [POINT](/previous-versions/dd162805\(v=vs.85\)) indiquant le coin supérieur gauche de la bitmap masque.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès, sinon 0.

### <a name="remarks"></a>Notes

Si *hbmMask* identifie une bitmap monochrome valide, `PlgBit` utilise cette bitmap pour masquer les bits de données de couleur du rectangle source.

Cette méthode s’applique à Windows NT, versions 4.0 et plus tard seulement. Voir [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) dans le Windows SDK pour plus d’informations détaillées.

## <a name="cimagereleasedc"></a><a name="releasedc"></a>CImage::ReleaseDC

Libère le contexte de l’appareil.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Notes

Parce qu’une seule bitmap peut être sélectionnée dans `ReleaseDC` un contexte d’appareil à la fois, vous devez appeler pour chaque appel à [GetDC](#getdc).

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage::ReleaseGDIPlus

Libère les ressources utilisées par GDIMD.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Notes

Cette méthode doit être appelée aux ressources `CImage` gratuites allouées par un objet global. Voir [CImage:CImage](#cimage).

## <a name="cimagesave"></a><a name="save"></a>CImage::Enregistrer

Enregistre une image sur le flux ou le fichier spécifié sur disque.

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
Un pointeur vers un objet COM IStream contenant les données d’image de fichier.

*pszFileName*<br/>
Un pointeur sur le nom du fichier pour l’image.

*guidFileType*<br/>
Le type de fichier pour enregistrer l’image comme. Il peut s'agir d'une des méthodes suivantes :

- `ImageFormatBMP`Une image de bitmap non compressée.

- `ImageFormatPNG`Une image compressée de graphique de réseau portable (PNG).

- `ImageFormatJPEG`Une image compressée JPEG.

- `ImageFormatGIF`Une image compressée GIF.

> [!NOTE]
> Pour une liste complète des constantes, voir **Image File Format Constants** dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Appelez cette fonction pour enregistrer l’image à l’aide d’un nom et d’un type spécifiés. Si le paramètre *guidFileType* n’est pas inclus, l’extension du fichier du nom de fichier sera utilisée pour déterminer le format d’image. Si aucune extension n’est fournie, l’image sera enregistrée en format BMP.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a>CImage::SetColorTable

Définit les valeurs de couleur rouge, verte, bleue (RGB) pour une gamme d’entrées dans la palette de la section DIB.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Paramètres

*iFirstColor (iFirstColor)*<br/>
L’index de table couleur de la première entrée à définir.

*nColors*<br/>
Le nombre d’entrées de table couleur à définir.

*prgbColors*<br/>
Un pointeur à la gamme de structures [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) pour définir les entrées de table de couleur.

### <a name="remarks"></a>Notes

Cette méthode ne prend en charge que les bitmaps de section DIB.

## <a name="cimagesetpixel"></a><a name="setpixel"></a>CImage::SetPixel

Définit la couleur d’un pixel à un endroit donné dans la bitmap.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Paramètres

*X*<br/>
L’emplacement horizontal du pixel à définir.

*y*<br/>
L’emplacement vertical du pixel à définir.

*Couleur*<br/>
La couleur à laquelle vous définissez le pixel.

### <a name="remarks"></a>Notes

Cette méthode échoue si les coordonnées de pixel se trouvent en dehors de la région de coupure sélectionnée.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage::SetPixelIndexé

Définit la couleur pixel à la couleur située à *iIndex* dans la palette de couleurs.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Paramètres

*X*<br/>
L’emplacement horizontal du pixel à définir.

*y*<br/>
L’emplacement vertical du pixel à définir.

*iIndex (en)*<br/>
L’index d’une couleur dans la palette de couleurs.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage::SetPixelRGB

Définit le pixel aux endroits spécifiés par *x* et *y* aux couleurs indiquées par *r,* *g*, et *b*, dans une image rouge, verte, bleue (RGB).

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Paramètres

*X*<br/>
L’emplacement horizontal du pixel à définir.

*y*<br/>
L’emplacement vertical du pixel à définir.

*R*<br/>
L’intensité de la couleur rouge.

*G*<br/>
L’intensité de la couleur verte.

*B*<br/>
L’intensité de la couleur bleue.

### <a name="remarks"></a>Notes

Les paramètres rouges, verts et bleus sont représentés chacun par un nombre compris entre 0 et 255. Si vous définissez les trois paramètres à zéro, la couleur combinée résultante est noir. Si vous définissez les trois paramètres à 255, la couleur combinée résultante est blanche.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage::SetTransparentColor

Définit une couleur à un endroit indexé donné comme transparent.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Paramètres

*iTransparentColor*<br/>
L’index, dans une palette de couleurs, de la couleur à définir à transparent. Si -1, aucune couleur n’est définie pour être transparente.

### <a name="return-value"></a>Valeur de retour

L’index de la couleur précédemment défini comme transparent.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a>CImage::StretchBlt

Copies d’un bitmap du contexte de l’appareil source à ce contexte actuel de l’appareil.

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
Une poignée vers le contexte de l’appareil de destination.

*xDest*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*nDestWidth (en)*<br/>
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
La hauteur, en unités logiques, du rectangle de destination.

*dwROP dwROP*<br/>
L’opération de raster à effectuer. Les codes d’exploitation raster définissent exactement comment combiner les bits de la source, la destination et le modèle (tel que défini par le pinceau actuellement sélectionné) pour former la destination. Voir [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) dans le Windows SDK pour une liste d’autres codes d’exploitation raster et leurs descriptions.

*rectDest*<br/>
Une référence à une structure [RECT,](/previous-versions/dd162897\(v=vs.85\)) l’identification de la destination.

*xSrc (en)*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle source.

*ySrc (en)*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle source.

*nSrcWidth (en)*<br/>
La largeur, en unités logiques, du rectangle source.

*nSrcHeight (en)*<br/>
La hauteur, en unités logiques, du rectangle source.

*rectSrc*<br/>
Une référence `RECT` à une structure, l’identification de la source.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès, sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) dans windows SDK.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a>CImage::TransparentBlt

Copies d’un bitmap du contexte de l’appareil source à ce contexte actuel de l’appareil.

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
Une poignée vers le contexte de l’appareil de destination.

*xDest*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*yDest*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle de destination.

*nDestWidth (en)*<br/>
La largeur, en unités logiques, du rectangle de destination.

*nDestHeight*<br/>
La hauteur, en unités logiques, du rectangle de destination.

*crTransparent*<br/>
La couleur dans la bitmap source à traiter comme transparent. Par défaut, CLR_INVALID, indiquant que la couleur actuellement définie comme la couleur transparente de l’image doit être utilisée.

*rectDest*<br/>
Une référence à une structure [RECT,](/previous-versions/dd162897\(v=vs.85\)) l’identification de la destination.

*xSrc (en)*<br/>
Le x-coordonner, dans les unités logiques, du coin supérieur gauche du rectangle source.

*ySrc (en)*<br/>
Le y-coordinate, dans les unités logiques, du coin supérieur gauche du rectangle source.

*nSrcWidth (en)*<br/>
La largeur, en unités logiques, du rectangle source.

*nSrcHeight (en)*<br/>
La hauteur, en unités logiques, du rectangle source.

*rectSrc*<br/>
Une référence `RECT` à une structure, l’identification de la source.

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès, sinon FALSE.

### <a name="remarks"></a>Notes

`TransparentBlt`est pris en charge pour les bitmaps source de 4 bits par pixel et 8 bits par pixel. Utilisez [CImage::AlphaBlend](#alphablend) pour spécifier 32 bits par pixel bitmaps avec transparence.

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

[Échantillon MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Échantillon SimpleImage](../../overview/visual-cpp-samples.md)<br/>
[Bitmaps indépendants de l’appareil](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CréationDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)<br/>
[Bitmaps indépendants de l’appareil](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CréationDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
