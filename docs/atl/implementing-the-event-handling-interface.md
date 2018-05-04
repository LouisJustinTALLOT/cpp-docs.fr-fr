---
title: Implémentation d’Interface de gestion d’événements | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea37aa4c84cb0824d11f0081e38d9e8157b77ed1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-the-event-handling-interface"></a>Implémentation d’Interface de gestion d’événements
ATL vous aide à tous les trois éléments requis pour la gestion des événements : implémentation de l’interface d’événement, indiquant la source d’événements et désinformation la source d’événements. Les étapes précises, que vous devrez prendre varient selon le type de l’interface d’événement et des exigences de performances de votre application.  
  
 Les méthodes les plus courantes de l’implémentation d’une interface à l’aide d’ATL sont :  
  
-   Dériver directement à partir d’une interface personnalisée.  
  
-   Dérivation de [IDispatchImpl](../atl/reference/idispatchimpl-class.md) pour les interfaces doubles décrites dans une bibliothèque de types.  
  
-   Dérivation de [IDispEventImpl](../atl/reference/idispeventimpl-class.md) pour dispinterfaces décrites dans une bibliothèque de types.  
  
-   Dérivation de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) pour dispinterfaces non décrites dans une bibliothèque de types ou lorsque vous souhaitez améliorer l’efficacité en chargeant ne pas les informations de type au moment de l’exécution.  
  

 Si vous implémentez une interface double ou personnalisée, vous devez informer la source d’événements en appelant [AtlAdvise](reference/connection-point-global-functions.md#atladvise) ou [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise). Vous devez conserver une trace du cookie retourné par l’appel vous-même. Appelez [AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise) pour rompre la liaison.  

  
 Si vous implémentez une dispinterface à l’aide de `IDispEventImpl` ou `IDispEventSimpleImpl`, vous devez informer la source d’événements en appelant [IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise). Appelez [IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise) pour rompre la liaison.  
  
 Si vous utilisez `IDispEventImpl` comme classe de base d’un contrôle composite, les sources d’événements répertoriées dans la table de récepteur sont averties et cessent d’être averties automatiquement à l’aide de [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).  
  
 Le `IDispEventImpl` et `IDispEventSimpleImpl` classes gèrent le cookie pour vous.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des événements](../atl/event-handling-and-atl.md)

