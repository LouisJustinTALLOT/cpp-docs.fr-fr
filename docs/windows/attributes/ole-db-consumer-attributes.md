---
title: Attributs du consommateur OLE DB (C++ COM) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35051c565a18ba61de53813ce57be147140cc468
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791045"
---
# <a name="ole-db-consumer-attributes"></a>Attributs du consommateur OLE DB
Attributs du consommateur OLE DB injectent du code, selon la [les modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md), pour créer un travail consommateur OLE DB qui effectue des tâches telles que les tables de l’ouverture, l’exécution de commandes et l’accès aux données.
  
|Attribut|Description|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|Lie les colonnes dans un ensemble de lignes et les lie aux mappages d’accesseur correspondant.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Exécute une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie.|
|[db_source](db-source.md)|Crée et encapsule une connexion, via un fournisseur, à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
  
## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)