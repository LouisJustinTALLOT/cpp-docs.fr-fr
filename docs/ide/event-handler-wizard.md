---
title: Assistant Gestionnaire d'événements
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
ms.openlocfilehash: e48d995aed0c59cc4ba7b645706448b5c3618b4a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654166"
---
# <a name="event-handler-wizard"></a>Assistant Gestionnaire d'événements

Cet Assistant ajoute un gestionnaire d’événements pour un contrôle de boîte de dialogue à la classe de votre choix. Si vous ajoutez un gestionnaire d’événements à partir de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), vous pouvez l’ajouter uniquement à la classe qui implémente la boîte de dialogue. Pour plus d’informations, consultez [Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md).

- **Nom de la commande**

   Identifie le contrôle sélectionné pour lequel le gestionnaire d’événements est ajouté. Cette zone n’est pas disponible.

- **Type de message**

   Affiche la liste des gestionnaires de messages actuels possibles pour le contrôle sélectionné.

- **Nom du gestionnaire de fonctions**

   Affiche le nom de la fonction ajoutée pour gérer l’événement. Par défaut, le nom est basé sur le type de message et la commande, précédé de « On ». Par exemple, pour le bouton appelé `IDC_BUTTON1`, le type de message `BN_CLICKED` affiche le nom du gestionnaire de fonctions `OnBnClickedButton1`.

- **Liste de classes**

   Affiche les classes disponibles auxquelles vous pouvez ajouter un gestionnaire d’événements. La classe de la boîte de dialogue sélectionnée s’affiche en rouge.

- **Description du gestionnaire**

   Fournit une description de l’élément sélectionné dans la zone **Type de message**. Cette zone n’est pas disponible.

- **Ajouter et modifier**

   Ajoute le gestionnaire de messages à l’objet ou la classe sélectionné et ouvre l’éditeur de texte sur la nouvelle fonction pour vous permettre d’ajouter le code du gestionnaire de notification de contrôle.

- **Modifier le code**

   Ouvre l’éditeur de texte sur la fonction existante sélectionnée pour pouvoir ajouter ou modifier le code du gestionnaire de notification de contrôle.

## <a name="see-also"></a>Voir aussi

[Ajout d’un gestionnaire d’événements](../ide/adding-an-event-handler-visual-cpp.md)