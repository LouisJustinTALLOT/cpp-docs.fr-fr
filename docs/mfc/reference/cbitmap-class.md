---
title: CBitmap, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 7161a4cf4484b6cc9e76e6955de558ca6e9121ca
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507452"
---
# <a name="cbitmap-class"></a>CBitmap, classe

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
|[CBitmap::CreateBitmap](#createbitmap)|Initialise l’objet avec une bitmap de mémoire dépendante de l’appareil qui a une largeur, une hauteur et un modèle binaire spécifiés.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Initialise l’objet avec une bitmap avec la largeur, la hauteur et le modèle binaire (le cas échéant) spécifiés dans une `BITMAP` structure.|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Initialise l’objet avec une bitmap afin qu’il soit compatible avec un périphérique spécifié.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Initialise l’objet avec une image bitmap pouvant être ignorée qui est compatible avec un périphérique spécifié.|
|[CBitmap::FromHandle](#fromhandle)|Retourne un pointeur vers un `CBitmap` objet lorsqu’un handle est fourni à une `HBITMAP` image bitmap Windows.|
|[CBitmap::GetBitmap](#getbitmap)|Remplit une `BITMAP` structure avec des informations sur l’image bitmap.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Copie les bits de l’image bitmap spécifiée dans la mémoire tampon spécifiée.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Retourne la largeur et la hauteur de la bitmap. La hauteur et la largeur sont supposées avoir été définies précédemment par la fonction membre [SetBitmapDimension](#setbitmapdimension) .|
|[CBitmap::LoadBitmap](#loadbitmap)|Initialise l’objet en chargeant une ressource bitmap nommée à partir du fichier exécutable de l’application et en attachant l’image bitmap à l’objet.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Charge une bitmap et mappe les couleurs aux couleurs système actuelles.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Initialise l’objet en chargeant une image bitmap Windows prédéfinie et en attachant l’image bitmap à l’objet.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Affecte les valeurs de bits spécifiées aux bits d’une image bitmap.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Affecte une largeur et une hauteur à une image bitmap en unités de 0,1 mm.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmap:: Operator HBITMAP](#operator_hbitmap)|Retourne le handle Windows attaché à l' `CBitmap` objet.|

## <a name="remarks"></a>Notes

Pour utiliser un `CBitmap` objet, construisez l’objet, attachez-lui un handle de bitmap avec l’une des fonctions membres d’initialisation, puis appelez les fonctions membres de l’objet.

Pour plus d’informations sur l’utilisation d' `CBitmap`objets graphiques comme, consultez [objets graphiques](../../mfc/graphic-objects.md).

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

L’objet obtenu doit être initialisé avec l’une des fonctions membres d’initialisation.

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
Pointe vers un tableau d’octets qui contient les valeurs de bit de l’image bitmap initiale. Si la valeur est NULL, la nouvelle bitmap reste non initialisée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Pour une image bitmap de couleur, le paramètre *nPlanes* ou *nBitcount* doit être défini sur 1. Si ces deux paramètres sont définis avec la valeur 1, `CreateBitmap` crée une image bitmap monochrome.

Même si une image bitmap ne peut pas être directement sélectionnée pour un périphérique d’affichage, elle peut être sélectionnée en tant qu’image bitmap active pour un « contexte de périphérique de mémoire » à l’aide de [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) et copiée dans un contexte de périphérique compatible à l’aide de la fonction [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) .

Quand vous en avez terminé avec l’objet `CBitmap` créé par la fonction `CreateBitmap` , commencez par sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez l’objet `CBitmap` .

Pour plus d’informations, consultez la description du `bmBits` champ dans la `BITMAP` structure. La structure [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) est décrite sous la fonction membre [CBitmap::CreateBitmapIndirect](#createbitmapindirect) .

##  <a name="createbitmapindirect"></a>  CBitmap::CreateBitmapIndirect

Initialise une bitmap qui a la largeur, la hauteur et le modèle binaire (le cas échéant) spécifiés dans la structure vers laquelle pointe *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Paramètres

*lpBitmap*<br/>
Pointe vers une structure [bitmap](/windows/win32/api/wingdi/ns-wingdi-bitmap) qui contient des informations sur l’image bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Même si une image bitmap ne peut pas être sélectionnée directement pour un périphérique d’affichage, elle peut être sélectionnée en tant que bitmap actuelle pour un contexte de périphérique de mémoire à l’aide de [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) et copiée dans n’importe quel contexte de périphérique compatible à l’aide de la fonction [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) ou [CDC:: Fonction StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) . (La fonction [CDC::P atblt](../../mfc/reference/cdc-class.md#patblt) peut copier l’image bitmap du pinceau actuel directement dans le contexte de périphérique d’affichage.)

Si la `BITMAP` structure vers laquelle pointe le paramètre *lpBitmap* a été remplie à l’aide de `GetObject` la fonction, les bits de l’image bitmap ne sont pas spécifiés et l’image bitmap n’est pas initialisée. Pour initialiser la bitmap, une application peut utiliser une fonction telle que [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) ou [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) pour copier les bits de la bitmap identifiée par le premier paramètre `CGdiObject::GetObject` de à l’image bitmap `CreateBitmapIndirect`créée par.

Lorsque vous avez terminé avec `CBitmap` l’objet créé `CreateBitmapIndirect` avec la fonction, commencez par sélectionner l’image bitmap hors du contexte de périphérique `CBitmap` , puis supprimez l’objet.

##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap

Initialise une bitmap qui est compatible avec l’appareil spécifié par le *contrôleur de domaine principal*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Spécifie le contexte de périphérique.

*nWidth*<br/>
Spécifie la largeur (en pixels) de l’image bitmap.

*nHeight*<br/>
Spécifie la hauteur (en pixels) de l’image bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap a le même nombre de plans de couleur ou le même format de bits par pixel que le contexte de périphérique spécifié. Il peut être sélectionné en tant que bitmap actuelle pour tout périphérique de mémoire compatible avec celui spécifié par le *contrôleur de domaine principal*.

Si le *contrôleur de domaine principal* est un contexte de périphérique de mémoire, le bitmap retourné a le même format que l’image bitmap actuellement sélectionnée dans ce contexte de périphérique. Un «contexte de périphérique de mémoire» est un bloc de mémoire qui représente une surface d’affichage. Il peut être utilisé pour préparer des images en mémoire avant de les copier sur la surface d’affichage réelle du périphérique compatible.

Lorsqu’un contexte de périphérique de mémoire est créé, GDI sélectionne automatiquement un bitmap de stock monochrome pour celui-ci.

Étant donné qu’un contexte de périphérique de mémoire de couleur peut avoir des bitmaps couleur ou monochrome sélectionnées, le format de `CreateCompatibleBitmap` l’image bitmap retournée par la fonction n’est pas toujours le même; Toutefois, le format d’une bitmap compatible pour un contexte de périphérique non-mémoire est toujours dans la format de l’appareil.

Lorsque vous avez terminé avec `CBitmap` l’objet créé à `CreateCompatibleBitmap` l’aide de la fonction, commencez par sélectionner l’image bitmap hors du contexte `CBitmap` de périphérique, puis supprimez l’objet.

##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap

Initialise une image bitmap pouvant être ignorée qui est compatible avec le contexte de périphérique identifié par le *contrôleur de domaine principal*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Spécifie un contexte de périphérique.

*nWidth*<br/>
Spécifie la largeur (en bits) de l’image bitmap.

*nHeight*<br/>
Spécifie la hauteur (en bits) de la bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap a le même nombre de plans de couleur ou le même format de bits par pixel que le contexte de périphérique spécifié. Une application peut sélectionner cette image bitmap en tant que bitmap actuelle pour un périphérique de mémoire qui est compatible avec celui spécifié par le *contrôleur de domaine principal*.

Windows peut ignorer une image bitmap créée par cette fonction uniquement si une application ne l’a pas sélectionnée dans un contexte d’affichage. Si Windows ignore le bitmap lorsqu’il n’est pas sélectionné et que l’application tente ultérieurement de la sélectionner, la fonction [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) retourne la valeur null.

Lorsque vous avez terminé avec `CBitmap` l’objet créé à `CreateDiscardableBitmap` l’aide de la fonction, commencez par sélectionner l’image bitmap hors du contexte `CBitmap` de périphérique, puis supprimez l’objet.

##  <a name="fromhandle"></a>  CBitmap::FromHandle

Retourne un pointeur vers un `CBitmap` objet en fonction d’un handle vers une image bitmap Windows GDI.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap*<br/>
Spécifie une image bitmap Windows GDI.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CBitmap` objet en cas de réussite; sinon, null.

### <a name="remarks"></a>Notes

Si un `CBitmap` objet n’est pas déjà attaché au descripteur, `CBitmap` un objet temporaire est créé et attaché. Cet objet `CBitmap` temporaire est valide uniquement jusqu’à la prochaine période d’inactivité de l’application dans sa boucle d’événements, auquel cas tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire n’est valide que pendant le traitement d’un message de fenêtre.

##  <a name="getbitmap"></a>  CBitmap::GetBitmap

Récupère les propriétés de l’image de la bitmap attachée.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Paramètres

*pBitMap*<br/>
Pointeur vers une structure [bitmap](/windows/win32/api/wingdi/ns-wingdi-bitmap) qui recevra les propriétés de l’image. Ce paramètre ne doit pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode a réussi; Sinon, 0.

### <a name="remarks"></a>Notes

##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits

Copie le modèle binaire de l’image bitmap attachée dans la mémoire tampon spécifiée.

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

Nombre d’octets copiés dans la mémoire tampon si la méthode a réussi; Sinon, 0.

### <a name="remarks"></a>Notes

Utilisez [CBitmap:: GetBitmap](#getbitmap) pour déterminer la taille de mémoire tampon requise.

##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension

Retourne la largeur et la hauteur de la bitmap.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur et la hauteur de la bitmap, mesurées en unités de 0,1 mm. La hauteur est dans le `cy` membre de l' `CSize` objet et la largeur est dans le `cx` membre. Si la largeur et la hauteur de la bitmap n’ont pas `SetBitmapDimension`été définies à l’aide de, la valeur de retour est 0.

### <a name="remarks"></a>Notes

La hauteur et la largeur sont supposées avoir été définies précédemment à l’aide de la fonction membre [SetBitmapDimension](#setbitmapdimension) .

##  <a name="loadbitmap"></a>  CBitmap::LoadBitmap

Charge la ressource bitmap nommée par *lpszResourceName* ou identifiée par le numéro d’ID dans *nIDResource* à partir du fichier exécutable de l’application.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName*<br/>
Pointe vers une chaîne se terminant par un caractère null qui contient le nom de la ressource bitmap.

*nIDResource*<br/>
Spécifie le numéro d’ID de ressource de la ressource bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap chargée est attachée à `CBitmap` l’objet.

Si la bitmap identifiée par *lpszResourceName* n’existe pas ou si la mémoire est insuffisante pour charger l’image bitmap, la fonction retourne 0.

Vous pouvez utiliser la fonction [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour supprimer la bitmap chargée par `LoadBitmap` la fonction, ou `CBitmap` le destructeur supprimera l’objet pour vous.

> [!CAUTION]
>  Avant de supprimer l’objet, assurez-vous qu’il n’est pas sélectionné dans un contexte de périphérique.

Les bitmaps suivantes ont été ajoutées aux versions 3,1 et ultérieures de Windows:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Ces bitmaps sont introuvables dans les pilotes de périphérique pour Windows versions 3,0 et antérieures. Pour obtenir la liste complète des bitmaps et un affichage de leur apparence, consultez la SDK Windows.

##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap

Appelez cette fonction membre pour charger une image bitmap et mapper les couleurs aux couleurs système actuelles.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Paramètres

*nIDBitmap*<br/>
ID de la ressource bitmap.

*nFlags*<br/>
Indicateur pour une image bitmap. Peut être égal à zéro ou CMB_MASKED.

*lpColorMap*<br/>
Pointeur vers une `COLORMAP` structure qui contient les informations de couleur nécessaires pour mapper les bitmaps. Si ce paramètre a la valeur NULL, la fonction utilise la carte de couleur par défaut.

*nMapSize*<br/>
Nombre de cartes de couleur vers lesquelles pointe *lpColorMap*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Par défaut, `LoadMappedBitmap` mappe les couleurs couramment utilisées dans les glyphes de bouton.

Pour plus d’informations sur la création d’une bitmap mappée, consultez la fonction Windows [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) et la structure [COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap) dans le SDK Windows.

##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap

Charge une bitmap prédéfinie utilisée par Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Paramètres

*nIDBitmap*<br/>
Numéro d’identification de la bitmap Windows prédéfinie. Les valeurs possibles sont répertoriées ci-dessous à partir de WINDOWS. Manutention

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

Les noms de bitmap qui commencent par OBM_OLD représentent les bitmaps utilisés par les versions de Windows antérieures à 3,0.

Notez que la constante OEMRESOURCE doit être définie avant les fenêtres incluses. H pour pouvoir utiliser l’une des constantes **OBM_** .

##  <a name="operator_hbitmap"></a>CBitmap:: Operator HBITMAP

Utilisez cet opérateur pour récupérer le handle Windows GDI attaché de l' `CBitmap` objet.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle vers l’objet Windows GDI représenté par `CBitmap` l’objet; sinon, null.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast qui prend en charge l’utilisation `HBITMAP` directe d’un objet.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez [objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits

Définit les bits d’une image bitmap sur les valeurs de bits données par *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Paramètres

*dwCount*<br/>
Spécifie le nombre d’octets pointés par *lpBits*.

*lpBits*<br/>
Pointe vers le tableau d’octets qui contient les valeurs en pixels à copier dans `CBitmap` l’objet. Pour que l’image bitmap puisse restituer correctement son image, les valeurs doivent être mises en forme pour se conformer aux valeurs de hauteur, de largeur et de profondeur de couleur qui ont été spécifiées lors de la création de l’instance CBitmap. Pour plus d’informations, consultez [CBitmap:: CreateBitmap](#createbitmap).

### <a name="return-value"></a>Valeur de retour

Nombre d’octets utilisés pour la définition des bits de la bitmap; 0 si la fonction échoue.

##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension

Affecte une largeur et une hauteur à une image bitmap en unités de 0,1 mm.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
Spécifie la largeur de l’image bitmap (en unités de 0,1 mm).

*nHeight*<br/>
Spécifie la hauteur de la bitmap (en unités de 0,1 mm).

### <a name="return-value"></a>Valeur de retour

Dimensions précédentes de la bitmap. Height est dans la `cy` variable membre de l' `CSize` objet et Width est dans la `cx` variable de membre.

### <a name="remarks"></a>Notes

Le GDI n’utilise pas ces valeurs, sauf pour les retourner lorsqu’une application appelle la fonction membre [GetBitmapDimension](#getbitmapdimension) .

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
