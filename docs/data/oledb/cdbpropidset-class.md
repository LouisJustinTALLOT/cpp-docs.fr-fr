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
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
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
ms.openlocfilehash: 9e878af3acf4c4d3a6ca785454c4bb072f17cf09
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022409"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet, classe

Hérite de la `DBPROPIDSET` structurer et ajoute un constructeur qui initialise les champs clés, ainsi que les [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) accéder à la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Ajoute une propriété à l’ensemble d’ID de propriété.|
|[CDBPropIDSet](#cdbpropidset)|Constructeur.|
|[SetGUID](#setguid)|Définit le GUID de l’ID de propriété de jeu.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator =](#op_equal)|Assigne le contenu d’une propriété ID définie à un autre.|

## <a name="remarks"></a>Notes

Utilisation de consommateurs OLE DB `DBPROPIDSET` structures pour passer un tableau d’ID de propriété pour lequel le consommateur souhaite obtenir des informations de propriété. Les propriétés identifiées dans un seul [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) structure appartiennent à une propriété est définie.

## <a name="addpropertyid"></a> CDBPropIDSet::AddPropertyID

Ajoute un ID de propriété à l’ensemble d’ID de propriété.

### <a name="syntax"></a>Syntaxe

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Paramètres

*propid*<br/>
[in] Définir l’ID de propriété à ajouter à l’ID de propriété.

## <a name="cdbpropidset"></a> CDBPropIDSet::CDBPropIDSet

Constructeur. Initialise le `rgProperties`, `cProperties`et (éventuellement) `guidPropertySet` champs de la [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) structure.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
[in] GUID utilisé pour initialiser le `guidPropertySet` champ.

*propidset*<br/>
[in] Un autre `CDBPropIDSet` objet pour la construction de copie.

## <a name="setguid"></a> CDBPropIDSet::SetGUID

Définit le champ GUID dans le `DBPROPIDSET` structure.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
[in] Un GUID utilisé pour définir le `guidPropertySet` champ la [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) structure.

### <a name="remarks"></a>Notes

Ce champ peut être défini le [constructeur](../../data/oledb/cdbpropidset-cdbpropidset.md) également. Appelez cette fonction si vous utilisez le constructeur par défaut pour cette classe.

## <a name="op_equal"></a> CDBPropIDSet::operator =

Assigne le contenu d’une propriété ID est défini à un autre jeu de propriétés d’ID.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)