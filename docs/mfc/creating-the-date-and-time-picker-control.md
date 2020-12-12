---
description: 'En savoir plus sur : création du contrôle de sélecteur de date et heure'
title: Création du contrôle de sélecteur de date et heure
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: 0ead228e98fdcbcfe707fee88c175453808e7047
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309730"
---
# <a name="creating-the-date-and-time-picker-control"></a>Création du contrôle de sélecteur de date et heure

Le mode de création du contrôle de sélecteur de date et d’heure varie selon que vous utilisez le contrôle dans une boîte de dialogue ou que vous le créez dans une fenêtre autre que la boîte de dialogue.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Pour utiliser CDateTimeCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle de sélecteur de date et heure à votre ressource de modèle de boîte de dialogue. Spécifiez son ID de contrôle.

1. Spécifiez les styles requis, à l’aide de la boîte de dialogue Propriétés du contrôle date et heure.

1. Utilisez l' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CDateTimeCtrl](reference/cdatetimectrl-class.md) avec la propriété Control. Vous pouvez utiliser ce membre pour appeler des `CDateTimeCtrl` fonctions membres.

1. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour mapper des fonctions de gestionnaire dans la classe de boîte de dialogue pour tous les messages de [notification](processing-notification-messages-in-date-and-time-picker-controls.md) de contrôle de sélecteur de date et d’heure que vous devez gérer (consultez [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](reference/cdialog-class.md#oninitdialog), définissez des styles supplémentaires pour l' `CDateTimeCtrl` objet.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Pour utiliser CDateTimeCtrl dans une fenêtre qui n’est pas une boîte de dialogue

1. Déclarez le contrôle dans la vue ou la classe de fenêtre.

1. Appelez la fonction membre [Create](reference/ctabctrl-class.md#create) du contrôle, éventuellement dans [OnInitialUpdate](reference/cview-class.md#oninitialupdate), éventuellement aussi tôt que la fonction gestionnaire [OnCreate](reference/cwnd-class.md#oncreate) de la fenêtre parente (si vous sous-classez le contrôle). Définissez les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Contrôles](controls-mfc.md)
