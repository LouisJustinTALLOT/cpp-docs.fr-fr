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
ms.openlocfilehash: 88b6884ff8543b3aa6ec329330563fbe1ad27b8e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071586"
---
# <a name="transaction-object-interfaces"></a>Interfaces de l’objet transaction

L’objet de transaction définit une unité atomique de travail sur une source de données et détermine la façon dont ces unités de travail sont liés entre eux. Cet objet n’est pas directement pris en charge par les modèles du fournisseur OLE DB (autrement dit, vous devez créer votre propre objet).  
  
Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de transaction.  
  
|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|  
|---------------|---------------|--------------------------------------|  
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obligatoire|Non|  
|[ITransaction](/previous-versions/windows/desktop/ms723053\(v=vs.85\))|Obligatoire|Non|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816\(v=vs.85\))|Facultatif|Non|  
  
## <a name="see-also"></a>Voir aussi  

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)