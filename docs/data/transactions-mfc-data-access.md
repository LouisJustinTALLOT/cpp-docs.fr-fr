---
title: Transactions (MFC Data Access) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9dd531aee6ac8014f2ce47ddee7fc5f82e35a63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107816"
---
# <a name="transactions--mfc-data-access"></a>Transactions (Accès aux données MFC)
Le concept de transaction a été développé pour gérer les cas dans lesquels l’état résultant de la base de données dépend du succès total d’une série d’opérations. Cette situation peut survenir car des opérations successives peuvent modifier les résultats des opérations précédentes. Dans ce cas, si l'une des opérations échoue, l'état résultant pourrait être indéterminé.  
  
 Pour résoudre ce problème, les transactions regroupent une série d'opérations pour que l'intégrité du résultat final puisse être assurée. Soit toutes les opérations doivent réussir puis être validées (écrites dans la base de données), soit la transaction entière échoue. L'annulation de la transaction est appelée « restauration ». La restauration permet d'annuler les modifications et de rétablir la base de données à l'état précédant la transaction.  
  
 Par exemple, dans une transaction bancaire automatisée, si vous transférez une somme d'argent du compte A au compte B, la retrait de A et le crédit de B doivent tous deux réussir pour que les fonds soient traités correctement ou la transaction complète doit échouer.  
  
 Une transaction doit avoir des propriétés ACID, à savoir :  
  
-   **Atomicité** une transaction est une unité atomique de travail s’exécute une seule fois ; le travail est effectué ou pas du tout.  
  
-   **Cohérence** une transaction préserve la cohérence des données, en transformant un état cohérent des données dans un autre état cohérent des données. Les données liées par une transaction doivent être préservées sémantiquement.  
  
-   **Isolation** une transaction est une unité d’isolement et chacune se produit séparément et indépendamment des transactions simultanées. Une transaction ne doit jamais voir les phases intermédiaires d’une autre transaction.  
  
-   **Durabilité** une transaction est une unité de récupération. Si une transaction réussit, ses mises à jour persistent, même si le système tombe en panne ou est arrêté. Si une transaction échoue, le système reste à l’état qui était le sien avant la validation de la transaction.  
  
 Vous pouvez prendre en charge des transactions dans OLE DB (voir [prise en charge des Transactions dans OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)) ou ODBC (consultez [Transaction (ODBC)](../data/odbc/transaction-odbc.md)).  
  
 Une transaction distribuée est une transaction qui met à jour des données distribuées, c’est-à-dire des données qui se trouvent sur plusieurs systèmes informatiques en réseau. Si vous souhaitez prendre en charge des transactions sur un système distribué, vous devez utiliser ADO.NET plutôt que la prise en charge des transactions OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation (MFC/ATL) d’accès aux données](../data/data-access-programming-mfc-atl.md)