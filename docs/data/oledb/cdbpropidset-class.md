---
title: Cdbpropidset, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 111b5ea4f6c25aab2abc4897c9e4bda2a14362a9
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336938"
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
|[opérateur =](#op_equal)|Assigne le contenu d’une propriété ID définie à un autre.|  
  
## <a name="remarks"></a>Notes  
 Utilisation de consommateurs OLE DB `DBPROPIDSET` structures pour passer un tableau d’ID de propriété pour lequel le consommateur souhaite obtenir des informations de propriété. Les propriétés identifiées dans un seul [DBPROPIDSET](https://msdn.microsoft.com/library/ms717981.aspx) structure appartiennent à une propriété est définie.  

## <a name="addpropertyid"></a> CDBPropIDSet::AddPropertyID
Ajoute un ID de propriété à l’ensemble d’ID de propriété.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
bool AddPropertyID(DBPROPID propid) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ID de propriété*  
 [in] Définir l’ID de propriété à ajouter à l’ID de propriété.  

## <a name="cdbpropidset"></a> CDBPropIDSet::CDBPropIDSet
Constructeur. Initialise le `rgProperties`, `cProperties`et (éventuellement) `guidPropertySet` champs de la [DBPROPIDSET](https://msdn.microsoft.com/library/ms717981.aspx) structure.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CDBPropIDSet(const GUID& guid);  

CDBPropIDSet(const CDBPropIDSet& propidset);  

CDBPropIDSet();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *guid*  
 [in] GUID utilisé pour initialiser le `guidPropertySet` champ.  
  
 *propidset*  
 [in] Un autre `CDBPropIDSet` objet pour la construction de copie.  

## <a name="setguid"></a> CDBPropIDSet::SetGUID
Définit le champ GUID dans le `DBPROPIDSET` structure.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *guid*  
 [in] Un GUID utilisé pour définir le `guidPropertySet` champ la [DBPROPIDSET](https://msdn.microsoft.com/library/ms717981.aspx) structure.  
  
### <a name="remarks"></a>Notes  
 Ce champ peut être défini le [constructeur](../../data/oledb/cdbpropidset-cdbpropidset.md) également. Appelez cette fonction si vous utilisez le constructeur par défaut pour cette classe.  

## <a name="op_equal"></a> CDBPropIDSet::operator =
Assigne le contenu d’une propriété ID est défini à un autre jeu de propriétés d’ID.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)