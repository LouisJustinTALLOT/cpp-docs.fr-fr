---
description: 'En savoir plus sur : classe Cd2dmesh,'
title: CD2DMesh, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
ms.openlocfilehash: fbdb941d04b87df5c136f1925445564caab63443
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193368"
---
# <a name="cd2dmesh-class"></a>CD2DMesh, classe

Wrapper pour ID2D1Mesh.

## <a name="syntax"></a>Syntaxe

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dmesh, :: Cd2dmesh,](#cd2dmesh)|Construit un objet Cd2dmesh,.|
|[Cd2dmesh, :: ~ Cd2dmesh,](#_dtorcd2dmesh)|Destructeur. Appelé lorsqu’un objet de maillage D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dmesh, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dmesh, :: Create](#create)|Crée un Cd2dmesh,. (Substitue [CD2DResource, :: Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[Cd2dmesh, ::D estroy](#destroy)|Détruit un objet Cd2dmesh,. (Substitue [CD2DResource, ::D estroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[Cd2dmesh, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dmesh, :: obtient](#get)|Retourne l’interface ID2D1Mesh|
|[Cd2dmesh, :: IsValid](#isvalid)|Vérifie la validité des ressources (Substitue [CD2DResource, :: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[Cd2dmesh, :: Open](#open)|Ouvre la maille pour le remplissage.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dmesh, :: Operator ID2D1Mesh *](#operator_id2d1mesh_star)|Retourne l’interface ID2D1Mesh|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dmesh, :: m_pMesh](#m_pmesh)|Pointeur vers un ID2D1Mesh.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dmeshcd2dmesh"></a><a name="_dtorcd2dmesh"></a> Cd2dmesh, :: ~ Cd2dmesh,

Destructeur. Appelé lorsqu’un objet de maillage D2D est détruit.

```
virtual ~CD2DMesh();
```

## <a name="cd2dmeshattach"></a><a name="attach"></a> Cd2dmesh, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas être NULL

## <a name="cd2dmeshcd2dmesh"></a><a name="cd2dmesh"></a> Cd2dmesh, :: Cd2dmesh,

Construit un objet Cd2dmesh,.

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dmeshcreate"></a><a name="create"></a> Cd2dmesh, :: Create

Crée un Cd2dmesh,.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Pointeur vers la cible de rendu.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="cd2dmeshdestroy"></a><a name="destroy"></a> Cd2dmesh, ::D estroy

Détruit un objet Cd2dmesh,.

```
virtual void Destroy();
```

## <a name="cd2dmeshdetach"></a><a name="detach"></a> Cd2dmesh, ::D Etach

Détache l’interface de ressource de l’objet

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dmeshget"></a><a name="get"></a> Cd2dmesh, :: obtient

Retourne l’interface ID2D1Mesh

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Mesh ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dmeshisvalid"></a><a name="isvalid"></a> Cd2dmesh, :: IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la ressource est valide ; Sinon, FALSe.

## <a name="cd2dmeshm_pmesh"></a><a name="m_pmesh"></a> Cd2dmesh, :: m_pMesh

Pointeur vers un ID2D1Mesh.

```
ID2D1Mesh* m_pMesh;
```

## <a name="cd2dmeshopen"></a><a name="open"></a> Cd2dmesh, :: Open

Ouvre la maille pour le remplissage.

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un ID2D1TessellationSink utilisé pour remplir le maillage.

## <a name="cd2dmeshoperator-id2d1mesh"></a><a name="operator_id2d1mesh_star"></a> Cd2dmesh, :: Operator ID2D1Mesh *

Retourne l’interface ID2D1Mesh

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Mesh ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
