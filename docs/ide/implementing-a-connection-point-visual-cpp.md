---
title: Implémenter un point de connexion
ms.date: 05/14/2019
helpviewer_keywords:
- connection points [C++], implementing
- implement connection point wizard [C++]
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: 8a75a5fbbabd20f4591e3a119c175d68cdfb1f90
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182599"
---
# <a name="implement-a-connection-point"></a>Implémenter un point de connexion

Pour implémenter un point de connexion à l’aide de l’Assistant Implémentation d’un point de connexion, vous devez avoir créé un projet, comme une application ATL COM ou une application MFC, avec une prise en charge ATL. Vous pouvez utiliser l’[Assistant Projet ATL](../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL dans une application MFC.

> [!NOTE]
> Pour plus d’informations sur l’implémentation des points de connexion pour un projet MFC, consultez [Points de connexion](../mfc/connection-points.md).

Une fois que vous avez créé le projet, vous devez ajouter un objet ATL pour pouvoir implémenter un point de connexion. Consultez [Ajout d’objets et de contrôles à un projet ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) pour obtenir la liste des Assistants permettant d’ajouter des objets à votre projet ATL.

> [!NOTE]
> L’Assistant ne prend pas en charge les boîtes de dialogue ATL, les services web XML créés avec ATL Server, les objets de performance ni les compteurs de performance.

Un objet connectable (c’est-à-dire une source) peut afficher un point de connexion pour chacune de ses interfaces sortantes. Chaque interface sortante peut être implémentée par un client sur un objet (autrement dit, un récepteur). Pour plus d’informations, consultez [ATL, points de connexion](../atl/atl-connection-points.md).

**Pour implémenter un point de connexion**

1. Dans Affichage de classes, cliquez avec le bouton droit sur le nom de la classe de votre objet ATL.

1. Choisissez **Ajouter** dans le menu contextuel, puis **Ajouter un point de connexion** pour afficher l’[Assistant Implémentation d’un point de connexion](#implement-connection-point-wizard).

1. Sélectionnez les interfaces de points de connexion à implémenter dans les bibliothèques de types appropriées et sélectionnez **Terminer**.

1. Dans l’affichage de classes, examinez les classes proxy créées pour chaque point de connexion. Les classes s’affichent sous la forme CProxy*NomInterface*\<T> et sont dérivées [d’IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).

1. Double-cliquez sur la classe du point de connexion pour afficher sa définition.

   - Si vous implémentez un point de connexion pour l’interface de votre propre projet, la définition suivante s’affiche :

     ```cpp
     template< class T >
     class CProxyInterfaceName :
     public IConnectionPointImpl< T, &IID_InterfaceName >
     {
     public:
     };
     ```

   - Si vous implémentez une interface locale, des méthodes et des propriétés apparaissent dans le corps de la classe.

   - Si vous implémentez un point de connexion pour une autre interface, la définition comprend les méthodes de l’interface, précédées chacune de `Fire_`.

## <a name="in-this-section"></a>Dans cette section

- [Assistant Implémentation d’un point de connexion](#implement-connection-point-wizard)

## <a name="implement-connection-point-wizard"></a>Assistant Implémentation d’un point de connexion

Cet Assistant implémente un point de connexion pour un objet COM. Un objet connectable (c’est-à-dire une source) peut afficher un point de connexion pour son interface personnelle ou pour n’importe quelle interface sortante. MSVC et Windows proposent des bibliothèques de types avec des interfaces sortantes. Chaque interface sortante peut être implémentée par un client sur un objet (autrement dit, un récepteur).

Pour plus d’informations, consultez [ATL, points de connexion](../atl/atl-connection-points.md).

- **Bibliothèques de types disponibles**

  Affiche les bibliothèques de types disponibles contenant les définitions d’interface pour lesquelles vous pouvez implémenter des points de connexion. Sélectionnez le bouton de sélection pour rechercher un fichier contenant la bibliothèque de types à utiliser.

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

  Affiche les noms des interfaces pour lesquelles vous implémentez des points de connexion quand vous sélectionnez **Terminer**.
