---
description: 'En savoir plus sur : Résumé de la gestion des événements ATL'
title: Résumé de la gestion des événements ATL
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
ms.openlocfilehash: c041de6cbd0e0852d5ce0e51d892c21c7d9a23d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148653"
---
# <a name="atl-event-handling-summary"></a>Résumé de la gestion des événements ATL

En général, la gestion des événements COM est un processus relativement simple. Il existe trois étapes principales :

- Implémentez l’interface d’événement sur votre objet.

- Conseillez à la source de l’événement que votre objet souhaite recevoir des événements.

- Désconseillez la source de l’événement lorsque votre objet n’a plus besoin de recevoir des événements.

## <a name="implementing-the-interface"></a>Implémentation de l'interface

Il existe quatre méthodes principales pour implémenter une interface à l’aide d’ATL.

|Dériver de |Adapté au type d’interface|Requiert que vous implémentiez toutes les méthodes *|Nécessite une bibliothèque de types au moment de l’exécution|
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|
|Interface|Vtable|Oui|Non|
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Double|Oui|Oui|
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|Non|Oui|
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|Non|Non|

\* Lorsque vous utilisez les classes de prise en charge ATL, vous n’avez jamais besoin d’implémenter les `IUnknown` `IDispatch` méthodes ou manuellement.

## <a name="advising-and-unadvising-the-event-source"></a>Avertissement et désavertissement de la source de l’événement

Il existe trois méthodes principales pour conseiller et désavertir une source d’événement à l’aide d’ATL.

|Fonction advise|Unadvise, fonction|Le plus approprié pour une utilisation avec|Vous oblige à effectuer le suivi d’un cookie|Commentaires|
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [CComPtrBase :: Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable ou interfaces doubles|Oui|`AtlAdvise` est une fonction ATL globale. `CComPtrBase::Advise` est utilisé par [CComPtr](../atl/reference/ccomptr-class.md) et [CComQIPtr](../atl/reference/ccomqiptr-class.md).|
|[IDispEventSimpleImpl ::D ispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl ::D ispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) ou [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Non|Moins de paramètres que dans `AtlAdvise` la mesure où la classe de base fait plus de travail.|
|[CComCompositeControl :: AdviseSinkMap (TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl :: AdviseSinkMap (FALSe)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|Contrôles ActiveX dans les contrôles composites|Non|`CComCompositeControl::AdviseSinkMap` avertit toutes les entrées de la table de récepteurs d’événements. La même fonction ne conseille pas les entrées. Cette méthode est appelée automatiquement par la `CComCompositeControl` classe.|
|[CAxDialogImpl :: AdviseSinkMap (TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl :: AdviseSinkMap (FALSe)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|Contrôles ActiveX dans une boîte de dialogue|Non|`CAxDialogImpl::AdviseSinkMap` conseille et déconseille tous les contrôles ActiveX dans la ressource de boîte de dialogue. Cela s’effectue automatiquement pour vous.|

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)<br/>
[Prise en charge d’IDispEventImpl](../atl/supporting-idispeventimpl.md)
