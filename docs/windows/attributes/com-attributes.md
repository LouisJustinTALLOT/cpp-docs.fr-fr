---
description: 'En savoir plus sur : attributs COM'
title: Attributs COM
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: d1377bdcb449190d01f529b2a4c713f138cbef5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269170"
---
# <a name="com-attributes"></a>Attributs COM

Les attributs COM injectent du code pour prendre en charge de nombreuses zones de développement COM et de .NET Framework common language runtime le développement. Ces zones vont de l’implémentation d’interface personnalisée et de la prise en charge d’interfaces existantes à la prise en charge des propriétés, des méthodes et des événements stock. En outre, la prise en charge est disponible pour l’implémentation du contrôle composite et ActiveX.

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique qu’un contrôle peut être agrégé par un autre contrôle.|
|[agrégats](aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[coclasse](coclass.md)|Crée un objet COM, qui peut implémenter une interface COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Ajoute une entrée d’interface à une table COM.|
|[implements_category](implements-category.md)|Spécifie les catégories de composant implémentées pour la classe.|
|[ProgID](progid.md)|Définit le ProgID pour un contrôle.|
|[rdx](rdx.md)|Crée ou modifie une clé de registre.|
|[registration_script](registration-script.md)|Exécute le script d’inscription spécifié.|
|[requires_category](requires-category.md)|Spécifie les catégories de composants nécessaires pour la classe.|
|[support_error_info](support-error-info.md)|Prend en charge la création de rapports d’erreurs pour l’objet cible.|
|[non](synchronize.md)|Synchronise l’accès à une méthode.|
|[Threading](threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|
|[vi_progid](vi-progid.md)|Définit un ProgID indépendant de la version pour un contrôle.|

## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)
