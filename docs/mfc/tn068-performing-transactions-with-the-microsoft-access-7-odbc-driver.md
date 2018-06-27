---
title: 'TN068 : Exécution de Transactions avec le pilote ODBC Microsoft Access 7 | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data.odbc
dev_langs:
- C++
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 653e1cf29ff2b2e2338df7e8e3a1e74d73a7d6fe
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950225"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068 : exécution de transactions avec le pilote ODBC Microsoft Access 7
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note décrit comment effectuer des transactions lorsque vous utilisez les classes de base de données ODBC MFC et le pilote ODBC de Microsoft Access 7.0 inclus dans la version de Microsoft ODBC Desktop Driver Pack 3.0.  
  
## <a name="overview"></a>Vue d'ensemble  
 Si votre application de base de données effectue des transactions, vous devez veiller à appeler `CDatabase::BeginTrans` et `CRecordset::Open` dans l’ordre approprié dans votre application. Le pilote Microsoft Access 7.0 utilise le moteur de base de données Microsoft Jet et Jet requiert que votre application ne commence pas une transaction sur une base de données qui a un curseur ouvert. Pour les classes de base de données ODBC MFC, un curseur ouvert équivaut à open `CRecordset` objet.  
  
 Si vous ouvrez un objet recordset avant d’appeler `BeginTrans`, vous ne pouvez pas voir les messages d’erreur. Toutefois, n’importe quel jeu d’enregistrements met à jour votre application, deviennent permanentes après l’appel `CRecordset::Update`, et les mises à jour ne seront pas restaurées en appelant `Rollback`. Pour éviter ce problème, vous devez appeler `BeginTrans` premier, puis ouvrez le jeu d’enregistrements.  
  
 MFC vérifie la fonctionnalité de pilote pour le comportement de validation et l’annulation du curseur. Classe `CDatabase` fournit deux fonctions membres, `GetCursorCommitBehavior` et `GetCursorRollbackBehavior`, afin de déterminer l’effet de toutes les transactions sur votre ouvert `CRecordset` objet. Pour le pilote ODBC de Microsoft Access 7.0, ces fonctions membres retournent `SQL_CB_CLOSE` , car le pilote Access ne prend pas en charge la conservation de curseur. Par conséquent, vous devez appeler `CRecordset::Requery` suivant un `CommitTrans` ou `Rollback` opération.  
  
 Lorsque vous avez besoin effectuer des transactions multiples une après l’autre, vous ne pouvez pas appeler `Requery` après la première transaction et puis démarrer suivant. Vous devez fermer le recordset avant le prochain appel à `BeginTrans` pour satisfaire l’exigence de Jet. Cette note technique décrit deux méthodes permettent de gérer cette situation :  
  
-   Fermeture de l’objet recordset après chaque `CommitTrans` ou `Rollback` opération.  
  
-   À l’aide de la fonction d’API ODBC `SQLFreeStmt`.  
  
## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Fermeture de l’objet Recordset après chaque CommitTrans ou d’une opération de restauration  
 Avant de commencer une transaction, assurez-vous que l’objet recordset est fermé. Après avoir appelé `BeginTrans`, appelez le jeu d’enregistrements `Open` fonction membre. Fermez l’objet recordset immédiatement après l’appel `CommitTrans` ou `Rollback`. Notez qu’ouverture et la fermeture du jeu d’enregistrements peuvent ralentir les performances d’une application.  
  
## <a name="using-sqlfreestmt"></a>À l’aide de SQLFreeStmt  
 Vous pouvez également utiliser la fonction d’API ODBC `SQLFreeStmt` explicitement fermer le curseur après la fin d’une transaction. Pour démarrer une autre transaction, appelez `BeginTrans` suivie `CRecordset::Requery`. Lors de l’appel `SQLFreeStmt`, vous devez spécifier HSTMT le jeu d’enregistrements comme premier paramètre et *SQL_CLOSE* comme second paramètre. Cette méthode est plus rapide que l’ouverture de l’ensemble d’enregistrements au début de chaque transaction et de clôture. Le code suivant montre comment implémenter cette technique :  
  
```  
CMyDatabase db;  
db.Open("MYDATASOURCE");

CMyRecordset rs(&db);

 
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor  
::SQLFreeStmt(rs.m_hstmt, SQL_CLOSE);

 
// start transaction 2  
db.BeginTrans();

 
// now get the result set  
rs.Requery();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();

 
rs.Close();

db.Close();
```  
  
 Un autre moyen d’implémenter cette technique consiste à écrire une nouvelle fonction, `RequeryWithBeginTrans`, que vous pouvez appeler pour démarrer la transaction suivante après validation ou annulation de le. Pour écrire une telle fonction, procédez comme suit :  
  
1.  Copiez le code de `CRecordset::Requery( )` à la nouvelle fonction.  
  
2.  Ajoutez la ligne suivante immédiatement après l’appel à `SQLFreeStmt`:  
  
 `m_pDatabase->BeginTrans( );`  
  
 Maintenant, vous pouvez appeler cette fonction entre chaque paire de transactions :  
  
```  
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor,
    start new transaction,  
// and get the result set  
rs.RequeryWithBeginTrans();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();
*// or Rollback()  
```  
  
> [!NOTE]
>  N’utilisez pas cette technique si vous avez besoin modifier les variables de membre du jeu d’enregistrements *m_strFilter* ou *m_strSort* entre les transactions. Dans ce cas, vous devez fermer le jeu d’enregistrements après chaque `CommitTrans` ou `Rollback` opération.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

