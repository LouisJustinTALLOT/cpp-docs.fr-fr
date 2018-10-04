---
title: Attributs COM | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 83d518aded30215684970e58d2868625fb8cd0e5
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790972"
---
# <a name="com-attributes"></a>Attributs COM

Les attributs COM injectent du code pour prendre en charge de nombreux domaines du développement COM et le développement du common language runtime du .NET Framework. Ces zones vont de prise en charge d’interfaces existantes et de mise en œuvre de l’interface personnalisée prenant en charge les propriétés stock, les méthodes et les événements. En outre, la prise en charge sont accessibles pour composite et l’implémentation de contrôle ActiveX.
  
|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique qu’un contrôle peut être agrégé par un autre contrôle.|
|[aggregates](aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[coclass](coclass.md)|Crée un objet COM, ce qui peut implémenter une interface COM.|
|[COM_INTERFACE_ENTRY](com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|
|[implements_category](implements-category.md)|Spécifie les catégories de composants implémentés pour la classe.|
|[progid](progid.md)|Définit le ProgID pour un contrôle.|
|[rdx](rdx.md)|Crée ou modifie une clé de Registre.|
|[registration_script](registration-script.md)|Exécute le script d’inscription spécifiée.|
|[requires_category](requires-category.md)|Spécifie les catégories de composants requis pour la classe.|
|[support_error_info](support-error-info.md)|Prend en charge les rapports d’erreurs pour l’objet cible.|
|[synchronize](synchronize.md)|Synchronise l’accès à une méthode.|
|[Threading](threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|
|[vi_progid](vi-progid.md)|Définit un ProgID indépendants de la version d’un contrôle.|
  
## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)