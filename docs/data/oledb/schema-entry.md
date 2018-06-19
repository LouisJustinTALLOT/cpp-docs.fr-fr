---
title: SCHEMA_ENTRY | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SCHEMA_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- SCHEMA_ENTRY macro
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 665b337861959b28670a0b2e57649814853a7384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109519"
---
# <a name="schemaentry"></a>SCHEMA_ENTRY
Associe un GUID à une classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>Paramètres  
 `guid`  
 Un GUID de lignes du schéma. Consultez [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) dans les *de référence du programmeur OLE DB* pour obtenir la liste des ensembles de lignes de schéma et les GUID.  
  
 *rowsetClass*  
 La classe qui sera créée pour représenter l’ensemble de lignes de schéma.  
  
## <a name="remarks"></a>Notes  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) peut ensuite la carte pour obtenir la liste des GUID de requête, ou créer un ensemble de lignes si elle se voit accorder un GUID. L’ensemble de lignes de schéma `IDBSchemaRowsetImpl` crée est similaire à une norme `CRowsetImpl`-classe dérivée, mais elle doit fournir une **Execute** méthode dont la signature suivante :  
  
```  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 Cela **Execute** fonction remplit les données de l’ensemble de lignes. L’Assistant Projet ATL crée, comme décrit dans [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) dans les *de référence du programmeur OLE DB*, trois initiale des ensembles de lignes de schéma dans le projet pour chacun des trois schémas OLE DB obligatoires :  
  
-   `DBSCHEMA_TABLES`  
  
-   **DBSCHEMA_COLUMNS**  
  
-   **SCHÉMA DBSCHEMA_PROVIDER_TYPES**  
  
 L’Assistant ajoute également trois entrées correspondantes dans le mappage de schéma. Consultez [création d’un fournisseur OLE DB modèle](../../data/oledb/creating-an-ole-db-provider.md) pour plus d’informations sur l’utilisation de l’Assistant pour créer un fournisseur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)