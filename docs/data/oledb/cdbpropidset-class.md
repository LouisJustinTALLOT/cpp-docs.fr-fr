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
ms.openlocfilehash: a52d7443ab335e8546a4bcce03cf68c3b1d60e3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212015"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet, classe

Hérite de la structure `DBPROPIDSET` et ajoute un constructeur qui initialise les champs clés ainsi que la méthode d’accès [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) .

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Ajoute une propriété à l’ensemble d’ID de propriété.|
|[CDBPropIDSet](#cdbpropidset)|Constructeur.|
|[SetGUID](#setguid)|Définit le GUID de l’ID de propriété défini.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](#op_equal)|Attribue le contenu d’un ensemble d’ID de propriété à un autre.|

## <a name="remarks"></a>Notes

OLE DB consommateurs utilisent des structures `DBPROPIDSET` pour passer un tableau d’ID de propriété pour lequel le consommateur souhaite obtenir des informations de propriété. Les propriétés identifiées dans une structure [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) unique appartiennent à un jeu de propriétés.

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a>CDBPropIDSet :: AddPropertyID

Ajoute un ID de propriété à l’ID de propriété défini.

### <a name="syntax"></a>Syntaxe

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Paramètres

*propid*<br/>
dans ID de propriété à ajouter à l’ID de propriété défini.

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a>CDBPropIDSet :: CDBPropIDSet

Constructeur. Initialise les champs `rgProperties`, `cProperties`et (éventuellement) `guidPropertySet` de la structure [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
dans GUID utilisé pour initialiser le champ `guidPropertySet`.

*propidset*<br/>
dans Un autre objet `CDBPropIDSet` pour la construction de copie.

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a>CDBPropIDSet :: SetGUID

Définit le champ GUID dans la structure `DBPROPIDSET`.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
dans GUID utilisé pour définir le champ `guidPropertySet` de la structure [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="remarks"></a>Notes

Ce champ peut également être défini par le [constructeur](../../data/oledb/cdbpropidset-cdbpropidset.md) . Appelez cette fonction si vous utilisez le constructeur par défaut pour cette classe.

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a>CDBPropIDSet :: Operator =

Attribue le contenu d’un ID de propriété à un autre jeu de propriétés d’ID.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
