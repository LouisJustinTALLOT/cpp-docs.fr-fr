---
title: Création du contrôle Month Calendar
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 9e430a86c2ac08bde0f031a4c91b9ae5c6f570f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907501"
---
# <a name="creating-the-month-calendar-control"></a>Création du contrôle Month Calendar

Le mode de création du contrôle Month Calendar varie selon que vous utilisez le contrôle dans une boîte de dialogue ou que vous le créez dans une fenêtre qui n’est pas une boîte de dialogue.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Pour utiliser CMonthCalCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle Month Calendar à votre ressource de modèle de boîte de dialogue. Spécifiez son ID de contrôle.

1. Spécifiez les styles requis, à l’aide de la boîte de dialogue Propriétés du contrôle Month Calendar.

1. Utilisez l' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) avec la propriété Control. Vous pouvez utiliser ce membre pour appeler `CMonthCalCtrl` des fonctions membres.

1. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour mapper des fonctions de gestionnaire dans la classe de boîte de dialogue pour tous les messages de notification de contrôle de calendrier mensuel que vous devez gérer (voir [mappage de messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez des styles supplémentaires pour l' `CMonthCalCtrl` objet.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Pour utiliser CMonthCalCtrl dans une fenêtre qui n’est pas une boîte de dialogue

1. Définissez le contrôle dans la vue ou la classe de fenêtre.

1. Appelez la fonction membre [Create](../mfc/reference/cmonthcalctrl-class.md#create) du contrôle, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement aussi tôt que la fonction gestionnaire [OnCreate](../mfc/reference/cwnd-class.md#oncreate) de la fenêtre parente (si vous sous-classez le contrôle). Définissez les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
