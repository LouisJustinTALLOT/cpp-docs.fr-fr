---
title: CD2DLayer, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: 30025d6097e439c07202d144a6e549845b78ffa6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754759"
---
# <a name="cd2dlayer-class"></a>CD2DLayer, classe

Un emballage pour ID2D1Layer.

## <a name="syntax"></a>Syntaxe

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Construit un objet CD2DLayer.|
|[CD2DLayer: :CD2DLayer](#_dtorcd2dlayer)|Destructeur. Appelé quand un objet de couche D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DLayer::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DLayer::Créer](#create)|Crée un CD2DLayer. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::Destroy](#destroy)|Détruit un objet CD2DLayer. (Overrides [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DLayer::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DLayer::Get](#get)|Retourne l’interface ID2D1Layer|
|[CD2DLayer::GetSize](#getsize)|Retourne la taille de la cible de rendu en pixels indépendants de l’appareil|
|[CD2DLayer::IsValid](#isvalid)|Vérifie la validité des ressources (Overrides [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DLayer::opérateur ID2D1Layer](#operator_id2d1layer_star)|Retourne l’interface ID2D1Layer|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|Stocke un pointeur sur un objet ID2D1Layer.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a>CD2DLayer: :CD2DLayer

Destructeur. Appelé quand un objet de couche D2D est détruit.

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a>CD2DLayer::Attach

Attache l’interface de ressources existante à l’objet

```cpp
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Impossible d’être NULL

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a>CD2DLayer::CD2DLayer

Construit un objet CD2DLayer.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Un pointeur à la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dlayercreate"></a><a name="create"></a>CD2DLayer::Créer

Crée un CD2DLayer.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a>CD2DLayer::Destroy

Détruit un objet CD2DLayer.

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a>CD2DLayer::Detach

Détache l’interface des ressources de l’objet

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dlayerget"></a><a name="get"></a>CD2DLayer::Get

Retourne l’interface ID2D1Layer

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Layer ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dlayergetsize"></a><a name="getsize"></a>CD2DLayer::GetSize

Retourne la taille de la cible de rendu en pixels indépendants de l’appareil

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille actuelle de la cible de rendu en pixels indépendants de l’appareil

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a>CD2DLayer::IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la ressource est valide; autrement FALSE.

## <a name="cd2dlayerm_player"></a><a name="m_player"></a>CD2DLayer::m_pLayer

Stocke un pointeur sur un objet ID2D1Layer.

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a>CD2DLayer::opérateur ID2D1Layer

Retourne l’interface ID2D1Layer

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Layer ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
