---
title: Attributs COM | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 8e18f64d48b357ed691f42fc900f68c8e8054776
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317249"
---
# <a name="com-attributes"></a>Attributs COM
Les attributs COM injectent du code pour prendre en charge de nombreux domaines du développement COM et le développement du common language runtime du .NET Framework. Ces zones vont de prise en charge d’interfaces existantes et de mise en œuvre de l’interface personnalisée prenant en charge les propriétés stock, les méthodes et les événements. En outre, la prise en charge sont accessibles pour composite et l’implémentation de contrôle ActiveX.
  
|Attribut|Description|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Indique qu’un contrôle peut être agrégé par un autre contrôle.|
|[aggregates](../windows/aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[coclass](../windows/coclass.md)|Crée un objet COM, ce qui peut implémenter une interface COM.|
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|
|[implements_category](../windows/implements-category.md)|Spécifie les catégories de composants implémentés pour la classe.|
|[progid](../windows/progid.md)|Définit le ProgID pour un contrôle.|
|[rdx](../windows/rdx.md)|Crée ou modifie une clé de Registre.|
|[registration_script](../windows/registration-script.md)|Exécute le script d’inscription spécifiée.|
|[requires_category](../windows/requires-category.md)|Spécifie les catégories de composants requis pour la classe.|
|[support_error_info](../windows/support-error-info.md)|Prend en charge les rapports d’erreurs pour l’objet cible.|
|[synchronize](../windows/synchronize.md)|Synchronise l’accès à une méthode.|
|[Threading](../windows/threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|
|[vi_progid](../windows/vi-progid.md)|Définit un ProgID indépendants de la version d’un contrôle.|
  
## <a name="see-also"></a>Voir aussi
 [Attributs par groupe](../windows/attributes-by-group.md)