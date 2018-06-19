---
title: Classes de contrôle OLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5dcbda85c33bab37babe5da861067d25cf31e32c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355351"
---
# <a name="ole-control-classes"></a>Classes de contrôle OLE
Voici les principales classes que vous utilisez lorsque vous entrez des contrôles OLE. Le `COleControlModule` classe dans un module de contrôle OLE est similaire à la [CWinApp](../mfc/reference/cwinapp-class.md) classe dans une application. Chaque module implémente un ou plusieurs contrôles OLE ; ces contrôles sont représentés par des objets `COleControl`. Ces contrôles communiquent avec leurs conteneurs à l'aide des objets `CConnectionPoint`.  
  
 Les classes `CPictureHolder` et `CFontHolder` encapsulent les interfaces COM pour les images et les polices, tandis que les classes `COlePropertyPage` et `CPropExchange` vous aident à implémenter les pages de propriétés et la persistance de propriété de votre contrôle.  
  
 [COleControlModule](../mfc/reference/colecontrolmodule-class.md)  
 Remplace la classe `CWinApp` de votre module de contrôle OLE. Dérive de la classe `COleControlModule` pour développer un objet de module de contrôle OLE. Elle fournit des fonctions membres pour initialiser le module de votre contrôle OLE.  
  
 [COleControl](../mfc/reference/colecontrol-class.md)  
 Dérive de la classe `COleControl` pour développer un contrôle OLE. Dérivée de `CWnd`, cette classe hérite de toutes les fonctionnalités d'un objet fenêtre Windows et des fonctionnalités OLE supplémentaires, comme le déclenchement d'événements et la capacité à prendre en charge des méthodes et des propriétés.  
  
 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)  
 La classe `CConnectionPoint` définit un type particulier d'interface utilisé pour communiquer avec d'autres objets OLE, appelé "point de connexion". Un point de connexion implémente une interface sortante qui peut initier des actions sur d'autres objets, tels que les événements de déclenchement et les notifications de modification.  
  
 [CPictureHolder](../mfc/reference/cpictureholder-class.md)  
 Encapsule les fonctionnalités d'un objet image Windows et l'interface COM `IPicture`. Permet d'implémenter la propriété Image personnalisée d'un contrôle OLE.  
  
 [CFontHolder](../mfc/reference/cfontholder-class.md)  
 Encapsule la fonctionnalité d'un objet de police Windows et l'interface COM `IFont`. Permet d'implémenter la propriété Font de stockage d'un contrôle OLE.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Affiche les propriétés d'un contrôle OLE dans une interface graphique, similaire à une boîte de dialogue.  
  
 [CPropExchange](../mfc/reference/cpropexchange-class.md)  
 Prend en charge l'implémentation de la persistance des propriétés de vos contrôles OLE. Analogue à [CDataExchange](../mfc/reference/cdataexchange-class.md) pour les boîtes de dialogue.  
  
 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)  
 Prend un moniker ou une représentation de chaîne pouvant être transformé en moniker, et le lie de façon synchrone au flux de données pour lequel le moniker est un nom.  
  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)  
 Fonctionne de manière similaire à `CMonikerFile` ; toutefois, lie le moniker asynchrone au flux de données pour lequel le moniker est un nom.  
  
 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)  
 Implémente une propriété de contrôle OLE qui peut être chargée de façon asynchrone.  
  
 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)  
 Implémente une propriété de contrôle OLE transférée de façon asynchrone et mise en cache dans un fichier de mémoire.  
  
 [COleCmdUI](../mfc/reference/colecmdui-class.md)  
 Permet à un document actif de recevoir les commandes qui proviennent de l'interface utilisateur de son conteneur (notamment Fichier-Nouveau, Ouvrir, Imprimer, etc.), mais permet à un conteneur de recevoir les commandes qui proviennent de l'interface utilisateur du document actif.  
  
 [COleSafeArray](../mfc/reference/colesafearray-class.md)  
 Compatible avec les tableaux de type et de dimension arbitraires.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

