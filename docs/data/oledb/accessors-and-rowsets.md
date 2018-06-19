---
title: Accesseurs et jeux de lignes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 49f5415f6c75984f968b25fb709c20d80dde554f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094493"
---
# <a name="accessors-and-rowsets"></a>Accesseurs et jeux de lignes
Pour définir et récupérer des données, les modèles OLE DB utilisent un accesseur et un ensemble de lignes via la [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) classe. Cette classe peut gérer plusieurs accesseurs de différents types.  
  
## <a name="accessor-types"></a>Types d’accesseurs  
 Tous les accesseurs dérivent [CAccessorBase](../../data/oledb/caccessorbase-class.md). `CAccessorBase` fournit les paramètres et la liaison de colonne.  
  
 La figure suivante illustre les types d’accesseurs.  
  
 ![Types d’accesseurs](../../data/oledb/media/vcaccessortypes.gif "vcaccessortypes")  
Classes d’accesseurs  
  
-   [CAccessor](../../data/oledb/caccessor-class.md) Utilisez cet accesseur si vous connaissez la structure de la source de la base de données au moment du design. `CAccessor` lie statiquement un enregistrement de base de données qui contient la mémoire tampon, à la source de données.  
  
-   [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Utilisez cet accesseur si vous ne connaissez pas la structure de la base de données au moment du design. `CDynamicAccessor` appels `IColumnsInfo::GetColumnInfo` pour obtenir les informations de colonne de base de données. Il crée et gère un accesseur et la mémoire tampon.  
  
-   [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) cet accesseur permet de gérer des types de commande inconnu. Lorsque vous préparez les commandes, `CDynamicParameterAccessor` peut obtenir des informations sur les paramètres à partir de la `ICommandWithParameters` de l’interface, si le fournisseur prend en charge `ICommandWithParameters`.  
  
-   [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md), et [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) Utilisez ces classes lorsque vous n’avez aucune connaissance du schéma de base de données. `CDynamicStringAccessorA` Récupère des données en tant que chaînes ANSI ; `CDynamicStringAccessorW` récupère les données comme des chaînes Unicode.  
  
-   [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) avec cette classe, vous pouvez utiliser les types de données que si le fournisseur peut convertir le type. Il gère les colonnes de résultat et les paramètres de commande.  
  
 Le tableau suivant récapitule la prise en charge dans les types d’accesseurs des modèles OLE DB.  
  
|Type d’accesseur|dynamique|Gère les paramètres|Mémoire tampon|Accesseurs multiples|  
|-------------------|-------------|--------------------|------------|------------------------|  
|`CAccessor`|Non|Oui|Utilisateur|Oui|  
|`CDynamicAccessor`|Oui|Non|modèles OLE DB|Non|  
|`CDynamicParameterAccessor`|Oui|Oui|modèles OLE DB|Non|  
|`CDynamicStringAccessor[A,W]`|Oui|Non|modèles OLE DB|Non|  
|`CManualAccessor`|Oui|Oui|Utilisateur|Oui|  
  
## <a name="rowset-types"></a>Types de l’ensemble de lignes  
 Les modèles OLE DB prennent en charge trois types d’ensembles de lignes (consultez l’illustration précédente) : jeux de lignes simples (implémentée par [CRowset](../../data/oledb/crowset-class.md)), en bloc d’ensembles de lignes (implémentée par [CBulkRowset](../../data/oledb/cbulkrowset-class.md)) et (implémenté les ensembles de lignes de tableau par [CArrayRowset](../../data/oledb/carrayrowset-class.md)). Extraction des ensembles de lignes unique une seule ligne gérer lorsque `MoveNext` est appelée. Ensembles de lignes en bloc peuvent extraire plusieurs handles de ligne. Ensembles de lignes de tableau sont des ensembles de lignes qui sont accessibles à l’aide de la syntaxe de tableau.  
  
 La figure suivante illustre les types de l’ensemble de lignes.  
  
 ![Graphique de RowsetType](../../data/oledb/media/vcrowsettypes.gif "vcrowsettypes")  
Classes de l’ensemble de lignes  
  
 [Ensembles de lignes de schéma](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) ne pas accéder aux données dans les données de stocker mais à la place accéder aux informations sur le magasin de données, appelée métadonnées. Ensembles de lignes de schéma sont généralement utilisés dans les situations dans lesquelles la structure de base de données n’est pas connue au moment de la compilation et doit être obtenue en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)