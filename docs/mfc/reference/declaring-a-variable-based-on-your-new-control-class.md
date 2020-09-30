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
ms.openlocfilehash: a828351a9e789228143d43d4c0a756abda879989
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506681"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Déclaration d'une variable basée sur votre nouvelle classe de contrôle

Une fois que vous avez créé une classe de contrôle MFC, vous pouvez déclarer une variable en fonction de celle-ci. Pour fournir un contexte pour la nouvelle variable, vous devez ouvrir l’éditeur de boîtes de dialogue et modifier la boîte de dialogue dans laquelle vous souhaitez utiliser votre contrôle réutilisable. En outre, une classe doit déjà être associée à la boîte de dialogue. Pour plus d’informations sur l’utilisation de l’éditeur de boîtes de dialogue, consultez [éditeur de boîtes de dialogue](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Pour déclarer une variable en fonction de votre classe réutilisable

1. Lors de la modification de la boîte de dialogue, faites glisser un contrôle du même type que la classe de base de votre nouveau contrôle à partir de la barre d’outils contrôles vers la boîte de dialogue.

1. Placez le pointeur de la souris sur le contrôle déplacé.

1. Tout en appuyant sur la touche CTRL, double-cliquez sur le contrôle.

   La boîte de dialogue [Ajouter une variable membre](../../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) s’affiche.

1. Dans la zone **accès** , sélectionnez l’accès approprié pour votre contrôle.

1. Activez la case à cocher **variable de contrôle** .

1. Dans la zone nom de la **variable** , tapez un nom.

1. Sous **catégorie**, cliquez sur **contrôle**.

1. Dans la liste **ID de contrôle** , sélectionnez le contrôle que vous avez ajouté. La liste des **types de variables** doit afficher le type de variable correct, et la zone **type de contrôle** doit afficher le type de contrôle approprié.

1. Dans la zone **Commentaire** , ajoutez tous les commentaires que vous souhaitez voir apparaître dans votre code.

1. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[Mappage de messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
