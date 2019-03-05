---
title: Résumé de la gestion des événements ATL
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
ms.openlocfilehash: 0e3a47719e3160170ed1bfa64b315415ddc7a1c8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265351"
---
# <a name="atl-event-handling-summary"></a>Résumé de la gestion des événements ATL

En règle générale, la gestion des événements COM sont un processus relativement simple. Il existe trois étapes principales :

- Implémentez l’interface d’événement sur votre objet.

- Avertir la source d’événements que votre objet souhaite recevoir des événements.

- Unadvise sur la source d’événements lorsque votre objet n’a plus besoin de recevoir des événements.

## <a name="implementing-the-interface"></a>Implémentation de l'interface

Il existe quatre méthodes d’implémentation d’une interface à l’aide d’ATL.

|Dériver de|Approprié pour le type d’Interface|Vous devez implémenter toutes les méthodes *|Requiert une bibliothèque de types au moment de l’exécution|
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|
|L’interface|Vtable|Oui|Aucune|
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Double|Oui|Oui|
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|Aucune|Oui|
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|Aucune|Aucune|

\* Lorsque vous utilisez des classes de prise en charge ATL, vous ne sont jamais requis pour implémenter le `IUnknown` ou `IDispatch` méthodes manuellement.

## <a name="advising-and-unadvising-the-event-source"></a>Information et désinformation la Source d’événements

Il existe trois méthodes principales d’information et désinformation une source d’événement à l’aide d’ATL.

|Conseiller (fonction)|Fonction Unadvise|Plus approprié pour une utilisation avec|Vous devez effectuer le suivi d’un cookie|Commentaires|
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable ou des interfaces doubles|Oui|`AtlAdvise` est une fonction ATL globale. `CComPtrBase::Advise` est utilisé par [CComPtr](../atl/reference/ccomptr-class.md) et [CComQIPtr](../atl/reference/ccomqiptr-class.md).|
|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) ou [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Aucune|Moins de paramètres que `AtlAdvise` car la classe de base n’en a plus de travail.|
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|Contrôles ActiveX dans des contrôles composites|Aucune|`CComCompositeControl::AdviseSinkMap` conseille à toutes les entrées de table de récepteur de l’événement. La même fonction avertit les entrées. Cette méthode est appelée automatiquement par le `CComCompositeControl` classe.|
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|Contrôles ActiveX dans une boîte de dialogue|Aucune|`CAxDialogImpl::AdviseSinkMap` conseille et avertit tous les contrôles ActiveX dans la ressource de boîte de dialogue. Cela est fait automatiquement pour vous.|

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)<br/>
[Prise en charge d’IDispEventImpl](../atl/supporting-idispeventimpl.md)
