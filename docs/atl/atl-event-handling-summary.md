---
title: ATL gestion d’événements résumé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a938bd072ea8df30e64cce28fbf0709f08547d28
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="atl-event-handling-summary"></a>Résumé de la gestion des événements ATL
En général, la gestion des événements COM sont un processus relativement simple. Il existe trois étapes principales :  
  
-   Implémentez l’interface d’événement sur votre objet.  
  
-   Informer la source d’événements que votre objet souhaite recevoir des événements.  
  
-   Déconseiller la source d’événements lorsque votre objet n’a plus besoin de recevoir des événements.  
  
## <a name="implementing-the-interface"></a>Implémentation de l'interface  
 Il existe quatre méthodes d’implémentation d’une interface à l’aide d’ATL.  
  
|Dériver de|Convient pour le type d’Interface|Vous devez implémenter toutes les méthodes *|Nécessite une bibliothèque de types au moment de l’exécution|  
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|  
|L’interface|Vtable|Oui|Non|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Double|Oui|Oui|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|Non|Oui|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|Non|Non|  
  
 \* Lors de l’utilisation des classes de prise en charge ATL, vous ne sont jamais requis pour implémenter le **IUnknown** ou `IDispatch` méthodes manuellement.  
  
## <a name="advising-and-unadvising-the-event-source"></a>Information et désinformation la Source d’événements  
 Il existe trois méthodes principales d’information et désinformation une source d’événement à l’aide d’ATL.  
  
|Conseiller (fonction)|Déconseiller (fonction)|Mieux adapté pour une utilisation avec|Vous devez effectuer le suivi d’un cookie|Commentaires|  
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|  

|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)| Vtable ou interfaces doubles | Oui | `AtlAdvise` est une fonction ATL globale. `CComPtrBase::Advise` est utilisé par [CComPtr](../atl/reference/ccomptr-class.md) et [CComQIPtr](../atl/reference/ccomqiptr-class.md). |  

|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) ou [ IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)| Ne | Moins de paramètres que `AtlAdvise` étant donné que la classe de base fonctionne plus. |  
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)| Contrôles ActiveX dans des contrôles composites | Ne | `CComCompositeControl::AdviseSinkMap` indique qu’il contient toutes les entrées de table de récepteur de l’événement. La même fonction avertit les entrées. Cette méthode est appelée automatiquement par le `CComCompositeControl` classe. |  
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)| Contrôles ActiveX dans une boîte de dialogue | Ne | `CAxDialogImpl::AdviseSinkMap` indique qu’il contient et avertit tous les contrôles ActiveX dans la ressource de boîte de dialogue. Cela s’effectue automatiquement pour vous. |  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des événements](../atl/event-handling-and-atl.md)   
 [Prise en charge d’IDispEventImpl](../atl/supporting-idispeventimpl.md)

