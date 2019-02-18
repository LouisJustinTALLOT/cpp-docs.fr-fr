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
ms.openlocfilehash: fef4a7f0d4c785a40ea946127d8e3c84c797e1aa
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336694"
---
# <a name="dialog-editor-c"></a>Éditeur de boîtes de dialogue (C++)

Le **boîte de dialogue** éditeur vous permet de créer ou modifier des ressources de boîte de dialogue. Vous ouvrez l’éditeur de boîtes de dialogue en double-cliquant sur le fichier .rc d’une boîte de dialogue le **affichage des ressources** fenêtre (**vue** > **affichage des ressources**). Notez que **affichage des ressources** n’est pas disponible dans les éditions Express.

L'une des premières étapes de la création d'une boîte de dialogue (ou d'un modèle de boîte de dialogue) consiste à ajouter des contrôles à la boîte de dialogue. Dans le **boîte de dialogue** éditeur, vous pouvez organiser les contrôles pour s’ajuster à une certaine taille, forme ou alignement, ou vous pouvez les déplacer pour travailler dans la boîte de dialogue. Vous pouvez aussi facilement supprimer un contrôle.

Vous pouvez stocker une boîte de dialogue en tant que modèle pour pouvoir la réutiliser. Vous pouvez aussi facilement basculer entre la conception de la boîte de dialogue et la modification du code qui l'implémente.

Il est également possible de modifier les propriétés d'un ou plusieurs contrôles dans l'Éditeur de boîtes de dialogue. Vous pouvez modifier l’ordre de tabulation, autrement dit, l’ordre dans lequel les contrôles obtiennent focus lorsque la **onglet** touche est enfoncée ou vous pouvez définir une clé d’accès (une combinaison de touches) qui permet aux utilisateurs de choisir un contrôle à l’aide du clavier.

Le **boîte de dialogue** éditeur vous permet également d’utiliser des contrôles personnalisés, notamment des contrôles ActiveX. En outre, vous pouvez modifier un [mode formulaire](../mfc/reference/cformview-class.md), des [vues d'enregistrements](../data/record-views-mfc-data-access.md)ou des [barres de boîte de dialogue](../mfc/dialog-bars.md).

À compter de Visual Studio 2015, vous pouvez utiliser l’éditeur de boîtes de dialogue pour définir des dispositions dynamiques qui spécifient comment les contrôles déplacent et redimensionnent lorsque l’utilisateur redimensionne une boîte de dialogue. Pour plus d’informations, consultez [Dynamic Layout](../mfc/dynamic-layout.md).

- [Guide pratique pour Créer une boîte de dialogue](../windows/creating-a-new-dialog-box.md)

- [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)

   > [!TIP]
   > Lors de l’utilisation du **boîte de dialogue** éditeur, dans de nombreux cas, vous pouvez sélectionner le bouton droit de la souris pour afficher un menu contextuel des commandes fréquemment utilisées.

## <a name="dialog-editor-toolbar"></a>Barre d'outils de l'Éditeur de boîtes de dialogue

Lorsque vous ouvrez le **boîte de dialogue** éditeur dans un projet C++, le **boîte de dialogue Éditeur** barre d’outils s’affiche automatiquement en haut de votre solution.

|Icône|Signification|Icône|Signification|
|----------|-------------|----------|-------------|
|![Bouton de boîte de dialogue test](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Boîte de dialogue Test|![Bouton Espacer horizontalement](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalement|
|![Aligner les côtés gauches bouton](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Aligner les côtés gauches|![Bouton Espacer verticalement](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Bas|
|![Aligner le bouton droits](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Aligner les côtés droits|![Bouton de la largeur de marque](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Uniformiser la largeur|
|![Bouton Aligner les sommets](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Aligner les sommets|![Bouton de même hauteur Make](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Uniformiser la hauteur|
|![Bouton Aligner les bases](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Aligner les bases|![Bouton de taille de la même marque](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Uniformiser la taille|
|![Bouton Centrer verticalement](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Bouton de grille bascule](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Activer/Désactiver la grille|
|![Bouton Centrer horizontalement](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Bouton de Guides bascule](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Activer/Désactiver les repères|

Le **boîte de dialogue Éditeur** barre d’outils contient des boutons pour organiser la disposition des contrôles dans la boîte de dialogue, par exemple la taille et l’alignement. **Boîte de dialogue Éditeur** des boutons de barre d’outils correspondent à des commandes sur le **Format** menu.

Lorsque vous êtes dans le **boîte de dialogue** éditeur, vous pouvez afficher ou masquer les le **boîte de dialogue Éditeur** la barre d’outils en le sélectionnant dans la liste des barres d’outils disponibles et windows.

- Pour afficher ou masquer la barre d’outils de l’éditeur de boîte de dialogue, sur le **vue** menu, sélectionnez **barres d’outils**, puis choisissez **boîte de dialogue Éditeur** dans le sous-menu.

   > [!NOTE]
   > Le **boîte de dialogue Éditeur** barre d’outils s’affiche par défaut lorsque vous ouvrez une ressource de boîte de dialogue dans l’éditeur de boîtes de dialogue ; Toutefois, si vous fermez explicitement la barre d’outils, vous devez appeler la prochaine fois que vous ouvrez une ressource de boîte de dialogue.

## <a name="switch-between-dialog-box-controls-and-code"></a>Basculer entre les contrôles de boîte de dialogue et le Code

Dans les applications MFC, vous pouvez double-cliquer sur les contrôles de boîte de dialogue pour accéder à leur code de gestionnaire ou pour créer rapidement des fonctions gestionnaires stub.

Avec un contrôle est sélectionné, cliquez sur le **ControlEvents** bouton ou le **Messages** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour afficher une liste complète des messages de Windows et les événements disponible pour l’élément sélectionné. Choisissez dans la liste pour créer ou modifier des fonctions de gestionnaire.

- Pour accéder au code à partir de l’éditeur de boîtes de dialogue, double-cliquez sur un contrôle dans la boîte de dialogue pour accéder à la déclaration de son message implémentée en dernier, fonction de gestion. (Pour les classes de boîte de dialogue ATL, vous passez toujours à la définition du constructeur.)

- Pour afficher les événements pour un contrôle, avec un contrôle est sélectionné, choisissez le **ControlEvents** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

   > [!NOTE]
   > En choisissant le **ControlEvents** bouton lorsque le *boîte de dialogue* a le focus expose une liste de tous les contrôles dans la boîte de dialogue, vous pouvez développer pour modifier les événements pour les contrôles individuels.

   Quand un seul contrôle a le focus dans la boîte de dialogue, vous pouvez faites un clic droit et sélectionnez **ajouter un gestionnaire d’événements** dans le menu contextuel. Cela vous permet de spécifier la classe à laquelle le gestionnaire est ajouté. Pour plus d’informations, consultez [Ajout d’un gestionnaire d’événements](../ide/adding-an-event-handler-visual-cpp.md).

- Pour afficher les messages pour une boîte de dialogue avec la boîte de dialogue sélectionnée, choisissez le **Messages** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

## <a name="accelerator-keys"></a>Touches accélérateur

Voici la valeur par défaut touches accélérateur pour les commandes de l’éditeur de boîte de dialogue. Pour changer les touches de raccourci, sélectionnez **Options** sur le **outils** menu, puis choisissez **clavier** sous le **environnement** dossier. Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Commande|Touches|Description|
|-------------|----------|-----------------|
|Format.AlignBottoms|**CTRL** + **MAJ** + **flèche vers le bas**|Aligne les bords inférieurs des contrôles sélectionnés sur le contrôle dominant|
|Format.AlignCenters|**MAJ** + **F9**|Aligne les centres verticaux des contrôles sélectionnés sur le contrôle dominant|
|Format.AlignLefts|**CTRL** + **MAJ** + **flèche gauche**|Aligner le bord gauche des contrôles sélectionnés sur le contrôle dominant|
|Format.AlignMiddles|**F9**|Aligne les centres horizontaux des contrôles sélectionnés sur le contrôle dominant|
|Format.AlignRights|**CTRL** + **MAJ** + **flèche droite**|Aligne les bords droits des contrôles sélectionnés sur le contrôle dominant|
|Format.AlignTops|**CTRL** + **MAJ** + **flèche vers le haut**|Aligne les bords supérieurs des contrôles sélectionnés sur le contrôle dominant|
|Format.ButtonBottom|**Ctrl** + **B**|Place les boutons sélectionnés le centre vers le bas de la boîte de dialogue|
|Format.ButtonRight|**Ctrl** + **R**|Place les boutons sélectionnés dans l’angle supérieur droit de la boîte de dialogue|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Centre les contrôles horizontalement dans la boîte de dialogue|
|Format.CenterVertical|**Ctrl** + **F9**|Centre les contrôles verticalement dans la boîte de dialogue|
|Format.CheckMnemonics|**Ctrl** + **M**|Unicité des vérifications de mnémoniques|
|Format.SizeToContent|**MAJ** + **F7**|Redimensionne les contrôles sélectionnés pour s’adapter au texte de légende|
|Format.SpaceAcross|**Alt** + **Flèche gauche**|Espacer horizontalement les contrôles sélectionnés|
|Format.SpaceDown|**ALT** + **flèche vers le bas**|Espacer verticalement les contrôles sélectionnés|
|Format.TabOrder|**Ctrl** + **D**|Définit l’ordre des contrôles dans la boîte de dialogue|
|Format.TestDialog|**Ctrl** + **T**|Exécute la boîte de dialogue pour tester l’apparence et le comportement|
|Format.ToggleGuides|**Ctrl** + **G**|Cycles entre aucune grille, des instructions et grille pour la modification de la boîte de dialogue|

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Guide pratique pour créer une ressource](../windows/how-to-create-a-resource.md)<br/>
[Contrôles](../mfc/controls-mfc.md)<br/>
[Classes de contrôle](../mfc/control-classes.md)<br/>
[Classes de boîte de dialogue](../mfc/dialog-box-classes.md)<br/>
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)