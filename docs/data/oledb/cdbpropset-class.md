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
ms.openlocfilehash: 1b94898cbe4a041ac1bb9a5d01c55380ee496106
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572173"
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
 *dwPropertyID*  
 [in] L’ID de la propriété à ajouter. Utilisé pour initialiser le `dwPropertyID` de la `DBPROP` structure ajouté au jeu de propriétés.  
  
 *var*  
 [in] Une variante permettant d’initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.  
  
 *szValue*  
 [in] Une chaîne utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.  
  
 *bValue*  
 [in] Un `BYTE` ou une valeur booléenne utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.  
  
 *%n%nValeur*  
 [in] Valeur entière utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.  
  
 *fltValue*  
 [in] Valeur à virgule flottante utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.  
  
 *dblValue*  
 [in] Une valeur à virgule flottante double précision utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.  
  
 *cyValue*  
 [in] Une valeur de devise CY utilisée pour initialiser la valeur de propriété pour le `DBPROP` structure ajouté au jeu de propriétés.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si la propriété a été ajoutée avec succès. Sinon, **false**. 

## <a name="cdbpropset"></a> CDBPropSet::CDBPropSet
Constructeur. Initialise le `rgProperties`, `cProperties`, et `guidPropertySet` champs de la [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) structure.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CDBPropSet(const GUID& guid);  

CDBPropSet(const CDBPropSet& propset);  

CDBPropSet();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *guid*  
 [in] GUID utilisé pour initialiser le `guidPropertySet` champ.  
  
 *propset*  
 [in] Un autre `CDBPropSet` objet pour la construction de copie.  

## <a name="setguid"></a> CDBPropSet::SetGUID
Définit le `guidPropertySet` champ dans le `DBPROPSET` structure.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *guid*  
 [in] Un GUID utilisé pour définir le `guidPropertySet` champ la [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) structure.  
  
### <a name="remarks"></a>Notes  
 Ce champ peut être défini le [constructeur](../../data/oledb/cdbpropset-cdbpropset.md) également.  

## <a name="op_equal"></a> CDBPropSet::operator =
Assigne le contenu d’une propriété définie sur un autre jeu de propriétés.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence de modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Cdbpropidset, classe](../../data/oledb/cdbpropidset-class.md)   
 [Structure DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))   
 [Structure DBPROP](/previous-versions/windows/desktop/ms717970\(v=vs.85\))