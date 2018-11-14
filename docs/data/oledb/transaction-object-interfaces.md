---
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
ms.openlocfilehash: 177f66222a054c3305418ffcd0acdda5c82ccf43
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556177"
---
# <a name="transaction-object-interfaces"></a>Interfaces de l’objet transaction

L’objet de transaction définit une unité atomique de travail sur une source de données et détermine la façon dont ces unités de travail sont liés entre eux. Cet objet n’est pas directement pris en charge par les modèles du fournisseur OLE DB (autrement dit, vous devez créer votre propre objet).

Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de transaction.

|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obligatoire|Non|
|[ITransaction](https://docs.microsoft.com/previous-versions/windows/desktop/ms723053(v=vs.85))|Obligatoire|Non|
|[ISupportErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/ms715816(v=vs.85))|Facultatif|Non|

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
