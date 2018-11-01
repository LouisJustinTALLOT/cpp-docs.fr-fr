---
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
ms.openlocfilehash: 869d8c9cffae1a257de04cf82446025be33ef7de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605866"
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
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Surchargé. Construit un objet CD2DBitmap à partir de HBITMAP.|
|[CD2DBitmap :: ~ CD2DBitmap](#_dtorcd2dbitmap)|Destructeur. Appelé lorsqu’un objet de bitmap D2D est détruit.|

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Surchargé. Construit un objet CD2DBitmap.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::Attach](#attach)|Attache existant à l’objet interface de la ressource|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Copie de la région spécifiée à partir de la bitmap spécifiée dans l’image bitmap actuelle|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Copie de la région spécifiée de la mémoire dans l’image bitmap actuelle|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Copie la région spécifiée à partir du spécifié cible de rendu dans l’image bitmap actuelle|
|[CD2DBitmap::Create](#create)|Crée un CD2DBitmap. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::Destroy](#destroy)|Détruit un objet CD2DBitmap. (Substitue [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBitmap::Detach](#detach)|Détache l’interface de ressources de l’objet|
|[CD2DBitmap::Get](#get)|Renvoie l’interface ID2D1Bitmap|
|[CD2DBitmap::GetDPI](#getdpi)|Retourner les points par pouce (PPP) de l’image bitmap|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Récupère le mode d’alpha et du format de pixel de l’image bitmap|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Retourne la taille, en unités dépendantes du périphérique (pixels), de l’image bitmap|
|[CD2DBitmap::GetSize](#getsize)|Retourne la taille, en pixels indépendants du périphérique (DIP), de l’image bitmap|
|[CD2DBitmap::IsValid](#isvalid)|Vérifie la validité des ressources (remplace [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|Initialise l’objet|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|Renvoie l’interface ID2D1Bitmap|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|TRUE si m_hBmpSrc doit être détruit ; Sinon, FALSE.|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Handle de bitmap source.|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Type de ressource.|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Stocke un pointeur vers un objet ID2D1Bitmap.|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Taille de la destination de la bitmap.|
|[CD2DBitmap::m_strPath](#m_strpath)|Chemin d’accès du fichier bitmap.|
|[CD2DBitmap::m_uiResID](#m_uiresid)|ID de ressource bitmap.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="_dtorcd2dbitmap"></a>  CD2DBitmap :: ~ CD2DBitmap

Destructeur. Appelé lorsqu’un objet de bitmap D2D est détruit.

```
virtual ~CD2DBitmap();
```

##  <a name="attach"></a>  CD2DBitmap::Attach

Attache existant à l’objet interface de la ressource.

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource*<br/>
Interface de la ressource existante. Ne peut pas être Null.

##  <a name="cd2dbitmap"></a>  CD2DBitmap::CD2DBitmap

Construit un objet CD2DBitmap à partir de la ressource.

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
Pointeur vers une chaîne se terminant par null qui contient le type de ressource.

*sizeDest*<br/>
Taille de la destination de la bitmap.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

*lpszPath*<br/>
Pointeur vers une chaîne se terminant par null qui contient le nom du fichier.

*hbmpSrc*<br/>
Handle de l’image bitmap.

##  <a name="commoninit"></a>  CD2DBitmap::CommonInit

Initialise l’objet.

```
void CommonInit();
```

##  <a name="copyfrombitmap"></a>  CD2DBitmap::CopyFromBitmap

Copie la région spécifiée à partir de la bitmap spécifiée dans l’image bitmap actuelle.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pBitmap*<br/>
La bitmap à copier.

*destPoint*<br/>
Dans l’image bitmap actuelle, l’angle supérieur gauche de la zone à laquelle la région spécifiée par srcRect est copiée.

*srcRect*<br/>
La zone de bitmap à copier.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="copyfrommemory"></a>  CD2DBitmap::CopyFromMemory

Copie la région spécifiée de la mémoire dans l’image bitmap actuelle.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>Paramètres

*srcData*<br/>
Les données à copier.

*Espacement*<br/>
Le stride, ou pas, de la bitmap source stockée dans srcData. Cette valeur est le nombre d’octets d’une ligne de numérisation (une ligne de pixels en mémoire). Le stride peut être calculé à partir de la formule suivante : largeur en pixels \* octets par pixel + remplissage de la mémoire.

*destRect*<br/>
Dans l’image bitmap actuelle, l’angle supérieur gauche de la zone à laquelle la région spécifiée par srcRect est copiée.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="copyfromrendertarget"></a>  CD2DBitmap::CopyFromRenderTarget

Copie la région spécifiée à partir du spécifié cible de rendu dans l’image bitmap en cours.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
La cible de rendu qui contient la zone à copier.

*destPoint*<br/>
Dans l’image bitmap actuelle, l’angle supérieur gauche de la zone à laquelle la région spécifiée par srcRect est copiée.

*srcRect*<br/>
Zone de la cible de rendu à copier.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="create"></a>  CD2DBitmap::Create

Crée un CD2DBitmap.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="destroy"></a>  CD2DBitmap::Destroy

Détruit un objet CD2DBitmap.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmap::Detach

Détache l’interface de ressources de l’objet.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface de la ressource détachée.

##  <a name="get"></a>  CD2DBitmap::Get

Renvoie l’interface ID2D1Bitmap.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1Bitmap ou NULL si l’objet n’est pas encore initialisé.

##  <a name="getdpi"></a>  CD2DBitmap::GetDPI

Retourner les points par pouce (PPP) de l’image bitmap.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>Valeur de retour

La résolution horizontale et verticale de l’image bitmap.

##  <a name="getpixelformat"></a>  CD2DBitmap::GetPixelFormat

Récupère le mode d’alpha et du format de pixel de l’image bitmap

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>Valeur de retour

Mode d’alpha et du format de pixel de la bitmap.

##  <a name="getpixelsize"></a>  CD2DBitmap::GetPixelSize

Retourne la taille, en unités dépendantes du périphérique (pixels), de la bitmap.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille, en pixels, de la bitmap...

##  <a name="getsize"></a>  CD2DBitmap::GetSize

Retourne la taille, en pixels indépendants du périphérique (DIP), de la bitmap.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille, en DIP, de la bitmap.

##  <a name="isvalid"></a>  CD2DBitmap::IsValid

Vérifie la validité de la ressource.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la ressource est valide ; Sinon, FALSE.

##  <a name="m_bautodestroyhbmp"></a>  CD2DBitmap::m_bAutoDestroyHBMP

TRUE si m_hBmpSrc doit être détruit ; Sinon, FALSE.

```
BOOL m_bAutoDestroyHBMP;
```

##  <a name="m_hbmpsrc"></a>  CD2DBitmap::m_hBmpSrc

Handle de bitmap source.

```
HBITMAP m_hBmpSrc;
```

##  <a name="m_lpsztype"></a>  CD2DBitmap::m_lpszType

Type de ressource.

```
LPCTSTR m_lpszType;
```

##  <a name="m_pbitmap"></a>  CD2DBitmap::m_pBitmap

Stocke un pointeur vers un objet ID2D1Bitmap.

```
ID2D1Bitmap* m_pBitmap;
```

##  <a name="m_sizedest"></a>  CD2DBitmap::m_sizeDest

Taille de la destination de la bitmap.

```
CD2DSizeU m_sizeDest;
```

##  <a name="m_strpath"></a>  CD2DBitmap::m_strPath

Chemin d’accès du fichier bitmap.

```
CString m_strPath;
```

##  <a name="m_uiresid"></a>  CD2DBitmap::m_uiResID

ID de ressource bitmap.

```
UINT m_uiResID;
```

##  <a name="operator_id2d1bitmap_star"></a>  CD2DBitmap::operator ID2D1Bitmap *

Renvoie l’interface ID2D1Bitmap

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface de ID2D1Bitmap ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
