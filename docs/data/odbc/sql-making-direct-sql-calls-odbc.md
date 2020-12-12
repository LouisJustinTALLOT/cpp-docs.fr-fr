---
description: 'En savoir plus sur : SQL : appels SQL directs (ODBC)'
title: 'SQL : appels SQL directs (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: 1cf7f20bf7de777f418c289f06878fa9ae448c12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124512"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL : appels SQL directs (ODBC)

Cette rubrique répond aux questions suivantes :

- Quand utiliser des appels SQL directs.

- [Comment effectuer des appels SQL directs à la source de données](#_core_making_direct_sql_function_calls).

> [!NOTE]
> Ces informations s’appliquent aux classes ODBC MFC. Si vous utilisez les classes DAO MFC, consultez la rubrique « Comparaison de Microsoft Jet Moteur de base de données SQL et ANSI SQL » dans l’aide de DAO.

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a> Quand appeler SQL directement

Pour créer des tables, supprimer des tables, modifier des tables existantes, créer des index et effectuer d’autres fonctions SQL qui modifient le schéma de la [source de données (ODBC)](../../data/odbc/data-source-odbc.md) , vous devez émettre une instruction SQL directement à la source de données à l’aide du langage de définition de base de données (DDL). Quand vous utilisez un Assistant pour créer un jeu d’enregistrements pour une table (au moment du Design), vous pouvez choisir les colonnes de la table à représenter dans le Recordset. Cela n’autorise pas les colonnes que vous ou un autre utilisateur de la source de données ajoute à la table ultérieurement, une fois votre programme compilé. Les classes de base de données ne prennent pas en charge DDL directement, mais vous pouvez toujours écrire du code pour lier une nouvelle colonne à votre jeu d’enregistrements de manière dynamique, au moment de l’exécution. Pour plus d’informations sur la façon d’effectuer cette liaison, consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Vous pouvez utiliser le SGBD lui-même pour modifier le schéma ou un autre outil qui vous permet d’exécuter des fonctions DDL. Vous pouvez également utiliser des appels de fonction ODBC pour envoyer des instructions SQL, telles que l’appel d’une requête prédéfinie (procédure stockée) qui ne retourne pas d’enregistrements.

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a> Appels directs des fonctions SQL

Vous pouvez exécuter directement un appel SQL à l’aide d’un objet de [classe CDatabase](../../mfc/reference/cdatabase-class.md) . Configurez votre chaîne d’instruction SQL (généralement dans un `CString` ) et transmettez-la à la fonction membre [CDatabase :: ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) de votre `CDatabase` objet. Si vous utilisez des appels de fonction ODBC pour envoyer une instruction SQL qui retourne normalement des enregistrements, ceux-ci sont ignorés.

## <a name="see-also"></a>Voir aussi

[SQL](../../data/odbc/sql.md)
