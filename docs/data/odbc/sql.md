---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: 58c0267728f2b26cf81d048fcf02edd8fc4909ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212563"
---
# <a name="sql"></a>SQL

SQL (Structured Query Language) est un moyen de communiquer avec une base de données relationnelle qui vous permet de définir, d’interroger, de modifier et de contrôler les données. À l’aide de la syntaxe SQL, vous pouvez construire une instruction qui extrait des enregistrements en fonction de critères que vous spécifiez.

> [!NOTE]
>  Ces informations s’appliquent aux classes ODBC MFC. Si vous utilisez les classes DAO MFC, consultez la rubrique Comparaison SQL entre le moteur de base de données Microsoft Jet et ANSI dans l’aide de DAO.

Les instructions SQL commencent par un verbe mot clé de type **CREATE** ou **SELECT**. SQL est un langage très puissant : une seule instruction peut affecter une table entière.

Il existe de nombreuses versions de SQL, chacune développée avec un SGBD particulier. Les classes de base de données MFC reconnaissent un ensemble d’instructions SQL qui correspondent au projet de spécification SQL CAE (Common Applications Environment) de X/Open et SQL Access Group (1991). Pour plus d’informations sur la syntaxe de ces instructions, consultez l’annexe C dans le *Guide de référence du programmeur* *ODBC SDK* sur le CD-ROM de MSDN Library.

Cette rubrique explique :

- [La relation entre ODBC et SQL](#_core_open_database_connectivity_.28.odbc.29).

- [Les mots clés SQL les plus couramment utilisés par les classes de base de données](#_core_the_database_classes).

- [Comment les classes de base de données utilisent SQL](#_core_how_the_database_classes_use_sql).

##  <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a> Open Database Connectivity (ODBC)

Les classes de base de données sont implémentées avec ODBC, qui utilise SQL dans une interface CLI au lieu d’incorporer des commandes SQL dans le code. ODBC utilise SQL pour communiquer avec une [source de données](../../data/odbc/data-source-odbc.md) par le biais de pilotes ODBC. Ces pilotes interprètent le langage SQL et le traduisent, si nécessaire, pour pouvoir l’utiliser avec un format de base de données particulier, comme Microsoft Access. Pour plus d’informations sur l’utilisation de SQL par ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md) et les *Informations de référence du programmeur* du SDK ODBC sur le CD MSDN Library.

##  <a name="database-classes"></a><a name="_core_the_database_classes"></a> Classes de base de données

> [!NOTE]
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez quand même créer un consommateur manuellement.

Les classes de base de données sont conçues pour vous permettre de manipuler et mettre à jour des données dans une [source de données](../../data/odbc/data-source-odbc.md) existante. L’[Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md), l’[Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (accessibles via **Ajouter une classe**) et les classes de base de données construisent la plupart des instructions SQL pour vous.

Les classes de base de données utilisent une partie de SQL connue sous le nom de langage de manipulation de données (DML). Ces commandes vous permettent d’utiliser tout ou partie de la source de données, d’ajouter de nouveaux enregistrements, de modifier des enregistrements et de supprimer des enregistrements. Le tableau suivant liste les mots clés SQL les plus courants et la façon dont les classes de base de données les utilisent.

### <a name="some-common-sql-keywords"></a>Quelques mots clés SQL courants

|Mot clé SQL|Les Assistants et les classes de base de données l’utilisent|
|-----------------|---------------------------------------------|
|**SELECT**|Pour identifier les tables et les colonnes de la source de données qui doivent être utilisées.|
|**WHERE**|Pour appliquer un filtre qui réduit la sélection.|
|**ORDER BY**|Pour appliquer un ordre de tri au recordset.|
|**INSERT**|Pour ajouter de nouveaux enregistrements à un recordset.|
|**DELETE**|Pour supprimer des enregistrements dans un recordset.|
|**UPDATE**|Pour modifier les champs d’un enregistrement.|

Par ailleurs, comme les classes de base de données reconnaissent les instructions **CALL** ODBC, vous pouvez les utiliser pour appeler une requête prédéfinie (ou procédure stockée) sur certaines sources de données. Le pilote de base de données ODBC interprète ces instructions et les remplace par la commande appropriée pour chaque SGBD.

> [!NOTE]
>  Les SGBD ne prennent pas tous en charge les instructions **CALL**.

Si les classes ne peuvent pas reconnaître une instruction fournie par l’utilisateur dans `CRecordset::Open`, elle est interprétée comme un nom de table.

Pour obtenir une explication de la façon dont l’infrastructure construit des instructions SQL, consultez [Recordset : comment les recordsets sélectionnent les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) et [SQL : personnalisation de l’instruction SQL du recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Les bases de données SQL utilisent des types de données similaires à ceux utilisés en C et C++. Pour une description de ces similarités, consultez [SQL : SQL et C++ types de données (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Vous trouverez plus d’informations sur SQL, notamment la liste des instructions SQL prises en charge, les types de données, la grammaire de base SQL et une liste de lectures des publications recommandées sur SQL, dans le *Guide de référence du programmeur* *ODBC SDK* sur le CD de MSDN Library.

##  <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a> Comment les classes de base de données utilisent SQL

Les recordsets que vous dérivez des classes de base de données utilisent ODBC pour communiquer avec une source de données, et ODBC récupère les enregistrements de la source de données en envoyant des instructions SQL. Cette rubrique explique la relation entre les classes de base de données et SQL.

Un recordset construit une instruction SQL en rassemblant les éléments d’une instruction SQL dans un `CString`. La chaîne est construite comme une instruction **SELECT**, qui retourne un jeu d’enregistrements.

Quand le recordset appelle ODBC pour envoyer une instruction SQL à la source de données, le Gestionnaire de pilotes ODBC transmet l’instruction au pilote ODBC, et le pilote l’envoie au SGBD sous-jacent. Le SGBD retourne le jeu d’enregistrements qui en résulte et le pilote ODBC retourne les enregistrements à l’application. Les classes de base de données permettent à votre programme d’accéder au jeu de résultats dans une classe C++ de type sécurisé à partir de `CRecordset`.

Les rubriques suivantes fournissent plus d’informations sur la façon dont les classes de base de données utilisent SQL :

- [SQL : personnalisation de l’instruction SQL de votre jeu d’enregistrements (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL : types de données SQL et C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)
