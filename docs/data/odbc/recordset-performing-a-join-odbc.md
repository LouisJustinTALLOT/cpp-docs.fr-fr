---
title: 'Recordset : Création d’une jointure (ODBC) | Documents Microsoft'
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
ms.openlocfilehash: 0be740a57f5c455b971dd23575401c666bf0723c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093309"
---
# <a name="recordset-performing-a-join-odbc"></a>Recordset : création d'une jointure (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
## <a name="what-a-join-is"></a>Ce qui est d’une jointure  
 L’opération de jointure, une tâche courante de l’accès aux données, vous permet de travailler avec des données à partir de plusieurs tables à l’aide d’un seul objet recordset. La jointure de deux ou plusieurs tables génère un jeu d’enregistrements qui peut contenir des colonnes de chaque table, mais apparaît sous la forme d’une table unique pour votre application. Parfois, la jointure utilise toutes les colonnes de toutes les tables, mais parfois, l’instruction SQL **sélectionnez** clause dans une jointure utilise uniquement certaines colonnes de chaque table. Les classes de base de données prend en charge les jointures en lecture seule mais non les jointures modifiables.  
  
 Pour sélectionner des enregistrements contenant des colonnes de tables jointes, vous devez les éléments suivants :  
  
-   Une liste de tables contenant les noms de toutes les tables jointes.  
  
-   Contenant les noms de toutes les colonnes participant à une liste de colonnes. Les colonnes portant le même nom mais provenant de tables différentes sont qualifiées par le nom de table.  
  
-   Un filtre (SQL **où** clause) qui spécifie les colonnes sur lesquelles les tables sont jointes. Ce filtre prend la forme « Table1.KeyCol = Table2.KeyCol » et réellement effectue la jointure.  
  
 Vous pouvez joindre plus de deux tables de la même façon en associant plusieurs paires de colonnes, chaque paire étant jointe par le mot clé SQL **AND**.  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [Recordset : Déclaration de la classe d’une Table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Recordset : lancement d’une nouvelle requête sur un recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)