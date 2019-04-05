---
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
ms.openlocfilehash: dc5a823951e07af96efceec52d2aa23552c2d002
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029484"
---
# <a name="dialog-editor-c"></a>Éditeur de boîtes de dialogue (C++)

Le **boîte de dialogue Éditeur** vous permet de créer ou modifier des ressources de boîte de dialogue.

- Pour ouvrir l’éditeur, double-cliquez sur le fichier .rc d’une boîte de dialogue le **affichage des ressources** fenêtre, ou accédez au menu **vue** > **affichage des ressources**.

Une des premières étapes pour effectuer une nouvelle boîte de dialogue ou d’un modèle de boîte de dialogue, ajoute des contrôles. Dans le **boîte de dialogue Éditeur**, vous pouvez organiser les contrôles pour s’ajuster à une certaine taille, forme ou alignement, ou vous pouvez les déplacer pour travailler dans la boîte de dialogue. Vous pouvez aussi facilement supprimer un contrôle.

Vous pouvez stocker une boîte de dialogue en tant que modèle pour pouvoir la réutiliser. Vous pouvez aussi facilement basculer entre la conception de la boîte de dialogue et la modification du code qui l'implémente.

Il est également possible de modifier les propriétés d’un seul ou plusieurs contrôles dans le **boîte de dialogue Éditeur**. Vous pouvez modifier l’ordre de tabulation, autrement dit, l’ordre dans lequel les contrôles obtiennent focus lorsque la **onglet** touche est enfoncée ou vous pouvez définir une clé d’accès ou la combinaison de touches qui permet aux utilisateurs de choisir un contrôle à l’aide du clavier.

Le **boîte de dialogue Éditeur** vous permet également d’utiliser des contrôles personnalisés, notamment des contrôles ActiveX. Vous pouvez également modifier un [mode formulaire](../mfc/reference/cformview-class.md), [enregistrer des vues](../data/record-views-mfc-data-access.md), ou [barres de boîte de dialogue](../mfc/dialog-bars.md).

À compter de Visual Studio 2015, vous pouvez utiliser la **boîte de dialogue Éditeur** pour définir des dispositions dynamiques qui spécifient comment déplacent des contrôles et redimensionner quand l’utilisateur redimensionne une boîte de dialogue. Pour plus d’informations, consultez [Dynamic Layout](../mfc/dynamic-layout.md).

Pour plus d’informations sur les ressources, consultez Comment [créer une boîte de dialogue](../windows/creating-a-new-dialog-box.md) et [contrôles de boîte de dialogue](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Lors de l’utilisation du **boîte de dialogue Éditeur**, dans de nombreux cas, vous pouvez sélectionner avec le bouton droit de la souris pour afficher un menu contextuel des commandes fréquemment utilisées.

## <a name="dialog-editor-toolbar"></a>Barre d'outils de l'Éditeur de boîtes de dialogue

Le **boîte de dialogue Éditeur** barre d’outils contient des boutons pour organiser la disposition des contrôles dans la boîte de dialogue, par exemple la taille et l’alignement. **Boîte de dialogue Éditeur** des boutons de barre d’outils correspondent à des commandes sur le **Format** menu.

|Icône|Signification|Icône|Signification|
|----------|-------------|----------|-------------|
|![Bouton de boîte de dialogue test](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Boîte de dialogue Test|![Bouton Espacer horizontalement](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalement|
|![Aligner les côtés gauches bouton](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Aligner les côtés gauches|![Bouton Espacer verticalement](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Bas|
|![Aligner le bouton droits](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Aligner les côtés droits|![Bouton de la largeur de marque](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Uniformiser la largeur|
|![Bouton Aligner les sommets](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Aligner les sommets|![Bouton de même hauteur Make](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Uniformiser la hauteur|
|![Bouton Aligner les bases](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Aligner les bases|![Bouton de taille de la même marque](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Uniformiser la taille|
|![Bouton Centrer verticalement](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Bouton de grille bascule](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Activer/Désactiver la grille|
|![Bouton Centrer horizontalement](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Bouton de Guides bascule](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Activer/Désactiver les repères|

- Pour afficher ou masquer la **boîte de dialogue Éditeur** barre d’outils, accédez au menu **vue** > **barres d’outils** > **boîte de dialogue Éditeur**.

Lorsque vous ouvrez le **boîte de dialogue Éditeur** dans un projet C++, le **boîte de dialogue Éditeur** barre d’outils s’affiche automatiquement en haut de votre solution, toutefois, si vous fermez explicitement la barre d’outils, vous devez appeler le prochaine fois que vous ouvrez le **boîte de dialogue Éditeur**. Vous pouvez afficher/masquer ses en le sélectionnant dans la liste des barres d’outils disponibles et windows.

## <a name="switch-between-dialog-box-controls-and-code"></a>Basculer entre les contrôles de boîte de dialogue et le Code

Dans les applications MFC, vous pouvez double-cliquer sur les contrôles de boîte de dialogue pour accéder à leur code de gestionnaire ou pour créer rapidement des fonctions gestionnaires stub.

Avec un contrôle est sélectionné, sélectionnez le **ControlEvents** bouton ou le **Messages** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour afficher une liste complète des messages de Windows et les événements disponible pour l’élément sélectionné. Choisissez dans la liste pour créer ou modifier des fonctions de gestionnaire.

- Pour accéder au code à partir la **boîte de dialogue Éditeur**, double-cliquez sur un contrôle dans la boîte de dialogue pour accéder à la déclaration de son message implémentée en dernier, fonction de gestion.

   Pour les classes de boîte de dialogue ATL, vous passez toujours à la définition du constructeur.

- Pour afficher les événements pour un contrôle, avec un contrôle est sélectionné, choisissez le **ControlEvents** situé dans le **propriétés** fenêtre.

   Quand un seul contrôle a le focus dans la boîte de dialogue, vous pouvez avec le bouton droit et sélectionnez **ajouter un gestionnaire d’événements**. Cela vous permet de spécifier la classe à laquelle le gestionnaire est ajouté. Pour plus d’informations, consultez [Ajout d’un gestionnaire d’événements](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > En choisissant le **ControlEvents** bouton quand la boîte de dialogue a le focus expose une liste de tous les contrôles dans la boîte de dialogue, vous pouvez développer pour modifier les événements pour les contrôles individuels.

- Pour afficher les messages pour une boîte de dialogue avec la boîte de dialogue sélectionnée, choisissez le **Messages** situé dans le **propriétés** fenêtre.

## <a name="accelerator-keys"></a>Touches accélérateur

Voici la valeur par défaut touches accélérateur pour le **boîte de dialogue Éditeur** commandes.  

|Commande|Touches|Description|
|-------------|----------|-----------------|
|Format.AlignBottoms|**CTRL** + **MAJ** + **flèche vers le bas**|Aligne le bas des contrôles sélectionnés sur le contrôle dominant.|
|Format.AlignCenters|**MAJ** + **F9**|Aligne les centres verticaux des contrôles sélectionnés sur le contrôle dominant.|
|Format.AlignLefts|**CTRL** + **MAJ** + **flèche gauche**|Aligne les bords gauche des contrôles sélectionnés sur le contrôle dominant.|
|Format.AlignMiddles|**F9**|Aligne les centres horizontaux des contrôles sélectionnés sur le contrôle dominant.|
|Format.AlignRights|**CTRL** + **MAJ** + **flèche droite**|Aligne les bords droits des contrôles sélectionnés sur le contrôle dominant.|
|Format.AlignTops|**CTRL** + **MAJ** + **flèche vers le haut**|Aligne les bords supérieurs des contrôles sélectionnés sur le contrôle dominant.|
|Format.ButtonBottom|**Ctrl** + **B**|Place les boutons sélectionnés le centre vers le bas de la boîte de dialogue.|
|Format.ButtonRight|**Ctrl** + **R**|Place les boutons sélectionnés dans l’angle supérieur droit de la boîte de dialogue.|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Centre les contrôles horizontalement dans la boîte de dialogue.|
|Format.CenterVertical|**Ctrl** + **F9**|Centre les contrôles verticalement dans la boîte de dialogue.|
|Format.CheckMnemonics|**Ctrl** + **M**|Vérifie l’unicité des mnémoniques.|
|Format.SizeToContent|**MAJ** + **F7**|Redimensionne les contrôles sélectionnés pour s’adapter au texte de légende.|
|Format.SpaceAcross|**Alt** + **Flèche gauche**|Espacer horizontalement les contrôles sélectionnés.|
|Format.SpaceDown|**ALT** + **flèche vers le bas**|Espacer verticalement les contrôles sélectionnés.|
|Format.TabOrder|**Ctrl** + **D**|Définit l’ordre des contrôles dans la boîte de dialogue.|
|Format.TestDialog|**Ctrl** + **T**|Exécute la boîte de dialogue pour tester l’apparence et le comportement.|
|Format.ToggleGuides|**Ctrl** + **G**|Cycles entre aucune grille, des instructions et grille pour la modification de la boîte de dialogue.|

- Pour changer les touches de raccourci, accédez au menu **outils** > **Options**, puis choisissez **clavier** sous le **environnement** dossier.

   Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Pour modifier vos paramètres, accédez au menu **outils** > **importation et exportation de paramètres**.

   Les options disponibles dans les boîtes de dialogue et les noms et les emplacements des commandes de menu vous le voyez, peuvent différer de ce qui est décrit dans **aide** en fonction de vos paramètres actifs ou votre édition.  Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[éditeurs de ressources](../windows/resource-editors.md)<br/>
[Procédure : Créer une boîte de dialogue](../windows/creating-a-new-dialog-box.md)<br/>
[Contrôles de boîte de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->