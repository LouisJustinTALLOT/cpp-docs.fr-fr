---
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
ms.openlocfilehash: 91460e3435130530ecc57bdcc09d1c7301333a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753077"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry, classe

Un emballage pour ID2D1PathGeometry.

## <a name="syntax"></a>Syntaxe

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Construit un objet CD2DPathGeometry.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DPathGeometry::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DPathGeometry::Créer](#create)|Crée un CD2DPathGeometry. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DPathGeometry::Destroy](#destroy)|Détruit un objet CD2DPathGeometry. (Overrides [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[CD2DPathGeometry::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Récupère le nombre de figures dans la géométrie du chemin.|
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Récupère le nombre de segments dans la géométrie du chemin.|
|[CD2DPathGeometry::Ouvert](#open)|Récupère l’évier de géométrie qui est utilisé pour peupler la géométrie du chemin avec des figures et des segments.|
|[CD2DPathGeometry::Stream](#stream)|Copie le contenu de la géométrie du chemin à l’ID2D1GeometrySink spécifié.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Un pointeur à un ID2D1PathGeometry.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

[CD2DGeometry (en anglais)](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a>CD2DPathGeometry::Attach

Attache l’interface de ressources existante à l’objet

```cpp
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Impossible d’être NULL

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry

Construit un objet CD2DPathGeometry.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Un pointeur à la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a>CD2DPathGeometry::Créer

Crée un CD2DPathGeometry.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a>CD2DPathGeometry::Destroy

Détruit un objet CD2DPathGeometry.

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a>CD2DPathGeometry::Detach

Détache l’interface des ressources de l’objet

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount

Récupère le nombre de figures dans la géométrie du chemin.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de chiffres dans la géométrie du chemin.

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount

Récupère le nombre de segments dans la géométrie du chemin.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de segments dans la géométrie du chemin.

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry

Un pointeur à un ID2D1PathGeometry.

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a>CD2DPathGeometry::Ouvert

Récupère l’évier de géométrie qui est utilisé pour peupler la géométrie du chemin avec des figures et des segments.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’ID2D1GeometrySink qui est utilisé pour peupler la géométrie du chemin avec des chiffres et des segments.

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a>CD2DPathGeometry::Stream

Copie le contenu de la géométrie du chemin à l’ID2D1GeometrySink spécifié.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>Paramètres

*géométrieSink*<br/>
L’évier auquel le contenu de la géométrie du chemin est copié. Modifier cet évier ne modifie pas le contenu de cette géométrie de chemin.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
