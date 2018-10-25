---
title: CDBPropSet, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- SetGUID
- CDBPropSet::SetGUID
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a047416c22eb57fc3ee3d3eb6a69275768182525
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081899"
---
# <a name="cdbpropset-class"></a>CDBPropSet, classe

Hérite de la `DBPROPSET` structurer et ajoute un constructeur qui initialise les champs clés, ainsi que les `AddProperty` accéder à la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddProperty](#addproperty)|Ajoute une propriété au jeu de propriétés.|
|[CDBPropSet](#cdbpropset)|Constructeur.|
|[SetGUID](#setguid)|Définit le `guidPropertySet` champ la `DBPROPSET` structure.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](#op_equal)|Assigne le contenu d’une propriété définie sur un autre.|

## <a name="remarks"></a>Notes

Utilisation de fournisseurs et consommateurs OLE DB `DBPROPSET` structures pour passer des tableaux de `DBPROP` structures. Chaque `DBPROP` structure représente une propriété unique qui peut être définie.

## <a name="addproperty"></a> CDBPropSet::AddProperty

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
[in] L’ID de la propriété à ajouter. Utilisé pour initialiser le `dwPropertyID` de la `DBPROP` structure ajouté au jeu de propriétés.

*var*<br/>
[in] Une variante permettant d’initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.

*szValue*<br/>
[in] Une chaîne utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.

*bValue*<br/>
[in] Un `BYTE` ou une valeur booléenne utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.

*%n%nValeur*<br/>
[in] Valeur entière utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.

*fltValue*<br/>
[in] Valeur à virgule flottante utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.

*dblValue*<br/>
[in] Une valeur à virgule flottante double précision utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.

*cyValue*<br/>
[in] Une valeur de devise CY utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.

### <a name="return-value"></a>Valeur de retour

**true** si la propriété a été ajoutée avec succès. Sinon, **false**.

## <a name="cdbpropset"></a> CDBPropSet::CDBPropSet

Constructeur. Initialise le `rgProperties`, `cProperties`, et `guidPropertySet` champs de la [DBPROPSET](/previous-versions/windows/desktop/ms714367) structure.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
[in] GUID utilisé pour initialiser le `guidPropertySet` champ.

*propset*<br/>
[in] Un autre `CDBPropSet` objet pour la construction de copie.

## <a name="setguid"></a> CDBPropSet::SetGUID

Définit le `guidPropertySet` champ dans le `DBPROPSET` structure.

### <a name="syntax"></a>Syntaxe

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
[in] Un GUID utilisé pour définir le `guidPropertySet` champ la [DBPROPSET](/previous-versions/windows/desktop/ms714367) structure.

### <a name="remarks"></a>Notes

Ce champ peut être défini le [constructeur](../../data/oledb/cdbpropset-cdbpropset.md) également.

## <a name="op_equal"></a> CDBPropSet::operator =

Assigne le contenu d’une propriété définie sur un autre jeu de propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet, classe](../../data/oledb/cdbpropidset-class.md)<br/>
[Structure DBPROPSET](/previous-versions/windows/desktop/ms714367)
[Structure DBPROP](/previous-versions/windows/desktop/ms717970)