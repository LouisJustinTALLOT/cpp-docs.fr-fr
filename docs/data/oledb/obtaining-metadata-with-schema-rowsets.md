---
title: Obtention de métadonnées avec les ensembles de lignes de schéma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7b131119f5f6207feccec3c683a470a8b099de12
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207840"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Récupération de métadonnées à l'aide de jeux de lignes du schéma
Vous avez parfois besoin d'obtenir des informations sur le fournisseur, un ensemble de lignes, une table, des colonnes ou d'autres informations de base de données sans ouvrir l'ensemble de lignes. Les données relatives à la structure de base de données s'appellent des métadonnées et peuvent être récupérées par différentes méthodes. L'une d'elles consiste à utiliser des ensembles de lignes de schéma.  
  
 Modèles OLE DB fournissent un ensemble de classes à récupérer des informations de schéma. Ces classes créent des ensembles de lignes de schéma prédéfinis et sont répertoriés dans [Classes d’ensemble de lignes de schéma et Classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
> [!NOTE]
>  Si vous utilisez OLAP et que certains de vos ensembles de lignes ne sont pas pris en charge par les classes d'ensembles de lignes de schéma (par exemple, si vous avez un nombre variable de colonnes), envisagez d'utiliser `CManualAccessor` ou `CDynamicAccessor`. Vous pouvez parcourir les colonnes et utiliser des instructions case pour gérer les types de données possibles de chaque colonne.  
  
## <a name="catalogschema-model"></a>Modèle catalogue/schéma  
 SQL ANSI définit un modèle catalogue/schéma pour les magasins de données ; OLE DB utilise ce modèle. Dans ce modèle, les catalogues (bases de données) contiennent des schémas et les schémas contiennent des tables.  
  
-   **Catalogue** un catalogue est un autre nom pour une base de données. Il s’agit d’une collection de schémas associés. Pour répertorier les catalogues (bases de données) appartenant à une source de données, utilisez [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Dans la mesure où la plupart des bases de données n'ont qu'un seul catalogue, les métadonnées sont parfois simplement appelées informations de schéma.  
  
-   **Schéma** un schéma est une collection d’objets de base de données qui appartiennent ou ont été créés par un utilisateur particulier. Pour répertorier les schémas appartenant à un utilisateur donné, utilisez [CSchemata](../../data/oledb/cschemata-cschematainfo.md).  
  
     Dans la terminologie Microsoft SQL Server et ODBC 2.x, un schéma est un propriétaire (par exemple, dbo est un nom de schéma type). En outre, SQL Server stocke les métadonnées dans un ensemble de tables : une table contient une liste de toutes les tables et une autre table contient une liste de toutes les colonnes. Il n'existe pas d'équivalent à un schéma dans une base de données Microsoft Access.  
  
-   **Table** Tables sont des collections de colonnes organisées dans un ordre spécifique. Pour répertorier les tables définies dans un catalogue donné (base de données) et des informations sur ces tables, utilisez [CTables](../../data/oledb/ctables-ctableinfo.md)).  
  
## <a name="restrictions"></a>Restrictions  
 Quand il s'agit de rechercher des informations de schéma, vous pouvez utiliser des restrictions pour spécifier le type d'information qui vous intéresse. Les restrictions s'apparentent à un filtre ou à un qualificateur de requête. Par exemple, dans la requête suivante :  
  
```sql  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name` est une restriction. Il s'agit d'un exemple très simple à une seule restriction ; les classes d'ensembles de lignes de schéma prennent en charge plusieurs restrictions.  
  
 Le [classes typedef d’ensemble de lignes de schéma](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) encapsulent tous les ensembles de lignes du schéma OLE DB afin que vous pouvez accéder à un ensemble de lignes de schéma comme n’importe quel autre ensemble de lignes en l’instanciant et en l’ouvrant. Par exemple, la classe typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) est défini comme :  
  
```cpp  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 Le [CRestrictions](../../data/oledb/crestrictions-class.md) classe fournit la prise en charge de la restriction. Après avoir créé une instance de l’ensemble de lignes du schéma, appelez [CRestrictions::Open](../../data/oledb/crestrictions-open.md). Cette méthode retourne un jeu de résultats basé sur les restrictions que vous spécifiez.  
  
 Pour spécifier des restrictions, consultez [annexe b : Schema Rowsets](/previous-versions/windows/desktop/ms712921\(v=vs.85\)) et rechercher l’ensemble de lignes que vous utilisez. Par exemple, `CColumns` correspond à la [ensemble de lignes COLUMNS](/previous-versions/windows/desktop/ms723052\(v%3dvs.85\)); cette rubrique répertorie les colonnes de restriction de l’ensemble de lignes COLUMNS : TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME. Vous devez suivre cet ordre quand vous spécifiez vos restrictions.  
  
 Par conséquent, par exemple, si vous souhaitez limiter par nom de table, notez que TABLE_NAME est la troisième colonne de restriction, puis appelez `Open`, spécifiant le nom de table voulue comme troisième paramètre de restriction, comme indiqué dans l’exemple suivant.  
  
#### <a name="to-use-schema-rowsets"></a>Pour utiliser des ensembles de lignes de schéma  
  
1.  Vous devez inclure le fichier d'en-tête Atldbsch.h (bien entendu, vous avez aussi besoin d'Atldbcli.h pour la prise en charge du consommateur).  
  
2.  Instanciez un objet ensemble de lignes de schéma dans le fichier d'en-tête du consommateur ou du document. Si vous souhaitez des informations sur les tables, déclarez un `CTables` l’objet ; si vous souhaitez des informations sur les colonnes, déclarez un `CColumns` objet. Cet exemple montre comment récupérer les colonnes de la table « authors » :  
  
    ```cpp  
    CDataSource ds;  
    ds.Open();  
    CSession ss;  
    ss.Open();  
    CColumns ColumnSchemaRowset;  
    // TABLE_NAME is the third restriction column, so  
    // specify "authors" as the third restriction parameter:  
    hr = ColumnSchemaRowset.Open(ss, NULL, NULL, "authors");  
    hr = ColumnSchemaRowset.MoveFirst();  
    while (hr == S_OK)  
    {  
       hr = ColumnSchemaRowset.MoveNext();  
    }  
    ```  
  
3.  Pour extraire les informations, accédez au membre de données approprié de l'objet ensemble de lignes de schéma, par exemple, `ColumnSchemaRowset.m_szColumnName`. Il s'agit ici de COLUMN_NAME. Pour voir quelle colonne OLE DB correspond chaque membre de données, consultez [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).  
  
 Pour la référence de l’ensemble de lignes de schéma, les classes typedef fournies dans les modèles OLE DB (consultez [Classes d’ensemble de lignes de schéma et Classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).  
  
 Pour plus d’informations sur les ensembles de lignes de schéma OLE DB, y compris les colonnes de restriction, consultez [annexe b : Schema Rowsets](/previous-versions/windows/desktop/ms712921\(v=vs.85\)) dans la référence du programmeur OLE DB.  
  
 Pour obtenir des exemples plus complexes de l’utilisation des classes de jeu de lignes de schéma, consultez le [CatDB](https://github.com/Microsoft/VCSamples) et [DBViewer](https://github.com/Microsoft/VCSamples) exemples.  
  
 Pour plus d’informations sur la prise en charge du fournisseur d’ensembles de lignes de schéma, consultez [prenant en charge les ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des accesseurs](../../data/oledb/using-accessors.md)