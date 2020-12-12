---
description: 'En savoir plus sur : classe CDBPropSet'
title: CDBPropSet, classe
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: 3c1695e16f050866c2df5725cec4a716c04b3093
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170813"
---
# <a name="cdbpropset-class"></a>CDBPropSet, classe

Hérite de la `DBPROPSET` structure et ajoute un constructeur qui initialise les champs clés ainsi que la `AddProperty` méthode d’accès.

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[AddProperty](#addproperty)|Ajoute une propriété au jeu de propriétés.|
|[CDBPropSet](#cdbpropset)|Constructeur.|
|[SetGUID](#setguid)|Définit le `guidPropertySet` champ de la `DBPROPSET` structure.|

### <a name="operators"></a>Opérateurs

| Nom | Description |
|-|-|
|[opérateur =](#op_equal)|Assigne le contenu d’une propriété définie à une autre.|

## <a name="remarks"></a>Notes

Les fournisseurs de OLE DB et les consommateurs utilisent `DBPROPSET` des structures pour passer des tableaux de `DBPROP` structures. Chaque `DBPROP` structure représente une propriété unique qui peut être définie.

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a> CDBPropSet :: AddProperty

Ajoute une propriété au jeu de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>Paramètres

*dwPropertyID*<br/>
dans ID de la propriété à ajouter. Utilisé pour initialiser le `dwPropertyID` de la `DBPROP` structure ajoutée au jeu de propriétés.

*var*<br/>
dans Variant utilisé pour initialiser la valeur de la propriété de la `DBPROP` structure ajoutée au jeu de propriétés.

*szValue*<br/>
dans Chaîne utilisée pour initialiser la valeur de la propriété de la `DBPROP` structure ajoutée au jeu de propriétés.

*bValue*<br/>
dans `BYTE` Valeur booléenne ou utilisée pour initialiser la valeur de la propriété de la `DBPROP` structure ajoutée au jeu de propriétés.

*nValeur*<br/>
dans Valeur entière utilisée pour initialiser la valeur de la propriété de la `DBPROP` structure ajoutée au jeu de propriétés.

*fltValue*<br/>
dans Valeur à virgule flottante utilisée pour initialiser la valeur de propriété de la `DBPROP` structure ajoutée au jeu de propriétés.

*dblValue*<br/>
dans Valeur à virgule flottante double précision utilisée pour initialiser la valeur de propriété de la `DBPROP` structure ajoutée au jeu de propriétés.

*cyValue*<br/>
dans Valeur de devise CY utilisée pour initialiser la valeur de la propriété de la `DBPROP` structure ajoutée au jeu de propriétés.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la propriété a été correctement ajoutée. Sinon, **`false`** .

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a> CDBPropSet :: CDBPropSet

Constructeur. Initialise les `rgProperties` champs, `cProperties` et `guidPropertySet` de la structure [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) .

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
dans GUID utilisé pour initialiser le `guidPropertySet` champ.

*propset*<br/>
dans Autre `CDBPropSet` objet pour la construction de copie.

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a> CDBPropSet :: SetGUID

Définit le `guidPropertySet` champ dans la `DBPROPSET` structure.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
dans GUID utilisé pour définir le `guidPropertySet` champ de la structure [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) .

### <a name="remarks"></a>Notes

Ce champ peut également être défini par le [constructeur](#cdbpropset) .

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a> CDBPropSet :: Operator =

Assigne le contenu d’une propriété à un autre jeu de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet, classe](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET, structure](/previous-versions/windows/desktop/ms714367(v=vs.85)) 
 [DBPROP, structure](/previous-versions/windows/desktop/ms717970(v=vs.85))
