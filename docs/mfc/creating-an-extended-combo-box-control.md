---
title: Création d'un contrôle de zone de liste déroulante étendue
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 87e2e1cd3c29ba838a17c24ece4a89adda21db0c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907722"
---
# <a name="creating-an-extended-combo-box-control"></a>Création d'un contrôle de zone de liste déroulante étendue

La façon dont le contrôle de zone de liste déroulante étendue est créé varie selon que vous utilisez le contrôle dans une boîte de dialogue ou que vous le créez dans une fenêtre qui n’est pas une boîte de dialogue.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Pour utiliser CComboBoxEx directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle de zone de liste déroulante étendue à votre ressource de modèle de boîte de dialogue. Spécifiez son ID de contrôle.

1. Spécifiez les styles requis, à l’aide de la boîte de dialogue Propriétés du contrôle de zone de liste déroulante étendue.

1. Utilisez l' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) avec la propriété Control. Vous pouvez utiliser ce membre pour appeler `CComboBoxEx` des fonctions membres.

1. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour mapper les fonctions de gestionnaire de la classe de boîte de dialogue pour tous les messages de notification de contrôle de zone de liste déroulante étendus que vous devez gérer (consultez [mappage de messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez des styles supplémentaires pour l' `CComboBoxEx` objet.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Pour utiliser CComboBoxEx dans une fenêtre qui n’est pas une boîte de dialogue

1. Définissez le contrôle dans la vue ou la classe de fenêtre.

1. Appelez la fonction membre [Create](../mfc/reference/ctabctrl-class.md#create) du contrôle, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement aussi tôt que la fonction gestionnaire [OnCreate](../mfc/reference/cwnd-class.md#oncreate) de la fenêtre parente. Définissez les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
