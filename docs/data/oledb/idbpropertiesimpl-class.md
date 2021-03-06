---
description: 'En savoir plus sur : classe IDBPropertiesImpl'
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
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: e8384086de5b61422cd63e2dc3fbda0cfe040843
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317491"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl, classe

Fournit une implémentation pour l' `IDBProperties` interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IDBPropertiesImpl` .

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[GetProperties](#getproperties)|Retourne les valeurs des propriétés dans la source de données, les informations sur la source de données et les groupes de propriétés d’initialisation qui sont actuellement définis sur l’objet source de données ou les valeurs des propriétés dans le groupe de propriétés d’initialisation qui sont actuellement définies sur l’énumérateur.|
|[GetPropertyInfo](#getpropertyinfo)|Retourne des informations sur toutes les propriétés prises en charge par le fournisseur.|
|[SetProperties](#setproperties)|Définit les propriétés de la source de données et des groupes de propriétés d’initialisation, pour les objets de source de données ou le groupe de propriétés d’initialisation, pour les énumérateurs.|

## <a name="remarks"></a>Notes

[IDBProperties](/previous-versions/windows/desktop/ms719607(v=vs.85)) est une interface obligatoire pour les objets de source de données et une interface facultative pour les énumérateurs. Toutefois, si un énumérateur expose [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)), il doit exposer `IDBProperties` . `IDBPropertiesImpl` implémente à `IDBProperties` l’aide d’une fonction statique définie par [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map).

## <a name="idbpropertiesimplgetproperties"></a><a name="getproperties"></a> IDBPropertiesImpl :: GetProperties

Retourne les valeurs des propriétés dans la source de données, les informations sur la source de données et les groupes de propriétés d’initialisation qui sont actuellement définis sur l’objet source de données ou les valeurs des propriétés dans le groupe de propriétés d’initialisation qui sont actuellement définies sur l’énumérateur.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcProperties,
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>Paramètres

Pour plus d’informations, consultez [IDBProperties :: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

Certains paramètres correspondent à *OLE DB paramètres de référence du programmeur* de différents noms, qui sont décrits dans `IDBProperties::GetProperties` :

|Paramètres du modèle de OLE DB|Paramètres *de référence du programmeur OLE DB*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>Notes

Si le fournisseur est initialisé, cette méthode retourne les valeurs des propriétés dans le DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT groupes de propriétés qui sont actuellement définis sur l’objet source de données. Si le fournisseur n’est pas initialisé, il retourne uniquement les propriétés de groupe DBPROPSET_DBINIT.

## <a name="idbpropertiesimplgetpropertyinfo"></a><a name="getpropertyinfo"></a> IDBPropertiesImpl :: GetPropertyInfo

Retourne les informations sur les propriétés prises en charge par la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcPropertyInfoSets,
   DBPROPINFOSET ** prgPropertyInfoSets,
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>Paramètres

Consultez [IDBProperties :: GetPropertyInfo](/previous-versions/windows/desktop/ms718175(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

Certains paramètres correspondent à *OLE DB paramètres de référence du programmeur* de différents noms, qui sont décrits dans `IDBProperties::GetPropertyInfo` :

|Paramètres du modèle de OLE DB|Paramètres *de référence du programmeur OLE DB*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Notes

Utilise [IDBInitializeImpl :: m_pCUtlPropInfo](./idbinitializeimpl-class.md#pcutlpropinfo) pour implémenter cette fonctionnalité.

## <a name="idbpropertiesimplsetproperties"></a><a name="setproperties"></a> IDBPropertiesImpl :: SetProperties

Définit les propriétés de la source de données et des groupes de propriétés d’initialisation, pour les objets de source de données ou le groupe de propriétés d’initialisation, pour les énumérateurs.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Paramètres

Pour plus d’informations, consultez [IDBProperties :: SetProperties](/previous-versions/windows/desktop/ms723049(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Si le fournisseur est initialisé, cette méthode définit les valeurs des propriétés dans les groupes de propriétés DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT pour l’objet source de données. Si le fournisseur n’est pas initialisé, il définit DBPROPSET_DBINIT propriétés de groupe uniquement.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
