---
title: 'Procédure : Contrôles de disposition (C++) | Microsoft Docs'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.grouping
- vc.editors.dialog.combo
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: 878b7371dfa77880d68f1001444ed44b84d7240c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037419"
---
# <a name="how-to-layout-controls-c"></a>Procédure : Contrôles de disposition (C++)

Le **boîte de dialogue Éditeur** fournit des outils de disposition qui alignent et dimensionnent un contrôle automatiquement. Pour la plupart des tâches, vous pouvez utiliser la [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Tous les **boîte de dialogue Éditeur** des commandes de barre d’outils sont également disponibles sur le **Format** menu et la plupart ont [touches de raccourci](../windows/accelerator-keys-for-the-dialog-editor.md).

De nombreuses commandes de disposition pour les boîtes de dialogue sont disponibles uniquement lorsque plus d’un contrôle est sélectionné. Vous pouvez sélectionner un ou plusieurs contrôles, et lorsque plus d’un contrôle est sélectionné, le premier que vous sélectionnez est par défaut du contrôle dominant.

L’emplacement, la hauteur et la largeur du contrôle actuel sont affichés dans le coin inférieur droit de la barre d’état. Lorsque la boîte de dialogue est activée, la barre d’état affiche la position de la boîte de dialogue sous la forme dans son ensemble et sa hauteur et sa largeur.

## <a name="arrange-controls"></a>Organiser les contrôles

Vous pouvez organiser les contrôles dans les boîtes de dialogue avec le **boîte de dialogue Éditeur** dans un des trois états différents :

- Avec les repères et marges sur, définissez comme valeur par défaut.

- Avec la grille de disposition sur.

- Sans les fonctionnalités du composant logiciel enfichable ou d’alignement.

Le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) contient des boutons qui contrôlent l’état.

- Pour modifier l’état, sélectionnez l’icône appropriée, ou accédez au menu **Format** > **Guide paramètres**.

Le **Guide paramètres** boîte de dialogue a les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Repères de disposition**|Affiche les paramètres pour les repères de disposition.|
|**Aucun.**|Masque les outils de disposition.|
|**Règles et repères**|Lorsque l’option est activée, les règles sont ajoutées aux outils de mise en page et permet guides à placer dans les règles. Les guides par défaut sont les marges.|
|**Grille**|Crée une grille de disposition. Nouveaux contrôles sont automatiquement alignés sur la grille.|
|**espacement de la grille**|Affiche les paramètres pour l’espacement de la grille en unités de boîte de dialogue (DLU).|
|**Largeur : DLU**|Définit la largeur de la grille de disposition en DLU. Une DLU horizontale correspond à la largeur moyenne de la police de la boîte de dialogue divisée par 4.|
|**Hauteur : DLU**|Définit la hauteur de la grille de disposition dans DLU. Une DLU verticale correspond à la hauteur moyenne de la police de la boîte de dialogue divisée par 8.|

### <a name="guides-and-margins"></a>Repères et marges

Si vous déplacez des contrôles, ajout de contrôles, ou réorganiser une disposition en cours, repères et marges peuvent aider à vous aligner précisément les contrôles dans une boîte de dialogue.

Lorsque vous créez une boîte de dialogue, quatre guides modifiés appelés marges sont fournis et apparaissent sous forme de lignes en pointillés bleues.

- Pour déplacer les marges, faites glisser la marge à la nouvelle position.

- Pour faire disparaître une marge, déplacez la marge à la position zéro.

- Afin de rétablir la marge, placez le pointeur sur la marge position zéro et déplacez la marge à la position.

Les repères s’affichent en bleu traits en pointillés dans la boîte de dialogue affichées dans l’éditeur et les flèches correspondantes dans les règles en haut et sur le côté gauche de la **boîte de dialogue Éditeur**. Les poignées de redimensionnement de contrôles alignent sur les repères lorsque les contrôles sont déplacés et guides s’aligner sur les contrôles si aucun contrôle précédemment aligné sur le guide. Lorsqu’un repère est déplacé, les contrôles qui dépendent, sont également déplacent. Les contrôles alignés sur plusieurs repères sont redimensionnés lorsqu’un des guides est déplacé.

- Pour créer un repère au sein de la règle, sélectionnez une seule fois pour créer un repère, ou double-cliquez sur pour lancer le **Guide paramètres** boîte de dialogue où vous pouvez spécifier les paramètres du guide.

- Pour définir un guide sur la boîte de dialogue, sélectionnez le guide et faites-le glisser vers une nouvelle position ou sélectionnez la flèche dans la règle pour faire glisser le repère associé.

   Les coordonnées du guide sont affichées dans la barre d’état en bas de la fenêtre et dans la règle ou déplacement le pointeur sur la flèche dans la règle pour afficher la position exacte de ce guide.

- Pour supprimer un repère, faites glisser le repère en dehors de la boîte de dialogue, ou faites glisser la flèche correspondante hors de la règle.

Les graduations dans les règles qui déterminent l’espacement des guides et des contrôles sont définies par les unités de boîte de dialogue (DLU). Une DLU est basée sur la taille de la police de la boîte de dialogue, normalement 8 points MS Shell Dlg. Une DLU horizontale est la largeur moyenne de la police de la boîte de dialogue divisée en quatre parties. Une DLU verticale est la hauteur moyenne de la police divisée par 8.

- Pour modifier les intervalles entre les graduations, accédez au menu **Format** > **Guide paramètres**, puis dans le **espacement de la grille** champ, spécifiez une nouvelle largeur et hauteur DLU.

### <a name="layout-grid"></a>Grille de disposition

Lorsque vous placez ou réorganiser les contrôles dans une boîte de dialogue, utilisez la grille de disposition pour un positionnement plus précis. Lorsque la grille est activée, les contrôles seront aligne sur les lignes en pointillés de la grille comme si elle était aimantée.

- Pour activer ou désactiver les la grille de disposition, accédez au menu **Format** > **Guide paramètres** et activez ou désactivez le **grille** bouton.

   Vous pouvez toujours contrôler la grille de la personne **boîte de dialogue Éditeur** windows à l’aide de la **bascule grille** bouton sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

- Pour modifier la taille de la grille de disposition, accédez au menu **Format** > **Guide paramètres** et tapez la hauteur et largeur dans DLU pour les cellules dans la grille. La largeur ou hauteur minimale est de 4.

### <a name="disable-guides"></a>Désactiver les repères

Vous pouvez utiliser les touches spéciales conjointement avec la souris pour désactiver l’alignement sur les guides. À l’aide de la **Alt** clé désactive les effets d’alignement du guide sélectionnée. Déplacement d’un repère avec le **MAJ** clé empêche le déplacement avec le guide de contrôles alignés.

- Pour désactiver l’alignement sur les repères, faites glisser le contrôle tout en maintenant enfoncée la **Alt** clé.

- Pour déplacer des repères sans déplacer les contrôles alignés, faites glisser le repère tout en maintenant enfoncée la **MAJ** clé.

- Pour désactiver les repères, accédez au menu **Format** > **Guide paramètres**. Ensuite, sous **repères de disposition**, sélectionnez **aucun**.

   > [!TIP]
   > Vous pouvez également utiliser le raccourci dans le menu **Format** > **activer/désactiver les repères**.

## <a name="select-controls"></a>Sélectionner des contrôles

Sélectionner des contrôles à la taille, aligner, déplacer, copier, ou supprimez-les, puis terminez l’opération que vous souhaitez. Dans la plupart des cas, vous devez sélectionner plusieurs contrôles à utiliser les outils de dimensionnement et d’alignement sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Lorsqu’un contrôle est sélectionné, il a une bordure ombrée autour avec solide (actif) ou vides (inactives) poignées, carrés de petites taille qui s’affichent dans la bordure de sélection de redimensionnement. Lorsque plusieurs contrôles sont sélectionnés, le contrôle dominant doté de poignées de redimensionnement solide et tous les autres contrôles sélectionnés ont des poignées de redimensionnement creux.

- Pour sélectionner des contrôles, dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox), sélectionnez le **pointeur** outil et utilisez une des étapes suivantes pour effectuer votre sélection :

  - Faites glisser le pointeur pour dessiner une zone de sélection autour des contrôles que vous souhaitez sélectionner dans votre boîte de dialogue. Lorsque vous relâchez le bouton de la souris, tous les contrôles à l’intérieur ou à l’intersection de la zone de sélection sont sélectionnés.

  - Maintenez la **MAJ** la clé, sélectionnez les contrôles que vous souhaitez inclure dans la sélection.

  - Maintenez la **Ctrl** la clé, sélectionnez les contrôles que vous souhaitez inclure dans la sélection.

- Pour ajouter ou supprimer un contrôle du groupe de contrôles sélectionnés, maintenez la **MAJ** la clé, sélectionnez le contrôle que vous souhaitez ajouter ou supprimer.

### <a name="dominant-controls"></a>Contrôles dominants

Lorsque vous êtes de dimensionnement ou aligner plusieurs contrôles, la **boîte de dialogue Éditeur** utilise le contrôle dominant pour déterminer comment les autres contrôles sont dimensionnés ou alignés. Par défaut, le contrôle dominant est le premier contrôle sélectionné.

- Pour spécifier le contrôle dominant, maintenez la **Ctrl** la clé, sélectionnez le contrôle que vous souhaitez utiliser pour influencer la taille ou l’emplacement d’autres contrôles *premier*. Maintenez la **Ctrl** clé et la sélection d’un contrôle au sein d’une sélection fera également qui contrôlent le contrôle dominant dans cette sélection.

- Pour modifier le contrôle dominant, effacer la sélection actuelle en la sélectionnant à l’extérieur de tous les contrôles actuellement sélectionnés et répétez la procédure ci-dessus, en sélectionnant un autre contrôle *premier*.

> [!NOTE]
> Les poignées de redimensionnement du contrôle dominant sont pleines tandis que celles des contrôles secondaires sont vides. Le dimensionnement ou l’alignement est basé sur le contrôle dominant.

## <a name="size-controls"></a>Contrôles de taille

Utilisez les poignées de redimensionnement pour redimensionner un contrôle. Lorsque le pointeur est positionné sur une poignée de redimensionnement, il change de forme pour indiquer les sens dans lequel le contrôle peut être redimensionné. Poignées de redimensionnement active sont correctes et si une poignée de redimensionnement est vide, le contrôle ne peut pas être redimensionné le long de cet axe.

- Pour dimensionner un contrôle, sélectionnez le contrôle et faites glisser les poignées de redimensionnement pour modifier la taille.

  - Taille des handles en haut et côtés modifier la taille horizontale ou verticale.

  - Handles de taille dans les angles modifier la taille horizontale et verticale.

   > [!TIP]
   > Vous pouvez redimensionner le contrôle d’unité une boîte de dialogue (DLU) à la fois en maintenant enfoncée la **MAJ** enfoncée et en utilisant le **droite** et **vers le bas** touches de direction.

- Pour dimensionner automatiquement un contrôle pour s’adapter au texte qu’il contient, accédez au menu **Format** ou cliquez sur le contrôle, puis choisissez **ajuster au contenu**.

- Pour rendre les contrôles de la même taille, sélectionnez les contrôles que vous souhaitez redimensionner et accédez au menu **Format** > **Uniformiser la taille**, puis choisissez **à la fois**, **Hauteur**, ou **largeur**.

   Vous redimensionnez un groupe de contrôles en fonction de la taille du contrôle dominant, qui est le contrôle sélectionné en premier dans la série. La taille finale des contrôles dans le groupe dépend de la taille du contrôle dominant.

- Taille d’un groupe de contrôles avec des guides, à un repère d’alignement côté « un » de contrôle (ou des contrôles), puis faites glisser un guide pour l’autre côté du contrôle (ou des contrôles). Vous pouvez maintenant passer des repères de dimensionner le contrôle (ou les contrôles).

   Si nécessaire, avec plusieurs contrôles, taille de chacun d’eux à s’aligner sur le second guide.

### <a name="other-controls"></a>Autres contrôles

Vous pouvez dimensionner une zone de liste déroulante lorsque vous l’ajoutez à la boîte de dialogue. Vous pouvez également spécifier la taille de la zone de liste déroulante. Pour plus d’informations, consultez [Ajout de valeurs à un contrôle Combo Box](../windows/adding-values-to-a-combo-box-control.md).

1. Sélectionnez le bouton de flèche de déroulement à droite de la zone de liste déroulante.

   ![Flèche sur une zone de liste déroulante dans un projet MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Le contour du contrôle change pour afficher la taille de la zone de liste déroulante avec la zone de liste déroulante étendue.

1. Utilisez la poignée de redimensionnement inférieure pour modifier la taille initiale de la zone de liste déroulante.

   ![Liste déroulante&#45;redimensionnement de la zone dans un projet MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Sélectionnez la flèche déroulante à nouveau pour fermer la partie de la liste déroulante de la zone de liste déroulante.

> [!NOTE]
> Lorsque vous ajoutez une zone de liste avec une barre de défilement horizontale à une boîte de dialogue à l’aide de MFC, la barre de défilement ne s’affichent automatiquement dans votre application.
>
> Définissez une largeur maximale pour l’élément le plus large en appelant [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) dans votre code. Sans cette valeur est définie, la barre de défilement ne s’affichent, même lorsque les éléments dans la zone de liste sont plus larges que la zone.

## <a name="align-controls"></a>Aligner les contrôles

- Pour aligner des contrôles, sélectionnez les contrôles que vous souhaitez aligner. Accédez au menu **Format** > **Align** et choisissez une des alignements suivants :

   |Alignement|Description|
   |-----|-----------|
   |**Côtés gauches**|Aligne les contrôles sélectionnés sur leurs côtés gauches.|
   |**Centres**|Aligne les contrôles sélectionnés sur leur centre horizontalement.|
   |**Droits**|Aligne les contrôles sélectionnés sur leurs côtés.|
   |**ToPS**|Aligne les contrôles sélectionnés sur leurs bords supérieurs.|
   |**Milieux**|Aligne les contrôles sélectionnés verticalement sur leur milieu.|
   |**Bases**|Aligne les contrôles sélectionnés sur le bord inférieur.|

   Veillez à sélectionner le contrôle que vous souhaitez être tout d’abord dominant ou définissez-le comme contrôle dominant avant d’exécuter l’alignement ou de dimensionnement de commande comme la position finale du groupe de contrôles dépend de la position du contrôle dominant.

- À uniformément les contrôles d’espace, sélectionnez les contrôles que vous souhaitez réorganiser. Accédez au menu **Format** > **Espace uniformément** et choisissez une des espacements suivants :

   |Espacement|Description|
   |---|---|
   |**Horizontalement**|Contrôles d’espace uniformément entre le plus à gauche et le plus à droite contrôle sélectionné.|
   |**Bas**|Contrôles d’espace uniformément entre le premier et le plus bas contrôle sélectionné.|

- Pour centrer les contrôles, sélectionnez l’ou les contrôles que vous souhaitez réorganiser. Accédez au menu **Format** > **Centrer dans la boîte de dialogue** et choisissez une des options suivantes :

   |Disposition|Description|
   |---|---|
   |**Vertical**|Centrer les contrôles verticalement dans la boîte de dialogue.|
   |**Horizontal**|Centrer les contrôles horizontalement dans la boîte de dialogue.|

- Pour aligner les boutons de commande, sélectionnez un ou plusieurs boutons de commande. Accédez au menu **Format** > **réorganiser les boutons**, puis choisissez une des options suivantes :

   |Disposition|Description|
   |---|---|
   |**Droit**|Aligne le bord droit de la boîte de dialogue de boutons.|
   |**Bas**|Aligne le bord inférieur de la boîte de dialogue de boutons.|

   Si vous sélectionnez un contrôle autre qu’un bouton de commande, sa position n’est pas affectée.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Gérer les contrôles de boîte de dialogue](controls-in-dialog-boxes.md)<br/>
[Procédure : Ajouter, modifier, ou supprimer des contrôles](adding-editing-or-deleting-controls.md)<br/>
[Procédure : Définir les valeurs et contrôler l’accès](defining-mnemonics-access-keys.md)<br/>