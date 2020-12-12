---
description: 'En savoir plus sur : accesseurs et ensembles de lignes'
title: Accesseurs et jeux de lignes
ms.date: 11/19/2018
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
ms.openlocfilehash: 5bda7957f808319de596edf51b6cb3e378c14254
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246108"
---
# <a name="accessors-and-rowsets"></a>Accesseurs et jeux de lignes

Pour définir et récupérer des données, OLE DB modèles utilisent un accesseur et un ensemble de lignes via la classe [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) . Cette classe peut gérer plusieurs accesseurs de types différents.

## <a name="accessor-types"></a>Types d’accesseurs

Tous les accesseurs dérivent de [CAccessorBase](../../data/oledb/caccessorbase-class.md). `CAccessorBase` fournit la liaison de paramètres et de colonnes.

L’illustration suivante montre les types d’accesseurs.

![Types d’accesseurs](../../data/oledb/media/vcaccessortypes.gif "Types d'accesseurs")<br/>
Classes d’accesseur

- [CAccessor](../../data/oledb/caccessor-class.md) Utilisez cet accesseur lorsque vous connaissez la structure de la source de base de données au moment de la conception. `CAccessor` lie statiquement un enregistrement de base de données, qui contient la mémoire tampon, à la source de données.

- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Utilisez cet accesseur lorsque vous ne connaissez pas la structure de la base de données au moment de la conception. `CDynamicAccessor` appelle `IColumnsInfo::GetColumnInfo` pour récupérer les informations de colonne de base de données. Il crée et gère un accesseur et la mémoire tampon.

- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) Utilisez cet accesseur pour gérer les types de commande inconnus. Lorsque vous préparez les commandes, `CDynamicParameterAccessor` peut recevoir des informations sur les paramètres à partir de l' `ICommandWithParameters` interface, si le fournisseur prend en charge `ICommandWithParameters` .

- [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)et [CDynamicStringAccessorW,](../../data/oledb/cdynamicstringaccessorw-class.md) utilisent ces classes lorsque vous n’avez aucune connaissance du schéma de base de données. `CDynamicStringAccessorA` Récupère les données sous forme de chaînes ANSI ; `CDynamicStringAccessorW` récupère les données sous forme de chaînes Unicode.

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) Avec cette classe, vous pouvez utiliser les types de données de votre choix si le fournisseur peut convertir le type. Il gère à la fois les colonnes de résultat et les paramètres de commande.

Le tableau suivant résume la prise en charge des types d’accesseurs de modèle OLE DB.

|Type d’accesseur|Dynamique|Gère les paramètres|Buffer|Accesseurs multiples|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|Non|Oui|Utilisateur|Oui|
|`CDynamicAccessor`|Oui|Non|modèles OLE DB|Non|
|`CDynamicParameterAccessor`|Oui|Oui|modèles OLE DB|Non|
|`CDynamicStringAccessor[A,W]`|Oui|Non|modèles OLE DB|Non|
|`CManualAccessor`|Oui|Oui|Utilisateur|Oui|

## <a name="rowset-types"></a>Types d’ensembles de lignes

Les modèles OLE DB prennent en charge trois types d’ensembles de lignes (voir la figure précédente) : ensembles de lignes simples (implémentés par [CRowset](../../data/oledb/crowset-class.md)), ensembles de lignes en bloc (implémentés par [CBulkRowset](../../data/oledb/cbulkrowset-class.md)) et ensembles de lignes de tableau (implémentés par [CArrayRowset](../../data/oledb/carrayrowset-class.md)). Les ensembles de lignes uniques extraient un descripteur de ligne unique lorsque `MoveNext` est appelé. Les ensembles de lignes en bloc peuvent extraire plusieurs handles de ligne. Les ensembles de lignes de tableau sont des ensembles de lignes accessibles à l’aide de la syntaxe de tableau.

L’illustration suivante montre les types d’ensembles de lignes.

![Graphique de RowsetType](../../data/oledb/media/vcrowsettypes.gif "Graphique de RowsetType")<br/>
Classes d’ensemble de lignes

Les [ensembles de lignes de schéma](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) n’accèdent pas aux données dans le magasin de données, mais les informations sur le magasin de données, appelées métadonnées. Les ensembles de lignes de schéma sont généralement utilisés dans les situations où la structure de la base de données n’est pas connue au moment de la compilation et doit être obtenue au moment de l’exécution.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)
