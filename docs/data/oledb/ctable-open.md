---
title: CTable::Open | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 5d006d95-74d7-4e2b-b243-a33bc53b5455
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ca271d8a88035151e6845db6b7cb9423c71c73ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102236"
---
# <a name="ctableopen"></a>CTable::Open
La table s’ouvre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `session`  
 [in] La session pour laquelle la table est ouverte.  
  
 *wszTableName*  
 [in] Le nom de la table à ouvrir, transmis sous forme de chaîne Unicode.  
  
 *szTableName*  
 [in] Le nom de la table à ouvrir, transmis sous forme de chaîne ANSI.  
  
 *dbid*  
 [in] Le **DBID** de la table à ouvrir.  
  
 *pPropSet*  
 [in] Un pointeur vers un tableau de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) les structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](https://msdn.microsoft.com/en-us/library/ms713696.aspx) dans les *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows. La valeur par défaut NULL ne spécifie aucune propriété.  
  
 `ulPropSets`  
 [in] Le nombre de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) structures passées dans le *pPropSet* argument.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CTable, classe](../../data/oledb/ctable-class.md)