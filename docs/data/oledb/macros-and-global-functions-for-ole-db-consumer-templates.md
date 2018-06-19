---
title: Macros et fonctions globales pour les modèles du consommateur OLE DB | Documents Microsoft
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
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 57f61dd54855a2cf0196c0e269eda92295c818b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33114313"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Macros et fonctions globales pour les modèles du consommateur OLE DB
Modèles du consommateur OLE DB inclut les macros suivantes et les fonctions globales :  
  
### <a name="global-functions"></a>Fonctions globales  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|Exporte les informations d’enregistrement de l’erreur OLE DB à l’unité de vidage si une erreur est retournée.|  
  
### <a name="accessor-map-macros"></a>Macros de mappage d’accesseur  
  
|||  
|-|-|  
|[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)|Marque le début d’une entrée de l’accesseur.|  
|[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)|Marque le début des entrées de mappage d’accesseur.|  
|[END_ACCESSOR](../../data/oledb/end-accessor.md)|Marque la fin d’une entrée de l’accesseur.|  
|[END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)|Marque la fin des entrées de mappage d’accesseur.|  
  
### <a name="column-map-macros"></a>Macros de mappage de colonnes  
  
|||  
|-|-|  
|[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)|Marque le début des entrées de mappage de colonne dans la classe d’enregistrement utilisateur.|  
|[BLOB_ENTRY](../../data/oledb/blob-entry.md)|Permet de lier un objet binaire volumineux (BLOB).|  
|[BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)|Indique la longueur de la colonne de données BLOB.|  
|[BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)|Indique la longueur et l’état de la colonne de données BLOB.|  
|[BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)|Signale l’état de la colonne de données BLOB.|  
|[BLOB_NAME](../../data/oledb/blob-name.md)|Permet de lier un objet binaire volumineux par nom de colonne.|  
|[BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)|Indique la longueur de la colonne de données BLOB.|  
|[BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)|Indique la longueur et l’état de la colonne de données BLOB.|  
|[BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)|Signale l’état de la colonne de données BLOB.|  
|[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)|Représente une entrée de signet sur l’ensemble de lignes. Une entrée de signet est un type spécial d’entrée de la colonne.|  
|[COLUMN_ENTRY](../../data/oledb/column-entry.md)|Représente une liaison à une colonne spécifique dans la base de données.|  
|[COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)|Représente une liaison à la colonne dans la base de données. Prend en charge `type`, *longueur*, *précision*, `scale`, et *état* paramètres.|  
|[COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)|Représente une liaison à la colonne dans la base de données. Prend en charge la *longueur* variable.|  
|[COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)|Représente une liaison à la colonne dans la base de données. Prend en charge *état* et *longueur* paramètres.|  
|[COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)|Représente une liaison à la colonne dans la base de données. Prend en charge *précision* et `scale` paramètres.|  
|[COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)|Représente une liaison à la colonne dans la base de données. Prend en charge la *longueur* variable, *précision* et `scale` paramètres.|  
|[COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)|Représente une liaison à la colonne dans la base de données. Prend en charge *état* et *longueur* variables, *précision* et `scale` paramètres.|  
|[COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)|Représente une liaison à la colonne dans la base de données. Prend en charge la *état* variable, *précision* et `scale` paramètres.|  
|[COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)|Représente une liaison à la colonne dans la base de données. Prend en charge la *état* variable.|  
|[COLUMN_ENTRY_TYPE](../../data/oledb/column-entry-type.md)|Représente une liaison à une colonne spécifique dans la base de données. Prend en charge `type` paramètre.|  
|[COLUMN_ENTRY_TYPE_SIZE](../../data/oledb/column-entry-type-size.md)|Représente une liaison à la colonne dans la base de données. Prend en charge `type` et `size` paramètres.|  
|[COLUMN_NAME](../../data/oledb/column-name.md)|Représente une liaison à une colonne spécifique dans la base de données par nom.|  
|[COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de type de données, taille, précision, échelle, longueur de colonne et l’état de la colonne.|  
|[COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de longueur de colonne.|  
|[COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de longueur de colonne et l’état.|  
|[COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de la précision et l’échelle.|  
|[COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de longueur de précision, échelle et de colonne.|  
|[COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de précision, échelle, longueur de colonne et état de colonne.|  
|[COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de l’état de précision, échelle et de colonne.|  
|[COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de l’état de la colonne.|  
|[COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification du type de données.|  
|[COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de type de données, la précision et l’échelle.|  
|[COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de type de données et la taille.|  
|[COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de l’état de type et de la colonne de données.|  
|[END_COLUMN_MAP](../../data/oledb/end-column-map.md)|Marque la fin des entrées de mappage de colonne.|  
  
### <a name="command-macros"></a>Macros de commande  
  
|||  
|-|-|  
|[DEFINE_COMMAND](../../data/oledb/define-command.md)|Spécifie la commande permettant de créer l’ensemble de lignes lors de l’utilisation du [CCommand](../../data/oledb/ccommand-class.md) classe. Accepte uniquement les types de chaîne correspondant au type d’application spécifié (ANSI ou Unicode). Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de `DEFINE_COMMAND`.|  
|[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)|Spécifie la commande permettant de créer l’ensemble de lignes lors de l’utilisation du [CCommand](../../data/oledb/ccommand-class.md) classe. Prend en charge les applications ANSI et Unicode.|  
  
### <a name="parameter-map-macros"></a>Macros de mappage de paramètre  
  
|||  
|-|-|  
|[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)|Marque le début des entrées de mappage de paramètre dans la classe d’enregistrement utilisateur.|  
|[END_PARAM_MAP](../../data/oledb/end-param-map.md)|Marque la fin des entrées de mappage de paramètre.|  
|[SET_PARAM_TYPE](../../data/oledb/set-param-type.md)|Spécifie `COLUMN_ENTRY` macros qui suivent le `SET_PARAM_TYPE` macro comme entrée, sortie ou d’entrée/sortie.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)