---
title: Transaction (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: 56629f8c5ff74aff4e0df589cda1e7b988fb5fd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376412"
---
# <a name="transaction-odbc"></a>Transaction (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Une transaction est un moyen de regrouper, ou de lot, une série de mises à jour à une source de [données](../../data/odbc/data-source-odbc.md) de sorte que tous sont engagés à la fois ou aucun sont engagés si vous annulez la transaction. Si vous n’utilisez pas de transaction, les modifications apportées à la source de données sont validées automatiquement plutôt que d’être validées à la demande.

> [!NOTE]
> Tous les moteurs de base de données ODBC ne prennent pas en charge les transactions. Appelez `CanTransact` la fonction membre de votre [CDatabase](../../mfc/reference/cdatabase-class.md) ou [CRecordset](../../mfc/reference/crecordset-class.md) pour déterminer si votre pilote prend en charge les transactions pour une base de données donnée. Notez `CanTransact` que ne vous indique pas si la source de données fournit un support complet de transaction. Vous devez `CDatabase::GetCursorCommitBehavior` également `CDatabase::GetCursorRollbackBehavior` `CommitTrans` appeler `Rollback` et après et vérifier l’effet de la transaction sur l’objet ouvert. `CRecordset`

Les appels `AddNew` `Edit` vers les fonctions et les fonctions des membres d’un `CRecordset` objet affectent immédiatement la source de données lorsque vous appelez `Update`. `Delete`les appels prennent également effet immédiatement. En revanche, vous pouvez utiliser une `AddNew`transaction `Edit` `Update`composée `Delete`de plusieurs appels à , `CommitTrans` , et , qui sont effectués, mais pas commis jusqu’à ce que vous appelez explicitement. En établissant une transaction, vous pouvez exécuter une série de ces appels tout en conservant la possibilité de les annuler. Si une ressource critique n’est pas disponible ou si une autre condition empêche la totalité de la transaction d’être effectuée, vous pouvez annuler la transaction au lieu de l’engager. Dans ce cas, aucun des changements appartenant à la transaction n’affecte la source de données.

> [!NOTE]
> À l’heure actuelle, la classe `CRecordset` ne prend pas en charge les mises à jour de la source de données si vous avez implémenté la ligne en vrac. Cela signifie que vous `AddNew` `Edit`ne `Delete`pouvez `Update`pas faire des appels à , , , ou . Toutefois, vous pouvez écrire vos propres fonctions pour effectuer des mises à jour, puis appeler ces fonctions dans une transaction donnée. Pour plus d’informations sur la ligne en vrac aller chercher, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> En plus d’affecter votre ensemble d’enregistrements, les transactions affectent les relevés SQL que vous exécutez directement tant que vous utilisez le **HDBC** ODBC associé à votre `CDatabase` objet ou à un **HSTMT** ODBC basé sur ce **HDBC**.

Les transactions sont particulièrement utiles lorsque vous avez plusieurs enregistrements qui doivent être mis à jour simultanément. Dans ce cas, vous voulez éviter une transaction à moitié terminée, comme cela pourrait se produire si une exception a été lancée avant la dernière mise à jour a été faite. Regrouper ces mises à jour dans une transaction permet une récupération (recul) des modifications et renvoie les enregistrements à l’état de prétransaction. Par exemple, si une banque transfère de l’argent du compte A au compte B, le retrait de A et le dépôt à B doivent réussir à traiter correctement les fonds ou l’ensemble de la transaction doit échouer.

Dans les classes de base `CDatabase` de données, vous effectuez des transactions via des objets. Un `CDatabase` objet représente une connexion à une source de données, et un ou plusieurs enregistrements associés à cet `CDatabase` objet fonctionnent sur des tables de la base de données via des fonctions de membre de l’ensemble d’enregistrements.

> [!NOTE]
> Un seul niveau de transactions est pris en charge. Vous ne pouvez pas imbriquer les transactions et une transaction ne peut pas s’étendre à plusieurs objets de base de données.

Les sujets suivants fournissent plus d’informations sur la façon dont les transactions sont effectuées :

- [Transaction : exécution d’une transaction dans un recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transaction : répercussions des transactions sur les mises à jour (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Voir aussi

[Connectivité open Database (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
