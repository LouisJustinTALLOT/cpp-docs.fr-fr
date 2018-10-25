---
title: SQL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 17403899d5ace5f4e5fd3263da936d6665e331a9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053252"
---
# <a name="sql"></a>SQL

SQL (Structured Query Language) est un moyen pour communiquer avec une base de données relationnelle qui vous permet de définir, interroger, de modifier et de contrôler les données. À l’aide de la syntaxe SQL, vous pouvez construire une instruction qui extrait des enregistrements en fonction des critères que vous spécifiez.

> [!NOTE]
>  Ces informations s’appliquent aux classes ODBC MFC. Si vous travaillez avec les classes DAO MFC, consultez la rubrique Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL dans l’aide de DAO.

Les instructions SQL commencent par un mot réservé tel que **créer** ou **sélectionnez**. SQL est un langage très puissant ; une seule instruction peut affecter une table entière.

Il existe autant de versions de SQL, chacun développé avec un SGBD particulier. Les classes de base de données MFC reconnaissent un ensemble d’instructions SQL qui correspond à X / Open et SQL de SQL Access groupe commun Applications environnement (IAO) le projet de spécification (1991). Pour plus d’informations sur la syntaxe de ces instructions, consultez l’annexe C dans le *ODBC SDK* *de référence du programmeur* sur le CD MSDN Library.

Cette rubrique explique :

- [La relation entre ODBC et SQL](#_core_open_database_connectivity_.28.odbc.29).

- [Les mots clés SQL plus couramment utilisées par les classes de base de données](#_core_the_database_classes).

- [Utilisent de SQL par les classes de base de données](#_core_how_the_database_classes_use_sql).

##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> Open Database Connectivity (ODBC)

Les classes de base de données sont implémentées avec ODBC, qui utilise SQL dans une interface de niveau d’appel, plutôt que d’intégrer des commandes SQL dans le code. ODBC utilise SQL pour communiquer avec un [source de données](../../data/odbc/data-source-odbc.md) via les pilotes ODBC. Ces pilotes interprètent le langage SQL et la traduisent, si nécessaire, pour une utilisation avec un format de base de données particulière, telle que Microsoft Access. Pour plus d’informations sur l’utilisation de SQL par ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md) et le SDK ODBC *de référence du programmeur* sur le CD MSDN Library.

##  <a name="_core_the_database_classes"></a> Classes de base de données

Les classes de base de données sont conçues pour vous permettre de manipuler et mettre à jour des données dans une existante [source de données](../../data/odbc/data-source-odbc.md). Le [Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md), le [Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (accessibles via **ajouter une classe**), et les classes de base de données construisent la plupart des instructions SQL pour vous.

Les classes de base de données utilisent une partie de SQL connu en tant que le langage DML (Data Manipulation). Ces commandes vous permettent de travailler avec tout ou partie de la source de données, ajouter de nouveaux enregistrements, modifier des enregistrements et supprimer des enregistrements. Le tableau suivant répertorie les mots clés SQL courants et les façons les classes de base de données utilisent.

### <a name="some-common-sql-keywords"></a>Certains mots clés SQL courants

|Mot clé SQL|Utilisent les Assistants et les classes de base de données|
|-----------------|---------------------------------------------|
|**SELECT**|Pour identifier les tables et les colonnes dans la source de données doivent être utilisées.|
|**WHERE**|Pour appliquer un filtre qui restreint la sélection.|
|**ORDER BY**|Pour appliquer un ordre de tri pour le jeu d’enregistrements.|
|**INSERT**|Pour ajouter de nouveaux enregistrements à un jeu d’enregistrements.|
|**SUPPRIMER**|Pour supprimer des enregistrements à partir d’un jeu d’enregistrements.|
|**MISE À JOUR**|Pour modifier les champs d’un enregistrement.|

En outre, les classes de base de données reconnaissent ODBC **appeler** les instructions, vous pouvez utiliser pour appeler une requête prédéfinie (ou procédure stockée) sur certaines sources de données. Le pilote de base de données ODBC interprète les instructions et les remplace par la commande appropriée pour chaque SGBD.

> [!NOTE]
>  Prise en charge pas toutes des SGBD **appeler** instructions.

Si les classes ne peut pas reconnaître une instruction fournie par l’utilisateur dans `CRecordset::Open`, il est interprété comme un nom de table.

Pour obtenir une explication de la façon dont le framework construit des instructions SQL, consultez [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) et [SQL : personnalisation du Recordset SQL instruction (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Bases de données SQL utilisent des types de données similaires à ceux utilisés dans C et C++. Pour une description de ces similitudes, consultez [SQL : SQL et les Types de données C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Vous trouverez plus d’informations sur SQL, y compris une liste des instructions SQL prises en charge, les types de données, grammaire SQL principale et une liste de lecture de publications recommandées sur SQL, dans le *ODBC SDK* *de référence du programmeur*  sur le CD MSDN Library.

##  <a name="_core_how_the_database_classes_use_sql"></a> Utilisent de SQL par les Classes de base de données

Les jeux d’enregistrements que vous dérivez à partir des classes de base de données utilise ODBC pour communiquer avec une source de données et ODBC extrait les enregistrements à partir de la source de données en envoyant des instructions SQL. Cette rubrique explique la relation entre les classes de base de données et SQL.

Un jeu d’enregistrements crée une instruction SQL en ajoutant les éléments d’une instruction SQL dans un `CString`. La chaîne est construite comme un **sélectionnez** instruction, qui retourne un jeu d’enregistrements.

Lorsque le jeu d’enregistrements appelle ODBC pour envoyer une instruction SQL à la source de données, le Gestionnaire de pilotes ODBC transmet l’instruction au pilote ODBC et le pilote envoie au SGBD sous-jacent. Le SGBD renvoie un jeu de résultats d’enregistrements et le pilote ODBC retourne les enregistrements à l’application. Les classes de base de données permettent à vos programmes par le jeu de résultats dans une classe C++ de type sécurisé dérivé `CRecordset`.

Les rubriques suivantes fournissent plus d’informations sur l’utilisent de SQL par les classes de base de données :

- [SQL : Personnalisation instruction SQL de votre jeu d’enregistrements (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL : types de données SQL et C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)