---
description: 'En savoir plus sur : obtention de métadonnées avec des ensembles de lignes de schéma'
title: Récupération de métadonnées à l'aide de jeux de lignes du schéma
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: 9692b27de6d949e23b3868b2c55b79b685d6b5fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317179"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Récupération de métadonnées à l'aide de jeux de lignes du schéma

Vous avez parfois besoin d'obtenir des informations sur le fournisseur, un ensemble de lignes, une table, des colonnes ou d'autres informations de base de données sans ouvrir l'ensemble de lignes. Les données relatives à la structure de base de données s'appellent des métadonnées et peuvent être récupérées par différentes méthodes. L'une d'elles consiste à utiliser des ensembles de lignes de schéma.

Les modèles de OLE DB fournissent un ensemble de classes pour récupérer des informations de schéma ; ces classes créent des ensembles de lignes de schéma prédéfinis et sont répertoriées dans [classes d’ensemble de lignes de schéma et classes typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

> [!NOTE]
> Si vous utilisez OLAP et que certains de vos ensembles de lignes ne sont pas pris en charge par les classes d'ensembles de lignes de schéma (par exemple, si vous avez un nombre variable de colonnes), envisagez d'utiliser `CManualAccessor` ou `CDynamicAccessor`. Vous pouvez parcourir les colonnes et utiliser des instructions case pour gérer les types de données possibles de chaque colonne.

## <a name="catalogschema-model"></a>Modèle catalogue/schéma

SQL ANSI définit un modèle catalogue/schéma pour les magasins de données ; OLE DB utilise ce modèle. Dans ce modèle, les catalogues (bases de données) ont des schémas et des schémas ont des tables.

- **Catalogue** Un catalogue est un autre nom pour une base de données. Il s’agit d’une collection de schémas associés. Pour répertorier les catalogues (bases de données) appartenant à une source de données donnée, utilisez [CCatalog](./schema-rowset-classes-and-typedef-classes.md#catalog). Étant donné que de nombreuses bases de données n’ont qu’un seul catalogue, les métadonnées sont parfois appelées informations de schéma.

- **Schéma** Un schéma est une collection d’objets de base de données qui sont détenus ou ont été créés par un utilisateur particulier. Pour répertorier les schémas appartenant à un utilisateur donné, utilisez [CSchemata](./schema-rowset-classes-and-typedef-classes.md#schemata).

   Dans la terminologie Microsoft SQL Server et ODBC 2.x, un schéma est un propriétaire (par exemple, dbo est un nom de schéma type). De même, SQL Server stocke les métadonnées dans un ensemble de tables : une de ces tables contient la liste de toutes les tables et une autre contient la liste de toutes les colonnes. Il n’existe pas d’équivalent à un schéma dans une base de données Microsoft Access.

- **Table** Les tables sont des collections de colonnes organisées dans des commandes spécifiques. Pour répertorier les tables définies dans un catalogue donné (base de données) et des informations sur ces tables, utilisez [CTables](./schema-rowset-classes-and-typedef-classes.md#table)).

## <a name="restrictions"></a>Restrictions

Lorsque vous recherchez des informations de schéma, vous pouvez utiliser des restrictions pour spécifier le type d’informations qui vous intéressent. Les restrictions s'apparentent à un filtre ou à un qualificateur de requête. Par exemple, dans la requête suivante :

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` est une restriction. Il s’agit d’un exemple simple avec une seule restriction ; les classes d’ensemble de lignes de schéma prennent en charge plusieurs restrictions.

Les [classes typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) de l’ensemble de lignes de schéma encapsulent tous les OLE DB ensembles de lignes de schéma afin que vous puissiez accéder à un ensemble de lignes de schéma comme n’importe quel autre ensemble de lignes en instanciant et en l’ouvrant. Par exemple, la classe typedef [CColumns](./schema-rowset-classes-and-typedef-classes.md#columns) est définie comme suit :

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

La classe [cRestrictions](../../data/oledb/crestrictions-class.md) fournit la prise en charge des restrictions. Après avoir créé une instance de l’ensemble de lignes de schéma, appelez [cRestrictions :: Open](./crestrictions-class.md#open). Cette méthode retourne un jeu de résultats basé sur les restrictions que vous spécifiez.

Pour spécifier des restrictions, reportez-vous à [l’annexe B : ensembles](/previous-versions/windows/desktop/ms712921(v=vs.85)) de lignes de schéma et recherchez l’ensemble de lignes que vous utilisez. Par exemple, `CColumns` correspond à l' [ensemble de lignes COLUMNS](/previous-versions/windows/desktop/ms723052(v=vs.85)); cette rubrique répertorie les colonnes de restriction dans l’ensemble de lignes columns : TABLE_CATALOG, TABLE_SCHEMA, table_name, column_name. Vous devez suivre cet ordre quand vous spécifiez vos restrictions.

Par exemple, si vous souhaitez restreindre par nom de table, TABLE_NAME est la troisième colonne de restriction, puis appelez, en `Open` spécifiant le nom de la table souhaitée comme troisième paramètre de restriction, comme indiqué dans l’exemple suivant.

### <a name="to-use-schema-rowsets"></a>Pour utiliser des ensembles de lignes de schéma

1. Incluez le fichier d’en-tête `Atldbsch.h` (vous avez besoin `Atldbcli.h` d’une prise en charge des consommateurs également).

1. Instanciez un objet ensemble de lignes de schéma dans le fichier d'en-tête du consommateur ou du document. Si vous souhaitez des informations de table, déclarez un `CTables` objet. Si vous souhaitez des informations sur les colonnes, déclarez un `CColumns` objet. Cet exemple montre comment récupérer les colonnes de la table « authors » :

    ```cpp
    CDataSource ds;
    ds.Open();
    CSession ss;
    ss.Open(ds);
    CColumns columnSchemaRowset;
    // TABLE_NAME is the third restriction column, so
    // specify "authors" as the third restriction parameter:
    HRESULT hr = columnSchemaRowset.Open(ss, NULL, NULL, L"authors");
    hr = columnSchemaRowset.MoveFirst();
    while (hr == S_OK)
    {
       hr = columnSchemaRowset.MoveNext();
    }
    ```

1. Pour récupérer les informations, accédez au membre de données approprié de l’objet ensemble de lignes de schéma, par exemple, `ColumnSchemaRowset.m_szColumnName`. Ce membre de données correspond à COLUMN_NAME. Pour connaître la OLE DB colonne à laquelle chaque membre de données correspond, consultez [CColumns](./schema-rowset-classes-and-typedef-classes.md#columns).

Pour obtenir la référence de l’ensemble de lignes de schéma, classes typedef fournies dans les modèles de OLE DB (consultez [classes d’ensemble de lignes de schéma et classes typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).

Pour plus d’informations sur les ensembles de lignes de schéma OLE DB, y compris les colonnes de restriction, consultez [l’annexe B : ensembles de lignes de schéma](/previous-versions/windows/desktop/ms712921(v=vs.85)) dans le **Guide de référence du programmeur OLE DB**.

Pour obtenir des exemples plus complexes sur l’utilisation des classes d’ensemble de lignes de schéma, consultez les exemples [CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) et [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

Pour plus d’informations sur la prise en charge des fournisseurs d’ensembles de lignes de schéma, consultez [prise en](../../data/oledb/supporting-schema-rowsets.md)charge des ensembles de lignes

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
