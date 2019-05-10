---
title: Assistant Ajout de classes d'une Typelib
ms.date: 05/09/2019
helpviewer_keywords:
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
ms.openlocfilehash: 794df6c207c2f2e93cdcc63a6b83cd3434764e87
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525476"
---
# <a name="add-class-from-typelib-wizard"></a>Assistant Ajout de classes d'une Typelib

::: moniker range="vs-2019"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="vs-2017"

Utilisez cet Assistant pour ajouter une classe MFC à partir d’une bibliothèque de types disponibles. L’Assistant crée une classe pour chaque interface que vous ajoutez à partir de la bibliothèque de types sélectionnée.

- **Ajouter une classe à partir de**

   Spécifie l’emplacement de la bibliothèque de types à partir de laquelle la classe est créée.

   |Option|Description|
   |------------|-----------------|
   |**Registry**|La bibliothèque de types est inscrite dans le système. Les bibliothèques de types inscrites sont répertoriées dans **Bibliothèques de types disponibles**.|
   |**Fichier**|La bibliothèque de types n’est pas nécessairement inscrite dans le système, mais est contenue dans un fichier. Vous devez fournir l’emplacement du fichier dans **Emplacement**.|

- **Bibliothèques de types disponibles**

   Répertorie les bibliothèques de types actuellement inscrits dans le système. Sélectionnez une bibliothèque de types à partir de cette liste pour afficher ses interfaces dans les **Interfaces** liste.

   Consultez « Inside Distributed COM : Type Libraries and Language Integration » dans MSDN library pour plus d’informations sur l’inscription des bibliothèques de types.

- **Emplacement**

   Spécifie l’emplacement de la bibliothèque de types. Si vous cliquez sur **Fichier** sous **Ajouter une classe à partir de**, vous pouvez indiquer l’emplacement du fichier contenant la bibliothèque de types. Pour accéder à l’emplacement du fichier, cliquez sur le bouton de sélection (...).

- **Interfaces**

   Répertorie les interfaces dans la bibliothèque de types actuellement sélectionné dans le **bibliothèques de types disponibles** liste.

   |Bouton de transfert|Description|
   |---------------------|-----------------|
   |**>**|Ajoute l’interface actuellement sélectionnée à la liste **Interfaces**. Estompé si aucune interface n’est sélectionnée.|
   |**>>**|Ajoute toutes les interfaces dans la bibliothèque de types actuellement sélectionnée dans le **bibliothèques de types disponibles** liste.|
   |**\<**|Supprime la classe actuellement sélectionnée de la liste **Classes générées**. Estompé si aucune classe n’est sélectionnée dans le **classes générées** liste.|
   |**\<\<**|Supprime toutes les classes de la liste **Classes générées**. If estompé le **classes générées** liste est vide.|

- **Classes générées**

   Spécifie les noms de classe à générer à partir des interfaces ajoutées à l’aide du bouton **>** ou **>>**. Vous pouvez cliquer sur cette case pour sélectionner une classe et puis utilisez le haut ou bas pour faire défiler la liste, afficher chaque nom de classe dans le **classe** boîte et nom de fichier dans le **fichier** zone que l’Assistant génère lorsque vous Cliquez sur **Terminer**. Vous ne pouvez sélectionner qu’une seule classe à la fois dans cette zone.

   Pour supprimer une classe, sélectionnez-la dans cette liste et cliquez sur **<**. Vous n’avez pas besoin de sélectionner une classe dans la zone de classes générées pour supprimer toutes les classes ; en cliquant sur **<<**, vous supprimez toutes les classes dans le **classes générées** boîte.

- **Classe**

   Spécifie le nom de la classe sélectionnée dans la zone **Classes générées**. Cette classe est ajoutée par l’Assistant quand vous cliquez sur **Terminer**. Vous pouvez modifier le nom dans la zone **Class**.

- **Fichier**

   Définit le nom du fichier d’en-tête de la nouvelle classe. Par défaut, ce nom est basé sur celui fourni dans **Classes générées**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Classe MFC à partir d’une bibliothèque de types](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)<br/>
[Clients Automation : Utilisation de bibliothèques de types](../../mfc/automation-clients-using-type-libraries.md)
