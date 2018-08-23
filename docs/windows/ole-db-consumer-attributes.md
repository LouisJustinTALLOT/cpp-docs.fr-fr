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
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++]
- attributes [C++], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4af8ccddce73e419bec468aefc1b0f63bee89ecf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604374"
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