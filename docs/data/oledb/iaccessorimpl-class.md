---
title: IAccessorImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: 356278b316912bdb81f1c43bbf2034f00ec3d785
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845612"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl, classe

Fournit une implémentation de l’interface [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe d’objet Rowset ou Command.

*BindType*<br/>
Unité de stockage pour les informations de liaison. La valeur par défaut est la `ATLBINDINGS` structure (consultez Atldb. h).

*BindingVector*<br/>
Unité de stockage pour les informations de colonne. La valeur par défaut est [CAtlMap](../../atl/reference/catlmap-class.md) où l’élément Key est une valeur hAccessor et l’élément value est un pointeur vers une `BindType` structure.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[IAccessorImpl](#iaccessorimpl)|Constructeur.|

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[AddRefAccessor](#addrefaccessor)|Ajoute un décompte de références à un accesseur existant.|
|[CreateAccessor](#createaccessor)|Crée un accesseur à partir d'un jeu de liaisons.|
|[GetBindings](#getbindings)|Retourne les liaisons dans un accesseur.|
|[ReleaseAccessor](#releaseaccessor)|Libère un accesseur.|

## <a name="remarks"></a>Notes

Cela est obligatoire sur les ensembles de lignes et les commandes. OLE DB exige que les fournisseurs implémentent un HACCESSOR, qui est une balise d’un tableau de structures [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) . Les HACCESSORs fournis par `IAccessorImpl` sont des adresses des `BindType` structures. Par défaut, `BindType` est défini en tant `ATLBINDINGS` que `IAccessorImpl` définition de modèle dans. `BindType` fournit un mécanisme utilisé par `IAccessorImpl` pour suivre le nombre d’éléments dans son `DBBINDING` tableau, ainsi qu’un décompte de références et des indicateurs d’accesseur.

## <a name="iaccessorimpliaccessorimpl"></a><a name="iaccessorimpl"></a> IAccessorImpl :: IAccessorImpl

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
IAccessorImpl();
```

## <a name="iaccessorimpladdrefaccessor"></a><a name="addrefaccessor"></a> IAccessorImpl :: AddRefAccessor

Ajoute un décompte de références à un accesseur existant.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Paramètres

Consultez [IAccessor :: AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="iaccessorimplcreateaccessor"></a><a name="createaccessor"></a> IAccessorImpl :: CreateAccessor

Crée un accesseur à partir d'un jeu de liaisons.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [IAccessor :: CreateAccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="iaccessorimplgetbindings"></a><a name="getbindings"></a> IAccessorImpl :: GetBindings

Retourne les liaisons de colonnes de base à partir du consommateur dans un accesseur.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Paramètres

Consultez [IAccessor :: GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="iaccessorimplreleaseaccessor"></a><a name="releaseaccessor"></a> IAccessorImpl :: ReleaseAccessor

Libère un accesseur.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Paramètres

Consultez [IAccessor :: ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
