---
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
ms.openlocfilehash: e2cc6be7119a2df193aa2af415a9c8d4054f537c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396299"
---
# <a name="cd2dresource-class"></a>CD2DResource, classe

Une classe abstraite qui fournit une interface pour créer et gérer des ressources D2D telles que des pinceaux, des couches et des textes.

## <a name="syntax"></a>Syntaxe

```
class CD2DResource : public CObject;
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|Construit un objet CD2DResource.|
|[CD2DResource :: ~ CD2DResource](#_dtorcd2dresource)|Destructeur. Appelé lorsqu’un objet de ressource D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DResource::Create](#create)|Crée un CD2DResource.|
|[CD2DResource::Destroy](#destroy)|Détruit un objet CD2DResource.|
|[CD2DResource::IsValid](#isvalid)|Vérifications de validité des ressources|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|Indicateur de destruction de vérification automatique.|
|[CD2DResource::ReCreate](#recreate)|Recrée un CD2DResource.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|Ressource sera détruite par le propriétaire (CRenderTarget)|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|Pointeur vers le parent CRenderTarget)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="_dtorcd2dresource"></a>  CD2DResource :: ~ CD2DResource

Destructeur. Appelé lorsqu’un objet de ressource D2D est détruit.

```
virtual ~CD2DResource();
```

##  <a name="cd2dresource"></a>  CD2DResource::CD2DResource

Construit un objet CD2DResource.

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

##  <a name="create"></a>  CD2DResource::Create

Crée un CD2DResource.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="destroy"></a>  CD2DResource::Destroy

Détruit un objet CD2DResource.

```
virtual void Destroy() = 0;
```

##  <a name="isautodestroy"></a>  CD2DResource::IsAutoDestroy

Indicateur de destruction de vérification automatique.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si l’objet sera détruit par son propriétaire ; Sinon, FALSE.

##  <a name="isvalid"></a>  CD2DResource::IsValid

Vérifications de validité des ressources

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la ressource est valide ; Sinon, FALSE.

##  <a name="m_bisautodestroy"></a>  CD2DResource::m_bIsAutoDestroy

Ressource sera détruite par le propriétaire (CRenderTarget)

```
BOOL m_bIsAutoDestroy;
```

##  <a name="m_pparenttarget"></a>  CD2DResource::m_pParentTarget

Pointeur vers le parent CRenderTarget)

```
CRenderTarget* m_pParentTarget;
```

##  <a name="recreate"></a>  CD2DResource::ReCreate

Recrée un CD2DResource.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
