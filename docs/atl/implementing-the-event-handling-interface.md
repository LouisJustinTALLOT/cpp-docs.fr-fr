---
description: 'En savoir plus sur : implémentation de l’interface de gestion des événements'
title: Implémentation de l’interface de gestion des événements
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
ms.openlocfilehash: 109fbb1fbdd4f18d0eb4c295fbc08de2b7cc3a35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152761"
---
# <a name="implementing-the-event-handling-interface"></a>Implémentation de l’interface de gestion des événements

ATL vous aide à utiliser les trois éléments requis pour la gestion des événements : implémentation de l’interface d’événement, avertissement de la source de l’événement et désavertissement de la source de l’événement. Les étapes précises que vous devez prendre dépendent du type de l’interface d’événement et des exigences de performances de votre application.

Les méthodes les plus courantes pour implémenter une interface à l’aide de ATL sont les suivantes :

- Dérivation directe à partir d’une interface personnalisée.

- Dérivation à partir de [IDispatchImpl](../atl/reference/idispatchimpl-class.md) pour les interfaces doubles décrites dans une bibliothèque de types.

- Dérivation à partir de [IDispEventImpl](../atl/reference/idispeventimpl-class.md) pour les dispinterfaces décrites dans une bibliothèque de types.

- Dérivation de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) pour les dispinterfaces non décrites dans une bibliothèque de types ou lorsque vous souhaitez améliorer l’efficacité en ne chargeant pas les informations de type au moment de l’exécution.

Si vous implémentez une interface personnalisée ou double, vous devez informer la source de l’événement en appelant [AtlAdvise](reference/connection-point-global-functions.md#atladvise) ou [CComPtrBase :: Advise](../atl/reference/ccomptrbase-class.md#advise). Vous devrez effectuer le suivi du cookie retourné par l’appel. Appelez [AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise) pour rompre la connexion.

Si vous implémentez une dispinterface à l’aide de `IDispEventImpl` ou `IDispEventSimpleImpl` de, vous devez informer la source de l’événement en appelant [IDispEventSimpleImpl ::D ispeventadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise). Appelez [IDispEventSimpleImpl ::D ispeventunadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise) pour rompre la connexion.

Si vous utilisez `IDispEventImpl` comme classe de base d’un contrôle composite, les sources d’événements répertoriées dans la table de récepteurs sont recommandées et ne sont pas automatiquement avisées à l’aide de [CComCompositeControl :: AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

Les `IDispEventImpl` `IDispEventSimpleImpl` classes et gèrent le cookie pour vous.

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)
