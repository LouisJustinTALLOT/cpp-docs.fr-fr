---
title: Interfaces de l'objet source de données
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: fc8d2f5edf854766dcb5dcc8ed6d57a849b8f2a0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033188"
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

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
