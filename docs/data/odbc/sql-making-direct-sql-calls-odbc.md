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
ms.openlocfilehash: e2421e047d217fdc7a138509385399fa37d36a1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374496"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL : appels SQL directs (ODBC)

Cette rubrique répond aux questions suivantes :

- Quand utiliser des appels SQL directs.

- [Comment vous effectuez des appels SQL directs vers la source de données](#_core_making_direct_sql_function_calls).

> [!NOTE]
> Ces informations s’appliquent aux classes ODBC MFC. Si vous travaillez avec les classes MFC DAO, consultez le thème "Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL" dans DAO Help.

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Quand appeler SQL directement

Pour créer de nouvelles tables, déposer (supprimer) des tables, modifier les tableaux existants, créer des index et effectuer d’autres fonctions SQL qui modifient le schéma [source de données (ODBC),](../../data/odbc/data-source-odbc.md) vous devez émettre une déclaration SQL directement à la source de données à l’aide de la langue de définition de base de données (DDL). Lorsque vous utilisez un assistant pour créer un jeu d’enregistrements pour une table (au moment de la conception), vous pouvez choisir les colonnes de la table à représenter dans l’enregistrement. Cela ne permet pas aux colonnes que vous ou un autre utilisateur de la source de données ajoutez à la table plus tard, après la compilation de votre programme. Les classes de base de données ne prennent pas en charge directement DDL, mais vous pouvez toujours écrire du code pour lier une nouvelle colonne à votre dossier dynamiquement, au moment de l’exécution. Pour plus d’informations sur la façon de faire cette liaison, voir [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Vous pouvez utiliser le DBMS lui-même pour modifier le schéma ou un autre outil qui vous permet d’effectuer des fonctions DDL. Vous pouvez également utiliser les appels de fonction ODBC pour envoyer des relevés SQL, comme l’appel d’une requête prédéfinie (procédure stockée) qui ne renvoie pas les enregistrements.

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Faire des appels directs de fonction SQL

Vous pouvez exécuter directement un appel SQL à l’aide d’un objet [CDatabase Class.](../../mfc/reference/cdatabase-class.md) Configurez votre chaîne de déclaration `CString`SQL (généralement dans un ) et passez-la à la `CDatabase` base de [CData ::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) fonction membre de votre objet. Si vous utilisez des appels de fonction ODBC pour envoyer une déclaration SQL qui renvoie normalement les enregistrements, les dossiers sont ignorés.

## <a name="see-also"></a>Voir aussi

[SQL](../../data/odbc/sql.md)
