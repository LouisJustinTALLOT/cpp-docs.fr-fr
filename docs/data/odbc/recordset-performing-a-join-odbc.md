---
description: 'En savoir plus sur : Recordset : exécution d’une jointure (ODBC)'
title: "Recordset : création d'une jointure (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 1c7aa7bfb6925d9f7e916ddb6cd60061667d7859
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204509"
---
# <a name="recordset-performing-a-join-odbc"></a>Recordset : création d'une jointure (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

## <a name="what-a-join-is"></a>Qu’est-ce qu’une jointure ?

L’opération de jointure, une tâche d’accès aux données commune, vous permet d’utiliser des données provenant de plusieurs tables à l’aide d’un seul objet Recordset. La jointure de deux tables ou plus génère un jeu d’enregistrements qui peut contenir des colonnes de chaque table, mais apparaît sous la forme d’une table unique pour votre application. Parfois, la jointure utilise toutes les colonnes de toutes les tables, mais parfois la clause SQL **Select** dans une jointure utilise uniquement certaines des colonnes de chaque table. Les classes de base de données prennent en charge les jointures en lecture seule, mais pas les jointures modifiables.

Pour sélectionner des enregistrements contenant des colonnes de tables jointes, vous avez besoin des éléments suivants :

- Liste de tables contenant les noms de toutes les tables jointes.

- Liste de colonnes contenant les noms de toutes les colonnes participantes. Les colonnes portant le même nom mais provenant de tables différentes sont qualifiées par le nom de la table.

- Filtre (clause SQL **Where** ) qui spécifie les colonnes sur lesquelles les tables sont jointes. Ce filtre prend la forme « table1. KeyCol = table2. KeyCol » et accomplit la jointure.

Vous pouvez joindre plus de deux tables de la même façon en assimilant plusieurs paires de colonnes, chaque paire jointe par le mot clé SQL **et**.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : déclaration d’une classe pour une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Recordset : déclaration d’une classe pour une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Recordset : rerequête d’un Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)
