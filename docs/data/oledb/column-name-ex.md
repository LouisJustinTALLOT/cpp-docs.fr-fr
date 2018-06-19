---
title: COLUMN_NAME_EX | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_NAME_EX
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_EX macro
ms.assetid: 4f916a85-f6ae-464a-9cbe-0a56dbb274a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3992a727519ed83a0dbf4c570bad3bbf8d0404ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098691"
---
# <a name="columnnameex"></a>COLUMN_NAME_EX
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également le type de données, taille, précision, échelle, longueur de colonne et l’état de la colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszName`  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez le faire en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 `wType`  
 [in] Le type de données.  
  
 `nLength`  
 [in] La taille des données en octets.  
  
 `nPrecision`  
 [in] La précision maximale à utiliser lors de l’obtention des données et `wType` est `DBTYPE_NUMERIC`. Dans le cas contraire, ce paramètre est ignoré.  
  
 `nScale`  
 [in] L’échelle à utiliser lors de l’obtention des données et `wType` est `DBTYPE_NUMERIC` ou **DBTYPE_DECIMAL**.  
  
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
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)