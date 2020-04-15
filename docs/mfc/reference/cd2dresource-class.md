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
ms.openlocfilehash: 5e747eda42e625d0f4cf65859e471933bbb043ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369093"
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
|[CD2DResource: 'CD2DResource](#_dtorcd2dresource)|Destructeur. Appelé lorsqu’un objet de ressources D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DResource::Créer](#create)|Crée un CD2DResource.|
|[CD2DResource::Destroy](#destroy)|Détruit un objet CD2DResource.|
|[CD2DResource::IsValid](#isvalid)|Vérifie la validité des ressources|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|Vérifiez le drapeau de destruction automatique.|
|[CD2DResource::ReCreate](#recreate)|Re-crée un CD2DResource.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|Les ressources seront détruites par le propriétaire (CRenderTarget)|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|Pointeur au parent CRenderTarget)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a>CD2DResource: 'CD2DResource

Destructeur. Appelé lorsqu’un objet de ressources D2D est détruit.

```
virtual ~CD2DResource();
```

## <a name="cd2dresourcecd2dresource"></a><a name="cd2dresource"></a>CD2DResource::CD2DResource

Construit un objet CD2DResource.

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Un pointeur à la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dresourcecreate"></a><a name="create"></a>CD2DResource::Créer

Crée un CD2DResource.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dresourcedestroy"></a><a name="destroy"></a>CD2DResource::Destroy

Détruit un objet CD2DResource.

```
virtual void Destroy() = 0;
```

## <a name="cd2dresourceisautodestroy"></a><a name="isautodestroy"></a>CD2DResource::IsAutoDestroy

Vérifiez le drapeau de destruction automatique.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si l’objet sera détruit par son propriétaire; autrement FALSE.

## <a name="cd2dresourceisvalid"></a><a name="isvalid"></a>CD2DResource::IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la ressource est valide; autrement FALSE.

## <a name="cd2dresourcem_bisautodestroy"></a><a name="m_bisautodestroy"></a>CD2DResource::m_bIsAutoDestroy

Les ressources seront détruites par le propriétaire (CRenderTarget)

```
BOOL m_bIsAutoDestroy;
```

## <a name="cd2dresourcem_pparenttarget"></a><a name="m_pparenttarget"></a>CD2DResource::m_pParentTarget

Pointeur au parent CRenderTarget)

```
CRenderTarget* m_pParentTarget;
```

## <a name="cd2dresourcerecreate"></a><a name="recreate"></a>CD2DResource::ReCreate

Re-crée un CD2DResource.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
