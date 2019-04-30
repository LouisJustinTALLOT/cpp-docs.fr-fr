---
title: IRowsetInfoImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: b42ecf6c03dd1023d1ba150d579f77c4bae8998a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390722"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl, classe

Fournit une implémentation pour le [IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IRowsetInfoImpl`.

*PropClass*<br/>
Une classe de propriété définis par l’utilisateur par défaut est *T*.

## <a name="requirements"></a>Configuration requise

**En-tête :** altdb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d’interface

|||
|-|-|
|[GetProperties](#getproperties)|Retourne les paramètres actuels de toutes les propriétés prises en charge par l’ensemble de lignes.|
|[GetReferencedRowset](#getreferencedrowset)|Retourne un pointeur d’interface pour l’ensemble de lignes auquel s’applique un signet.|
|[GetSpecification](#getspecification)|Retourne un pointeur d’interface sur l’objet (commande ou session) qui a créé cet ensemble de lignes.|

## <a name="remarks"></a>Notes

Une interface obligatoire sur les ensembles de lignes. Cette classe implémente les propriétés de l’ensemble de lignes à l’aide de la [mappage de jeu de propriétés](../../data/oledb/begin-propset-map.md) définies dans votre classe de commande. Bien que la classe d’ensemble de lignes s’affiche à l’utilisation de propriété de la classe de commande définit, l’ensemble de lignes est fourni avec sa propre copie des propriétés d’exécution, lorsqu’il est créé par un objet de commande ou session.

## <a name="getproperties"></a> IRowsetInfoImpl::GetProperties

Retourne les paramètres actuels pour les propriétés de le `DBPROPSET_ROWSET` groupe.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetInfo::GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="getreferencedrowset"></a> IRowsetInfoImpl::GetReferencedRowset

Retourne un pointeur d’interface pour l’ensemble de lignes auquel s’applique un signet.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetInfo::GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) dans le *de référence du programmeur OLE DB*. Le *iOrdinal* paramètre doit être une colonne de signet.

## <a name="getspecification"></a> IRowsetInfoImpl::GetSpecification

Retourne un pointeur d’interface sur l’objet (commande ou session) qui a créé cet ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetInfo::GetSpecification](/previous-versions/windows/desktop/ms716746(v=vs.85)) dans le *de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Utilisez cette méthode avec [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md) pour récupérer des propriétés de l’objet de source de données.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)