---
description: 'En savoir plus sur : classes de contrôle OLE'
title: Classes de contrôle OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: da59fcd66fa21602ad864deecac9f568bd5123bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244145"
---
# <a name="ole-control-classes"></a>Classes de contrôle OLE

Voici les principales classes que vous utilisez lorsque vous entrez des contrôles OLE. La `COleControlModule` classe dans un module de contrôle OLE est semblable à la classe [CWinApp](reference/cwinapp-class.md) dans une application. Chaque module implémente un ou plusieurs contrôles OLE ; ces contrôles sont représentés par des objets `COleControl`. Ces contrôles communiquent avec leurs conteneurs à l'aide des objets `CConnectionPoint`.

Les classes `CPictureHolder` et `CFontHolder` encapsulent les interfaces COM pour les images et les polices, tandis que les classes `COlePropertyPage` et `CPropExchange` vous aident à implémenter les pages de propriétés et la persistance de propriété de votre contrôle.

[COleControlModule](reference/colecontrolmodule-class.md)<br/>
Remplace la classe `CWinApp` de votre module de contrôle OLE. Dérive de la classe `COleControlModule` pour développer un objet de module de contrôle OLE. Elle fournit des fonctions membres pour initialiser le module de votre contrôle OLE.

[COleControl](reference/colecontrol-class.md)<br/>
Dérive de la classe `COleControl` pour développer un contrôle OLE. Dérivée de `CWnd`, cette classe hérite de toutes les fonctionnalités d'un objet fenêtre Windows et des fonctionnalités OLE supplémentaires, comme le déclenchement d'événements et la capacité à prendre en charge des méthodes et des propriétés.

[CConnectionPoint](reference/cconnectionpoint-class.md)<br/>
La classe `CConnectionPoint` définit un type particulier d'interface utilisé pour communiquer avec d'autres objets OLE, appelé "point de connexion". Un point de connexion implémente une interface sortante qui peut initier des actions sur d'autres objets, tels que les événements de déclenchement et les notifications de modification.

[CPictureHolder](reference/cpictureholder-class.md)<br/>
Encapsule les fonctionnalités d'un objet image Windows et l'interface COM `IPicture`. Permet d'implémenter la propriété Image personnalisée d'un contrôle OLE.

[CFontHolder](reference/cfontholder-class.md)<br/>
Encapsule la fonctionnalité d'un objet de police Windows et l'interface COM `IFont`. Permet d'implémenter la propriété Font de stockage d'un contrôle OLE.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
Affiche les propriétés d'un contrôle OLE dans une interface graphique, similaire à une boîte de dialogue.

[CPropExchange](reference/cpropexchange-class.md)<br/>
Prend en charge l'implémentation de la persistance des propriétés de vos contrôles OLE. Analogue à [CDataExchange](reference/cdataexchange-class.md) pour les boîtes de dialogue.

[CMonikerFile](reference/cmonikerfile-class.md)<br/>
Prend un moniker ou une représentation de chaîne pouvant être transformé en moniker, et le lie de façon synchrone au flux de données pour lequel le moniker est un nom.

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)<br/>
Fonctionne de manière similaire à `CMonikerFile` ; toutefois, lie le moniker asynchrone au flux de données pour lequel le moniker est un nom.

[CDataPathProperty](reference/cdatapathproperty-class.md)<br/>
Implémente une propriété de contrôle OLE qui peut être chargée de façon asynchrone.

[CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md)<br/>
Implémente une propriété de contrôle OLE transférée de façon asynchrone et mise en cache dans un fichier de mémoire.

[COleCmdUI](reference/colecmdui-class.md)<br/>
Permet à un document actif de recevoir les commandes qui proviennent de l'interface utilisateur de son conteneur (notamment Fichier-Nouveau, Ouvrir, Imprimer, etc.), mais permet à un conteneur de recevoir les commandes qui proviennent de l'interface utilisateur du document actif.

[COleSafeArray](reference/colesafearray-class.md)<br/>
Compatible avec les tableaux de type et de dimension arbitraires.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
