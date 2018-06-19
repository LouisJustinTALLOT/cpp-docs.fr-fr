---
title: Macros pour les modèles du fournisseur OLE DB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab7611c49f625a36023b4e31bf6aff47ab16f156
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111735"
---
# <a name="macros-for-ole-db-provider-templates"></a>Macros pour les modèles du fournisseur OLE DB
Les macros de fournisseur de modèles OLE DB offrent des fonctionnalités dans les catégories suivantes :  
  
### <a name="property-set-map-macros"></a>Macros de table de jeu de propriétés  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](../../data/oledb/begin-property-set.md)|Marque le début d’un jeu de propriétés.|  
|[BEGIN_PROPERTY_SET_EX](../../data/oledb/begin-property-set-ex.md)|Marque le début d’un jeu de propriétés.|  
|[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)|Marque le début d’une propriété de valeur qui peut être masqué ou défini en dehors de la portée du fournisseur.|  
|[CHAIN_PROPERTY_SET](../../data/oledb/chain-property-set.md)|Chaîne ensemble les groupes de propriétés.|  
|[END_PROPERTY_SET](../../data/oledb/end-property-set.md)|Marque la fin d’un jeu de propriétés.|  
|[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)|Marque la fin d’un mappage de jeu de propriétés.|  
|[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)|Définit une propriété spécifique dans une propriété avec une valeur par défaut.|  
|[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)|Définit une propriété spécifique dans une propriété avec une valeur fournie par vous. Vous permet également de définir les options et les indicateurs.|  
|[PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)|Définit une propriété spécifique dans une propriété avec une valeur fournie par vous.|  
  
### <a name="column-map-macros"></a>Macros de mappage de colonnes  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)|Marque le début des entrées de mappage de colonne fournisseur.|  
|[END_PROVIDER_COLUMN_MAP](../../data/oledb/end-provider-column-map.md)|Marque la fin des entrées de mappage de colonne fournisseur.|  
|[PROVIDER_COLUMN_ENTRY](../../data/oledb/provider-column-entry.md)|Représente une colonne spécifique pris en charge par le fournisseur.|  
|[PROVIDER_COLUMN_ENTRY_GN](../../data/oledb/provider-column-entry-gn.md)|Représente une colonne spécifique pris en charge par le fournisseur. Vous pouvez spécifier la taille de la colonne, type de données, précision, échelle et de lignes du schéma GUID.|  
|[PROVIDER_COLUMN_ENTRY_FIXED](../../data/oledb/provider-column-entry-fixed.md)|Représente une colonne spécifique pris en charge par le fournisseur. Vous pouvez spécifier le type de données de colonne.|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)|Représente une colonne spécifique pris en charge par le fournisseur. Vous pouvez spécifier la taille de colonne.|  
|[PROVIDER_COLUMN_ENTRY_STR](../../data/oledb/provider-column-entry-str.md)|Représente une colonne spécifique pris en charge par le fournisseur. Il suppose que le type de colonne est une chaîne.|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|Représente une colonne spécifique pris en charge par le fournisseur. Comme les PROVIDER_COLUMN_ENTRY_LENGTH, mais vous permet également de spécifier le type de données de la colonne, ainsi que la taille.|  
|[PROVIDER_COLUMN_ENTRY_WSTR](../../data/oledb/provider-column-entry-wstr.md)|Représente une colonne spécifique pris en charge par le fournisseur. Il suppose que le type de colonne est une chaîne de caractères Unicode.|  
  
### <a name="schema-rowset-macros"></a>Macros d’ensemble de lignes de schéma  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)|Marque le début d’un mappage de schéma.|  
|[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)|Associe un GUID à une classe.|  
|[END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)|Marque la fin d’un mappage de schéma.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)   
 [Référence des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)