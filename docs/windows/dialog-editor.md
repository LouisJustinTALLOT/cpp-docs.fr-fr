---
description: 'En savoir plus sur : éditeur de boîtes de dialogue (C++)'
title: Éditeur de boîtes de dialogue (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
- vc.editors.dialog
helpviewer_keywords:
- resource editors [C++], Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes [C++], editing
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
- Dialog Editor [C++], shortcut keys
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
ms.openlocfilehash: 547d00208cc2a05814a9820e219cdfc5c7163436
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327159"
---
# <a name="dialog-editor-c"></a>Éditeur de boîtes de dialogue (C++)

L' **éditeur de boîtes de dialogue** vous permet de créer ou de modifier des ressources de boîte de dialogue.

- Pour ouvrir l’éditeur, double-cliquez sur le fichier. RC d’une boîte de dialogue dans la fenêtre **affichage des ressources** ou accédez à menu **Afficher**  >  **autres**  >  **affichage des ressources** Windows.

L’une des premières étapes de création d’un nouveau modèle de boîte de dialogue ou de boîte de dialogue consiste à ajouter des contrôles. Dans l' **éditeur de boîtes de dialogue**, vous pouvez organiser les contrôles en fonction d’une taille, d’une forme ou d’un alignement spécifique, ou vous pouvez les déplacer pour travailler dans la boîte de dialogue. Vous pouvez aussi facilement supprimer un contrôle.

Vous pouvez stocker une boîte de dialogue en tant que modèle pour pouvoir la réutiliser. Vous pouvez aussi facilement basculer entre la conception de la boîte de dialogue et la modification du code qui l'implémente.

Il est également possible de modifier les propriétés d’un ou de plusieurs contrôles dans l' **éditeur de boîtes de dialogue**. Vous pouvez modifier l’ordre de tabulation, c’est-à-dire l’ordre dans lequel les contrôles obtiennent le focus quand la touche **Tab** est enfoncée, ou vous pouvez définir une touche d’accès ou une combinaison de touches qui permet aux utilisateurs de choisir un contrôle à l’aide du clavier.

L' **éditeur de boîtes de dialogue** vous permet également d’utiliser des contrôles personnalisés, y compris des contrôles ActiveX. Vous pouvez également modifier un [mode formulaire](../mfc/reference/cformview-class.md), des [vues d’enregistrement](../data/record-views-mfc-data-access.md)ou des barres de boîte de [dialogue](../mfc/dialog-bars.md).

À compter de Visual Studio 2015, vous pouvez utiliser l' **éditeur de boîtes de dialogue** pour définir des dispositions dynamiques qui spécifient le mode de déplacement et de redimensionnement des contrôles quand l’utilisateur redimensionne une boîte de dialogue. Pour plus d’informations, consultez [Dynamic Layout](../mfc/dynamic-layout.md).

Pour plus d’informations sur les ressources, consultez Guide pratique pour [créer une](../windows/creating-a-new-dialog-box.md) boîte de dialogue et des [contrôles de boîte de dialogue](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Lorsque vous utilisez l' **éditeur de boîtes de dialogue**, dans de nombreux cas, vous pouvez sélectionner avec le bouton droit de la souris pour afficher un menu contextuel des commandes fréquemment utilisées.

## <a name="dialog-editor-toolbar"></a>Barre d'outils de l'Éditeur de boîtes de dialogue

La barre d’outils de l' **éditeur de boîtes de dialogue** contient des boutons permettant de réorganiser la disposition des contrôles dans la boîte de dialogue, par exemple la taille et l’alignement. Les boutons de la barre d’outils de l' **éditeur de boîtes de dialogue** correspondent aux commandes du menu **format** .

|Icône|Signification|Icône|Signification|
|----------|-------------|----------|-------------|
|![Bouton Tester la boîte de dialogue](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Boîte de dialogue Test|![Bouton Espacer horizontalement](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalement|
|![Bouton Aligner les côtés gauches](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Aligner les côtés gauches|![Bouton Espacer verticalement](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Descendre|
|![Bouton Aligner les côtés droits](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Aligner les côtés droits|![Bouton Uniformiser la largeur](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Uniformiser la largeur|
|![Bouton Aligner les sommets](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Aligner les sommets|![Bouton Uniformiser la hauteur](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Uniformiser la hauteur|
|![Bouton Aligner les bases](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Aligner les bases|![Bouton Uniformiser la taille](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Uniformiser la taille|
|![Bouton Centrer verticalement](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Bouton Activer/Désactiver la grille](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Activer/Désactiver la grille|
|![Bouton Centrer horizontalement](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Bouton Activer/Désactiver les repères](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Activer/Désactiver les repères|

- Pour afficher ou masquer la barre d’outils de l' **éditeur de boîtes de dialogue** , accédez à menu **Afficher** les  >  **barres d’outils**  >  **éditeur de boîtes de dialogue**.

Quand vous ouvrez l' **éditeur de boîtes de dialogue** dans un projet C++, la barre d’outils de l' **éditeur de boîtes de dialogue** apparaît automatiquement en haut de votre solution. Toutefois, si vous fermez explicitement la barre d’outils, vous devez l’appeler la prochaine fois que vous ouvrez l’éditeur de boîtes de **dialogue**. Vous pouvez basculer son affichage en le sélectionnant dans la liste des barres d’outils et des fenêtres disponibles.

## <a name="switch-between-dialog-box-controls-and-code"></a>Basculer entre les contrôles de boîte de dialogue et le code

Dans les applications MFC, vous pouvez double-cliquer sur les contrôles de boîte de dialogue pour accéder à leur code de gestionnaire ou créer rapidement des fonctions de gestionnaire stub.

Lorsqu’un contrôle est sélectionné, sélectionnez le bouton **ControlEvents** ou le bouton **Messages** dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour afficher la liste complète des messages et événements Windows disponibles pour l’élément sélectionné. Choisissez dans la liste pour créer ou modifier des fonctions de gestionnaire.

- Pour accéder au code à partir de l' **éditeur de boîtes de dialogue**, double-cliquez sur un contrôle dans la boîte de dialogue pour accéder à la déclaration de sa fonction de gestion des messages implémentée le plus récemment.

   Pour les classes de boîte de dialogue basées sur ATL, vous accédez toujours à la définition du constructeur.

- Pour afficher les événements d’un contrôle, lorsqu’un contrôle est sélectionné, choisissez le bouton **ControlEvents** dans la fenêtre **Propriétés** .

   Quand un contrôle unique a le focus dans la boîte de dialogue, vous pouvez cliquer avec le bouton droit et sélectionner **Ajouter un gestionnaire d’événements**. Cela vous permet de spécifier la classe à laquelle le gestionnaire est ajouté. Pour plus d’informations, consultez [Ajout d’un gestionnaire d’événements](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Le choix du bouton **ControlEvents** lorsque la boîte de dialogue a le focus expose une liste de tous les contrôles dans la boîte de dialogue, que vous pouvez ensuite développer pour modifier les événements pour les contrôles individuels.

- Pour afficher les messages d’une boîte de dialogue, la boîte de dialogue étant sélectionnée, choisissez le bouton **messages** dans la fenêtre **Propriétés** .

## <a name="accelerator-keys"></a>Touches accélérateur

Vous trouverez ci-dessous les touches d’accès rapide par défaut pour les commandes de l' **éditeur de boîtes de dialogue** .  

|Commande|Keys|Description|
|-------------|----------|-----------------|
|Format.AlignBottoms|**CTRL**  +  **MAJ**  +  **Flèche bas**|Aligne les bords inférieurs des contrôles sélectionnés avec le contrôle dominant.|
|Format.AlignCenters|**MAJ**  +  **F9**|Aligne les centres verticaux des contrôles sélectionnés avec le contrôle dominant.|
|Format.AlignLefts|**CTRL**  +  **MAJ**  +  **Flèche gauche**|Aligne les bords gauches des contrôles sélectionnés avec le contrôle dominant.|
|Format.AlignMiddles|**F9**|Aligne les centres horizontaux des contrôles sélectionnés avec le contrôle dominant.|
|Format.AlignRights|**CTRL**  +  **MAJ**  +  **Flèche droite**|Aligne les bords droits des contrôles sélectionnés avec le contrôle dominant.|
|Format.AlignTops|**CTRL**  +  **MAJ**  +  **Flèche haut**|Aligne les bords supérieurs des contrôles sélectionnés avec le contrôle dominant.|
|Format.ButtonBottom|**Ctrl** + **B**|Place les boutons sélectionnés en bas au centre de la boîte de dialogue.|
|Format.ButtonRight|**CTRL**  +  **R**|Place les boutons sélectionnés dans l’angle supérieur droit de la boîte de dialogue.|
|Format.CenterHorizontal|**CTRL**  +  **MAJ**  +  **F9**|Centre les contrôles horizontalement dans la boîte de dialogue.|
|Format.CenterVertical|**CTRL**  +  **F9**|Centre les contrôles verticalement dans la boîte de dialogue.|
|Format.CheckMnemonics|**CTRL**  +  **M**|Vérifie l’unicité des mnémoniques.|
|Format. SizeToContent|**MAJ**  +  **F7**|Redimensionne le ou les contrôles sélectionnés pour qu’ils correspondent au texte de la légende.|
|Format.SpaceAcross|**ALT**  +  **Flèche gauche**|Espace uniformément les contrôles sélectionnés horizontalement.|
|Format.SpaceDown|**ALT**  +  **Flèche bas**|Espace uniformément les contrôles sélectionnés verticalement.|
|Format.TabOrder|**CTRL**  +  **D**|Définit l’ordre des contrôles dans la boîte de dialogue.|
|Format.TestDialog|**CTRL**  +  **T**|Exécute la boîte de dialogue pour tester l’apparence et le comportement.|
|Format.ToggleGuides|**CTRL**  +  **G**|Effectue un cycle entre aucune grille, instruction et grille pour la modification de la boîte de dialogue.|

- Pour modifier les touches de raccourci, accédez à **Outils** de menu  >  **options**, puis choisissez **clavier** dans le dossier **environnement** .

   Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Pour modifier vos paramètres, accédez à **Outils** de menu  >  **Importer et exporter les paramètres**.

   Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans **l’aide** en fonction de vos paramètres actifs ou de l’édition.  Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Comment : créer une boîte de dialogue](../windows/creating-a-new-dialog-box.md)<br/>
[Contrôles de boîte de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/adding-a-member-variable-visual-cpp.md#dialog-box-controls-and-variable-types)-->
