---
title: Implémentation d’Interface de gestion d’événements
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
ms.openlocfilehash: 0e676076e09620cb3e69e788549d808be4f6df1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455456"
---
# <a name="implementing-the-event-handling-interface"></a>Implémentation d’Interface de gestion d’événements

ATL vous aide à tous les trois éléments requis pour la gestion des événements : implémentation de l’interface d’événement, informant de la source d’événements et désinformation la source d’événements. Les étapes précises, que vous devrez prendre varient selon le type de l’interface d’événement et les exigences de performances de votre application.

Les méthodes les plus courantes de l’implémentation d’une interface à l’aide de ATL sont :

- La dérivation à partir d’une interface personnalisée directement.

- Dérivant de [IDispatchImpl](../atl/reference/idispatchimpl-class.md) pour les interfaces doubles décrites dans une bibliothèque de types.

- Dérivant de [IDispEventImpl](../atl/reference/idispeventimpl-class.md) pour les dispinterfaces décrites dans une bibliothèque de types.

- Dérivant de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) pour dispinterfaces non décrites dans une bibliothèque de types ou lorsque vous souhaitez améliorer l’efficacité en ne chargeant ne pas les informations de type au moment de l’exécution.

Si vous implémentez une interface double ou personnalisée, vous devez informer la source d’événements en appelant [AtlAdvise](reference/connection-point-global-functions.md#atladvise) ou [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise). Vous devez effectuer le suivi de cookie retourné par l’appel vous-même. Appelez [AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise) interrompre la connexion.

Si vous implémentez une dispinterface à l’aide `IDispEventImpl` ou `IDispEventSimpleImpl`, vous devez informer la source d’événements en appelant [IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise). Appelez [IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise) interrompre la connexion.

Si vous utilisez `IDispEventImpl` comme classe de base d’un contrôle composite, les sources d’événements répertoriées dans la table de récepteur sont averties et arrêter automatiquement à l’aide de [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

Le `IDispEventImpl` et `IDispEventSimpleImpl` classes gèrent le cookie pour vous.

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)
