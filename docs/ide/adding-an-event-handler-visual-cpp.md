---
description: 'En savoir plus sur : ajouter un gestionnaire d’événements'
title: Ajouter un gestionnaire d’événements
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 0e65d25573b4e16d9815db289401251a6bb2d0f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265530"
---
# <a name="add-an-event-handler"></a>Ajouter un gestionnaire d’événements

À partir de l’éditeur de ressources, vous pouvez ajouter un nouveau gestionnaire d’événements ou modifier un gestionnaire existant pour un contrôle de boîte de dialogue en recourant à l’[Assistant Gestionnaire d’événements](#event-handler-wizard).

Vous pouvez ajouter un événement à la classe implémentant la boîte de dialogue à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Pour ajouter l’événement à une classe autre que celle de la boîte de dialogue, utilisez l’Assistant Gestionnaire d’événements.

**Pour ajouter un gestionnaire d’événements à un contrôle de boîte de dialogue**

1. Double-cliquez sur la ressource boîte de dialogue dans [l’affichage des ressources](../windows/how-to-create-a-resource-script-file.md#create-resources) pour ouvrir la ressource boîte de dialogue qui contient le contrôle dans [l’Éditeur de boîtes de dialogue](../windows/dialog-editor.md).

1. Cliquez avec le bouton droit sur le contrôle pour lequel vous souhaitez gérer l’événement de notification.

1. Dans le menu contextuel, choisissez **Ajouter un gestionnaire d’événements** pour afficher l’Assistant Gestionnaire d’événements.

1. Dans la zone **Type de message**, sélectionnez l’événement à ajouter à la classe sélectionnée dans la zone **Liste de classes**.

1. Acceptez le nom par défaut de la zone **Nom du gestionnaire de fonctions** ou indiquez le nom de votre choix.

1. Sélectionnez **Ajouter et modifier** pour ajouter le gestionnaire d’événements au projet et ouvrir l’éditeur de texte à l’emplacement de la nouvelle fonction pour ajouter le code approprié du gestionnaire d’événements.

   Si le type de message sélectionné possède déjà un gestionnaire d’événements pour la classe sélectionnée, **Ajouter et modifier** n’est pas disponible contrairement à **Modifier le code**. Sélectionnez **Modifier le code** pour ouvrir l’éditeur de texte à l’emplacement de la fonction existante.

Une autre solution consiste à ajouter les gestionnaires d’événements à partir de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Pour plus d’informations, consultez [Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-editing-or-deleting-controls.md).

## <a name="in-this-section"></a>Dans cette section

- [Assistant Gestionnaire d’événements](#event-handler-wizard)

## <a name="event-handler-wizard"></a>Assistant Gestionnaire d’événements

Cet Assistant ajoute un gestionnaire d’événements pour un contrôle de boîte de dialogue à la classe de votre choix. Si vous ajoutez un gestionnaire d’événements à partir de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), vous pouvez l’ajouter uniquement à la classe qui implémente la boîte de dialogue. Pour plus d’informations, consultez [Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-editing-or-deleting-controls.md).

- **Nom de la commande**

  Identifie le contrôle sélectionné pour lequel le gestionnaire d’événements est ajouté. Cette zone n’est pas disponible.

- **Type de message**

  Affiche la liste des gestionnaires de messages actuels possibles pour le contrôle sélectionné.

- **Nom du gestionnaire de fonctions**

  Affiche le nom de la fonction ajoutée pour gérer l’événement. Le nom par défaut est basé sur le type de message et la commande, précédé de `On`. Par exemple, pour le bouton appelé `IDC_BUTTON1`, le type de message `BN_CLICKED` affiche le nom du gestionnaire de fonctions `OnBnClickedButton1`.

- **Liste de classes**

  Affiche les classes disponibles auxquelles vous pouvez ajouter un gestionnaire d’événements. La classe de la boîte de dialogue sélectionnée s’affiche en rouge.

- **Description du gestionnaire**

  Fournit une description de l’élément sélectionné dans la zone **Type de message**. Cette zone n’est pas disponible.

- **Ajouter et modifier**

  Ajoute le gestionnaire de messages à l’objet ou à la classe sélectionné(e). Ouvre également l’éditeur de texte dans la nouvelle fonction, afin que vous puissiez ajouter le code du gestionnaire pour la notification de contrôle.

- **Modifier le code**

  Ouvre l’éditeur de texte sur la fonction existante sélectionnée pour pouvoir ajouter ou modifier le code du gestionnaire de notification de contrôle.
