---
title: Interfaces de l’objet de Source de données | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c8aaed0a9f50e20dba5938b9b37425f4caa2bb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101875"
---
# <a name="data-source-object-interfaces"></a>Interfaces de l'objet source de données
Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de source de données.  
  
|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|  
|---------------|---------------|--------------------------------------|  
|`IDBCreateSession`|Obligatoire|Oui|  
|`IDBInitialize`|Obligatoire|Oui|  
|`IDBProperties`|Obligatoire|Oui|  
|[IPersist](http://msdn.microsoft.com/library/windows/desktop/ms688695)|Obligatoire|Oui|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Facultatif|Non|  
|`IDBDataSourceAdmin`|Facultatif|Non|  
|`IDBInfo`|Facultatif|Non|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Facultatif|Non|  
|`ISupportErrorInfo`|Facultatif|Non|  
  
 La source de données objet implémente le `IDBProperties`, `IDBInitialize`, et `IDBCreateSession` interfaces via l’héritage. Vous pouvez choisir de prendre en charge des fonctionnalités supplémentaires en héritant ou non de l’une de ces classes d’implémentation. Si vous souhaitez prendre en charge la `IDBDataSourceAdmin` interface, vous devez hériter de la `IDBDataSourceAdminImpl` classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)