---
title: Créer par programmation une table dans une source de données ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 25c975560d6a73ce67294d97830b2f5bec9cd635
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213276"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Source de données : création d'une table par programme dans une source de données ODBC

Cette rubrique explique comment créer une table pour votre source de données, à l’aide de la fonction membre `ExecuteSQL` de la classe `CDatabase`, en passant à la fonction une chaîne qui contient une instruction SQL **Create table** .

Pour obtenir des informations générales sur les sources de données ODBC dans MFC, consultez [source de données (ODBC)](../../data/odbc/data-source-odbc.md). La rubrique [source de données : configuration d’une source de données ODBC par programmation](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) décrit la création de sources de données.

Une fois la source de données établie, vous pouvez facilement créer des tables à l’aide de la fonction membre `ExecuteSQL` et de l’instruction SQL **Create table** . Par exemple, si vous avez un objet `CDatabase` nommé `myDB`, vous pouvez utiliser le code MFC suivant pour créer une table :

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Cet exemple de code crée une table appelée « bureaux » dans la connexion à la source de données Microsoft Access conservée par `myDB`; la table contient deux champs « OfficeID » et « OfficeName ».

> [!NOTE]
>  Les types de champs spécifiés dans la **Create table** instruction SQL peuvent varier en fonction du pilote ODBC que vous utilisez. Le programme Microsoft Query (distribué avec Visual C++ 1,5) est un moyen de découvrir les types de champ disponibles pour une source de données. Dans Microsoft Query, cliquez sur **fichier**, sur **Table_Definition**, sélectionnez une table à partir d’une source de données, puis examinez le type affiché dans la zone de liste déroulante **type** . La syntaxe SQL existe également pour créer des index.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)
