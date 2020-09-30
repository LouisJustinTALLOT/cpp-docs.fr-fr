---
title: ICommandPropertiesImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: bd4dd73c79085a2c2d85a5dbacbfd20bc920108e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501765"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl, classe

Fournit une implémentation de l’interface [ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de

*PropClass*<br/>
Votre classe de propriétés.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[GetProperties](#getproperties)|Retourne la liste des propriétés dans le groupe de propriétés rowset actuellement demandé pour l’ensemble de lignes.|
|[SetProperties](#setproperties)|Définit des propriétés dans le groupe de propriétés rowset.|

## <a name="remarks"></a>Remarques

Cela est obligatoire sur les commandes. L’implémentation est fournie par une fonction statique définie par la macro [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map) .

## <a name="icommandpropertiesimplgetproperties"></a><a name="getproperties"></a> Icommandpropertiesimpl, :: GetProperties

Retourne tous les jeux de propriétés demandés à l’aide du mappage des propriétés de la commande.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommandProperties :: GetProperties](/previous-versions/windows/desktop/ms723119(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Remarques

Voir [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map).

## <a name="icommandpropertiesimplsetproperties"></a><a name="setproperties"></a> Icommandpropertiesimpl, :: SetProperties

Définit les propriétés de l’objet de commande.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommandProperties :: SetProperties](/previous-versions/windows/desktop/ms711497(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
