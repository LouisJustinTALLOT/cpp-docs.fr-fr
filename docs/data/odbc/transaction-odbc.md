---
title: Transactions (ODBC) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3acd47746d3a920b679fb5509c34e5978ad43eed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094024"
---
# <a name="transaction-odbc"></a>Transaction (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Une transaction est un moyen pour le groupe ou le lot, une série de mises à jour pour un [source de données](../../data/odbc/data-source-odbc.md) afin que toutes validées en même temps ou aucune n’est validée si vous annulez la transaction. Si vous n’utilisez pas une transaction, les modifications apportées à la source de données sont validées automatiquement au lieu d’être validées sur demande.  
  
> [!NOTE]
>  Pas de tous les pilotes de base de données ODBC prend en charge les transactions. Appelez le `CanTransact` fonction membre de votre [CDatabase](../../mfc/reference/cdatabase-class.md) ou [CRecordset](../../mfc/reference/crecordset-class.md) objet afin de déterminer si votre pilote prend en charge les transactions pour une base de données. Notez que `CanTransact` n’indique pas de savoir si la source de données fournit une prise en charge complète des transactions. Vous devez également appeler `CDatabase::GetCursorCommitBehavior` et `CDatabase::GetCursorRollbackBehavior` après **CommitTrans** et **restauration** pour vérifier l’effet de la transaction à l’ouverture `CRecordset` objet.  
  
 Appels à la `AddNew` et **modifier** fonctions membres d’un `CRecordset` affectent la source de données immédiatement lorsque vous appelez l’objet **mise à jour**. **Supprimer** appelle également prendre effet immédiatement. En revanche, vous pouvez utiliser une transaction composée de plusieurs appels à `AddNew`, **modifier**, **mise à jour**, et **supprimer**, qui sont exécuté mais pas validé tant que vous appelez **CommitTrans** explicitement. En établissant une transaction, vous pouvez exécuter une série de tels appels tout en conservant la possibilité de les annuler. Si une ressource critique n’est pas disponible, ou toute autre condition empêche toute la transaction de s’exécuter, vous pouvez restaurer la transaction au lieu de sa validation. Dans ce cas, aucune des modifications appartenant à la transaction affecte la source de données.  
  
> [!NOTE]
>  Actuellement, la classe `CRecordset` ne prend pas en charge les mises à jour de la source de données si vous avez implémenté l’extraction de lignes en bloc. Cela signifie que vous ne pouvez pas effectuer des appels vers `AddNew`, **modifier**, **supprimer**, ou **mise à jour**. Toutefois, vous pouvez écrire vous propres fonctions pour effectuer des mises à jour, puis appeler ces fonctions au sein d’une transaction donnée. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Affecte le jeu d’enregistrements, les transactions n’affectent que vous exécutez directement tant que vous utilisez ODBC **pas** associé à votre `CDatabase` objet ou une application ODBC **HSTMT** basé sur qui **pas**.  
  
 Les transactions sont particulièrement utiles lorsque vous avez plusieurs enregistrements qui doivent être mis à jour simultanément. Dans ce cas, vous souhaitez éviter une transaction moitié terminée, tels que peut se produire si une exception a été levée avant la dernière mise à jour a été effectuée. Regroupement de ces mises à jour dans une transaction permet une restauration (rollback) à partir des modifications et retourne les enregistrements à l’état précédant. Par exemple, si une banque transfère de l’argent du compte A au compte B, à la fois le retrait de A et le crédit de B doit réussir pour que les fonds correctement ou la transaction complète doit échouer.  
  
 Dans les classes de base de données, vous effectuez des transactions via `CDatabase` objets. A `CDatabase` objet représente une connexion à une source de données, et un ou plusieurs jeux d’enregistrements associée à cet `CDatabase` objet agissent sur les tables de la base de données via des fonctions membres de jeu d’enregistrements.  
  
> [!NOTE]
>  Un seul niveau de transactions est pris en charge. Vous ne pouvez pas imbriquer des transactions ni peut une transaction s’étendre sur plusieurs objets de base de données.  
  
 Les rubriques suivantes fournissent plus d’informations sur la façon dont les transactions sont effectuées :  
  
-   [Transaction : exécution d’une transaction dans un recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [Transaction : répercussions des transactions sur les mises à jour (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)