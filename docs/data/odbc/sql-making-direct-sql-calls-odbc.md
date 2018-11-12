---
title: 'SQL : appels SQL directs (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: 17b3279a4803a61595af64ab18629d6cf69f0f10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549849"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL : appels SQL directs (ODBC)

Cette rubrique explique :

- Quand utiliser SQL directe appelle.

- [Comment faire diriger SQL appelle à la source de données](#_core_making_direct_sql_function_calls).

> [!NOTE]
>  Ces informations s’appliquent aux classes ODBC MFC. Si vous travaillez avec les classes DAO MFC, consultez la rubrique « Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL » dans l’aide de DAO.

##  <a name="_core_when_to_call_sql_directly"></a> Quand appeler SQL directement

Pour créer des tables, supprimer (delete) tables, modifier des tables existantes, créer des index et exécuter d’autres fonctions SQL qui modifient le [Source de données (ODBC)](../../data/odbc/data-source-odbc.md) schéma, vous devez émettre une instruction SQL directement à la source de données à l’aide de la base de données Langage de définition (DDL). Lorsque vous utilisez un Assistant pour créer un jeu d’enregistrements pour une table (au moment du design), vous pouvez choisir les colonnes de la table à représenter dans le jeu d’enregistrements. Cela ne permet pas pour les colonnes que vous ou un autre utilisateur de la source de données ajouter à la table ultérieurement, une fois que votre programme a été compilé. Les classes de base de données ne prennent pas en charge DDL directement, mais vous pouvez toujours écrire du code pour lier d’une nouvelle colonne à votre jeu d’enregistrements dynamiquement, en cours d’exécution. Pour plus d’informations sur la procédure à suivre cette liaison, consultez [Recordset : liaison dynamique de colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Vous pouvez utiliser le SGBD lui-même pour modifier le schéma ou un autre outil qui vous permet d’effectuer les fonctions DDL. Vous pouvez également utiliser des appels de fonction ODBC pour l’envoi d’instructions SQL, telles que l’appel d’une requête prédéfinie (procédure stockée) qui ne retourne pas d’enregistrements.

##  <a name="_core_making_direct_sql_function_calls"></a> Appels de fonction SQL directs

Vous pouvez exécuter directement un appel SQL en utilisant un [CDatabase, classe](../../mfc/reference/cdatabase-class.md) objet. Configurer votre chaîne d’instruction SQL (généralement dans un `CString`) et transmettez-le à la [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) fonction membre de votre `CDatabase` objet. Si vous utilisez des appels de fonction ODBC pour envoyer une instruction SQL qui retourne normalement des enregistrements, les enregistrements sont ignorés.

## <a name="see-also"></a>Voir aussi

[SQL](../../data/odbc/sql.md)