---
description: 'En savoir plus sur : classe Cd2dpathgeometry,'
title: CD2DPathGeometry, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: eb33d498436c887eb038b3312e2b98ca04d6620b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280532"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry, classe

Wrapper pour ID2D1PathGeometry.

## <a name="syntax"></a>Syntaxe

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dpathgeometry, :: Cd2dpathgeometry,](#cd2dpathgeometry)|Construit un objet Cd2dpathgeometry,.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dpathgeometry, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dpathgeometry, :: Create](#create)|Crée un Cd2dpathgeometry,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dpathgeometry, ::D estroy](#destroy)|Détruit un objet Cd2dpathgeometry,. (Substitue [CD2DGeometry, ::D estroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[Cd2dpathgeometry, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dpathgeometry, :: GetFigureCount](#getfigurecount)|Récupère le nombre de figures dans la géométrie de tracé.|
|[Cd2dpathgeometry, :: GetSegmentCount](#getsegmentcount)|Récupère le nombre de segments dans la géométrie de tracé.|
|[Cd2dpathgeometry, :: Open](#open)|Récupère le récepteur de géométrie utilisé pour remplir la géométrie de tracé avec des figures et des segments.|
|[Cd2dpathgeometry, :: Stream](#stream)|Copie le contenu de la géométrie du tracé dans le ID2D1GeometrySink spécifié.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dpathgeometry, :: m_pPathGeometry](#m_ppathgeometry)|Pointeur vers un ID2D1PathGeometry.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

[Cd2dgeometry,](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a> Cd2dpathgeometry, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas être NULL

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a> Cd2dpathgeometry, :: Cd2dpathgeometry,

Construit un objet Cd2dpathgeometry,.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a> Cd2dpathgeometry, :: Create

Crée un Cd2dpathgeometry,.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a> Cd2dpathgeometry, ::D estroy

Détruit un objet Cd2dpathgeometry,.

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a> Cd2dpathgeometry, ::D Etach

Détache l’interface de ressource de l’objet

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a> Cd2dpathgeometry, :: GetFigureCount

Récupère le nombre de figures dans la géométrie de tracé.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de figures dans la géométrie du tracé.

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a> Cd2dpathgeometry, :: GetSegmentCount

Récupère le nombre de segments dans la géométrie de tracé.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de segments dans la géométrie du tracé.

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a> Cd2dpathgeometry, :: m_pPathGeometry

Pointeur vers un ID2D1PathGeometry.

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a> Cd2dpathgeometry, :: Open

Récupère le récepteur de géométrie utilisé pour remplir la géométrie de tracé avec des figures et des segments.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le ID2D1GeometrySink utilisé pour remplir la géométrie de tracé avec des figures et des segments.

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a> Cd2dpathgeometry, :: Stream

Copie le contenu de la géométrie du tracé dans le ID2D1GeometrySink spécifié.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>Paramètres

*geometrySink*<br/>
Récepteur dans lequel le contenu de la géométrie du chemin d’accès est copié. La modification de ce récepteur ne modifie pas le contenu de cette géométrie de tracé.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
