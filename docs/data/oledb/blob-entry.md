---
title: BLOB_ENTRY | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BLOB_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- BLOB_ENTRY macro
ms.assetid: 89e40678-0869-49ed-b502-0fa2630a9081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b3922b82c53b5ace7a518893154b4f5e5b7c489f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095097"
---
# <a name="blobentry"></a>BLOB_ENTRY
Utilisé avec `BEGIN_COLUMN_MAP` et `END_COLUMN_MAP` pour lier un objet binaire volumineux ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nOrdinal`  
 [in] Le numéro de colonne.  
  
 *IID*  
 [in] Interface, GUID, tels que **IDD_ISequentialStream**, utilisée pour récupérer l’objet BLOB.  
  
 `flags`  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, **STGM_READ**).  
  
 `data`  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
## <a name="example"></a>Exemple  
 Consultez [comment récupérer un objet BLOB ?](../../data/oledb/retrieving-a-blob.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)   
 [BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)