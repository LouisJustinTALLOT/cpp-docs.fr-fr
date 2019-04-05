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
ms.openlocfilehash: 0caecc797a3175d5769f98e181e1d99ef6b1ad16
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034032"
---
# <a name="transaction-object-interfaces"></a>Interfaces de l’objet transaction

L’objet de transaction définit une unité atomique de travail sur une source de données et détermine la façon dont ces unités de travail sont liés entre eux. Cet objet n’est pas directement pris en charge par les modèles du fournisseur OLE DB (autrement dit, vous devez créer votre propre objet).

Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de transaction.

|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obligatoire|Non|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Obligatoire|Non|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Facultatif|Non|

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
