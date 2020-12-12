---
description: 'En savoir plus sur : classe Cd2dlayer,'
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
ms.openlocfilehash: bd41cd591e6422c9434cd84d20cb6e5d778410bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306948"
---
# <a name="cd2dlayer-class"></a>CD2DLayer, classe

Wrapper pour ID2D1Layer.

## <a name="syntax"></a>Syntaxe

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dlayer, :: Cd2dlayer,](#cd2dlayer)|Construit un objet Cd2dlayer,.|
|[Cd2dlayer, :: ~ Cd2dlayer,](#_dtorcd2dlayer)|Destructeur. Appelé lorsqu’un objet de couche D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dlayer, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dlayer, :: Create](#create)|Crée un Cd2dlayer,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dlayer, ::D estroy](#destroy)|Détruit un objet Cd2dlayer,. (Substitue [CD2DResource, ::D estroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[Cd2dlayer, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dlayer, :: obtient](#get)|Retourne l’interface ID2D1Layer|
|[Cd2dlayer, :: est à obtenir](#getsize)|Retourne la taille de la cible de rendu en pixels indépendants du périphérique|
|[Cd2dlayer, :: IsValid](#isvalid)|Vérifie la validité des ressources (Substitue [CD2DResource, :: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dlayer, :: Operator ID2D1Layer *](#operator_id2d1layer_star)|Retourne l’interface ID2D1Layer|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dlayer, :: m_pLayer](#m_player)|Stocke un pointeur vers un objet ID2D1Layer.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a> Cd2dlayer, :: ~ Cd2dlayer,

Destructeur. Appelé lorsqu’un objet de couche D2D est détruit.

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a> Cd2dlayer, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas être NULL

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a> Cd2dlayer, :: Cd2dlayer,

Construit un objet Cd2dlayer,.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dlayercreate"></a><a name="create"></a> Cd2dlayer, :: Create

Crée un Cd2dlayer,.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a> Cd2dlayer, ::D estroy

Détruit un objet Cd2dlayer,.

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a> Cd2dlayer, ::D Etach

Détache l’interface de ressource de l’objet

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dlayerget"></a><a name="get"></a> Cd2dlayer, :: obtient

Retourne l’interface ID2D1Layer

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Layer ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dlayergetsize"></a><a name="getsize"></a> Cd2dlayer, :: est à obtenir

Retourne la taille de la cible de rendu en pixels indépendants du périphérique

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille actuelle de la cible de rendu en pixels indépendants du périphérique

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a> Cd2dlayer, :: IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la ressource est valide ; Sinon, FALSe.

## <a name="cd2dlayerm_player"></a><a name="m_player"></a> Cd2dlayer, :: m_pLayer

Stocke un pointeur vers un objet ID2D1Layer.

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a> Cd2dlayer, :: Operator ID2D1Layer *

Retourne l’interface ID2D1Layer

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Layer ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
