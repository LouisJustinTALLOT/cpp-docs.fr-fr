---
title: IDBPropertiesImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: 13c41b97190ff13b87361b6e8344b8f17798708a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413340"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl, classe

Fournit une implémentation pour le `IDBProperties` interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IDBPropertiesImpl`.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d’interface

|||
|-|-|
|[GetProperties](#getproperties)|Retourne les valeurs des propriétés dans les groupes de propriétés de Source de données, sources de données et d’initialisation qui sont actuellement définies sur l’objet de source de données ou les valeurs des propriétés dans le groupe de propriétés d’initialisation qui sont actuellement définies sur le énumérateur.|
|[GetPropertyInfo](#getpropertyinfo)|Retourne des informations sur toutes les propriétés prises en charge par le fournisseur.|
|[SetProperties](#setproperties)|Définit les propriétés dans les groupes de propriétés de Source de données et d’initialisation, pour les objets de source de données, ou le groupe de propriétés d’initialisation pour les énumérateurs.|

## <a name="remarks"></a>Notes

[IDBProperties](/previous-versions/windows/desktop/ms719607(v=vs.85)) est une interface obligatoire pour les objets de source de données et une interface facultative pour les énumérateurs. Toutefois, si un énumérateur expose [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)), elle doit exposer `IDBProperties`. `IDBPropertiesImpl` implémente `IDBProperties` à l’aide d’une fonction statique définie par [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="getproperties"></a> IDBPropertiesImpl::GetProperties

Retourne les valeurs des propriétés dans les groupes de propriétés de Source de données, sources de données et d’initialisation qui sont actuellement définies sur l’objet de source de données ou les valeurs des propriétés dans le groupe de propriétés d’initialisation qui sont actuellement définies sur le énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcProperties,
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>Paramètres

Consultez [IDBProperties::GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) dans le *de référence du programmeur OLE DB*.

Certains paramètres correspondent aux *de référence du programmeur OLE DB* des noms différents, qui sont décrites dans les paramètres `IDBProperties::GetProperties`:

|Paramètres de modèle OLE DB|*Référence du programmeur OLE DB* paramètres|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>Notes

Si le fournisseur est initialisé, cette méthode retourne les valeurs des propriétés dans le DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO, les groupes de propriétés DBPROPSET_DBINIT qui sont actuellement définies sur l’objet de source de données. Si le fournisseur n’est pas initialisé, elle retourne uniquement les propriétés de groupe DBPROPSET_DBINIT.

## <a name="getpropertyinfo"></a> IDBPropertiesImpl::GetPropertyInfo

Retourne des informations de propriété pris en charge par la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcPropertyInfoSets,
   DBPROPINFOSET ** prgPropertyInfoSets,
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>Paramètres

Consultez [IDBProperties::GetPropertyInfo](/previous-versions/windows/desktop/ms718175(v=vs.85)) dans le *de référence du programmeur OLE DB*.

Certains paramètres correspondent aux *de référence du programmeur OLE DB* des noms différents, qui sont décrites dans les paramètres `IDBProperties::GetPropertyInfo`:

|Paramètres de modèle OLE DB|*Référence du programmeur OLE DB* paramètres|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Notes

Utilise [IDBInitializeImpl::m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) pour implémenter cette fonctionnalité.

## <a name="setproperties"></a> IDBPropertiesImpl::SetProperties

Définit les propriétés dans les groupes de propriétés de Source de données et d’initialisation, pour les objets de source de données, ou le groupe de propriétés d’initialisation pour les énumérateurs.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [IDBProperties::SetProperties](/previous-versions/windows/desktop/ms723049(v=vs.85)) dans le *de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Si le fournisseur est initialisé, cette méthode définit les valeurs des propriétés dans le DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO, groupes de propriétés DBPROPSET_DBINIT pour l’objet de source de données. Si le fournisseur n’est pas initialisé, elle définit uniquement les propriétés de groupe DBPROPSET_DBINIT.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)