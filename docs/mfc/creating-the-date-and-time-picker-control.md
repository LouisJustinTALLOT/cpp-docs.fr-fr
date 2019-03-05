---
title: Création du contrôle de sélecteur de date et heure
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: b3dd04d917667ff04001a455263d2a2f4af9bf9c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282069"
---
# <a name="creating-the-date-and-time-picker-control"></a>Création du contrôle de sélecteur de date et heure

Comment le contrôle de sélecteur de date et d’heure est créé dépend de si vous l’utilisation du contrôle dans une boîte de dialogue ou créée dans un autre type de fenêtre.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Pour utiliser CDateTimeCtrl directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue Ajouter une Date et un contrôle de sélecteur de temps à votre ressource de modèle de boîte de dialogue. Spécifier son ID de contrôle.

1. Spécifiez les styles nécessaires, à l’aide de la boîte de dialogue Propriétés de contrôle de sélecteur de date et d’heure.

1. Utilisez le [Assistant Ajout de Variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) avec la propriété du contrôle. Vous pouvez utiliser ce membre pour appeler `CDateTimeCtrl` fonctions membres.

1. Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe de boîte de dialogue pour n’importe quel contrôle date time picker [notification](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) messages, vous devez gérer (consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez d’autres styles pour le `CDateTimeCtrl` objet.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Pour utiliser CDateTimeCtrl dans un autre type de fenêtre

1. Déclarer le contrôle dans la classe de vue ou de la fenêtre.

1. Le contrôle de l’appel [créer](../mfc/reference/ctabctrl-class.md#create) fonction membre, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement en même temps que la fenêtre parente [OnCreate](../mfc/reference/cwnd-class.md#oncreate) fonction de gestionnaire (si vous êtes sous-classe le contrôle). Définir les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
