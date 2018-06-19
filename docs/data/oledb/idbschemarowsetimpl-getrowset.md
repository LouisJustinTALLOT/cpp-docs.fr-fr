---
title: IDBSchemaRowsetImpl::GetRowset | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
dev_langs:
- C++
helpviewer_keywords:
- GetRowset method
ms.assetid: 3ae28c22-e186-4a15-8591-b0192e784a6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ec479809bf95d4a88338401013b7f5980b703d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103747"
---
# <a name="idbschemarowsetimplgetrowset"></a>IDBSchemaRowsetImpl::GetRowset
Retourne un ensemble de lignes de schéma.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetRowset)(IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pUnkOuter`  
 [in] **IUnknown** externe pendant l’agrégation ; sinon, **NULL**.  
  
 `rguidSchema`  
 [in] Référence au GUID d’ensemble de lignes de schéma demandé (par exemple, `DBSCHEMA_TABLES`).  
  
 `cRestrictions`  
 [in] Nombre de restrictions à appliquer à l’ensemble de lignes.  
  
 `rgRestrictions`  
 [in] Tableau d’objets `cRestrictions`**VARIANT**qui représentent les restrictions.  
  
 `riid`  
 [in] IID associé à la demande portant sur l’ensemble de lignes de schéma nouvellement créé.  
  
 `cPropertySets`  
 [in] Nombre de sets de propriétés à définir.  
  
 `rgPropertySets`  
 [in/out] Tableau de structures [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) à définir sur l’ensemble de lignes de schéma nouvellement créé.  
  
 `ppRowset`  
 [out] Pointeur désignant l’interface demandée sur l’ensemble de lignes de schéma nouvellement créé.  
  
## <a name="remarks"></a>Notes  
 Cette méthode impose à l’utilisateur de disposer d’un mappage de schéma dans la classe session. À partir des informations de mappage de schéma, `GetRowset` crée un objet rowset donné si le paramètre `rguidSchema` est égal à l’un des GUID d’entrée de mappage. Consultez [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) pour obtenir une description de l’entrée de mappage.  
  
 Consultez [IDBSchemaRowset::GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx) dans le Kit de développement logiciel Windows.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IDBSchemaRowsetImpl (classe)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Membres IDBSchemaRowsetImpl (classe)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)   
 [Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)