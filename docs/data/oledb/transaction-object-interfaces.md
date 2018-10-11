---
title: Interfaces de l’objet transaction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: caf57ab85b7a37b8e43230dc9bcf1caf031f7a78
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083786"
---
# <a name="transaction-object-interfaces"></a>Interfaces de l’objet transaction

L’objet de transaction définit une unité atomique de travail sur une source de données et détermine la façon dont ces unités de travail sont liés entre eux. Cet objet n’est pas directement pris en charge par les modèles du fournisseur OLE DB (autrement dit, vous devez créer votre propre objet).  
  
Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de transaction.  
  
|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|  
|---------------|---------------|--------------------------------------|  
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obligatoire|Non|  
|[ITransaction](/previous-versions/windows/desktop/ms723053)|Obligatoire|Non|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|Facultatif|Non|  
  
## <a name="see-also"></a>Voir aussi  

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)