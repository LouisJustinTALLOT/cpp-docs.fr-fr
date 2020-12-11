---
description: 'En savoir plus sur : options, Assistant objet simple ATL'
title: Options, Assistant Objet simple ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.options
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
ms.openlocfilehash: 37353358aecddc084e5f29c6c6ee75b393fe8ded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157839"
---
# <a name="options-atl-simple-object-wizard"></a>Options, Assistant Objet simple ATL

Utilisez cette page de l’Assistant objet simple ATL pour concevoir une plus grande efficacité et une meilleure prise en charge des erreurs pour l’objet.

Pour plus d’informations sur les projets ATL et les classes ATL COM, consultez [Composants ATL COM Desktop](../../atl/atl-com-desktop-components.md).

- **Modèle de thread**

   Indique la méthode de gestion des threads. Par défaut, le projet utilise le thread **cloisonné** .

   Consultez [Spécification du modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Unique**|Spécifie que l’objet s’exécute toujours dans le thread COM principal. Pour plus d’informations, consultez Apartments et [InprocServer32](/windows/win32/com/inprocserver32) à [thread unique](/windows/win32/com/single-threaded-apartments) .|
   |**STA**|Spécifie que l’objet utilise le thread cloisonné. Équivalent à un cloisonnement de thread unique. Chaque objet d’un composant à thread cloisonné se voit assigner un cloisonnement pour son thread, pour la durée de vie de l’objet. Toutefois, plusieurs threads peuvent être utilisés pour plusieurs objets. Chaque cloisonnement est lié à un thread spécifique et a une pompe de messages Windows (valeur par défaut).<br /><br /> Pour plus d’informations, consultez [Apartments à thread unique](/windows/win32/com/single-threaded-apartments) .|
   |**Les deux**|Spécifie que l’objet peut utiliser un thread cloisonné ou libre, en fonction du type de thread qu’il a créé.|
   |**Gratuit**|Spécifie que l’objet utilise le Threading libre. Le Threading libre est équivalent à un modèle multithread cloisonné. Pour plus d’informations, consultez [Apartments (cloisonnés) multithread](/windows/win32/com/multithreaded-apartments) .|
   |**Neutralisant**|Spécifie que l’objet suit les indications pour les cloisonnements multithread, mais il peut s’exécuter sur n’importe quel type de thread.|

- **Agrégation**

   Indique si l’objet utilise l' [agrégation](/windows/win32/com/aggregation). L’objet d’agrégation choisit les interfaces à exposer aux clients, et les interfaces sont exposées comme si l’objet d’agrégation les implémentait. Les clients de l’objet d’agrégation communiquent uniquement avec l’objet d’agrégation.

   |Option|Description|
   |------------|-----------------|
   |**Oui**|Spécifie que l’objet peut être agrégé. Valeur par défaut.|
   |**Non**|Spécifie que l’objet n’est pas agrégé.|
   |**Ne**|Spécifie que l’objet doit être agrégé.|

- **Interface**

   Indique le type d’interface pris en charge par l’objet. Par défaut, l’objet prend en charge une interface double.

   |Option|Description|
   |------------|-----------------|
   |**Double**|Spécifie que l’objet prend en charge une interface double (son vtable a des fonctions d’interface personnalisées et des méthodes de liaison tardive `IDispatch` ). Permet aux clients COM et aux [contrôleurs Automation](../../mfc/automation-clients.md) d’accéder à l’objet. Valeur par défaut.|
   |**Personnalisée**|Spécifie que l’objet prend en charge une interface personnalisée (sa vtable comprend des fonctions d’interface personnalisées). Une interface personnalisée peut être plus rapide qu’une interface double, en particulier entre les frontières de processus.<br /><br /> - **Compatible Automation** Permet aux contrôleurs Automation d’accéder à un objet qui dispose de la prise en charge de l’interface personnalisée.|

- **Support**

   Indique une prise en charge supplémentaire de l’objet.

   |Option|Description|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crée une prise en charge pour l’interface [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) afin que l’objet puisse retourner les informations d’erreur au client.|
   |**Points de connexion**|Active les points de connexion pour votre objet en faisant dériver la classe de votre objet de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Marshaleur à threads libres**|Crée un objet marshaleur libre de threads pour marshaler efficacement les pointeurs d’interface entre les threads dans le même processus. Disponible pour l’objet qui spécifie à la **fois** comme modèle de thread.|
   |**IObjectWithSite** (prise en charge des objets IE)|Implémente [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), qui offre un moyen simple de prendre en charge la communication entre un objet et son site dans un conteneur.|

## <a name="see-also"></a>Voir aussi

[Assistant Objet simple ATL](../../atl/reference/atl-simple-object-wizard.md)<br/>
[Objet simple ATL](../../atl/reference/adding-an-atl-simple-object.md)<br/>
[Problèmes liés aux threads du serveur in-process](/windows/win32/com/in-process-server-threading-issues)
