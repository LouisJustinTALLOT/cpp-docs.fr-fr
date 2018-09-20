---
title: 'TN068 : Exécution de Transactions avec le pilote ODBC Microsoft Access 7 | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 4006ee6953342fd55b644eeb2a8e8f30c1d80285
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395841"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068 : exécution de transactions avec le pilote ODBC Microsoft Access 7

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit comment effectuer des transactions lorsque vous utilisez les classes de base de données ODBC MFC et le pilote ODBC Microsoft Access 7.0 inclus dans la version de Microsoft ODBC Desktop Driver Pack 3.0.

## <a name="overview"></a>Vue d'ensemble

Si votre application de base de données effectue des transactions, vous devez veiller à appeler `CDatabase::BeginTrans` et `CRecordset::Open` dans l’ordre approprié dans votre application. Le pilote Microsoft Access 7.0 utilise le moteur de base de données Microsoft Jet et Jet nécessite que votre application ne commence pas une transaction sur une base de données qui a un curseur ouvert. Pour les classes de base de données ODBC MFC, un curseur ouvert équivaut à une ouverture `CRecordset` objet.

Si vous ouvrez un jeu d’enregistrements avant d’appeler `BeginTrans`, vous ne voyiez pas les messages d’erreur. Toutefois, n’importe quel jeu d’enregistrements met à jour votre application, deviennent permanentes après avoir appelé `CRecordset::Update`, et les mises à jour ne seront pas restaurées en appelant `Rollback`. Pour éviter ce problème, vous devez appeler `BeginTrans` premier, puis ouvrez le jeu d’enregistrements.

MFC vérifie la fonctionnalité de pilote pour le comportement de validation et l’annulation du curseur. Classe `CDatabase` fournit deux fonctions membres, `GetCursorCommitBehavior` et `GetCursorRollbackBehavior`, pour déterminer l’effet d’une transaction sur votre open `CRecordset` objet. Pour le pilote ODBC Microsoft Access 7.0, ces fonctions membres retournent `SQL_CB_CLOSE` , car le pilote Access ne prend pas en charge la conservation de curseur. Par conséquent, vous devez appeler `CRecordset::Requery` suivant un `CommitTrans` ou `Rollback` opération.

Lorsque vous avez besoin effectuer des transactions multiples une après l’autre, vous ne pouvez pas appeler `Requery` après la première transaction et le démarrage puis celle qui suit. Vous devez fermer le jeu d’enregistrements avant l’appel suivant à `BeginTrans` afin de satisfaire à des exigences de Jet. Cette note technique décrit deux méthodes pour gérer cette situation :

- Fermeture de l’objet recordset après chaque `CommitTrans` ou `Rollback` opération.

- À l’aide de la fonction API ODBC `SQLFreeStmt`.

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Fermeture de l’objet Recordset après chaque CommitTrans ou d’une opération de restauration

Avant de commencer une transaction, assurez-vous que l’objet recordset est fermé. Après avoir appelé `BeginTrans`, appelez le jeu d’enregistrements `Open` fonction membre. Fermer le jeu d’enregistrements immédiatement après l’appel `CommitTrans` ou `Rollback`. Notez qu’à plusieurs reprises ouvrant et fermant le jeu d’enregistrements peuvent ralentir les performances d’une application.

## <a name="using-sqlfreestmt"></a>À l’aide de SQLFreeStmt

Vous pouvez également utiliser la fonction API ODBC `SQLFreeStmt` pour fermer explicitement le curseur après la fin d’une transaction. Pour démarrer une autre transaction, appelez `BeginTrans` suivie `CRecordset::Requery`. Lors de l’appel `SQLFreeStmt`, vous devez spécifier HSTMT le jeu d’enregistrements comme premier paramètre et *SQL_CLOSE* comme deuxième paramètre. Cette méthode est plus rapide que l’ouverture de l’ensemble d’enregistrements au début de chaque transaction et de clôture. Le code suivant montre comment implémenter cette technique :

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

Une autre façon d’implémenter cette technique consiste à écrire une nouvelle fonction, `RequeryWithBeginTrans`, que vous pouvez appeler pour démarrer la transaction suivante après avoir validé ou restauration de la première condition. Pour écrire une telle fonction, procédez comme suit :

1. Copiez le code pour `CRecordset::Requery( )` à la nouvelle fonction.

2. Ajoutez la ligne suivante immédiatement après l’appel à `SQLFreeStmt`:

   `m_pDatabase->BeginTrans( );`

Maintenant, vous pouvez appeler cette fonction entre chaque paire de transactions :

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
> N’utilisez pas cette technique si vous avez besoin de modifier les variables de membre du jeu d’enregistrements *m_strFilter* ou *m_strSort* entre les transactions. Dans ce cas, vous devez fermer le jeu d’enregistrements après chaque `CommitTrans` ou `Rollback` opération.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
