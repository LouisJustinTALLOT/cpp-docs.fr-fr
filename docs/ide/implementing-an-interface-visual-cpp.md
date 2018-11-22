---
title: Implémenter une interface
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: 8e166f806d247cd93ff0f471360d749fa95e430b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692899"
---
# <a name="implement-an-interface"></a>Implémenter une interface

Pour implémenter une interface, vous devez avoir créé un projet, comme une application COM ATL ou une application MFC avec prise en charge ATL. Vous pouvez utiliser l’[Assistant Projet ATL](../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL dans une application MFC.

Une fois que vous avez créé un projet, vous devez ajouter un objet ATL pour pouvoir implémenter une interface. Consultez [Ajouter des objets et des contrôles à un projet ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) pour obtenir la liste des Assistants permettant d’ajouter des objets à votre projet ATL.

> [!NOTE]
> L’Assistant ne prend pas en charge les boîtes de dialogue ATL, les services web XML utilisant ATL, les objets de performance ou les compteurs de performance.

Si vous [ajoutez un contrôle ATL](../atl/reference/adding-an-atl-control.md), vous pouvez spécifier s’il faut implémenter des interfaces par défaut. Les interfaces par défaut sont listées dans la page [Interfaces](../atl/reference/interfaces-atl-control-wizard.md) de cet Assistant et définies dans le fichier atlcom.h.

Une fois que vous avez ajouté l’objet ou le contrôle, vous pouvez implémenter d’autres interfaces, situées dans n’importe quelle bibliothèque de types disponible, à l’aide de l’Assistant Implémentation d’interface.

Si vous ajoutez une nouvelle interface, vous devez l’ajouter manuellement au fichier .idl du projet. Pour plus d’informations, consultez [Ajouter une nouvelle interface à un projet ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md).

**Pour implémenter une interface**

1. Dans Affichage de classes, cliquez avec le bouton droit sur le nom de la classe de votre objet ATL.

1. Choisissez **Ajouter** dans le menu contextuel, puis **Implémenter l’interface** pour afficher l’[Assistant Implémentation d’interface](#implement-interface-wizard).

1. Sélectionnez les interfaces à implémenter dans les bibliothèques de types appropriées et sélectionnez **Terminer**.

1. Dans Affichage de classes, développez le nœud Bases et interfaces de l’objet pour afficher l’interface que vous avez implémentée. Ensuite, développez le nœud de l’interface pour afficher ses propriétés, méthodes et événements disponibles.

   > [!NOTE]
   > Vous pouvez également utiliser l’[Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code) pour examiner les membres de l’interface.

## <a name="in-this-section"></a>Dans cette section

- [Assistant Implémentation d’interface](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>Assistant Implémentation d’interface

Cet Assistant implémente une interface pour un objet COM. Les implémentations de nombreuses interfaces sont incluses dans les bibliothèques COM disponibles avec Visual Studio et Windows. Une implémentation d’interface est associée à un objet quand une instance de cet objet est créée. Elle fournit également les services qu’offre l’objet.

Pour en savoir plus sur les interfaces et les implémentations, consultez [Interfaces et implémentations d’interface](/windows/desktop/com/interfaces-and-interface-implementations) dans le SDK Windows.

- **Implémenter une interface à partir de**

  Spécifie l’emplacement de la bibliothèque de types à partir de laquelle est créée l’interface.

  |Option|Description|
  |------------|-----------------|
  |**Projet**|La bibliothèque de types fait partie du projet.|
  |**Registry**|La bibliothèque de types est inscrite dans le système. Les bibliothèques de types inscrites sont répertoriées dans **Bibliothèques de types disponibles**.|
  |**Fichier**|La bibliothèque de types n’est pas nécessairement inscrite dans le système, mais est contenue dans un fichier. Spécifiez l’emplacement du fichier dans **Emplacement**.|

- **Bibliothèques de types disponibles**

  Affiche les bibliothèques de types disponibles contenant les définitions d’interface que vous pouvez implémenter. Quand vous choisissez **Fichier** sous **Implémenter une interface à partir de**, cette zone n’est pas modifiable.

- **Emplacement**

  Affiche l’emplacement de la bibliothèque de types actuellement sélectionnée dans la liste **Bibliothèques de types disponibles**. Si vous avez sélectionné **Fichier** sous **Implémenter une interface à partir de**, sélectionnez le bouton de sélection pour rechercher un fichier contenant la bibliothèque de types à utiliser.

- **Interfaces**

  Affiche les interfaces dont les définitions sont contenues dans la bibliothèque de types actuellement sélectionnée dans la zone **Bibliothèques de types disponibles**.

  > [!NOTE]
  > Les interfaces qui ont le même nom que celles déjà implémentées par l’objet sélectionné ne sont pas affichées dans la zone **Interfaces**.

  |Bouton de transfert|Description|
  |---------------------|-----------------|
  |**>**|Ajoute à la liste **Implémenter les interfaces** le nom d’interface actuellement sélectionné dans la liste **Interfaces**.|
  |**>>**|Ajoute à la liste **Implémenter les interfaces** tous les noms d’interface disponibles dans la liste **Interfaces**.|
  |**\<**|Supprime le nom d’interface actuellement sélectionné dans la liste **Implémenter les interfaces**.|
  |**\<\<**|Supprime tous les noms d’interface actuellement répertoriés dans la liste **Implémenter les interfaces**.|

- **Implémenter les interfaces**

  Affiche le nom des interfaces que vous avez choisi d’implémenter dans votre objet.

  > [!NOTE]
  > Si vous incluez plusieurs interfaces qui dérivent de `IDispatch` ou si vous essayez d’implémenter une interface dérivée d’une autre interface déjà présente dans votre classe, vous devez clarifier les entrées COM_MAP. Pour plus d’informations, consultez [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2).
