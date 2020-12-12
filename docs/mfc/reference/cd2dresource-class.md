---
description: 'En savoir plus sur : classe Cd2dresource,'
title: CD2DResource, classe
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: a110732a7e2bde5ab2fb3b6025acf98d6a3278c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118730"
---
# <a name="cd2dresource-class"></a>CD2DResource, classe

Classe abstraite qui fournit une interface pour créer et gérer des ressources D2D, telles que des pinceaux, des couches et des textes.

## <a name="syntax"></a>Syntaxe

```
class CD2DResource : public CObject;
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dresource, :: Cd2dresource,](#cd2dresource)|Construit un objet Cd2dresource,.|
|[Cd2dresource, :: ~ Cd2dresource,](#_dtorcd2dresource)|Destructeur. Appelé lorsqu’un objet de ressource D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dresource, :: Create](#create)|Crée un Cd2dresource,.|
|[Cd2dresource, ::D estroy](#destroy)|Détruit un objet Cd2dresource,.|
|[Cd2dresource, :: IsValid](#isvalid)|Vérifie la validité des ressources|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[Cd2dresource, :: IsAutoDestroy](#isautodestroy)|Activez l’indicateur de destruction automatique.|
|[Cd2dresource, :: recréer](#recreate)|Recrée un Cd2dresource,.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dresource, :: m_bIsAutoDestroy](#m_bisautodestroy)|La ressource sera détruite par le propriétaire (CRenderTarget,)|
|[Cd2dresource, :: m_pParentTarget](#m_pparenttarget)|Pointeur vers le CRenderTarget, parent)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a> Cd2dresource, :: ~ Cd2dresource,

Destructeur. Appelé lorsqu’un objet de ressource D2D est détruit.

```
virtual ~CD2DResource();
```

## <a name="cd2dresourcecd2dresource"></a><a name="cd2dresource"></a> Cd2dresource, :: Cd2dresource,

Construit un objet Cd2dresource,.

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dresourcecreate"></a><a name="create"></a> Cd2dresource, :: Create

Crée un Cd2dresource,.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dresourcedestroy"></a><a name="destroy"></a> Cd2dresource, ::D estroy

Détruit un objet Cd2dresource,.

```
virtual void Destroy() = 0;
```

## <a name="cd2dresourceisautodestroy"></a><a name="isautodestroy"></a> Cd2dresource, :: IsAutoDestroy

Activez l’indicateur de destruction automatique.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’objet sera détruit par son propriétaire ; Sinon, FALSe.

## <a name="cd2dresourceisvalid"></a><a name="isvalid"></a> Cd2dresource, :: IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la ressource est valide ; Sinon, FALSe.

## <a name="cd2dresourcem_bisautodestroy"></a><a name="m_bisautodestroy"></a> Cd2dresource, :: m_bIsAutoDestroy

La ressource sera détruite par le propriétaire (CRenderTarget,)

```
BOOL m_bIsAutoDestroy;
```

## <a name="cd2dresourcem_pparenttarget"></a><a name="m_pparenttarget"></a> Cd2dresource, :: m_pParentTarget

Pointeur vers le CRenderTarget, parent)

```
CRenderTarget* m_pParentTarget;
```

## <a name="cd2dresourcerecreate"></a><a name="recreate"></a> Cd2dresource, :: recréer

Recrée un Cd2dresource,.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
