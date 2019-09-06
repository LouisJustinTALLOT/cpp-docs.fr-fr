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
ms.openlocfilehash: a615694a9db75cdaf3b187cf6d29248bd26ef978
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311802"
---
# <a name="data-source-object-interfaces"></a>Interfaces de l'objet source de données

Le tableau suivant indique les interfaces obligatoires et facultatives définies par OLE DB pour un objet source de données.

|Interface|Requis ?|Implémenté par OLE DB modèles ?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Obligatoire|Oui|
|`IDBInitialize`|Obligatoire|Oui|
|`IDBProperties`|Obligatoire|Oui|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|Obligatoire|Oui|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Facultatif|Non|
|`IDBDataSourceAdmin`|Facultatif|Non|
|`IDBInfo`|Facultatif|Non|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|Facultatif|Non|
|`ISupportErrorInfo`|Facultatif|Non|

L’objet de source de données implémente les `IDBProperties`interfaces `IDBCreateSession` , `IDBInitialize`et via l’héritage. Vous pouvez choisir de prendre en charge des fonctionnalités supplémentaires en héritant ou n’héritant pas de l’une de ces classes d’implémentation. Si vous souhaitez prendre en charge `IDBDataSourceAdmin` l’interface, vous devez hériter `IDBDataSourceAdminImpl` de la classe.

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
