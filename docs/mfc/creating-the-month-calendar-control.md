---
description: 'En savoir plus sur : création du contrôle Month Calendar'
title: Création du contrôle Month Calendar
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 98c707e16f05a8f5e4d3b42e3c9504f74e4aca29
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309522"
---
# <a name="creating-the-month-calendar-control"></a>Création du contrôle Month Calendar

Le mode de création du contrôle Month Calendar varie selon que vous utilisez le contrôle dans une boîte de dialogue ou que vous le créez dans une fenêtre qui n’est pas une boîte de dialogue.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Pour utiliser CMonthCalCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle Month Calendar à votre ressource de modèle de boîte de dialogue. Spécifiez son ID de contrôle.

1. Spécifiez les styles requis, à l’aide de la boîte de dialogue Propriétés du contrôle Month Calendar.

1. Utilisez l' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CMonthCalCtrl](reference/cmonthcalctrl-class.md) avec la propriété Control. Vous pouvez utiliser ce membre pour appeler des `CMonthCalCtrl` fonctions membres.

1. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour mapper des fonctions de gestionnaire dans la classe de boîte de dialogue pour tous les messages de notification de contrôle de calendrier mensuel que vous devez gérer (voir [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](reference/cdialog-class.md#oninitdialog), définissez des styles supplémentaires pour l' `CMonthCalCtrl` objet.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Pour utiliser CMonthCalCtrl dans une fenêtre qui n’est pas une boîte de dialogue

1. Définissez le contrôle dans la vue ou la classe de fenêtre.

1. Appelez la fonction membre [Create](reference/cmonthcalctrl-class.md#create) du contrôle, éventuellement dans [OnInitialUpdate](reference/cview-class.md#oninitialupdate), éventuellement aussi tôt que la fonction gestionnaire [OnCreate](reference/cwnd-class.md#oncreate) de la fenêtre parente (si vous sous-classez le contrôle). Définissez les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CMonthCalCtrl](using-cmonthcalctrl.md)<br/>
[Contrôles](controls-mfc.md)
