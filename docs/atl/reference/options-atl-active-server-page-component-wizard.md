---
title: Options, Assistant composant ASP ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdd3e62915b81311450cf4d798b04f8df30492ff
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884598"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Options, Assistant Composant ASP ATL
Utilisez cette page de l’Assistant composant Active Server Page ATL pour une efficacité accrue et prise en charge de l’erreur de l’objet.  
  
 Pour plus d’informations sur les projets ATL et les classes ATL COM, consultez [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).  
  
 **Modèle de thread**  
 Indique la méthode de gestion des threads. Par défaut, le projet utilise **cloisonnement** threading.  
  
 Consultez [en spécifiant le modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.  
  
|Option|Description|  
|------------|-----------------|  
|**Single**|Spécifie que l’objet utilise le modèle de thread unique. Dans le modèle de thread unique, un objet s’exécute toujours dans le thread COM principal. Consultez [Single-Threaded Apartments](http://msdn.microsoft.com/library/windows/desktop/ms680112) et [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) pour plus d’informations.|  
|**Cloisonnement**|Spécifie que l’objet utilise le modèle de thread cloisonné. Cloisonnement de threads équivalent au seul. Chaque objet d’un composant avec thread cloisonné se voit assigner un cloisonnement pour son thread, pour la durée de vie de l’objet ; Toutefois, plusieurs threads peuvent être utilisés pour plusieurs objets. Chaque cloisonnement est lié à un thread spécifique et possède une pompe de messages Windows (valeur par défaut).<br /><br /> Consultez [Single-Threaded Apartments](http://msdn.microsoft.com/library/windows/desktop/ms680112) pour plus d’informations.|  
|**Les deux**|Spécifie que l’objet peut utiliser soit cloisonné ou libre, selon le type d’un thread est créé.|  
|**Gratuit**|Spécifie que l’objet utilise le modèle de thread libre. Ce qui équivaut à un modèle de cloisonnement multithread. Consultez [multithreads cloisonnés](http://msdn.microsoft.com/library/windows/desktop/ms693421) pour plus d’informations.|  
|**Neutral**|Spécifie que l’objet suit les indications des multithreads cloisonnés, mais il peut s’exécuter sur n’importe quel type de thread.|  
  
 **Aggregation**  
 Indique si l’objet utilise [agrégation](http://msdn.microsoft.com/library/windows/desktop/ms686558). L’objet d’agrégation choisit les interfaces à exposer aux clients et les interfaces sont exposées comme si l’objet d’agrégation les implémenter. Les clients de l’objet d’agrégation communiquent uniquement avec l’objet d’agrégation.  
  
|Option|Description|  
|------------|-----------------|  
|**Oui**|Spécifie que l’objet peut être agrégé. Valeur par défaut.|  
|**Non**|Spécifie que l’objet n’est pas agrégée.|  
|**Uniquement**|Spécifie que l’objet doit être agrégée.|  
  
 **Prise en charge**  
 (Description de l’élément à ajouter)  
  
|Option|Description|  
|------------|-----------------|  
|`ISupportErrorInfo`|Crée la prise en charge pour le [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interface afin que l’objet puisse retourner les informations d’erreur au client.|  
|**Points de connexion**|Active les points de connexion pour votre objet en faisant dériver la classe de l’objet [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Marshaleur libre de threads**|Crée un objet marshaler libre de threads pour marshaler des pointeurs d’interface efficacement entre les threads dans le même processus. Disponible pour l’objet spécifiant soit **à la fois** ou **gratuit** en tant que le modèle de thread.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant composant ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Composant ASP ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

