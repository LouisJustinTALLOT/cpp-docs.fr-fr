---
description: 'En savoir plus sur : options, Assistant composant de page Active Server ATL'
title: Options, Assistant Composant ASP ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: 6d41b5cb43aa9f0445e73bbe148a2a753e374a15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139020"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Options, Assistant Composant ASP ATL

Utilisez cette page de l’Assistant composant de page Active Server ATL pour concevoir une meilleure efficacité et une meilleure prise en charge des erreurs pour l’objet.

Pour plus d’informations sur les projets ATL et les classes ATL COM, consultez [Composants ATL COM Desktop](../../atl/atl-com-desktop-components.md).

- **Modèle de thread**

   Indique la méthode de gestion des threads. Par défaut, le projet utilise le thread **cloisonné** .

   Consultez [Spécification du modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Unique**|Spécifie que l’objet utilise le modèle de thread unique. Dans le modèle à thread unique, un objet s’exécute toujours dans le thread COM principal. Pour plus d’informations, consultez Apartments et [InprocServer32](/windows/win32/com/inprocserver32) à [thread unique](/windows/win32/com/single-threaded-apartments) .|
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

- **Support**

   Options de support supplémentaires :

   |Option|Description|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crée une prise en charge pour l’interface [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) afin que l’objet puisse retourner les informations d’erreur au client.|
   |**Points de connexion**|Active les points de connexion pour votre objet en faisant dériver la classe de votre objet de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Marshaleur à threads libres**|Crée un objet marshaleur libre de threads pour marshaler efficacement les pointeurs d’interface entre les threads dans le même processus. Disponible pour l’objet, en spécifiant **les deux** ou **gratuitement** comme modèle de thread.|

## <a name="see-also"></a>Voir aussi

[Assistant Composant ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Composant ASP ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
