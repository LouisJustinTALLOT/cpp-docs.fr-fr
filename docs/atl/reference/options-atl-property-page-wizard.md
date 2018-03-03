---
title: "Options, Assistant Page de propriétés ATL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbc27457fa3ace7b1cdfad4894bbd296739de2ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="options-atl-property-page-wizard"></a>Options, Assistant Page de propriétés ATL
Utilisez cette page de l’Assistant pour définir le niveau d’agrégation et le modèle de thread de page de propriétés que vous créez.  
  
 **Modèle de thread**  
 Spécifie le modèle de thread utilisé par la page de propriétés.  
  
 Consultez [en spécifiant le modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.  
  
|Option|Description|  
|------------|-----------------|  
|`Single`|La page de propriétés s’exécute uniquement dans le thread COM principal.|  
|**Cloisonnement**|La page de propriétés peut être créée dans n’importe quel cloisonnement du thread unique. Valeur par défaut.|  
  
 **Aggregation**  
 Ajoute la prise en charge de l’agrégation de la page de propriétés que vous créez. Consultez [agrégation](../../atl/aggregation.md) pour plus d’informations.  
  
|Option|Description|  
|------------|-----------------|  
|**Oui**|Créer une page de propriétés qui peut être agrégée.|  
|**Non**|Créer une page de propriétés qui ne peut pas être agrégée.|  
|**Uniquement**|Créer une page de propriétés qui ne peut être instanciée par le biais d’agrégation.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md)   
 [Chaînes, Assistant Page de propriétés ATL](../../atl/reference/strings-atl-property-page-wizard.md)

