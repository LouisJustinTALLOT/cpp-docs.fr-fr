---
title: Attributs de membre de données | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- data members [C++], attributes
- data members [C++]
ms.assetid: 95b2397d-1daf-4ae4-8cd0-06956d005b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5eb54889cb6e2590c334ad4e9aed497a945cc99d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601781"
---
# <a name="data-member-attributes"></a>Attributs de membre de données

Les attributs suivants s’appliquent aux membres de données dans une classe, une coclasse ou une interface.

|Attribut|Description|
|---------------|-----------------|
|[db_accessor](../windows/db-accessor.md)|Groupes `db_column` attributs participer `IAccessor`-en fonction de liaison.|
|[db_column](../windows/db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](../windows/db-command.md)|Crée une commande OLE DB.|
|[db_param](../windows/db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](../windows/db-source.md)|Crée une connexion à une source de données.|
|[db_table](../windows/db-table.md)|Ouvre une table OLE DB.|
|[defaultbind](../windows/defaultbind.md)|Indique la propriété unique, pouvant être liée qui correspond le mieux à l’objet.|
|[displaybind](../windows/displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|
|[ID](../windows/id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).|
|[range](../windows/range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[rdx](../windows/rdx.md)|Crée une clé de Registre ou modifie une clé de Registre existante.|
|[readonly](../windows/readonly-cpp.md)|Interdit l’assignation à un membre de données.|
|[requestedit](../windows/requestedit.md)|Indique que la propriété prend en charge la `OnRequestEdit` notification.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](../windows/attributes-by-usage.md)