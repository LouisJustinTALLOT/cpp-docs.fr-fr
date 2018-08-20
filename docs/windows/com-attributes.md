---
title: Attributs COM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d37ba5c690b61840ad261e6ab966d0cc74c07c1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861384"
---
# <a name="com-attributes"></a>Attributs COM
Le COM injectent du code pour prendre en charge plusieurs domaines de développement COM et le développement du common language runtime du .NET Framework. Ces zones vont de prise en charge d’interfaces existantes et de mise en œuvre de l’interface personnalisée prise en charge des propriétés stock, les méthodes et les événements. En outre, la prise en charge sont accessibles pour composite et de l’implémentation du contrôle ActiveX.  
  
|Attribut|Description|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Indique qu’un contrôle peut être agrégé par un autre contrôle.|  
|[aggregates](../windows/aggregates.md)|Indique qu’un contrôle agrège la classe cible.|  
|[coclass](../windows/coclass.md)|Crée un objet COM, ce qui peut implémenter une interface COM.|  
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|  
|[implements_category](../windows/implements-category.md)|Spécifie les catégories de composants de mise en œuvre de la classe.|  
|[progid](../windows/progid.md)|Définit le ProgID pour un contrôle.|  
|[rdx](../windows/rdx.md)|Crée ou modifie une clé de Registre.|  
|[registration_script](../windows/registration-script.md)|Exécute le script d’enregistrement spécifié.|  
|[requires_category](../windows/requires-category.md)|Spécifie les catégories de composants requis pour la classe.|  
|[support_error_info](../windows/support-error-info.md)|Prend en charge les rapports d’erreurs pour l’objet cible.|  
|[synchronize](../windows/synchronize.md)|Synchronise l’accès à une méthode.|  
|[Modèle de thread](../windows/threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|  
|[vi_progid](../windows/vi-progid.md)|Définit un ProgID indépendants de la version d’un contrôle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs par groupe](../windows/attributes-by-group.md)