---
title: PROVIDER_COLUMN_ENTRY_GN | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_GN
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_GN macro
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: be0cfa80b0d2a18d04dd329feda6547b5d89e6e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109974"
---
# <a name="providercolumnentrygn"></a>PROVIDER_COLUMN_ENTRY_GN
Représente une colonne spécifique pris en charge par le fournisseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *name*  
 [in] Le nom de colonne.  
  
 `ordinal`  
 [in] Le numéro de colonne. Sauf si la colonne est une colonne de signet, le numéro de colonne ne doit pas être 0.  
  
 `flags`  
 [in] Spécifie la manière dont les données sont retournées. Consultez le `dwFlags` description dans [Structures DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *colSize*  
 [in] La taille de la colonne.  
  
 `dbtype`  
 [in] Indique le type de données de la valeur. Consultez le **wType** description dans [Structures DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *precision*  
 [in] Indique la précision à utiliser lors de l’obtention des données si *dbType* est `DBTYPE_NUMERIC` ou **DBTYPE_DECIMAL**. Consultez le **bPrecision** description dans [Structures DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `scale`  
 [in] Indique l’échelle à utiliser lors de l’obtention des données si dbType est `DBTYPE_NUMERIC` ou **DBTYPE_DECIMAL**. Consultez le **bScale** description dans [Structures DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `guid`  
 Un GUID de lignes du schéma. Consultez [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) dans les *de référence du programmeur OLE DB* pour obtenir la liste des ensembles de lignes de schéma et les GUID.  
  
## <a name="remarks"></a>Notes  
 Vous permet de spécifier la taille de la colonne, type de données, précision, échelle et de lignes du schéma GUID.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)