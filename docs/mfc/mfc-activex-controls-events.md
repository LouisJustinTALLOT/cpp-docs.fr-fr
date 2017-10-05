---
title: "Contrôles ActiveX MFC : Événements | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 3903be230f130aeaeb1953faf73a0c8af4c3492f
ms.openlocfilehash: f4e6cfc21a12288a53eca391eccb86bb4ea3ff55
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="mfc-activex-controls-events"></a>Contrôles ActiveX MFC : événements
Les contrôles ActiveX utilisent des événements pour avertir un conteneur que quelque chose est arrivé au contrôle. Les clics sur le contrôle, les données saisies à l'aide du clavier et les modifications de l'état du contrôle sont des exemples courants d'événements. Lorsque ces actions se produisent, le contrôle déclenche un événement pour avertir le conteneur.  
  
 Les événements sont également appelés des messages.  
  
 MFC prend en charge deux types d'événements : stock et personnalisés. Événements stock sont des événements qui classe [COleControl](../mfc/reference/colecontrol-class.md) gère automatiquement. Pour obtenir une liste complète des événements stock, consultez l’article [contrôles ActiveX MFC : ajout d’événements Stock](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Les événements personnalisés permettent à un contrôle d'avertir le conteneur lorsqu'une action spécifique à ce contrôle se produit. Une modification de l'état interne d'un contrôle ou la réception d'un certain message de fenêtre en sont des exemples.  
  
 Pour que votre contrôle déclenche correctement des événements, votre classe de contrôle doit mapper chaque événement du contrôle à une fonction membre qui doit être appelée lorsque l'événement associé se produit. Ce mécanisme de mappage (appelé table d'événements) centralise les informations relatives à l'événement et permet à Visual Studio d'accéder et de manipuler facilement les événements du contrôle. Cette table d'événements est déclarée par la macro ci-après, située dans le fichier d'en-tête (.H) de la déclaration de classe du contrôle :  
  
 [!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]  
  
 Une fois la table d'événements déclarée, elle doit être définie dans le fichier d'implémentation (.CPP) de votre contrôle. Les lignes de code suivantes définissent la table d'événements, ce qui permet à votre contrôle de déclencher des événements spécifiques :  
  
 [!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]  
  
 Si vous utilisez l'Assistant Contrôle ActiveX MFC pour créer le projet, celui-ci ajoute automatiquement ces lignes. Dans le cas contraire, vous devez ajouter manuellement ces lignes.  
  
 Avec l'affichage de classes, vous pouvez ajouter des événements stock pris en charge par la classe `COleControl`, ou des événements personnalisés que vous définissez. Pour chaque nouvel événement, l'affichage de classes ajoute automatiquement l'entrée correcte à la table d'événements du contrôle et au fichier .IDL du contrôle.  
  
 Deux autres articles traitent des événements en détail :  
  
-   [Contrôles ActiveX MFC : Ajout d’événements Stock](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [Contrôles ActiveX MFC : ajout d’événements personnalisés](../mfc/mfc-activex-controls-adding-custom-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)   
 [COleControl, classe](../mfc/reference/colecontrol-class.md)

