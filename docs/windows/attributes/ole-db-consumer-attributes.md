---
title: Attributs du consommateur OLE DBC++ (com)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
ms.openlocfilehash: 67f58d6dd32360248c6437f66fa7042871bc4ea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214684"
---
# <a name="ole-db-consumer-attributes"></a>Attributs du consommateur OLE DB
Les attributs de consommateur OLE DB injectent du code, basé sur les [modèles de consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md), pour créer un consommateur de OLE DB fonctionnel qui effectue des tâches telles que l’ouverture de tables, l’exécution de commandes et l’accès aux données.

|Attribut|Description|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|Lie les colonnes d’un ensemble de lignes et les lie aux mappages d’accesseur correspondants.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Exécute une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable membre spécifiée à un paramètre d’entrée ou de sortie.|
|[db_source](db-source.md)|Crée et encapsule une connexion, via un fournisseur, à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|

## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)
