---
description: 'En savoir plus sur : source de données : création d’une table par programmation dans une source de données ODBC'
title: Créer par programmation une table dans une source de données ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: b195cc4fb81f1caed0b280c5df6a2032f4944ddf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155707"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Source de données : création d'une table par programme dans une source de données ODBC

Cette rubrique explique comment créer une table pour votre source de données, à l’aide `ExecuteSQL` de la fonction membre de la classe `CDatabase` , en passant à la fonction une chaîne qui contient une **Create table** instruction SQL.

Pour obtenir des informations générales sur les sources de données ODBC dans MFC, consultez [source de données (ODBC)](../../data/odbc/data-source-odbc.md). La rubrique [source de données : configuration d’une source de données ODBC par programmation](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) décrit la création de sources de données.

Une fois la source de données établie, vous pouvez facilement créer des tables à l’aide de la `ExecuteSQL` fonction membre et de l’instruction SQL **Create table** . Par exemple, si vous avez un `CDatabase` objet appelé `myDB` , vous pouvez utiliser le code MFC suivant pour créer une table :

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Cet exemple de code crée une table appelée « bureaux » dans la connexion à la source de données Microsoft Access gérée par `myDB` ; la table contient deux champs « OfficeId » et « OfficeName ».

> [!NOTE]
> Les types de champs spécifiés dans la **Create table** instruction SQL peuvent varier en fonction du pilote ODBC que vous utilisez. Le programme Microsoft Query (distribué avec Visual C++ 1,5) est un moyen de découvrir les types de champ disponibles pour une source de données. Dans Microsoft Query, cliquez sur **fichier**, sur **Table_Definition**, sélectionnez une table à partir d’une source de données, puis examinez le type affiché dans la zone de liste déroulante **type** . La syntaxe SQL existe également pour créer des index.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)
