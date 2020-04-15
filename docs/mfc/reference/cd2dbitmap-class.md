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
ms.openlocfilehash: ce4fe49e8af85c4b63be31bf10e9f196f85c019f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369317"
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap, classe

Un emballage pour ID2D1Bitmap.

## <a name="syntax"></a>Syntaxe

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Surchargé. Construit un objet CD2DBitmap à partir de HBITMAP.|
|[CD2DBitmap: :CD2DBitmap](#_dtorcd2dbitmap)|Destructeur. Appelé quand un objet de bitmap D2D est détruit.|

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Surchargé. Construit un objet CD2DBitmap.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DBitmap::CopyDeBitmap](#copyfrombitmap)|Copies de la région spécifiée à partir de la bitmap spécifiée dans la bitmap actuelle|
|[CD2DBitmap::CopyDeMemory](#copyfrommemory)|Copies de la région spécifiée de la mémoire dans la bitmap actuelle|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Copies de la région spécifiée à partir de la cible de rendu spécifiée dans la bitmap actuelle|
|[CD2DBitmap::Créer](#create)|Crée un CD2DBitmap. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::Destroy](#destroy)|Détruit un objet CD2DBitmap. (Overrides [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBitmap::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DBitmap::Get](#get)|Retourne l’interface ID2D1Bitmap|
|[CD2DBitmap::GetDPI](#getdpi)|Retourner les points par pouce (DPI) de la bitmap|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Récupère le format pixel et le mode alpha de la bitmap|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Retourne la taille, dans les unités dépendantes de l’appareil (pixels), de la bitmap|
|[CD2DBitmap::GetSize](#getsize)|Retourne la taille, en pixels indépendants de l’appareil (PPE), de la bitmap|
|[CD2DBitmap::IsValid](#isvalid)|Vérifie la validité des ressources (Overrides [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|Initialise l’objet|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::opérateur ID2D1Bitmap](#operator_id2d1bitmap_star)|Retourne l’interface ID2D1Bitmap|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|VRAI si m_hBmpSrc doit être détruit; autrement FALSE.|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Poignée de bitmap source.|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Type de ressource.|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Stocke un pointeur sur un objet ID2D1Bitmap.|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Taille de destination Bitmap.|
|[CD2DBitmap::m_strPath](#m_strpath)|Chemin de fichier Botmap.|
|[CD2DBitmap::m_uiResID](#m_uiresid)|Id de ressources Bitmap.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dbitmapcd2dbitmap"></a><a name="_dtorcd2dbitmap"></a>CD2DBitmap: :CD2DBitmap

Destructeur. Appelé quand un objet de bitmap D2D est détruit.

```
virtual ~CD2DBitmap();
```

## <a name="cd2dbitmapattach"></a><a name="attach"></a>CD2DBitmap::Attach

Attache l’interface de ressources existante à l’objet.

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Ne peut pas avoir la valeur NULL.

## <a name="cd2dbitmapcd2dbitmap"></a><a name="cd2dbitmap"></a>CD2DBitmap::CD2DBitmap

Construit un objet CD2DBitmap à partir d’une ressource.

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
Un pointeur à la cible de rendu.

*uiResID*<br/>
Le numéro d’identification des ressources de la ressource.

*lpszType (lpszType)*<br/>
Pointeur vers une chaîne non terminée qui contient le type de ressource.

*tailleDest*<br/>
Taille de destination de la bitmap.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

*lpszPath*<br/>
Pointeur vers une chaîne non terminée qui contient le nom du fichier.

*hbmpSrc (en)*<br/>
Manipulez à la bitmap.

## <a name="cd2dbitmapcommoninit"></a><a name="commoninit"></a>CD2DBitmap::CommonInit

Initialise l'objet.

```
void CommonInit();
```

## <a name="cd2dbitmapcopyfrombitmap"></a><a name="copyfrombitmap"></a>CD2DBitmap::CopyDeBitmap

Copie la région spécifiée à partir de la bitmap spécifiée dans la bitmap actuelle.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pBitmap (en)*<br/>
La bitmap à copier.

*destPoint*<br/>
Dans la bitmap actuelle, le coin supérieur gauche de la zone à laquelle la région spécifiée par le srcRect est copié.

*srcRect*<br/>
La zone de bitmap à copier.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dbitmapcopyfrommemory"></a><a name="copyfrommemory"></a>CD2DBitmap::CopyDeMemory

Copie la région spécifiée de la mémoire dans la bitmap actuelle.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>Paramètres

*srcData*<br/>
Données à copier.

*Terrain*<br/>
La foulée, ou la hauteur, de la bitmap source stockée dans srcData. La foulée est le nombre d’endes d’une ligne de scan (une rangée de pixels dans la mémoire). La foulée peut être calculée à partir \* de la formule suivante : octets de largeur de pixel par pixel et rembourrage de mémoire.

*destRect*<br/>
Dans la bitmap actuelle, le coin supérieur gauche de la zone à laquelle la région spécifiée par le srcRect est copié.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dbitmapcopyfromrendertarget"></a><a name="copyfromrendertarget"></a>CD2DBitmap::CopyFromRenderTarget

Copie la région spécifiée à partir de la cible de rendu spécifiée dans la bitmap actuelle.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
La cible de rendu qui contient la région à copier.

*destPoint*<br/>
Dans la bitmap actuelle, le coin supérieur gauche de la zone à laquelle la région spécifiée par le srcRect est copié.

*srcRect*<br/>
La zone de renduTarget à copier.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dbitmapcreate"></a><a name="create"></a>CD2DBitmap::Créer

Crée un CD2DBitmap.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dbitmapdestroy"></a><a name="destroy"></a>CD2DBitmap::Destroy

Détruit un objet CD2DBitmap.

```
virtual void Destroy();
```

## <a name="cd2dbitmapdetach"></a><a name="detach"></a>CD2DBitmap::Detach

Détache l’interface des ressources de l’objet.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dbitmapget"></a><a name="get"></a>CD2DBitmap::Get

Retourne l’interface ID2D1Bitmap.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Bitmap ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dbitmapgetdpi"></a><a name="getdpi"></a>CD2DBitmap::GetDPI

Retourner les points par pouce (DPI) de la bitmap.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>Valeur de retour

Le DPI horizontal et vertical de la bitmap.

## <a name="cd2dbitmapgetpixelformat"></a><a name="getpixelformat"></a>CD2DBitmap::GetPixelFormat

Récupère le format pixel et le mode alpha de la bitmap

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>Valeur de retour

Le format pixel et le mode alpha de la bitmap.

## <a name="cd2dbitmapgetpixelsize"></a><a name="getpixelsize"></a>CD2DBitmap::GetPixelSize

Retourne la taille, dans les unités dépendantes de l’appareil (pixels), de la bitmap.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille, en pixels, de la bitmap.

## <a name="cd2dbitmapgetsize"></a><a name="getsize"></a>CD2DBitmap::GetSize

Retourne la taille, en pixels indépendants de l’appareil (PPE), de la bitmap.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille, en PPE, de la bitmap.

## <a name="cd2dbitmapisvalid"></a><a name="isvalid"></a>CD2DBitmap::IsValid

Vérifie la validité des ressources.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la ressource est valide; autrement FALSE.

## <a name="cd2dbitmapm_bautodestroyhbmp"></a><a name="m_bautodestroyhbmp"></a>CD2DBitmap::m_bAutoDestroyHBMP

VRAI si m_hBmpSrc doit être détruit; autrement FALSE.

```
BOOL m_bAutoDestroyHBMP;
```

## <a name="cd2dbitmapm_hbmpsrc"></a><a name="m_hbmpsrc"></a>CD2DBitmap::m_hBmpSrc

Poignée de bitmap source.

```
HBITMAP m_hBmpSrc;
```

## <a name="cd2dbitmapm_lpsztype"></a><a name="m_lpsztype"></a>CD2DBitmap::m_lpszType

Type de ressource.

```
LPCTSTR m_lpszType;
```

## <a name="cd2dbitmapm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmap::m_pBitmap

Stocke un pointeur sur un objet ID2D1Bitmap.

```
ID2D1Bitmap* m_pBitmap;
```

## <a name="cd2dbitmapm_sizedest"></a><a name="m_sizedest"></a>CD2DBitmap::m_sizeDest

Taille de destination Bitmap.

```
CD2DSizeU m_sizeDest;
```

## <a name="cd2dbitmapm_strpath"></a><a name="m_strpath"></a>CD2DBitmap::m_strPath

Chemin de fichier Botmap.

```
CString m_strPath;
```

## <a name="cd2dbitmapm_uiresid"></a><a name="m_uiresid"></a>CD2DBitmap::m_uiResID

Id de ressources Bitmap.

```
UINT m_uiResID;
```

## <a name="cd2dbitmapoperator-id2d1bitmap"></a><a name="operator_id2d1bitmap_star"></a>CD2DBitmap::opérateur ID2D1Bitmap

Retourne l’interface ID2D1Bitmap

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Bitmap ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
