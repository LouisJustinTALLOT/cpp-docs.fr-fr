---
description: 'En savoir plus sur : ajouter un événement'
title: Ajouter un événement
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.event.overview
helpviewer_keywords:
- ActiveX controls [C++], adding events to
- MFC ActiveX controls [C++], adding events
- events [C++], ActiveX controls
- add event wizard [C++]
ms.assetid: fe34832a-edfc-4f86-aacb-8df77001873d
ms.openlocfilehash: c369be0fe241867b101ab458344ae706b1fd440d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240817"
---
# <a name="add-an-event"></a>Ajouter un événement

À partir d’Affichage de classes, vous pouvez ajouter un événement à l’aide de l’[Assistant Ajout d’événement](#add-event-wizard) uniquement à la classe de contrôle de votre projet de [contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). Si vous souhaitez ajouter un événement à un autre type de projet, utilisez le bouton **Événements** de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

**Pour ajouter un événement à votre projet de contrôle ActiveX MFC**

1. Dans l’affichage de classes, développez le nœud du projet afin d’afficher ses classes.

1. Cliquez avec le bouton droit sur la classe de contrôle du projet.

1. Dans le menu contextuel, choisissez **Ajouter**, puis **Ajouter un événement** pour afficher l’Assistant Ajout d’événement.

1. Indiquez les informations sur l’événement dans les zones appropriées de l’Assistant.

1. Sélectionnez **Terminer** pour ajouter l’événement au projet.

## <a name="in-this-section"></a>Dans cette section

- [Assistant Ajout d’événement](#add-event-wizard)

## <a name="add-event-wizard"></a>Assistant Ajout d’événement

Cet Assistant ajoute un événement à un projet de contrôle ActiveX MFC. Vous pouvez spécifier votre propre événement, personnaliser un événement stock standard ou sélectionner un événement stock dans une liste.

- **Event name**

   Définit le nom utilisé par les clients Automation pour demander un événement de la classe. Entrez un nom ou sélectionnez-en un dans la liste.

- **Type d’événement**

   Indique le type d’événement à ajouter. Disponible uniquement si vous sélectionnez dans la liste nom de l' **événement** .

   |Option|Description|
   |------------|-----------------|
   |**Boursier**|Spécifie qu’un événement stock, tel qu’un clic sur un bouton, est implémenté pour cette classe. Les événements stock sont définis dans la bibliothèque MFC (Microsoft Foundation Class).|
   |**Personnalisée**|Indique que vous utilisez votre propre implémentation de l’événement.|

- **Nom interne**

   Définit le nom de la fonction membre qui envoie l’événement. Disponible uniquement pour les événements personnalisés. Le nom est basé sur le **Nom de l’événement**. Vous pouvez changer le nom interne si vous souhaitez attribuer un nom différent du **Nom de l’événement**.

- **Type de paramètre**

   Définit le type du **Nom du paramètre**. Sélectionnez le type dans la liste.

- **Nom du paramètre**

   Définit le nom d’un paramètre à passer par l’intermédiaire de votre événement. Après avoir tapé le nom, vous devez sélectionner **Ajouter** pour l’ajouter à la liste de paramètres.

   Dès que vous sélectionnez **Ajouter**, le nom du paramètre s’affiche dans **Liste de paramètres**.

   > [!NOTE]
   > Si vous fournissez un nom de paramètre et sélectionnez **Terminer** avant de sélectionner **Ajouter**, le paramètre n’est pas ajouté à l’événement. Vous devez rechercher la méthode et insérer le paramètre manuellement.

- **Ajouter**

   Ajoute le paramètre que vous spécifiez dans **Nom du paramètre** et son type à **Liste de paramètres**. Sélectionnez **Ajouter** pour ajouter un paramètre à la liste.

- **Supprimer**

   Supprime de la liste le paramètre que vous sélectionnez dans **Liste de paramètres**.

- **Liste de paramètres**

   Affiche tous les paramètres et leurs types actuellement ajoutés pour la méthode. Quand vous ajoutez des paramètres, l’Assistant met à jour la **Liste de paramètres** pour afficher chaque paramètre avec son type.
