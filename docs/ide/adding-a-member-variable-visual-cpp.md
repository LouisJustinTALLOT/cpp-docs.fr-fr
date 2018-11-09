---
title: Ajout d’une variable membre (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.member.variable
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: 3c7f64fae00e489da7c71bcfe5731db72e1afdf7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595774"
---
# <a name="adding-a-member-variable--visual-c"></a>Ajout d'une variable membre (Visual C++)

Vous pouvez ajouter une variable membre à une classe à l’aide de l’affichage de classes. Les variables membres peuvent être utilisées pour [l’échange et la validation de données](../mfc/dialog-data-exchange-and-validation.md), ou elles peuvent être génériques. L’Assistant Ajout de variable membre est spécialement conçu pour prélever les informations importantes et les utiliser pour insérer des éléments dans vos fichiers sources aux emplacements appropriés. Vous pouvez ajouter une variable membre à partir de [l’Éditeur de boîtes de dialogue](../windows/dialog-editor.md) dans [l’affichage des ressources](../windows/resource-view-window.md), ou à partir de [l’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
>  Quand vous concevez et implémentez une boîte de dialogue, il peut être plus efficace d’utiliser l’Éditeur de boîtes de dialogue pour ajouter les contrôles de boîte de dialogue, puis d’implémenter les variables membres des contrôles.

### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Pour ajouter une variable membre pour un contrôle de boîte de dialogue dans l’affichage des ressources à l’aide de l’Assistant Ajout de variable membre

1. Dans l’affichage des ressources, développez le nœud du projet et le nœud Boîte de dialogue pour afficher la liste des boîtes de dialogue du projet.

1. Double-cliquez sur la boîte de dialogue à laquelle vous souhaitez ajouter la variable membre pour l’ouvrir dans l’Éditeur de boîtes de dialogue.

1. Dans la boîte de dialogue affichée dans l’Éditeur de boîtes de dialogue, cliquez avec le bouton droit sur le contrôle auquel vous souhaitez ajouter la variable membre.

1. Dans le menu contextuel, cliquez sur **Ajouter une variable** afin d’afficher [l’Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md).

   > [!NOTE]
   > Une valeur par défaut vous est déjà proposée dans **ID de contrôle**.

1. Indiquez les informations nécessaires dans les zones appropriées de l’Assistant. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md).

1. Cliquez sur **Terminer** pour ajouter la définition et le code d’implémentation au projet et fermer l’Assistant.

### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Pour ajouter une variable membre à partir de l’affichage de classes à l’aide de l’Assistant Ajout de variable membre

1. Dans [l’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), développez le nœud du projet afin d’afficher ses classes.

1. Cliquez avec le bouton droit sur la classe à laquelle vous souhaitez ajouter une variable.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une variable** afin d’afficher l’Assistant Ajout de variable membre.

1. Indiquez les informations nécessaires dans les zones appropriées de l’Assistant. Pour plus d’informations, consultez [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md).

1. Cliquez sur **Terminer** pour ajouter la définition et le code d’implémentation au projet et fermer l’Assistant.

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)<br>
[Ajout d’une fonction membre](../ide/adding-a-member-function-visual-cpp.md)<br>
[Gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Parcours de la structure de classe](../ide/navigating-the-class-structure-visual-cpp.md)