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
ms.openlocfilehash: 994f81524001a80d1cf0dd3783b9de742d61e84d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365846"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Déclaration d'une variable basée sur votre nouvelle classe de contrôle

Une fois que vous avez créé une classe de contrôle MFC, vous pouvez déclarer une variable basée sur elle. Pour fournir un contexte pour la nouvelle variable, vous devez ouvrir l’éditeur de dialogue et modifier la boîte de dialogue dans laquelle vous souhaitez utiliser votre contrôle réutilisable. En outre, la boîte de dialogue doit déjà avoir une classe qui lui est associée. Pour plus d’informations sur l’utilisation de l’éditeur de dialogue, voir [Dialog Editor](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Déclarer une variable en fonction de votre classe réutilisable

1. Lors de l’édition de la boîte de dialogue, faites glisser un contrôle du même type que la classe de base de votre nouveau contrôle à partir de la barre d’outils Controls sur la boîte de dialogue.

1. Placez le pointeur de la souris sur le contrôle abandonné.

1. Tout en appuyant sur la touche CTRL, cliquez double sur le contrôle.

   La boîte de dialogue [Variable Add Member](../../ide/add-member-variable-wizard.md) apparaît.

1. Dans la boîte **d’accès,** sélectionnez l’accès correct pour votre contrôle.

1. Cliquez sur la case à cocher **variable Control.**

1. Dans la boîte **à noms variable,** tapez un nom.

1. Sous **catégorie**, cliquez sur **Contrôle**.

1. Dans la liste **d’identification de contrôle,** choisissez le contrôle que vous avez ajouté. La liste **de type variable** doit afficher le type variable correct, et la boîte de type **Contrôle** doit afficher le type de contrôle correct.

1. Dans la boîte **commentaire,** ajoutez n’importe quel commentaire que vous souhaitez apparaître dans votre code.

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
