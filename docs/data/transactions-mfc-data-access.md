---
title: Transactions (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
ms.openlocfilehash: 742e95d896d107fb89b3d65f0eeb6d418f1b2057
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209064"
---
# <a name="transactions--mfc-data-access"></a>Transactions (Accès aux données MFC)

Le concept de transaction a été développé pour gérer les cas dans lesquels l'état résultant de la base de données dépend du succès total d'une série d'opérations. Cette situation peut survenir car des opérations successives peuvent modifier les résultats des opérations précédentes. Dans ce cas, si l'une des opérations échoue, l'état résultant pourrait être indéterminé.

Pour résoudre ce problème, les transactions regroupent une série d'opérations pour que l'intégrité du résultat final puisse être assurée. Soit toutes les opérations doivent réussir puis être validées (écrites dans la base de données), soit la transaction entière échoue. L'annulation de la transaction est appelée « restauration ». La restauration permet d'annuler les modifications et de rétablir la base de données à l'état précédant la transaction.

Par exemple, dans une transaction bancaire automatisée, si vous transférez une somme d’argent du compte A au compte B, la retrait de A et le crédit de B doivent tous deux réussir pour que les fonds soient traités correctement ou la transaction complète doit échouer.

Une transaction doit avoir des propriétés ACID, à savoir :

- **Atomicité** Une transaction est une unité de travail atomique et s’exécute exactement une fois ; soit la totalité du travail est terminée, soit rien ne l’est.

- **Cohérence** Une transaction conserve la cohérence des données, transformant un état cohérent des données en un autre état cohérent des données. Les données liées par une transaction doivent être préservées sémantiquement.

- **Isolation** Une transaction est une unité d’isolation et chacune se produit séparément et indépendamment des transactions simultanées. Une transaction ne doit jamais voir les phases intermédiaires d’une autre transaction.

- **Durabilité** Une transaction est une unité de récupération. Si une transaction réussit, ses mises à jour persistent, même si le système tombe en panne ou est arrêté. Si une transaction échoue, le système reste à l’état qui était le sien avant la validation de la transaction.

Vous pouvez prendre en charge les transactions dans OLE DB (voir [prise en charge des transactions dans OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)) ou ODBC (voir [transaction (ODBC)](../data/odbc/transaction-odbc.md)).

Une transaction distribuée est une transaction qui met à jour des données distribuées, c'est-à-dire des données qui se trouvent sur plusieurs systèmes informatiques en réseau. Si vous souhaitez prendre en charge les transactions sur un système distribué, vous devez utiliser ADO.NET au lieu de la prise en charge des transactions OLE DB.

## <a name="see-also"></a>Voir aussi

[Programmation de l’accès aux données (MFC/ATL)](../data/data-access-programming-mfc-atl.md)
