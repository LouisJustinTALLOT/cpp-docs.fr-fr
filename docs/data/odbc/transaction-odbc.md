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
ms.openlocfilehash: 0deb21a43ff17ca94efe29bdec37db7611331a86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615811"
---
# <a name="transaction-odbc"></a>Transaction (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Une transaction est un moyen pour le groupe ou le lot, une série de mises à jour à un [source de données](../../data/odbc/data-source-odbc.md) afin que toutes validées en même temps ou aucune n’est validée si vous annulez la transaction. Si vous n’utilisez pas une transaction, les modifications apportées à la source de données sont validées automatiquement au lieu d’être validées sur demande.

> [!NOTE]
>  Pas tous les pilotes de base de données ODBC prend en charge les transactions. Appelez le `CanTransact` fonction membre de votre [CDatabase](../../mfc/reference/cdatabase-class.md) ou [CRecordset](../../mfc/reference/crecordset-class.md) objet pour déterminer si votre pilote prend en charge les transactions pour une base de données. Notez que `CanTransact` ne vous dit pas si la source de données fournit la prise en charge complète des transactions. Vous devez également appeler `CDatabase::GetCursorCommitBehavior` et `CDatabase::GetCursorRollbackBehavior` après `CommitTrans` et `Rollback` pour vérifier l’effet de la transaction à l’ouverture `CRecordset` objet.

Appels à la `AddNew` et `Edit` fonctions membres d’un `CRecordset` affectent la source de données immédiatement lorsque vous appelez l’objet `Update`. `Delete` appels également immédiatement en vigueur. En revanche, vous pouvez utiliser une transaction composée de plusieurs appels à `AddNew`, `Edit`, `Update`, et `Delete`, qui sont effectué, mais pas validé jusqu'à ce que vous appeliez `CommitTrans` explicitement. En établissant une transaction, vous pouvez exécuter une série de tels appels tout en conservant la possibilité de les annuler. Si une ressource critique n’est pas disponible ou une autre condition empêche toute la transaction à partir de l’exécution, vous pouvez restaurer la transaction au lieu de la valider. Dans ce cas, aucune des modifications appartenant à la transaction affectent la source de données.

> [!NOTE]
>  Actuellement, la classe `CRecordset` ne prend pas en charge les mises à jour de la source de données si vous avez implémenté l’extraction de lignes en bloc. Cela signifie que vous ne pouvez pas effectuer des appels vers `AddNew`, `Edit`, `Delete`, ou `Update`. Toutefois, vous pouvez écrire vous propres fonctions pour effectuer des mises à jour, puis appeler ces fonctions au sein d’une transaction donnée. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Affecte le jeu d’enregistrements, les transactions n’affectent que vous exécutez directement tant que vous utilisez ODBC **pas** associé à votre `CDatabase` objet ou une application ODBC **HSTMT** selon qui **pas**.

Les transactions sont particulièrement utiles lorsque vous avez plusieurs enregistrements qui doivent être mis à jour simultanément. Dans ce cas, vous souhaitez éviter une transaction à moitié terminée, telles que peut se produire si une exception a été levée avant la dernière mise à jour a été effectuée. Le regroupement de ces mises à jour dans une transaction permet une récupération (rollback) à partir des modifications et retourne les enregistrements à l’état précédant. Par exemple, si une banque transfère de l’argent du compte A au compte B, à la fois le débit à partir d’un et le dépôt sur B doit réussir pour permettre de traiter correctement les fonds ou la transaction complète doit échouer.

Dans les classes de base de données, vous effectuez des transactions via `CDatabase` objets. Un `CDatabase` objet représente une connexion à une source de données, et un ou plusieurs jeux d’enregistrements associés `CDatabase` objet agissent sur les tables de la base de données via des fonctions membres de jeu d’enregistrements.

> [!NOTE]
>  Un seul niveau de transactions est pris en charge. Vous ne pouvez pas imbriquer des transactions ni peut une transaction s’étendre sur plusieurs objets de base de données.

Les rubriques suivantes fournissent plus d’informations sur la façon dont les transactions sont effectuées :

- [Transaction : exécution d’une transaction dans un recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transaction : répercussions des transactions sur les mises à jour (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)