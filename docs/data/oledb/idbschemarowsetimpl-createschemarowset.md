---
title: IDBSchemaRowsetImpl::CreateSchemaRowset | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateSchemaRowset method
ms.assetid: ad3e3e4d-45b9-461c-b7b8-3af6843631b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 90a942fc92faf3066669b46fd825ad2eae393f43
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103994"
---
# <a name="idbschemarowsetimplcreateschemarowset"></a>IDBSchemaRowsetImpl::CreateSchemaRowset
Implémente une fonction du créateur d’objet COM pour l’objet spécifié par le paramètre de modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template template <class SchemaRowsetClass>  
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   SchemaRowsetClass*& pSchemaRowset);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pUnkOuter`  
 [in] [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) externe pendant l’agrégation ; sinon, **NULL**.  
  
 `cRestrictions`  
 [in] Nombre de restrictions appliquées à l’ensemble de lignes du schéma.  
  
 `rgRestrictions`  
 [in] Tableau de `cRestrictions`**s de**à appliquer à l’ensemble de lignes.  
  
 `riid`  
 [in] Interface [QueryInterface](../../atl/queryinterface.md) pour le **IUnknown**de sortie.  
  
 `cPropertySets`  
 [in] Nombre de sets de propriétés à définir.  
  
 `rgPropertySets`  
 [in] Tableau de structures [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) qui spécifient les propriétés définies.  
  
 `ppRowset`  
 [out] **IUnknown** sortant demandé par `riid`. Ce **IUnknown** est une interface sur l’objet d’ensemble de lignes du schéma.  
  
 `pSchemaRowset`  
 [out] Pointeur vers une instance de la classe d’ensemble de lignes du schéma. Ce paramètre n’est généralement pas utilisé, mais il peut l’être si vous devez effectuer des tâches supplémentaires sur l’ensemble de lignes du schéma avant de le passer à un objet COM. La durée de vie de `pSchemaRowset` est limitée par `ppRowset`.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Cette fonction implémente un créateur générique pour tous les types d’ensembles de lignes du schéma. En règle générale, l’utilisateur n’appelle pas cette fonction. Elle est appelée par l’implémentation du mappage de schéma.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IDBSchemaRowsetImpl (classe)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Membres IDBSchemaRowsetImpl (classe)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)