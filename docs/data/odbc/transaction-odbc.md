---
description: 'En savoir plus sur : transaction (ODBC)'
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
ms.openlocfilehash: a7b769c37b58b34433939a18cb0dccf5fb4a798d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333871"
---
# <a name="transaction-odbc"></a>Transaction (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Une transaction est un moyen de regrouper, ou de traiter par lots, une série de mises à jour d’une [source de données](../../data/odbc/data-source-odbc.md) afin que toutes les validations soient validées simultanément, ou aucune n’est validée si vous restaurez la transaction. Si vous n’utilisez pas de transaction, les modifications apportées à la source de données sont validées automatiquement au lieu d’être validées à la demande.

> [!NOTE]
> Tous les pilotes de base de données ODBC ne prennent pas en charge les transactions. Appelez la `CanTransact` fonction membre de votre objet [CDatabase](../../mfc/reference/cdatabase-class.md) ou [CRecordset](../../mfc/reference/crecordset-class.md) pour déterminer si votre pilote prend en charge les transactions pour une base de données donnée. Notez que `CanTransact` ne vous indique pas si la source de données fournit une prise en charge complète des transactions. Vous devez également appeler `CDatabase::GetCursorCommitBehavior` et `CDatabase::GetCursorRollbackBehavior` après `CommitTrans` et `Rollback` pour vérifier l’effet de la transaction sur l' `CRecordset` objet ouvert.

Les appels aux `AddNew` `Edit` fonctions membres et d’un `CRecordset` objet affectent immédiatement la source de données lorsque vous appelez `Update` . `Delete` les appels prennent également effet immédiatement. En revanche, vous pouvez utiliser une transaction composée de plusieurs appels à `AddNew` , `Edit` , `Update` et `Delete` , qui sont effectués mais non validés jusqu’à ce que vous appeliez `CommitTrans` explicitement. En établissant une transaction, vous pouvez exécuter une série de tels appels tout en conservant la possibilité de les restaurer. Si une ressource critique n’est pas disponible ou si une autre condition empêche l’achèvement de la transaction entière, vous pouvez restaurer la transaction au lieu de la valider. Dans ce cas, aucune des modifications appartenant à la transaction n’affecte la source de données.

> [!NOTE]
> Actuellement, `CRecordset` la classe ne prend pas en charge les mises à jour de la source de données si vous avez implémenté l’extraction de lignes en bloc. Cela signifie que vous ne pouvez pas effectuer d’appels à `AddNew` , `Edit` , `Delete` ou `Update` . Toutefois, vous pouvez écrire vos propres fonctions pour effectuer des mises à jour, puis appeler ces fonctions au sein d’une transaction donnée. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> Outre l’impact de votre Recordset, les transactions affectent les instructions SQL que vous exécutez directement tant que vous utilisez l’ODBC **hdbc** associé à votre `CDatabase` objet ou un **HSTMT** ODBC basé sur ce **hdbc**.

Les transactions sont particulièrement utiles lorsque vous avez plusieurs enregistrements qui doivent être mis à jour simultanément. Dans ce cas, vous souhaitez éviter une transaction partiellement terminée, comme cela peut se produire si une exception a été levée avant la dernière mise à jour. Le regroupement de ces mises à jour dans une transaction permet une récupération (ROLLBACK) des modifications et renvoie les enregistrements à l’état de la prétransaction. Par exemple, si une banque transfère de l’argent du compte A au compte B, le retrait d’un et le dépôt à B doivent tous deux réussir pour traiter les fonds correctement ou l’ensemble de la transaction doit échouer.

Dans les classes de base de données, vous effectuez des transactions par le biais d' `CDatabase` objets. Un `CDatabase` objet représente une connexion à une source de données, et un ou plusieurs recordsets associés à cet `CDatabase` objet opèrent sur les tables de la base de données à l’aide des fonctions membres du Recordset.

> [!NOTE]
> Un seul niveau de transactions est pris en charge. Vous ne pouvez pas imbriquer des transactions et une transaction sur plusieurs objets de base de données.

Les rubriques suivantes fournissent plus d’informations sur la façon dont les transactions sont effectuées :

- [Transaction : exécution d’une transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transaction : répercussions des transactions sur les mises à jour (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Voir aussi

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
