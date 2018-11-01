---
title: Options, Assistant Composant ASP ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: d8d8eaa6190bd04d626b9a23c9d27d1f9daeb003
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595635"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Options, Assistant Composant ASP ATL

Utilisez cette page de l’Assistant composant Active Server Page ATL pour une efficacité accrue et prise en charge de l’erreur de l’objet.

Pour plus d’informations sur les projets ATL et les classes ATL COM, consultez [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).

- **Modèle de thread**

   Indique la méthode de gestion des threads. Par défaut, le projet utilise **cloisonnement** threading.

   Consultez [en spécifiant le modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Single**|Spécifie que l’objet utilise le modèle de thread unique. Dans le modèle de thread unique, un objet s’exécute toujours dans le thread COM principal. Consultez [Single-Threaded Apartments](/windows/desktop/com/single-threaded-apartments) et [InprocServer32](/windows/desktop/com/inprocserver32) pour plus d’informations.|
   |**Cloisonnement**|Spécifie que l’objet utilise le modèle de thread cloisonné. Cloisonnement de threads équivalent au seul. Chaque objet d’un composant avec thread cloisonné se voit assigner un cloisonnement pour son thread, pour la durée de vie de l’objet ; Toutefois, plusieurs threads peuvent être utilisés pour plusieurs objets. Chaque cloisonnement est lié à un thread spécifique et possède une pompe de messages Windows (valeur par défaut).<br /><br /> Consultez [Single-Threaded Apartments](/windows/desktop/com/single-threaded-apartments) pour plus d’informations.|
   |**Les deux**|Spécifie que l’objet peut utiliser soit cloisonné ou libre, selon le type d’un thread est créé.|
   |**Gratuit**|Spécifie que l’objet utilise le modèle de thread libre. Ce qui équivaut à un modèle de cloisonnement multithread. Consultez [multithreads cloisonnés](/windows/desktop/com/multithreaded-apartments) pour plus d’informations.|
   |**Neutral**|Spécifie que l’objet suit les indications des multithreads cloisonnés, mais il peut s’exécuter sur n’importe quel type de thread.|

- **Aggregation**

   Indique si l’objet utilise [agrégation](/windows/desktop/com/aggregation). L’objet d’agrégation choisit les interfaces à exposer aux clients et les interfaces sont exposées comme si l’objet d’agrégation les implémenter. Les clients de l’objet d’agrégation communiquent uniquement avec l’objet d’agrégation.

   |Option|Description|
   |------------|-----------------|
   |**Oui**|Spécifie que l’objet peut être agrégé. Valeur par défaut.|
   |**Non**|Spécifie que l’objet n’est pas agrégée.|
   |**Uniquement**|Spécifie que l’objet doit être agrégée.|

- **Prise en charge**

   Options de support supplémentaires :

   |Option|Description|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crée la prise en charge pour le [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interface afin que l’objet puisse retourner les informations d’erreur au client.|
   |**Points de connexion**|Active les points de connexion pour votre objet en faisant dériver la classe de l’objet [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Marshaleur libre de threads**|Crée un objet marshaler libre de threads pour marshaler des pointeurs d’interface efficacement entre les threads dans le même processus. Disponible pour l’objet spécifiant soit **à la fois** ou **gratuit** en tant que le modèle de thread.|

## <a name="see-also"></a>Voir aussi

[Assistant Composant ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Composant ASP ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

