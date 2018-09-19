---
title: Accès aux données XML | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cfde3980e58ba86d6923eaac765332a23e40ad7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062499"
---
# <a name="accessing-xml-data"></a>Accès aux données XML

Il existe deux méthodes distinctes de la récupération de données XML à partir d’une source de données : une utilise [CStreamRowset](../../data/oledb/cstreamrowset-class.md) et les autres utilisations [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).  
  
|Fonctionnalité|CStreamRowset|CXMLAccessor|  
|-------------------|-------------------|------------------|  
|Quantité de données transférées|Récupère les données de toutes les colonnes et lignes à la fois.|Récupère les données de toutes les colonnes, mais qu’une seule ligne à la fois. Vous devez accéder à l’aide de méthodes telles que des lignes `MoveNext`.|  
|La chaîne de mise en forme|SQL Server met en forme la chaîne XML et l’envoie au consommateur.|Récupère les données de l’ensemble de lignes dans son format natif (demande que le fournisseur de l’envoyer en tant que chaînes Unicode), puis génère la chaîne contenant les données au format XML.|  
|Contrôler la mise en forme|Vous avez un certain niveau de contrôle sur la façon dont la chaîne XML est mise en forme en définissant certaines propriétés spécifiques à SQL Server 2000.|Vous n’avez aucun contrôle sur le format de la chaîne XML générée.|  
  
Bien que `CStreamRowset` fournit plus globalement une méthode efficace de récupération de données au format XML, il est uniquement pris en charge par SQL Server 2000.  
  
## <a name="retrieving-xml-data-using-cstreamrowset"></a>Récupération des données XML à l’aide de CStreamRowset  

Vous spécifiez [CStreamRowset](../../data/oledb/cstreamrowset-class.md) en tant que le type d’ensemble de lignes dans votre `CCommand` ou `CTable` déclaration. Vous pouvez l’utiliser avec votre propre accesseur ou sans accesseur, par exemple :  
  
```cpp  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
- ou -  
  
```cpp  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
Normalement, lorsque vous appelez `CCommand::Open` (en spécifiant, par exemple, `CRowset` en tant que le `TRowset` classe), il obtient un `IRowset` pointeur. `ICommand::Execute` Retourne un `IRowset` pointeur, qui est stocké dans le `m_spRowset` membre de la `CRowset` objet. Méthodes telles que `MoveFirst`, `MoveNext`, et `GetData` utilisent ce pointeur pour récupérer les données.  
  
En revanche, lorsque vous appelez `CCommand::Open` (mais spécifiez `CStreamRowset` en tant que le `TRowset` classe), `ICommand::Execute` retourne un `ISequentialStream` pointeur, qui est stocké dans le `m_spStream` membre de données de [CStreamRowset](../../data/oledb/cstreamrowset-class.md). Vous utilisez ensuite le `Read` méthode pour récupérer les données (chaîne Unicode) au format XML. Exemple :  
  
```cpp  
myCmd.m_spStream->Read()  
```  
  
SQL Server 2000 effectue la mise en forme XML et retourne toutes les colonnes et toutes les lignes de l’ensemble de lignes sous forme de chaîne XML.  
  
Pour obtenir un exemple utilisant le `Read` (méthode), consultez la section « Ajout de la prise en charge XML au consommateur » dans [implémentation d’un consommateur Simple](../../data/oledb/implementing-a-simple-consumer.md).  
  
> [!NOTE]
>  Prise en charge de XML à l’aide de `CStreamRowset` fonctionne uniquement avec SQL Server 2000 et vous devez disposer du fournisseur OLE DB pour SQL Server 2000 (installé avec MDAC).  
  
## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Récupération des données XML à l’aide de CXMLAccessor  

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) vous permet d’accéder aux données à partir d’une source de données en tant que données de chaîne lorsque vous n’avez aucune connaissance du schéma du magasin de données. `CXMLAccessor` fonctionne comme `CDynamicStringAccessorW` , à ceci près que ce dernier convertit toutes les données accédées à partir du magasin de données au format XML (référencé). Les noms de balise XML correspondent aussi fidèlement que possible les noms de colonnes du magasin de données.  
  
Utilisez `CXMLAccessor` comme vous le feriez pour toute autre classe d’accesseur, en lui passant comme paramètre de modèle à `CCommand` ou `CTable`:  
  
```cpp  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
Utilisez [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) pour récupérer des données à partir de la table une ligne à la fois et parcourir les lignes à l’aide de méthodes telles que `MoveNext`, par exemple :  
  
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
  
Vous pouvez utiliser [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) pour récupérer les informations de colonne (type de données) en tant que données de chaîne au format XML.  
  
## <a name="see-also"></a>Voir aussi  

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)