---
title: 'Recordset : Création d’une jointure (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e033a300a023b3460fb27ced7cd4bae99ebd0b92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097888"
---
# <a name="recordset-performing-a-join-odbc"></a>Recordset : création d'une jointure (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.  
  
## <a name="what-a-join-is"></a>Ce qui est une jointure  

L’opération de jointure, une tâche très courante de l’accès aux données, vous permet de travailler avec des données à partir de plusieurs tables à l’aide d’un seul objet recordset. La jointure de deux ou plusieurs tables génère un jeu d’enregistrements qui peut contenir des colonnes de chaque table, mais apparaît sous la forme d’une table unique à votre application. Parfois, la jointure utilise toutes les colonnes de toutes les tables, mais parfois, le code SQL **sélectionnez** clause dans une jointure utilise uniquement certaines colonnes de chaque table. Les classes de base de données prend en charge les jointures en lecture seule mais non les jointures modifiables.  
  
Pour sélectionner les enregistrements contenant des colonnes de tables jointes, vous avez besoin des éléments suivants :  
  
- Une liste de tables contenant les noms de toutes les tables jointes.  
  
- Une liste de colonnes contenant les noms de toutes les colonnes participantes. Les colonnes portant le même nom mais provenant de tables différentes sont qualifiés par le nom de table.  
  
- Un filtre (SQL **où** clause) qui spécifie les colonnes sur lesquelles les tables sont jointes. Ce filtre prend la forme « Table1.KeyCol = Table2.KeyCol » et effectue réellement la jointure.  
  
Vous pouvez joindre des plus de deux tables de la même façon en associant plusieurs paires de colonnes, chaque paire étant jointe par le mot clé SQL **AND**.  
  
## <a name="see-also"></a>Voir aussi  

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Recordset : déclaration de la classe d’une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Recordset : lancement d’une nouvelle requête sur un recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)