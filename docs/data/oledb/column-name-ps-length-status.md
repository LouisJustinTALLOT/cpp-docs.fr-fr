---
title: COLUMN_NAME_PS_LENGTH_STATUS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_NAME_PS_LENGTH_STATUS
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_PS_LENGTH_STATUS macro
ms.assetid: a1a2e2ca-f0ae-4896-8aa3-67a96c270b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 033b04c98ba7f7cee56cd6ecc235a0679a62754d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091328"
---
# <a name="columnnamepslengthstatus"></a>COLUMN_NAME_PS_LENGTH_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également la précision, échelle, longueur de colonne et état de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszName`  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez le faire en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 `nPrecision`  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 `nScale`  
 [in] L’échelle de la colonne que vous souhaitez lier.  
  
 `data`  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable à lier à la longueur de colonne.  
  
 *status*  
 [in] La variable à lier à l’état de la colonne.  
  
## <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur la **COLUMN_NAME_\***  macros sont utilisées.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)