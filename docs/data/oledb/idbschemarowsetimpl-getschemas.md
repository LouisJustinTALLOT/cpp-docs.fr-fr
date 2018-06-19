---
title: IDBSchemaRowsetImpl::GetSchemas | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
dev_langs:
- C++
helpviewer_keywords:
- GetSchemas method
ms.assetid: fbe725a6-3acd-45f8-bcaf-10a6c1239cd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 886b3ea82d8eb0193207438ce7c5a4fc51981cbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103305"
---
# <a name="idbschemarowsetimplgetschemas"></a>IDBSchemaRowsetImpl::GetSchemas
Retourne une liste d’ensembles de lignes de schéma accessibles par [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetSchema s )(ULONG * pcSchemas,  
   GUID ** prgSchemas,  
   ULONG** prgRest);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pcSchemas*  
 [out] Pointeur désignant un **ULONG** complété du nombre de schémas.  
  
 *prgSchemas*  
 [out] Pointeur désignant un tableau de GUID complété d’un pointeur désignant un tableau de GUID d’ensembles de lignes de schéma.  
  
 *prgRest*  
 [out] Pointeur désignant un tableau de **ULONG**qui doit être complété du tableau de restrictions.  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un tableau de tous les ensembles de lignes de schéma pris en charge par le fournisseur. Consultez [IDBSchemaRowset::GetSchemas](https://msdn.microsoft.com/en-us/library/ms719605.aspx) dans le Kit de développement logiciel Windows.  
  
 L’implémentation de cette fonction impose à l’utilisateur de disposer d’un mappage de schéma dans la classe session. À partir des informations de mappage de schéma, elle répond ensuite avec le tableau de GUID des schémas contenus dans le mappage. Il s’agit des schémas pris en charge par le fournisseur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IDBSchemaRowsetImpl (classe)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Membres IDBSchemaRowsetImpl (classe)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)   
 [IDBSchemaRowset::GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx)   
 [Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)