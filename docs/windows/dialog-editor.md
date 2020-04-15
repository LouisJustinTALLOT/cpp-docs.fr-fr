---
title: Rédacteur en chef de Dialog (CMD)
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
ms.openlocfilehash: f1544d3a8e14f9373e21b77d888860d24ab1ed6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370292"
---
# <a name="dialog-editor-c"></a>Rédacteur en chef de Dialog (CMD)

**L’éditeur Dialog** vous permet de créer ou d’éditer des ressources de boîte de dialogue.

- Pour ouvrir l’éditeur, cliquez deux fois sur le fichier .rc d’un dialogue dans la fenêtre **Resource View,** ou rendez-vous au menu **Voir** > **d’autres windows** > **Resource View**.

L’une des premières étapes dans la fabrication d’une nouvelle boîte de dialogue ou de modèle de boîte de dialogue, est l’ajout de contrôles. Dans **l’éditeur De dialogue,** vous pouvez organiser des commandes pour s’adapter à une certaine taille, forme ou alignement, ou vous pouvez les déplacer pour travailler dans la boîte de dialogue. Vous pouvez aussi facilement supprimer un contrôle.

Vous pouvez stocker une boîte de dialogue en tant que modèle pour pouvoir la réutiliser. Vous pouvez aussi facilement basculer entre la conception de la boîte de dialogue et la modification du code qui l'implémente.

Il est également possible d’éditer des propriétés de contrôles simples ou multiples dans **l’éditeur Dialog**. Vous pouvez modifier l’ordre d’onglet, c’est-à-dire l’ordre dans lequel les contrôles se mettent au point lorsque la clé **Tab** est pressée, ou vous pouvez définir une clé d’accès ou une combinaison de clés qui permet aux utilisateurs de choisir un contrôle à l’aide du clavier.

**L’éditeur Dialog** vous permet également d’utiliser des contrôles personnalisés, y compris les contrôles ActiveX. Vous pouvez également modifier une [vue de formulaire,](../mfc/reference/cformview-class.md) [des vues d’enregistrement,](../data/record-views-mfc-data-access.md)ou [des barres de dialogue](../mfc/dialog-bars.md).

En commençant par Visual Studio 2015, vous pouvez utiliser **l’éditeur Dialog** pour définir des mises en page dynamiques, qui spécifient comment les contrôles se déplacent et resize lorsque l’utilisateur resizes un dialogue. Pour plus d’informations, consultez [Dynamic Layout](../mfc/dynamic-layout.md).

Pour plus d’informations sur les ressources, voir comment [créer une boîte de dialogue](../windows/creating-a-new-dialog-box.md) et [dialog Box Controls](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Tout en utilisant **l’éditeur Dialog**, dans de nombreux cas, vous pouvez sélectionner avec le bouton de la souris droite pour afficher un menu raccourci de commandes fréquemment utilisées.

## <a name="dialog-editor-toolbar"></a>Barre d'outils de l'Éditeur de boîtes de dialogue

La barre **d’outils Dialog Editor** contient des boutons pour organiser la disposition des commandes sur la boîte de dialogue, par exemple la taille et l’alignement. Les boutons de barre **d’outils Dialog Editor** correspondent aux commandes du menu **Format.**

|Icône|Signification|Icône|Signification|
|----------|-------------|----------|-------------|
|![Bouton Tester la boîte de dialogue](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Boîte de dialogue Test|![Bouton Espacer horizontalement](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalement|
|![Bouton Aligner les côtés gauches](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Aligner les côtés gauches|![Bouton Espacer verticalement](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Descendre|
|![Bouton Aligner les côtés droits](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Aligner les côtés droits|![Bouton Uniformiser la largeur](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Uniformiser la largeur|
|![Bouton Aligner les sommets](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Aligner les sommets|![Bouton Uniformiser la hauteur](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Uniformiser la hauteur|
|![Bouton Aligner les bases](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Aligner les bases|![Bouton Uniformiser la taille](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Uniformiser la taille|
|![Bouton Centrer verticalement](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Bouton Activer/Désactiver la grille](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Activer/Désactiver la grille|
|![Bouton Centrer horizontalement](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Bouton Activer/Désactiver les repères](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Activer/Désactiver les repères|

- Pour montrer ou cacher la barre d’outils **Dialog Editor,** rendez-vous sur le menu **View** > **Toolbars** > **Dialog Editor**.

Lorsque vous ouvrez **l’éditeur De dialogue** dans un projet C, la barre d’outils **Dialog Editor** apparaît automatiquement en haut de votre solution, cependant, si vous fermez explicitement la barre d’outils, vous devrez l’invoquer la prochaine fois que vous ouvrez l’éditeur **Dialog**. Vous pouvez basculer son affichage en le sélectionnant dans la liste des barres d’outils et fenêtres disponibles.

## <a name="switch-between-dialog-box-controls-and-code"></a>Changement entre les contrôles de boîte de dialogue et le code

Dans les applications MFC, vous pouvez cliquer en double sur les commandes de la boîte de dialogue pour sauter sur leur code de gestionnaire ou pour créer rapidement des fonctions de gestionnaire de talons.

Avec un contrôle sélectionné, sélectionnez le bouton **ControlEvents** ou le bouton **Messages** dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour afficher une liste complète des messages et événements Windows disponibles pour l’élément sélectionné. Choisissez parmi la liste pour créer ou modifier les fonctions de gestionnaire.

- Pour passer au code de **l’éditeur Dialog**, cliquez deux fois sur un contrôle dans la boîte de dialogue pour sauter à la déclaration pour sa fonction de manipulation de message la plus récemment mis en œuvre.

   Pour les cours de dialogue à base d’ATL, vous sautez toujours à la définition du constructeur.

- Pour afficher les événements pour un contrôle, avec un contrôle sélectionné, choisissez le bouton **ControlEvents** dans la fenêtre **Propriétés.**

   Lorsqu’un seul contrôle est focaliste dans la boîte de dialogue, vous pouvez cliquer à droite et sélectionner **Add Event Handler**. Cela vous permet de spécifier la classe à laquelle le gestionnaire est ajouté. Pour plus d’informations, voir [Ajouter un gestionnaire d’événements](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Le choix du bouton **ControlEvents** lorsque la boîte de dialogue est ciblée expose une liste de tous les contrôles de la boîte de dialogue, que vous pouvez ensuite étendre pour modifier les événements pour les contrôles individuels.

- Pour afficher les messages d’une boîte de dialogue, avec la boîte de dialogue sélectionnée, choisissez le bouton **Messages** dans la fenêtre **Propriétés.**

## <a name="accelerator-keys"></a>Touches accélérateur

Vous trouverez ci-dessous les clés d’accélérateur par défaut des commandes **Dialog Editor.**  

|Commande|Keys|Description|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **Shift** + **Down Arrow**|Aligne les bords inférieurs des commandes sélectionnées avec le contrôle dominant.|
|Format.AlignCenters|**Changement** + **F9**|Aligne les centres verticaux des commandes sélectionnées avec le contrôle dominant.|
|Format.AlignLefts|**Ctrl** + **Shift** + **Flèche gauche**|Aligne les bords gauches des commandes sélectionnées avec le contrôle dominant.|
|Format.AlignMiddles|**F9**|Aligne les centres horizontaux des commandes sélectionnées avec le contrôle dominant.|
|Format.AlignRights|**Ctrl** + **Shift** + **Droite Flèche**|Aligne les bords droits des commandes sélectionnées avec le contrôle dominant.|
|Format.AlignTops|**Ctrl** + **Shift** + **Up Arrow**|Aligne les bords supérieurs des commandes sélectionnées avec le contrôle dominant.|
|Format.ButtonBottom|**Ctrl** + **B**|Place les boutons sélectionnés le long du centre inférieur de la boîte de dialogue.|
|Format.ButtonRight|**Ctrl** + **R**|Place les boutons sélectionnés dans le coin supérieur droit de la boîte de dialogue.|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Centre les commandes horizontalement dans la boîte de dialogue.|
|Format.CenterVertical|**Ctrl** + **F9**|Centre les commandes verticalement dans la boîte de dialogue.|
|Format.CheckMnemonics|**Ctrl** + **M**|Vérifie l’unicité des mnémoniques.|
|Format.SizeToContent|**Changement** + **F7**|Resizes the selected control(s) to fit the caption text.|
|Format.SpaceAcross|**Flèche** + **gauche d’Alt**|Espacer uniformément les contrôles sélectionnés horizontalement.|
|Format.SpaceDown|**Flèche Alt** + **Down**|Espacer uniformément les commandes sélectionnées verticalement.|
|Format.TabOrder|**Ctrl** + **D**|Définit l’ordre des contrôles dans le dialogue.|
|Format.TestDialog|**Ctrl** + **T**|Exécute la boîte de dialogue pour tester l’apparence et le comportement.|
|Format.ToggleGuides|**Ctrl** + **G**|Cycles entre aucune grille, lignes directrices et grille pour l’édition de dialogue.|

- Pour changer les touches de raccourci, rendez-vous sur les **options d’outils** > **Options**de menu et choisissez **clavier** sous le dossier **Environnement.**

   Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Pour modifier vos paramètres, rendez-vous sur les paramètres**d’importation et d’exportation d’outils** **Tools** > de menu .

   Les options disponibles dans les boîtes de dialogue, ainsi que les noms et les emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans **Help** en fonction de vos paramètres ou éditions actives.  Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Rédacteurs en ressources](../windows/resource-editors.md)<br/>
[Comment: Créer une boîte de dialogue](../windows/creating-a-new-dialog-box.md)<br/>
[Contrôles de boîte de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
