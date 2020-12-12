---
description: 'En savoir plus sur : contrôles ActiveX MFC : événements'
title: 'Contrôles ActiveX MFC : événements'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
ms.openlocfilehash: 8a360931287432e9f0ee0fc55e7e5120bcbd390f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240687"
---
# <a name="mfc-activex-controls-events"></a>Contrôles ActiveX MFC : événements

Les contrôles ActiveX utilisent des événements pour avertir un conteneur que quelque chose est arrivé au contrôle. Les clics sur le contrôle, les données saisies à l'aide du clavier et les modifications de l'état du contrôle sont des exemples courants d'événements. Lorsque ces actions se produisent, le contrôle déclenche un événement pour avertir le conteneur.

Les événements sont également appelés des messages.

MFC prend en charge deux types d'événements : stock et personnalisés. Les événements stock sont les événements que la classe [COleControl](reference/colecontrol-class.md) gère automatiquement. Pour obtenir la liste complète des événements stock, consultez l’article [contrôles ActiveX MFC : ajout d’événements stock](mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Les événements personnalisés permettent à un contrôle d'avertir le conteneur lorsqu'une action spécifique à ce contrôle se produit. Une modification de l'état interne d'un contrôle ou la réception d'un certain message de fenêtre en sont des exemples.

Pour que votre contrôle déclenche correctement des événements, votre classe de contrôle doit mapper chaque événement du contrôle à une fonction membre qui doit être appelée lorsque l'événement associé se produit. Ce mécanisme de mappage (appelé table d'événements) centralise les informations relatives à l'événement et permet à Visual Studio d'accéder et de manipuler facilement les événements du contrôle. Cette table d'événements est déclarée par la macro ci-après, située dans le fichier d'en-tête (.H) de la déclaration de classe du contrôle :

[!code-cpp[NVC_MFC_AxUI#2](codesnippet/cpp/mfc-activex-controls-events_1.h)]

Une fois la table d'événements déclarée, elle doit être définie dans le fichier d'implémentation (.CPP) de votre contrôle. Les lignes de code suivantes définissent la table d'événements, ce qui permet à votre contrôle de déclencher des événements spécifiques :

[!code-cpp[NVC_MFC_AxUI#3](codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

Si vous utilisez l'Assistant Contrôle ActiveX MFC pour créer le projet, celui-ci ajoute automatiquement ces lignes. Dans le cas contraire, vous devez ajouter manuellement ces lignes.

Avec l'affichage de classes, vous pouvez ajouter des événements stock pris en charge par la classe `COleControl`, ou des événements personnalisés que vous définissez. Pour chaque nouvel événement, l'affichage de classes ajoute automatiquement l'entrée correcte à la table d'événements du contrôle et au fichier .IDL du contrôle.

Deux autres articles traitent des événements en détail :

- [Contrôles ActiveX MFC : ajout d'événements stock](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Contrôles ActiveX MFC : ajout d’événements personnalisés](mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : méthodes](mfc-activex-controls-methods.md)<br/>
[Classe COleControl](reference/colecontrol-class.md)
