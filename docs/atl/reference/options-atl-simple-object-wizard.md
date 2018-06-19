---
title: Options, Assistant objet Simple ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffc38f5359b68b90f91a2643e1fbaa743a94e559
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364139"
---
# <a name="options-atl-simple-object-wizard"></a>Options, Assistant Objet simple ATL
Utilisez cette page de l’Assistant objet Simple ATL pour une efficacité accrue et de prise en charge de l’erreur pour l’objet.  
  
 Pour plus d’informations sur les projets ATL et les classes ATL COM, consultez [composants de bureau ATL COM](../../atl/atl-com-desktop-components.md).  
  
 **Modèle de thread**  
 Indique la méthode de gestion des threads. Par défaut, le projet utilise **cloisonnement** threads.  
  
 Consultez [en spécifiant le modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.  
  
|Option|Description|  
|------------|-----------------|  
|`Single`|Spécifie que l’objet s’exécute toujours dans le thread COM principal. Consultez [Single-Threaded cloisonnements](http://msdn.microsoft.com/library/windows/desktop/ms680112) et [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) pour plus d’informations.|  
|**Cloisonnement**|Spécifie que l’objet utilise le modèle de thread cloisonné. Cloisonnement du thread équivalent au seul. Chaque objet d’un composant avec thread cloisonné est attribué un cloisonnement pour son thread, pour la durée de vie de l’objet. Toutefois, plusieurs threads peuvent être utilisés pour plusieurs objets. Chaque cloisonnement est lié à un thread spécifique et possède une pompe de messages Windows (par défaut).<br /><br /> Consultez [Single-Threaded cloisonnements](http://msdn.microsoft.com/library/windows/desktop/ms680112) pour plus d’informations.|  
|**Les deux**|Spécifie que l’objet peut utiliser cloisonné ou libre de threads, selon le type d’un thread est créé.|  
|**Gratuit**|Spécifie que l’objet utilise le modèle de thread libre. Ce qui équivaut à un modèle de cloisonnement multithread. Consultez [multithreads cloisonnés](http://msdn.microsoft.com/library/windows/desktop/ms693421) pour plus d’informations.|  
|**Neutral**|Spécifie que l’objet suit les indications des multithreads cloisonnés, mais il peut s’exécuter sur n’importe quel type de thread.|  
  
 **Aggregation**  
 Indique si l’objet utilise [agrégation](http://msdn.microsoft.com/library/windows/desktop/ms686558). L’objet d’agrégat choisit les interfaces à exposer aux clients et les interfaces sont exposées comme si l’objet d’agrégation les implémenter. Les clients de l’objet d’agrégat communiquent uniquement avec l’objet d’agrégation.  
  
|Option|Description|  
|------------|-----------------|  
|Oui|Spécifie que l’objet peut être agrégé. Valeur par défaut.|  
|Non|Spécifie que l’objet n’est pas agrégée.|  
|Uniquement|Spécifie que l’objet doit être agrégée.|  
  
 **Interface**  
 Indique le type d’interface que prend en charge de l’objet. Par défaut, l’objet prend en charge une interface double.  
  
|Option|Description|  
|------------|-----------------|  
|**Double**|Spécifie que l’objet prend en charge une interface double (sa table vtable a des fonctions d’interface personnalisée ainsi la liaison tardive `IDispatch` méthodes). Permet à la fois les clients COM et [contrôleurs Automation](../../mfc/automation-clients.md) pour accéder à l’objet. Valeur par défaut.|  
|**Personnalisé**|Spécifie que l’objet prend en charge une interface personnalisée (sa table vtable a des fonctions d’interface personnalisées). Une interface personnalisée peut être plus rapide qu’une interface double, en particulier les limites du processus.<br /><br /> -   **Compatible Automation** contrôleurs d’Automation de permet d’accéder à un objet qui possède la prise en charge de l’interface personnalisée.|  
  
 **Prise en charge**  
 Indique la prise en charge supplémentaire pour l’objet.  
  
|Option|Description|  
|------------|-----------------|  
|**ISupportErrorInfo**|Crée la prise en charge pour le [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) afin que l’objet puisse retourner des informations d’erreur au client de l’interface.|  
|**Points de connexion**|Active les points de connexion pour votre objet en faisant dériver la classe de l’objet [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Marshaleur libre de threads**|Crée un objet marshaler libre de threads pour marshaler des pointeurs d’interface efficacement entre les threads dans le même processus. Disponible à la spécification de l’objet **les deux** comme modèle de thread.|  
|**IObjectWithSite (prise en charge d’objet Internet Explorer)**|Implémente [IObjectWithSiteImpl de prendre facilement](../../atl/reference/iobjectwithsiteimpl-class.md), qui offre un moyen simple pour prendre en charge la communication entre un objet et son site dans un conteneur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant objet Simple ATL](../../atl/reference/atl-simple-object-wizard.md)   
 [Objet Simple ATL](../../atl/reference/adding-an-atl-simple-object.md)   
 [Problèmes liés aux threads de serveur in-Process](http://msdn.microsoft.com/library/windows/desktop/ms687205)

