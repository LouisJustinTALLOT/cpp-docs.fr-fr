---
title: Créer par programmation une Table dans une Source de données ODBC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9917e6885e1c15950032bfd5ca983cc932c44a3c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064834"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Source de données : création d'une table par programme dans une source de données ODBC

Cette rubrique explique comment créer une table pour vos données source, à l’aide de la `ExecuteSQL` fonction membre de classe `CDatabase`, en passant la fonction de chaîne qui contient un **CREATE TABLE** instruction SQL.

Pour obtenir des informations générales sur les sources de données ODBC dans MFC, consultez [Source de données (ODBC)](../../data/odbc/data-source-odbc.md). La rubrique [Source de données : configuration d’une Source de données ODBC par programmation](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) décrit la création de sources de données.

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