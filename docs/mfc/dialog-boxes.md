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
ms.openlocfilehash: da6a2eca7c2366e519b9bf2e809b042dc3ee2e50
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616871"
---
# <a name="dialog-boxes"></a>Boîtes de dialogue

Les applications pour Windows communiquent fréquemment avec l’utilisateur par le biais de boîtes de dialogue. La classe [CDialog](reference/cdialog-class.md) fournit une interface pour la gestion des boîtes de dialogue, l’éditeur de boîtes de dialogue Visual C++ facilite la conception de boîtes de dialogue et la création de leurs ressources de modèle de boîte de dialogue, tandis que les assistants code simplifient le processus d’initialisation et de validation des contrôles dans une boîte de dialogue et de collecte des valeurs entrées par l’utilisateur.

Les boîtes de dialogue contiennent des contrôles, notamment :

- Contrôles communs Windows, tels que les zones d’édition, les boutons de commande, les zones de liste, les zones de liste déroulante, les contrôles d’arborescence, les contrôles de liste et les indicateurs de progression.

- Contrôles ActiveX.

- Contrôles owner-drawn : contrôles que vous êtes chargé de dessiner dans la boîte de dialogue.

La plupart des boîtes de dialogue sont modales, ce qui oblige l’utilisateur à fermer la boîte de dialogue avant d’utiliser une autre partie du programme. Toutefois, il est possible de créer des boîtes de dialogue non modales, qui permettent aux utilisateurs d’utiliser d’autres fenêtres pendant que la boîte de dialogue est ouverte. MFC prend en charge les deux types de boîtes de dialogue avec la classe `CDialog` . Les contrôles sont organisés et gérés à l’aide d’une ressource de modèle de boîte de dialogue, créée à l’aide de l' [éditeur de boîtes de dialogue](../windows/dialog-editor.md).

Les [feuilles de propriétés](property-sheets-mfc.md), également appelées boîtes de dialogue à onglets, sont des boîtes de dialogue qui contiennent des « pages » de contrôles de boîte de dialogue distincts. Chaque page comporte un dossier de fichiers « onglet » en haut. Le fait de cliquer sur un onglet amène cette page au début de la boîte de dialogue.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Exemple : affichage d'une boîte de dialogue via une commande de menu](example-displaying-a-dialog-box-via-a-menu-command.md)

- [Composants de boîte de dialogue dans le Framework](dialog-box-components-in-the-framework.md)

- [Boîtes de dialogue modales et non modales](modal-and-modeless-dialog-boxes.md)

- [Feuilles de propriétés et pages de propriétés](property-sheets-and-property-pages-mfc.md) dans une boîte de dialogue

- [Création de ressources de boîte de dialogue](creating-the-dialog-resource.md)

- [Création d’une classe de boîte de dialogue à l’aide des assistants code](creating-a-dialog-class-with-code-wizards.md)

- [Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)

- [Échange de données de boîtes de dialogue (DDX) et validation (DDV)](dialog-data-exchange-and-validation.md)

- [Accès de type sécurisé aux contrôles d'une boîte de dialogue](type-safe-access-to-controls-in-a-dialog-box.md)

- [Mappage des messages Windows à votre classe](mapping-windows-messages-to-your-class.md)

- [Fonctions membres couramment substituées](commonly-overridden-member-functions.md)

- [Fonctions membres couramment ajoutées](commonly-added-member-functions.md)

- [Classes de boîtes de dialogue communes](common-dialog-classes.md)

- [Boîtes de dialogue dans OLE](dialog-boxes-in-ole.md)

- Créer une application dont l’interface utilisateur est une boîte de dialogue : consultez les exemples de programmes [CMNCTRL1](../overview/visual-cpp-samples.md) ou [CMNCTRL2](../overview/visual-cpp-samples.md) . L’Assistant application fournit également cette option.

- [Exemples](dialog-sample-list.md)

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](user-interface-elements-mfc.md)
