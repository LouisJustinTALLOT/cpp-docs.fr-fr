---
title: COLUMN_ENTRY_TYPE_SIZE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_TYPE_SIZE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE_SIZE macro
ms.assetid: d8b169e8-af22-464b-8cb3-eaa346f7a739
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1acb969015acda4213532cac3e185bf97a3ac31d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097170"
---
# <a name="columnentrytypesize"></a>COLUMN_ENTRY_TYPE_SIZE
Représente une liaison à la colonne dans la base de données. Prend en charge `type` et `size` paramètres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nOrdinal`  
 [in] Le numéro de colonne.  
  
 `wType`  
 [in] Type de données d’entrée de la colonne.  
  
 `nLength`  
 [in] Taille de l’entrée de la colonne en octets.  
  
 `data`  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
## <a name="remarks"></a>Notes  
 Cette macro est une variante spécialisée de la [COLUMN_ENTRY](../../data/oledb/column-entry.md) macro qui fournit un moyen de spécifier la taille des données et le type.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)