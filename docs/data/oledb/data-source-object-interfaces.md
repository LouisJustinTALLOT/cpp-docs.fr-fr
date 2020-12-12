---
description: 'En savoir plus sur : interfaces d’objet de source de données'
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
ms.openlocfilehash: ecc37ca4286e288939ccd15bdcd073379c27f7c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287617"
---
# <a name="data-source-object-interfaces"></a>Interfaces de l'objet source de données

Le tableau suivant indique les interfaces obligatoires et facultatives définies par OLE DB pour un objet source de données.

|Interface|Requis ?|Implémenté par OLE DB modèles ?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Obligatoire|Oui|
|`IDBInitialize`|Obligatoire|Oui|
|`IDBProperties`|Obligatoire|Oui|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|Obligatoire|Oui|
|[Interfaces](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Facultatif|Non|
|`IDBDataSourceAdmin`|Facultatif|Non|
|`IDBInfo`|Facultatif|Non|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|Facultatif|Non|
|`ISupportErrorInfo`|Facultatif|Non|

L’objet de source de données implémente les `IDBProperties` `IDBInitialize` interfaces, et `IDBCreateSession` via l’héritage. Vous pouvez choisir de prendre en charge des fonctionnalités supplémentaires en héritant ou n’héritant pas de l’une de ces classes d’implémentation. Si vous souhaitez prendre en charge l' `IDBDataSourceAdmin` interface, vous devez hériter de la `IDBDataSourceAdminImpl` classe.

## <a name="see-also"></a>Voir aussi

[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
