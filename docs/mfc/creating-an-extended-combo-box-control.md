---
title: Création d'un contrôle de zone de liste déroulante étendue
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: bfc201fbb10c3caa3eaabd0e81206b9493ff7196
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153279"
---
# <a name="creating-an-extended-combo-box-control"></a>Création d'un contrôle de zone de liste déroulante étendue

Comment le contrôle de zone de liste déroulante étendue est créé dépend de si vous l’utilisation du contrôle dans une boîte de dialogue ou créée dans un autre type de fenêtre.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Pour utiliser CComboBoxEx directement dans une boîte de dialogue

1. Dans l’éditeur de boîtes de dialogue, ajoutez un contrôle de zone de liste déroulante étendue à votre ressource de modèle de boîte de dialogue. Spécifier son ID de contrôle.

1. Spécifiez les styles requis, à l’aide de la boîte de dialogue Propriétés du contrôle de zone de liste déroulante étendue.

1. Utilisez le [Assistant Ajout de Variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) avec la propriété du contrôle. Vous pouvez utiliser ce membre pour appeler `CComboBoxEx` fonctions membres.

1. Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe de boîte de dialogue pour tout message notification du contrôle de zone de liste déroulante étendue vous devez gérer (consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).

1. Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez d’autres styles pour le `CComboBoxEx` objet.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Pour utiliser CComboBoxEx dans un autre type de fenêtre

1. Définissez le contrôle dans la classe de vue ou de la fenêtre.

1. Le contrôle de l’appel [créer](../mfc/reference/ctabctrl-class.md#create) fonction membre, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement en même temps que la fenêtre parente [OnCreate](../mfc/reference/cwnd-class.md#oncreate) fonction gestionnaire. Définir les styles pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
