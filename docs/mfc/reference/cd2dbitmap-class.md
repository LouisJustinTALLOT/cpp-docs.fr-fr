---
description: 'En savoir plus sur : classe Cd2dbitmap,'
title: CD2DBitmap, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
ms.openlocfilehash: ab023caa92683b24098db1a03d081922e3dfd48b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227648"
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap, classe

Wrapper pour ID2D1Bitmap.

## <a name="syntax"></a>Syntaxe

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dbitmap, :: Cd2dbitmap,](#cd2dbitmap)|Surchargé. Construit un objet Cd2dbitmap, à partir de HBITMAP.|
|[Cd2dbitmap, :: ~ Cd2dbitmap,](#_dtorcd2dbitmap)|Destructeur. Appelé lorsqu’un objet Bitmap D2D est en cours de destruction.|

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dbitmap, :: Cd2dbitmap,](#cd2dbitmap)|Surchargé. Construit un objet Cd2dbitmap,.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dbitmap, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dbitmap, :: CopyFromBitmap](#copyfrombitmap)|Copie la région spécifiée à partir de la bitmap spécifiée dans l’image bitmap actuelle|
|[Cd2dbitmap, :: CopyFromMemory](#copyfrommemory)|Copie la région spécifiée de la mémoire dans l’image bitmap actuelle|
|[Cd2dbitmap, :: CopyFromRenderTarget](#copyfromrendertarget)|Copie la région spécifiée de la cible de rendu spécifiée dans l’image bitmap actuelle|
|[Cd2dbitmap, :: Create](#create)|Crée un Cd2dbitmap,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dbitmap, ::D estroy](#destroy)|Détruit un objet Cd2dbitmap,. (Substitue [CD2DResource, ::D estroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[Cd2dbitmap, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dbitmap, :: obtient](#get)|Retourne l’interface ID2D1Bitmap|
|[Cd2dbitmap, :: GetDPI](#getdpi)|Retourner les points par pouce (DPI) de la bitmap|
|[Cd2dbitmap, :: GetPixelFormat](#getpixelformat)|Récupère le format de pixel et le mode Alpha de la bitmap.|
|[Cd2dbitmap, :: GetPixelSize](#getpixelsize)|Retourne la taille, en unités dépendantes du périphérique (pixels), de la bitmap|
|[Cd2dbitmap, :: est à obtenir](#getsize)|Retourne la taille, en pixels indépendants du périphérique (DIP), de l’image bitmap.|
|[Cd2dbitmap, :: IsValid](#isvalid)|Vérifie la validité des ressources (Substitue [CD2DResource, :: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[Cd2dbitmap, :: CommonInit](#commoninit)|Initialise l’objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dbitmap, :: Operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|Retourne l’interface ID2D1Bitmap|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dbitmap, :: m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|TRUE si m_hBmpSrc doit être détruite ; Sinon, FALSe.|
|[Cd2dbitmap, :: m_hBmpSrc](#m_hbmpsrc)|Handle de bitmap source.|
|[Cd2dbitmap, :: m_lpszType](#m_lpsztype)|Type de ressource.|
|[Cd2dbitmap, :: m_pBitmap](#m_pbitmap)|Stocke un pointeur vers un objet ID2D1Bitmap.|
|[Cd2dbitmap, :: m_sizeDest](#m_sizedest)|Taille de destination de la bitmap.|
|[Cd2dbitmap, :: m_strPath](#m_strpath)|Chemin d’accès du fichier Botmap.|
|[Cd2dbitmap, :: m_uiResID](#m_uiresid)|ID de ressource bitmap.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dbitmapcd2dbitmap"></a><a name="_dtorcd2dbitmap"></a> Cd2dbitmap, :: ~ Cd2dbitmap,

Destructeur. Appelé lorsqu’un objet Bitmap D2D est en cours de destruction.

```
virtual ~CD2DBitmap();
```

## <a name="cd2dbitmapattach"></a><a name="attach"></a> Cd2dbitmap, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas avoir la valeur NULL.

## <a name="cd2dbitmapcd2dbitmap"></a><a name="cd2dbitmap"></a> Cd2dbitmap, :: Cd2dbitmap,

Construit un objet Cd2dbitmap, à partir de la ressource.

```
CD2DBitmap(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszPath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    HBITMAP hbmpSrc,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*uiResID*<br/>
Numéro d’ID de ressource de la ressource.

*lpszType*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le type de ressource.

*Taille*<br/>
Taille de destination de l’image bitmap.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

*lpszPath*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom du fichier.

*hbmpSrc*<br/>
Handle de l’image bitmap.

## <a name="cd2dbitmapcommoninit"></a><a name="commoninit"></a> Cd2dbitmap, :: CommonInit

Initialise l'objet.

```cpp
void CommonInit();
```

## <a name="cd2dbitmapcopyfrombitmap"></a><a name="copyfrombitmap"></a> Cd2dbitmap, :: CopyFromBitmap

Copie la région spécifiée à partir de la bitmap spécifiée dans l’image bitmap actuelle.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pBitmap*<br/>
Bitmap à partir de laquelle effectuer la copie.

*destPoint*<br/>
Dans l’image bitmap actuelle, le coin supérieur gauche de la zone dans laquelle la zone spécifiée par srcRect est copiée.

*srcRect*<br/>
Zone de l’image bitmap à copier.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dbitmapcopyfrommemory"></a><a name="copyfrommemory"></a> Cd2dbitmap, :: CopyFromMemory

Copie la région spécifiée de la mémoire dans l’image bitmap actuelle.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>Paramètres

*srcData*<br/>
Données à copier.

*donn*<br/>
STRIDE, ou pas, de l’image bitmap source stockée dans srcData. La valeur Stride est le nombre d’octets d’un numérisation (une ligne de pixels en mémoire). Le Stride peut être calculé à partir de la formule suivante : largeur en pixels en \* octets par pixel + remplissage de la mémoire.

*destRect*<br/>
Dans l’image bitmap actuelle, le coin supérieur gauche de la zone dans laquelle la zone spécifiée par srcRect est copiée.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dbitmapcopyfromrendertarget"></a><a name="copyfromrendertarget"></a> Cd2dbitmap, :: CopyFromRenderTarget

Copie la région spécifiée de la cible de rendu spécifiée dans l’image bitmap actuelle.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Cible de rendu qui contient la zone à copier.

*destPoint*<br/>
Dans l’image bitmap actuelle, le coin supérieur gauche de la zone dans laquelle la zone spécifiée par srcRect est copiée.

*srcRect*<br/>
Zone de renderTarget à copier.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dbitmapcreate"></a><a name="create"></a> Cd2dbitmap, :: Create

Crée un Cd2dbitmap,.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dbitmapdestroy"></a><a name="destroy"></a> Cd2dbitmap, ::D estroy

Détruit un objet Cd2dbitmap,.

```
virtual void Destroy();
```

## <a name="cd2dbitmapdetach"></a><a name="detach"></a> Cd2dbitmap, ::D Etach

Détache l’interface de ressource de l’objet.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dbitmapget"></a><a name="get"></a> Cd2dbitmap, :: obtient

Retourne l’interface ID2D1Bitmap.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Bitmap ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbitmapgetdpi"></a><a name="getdpi"></a> Cd2dbitmap, :: GetDPI

Retourne les points par pouce (DPI) de la bitmap.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>Valeur renvoyée

PPP horizontal et vertical de la bitmap.

## <a name="cd2dbitmapgetpixelformat"></a><a name="getpixelformat"></a> Cd2dbitmap, :: GetPixelFormat

Récupère le format de pixel et le mode Alpha de la bitmap.

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>Valeur renvoyée

Le format de pixel et le mode Alpha de l’image bitmap.

## <a name="cd2dbitmapgetpixelsize"></a><a name="getpixelsize"></a> Cd2dbitmap, :: GetPixelSize

Retourne la taille, en unités dépendantes du périphérique (pixels), de la bitmap.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille, en pixels, de l’image bitmap.

## <a name="cd2dbitmapgetsize"></a><a name="getsize"></a> Cd2dbitmap, :: est à obtenir

Retourne la taille, en pixels indépendants du périphérique (DIP), de l’image bitmap.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille, en DIP, de l’image bitmap.

## <a name="cd2dbitmapisvalid"></a><a name="isvalid"></a> Cd2dbitmap, :: IsValid

Vérifie la validité des ressources.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la ressource est valide ; Sinon, FALSe.

## <a name="cd2dbitmapm_bautodestroyhbmp"></a><a name="m_bautodestroyhbmp"></a> Cd2dbitmap, :: m_bAutoDestroyHBMP

TRUE si m_hBmpSrc doit être détruite ; Sinon, FALSe.

```
BOOL m_bAutoDestroyHBMP;
```

## <a name="cd2dbitmapm_hbmpsrc"></a><a name="m_hbmpsrc"></a> Cd2dbitmap, :: m_hBmpSrc

Handle de bitmap source.

```
HBITMAP m_hBmpSrc;
```

## <a name="cd2dbitmapm_lpsztype"></a><a name="m_lpsztype"></a> Cd2dbitmap, :: m_lpszType

Type de ressource.

```
LPCTSTR m_lpszType;
```

## <a name="cd2dbitmapm_pbitmap"></a><a name="m_pbitmap"></a> Cd2dbitmap, :: m_pBitmap

Stocke un pointeur vers un objet ID2D1Bitmap.

```
ID2D1Bitmap* m_pBitmap;
```

## <a name="cd2dbitmapm_sizedest"></a><a name="m_sizedest"></a> Cd2dbitmap, :: m_sizeDest

Taille de destination de la bitmap.

```
CD2DSizeU m_sizeDest;
```

## <a name="cd2dbitmapm_strpath"></a><a name="m_strpath"></a> Cd2dbitmap, :: m_strPath

Chemin d’accès du fichier Botmap.

```
CString m_strPath;
```

## <a name="cd2dbitmapm_uiresid"></a><a name="m_uiresid"></a> Cd2dbitmap, :: m_uiResID

ID de ressource bitmap.

```
UINT m_uiResID;
```

## <a name="cd2dbitmapoperator-id2d1bitmap"></a><a name="operator_id2d1bitmap_star"></a> Cd2dbitmap, :: Operator ID2D1Bitmap *

Retourne l’interface ID2D1Bitmap

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Bitmap ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
