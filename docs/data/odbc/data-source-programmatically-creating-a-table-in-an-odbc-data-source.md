---
title: Créer un tableau programmatique dans une source de données ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 6cf26cad7fe39f374daf371902525087b446658c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358835"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Source de données : création d'une table par programme dans une source de données ODBC

Ce sujet explique comment créer une table pour `ExecuteSQL` votre source `CDatabase`de données, en utilisant la fonction membre de la classe, en passant la fonction d’une chaîne qui contient une déclaration **CREATE TABLE** SQL.

Pour obtenir de l’information générale sur les sources de données ODBC dans MFC, voir [Data Source (ODBC)](../../data/odbc/data-source-odbc.md). Le sujet [Source de données : Configurer programmatiquement une source de données ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) décrit la création de sources de données.

Lorsque vous avez la source de données établie, vous pouvez facilement créer des tables en utilisant la `ExecuteSQL` fonction membre et la déclaration CREATE **TABLE** SQL. Par exemple, si `CDatabase` vous `myDB`aviez un objet appelé, vous pouvez utiliser le code MFC suivant pour créer une table :

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Cet exemple de code crée un tableau appelé "OFFICES" `myDB`dans la connexion de source de données Microsoft Access maintenue par ; la table contient deux domaines "OfficeID" et "OfficeName".

> [!NOTE]
> Les types de terrain spécifiés dans l’instruction **CREATE TABLE** SQL peuvent varier selon le conducteur ODBC que vous utilisez. Le programme Microsoft Query (distribué avec Visual C 1.5) est une façon de découvrir quels types de terrain sont disponibles pour une source de données. Dans Microsoft Query, cliquez sur **Fichier**, cliquez **Table_Definition**, sélectionnez une table à partir d’une source de données, et regardez le type indiqué dans la boîte combo **Type.** La syntaxe SQL existe également pour créer des index.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)
