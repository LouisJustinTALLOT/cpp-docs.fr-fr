---
title: Attributs du consommateur OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 07b129e2810b7b1310eb8988ca60fbd6e5dcad5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391921"
---
# <a name="ole-db-consumer-attributes"></a>Attributs du consommateur OLE DB
Attributs du consommateur OLE DB injectent du code, selon la [les modèles du consommateur OLE DB](../data/oledb/ole-db-consumer-templates-reference.md), pour créer un travail consommateur OLE DB qui effectue des tâches telles que les tables de l’ouverture, l’exécution de commandes et l’accès aux données.
  
|Attribut|Description|
|---------------|-----------------|
|[db_accessor](../windows/db-accessor.md)|Lie les colonnes dans un ensemble de lignes et les lie aux mappages d’accesseur correspondant.|
|[db_column](../windows/db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](../windows/db-command.md)|Exécute une commande OLE DB.|
|[db_param](../windows/db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie.|
|[db_source](../windows/db-source.md)|Crée et encapsule une connexion, via un fournisseur, à une source de données.|
|[db_table](../windows/db-table.md)|Ouvre une table OLE DB.|
  
## <a name="see-also"></a>Voir aussi

[Attributs par groupe](../windows/attributes-by-group.md)