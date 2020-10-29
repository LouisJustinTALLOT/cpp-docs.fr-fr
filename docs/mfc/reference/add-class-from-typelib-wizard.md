---
title: Assistant Ajout de classes d'une Typelib
ms.date: 05/09/2019
helpviewer_keywords:
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
ms.openlocfilehash: 73f2668883add0e711f0ef73e5602dd9cdc4ab28
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924104"
---
# <a name="add-class-from-typelib-wizard"></a>Assistant Ajout de classes d'une Typelib

::: moniker range="msvc-160"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=msvc-150"

Utilisez cet Assistant pour ajouter une classe MFC à partir d’une bibliothèque de types disponible. L’Assistant crée une classe pour chaque interface que vous ajoutez à partir de la bibliothèque de types sélectionnée.

- **Ajouter une classe à partir de**

   Spécifie l’emplacement de la bibliothèque de types à partir de laquelle la classe est créée.

   |Option|Description|
   |------------|-----------------|
   |**Registre**|La bibliothèque de types est inscrite dans le système. Les bibliothèques de types inscrites sont répertoriées dans **Bibliothèques de types disponibles** .|
   |**File**|La bibliothèque de types n’est pas nécessairement inscrite dans le système, mais est contenue dans un fichier. Vous devez fournir l’emplacement du fichier dans **Emplacement** .|

- **Bibliothèques de types disponibles**

   Répertorie les bibliothèques de types actuellement inscrites dans le système. Sélectionnez une bibliothèque de types dans cette liste pour afficher ses interfaces dans la liste **interfaces** .

- **Lieu**

   Spécifie l’emplacement de la bibliothèque de types. Si vous cliquez sur **Fichier** sous **Ajouter une classe à partir de** , vous pouvez indiquer l’emplacement du fichier contenant la bibliothèque de types. Pour accéder à l’emplacement du fichier, cliquez sur le bouton de sélection (...).

- **Interfaces**

   Répertorie les interfaces dans la bibliothèque de types actuellement sélectionnée dans la liste **bibliothèques de types disponibles** .

   |Bouton de transfert|Description|
   |---------------------|-----------------|
   |**>**|Ajoute l’interface actuellement sélectionnée à la liste **Interfaces** . Grisé si aucune interface n’est sélectionnée.|
   |**>>**|Ajoute toutes les interfaces dans la bibliothèque de types actuellement sélectionnée dans la liste **bibliothèques de types disponibles** .|
   |**\<**|Supprime la classe actuellement sélectionnée de la liste **Classes générées** . Grisé si aucune classe n’est actuellement sélectionnée dans la liste **classes générées** .|
   |**\<\<**|Supprime toutes les classes de la liste **Classes générées** . Grisé si la liste **classes générées** est vide.|

- **Classes générées**

   Spécifie les noms de classes à générer à partir des interfaces ajoutées à l’aide du **>** **>>** bouton ou. Vous pouvez cliquer sur cette zone pour sélectionner une classe, puis utiliser les touches haut ou haut pour faire défiler la liste, afficher chaque nom de classe dans la zone de **classe** et le nom de fichier dans la zone de **fichier** que l’Assistant génère quand vous cliquez sur **Terminer** . Vous ne pouvez sélectionner qu’une seule classe à la fois dans cette zone.

   Vous pouvez supprimer une classe en la sélectionnant dans cette liste, puis en cliquant sur **<** . Vous n’êtes pas obligé de sélectionner une classe dans la zone Classes générées pour supprimer toutes les classes. Cliquez sur **<<** pour supprimer toutes les classes de la zone **Classes générées** .

- **Classe**

   Spécifie le nom de la classe sélectionnée dans la zone **Classes générées** . Cette classe est ajoutée par l’Assistant quand vous cliquez sur **Terminer** . Vous pouvez modifier le nom dans la zone **Class** .

- **File**

   Définit le nom du fichier d’en-tête de la nouvelle classe. Par défaut, ce nom est basé sur celui fourni dans **Classes générées** . Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer** , l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Classe MFC à partir d'une bibliothèque de types](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)<br/>
[Clients Automation : utilisation des bibliothèques de types](../../mfc/automation-clients-using-type-libraries.md)
