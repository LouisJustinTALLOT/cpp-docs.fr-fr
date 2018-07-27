---
title: Irowsetinfoimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ccf4d6b34362d4c8b7875319af444f755d741e7
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322034"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl, classe
Fournit une implémentation pour le [IRowsetInfo](https://msdn.microsoft.com/library/ms724541.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `IRowsetInfoImpl`.  
  
 *PropClass*  
 Une classe de propriété définis par l’utilisateur par défaut est *T*. 

## <a name="requirements"></a>Configuration requise  
 **En-tête :** altdb.h   
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|Retourne les paramètres actuels de toutes les propriétés prises en charge par l’ensemble de lignes.|  
|[GetReferencedRowset](#getreferencedrowset)|Retourne un pointeur d’interface pour l’ensemble de lignes auquel s’applique un signet.|  
|[GetSpecification](#getspecification)|Retourne un pointeur d’interface sur l’objet (commande ou session) qui a créé cet ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 Une interface obligatoire sur les ensembles de lignes. Cette classe implémente les propriétés de l’ensemble de lignes à l’aide de la [mappage de jeu de propriétés](../../data/oledb/begin-propset-map.md) définies dans votre classe de commande. Bien que la classe d’ensemble de lignes s’affiche à l’utilisation de propriété de la classe de commande définit, l’ensemble de lignes est fourni avec sa propre copie des propriétés d’exécution, lorsqu’il est créé par un objet de commande ou session.  
  
## <a name="getproperties"></a> IRowsetInfoImpl::GetProperties
Retourne les paramètres actuels pour les propriétés de le `DBPROPSET_ROWSET` groupe.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,  
   const DBPROPIDSET rgPropertyIDSets[],  
   ULONG* pcPropertySets,  
   DBPROPSET** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetInfo::GetProperties](https://msdn.microsoft.com/library/ms719611.aspx) dans le *de référence du programmeur OLE DB*. 

## <a name="getreferencedrowset"></a> IRowsetInfoImpl::GetReferencedRowset
Retourne un pointeur d’interface pour l’ensemble de lignes auquel s’applique un signet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,  
   REFIID riid,  
   IUnknown** ppReferencedRowset);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetInfo::GetReferencedRowset](https://msdn.microsoft.com/library/ms721145.aspx) dans le *de référence du programmeur OLE DB*. Le *iOrdinal* paramètre doit être une colonne de signet. 

## <a name="getspecification"></a> IRowsetInfoImpl::GetSpecification
Retourne un pointeur d’interface sur l’objet (commande ou session) qui a créé cet ensemble de lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetSpecification )(REFIID riid,  
   IUnknown** ppSpecification);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IRowsetInfo::GetSpecification](https://msdn.microsoft.com/library/ms716746.aspx) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode avec [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md) pour récupérer des propriétés de l’objet de source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
