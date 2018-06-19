---
title: BEGIN_COLUMN_MAP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_COLUMN_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_COLUMN_MAP macro
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b6a619e36e3457902ce6ced07389ca8461499682
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094723"
---
# <a name="begincolumnmap"></a>BEGIN_COLUMN_MAP
Marque le début d’une entrée de mappage de colonnes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BEGIN_COLUMN_MAP(x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Nom de la classe d’enregistrement utilisateur dérivée de `CAccessor`.  
  
## <a name="remarks"></a>Notes  
 Cette macro est utilisée dans le cas d’un seul accesseur sur un ensemble de lignes. Si vous avez plusieurs accesseurs sur un ensemble de lignes, utilisez [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
 La macro `BEGIN_COLUMN_MAP` se termine avec la macro `END_COLUMN_MAP` . Cette macro est utilisée quand un seul accesseur est obligatoire dans l’enregistrement utilisateur.  
  
 Les colonnes correspondent aux champs de l’ensemble de lignes à lier.  
  
## <a name="example"></a>Exemple  
 Voici un exemple de mappage de colonnes et de paramètres :  
  
 <!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)