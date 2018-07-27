---
title: IAccessorImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
dev_langs:
- C++
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ac22d8ee45209ad6a20dcb34a75c06dd9b80b58
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269886"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl, classe
Fournit une implémentation de la [IAccessor](https://msdn.microsoft.com/library/ms719672.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, 
          class BindType = ATLBINDINGS,
          class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe d’objet ensemble de lignes ou de la commande.  
  
 *BindType*  
 Unité de stockage pour les informations de liaison. La valeur par défaut est le `ATLBINDINGS` structure (consultez atldb.h).  
  
 *BindingVector*  
 Unité de stockage pour les informations de colonne. La valeur par défaut est [CAtlMap](../../atl/reference/catlmap-class.md) où l’élément clé est une valeur HACCESSOR et l’élément de la valeur est un pointeur vers un `BindType` structure.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  

## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[IAccessorImpl](#iaccessorimpl)|Constructeur.|  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[AddRefAccessor](#addrefaccessor)|Ajoute un décompte de références à un accesseur existant.|  
|[CreateAccessor](#createaccessor)|Crée un accesseur à partir d’un jeu de liaisons.|  
|[GetBindings](#getbindings)|Retourne les liaisons dans un accesseur.|  
|[ReleaseAccessor](#releaseaccessor)|Libère un accesseur.|  
  
## <a name="remarks"></a>Notes  
 Ce champ est obligatoire sur les ensembles de lignes et de commandes. OLE DB requiert des fournisseurs implémenter un HACCESSOR, qui est une balise à un tableau de [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) structures. HACCESSORs fournis par `IAccessorImpl` sont des adresses de la `BindType` structures. Par défaut, `BindType` est défini comme un `ATLBINDINGS` dans `IAccessorImpl`de définition de modèle. `BindType` fournit un mécanisme utilisé par `IAccessorImpl` pour suivre le nombre d’éléments dans son `DBBINDING` ainsi que d’un nombre et accesseur des indicateurs de référence de tableau.  

## <a name="iaccessorimpl"></a> IAccessorImpl::IAccessorImpl
Constructeur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
IAccessorImpl();  
  
```  

## <a name="addrefaccessor"></a> IAccessorImpl::AddRefAccessor
Ajoute un décompte de références à un accesseur existant.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IAccessor::AddRefAccessor](https://msdn.microsoft.com/library/ms714978.aspx) dans le *de référence du programmeur OLE DB*.

## <a name="createaccessor"></a> IAccessorImpl::CreateAccessor
Crée un accesseur à partir d’un jeu de liaisons.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,  
   DBCOUNTITEM cBindings,  
   const DBBINDING rgBindings[],  
   DBLENGTH cbRowSize,  
   HACCESSOR* phAccessor,  
   DBBINDSTATUS rgStatus[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IAccessor::CreateAccessor](https://msdn.microsoft.com/library/ms720969.aspx) dans le *de référence du programmeur OLE DB*.  

## <a name="getbindings"></a> IAccessorImpl::GetBindings
Retourne les liaisons de colonnes de base du consommateur dans un accesseur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(GetBindings)(HACCESSOR hAccessor,  
   DBACCESSORFLAGS* pdwAccessorFlags,  
   DBCOUNTITEM* pcBindings,  
   DBBINDING** prgBindings);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IAccessor::GetBindings](https://msdn.microsoft.com/library/ms721253.aspx) dans le *de référence du programmeur OLE DB*. 

## <a name="releaseaccessor"></a> IAccessorImpl::ReleaseAccessor
Libère un accesseur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IAccessor::ReleaseAccessor](https://msdn.microsoft.com/library/ms719717.aspx) dans le *de référence du programmeur OLE DB*.
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
