---
title: Accès aux données XML
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: 437f1d103420ec5727294894c02587c68cffbdda
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509129"
---
# <a name="accessing-xml-data"></a>Accès aux données XML

Il existe deux méthodes distinctes pour récupérer des données XML à partir d’une source de données : l’une utilise [CStreamRowset](../../data/oledb/cstreamrowset-class.md) et l’autre la [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).

|Fonctionnalités|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|Quantité de données transférées|Récupère des données de toutes les colonnes et lignes à la fois.|Récupère des données de toutes les colonnes, mais une seule ligne à la fois. Vous devez parcourir les lignes à l’aide de méthodes telles que `MoveNext` .|
|Mise en forme de la chaîne|SQL Server met en forme la chaîne XML et l’envoie au consommateur.|Récupère les données de l’ensemble de lignes dans son format natif (demande que le fournisseur l’envoie en tant que chaînes Unicode), puis génère la chaîne contenant les données au format XML.|
|Contrôle de la mise en forme|Vous disposez d’un certain niveau de contrôle sur la façon dont la chaîne XML est mise en forme en définissant des propriétés spécifiques à SQL Server 2000.|Vous n’avez aucun contrôle sur le format de la chaîne XML générée.|

Bien que `CStreamRowset` offre un moyen plus efficace d’extraire des données au format XML, il est uniquement pris en charge par SQL Server 2000.

## <a name="retrieving-xml-data-using-cstreamrowset"></a>Récupération de données XML à l’aide de CStreamRowset

Vous spécifiez [CStreamRowset](../../data/oledb/cstreamrowset-class.md) comme type d’ensemble de lignes dans votre `CCommand` `CTable` déclaration ou. Vous pouvez l’utiliser avec votre propre accesseur ou aucun accesseur, par exemple :

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

-ou-

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

Normalement, lorsque vous appelez `CCommand::Open` (en spécifiant, par exemple, `CRowset` comme `TRowset` classe), il obtient un `IRowset` pointeur. `ICommand::Execute` retourne un `IRowset` pointeur, qui est stocké dans le `m_spRowset` membre de l' `CRowset` objet. Les méthodes telles que `MoveFirst` , `MoveNext` et `GetData` utilisent ce pointeur pour récupérer les données.

En revanche, quand vous appelez `CCommand::Open` (mais que vous spécifiez `CStreamRowset` comme `TRowset` classe), `ICommand::Execute` retourne un `ISequentialStream` pointeur, qui est stocké dans la `m_spStream` donnée membre de [CStreamRowset](../../data/oledb/cstreamrowset-class.md). Vous utilisez ensuite la `Read` méthode pour récupérer les données (chaîne Unicode) au format XML. Par exemple :

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 effectue la mise en forme XML et retourne toutes les colonnes et toutes les lignes de l’ensemble de lignes sous la forme d’une chaîne XML.

Pour obtenir un exemple d’utilisation de la `Read` méthode, consultez **Ajout de la prise en charge XML au consommateur** lors de l' [implémentation d’un consommateur simple](../../data/oledb/implementing-a-simple-consumer.md).

> [!NOTE]
> La prise en charge XML à l’aide `CStreamRowset` de fonctionne avec SQL Server 2000 uniquement et nécessite que vous disposiez du fournisseur OLE DB pour SQL Server 2000 (installé avec MDAC).

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Récupération de données XML à l’aide de CXMLAccessor

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) vous permet d’accéder aux données d’une source de données en tant que données de chaîne lorsque vous n’avez aucune connaissance du schéma de la Banque de données. `CXMLAccessor` fonctionne comme `CDynamicStringAccessorW` , sauf que la première convertit toutes les données accessibles depuis le magasin de données en tant que données au format XML (balisées). Les noms de balises XML correspondent le mieux possible aux noms de colonnes de la Banque de données.

Utilisez `CXMLAccessor` comme vous le feriez pour toute autre classe d’accesseur, en la transmettant en tant que paramètre de modèle à `CCommand` ou `CTable` :

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

Utilisez [GetXMLRowData](./cxmlaccessor-class.md#getxmlrowdata) pour récupérer des données de la table une ligne à la fois et parcourez les lignes à l’aide de méthodes telles que `MoveNext` , par exemple :

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

Vous pouvez utiliser [GetXMLColumnData](./cxmlaccessor-class.md#getxmlcolumndata) pour récupérer les informations de colonne (type de données) en tant que données de chaîne au format XML.

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
