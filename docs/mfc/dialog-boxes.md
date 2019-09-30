---
title: Boîtes de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: 18b4c4d1386716a0a3282b88d6fdf5a701abce08
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685798"
---
# <a name="dialog-boxes"></a>Boîtes de dialogue

Les applications pour Windows communiquent fréquemment avec l’utilisateur par le biais de boîtes de dialogue. La classe [CDialog](../mfc/reference/cdialog-class.md) fournit une interface pour la gestion des boîtes de C++ dialogue, l’éditeur de boîtes de dialogue visuelles facilite la conception des boîtes de dialogue et la création de leurs ressources de modèle de boîte de dialogue, tandis que les assistants code simplifient le processus d’initialisation et de validation de l’interface contrôles dans une boîte de dialogue et collecte des valeurs entrées par l’utilisateur.

Les boîtes de dialogue contiennent des contrôles, notamment :

- Contrôles communs Windows, tels que les zones d’édition, les boutons de commande, les zones de liste, les zones de liste déroulante, les contrôles d’arborescence, les contrôles de liste et les indicateurs de progression.

- Contrôles ActiveX.

- Contrôles owner-drawn : contrôles que vous êtes chargé de dessiner dans la boîte de dialogue.

La plupart des boîtes de dialogue sont modales, ce qui oblige l’utilisateur à fermer la boîte de dialogue avant d’utiliser une autre partie du programme. Toutefois, il est possible de créer des boîtes de dialogue non modales, qui permettent aux utilisateurs d’utiliser d’autres fenêtres pendant que la boîte de dialogue est ouverte. MFC prend en charge les deux types de boîtes de dialogue avec la classe `CDialog`. Les contrôles sont organisés et gérés à l’aide d’une ressource de modèle de boîte de dialogue, créée à l’aide de l' [éditeur de boîtes de dialogue](../windows/dialog-editor.md).

Les [feuilles de propriétés](../mfc/property-sheets-mfc.md), également appelées boîtes de dialogue à onglets, sont des boîtes de dialogue qui contiennent des « pages » de contrôles de boîte de dialogue distincts. Chaque page comporte un dossier de fichiers « onglet » en haut. Le fait de cliquer sur un onglet amène cette page au début de la boîte de dialogue.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Exemple : Affichage d’une boîte de dialogue via une commande de menu](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [Composants de boîte de dialogue dans le Framework](../mfc/dialog-box-components-in-the-framework.md)

- [Boîtes de dialogue modales et non modales](../mfc/modal-and-modeless-dialog-boxes.md)

- [Feuilles de propriétés et pages de propriétés](../mfc/property-sheets-and-property-pages-mfc.md) dans une boîte de dialogue

- [Création de la ressource de boîte de dialogue](../mfc/creating-the-dialog-resource.md)

- [Création d’une classe de boîte de dialogue à l’aide des assistants code](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)

- [Échange de données de boîtes de dialogue (DDX) et validation (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Accès de type sécurisé aux contrôles dans une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Mappage des messages Windows à votre classe](../mfc/mapping-windows-messages-to-your-class.md)

- [Fonctions membres couramment substituées](../mfc/commonly-overridden-member-functions.md)

- [Fonctions membres couramment ajoutées](../mfc/commonly-added-member-functions.md)

- [Classes de boîtes de dialogue communes](../mfc/common-dialog-classes.md)

- [Boîtes de dialogue dans OLE](../mfc/dialog-boxes-in-ole.md)

- Créer une application dont l’interface utilisateur est une boîte de dialogue : consultez les exemples de programmes [CMNCTRL1](../overview/visual-cpp-samples.md) ou [CMNCTRL2](../overview/visual-cpp-samples.md) . L’Assistant application fournit également cette option.

- [Exemples](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](../mfc/user-interface-elements-mfc.md)
