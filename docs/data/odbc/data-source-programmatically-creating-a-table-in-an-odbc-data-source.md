---
title: Créer par programmation une Table dans une Source de données ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 61d3f3e39362db27d1e3abc00fa3cb9ea82b86e2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028397"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Source de données : Création d’une Table dans une Source de données ODBC par programmation

Cette rubrique explique comment créer une table pour vos données source, à l’aide de la `ExecuteSQL` fonction membre de classe `CDatabase`, en passant la fonction de chaîne qui contient un **CREATE TABLE** instruction SQL.

Pour obtenir des informations générales sur les sources de données ODBC dans MFC, consultez [Source de données (ODBC)](../../data/odbc/data-source-odbc.md). La rubrique [Source de données : Configuration d’une Source de données ODBC par programmation](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) décrit la création de sources de données.

Lorsque vous avez établi la source de données, vous pouvez facilement créer des tables à l’aide de la `ExecuteSQL` fonction membre et le **CREATE TABLE** instruction SQL. Par exemple, si vous aviez un `CDatabase` objet appelé `myDB`, vous pouvez utiliser le code MFC suivant pour créer une table :

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Cet exemple de code crée une table appelée « Bureaux » dans la connexion de source de données Microsoft Access gérée par `myDB`; la table contient deux champs « OfficeID » et « OfficeName ».

> [!NOTE]
>  Les types de champ spécifiés dans le **CREATE TABLE** instruction SQL peut varier selon le pilote ODBC que vous utilisez. Le programme Microsoft Query (livré avec Visual C++ 1.5) est une façon de découvrir les types de champ sont disponibles pour une source de données. Dans Microsoft Query, cliquez sur **fichier**, cliquez sur **définition_de_table**, sélectionnez une table dans une source de données et examiner le type indiqué dans le **Type** zone de liste déroulante. Il existe également la syntaxe SQL pour créer des index.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)