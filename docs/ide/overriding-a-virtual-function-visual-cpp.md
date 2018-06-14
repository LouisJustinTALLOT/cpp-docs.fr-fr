---
title: Remplacement d’une fonction virtuelle (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.virtualfunc.override
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8580d27442b0cae7e343a568beaa9aeae500461
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337741"
---
# <a name="overriding-a-virtual-function-visual-c"></a>Remplacement d’une fonction virtuelle (Visual C++)
Vous pouvez remplacer des fonctions virtuelles définies dans une classe de base à partir de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) de Visual Studio.  
  
### <a name="to-override-a-virtual-function-in-the-properties-window"></a>Pour remplacer une fonction virtuelle dans la fenêtre Propriétés  
  
1.  Dans Affichage de classes, cliquez sur la classe.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le bouton **Remplacements**.  
  
    > [!NOTE]
    >  Le bouton **Remplacements** est disponible quand vous sélectionnez le nom de la classe dans Affichage de classes ou que vous cliquez dans la fenêtre source.  
  
     La colonne de gauche liste les fonctions virtuelles. Si le nom d’une fonction virtuelle apparaît également dans la colonne de droite, un remplacement a déjà été implémenté.  
  
3.  Si la fonction n’a pas de remplacement, cliquez sur la cellule de la colonne de droite dans la fenêtre Propriétés pour afficher le nom suggéré du remplacement de la fonction comme \<add>*FuncName*.  
  
4.  Cliquez sur le nom suggéré pour ajouter du code stub pour la fonction.  
  
5.  Pour modifier une fonction de remplacement, double-cliquez sur le nom de la fonction dans Affichage de classes et modifiez le code dans la fenêtre source.  
  
 Pour supprimer un remplacement, cliquez sur le nom de la fonction de remplacement dans la colonne de droite et sélectionnez \<delete>*FuncName*. Le code de la fonction est commenté.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)   
 [Ajout d’une fonction membre](../ide/adding-a-member-function-visual-cpp.md)   
 [Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md)   
 [Gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Parcours de la structure de classe](../ide/navigating-the-class-structure-visual-cpp.md)