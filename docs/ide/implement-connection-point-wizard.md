---
title: Assistant Implémentation d'un point de connexion
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.impl.cp.overview
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
ms.openlocfilehash: b818a1a149e95805a8694f6c8d8d1325b33211b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531532"
---
# <a name="implement-connection-point-wizard"></a>Assistant Implémentation d'un point de connexion

Cet Assistant implémente un point de connexion pour un objet COM. Un objet connectable (c’est-à-dire une source) peut exposer un point de connexion pour son interface personnelle ou pour n’importe quelle interface sortante. Visual C++ et Windows proposent des bibliothèques de types avec des interfaces sortantes. Chaque interface sortante peut être implémentée par un client sur un objet (autrement dit, un récepteur).

Pour plus d’informations, consultez [ATL, points de connexion](../atl/atl-connection-points.md).

- **Bibliothèques de types disponibles**

   Affiche les bibliothèques de types disponibles contenant les définitions d’interface pour lesquelles vous pouvez implémenter des points de connexion. Cliquez sur le bouton de sélection pour rechercher un fichier contenant la bibliothèque de types à utiliser.

- **Emplacement**

   Affiche l’emplacement de la bibliothèque de types actuellement sélectionnée dans la liste **Bibliothèques de types disponibles**.

- **Interfaces**

   Affiche les interfaces dont les définitions sont contenues dans la bibliothèque de types actuellement sélectionnée dans la zone **Bibliothèques de types disponibles**.

   |Bouton de transfert|Description|
   |---------------------|-----------------|
   |**>**|Ajoute à la liste **Implémenter les points de connexion** le nom d’interface actuellement sélectionné dans la liste **Interfaces**.|
   |**>>**|Ajoute à la liste **Implémenter les points de connexion** les noms de toutes les interfaces disponibles dans la liste **Interfaces**.|
   |**\<**|Supprime le nom d’interface actuellement sélectionné dans la liste **Implémenter les points de connexion**.|
   |**\<\<**|Supprime les noms de toutes les interfaces actuellement affichés dans la liste **Implémenter les points de connexion**.|

- **Implémenter les points de connexion**

   Affiche les noms des interfaces pour lesquelles vous implémentez des points de connexion quand vous cliquez sur **Terminer**.

## <a name="see-also"></a>Voir aussi

[Implémentation d’un point de connexion](../ide/implementing-a-connection-point-visual-cpp.md)