---
title: COLUMN_ENTRY_LENGTH | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_LENGTH macro
ms.assetid: 1758babf-204c-4d1d-b82a-f9a607072e9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a923f4474f15ffbb2011611bc1f8de476fc399c7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098236"
---
# <a name="columnentrylength"></a>COLUMN_ENTRY_LENGTH
Représente une liaison sur l’ensemble de lignes à la colonne dans la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) dans les *de référence du programmeur OLE DB*.  
  
 `nOrdinal`  
 [in] Le numéro de colonne, en commençant par un. Signet correspond à la colonne zéro.  
  
 `data`  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable à lier à la longueur de colonne.  
  
## <a name="remarks"></a>Notes  
 Cette macro prend en charge la *longueur* variable. Il est utilisé dans les emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)