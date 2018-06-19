---
title: Boîtes de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c8de283d81aa9d260b891f285f06555dc67895f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346673"
---
# <a name="dialog-boxes"></a>Boîtes de dialogue
Pour Windows, les applications communiquent fréquemment avec l’utilisateur via les boîtes de dialogue. Classe [CDialog](../mfc/reference/cdialog-class.md) fournit une interface pour la gestion des boîtes de dialogue, l’éditeur de boîte de dialogue Visual C++ rend facile à concevoir des boîtes de dialogue et créer leurs ressources de modèle de boîte de dialogue et Assistants Code simplifient le processus d’initialisation et validation des contrôles dans une boîte de dialogue et de la collecte des valeurs entrées par l’utilisateur.  
  
 Boîtes de dialogue contiennent des contrôles, notamment :  
  
-   Contrôles communs Windows telles que modifier les zones, boutons de commande, zones de liste, zones de liste déroulante, les contrôles d’arborescence, les contrôles de liste et indicateurs de progression.  
  
-   Contrôles ActiveX.  
  
-   Contrôles owner-drawn : les contrôles que vous êtes responsable du dessin dans la boîte de dialogue.  
  
 La plupart des boîtes de dialogue sont modales, ce qui oblige l’utilisateur fermer la boîte de dialogue avant d’utiliser une autre partie du programme. Mais il est possible de créer des boîtes de dialogue non modale qui permettent aux utilisateurs de travailler avec d’autres fenêtres pendant que la boîte de dialogue est ouverte. MFC prend en charge les deux types de boîte de dialogue avec la classe `CDialog`. Les contrôles sont organisés et gérés à l’aide d’une ressource de modèle de boîte de dialogue, créée avec le [éditeur de boîte de dialogue](../windows/dialog-editor.md).  
  
 [Feuilles de propriétés](../mfc/property-sheets-mfc.md), également appelé onglet boîtes de dialogue, sont des boîtes de dialogue qui contiennent des « pages » de contrôles de boîte de dialogue distinctes. Chaque page possède un dossier de fichiers « onglet » en haut. Cliquer sur un onglet pour afficher cette page au début de la boîte de dialogue.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Exemple : affichage d’une boîte de dialogue via une commande de menu](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)  
  
-   [Composants de boîte de dialogue dans le framework](../mfc/dialog-box-components-in-the-framework.md)  
  
-   [Boîtes de dialogue modales et non modales](../mfc/modal-and-modeless-dialog-boxes.md)  
  
-   [Feuilles de propriétés et pages de propriétés](../mfc/property-sheets-and-property-pages-mfc.md) dans une boîte de dialogue  
  
-   [Création de la ressource de boîte de dialogue](../mfc/creating-the-dialog-resource.md)  
  
-   [Création d’une classe de boîte de dialogue des Assistants Code](../mfc/creating-a-dialog-class-with-code-wizards.md)  
  
-   [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)  
  
-   [Échange de données de boîtes de dialogue (DDX) et validation (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Accès de type sécurisé aux contrôles dans une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [Mappage des messages Windows à votre classe](../mfc/mapping-windows-messages-to-your-class.md)  
  
-   [Fonctions membres couramment substituées](../mfc/commonly-overridden-member-functions.md)  
  
-   [Fonctions membres couramment ajoutées](../mfc/commonly-added-member-functions.md)  
  
-   [Classes de boîte de dialogue communes](../mfc/common-dialog-classes.md)  
  
-   [Boîtes de dialogue dans OLE](../mfc/dialog-boxes-in-ole.md)  
  
-   Créer une application dont l’interface utilisateur est une boîte de dialogue : consultez le [CMNCTRL1](../visual-cpp-samples.md) ou [CMNCTRL2](../visual-cpp-samples.md) des exemples de programmes. L’Assistant Application fournit également cette option.  
  
-   [Exemples](../mfc/dialog-sample-list.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)
