---
title: Interfaces de l’objet de Source de données | Microsoft Docs
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
ms.openlocfilehash: 25fca5e7e51789aceef8fb92cf48cc238a8e26fa
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195995"
---
# <a name="data-source-object-interfaces"></a>Interfaces de l'objet source de données
Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de source de données.  
  
|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|  
|---------------|---------------|--------------------------------------|  
|`IDBCreateSession`|Obligatoire|Oui|  
|`IDBInitialize`|Obligatoire|Oui|  
|`IDBProperties`|Obligatoire|Oui|  
|[IPersist](/windows/desktop/api/objidl/nn-objidl-ipersist)|Obligatoire|Oui|  
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Facultatif|Non|  
|`IDBDataSourceAdmin`|Facultatif|Non|  
|`IDBInfo`|Facultatif|Non|  
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Facultatif|Non|  
|`ISupportErrorInfo`|Facultatif|Non|  
  
 La source de données objet implémente le `IDBProperties`, `IDBInitialize`, et `IDBCreateSession` interfaces via l’héritage. Vous pouvez choisir de prendre en charge des fonctionnalités supplémentaires en héritant ou non à partir d’une de ces classes d’implémentation. Si vous souhaitez prendre en charge la `IDBDataSourceAdmin` interface, vous devez hériter de la `IDBDataSourceAdminImpl` classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)