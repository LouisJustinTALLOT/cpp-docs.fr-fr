---
title: Récupération d’un BLOB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 420e863fcd5d4c666bf8e9a25a2f0f53e726c871
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105203"
---
# <a name="retrieving-a-blob"></a>Récupération d'un BLOB
Vous pouvez récupérer un objet binaire volumineux (BLOB) de différentes manières. Vous pouvez utiliser **DBTYPE_BYTES** pour récupérer l’objet BLOB sous la forme d’une séquence d’octets ou utiliser une interface de type `ISequentialStream`. Pour plus d’informations, consultez [BLOB et les objets OLE](https://msdn.microsoft.com/en-us/library/ms711511.aspx) dans les *de référence du programmeur OLE DB*.  
  
 Le code suivant montre comment récupérer un objet BLOB à l’aide de `ISequentialStream`. La macro [BLOB_ENTRY](../../data/oledb/blob-entry.md) vous permet de spécifier l’interface et les indicateurs utilisés pour l’interface. Après l’ouverture de la table, le code appelle **en lecture** à maintes reprises sur `ISequentialStream` pour lire les octets à partir de l’objet BLOB. Le code appelle **version** pour supprimer le pointeur d’interface avant d’appeler `MoveNext` pour obtenir l’enregistrement suivant.  
  
```  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories>> categories;  
ULONG          cb;  
BYTE            myBuffer[65536];  
  
categories.Open(session, "Categories");  

while (categories.MoveNext() == S_OK)  
{  
   do  
   {  
      categories.pPicture->Read(myBuffer, 65536, &cb);  
      // Do something with the buffer  
   } while (cb > 0);  
   categories.pPicture->Release();  
}  
```  
  
 Pour plus d’informations sur les macros qui gèrent les données BLOB, consultez « Macros de mappage de colonnes » dans [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’accesseurs](../../data/oledb/using-accessors.md)   
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)