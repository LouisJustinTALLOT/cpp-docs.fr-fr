---
title: CDBPropIDSet, classe
ms.date: 11/04/2016
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
- CDBPropIDSet.AddPropertyID
- CDBPropIDSet::AddPropertyID
- AddPropertyID
- ATL.CDBPropIDSet.AddPropertyID
- ATL::CDBPropIDSet::AddPropertyID
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
ms.openlocfilehash: 24cc621e522ed1939fe3127d97e8d54b75fa1618
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838293"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet, classe

Hérite de la `DBPROPIDSET` structure et ajoute un constructeur qui initialise les champs clés ainsi que la méthode d’accès [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) .

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[AddPropertyID](#addpropertyid)|Ajoute une propriété à l’ensemble d’ID de propriété.|
|[CDBPropIDSet](#cdbpropidset)|Constructeur.|
|[SetGUID](#setguid)|Définit le GUID de l’ID de propriété défini.|

### <a name="operators"></a>Opérateurs

| Nom | Description |
|-|-|
|[opérateur =](#op_equal)|Attribue le contenu d’un ensemble d’ID de propriété à un autre.|

## <a name="remarks"></a>Notes

OLE DB consommateurs utilisent des `DBPROPIDSET` structures pour passer un tableau d’ID de propriété pour lequel le consommateur souhaite obtenir des informations de propriété. Les propriétés identifiées dans une structure [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) unique appartiennent à un jeu de propriétés.

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a> CDBPropIDSet :: AddPropertyID

Ajoute un ID de propriété à l’ID de propriété défini.

### <a name="syntax"></a>Syntaxe

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Paramètres

*propid*<br/>
dans ID de propriété à ajouter à l’ID de propriété défini.

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a> CDBPropIDSet :: CDBPropIDSet

Constructeur. Initialise les `rgProperties` champs, `cProperties` et (éventuellement) `guidPropertySet` de la structure [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
dans GUID utilisé pour initialiser le `guidPropertySet` champ.

*propidset*<br/>
dans Autre `CDBPropIDSet` objet pour la construction de copie.

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a> CDBPropIDSet :: SetGUID

Définit le champ GUID dans la `DBPROPIDSET` structure.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
dans GUID utilisé pour définir le `guidPropertySet` champ de la structure [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="remarks"></a>Notes

Ce champ peut également être défini par le [constructeur](../../data/oledb/cdbpropidset-cdbpropidset.md) . Appelez cette fonction si vous utilisez le constructeur par défaut pour cette classe.

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a> CDBPropIDSet :: Operator =

Attribue le contenu d’un ID de propriété à un autre jeu de propriétés d’ID.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
