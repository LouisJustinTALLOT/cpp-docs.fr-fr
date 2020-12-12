---
description: 'En savoir plus sur : interfaces d’objet de transaction'
title: Interfaces de l’objet transaction
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
ms.openlocfilehash: bc8eec6ca5a962e825eafa12255d8a47a8a463f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272641"
---
# <a name="transaction-object-interfaces"></a>Interfaces de l’objet transaction

L’objet transaction définit une unité de travail atomique sur une source de données et détermine la relation entre ces unités de travail. Cet objet n’est pas directement pris en charge par les modèles du fournisseur OLE DB (autrement dit, vous devez créer votre propre objet).

Le tableau suivant indique les interfaces obligatoires et facultatives définies par OLE DB pour un objet de transaction.

|Interface|Requis ?|Implémenté par OLE DB modèles ?|
|---------------|---------------|--------------------------------------|
|[Interfaces](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obligatoire|Non|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Obligatoire|Non|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Facultatif|Non|

## <a name="see-also"></a>Voir aussi

[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
