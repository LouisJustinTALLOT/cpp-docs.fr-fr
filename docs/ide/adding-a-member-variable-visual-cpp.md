---
title: Ajout d’une variable membre (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.member.variable
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa2a8ef8f7bcdc2d90893acdad98705c9588a5d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325729"
---
# <a name="adding-a-member-variable--visual-c"></a>Ajout d'une variable membre (Visual C++)
Vous pouvez ajouter une variable membre à une classe à l’aide de l’affichage de classes. Les variables membres peuvent être utilisées pour [l’échange et la validation de données](../mfc/dialog-data-exchange-and-validation.md), ou elles peuvent être génériques. L’Assistant Ajout de variable membre est spécialement conçu pour prélever les informations importantes et les utiliser pour insérer des éléments dans vos fichiers sources aux emplacements appropriés. Vous pouvez ajouter une variable membre à partir de [l’Éditeur de boîtes de dialogue](../windows/dialog-editor.md) dans [l’affichage des ressources](../windows/resource-view-window.md), ou à partir de [l’affichage de classes](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Quand vous concevez et implémentez une boîte de dialogue, il peut être plus efficace d’utiliser l’Éditeur de boîtes de dialogue pour ajouter les contrôles de boîte de dialogue, puis d’implémenter les variables membres des contrôles.  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Pour ajouter une variable membre pour un contrôle de boîte de dialogue dans l’affichage des ressources à l’aide de l’Assistant Ajout de variable membre  
  
1.  Dans l’affichage des ressources, développez le nœud du projet et le nœud Boîte de dialogue pour afficher la liste des boîtes de dialogue du projet.  
  
2.  Double-cliquez sur la boîte de dialogue à laquelle vous souhaitez ajouter la variable membre pour l’ouvrir dans l’Éditeur de boîtes de dialogue.  
  
3.  Dans la boîte de dialogue affichée dans l’Éditeur de boîtes de dialogue, cliquez avec le bouton droit sur le contrôle auquel vous souhaitez ajouter la variable membre.  
  
4.  Dans le menu contextuel, cliquez sur **Ajouter une variable** afin d’afficher [l’Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md).  
  
    > [!NOTE]
    >  Une valeur par défaut vous est déjà proposée dans **ID de contrôle**.  
  
5.  Indiquez les informations nécessaires dans les zones appropriées de l’Assistant. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md).  
  
6.  Cliquez sur **Terminer** pour ajouter la définition et le code d’implémentation au projet et fermer l’Assistant.  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Pour ajouter une variable membre à partir de l’affichage de classes à l’aide de l’Assistant Ajout de variable membre  
  
1.  Dans [l’affichage de classes](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), développez le nœud du projet afin d’afficher ses classes.  
  
2.  Cliquez avec le bouton droit sur la classe à laquelle vous souhaitez ajouter une variable.  
  
3.  Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une variable** afin d’afficher l’Assistant Ajout de variable membre.  
  
4.  Indiquez les informations nécessaires dans les zones appropriées de l’Assistant. Pour plus d’informations, consultez [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md).  
  
5.  Cliquez sur **Terminer** pour ajouter la définition et le code d’implémentation au projet et fermer l’Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)   
 [Ajout d’une fonction membre](../ide/adding-a-member-function-visual-cpp.md)   
 [Gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Parcours de la structure de classe](../ide/navigating-the-class-structure-visual-cpp.md)