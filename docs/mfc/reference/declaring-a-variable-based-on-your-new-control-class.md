---
title: Déclaration d’une Variable basée sur votre nouvelle classe de contrôle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.control.variable
dev_langs:
- C++
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 677006d441c940f478b3d23744d1057667307e1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Déclaration d'une variable basée sur votre nouvelle classe de contrôle
Une fois que vous avez créé une classe de contrôle MFC, vous pouvez déclarer une variable basée sur celui-ci. Pour fournir un contexte pour la nouvelle variable, vous devez ouvrir l’éditeur de boîte de dialogue et modifiez la boîte de dialogue dans laquelle vous souhaitez utiliser votre contrôle réutilisable. En outre, la boîte de dialogue doit avoir déjà associée à une classe. Pour plus d’informations sur l’utilisation de l’éditeur de boîte de dialogue, consultez [boîte de dialogue Éditeur](../../windows/dialog-editor.md).  
  
### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Pour déclarer une variable en fonction de votre classe réutilisable  
  
1.  Lors de la modification de la boîte de dialogue, faites glisser un contrôle du même type que la classe de base de votre nouveau contrôle à partir de la barre d’outils de contrôle sur la boîte de dialogue.  
  
2.  Placez le pointeur de la souris sur le contrôle supprimé.  
  
3.  Tout en appuyant sur la touche CTRL ENFONCÉE, double-cliquez sur le contrôle.  
  
     Le [ajouter une Variable membre](../../ide/add-member-variable-wizard.md) boîte de dialogue s’affiche.  
  
4.  Dans le **accès** , sélectionnez l’accès correct pour votre contrôle.  
  
5.  Cliquez sur le **la variable de contrôle** case à cocher.  
  
6.  Dans le **nom de la Variable** , tapez un nom.  
  
7.  Sous **catégorie**, cliquez sur **contrôle**.  
  
8.  Dans le **ID de contrôle** liste, sélectionnez le contrôle que vous avez ajouté. Le **le type de Variable** liste affiche le type de variable correct et le **type de contrôle** zone doit afficher le type de contrôle correct.  
  
9. Dans le **commentaire** zone, ajouter des commentaires que vous souhaitez voir apparaître dans votre code.  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)   
 [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)   
 [Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)   
 [Ajout d’une Variable membre](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Une fonction virtuelle de substitution](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigation dans la Structure de classe](../../ide/navigating-the-class-structure-visual-cpp.md)
