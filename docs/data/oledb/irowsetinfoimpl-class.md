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
ms.openlocfilehash: 7389ba689fb1f371b5fbf73045dcdc78cd465d88
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446188"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl, classe

Fournit une implémentation pour l’interface [IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) .

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
Classe de propriété définissable par l’utilisateur qui A par défaut la valeur *T*.

## <a name="requirements"></a>Spécifications

**En-tête :** altdb. h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

|||
|-|-|
|[GetProperties](#getproperties)|Retourne les paramètres actuels de toutes les propriétés prises en charge par le jeu de lignes.|
|[GetReferencedRowset](#getreferencedrowset)|Retourne un pointeur d’interface vers l’ensemble de lignes auquel un signet s’applique.|
|[GetSpecification](#getspecification)|Retourne un pointeur d'interface sur l'objet (commande ou session) qui a créé ce jeu de lignes.|

## <a name="remarks"></a>Notes

Interface obligatoire sur les ensembles de lignes. Cette classe implémente les propriétés de l’ensemble de lignes à l’aide du [mappage de jeu de propriétés](../../data/oledb/begin-propset-map.md) défini dans votre classe de commande. Bien que la classe d’ensemble de lignes semble utiliser les jeux de propriétés de la classe de commande, l’ensemble de lignes est fourni avec sa propre copie des propriétés au moment de l’exécution, lorsqu’il est créé par un objet de commande ou de session.

## <a name="getproperties"></a>IRowsetInfoImpl :: GetProperties

Retourne les paramètres actuels des propriétés dans le groupe de `DBPROPSET_ROWSET`.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetInfo :: GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="getreferencedrowset"></a>IRowsetInfoImpl :: GetReferencedRowset

Retourne un pointeur d’interface vers l’ensemble de lignes auquel un signet s’applique.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetInfo :: GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*. Le paramètre *iOrdinal* doit être une colonne de signets.

## <a name="getspecification"></a>IRowsetInfoImpl :: GetSpecification

Retourne un pointeur d'interface sur l'objet (commande ou session) qui a créé ce jeu de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetInfo :: GetSpecification](/previous-versions/windows/desktop/ms716746(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Utilisez cette méthode avec [igetdatasourceimpl,](../../data/oledb/igetdatasourceimpl-class.md) pour récupérer les propriétés de l’objet source de données.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)