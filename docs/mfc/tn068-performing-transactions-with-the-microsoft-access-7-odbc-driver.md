---
description: 'En savoir plus sur : TN068 : exécution de transactions avec le pilote ODBC Microsoft Access 7'
title: 'TN068 : exécution de transactions avec le pilote ODBC Microsoft Access 7'
ms.date: 06/28/2018
f1_keywords:
- vc.data.odbc
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
ms.openlocfilehash: ebc98a0fd2bea78c0159daa9a53a11a292482257
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214544"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068 : exécution de transactions avec le pilote ODBC Microsoft Access 7

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit comment effectuer des transactions lors de l’utilisation des classes de base de données ODBC MFC et du pilote ODBC Microsoft Access 7,0 inclus dans Microsoft ODBC Desktop Driver Pack version 3,0.

## <a name="overview"></a>Vue d’ensemble

Si votre application de base de données effectue des transactions, vous devez veiller à appeler `CDatabase::BeginTrans` et `CRecordset::Open` dans l’ordre correct dans votre application. Le pilote Microsoft Access 7,0 utilise le moteur de base de données Microsoft Jet, et jet requiert que votre application ne démarre pas de transaction sur une base de données qui a un curseur ouvert. Pour les classes de base de données ODBC MFC, un curseur ouvert correspond à un `CRecordset` objet ouvert.

Si vous ouvrez un Recordset avant d’appeler `BeginTrans` , vous risquez de ne pas voir de messages d’erreur. Toutefois, tout Recordset mis à jour votre application devient permanent après l’appel de `CRecordset::Update` , et les mises à jour ne sont pas annulées en appelant `Rollback` . Pour éviter ce problème, vous devez d' `BeginTrans` abord appeler, puis ouvrir le jeu d’enregistrements.

MFC vérifie la fonctionnalité du pilote pour la validation de curseur et le comportement de restauration. `CDatabase`La classe fournit deux fonctions membres, `GetCursorCommitBehavior` et `GetCursorRollbackBehavior` , pour déterminer l’effet de toute transaction sur votre `CRecordset` objet ouvert. Pour le pilote ODBC Microsoft Access 7,0, ces fonctions membres retournent `SQL_CB_CLOSE` car le pilote Access ne prend pas en charge la conservation des curseurs. Par conséquent, vous devez appeler `CRecordset::Requery` après `CommitTrans` une `Rollback` opération ou.

Lorsque vous devez effectuer plusieurs transactions l’une après l’autre, vous ne pouvez pas appeler `Requery` après la première transaction, puis démarrer la suivante. Vous devez fermer le Recordset avant le prochain appel à pour `BeginTrans` répondre aux exigences de jet. Cette note technique décrit deux méthodes de gestion de cette situation :

- Fermeture du recordset après chaque `CommitTrans` `Rollback` opération ou.

- Utilisation de la fonction API ODBC `SQLFreeStmt` .

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Fermeture du recordset après chaque opération CommitTrans ou Rollback

Avant de démarrer une transaction, assurez-vous que l’objet Recordset est fermé. Après l’appel de `BeginTrans` , appelez la fonction membre du recordset `Open` . Fermez le Recordset juste après l’appel `CommitTrans` de ou de `Rollback` . Notez que l’ouverture et la fermeture répétées du Recordset peuvent ralentir les performances d’une application.

## <a name="using-sqlfreestmt"></a>Utilisation de SQLFreeStmt

Vous pouvez également utiliser la fonction API ODBC `SQLFreeStmt` pour fermer explicitement le curseur après la fin d’une transaction. Pour démarrer une autre transaction, appelez `BeginTrans` suivi de `CRecordset::Requery` . Lors de l’appel de `SQLFreeStmt` , vous devez spécifier HSTMT du Recordset comme premier paramètre et *SQL_CLOSE* comme deuxième paramètre. Cette méthode est plus rapide que la fermeture et l’ouverture du Recordset au début de chaque transaction. Le code suivant montre comment implémenter cette technique :

```cpp
CMyDatabase db;
db.Open("MYDATASOURCE");
CMyRecordset rs(&db);

// start transaction 1 and
// open the recordset
db.BeginTrans();
rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans(); // or Rollback()

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

Une autre façon d’implémenter cette technique consiste à écrire une nouvelle fonction, `RequeryWithBeginTrans` , que vous pouvez appeler pour démarrer la transaction suivante après la validation ou la restauration de la première. Pour écrire une telle fonction, procédez comme suit :

1. Copiez le code pour `CRecordset::Requery( )` dans la nouvelle fonction.

2. Ajoutez la ligne suivante immédiatement après l’appel à `SQLFreeStmt` :

   `m_pDatabase->BeginTrans( );`

Vous pouvez maintenant appeler cette fonction entre chaque paire de transactions :

```cpp
// start transaction 1 and
// open the recordset
db.BeginTrans();

rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans();   // or Rollback()

// close the cursor, start new transaction,
// and get the result set
rs.RequeryWithBeginTrans();

// manipulate data

// end transaction 2
db.CommitTrans();   // or Rollback()
```

> [!NOTE]
> N’utilisez pas cette technique si vous devez modifier les variables de membre du jeu d’enregistrements *m_strFilter* ou *m_strSort* entre les transactions. Dans ce cas, vous devez fermer le jeu d’enregistrements après `CommitTrans` chaque `Rollback` opération ou.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
