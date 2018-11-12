---
title: Création du contrôle Month Calendar
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: f98ce6c0272b64442d42cb0ba78b10affe5ede8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523770"
---
# <a name="creating-the-month-calendar-control"></a>Création du contrôle Month Calendar

Création du contrôle month calendar dépend à l’aide du contrôle dans une boîte de dialogue ou de la création dans un autre type de fenêtre.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Pour utiliser CMonthCalCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de la boîte de dialogue, ajoutez un contrôle Month Calendar à votre ressource de modèle de boîte de dialogue. Spécifier son ID de contrôle.

1. Spécifiez les styles requis, à l’aide de la boîte de dialogue Propriétés du contrôle month calendar.

1. Utilisez le [Assistant Ajout de Variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) avec la propriété du contrôle. Vous pouvez utiliser ce membre pour appeler `CMonthCalCtrl` fonctions membres.

1. Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe de boîte de dialogue pour toute notification de contrôle de calendrier mois messages vous devez gérer (consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez d’autres styles pour le `CMonthCalCtrl` objet.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Pour utiliser CMonthCalCtrl dans un autre type de fenêtre

1. Définissez le contrôle dans la classe de vue ou de la fenêtre.

1. Le contrôle de l’appel [créer](../mfc/reference/cmonthcalctrl-class.md#create) fonction membre, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement en même temps que la fenêtre parente [OnCreate](../mfc/reference/cwnd-class.md#oncreate) fonction de gestionnaire (si vous êtes sous-classe le contrôle). Définir les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

