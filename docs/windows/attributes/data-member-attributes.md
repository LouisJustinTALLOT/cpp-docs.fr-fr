---
title: Attributs de membre de données (C++ COM) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- data members [C++], attributes
- data members [C++]
ms.assetid: 95b2397d-1daf-4ae4-8cd0-06956d005b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5019503bed9dd0012d8aafc1ade4abd3107335ac
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790689"
---
# <a name="data-member-attributes"></a>Attributs de membre de données

Les attributs suivants s’appliquent aux membres de données dans une classe, une coclasse ou une interface.

|Attribut|Description|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|Groupes `db_column` attributs participer `IAccessor`-en fonction de liaison.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](db-source.md)|Crée une connexion à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[defaultbind](defaultbind.md)|Indique la propriété unique, pouvant être liée qui correspond le mieux à l’objet.|
|[displaybind](displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|
|[ID](id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).|
|[range](range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[rdx](rdx.md)|Crée une clé de Registre ou modifie une clé de Registre existante.|
|[readonly](readonly-cpp.md)|Interdit l’assignation à un membre de données.|
|[requestedit](requestedit.md)|Indique que la propriété prend en charge la `OnRequestEdit` notification.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)