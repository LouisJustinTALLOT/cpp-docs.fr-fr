---
title: Classe CBitmap
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
ms.openlocfilehash: 9a33a6e1bea601422e043d7f2a80029c72d97e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352741"
---
# <a name="cbitmap-class"></a>Classe CBitmap

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
|[CBitmap::CreateBitmap](#createbitmap)|Initialise l’objet avec un bitmap de mémoire dépendant de l’appareil qui a une largeur spécifiée, hauteur et modèle de bit.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Initialise l’objet avec une bitmap avec la largeur, la hauteur et `BITMAP` le motif de bit (si l’on est spécifié) donné dans une structure.|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Initialise l’objet avec un bitmap de sorte qu’il est compatible avec un appareil spécifié.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Initialise l’objet avec un bitmap jetable compatible avec un appareil spécifié.|
|[CBitmap::DeHandle](#fromhandle)|Retourne un pointeur à un `CBitmap` objet `HBITMAP` lorsqu’on lui donne une poignée à un bitmap Windows.|
|[CBitmap::GetBitmap](#getbitmap)|Remplit une `BITMAP` structure d’informations sur la bitmap.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Copie les bits de la bitmap spécifiée dans le tampon spécifié.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Retourne la largeur et la hauteur de la bitmap. La hauteur et la largeur sont supposées avoir été réglées précédemment par la fonction membre [SetBitmapDimension.](#setbitmapdimension)|
|[CBitmap::LoadBitmap](#loadbitmap)|Initialise l’objet en chargeant une ressource de bitmap nommée à partir du fichier exécutable de l’application et en attachant la bitmap à l’objet.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Charge une bitmap et cartographie les couleurs aux couleurs actuelles du système.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Initialise l’objet en chargeant une bitmap Windows prédéfinie et en attachant le bitmap à l’objet.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Définit les bits d’un bitmap aux valeurs de bit spécifiées.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Attribue une largeur et une hauteur à une bitmap en unités de 0,1 millimètre.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmap::opérateur HBITMAP](#operator_hbitmap)|Retourne la poignée Windows `CBitmap` attachée à l’objet.|

## <a name="remarks"></a>Notes

Pour utiliser `CBitmap` un objet, construisez l’objet, attachez-lui une poignée de bitmap avec l’une des fonctions du membre de l’initialisation, puis appelez les fonctions du membre de l’objet.

Pour plus d’informations `CBitmap`sur l’utilisation d’objets graphiques comme , voir [Objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a>CBitmap::CBitmap

Construit un objet `CBitmap`.

```
CBitmap();
```

### <a name="remarks"></a>Notes

L’objet résultant doit être paradé avec l’une des fonctions des membres de l’initialisation.

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a>CBitmap::CreateBitmap

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

*nWidth (en)*<br/>
Spécifie la largeur (en pixels) de l’image bitmap.

*nHeight (en)*<br/>
Spécifie la hauteur (en pixels) de l’image bitmap.

*nPlanes (en)*<br/>
Spécifie le nombre de plans de couleur de l’image bitmap.

*nBitcount (en)*<br/>
Spécifie le nombre de bits de couleur par pixel d’affichage.

*lpBits*<br/>
Pointe vers un tableau d’octets qui contient les valeurs de bit de l’image bitmap initiale. Si elle a la valeur NULL, la nouvelle image bitmap n’est pas initialisée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Pour un bitmap couleur, soit les *nPlanes* ou *nBitcount* paramètre doit être réglé à 1. Si ces deux paramètres sont définis avec la valeur 1, `CreateBitmap` crée une image bitmap monochrome.

Même si une image bitmap ne peut pas être directement sélectionnée pour un périphérique d’affichage, elle peut être sélectionnée en tant qu’image bitmap active pour un « contexte de périphérique de mémoire » à l’aide de [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) et copiée dans un contexte de périphérique compatible à l’aide de la fonction [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) .

Quand vous en avez terminé avec l’objet `CBitmap` créé par la fonction `CreateBitmap` , commencez par sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez l’objet `CBitmap` .

Pour plus d’informations, `bmBits` voir la `BITMAP` description du champ dans la structure. La structure [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) est décrite sous la fonction membre [CBitmap::CreateBitmapIndirect](#createbitmapindirect) .

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect

Initialise une bitmap qui a la largeur, la hauteur, et le modèle de bit (si l’on est spécifié) donné dans la structure indiquée par *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Paramètres

*lpBitmap*<br/>
Indique une structure [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) qui contient des informations sur la bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Bien qu’un bitmap ne puisse pas être directement sélectionné pour un appareil d’affichage, il peut être sélectionné comme bitmap actuel pour un contexte de dispositif de mémoire en utilisant [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) et copié à n’importe quel contexte d’appareil compatible en utilisant le [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) ou [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) fonction. (La fonction [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) peut copier la bitmap pour le pinceau actuel directement au contexte de l’appareil d’affichage.)

Si `BITMAP` la structure indiquée par le paramètre *lpBitmap* a été remplie en utilisant la `GetObject` fonction, les bits de la bitmap ne sont pas spécifiés et la bitmap est uninitialisée. Pour initialiser la bitmap, une application peut utiliser une fonction telle que [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) ou [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) pour `CGdiObject::GetObject` copier les bits `CreateBitmapIndirect`de la bitmap identifiée par le premier paramètre de la bitmap créé par .

Lorsque vous terminez avec l’objet `CBitmap` créé avec `CreateBitmapIndirect` la fonction, sélectionnez `CBitmap` d’abord la bitmap hors du contexte de l’appareil, puis supprimez l’objet.

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap

Initialise un bitmap qui est compatible avec l’appareil spécifié par *pDC*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Spécifie le contexte de l’appareil.

*nWidth (en)*<br/>
Spécifie la largeur (en pixels) de l’image bitmap.

*nHeight (en)*<br/>
Spécifie la hauteur (en pixels) de l’image bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap a le même nombre d’avions de couleur ou le même format bits par pixel que le contexte de l’appareil spécifié. Il peut être sélectionné comme le bitmap actuel pour tout appareil mémoire qui est compatible avec celui spécifié par *pDC*.

Si *pDC* est un contexte de dispositif de mémoire, le bitmap retourné a le même format que le bitmap actuellement sélectionné dans ce contexte de dispositif. Un « contexte de dispositif de mémoire » est un bloc de mémoire qui représente une surface d’affichage. Il peut être utilisé pour préparer des images en mémoire avant de les copier sur la surface d’affichage réelle de l’appareil compatible.

Lorsqu’un contexte de dispositif de mémoire est créé, GDI sélectionne automatiquement un bitmap de stock monochrome pour elle.

Étant donné qu’un contexte de dispositif de mémoire de couleur peut avoir des bitmaps de couleur ou monochrome sélectionnés, le format de la bitmap retourné par la `CreateCompatibleBitmap` fonction n’est pas toujours le même ; cependant, le format d’un bitmap compatible pour un contexte d’appareil non-mémoire est toujours dans le format de l’appareil.

Lorsque vous terminez avec `CBitmap` `CreateCompatibleBitmap` l’objet créé avec la fonction, sélectionnez d’abord la bitmap hors du contexte de l’appareil, puis supprimez l’objet. `CBitmap`

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap

Initialise une bitmap jetable qui est compatible avec le contexte de l’appareil identifié par *pDC*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Spécifie un contexte d’appareil.

*nWidth (en)*<br/>
Spécifie la largeur (en bits) de la bitmap.

*nHeight (en)*<br/>
Spécifie la hauteur (en morceaux) de la bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap a le même nombre d’avions de couleur ou le même format bits par pixel que le contexte de l’appareil spécifié. Une application peut sélectionner ce bitmap comme le bitmap actuel pour un dispositif de mémoire qui est compatible avec celui spécifié par *pDC*.

Windows ne peut jeter une bitmap créée par cette fonction que si une application ne l’a pas sélectionnée dans un contexte d’affichage. Si Windows rejette la bitmap lorsqu’elle n’est pas sélectionnée et que l’application tente plus tard de la sélectionner, la fonction [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) retournera NULL.

Lorsque vous terminez avec `CBitmap` `CreateDiscardableBitmap` l’objet créé avec la fonction, sélectionnez d’abord la bitmap hors du contexte de l’appareil, puis supprimez l’objet. `CBitmap`

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a>CBitmap::DeHandle

Retourne un pointeur à un `CBitmap` objet lorsqu’on lui donne une poignée à un bitmap GDI Windows.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap (en)*<br/>
Spécifie une bitmap GDI Windows.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CBitmap` à un objet en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si `CBitmap` un objet n’est pas déjà `CBitmap` attaché à la poignée, un objet temporaire est créé et attaché. Cet `CBitmap` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, date à laquelle tous les objets graphiques temporaires sont supprimés. Une autre façon de dire cela est que l’objet temporaire n’est valable que pendant le traitement d’un message de fenêtre.

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a>CBitmap::GetBitmap

Récupère les propriétés d’image pour la bitmap attachée.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Paramètres

*pBitMap (en)*<br/>
Pointeur vers une structure [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) qui recevra les propriétés d’image. Ce paramètre ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a>CBitmap::GetBitmapBits

Copie le modèle de bit de la bitmap attachée dans le tampon spécifié.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Paramètres

*dwCompte*<br/>
Nombre d’octets à copier dans la mémoire tampon.

*lpBits*<br/>
Pointeur vers le tampon qui recevra la bitmap.

### <a name="return-value"></a>Valeur de retour

Le nombre d’octets copiés au tampon si la méthode était efficace; sinon 0.

### <a name="remarks"></a>Notes

Utilisez [CBitmap::GetBitmap](#getbitmap) pour déterminer la taille du tampon requis.

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension

Retourne la largeur et la hauteur de la bitmap.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur et la hauteur de la bitmap, mesurée en unités de 0,1 millimètre. La hauteur est `cy` dans `CSize` le membre de l’objet, et la largeur est dans le `cx` membre. Si la largeur et la hauteur de `SetBitmapDimension`la bitmap n’ont pas été définies en utilisant, la valeur de retour est de 0.

### <a name="remarks"></a>Notes

La hauteur et la largeur sont supposées avoir été réglées précédemment en utilisant la fonction [membre SetBitmapDimension.](#setbitmapdimension)

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a>CBitmap::LoadBitmap

Charge la ressource de bitmap nommée par *lpszResourceName* ou identifiée par le numéro d’identification dans *nIDResource* à partir du fichier exécutable de l’application.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName (en)*<br/>
Indique une chaîne non terminée qui contient le nom de la ressource de bitmap.

*nIDResource (en)*<br/>
Spécifie le numéro d’identification des ressources de la ressource de bitmap.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La bitmap chargée est `CBitmap` attachée à l’objet.

Si la bitmap identifiée par *lpszResourceName* n’existe pas ou s’il n’y a pas suffisamment de mémoire pour charger la bitmap, la fonction renvoie 0.

Vous pouvez utiliser la fonction [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) pour supprimer le `LoadBitmap` bitmap `CBitmap` chargé par la fonction, ou le destructeur supprimera l’objet pour vous.

> [!CAUTION]
> Avant de supprimer l’objet, assurez-vous qu’il n’est pas sélectionné dans un contexte d’appareil.

Les bitmaps suivants ont été ajoutés aux versions Windows 3.1 et plus tard :

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Ces bitmaps ne sont pas trouvés dans les pilotes d’appareils pour les versions Windows 3.0 et plus tôt. Pour une liste complète de bitmaps et un affichage de leur apparence, voir le Windows SDK.

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap

Appelez cette fonction de membre pour charger une bitmap et cartographier les couleurs aux couleurs actuelles du système.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Paramètres

*nIDBitmap (en)*<br/>
L’ID de la ressource de bitmap.

*nFlags*<br/>
Un drapeau pour un bitmap. Peut être nul ou CMB_MASKED.

*lpColorMap*<br/>
Un pointeur `COLORMAP` à une structure qui contient les informations de couleur nécessaires pour cartographier les bitmaps. Si ce paramètre est NULL, la fonction utilise la carte de couleur par défaut.

*nMapSize (en)*<br/>
Le nombre de cartes de couleur indiquées par *lpColorMap*.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Par défaut, `LoadMappedBitmap` la cartographie des couleurs couramment utilisées dans les glyphes de bouton.

Pour plus d’informations sur la création d’un bitmap cartographié, consultez la fonction Windows [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) et la structure [COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap) dans le SDK Windows.

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap

Charge un bitmap prédéfini utilisé par Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Paramètres

*nIDBitmap (en)*<br/>
Numéro d’identification du bitmap Windows prédéfini. Les valeurs possibles sont énumérées ci-dessous à partir de WINDOWS. H:

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

Les noms Bitmap qui commencent par OBM_OLD représentent des bitmaps utilisés par les versions Windows avant 3.0.

Notez que la constante OEMRESOURCE doit être définie avant d’inclure WINDOWS. H afin d’utiliser l’une des constantes **OBM_.**

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a>CBitmap::opérateur HBITMAP

Utilisez cet opérateur pour obtenir la poignée `CBitmap` Windows GDI attachée de l’objet.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, une poignée à `CBitmap` l’objet GDI Windows représenté par l’objet; autrement NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de coulée, qui prend en charge l’utilisation directe d’un `HBITMAP` objet.

Pour plus d’informations sur l’utilisation d’objets graphiques, voir [Objets graphiques](/windows/win32/gdi/graphic-objects) dans le SDK Windows.

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a>CBitmap::SetBitmapBits

Définit les bits d’un bitmap aux valeurs de bit donnés par *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Paramètres

*dwCompte*<br/>
Spécifie le nombre d’octets indiqués par *lpBits*.

*lpBits*<br/>
Points vers le tableau BYTE qui contient les `CBitmap` valeurs de pixels à copier à l’objet. Afin que la bitmap puisse rendre son image correctement, les valeurs doivent être formatées pour se conformer aux valeurs de hauteur, de largeur et de profondeur de couleur qui ont été spécifiées lors de la création de l’instance CBitmap. Pour plus d’informations, voir [CBitmap:CreateBitmap](#createbitmap).

### <a name="return-value"></a>Valeur de retour

Le nombre d’octets utilisés dans la configuration des bits de bitmap; 0 si la fonction échoue.

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension

Attribue une largeur et une hauteur à une bitmap en unités de 0,1 millimètre.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Paramètres

*nWidth (en)*<br/>
Specifie la largeur de la bitmap (en unités de 0,1 millimètre).

*nHeight (en)*<br/>
Specifie la hauteur de la bitmap (en unités de 0,1 millimètre).

### <a name="return-value"></a>Valeur de retour

Les dimensions bitmap précédentes. La hauteur `cy` est dans `CSize` la variable de membre `cx` de l’objet, et la largeur est dans la variable de membre.

### <a name="remarks"></a>Notes

Le GDI n’utilise pas ces valeurs sauf pour les retourner lorsqu’une application appelle la fonction membre [GetBitmapDimension.](#getbitmapdimension)

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
