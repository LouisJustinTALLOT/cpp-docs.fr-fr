---
description: 'En savoir plus sur : classe Icommandpropertiesimpl,'
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
ms.openlocfilehash: bf6a6f9a3ddd43a61671a85a791d63958f63c3e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317561"
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

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[GetProperties](#getproperties)|Retourne la liste des propriétés dans le groupe de propriétés rowset actuellement demandé pour l’ensemble de lignes.|
|[SetProperties](#setproperties)|Définit des propriétés dans le groupe de propriétés rowset.|

## <a name="remarks"></a>Notes

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

### <a name="remarks"></a>Notes

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
