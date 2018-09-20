---
title: CBitmap, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
dev_langs:
- C++
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 322b13ee62e61a836d6b0c66ab619a11348adeae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375639"
---
# <a name="cbitmap-class"></a>CBitmap (classe)

Encapsule une bitmap GDI (Graphics Device Interface) Windows et fournit des fonctions membres pour la manipuler.

## <a name="syntax"></a>Syntaxe

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmap::CBitmap](#cbitmap)|Construit un objet `CBitmap`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBitmap::CreateBitmap](#createbitmap)|Initialise l’objet avec une image bitmap dépendant du périphérique mémoire qui a une largeur spécifiée, la hauteur et le modèle binaire.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Initialise l’objet avec une image bitmap avec la largeur, la hauteur et le modèle binaire (le cas échéant) donné dans un `BITMAP` structure.|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Initialise l’objet avec une image bitmap afin qu’il soit compatible avec un périphérique spécifié.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Initialise l’objet avec une image bitmap pouvant être éliminée qui est compatible avec un périphérique spécifié.|
|[CBitmap::FromHandle](#fromhandle)|Retourne un pointeur vers un `CBitmap` lorsqu’un handle vers un Windows de l’objet `HBITMAP` bitmap.|
|[CBitmap::GetBitmap](#getbitmap)|Remplit un `BITMAP` structure avec des informations sur l’image bitmap.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Copie les bits de la bitmap spécifiée dans la mémoire tampon spécifiée.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Retourne la largeur et la hauteur de la bitmap. La hauteur et largeur sont supposées ont été définis précédemment par le [SetBitmapDimension](#setbitmapdimension) fonction membre.|
|[CBitmap::LoadBitmap](#loadbitmap)|Initialise l’objet par le chargement d’une ressource bitmap nommée à partir du fichier exécutable de l’application et l’attachement de la bitmap à l’objet.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Charge une bitmap et mappe les couleurs aux couleurs système en cours.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Initialise l’objet en chargeant un bitmap Windows prédéfini et en attachant la bitmap à l’objet.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Définit les bits d’une image bitmap pour les valeurs de bits spécifié.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Assigne une largeur et la hauteur à une image bitmap en unités de millimètre de 0,1.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Retourne le handle Windows associé à la `CBitmap` objet.|

## <a name="remarks"></a>Notes

Pour utiliser un `CBitmap` de l’objet, construire l’objet, attacher un handle de bitmap à l’aide d’une des fonctions de membre de l’initialisation et ensuite, appelez les fonctions membres de l’objet.

Pour plus d’informations sur l’utilisation des objets graphiques tels que `CBitmap`, consultez [les objets de graphique](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cbitmap"></a>  CBitmap::CBitmap

Construit un objet `CBitmap`.

```
CBitmap();
```

### <a name="remarks"></a>Notes

L’objet résultant doit être initialisée avec une des fonctions de membre de l’initialisation.

##  <a name="createbitmap"></a>  CBitmap::CreateBitmap

Initialise une image bitmap de mémoire dépendante de l’appareil avec la largeur, la hauteur et le modèle binaire spécifiés.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
Spécifie la largeur (en pixels) de l’image bitmap.

*nHeight*<br/>
Spécifie la hauteur (en pixels) de l’image bitmap.

*nPlanes*<br/>
Spécifie le nombre de plans de couleur de l’image bitmap.

*nBitcount*<br/>
Spécifie le nombre de bits de couleur par pixel d’affichage.

*lpBits*<br/>
Pointe vers un tableau d’octets qui contient les valeurs de bit de l’image bitmap initiale. Si sa valeur est NULL, la nouvelle bitmap reste non initialisé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Pour une image bitmap de couleur, soit le *nPlanes* ou *nBitcount* paramètre doit être défini sur 1. Si ces deux paramètres sont définis avec la valeur 1, `CreateBitmap` crée une image bitmap monochrome.

Bien qu’une image bitmap ne peut pas être directement sélectionnée pour un périphérique d’affichage, il peut être sélectionné en tant qu’image bitmap active pour un « contexte de périphérique de mémoire » à l’aide de [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) et copiée dans un contexte de périphérique compatible à l’aide de la [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) (fonction).

Quand vous en avez terminé avec l’objet `CBitmap` créé par la fonction `CreateBitmap` , commencez par sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez l’objet `CBitmap` .

Pour plus d’informations, consultez la description de la `bmBits` champ dans le `BITMAP` structure. Le [BITMAP](../../mfc/reference/bitmap-structure.md) structure est décrite sous la [CBitmap::CreateBitmapIndirect](#createbitmapindirect) fonction membre.

##  <a name="createbitmapindirect"></a>  CBitmap::CreateBitmapIndirect

Initialise une image bitmap de la largeur, hauteur et un modèle de bits (le cas échéant) figurant à la structure vers laquelle pointe *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Paramètres

*lpBitmap*<br/>
Pointe vers un [BITMAP](../../mfc/reference/bitmap-structure.md) structure qui contient des informations sur l’image bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Bien qu’une image bitmap ne peut pas être directement sélectionnée pour un périphérique d’affichage, il peut être sélectionné en tant qu’image bitmap active pour un contexte de périphérique de mémoire à l’aide de [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) et copiée dans un contexte de périphérique compatible à l’aide de la [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) ou [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) (fonction). (Le [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) fonction pouvez copier l’image bitmap pour le pinceau actuel directement dans le contexte de périphérique d’affichage.)

Si le `BITMAP` structure vers laquelle pointe le *lpBitmap* paramètre a été rempli à l’aide de la `GetObject` (fonction), les bits de l’image bitmap ne sont pas spécifiés, et l’image bitmap n’est pas initialisée. Pour initialiser la bitmap, une application peut utiliser une fonction comme [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) ou [SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits) pour copier les bits du bitmap identifié par le premier paramètre de `CGdiObject::GetObject` à l’image bitmap créé par `CreateBitmapIndirect`.

Lorsque vous avez terminé avec le `CBitmap` objet créé avec `CreateBitmapIndirect` fonctionner, tout d’abord sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez le `CBitmap` objet.

##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap

Initialise une bitmap qui est compatible avec l’appareil spécifié par *pDC*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Spécifie le contexte de périphérique.

*nWidth*<br/>
Spécifie la largeur (en pixels) de l’image bitmap.

*nHeight*<br/>
Spécifie la hauteur (en pixels) de l’image bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap possède le même nombre de plans de couleur ou le même format de bits par pixel que le contexte de périphérique spécifié. Il peut être sélectionné en tant qu’image bitmap active pour n’importe quel dispositif de mémoire qui est compatible avec celui spécifié par *pDC*.

Si *pDC* est un contexte de périphérique de mémoire, la bitmap retournée a le même format que la bitmap actuellement sélectionné dans ce contexte de périphérique. Un « contexte de périphérique de mémoire » est un bloc de mémoire qui représente une surface d’affichage. Il peut être utilisé pour préparer des images en mémoire avant de les copier vers la surface d’affichage réel de l’appareil compatible.

Lorsqu’un contexte de périphérique de mémoire est créé, GDI sélectionne automatiquement un bitmap monochrome stock pour celui-ci.

Dans la mesure où un contexte de périphérique de mémoire de couleur peut avoir une couleur ou les images bitmap monochromes sélectionnés, le format de l’image bitmap retourné par la `CreateCompatibleBitmap` fonction n’est pas toujours les mêmes ; Toutefois, le format d’une bitmap compatible pour un contexte de périphérique sans mémoire est toujours dans le format de l’appareil.

Lorsque vous avez terminé avec le `CBitmap` objet créé avec le `CreateCompatibleBitmap` fonctionner, tout d’abord sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez le `CBitmap` objet.

##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap

Initialise une image bitmap pouvant être éliminée qui est compatible avec le contexte de périphérique identifié par *pDC*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Spécifie un contexte de périphérique.

*nWidth*<br/>
Spécifie la largeur (en bits) de l’image bitmap.

*nHeight*<br/>
Spécifie la hauteur (en bits) de l’image bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap possède le même nombre de plans de couleur ou le même format de bits par pixel que le contexte de périphérique spécifié. Une application peut sélectionner cette image bitmap en tant qu’image bitmap active pour un dispositif de mémoire qui est compatible avec celui spécifié par *pDC*.

Windows peut abandonner une image créée par cette fonction uniquement si une application ne le n'a pas sélectionné dans un contexte d’affichage. Si Windows ignore la bitmap lorsqu’il n’est pas sélectionnée et ultérieurement l’application tente de le sélectionner, le [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) fonction retournera NULL.

Lorsque vous avez terminé avec le `CBitmap` objet créé avec le `CreateDiscardableBitmap` fonctionner, tout d’abord sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez le `CBitmap` objet.

##  <a name="fromhandle"></a>  CBitmap::FromHandle

Retourne un pointeur vers un `CBitmap` lorsqu’un handle vers une bitmap GDI de Windows de l’objet.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap*<br/>
Spécifie une bitmap GDI de Windows.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CBitmap` objet en cas de réussite ; sinon, NULL.

### <a name="remarks"></a>Notes

Si un `CBitmap` objet n’est pas déjà attaché au handle, une table temporaire `CBitmap` objet est créé et attaché. Ce fichier temporaire `CBitmap` objet est valide uniquement jusqu'à ce que la prochaine fois que l’application possède les temps d’inactivité dans sa boucle de l’événement, alors graphique temporaire de tous les objets sont supprimés. Une autre façon de dire cela est que l’objet temporaire est valide uniquement pendant le traitement du message d’une fenêtre.

##  <a name="getbitmap"></a>  CBitmap::GetBitmap

Récupère les propriétés de l’image pour l’image bitmap attaché.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Paramètres

*pBitMap*<br/>
Pointeur vers un [Structure BITMAP](../../mfc/reference/bitmap-structure.md) structure qui recevra les propriétés de l’image. Ce paramètre ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode a réussi ; sinon 0.

### <a name="remarks"></a>Notes

##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits

Copie le modèle binaire de l’image bitmap jointe dans la mémoire tampon spécifiée.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Paramètres

*dwCount*<br/>
Nombre d’octets à copier dans la mémoire tampon.

*lpBits*<br/>
Pointeur vers la mémoire tampon qui recevra la bitmap.

### <a name="return-value"></a>Valeur de retour

Le nombre d’octets copiés vers la mémoire tampon si la méthode a réussi ; sinon 0.

### <a name="remarks"></a>Notes

Utilisez [CBitmap::GetBitmap](#getbitmap) pour déterminer la taille de mémoire tampon requise.

##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension

Retourne la largeur et la hauteur de la bitmap.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur et la hauteur de l’image bitmap, mesurée en unités de millimètre de 0,1. La hauteur est dans le `cy` membre de la `CSize` objet et la largeur est dans le `cx` membre. Si la hauteur et la largeur de la bitmap n’ont pas été définies à l’aide de `SetBitmapDimension`, la valeur de retour est 0.

### <a name="remarks"></a>Notes

La hauteur et largeur sont supposées avoir été défini précédemment à l’aide de la [SetBitmapDimension](#setbitmapdimension) fonction membre.

##  <a name="loadbitmap"></a>  CBitmap::LoadBitmap

Charge la ressource bitmap nommée par *lpszResourceName* ou identifiée par le numéro d’ID dans *nIDResource* à partir du fichier exécutable de l’application.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName*<br/>
Pointe vers une chaîne se terminant par null qui contient le nom de la ressource bitmap.

*nIDResource*<br/>
Spécifie le numéro d’ID de ressource de la ressource bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap chargée est attachée à la `CBitmap` objet.

Si la bitmap est identifié par *lpszResourceName* n’existe pas ou si la mémoire est insuffisante pour charger l’image bitmap, la fonction retourne 0.

Vous pouvez utiliser la [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) fonction pour supprimer la bitmap est chargée par le `LoadBitmap` (fonction), ou le `CBitmap` destructeur supprimera l’objet pour vous.

> [!CAUTION]
>  Avant de supprimer l’objet, assurez-vous qu’il n’est pas sélectionnée dans un contexte de périphérique.

Les bitmaps suivantes ont été ajoutées aux versions de Windows 3.1 et version ultérieures :

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Ces bitmaps sont introuvables dans les pilotes de périphérique pour les versions de Windows 3.0 et versions antérieures. Pour obtenir une liste complète des bitmaps et un affichage de leur apparence, consultez le Kit de développement Windows.

##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap

Appelez cette fonction membre pour charger une image bitmap et de mapper les couleurs pour les couleurs système en cours.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Paramètres

*nIDBitmap*<br/>
L’ID de la ressource bitmap.

*nIndicateurs*<br/>
Un indicateur pour une image bitmap. Peut être zéro ou CMB_MASKED.

*lpColorMap*<br/>
Un pointeur vers un `COLORMAP` structure qui contient les informations de couleur nécessaires pour mapper les bitmaps. Si ce paramètre est NULL, la fonction utilise le mappage de couleur par défaut.

*nMapSize*<br/>
Le nombre de couleur est mappé vers lequel pointe *lpColorMap*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Par défaut, `LoadMappedBitmap` mappera les couleurs utilisées dans les glyphes de bouton.

Pour plus d’informations sur la création d’une image bitmap mappée, consultez la fonction Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562) et [COLORMAP](/windows/desktop/api/commctrl/ns-commctrl-_colormap) structure dans le SDK Windows.

##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap

Charge une bitmap prédéfinie utilisée par Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Paramètres

*nIDBitmap*<br/>
Numéro d’identification de la bitmap Windows prédéfinie. Les valeurs possibles sont répertoriées ci-dessous à partir de WINDOWS. H :

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les noms de bitmap qui commencent par OBM_OLD représentent les bitmaps utilisées par les versions de Windows antérieures à 3.0.

Notez que la constante OEMRESOURCE doit être défini avant d’inclure WINDOWS. H pour pouvoir utiliser le **OBM_** constantes.

##  <a name="operator_hbitmap"></a>  CBitmap::operator HBITMAP

Utilisez cet opérateur pour obtenir le handle Windows GDI attaché de la `CBitmap` objet.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Valeur de retour

Si réussie, un handle vers l’objet de Windows GDI représenté par le `CBitmap` de l’objet ; sinon, NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast, qui prend en charge l’utilisation directe d’un `HBITMAP` objet.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez [graphique objets](/windows/desktop/gdi/graphic-objects) dans le SDK Windows.

##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits

Définit les bits d’une image bitmap pour les valeurs de bits donnés par *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Paramètres

*dwCount*<br/>
Spécifie le nombre d’octets vers laquelle pointé *lpBits*.

*lpBits*<br/>
Pointe vers le tableau d’octets qui contient les valeurs de pixel à copier vers le `CBitmap` objet. Afin que la bitmap à être en mesure d’afficher l’image correctement, les valeurs doivent être mis en forme pour être conforme aux hauteur, largeur et la couleur profondeur les valeurs qui ont été spécifiés lors de la création de l’instance CBitmap. Pour plus d’informations, consultez [CBitmap::CreateBitmap](#createbitmap).

### <a name="return-value"></a>Valeur de retour

Le nombre d’octets utilisés lors de la définition des bits de la bitmap ; 0 si la fonction échoue.

##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension

Assigne une largeur et la hauteur à une image bitmap en unités de millimètre de 0,1.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
Spécifie la largeur de l’image bitmap (en unités de 0,1-millimètre).

*nHeight*<br/>
Spécifie la hauteur de l’image bitmap (en unités de 0,1-millimètre).

### <a name="return-value"></a>Valeur de retour

Les dimensions de bitmap précédente. Hauteur est dans le `cy` variable membre de la `CSize` objet et la largeur est dans le `cx` variable membre.

### <a name="remarks"></a>Notes

L’interface GDI n’utilise pas ces valeurs, à l’exception to les retourner lorsqu’une application appelle la [GetBitmapDimension](#getbitmapdimension) fonction membre.

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDI](../../visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

