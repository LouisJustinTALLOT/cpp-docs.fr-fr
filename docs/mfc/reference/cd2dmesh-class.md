---
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
ms.openlocfilehash: 64f5dd7b40853a86dc7f964ecd3701f132a94e16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369180"
---
# <a name="cd2dmesh-class"></a>CD2DMesh, classe

Un emballage pour ID2D1Mesh.

## <a name="syntax"></a>Syntaxe

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Construit un objet CD2DMesh.|
|[CD2DMesh: :CD2DMesh](#_dtorcd2dmesh)|Destructeur. Appelé quand un objet de maille D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DMesh::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DMesh::Créer](#create)|Crée un CD2DMesh. (Overrides [CD2DResource::Créer](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DMesh::Destroy](#destroy)|Détruit un objet CD2DMesh. (Overrides [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DMesh::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DMesh::Get](#get)|Retourne l’interface ID2D1Mesh|
|[CD2DMesh::IsValid](#isvalid)|Vérifie la validité des ressources (Overrides [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DMesh::Ouvert](#open)|Ouvre le maillage pour la population.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DMesh::opérateur ID2D1Mesh](#operator_id2d1mesh_star)|Retourne l’interface ID2D1Mesh|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DMesh::m_pMesh](#m_pmesh)|Un pointeur à un ID2D1Mesh.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dmeshcd2dmesh"></a><a name="_dtorcd2dmesh"></a>CD2DMesh: :CD2DMesh

Destructeur. Appelé quand un objet de maille D2D est détruit.

```
virtual ~CD2DMesh();
```

## <a name="cd2dmeshattach"></a><a name="attach"></a>CD2DMesh::Attach

Attache l’interface de ressources existante à l’objet

```
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Impossible d’être NULL

## <a name="cd2dmeshcd2dmesh"></a><a name="cd2dmesh"></a>CD2DMesh::CD2DMesh

Construit un objet CD2DMesh.

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Un pointeur à la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dmeshcreate"></a><a name="create"></a>CD2DMesh::Créer

Crée un CD2DMesh.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Paramètres

*pRenderTarget*<br/>
Un pointeur à la cible de rendu.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="cd2dmeshdestroy"></a><a name="destroy"></a>CD2DMesh::Destroy

Détruit un objet CD2DMesh.

```
virtual void Destroy();
```

## <a name="cd2dmeshdetach"></a><a name="detach"></a>CD2DMesh::Detach

Détache l’interface des ressources de l’objet

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dmeshget"></a><a name="get"></a>CD2DMesh::Get

Retourne l’interface ID2D1Mesh

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Mesh ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dmeshisvalid"></a><a name="isvalid"></a>CD2DMesh::IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la ressource est valide; autrement FALSE.

## <a name="cd2dmeshm_pmesh"></a><a name="m_pmesh"></a>CD2DMesh::m_pMesh

Un pointeur à un ID2D1Mesh.

```
ID2D1Mesh* m_pMesh;
```

## <a name="cd2dmeshopen"></a><a name="open"></a>CD2DMesh::Ouvert

Ouvre le maillage pour la population.

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un ID2D1TessellationSink qui est utilisé pour peupler le maillage.

## <a name="cd2dmeshoperator-id2d1mesh"></a><a name="operator_id2d1mesh_star"></a>CD2DMesh::opérateur ID2D1Mesh

Retourne l’interface ID2D1Mesh

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Mesh ou NULL si l’objet n’est pas encore initialisé.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
