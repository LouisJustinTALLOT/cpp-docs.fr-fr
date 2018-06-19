---
title: BLOB_NAME_LENGTH | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BLOB_NAME_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- BLOB_NAME_LENGTH macro
ms.assetid: 38150260-a127-486d-a7ab-0d01b731b6fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a05c9539994827efb427eeb5b76645ac08f4e810
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092058"
---
# <a name="blobnamelength"></a>BLOB_NAME_LENGTH
Utilisé avec `BEGIN_COLUMN_MAP` et `END_COLUMN_MAP` pour lier un objet binaire volumineux ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Semblable à [BLOB_NAME](../../data/oledb/blob-name.md), sauf que cette macro obtient également la longueur en octets de la colonne de données BLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszName`  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez le faire en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *IID*  
 [in] Interface, GUID, tels que **IDD_ISequentialStream**, utilisée pour récupérer l’objet BLOB.  
  
 `flags`  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, **STGM_READ**).  
  
 `data`  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [out] Longueur (réelle), en octets, de la colonne BLOB.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME](../../data/oledb/blob-name.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)