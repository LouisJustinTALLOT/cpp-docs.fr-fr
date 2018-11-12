---
title: Déclaration d'une variable basée sur votre nouvelle classe de contrôle
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: f79ecb6edec58d26042818d647a0ea121dd41a55
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595687"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Déclaration d'une variable basée sur votre nouvelle classe de contrôle

Une fois que vous avez créé une classe de contrôle MFC, vous pouvez déclarer une variable basée sur celui-ci. Pour fournir un contexte pour la nouvelle variable, vous devez ouvrir l’éditeur de boîtes de dialogue et modifier la boîte de dialogue dans laquelle vous souhaitez utiliser votre contrôle réutilisable. En outre, la boîte de dialogue doit avoir déjà associée à une classe. Pour plus d’informations sur l’utilisation de l’éditeur de boîtes de dialogue, consultez [boîte de dialogue Éditeur](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Pour déclarer une variable basée sur votre classe réutilisable

1. Lors de la modification de la boîte de dialogue, faites glisser un contrôle du même type que la classe de base de votre nouveau contrôle à partir de la barre d’outils de contrôles sur la boîte de dialogue.

1. Placez le pointeur de la souris sur le contrôle supprimé.

1. Tout en appuyant sur la touche CTRL enfoncée, double-cliquez sur le contrôle.

   Le [ajouter une Variable membre](../../ide/add-member-variable-wizard.md) boîte de dialogue s’affiche.

1. Dans le **accès** , sélectionnez l’accès correct pour votre contrôle.

1. Cliquez sur le **variable de contrôle** case à cocher.

1. Dans le **nom de la Variable** , tapez un nom.

1. Sous **catégorie**, cliquez sur **contrôle**.

1. Dans le **ID de contrôle** liste, sélectionnez le contrôle que vous avez ajouté. Le **type de Variable** liste affiche le type de variable correct et le **type de contrôle** zone doit afficher le type de contrôle correct.

9. Dans le **commentaire** zone, ajoutez des commentaires que vous souhaitez voir apparaître dans votre code.

10. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[Mappage des messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigating-the-class-structure-visual-cpp.md)
