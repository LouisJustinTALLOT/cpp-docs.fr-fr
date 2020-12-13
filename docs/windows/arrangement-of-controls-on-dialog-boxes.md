---
description: 'En savoir plus sur : Comment : mettre en page des contrôles (C++)'
title: 'Comment : mettre en page des contrôles (C++) | Microsoft Docs'
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
ms.openlocfilehash: 75fef5d47df163e1b21b9dd2861ec652179d9eb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337832"
---
# <a name="how-to-layout-controls-c"></a>Comment : mettre en page des contrôles (C++)

L' **éditeur de boîtes de dialogue** fournit des outils de disposition qui alignent et dimensionnent automatiquement les contrôles. Pour la plupart des tâches, vous pouvez utiliser la [barre d’outils](./dialog-editor.md)de l’éditeur de boîtes de dialogue. Toutes les commandes de la barre d’outils de l' **éditeur de boîtes de dialogue** sont également disponibles dans le menu **format** , et la plupart ont des [touches de raccourci](./dialog-editor.md).

De nombreuses commandes de disposition pour les boîtes de dialogue sont disponibles uniquement lorsque plusieurs contrôles sont sélectionnés. Vous pouvez sélectionner un ou plusieurs contrôles, et lorsque plusieurs contrôles sont sélectionnés, le premier contrôle sélectionné est par défaut le contrôle dominant.

L’emplacement, la hauteur et la largeur du contrôle actuel s’affichent dans l’angle inférieur droit de la barre d’État. Lorsque la boîte de dialogue entière est sélectionnée, la barre d’état affiche la position de la boîte de dialogue dans son ensemble, ainsi que sa hauteur et sa largeur.

## <a name="arrange-controls"></a>organiser les contrôles

Vous pouvez organiser les contrôles des boîtes de dialogue avec l' **éditeur de boîtes de dialogue** dans l’un des trois États suivants :

- Avec les repères et les marges sur, définissez par défaut.

- Avec la grille de disposition sur.

- Sans fonctions d’alignement ou d’alignement.

La [barre d’outils](./dialog-editor.md) de l’éditeur de boîtes de dialogue contient des boutons qui contrôlent l’État.

- Pour modifier l’État, sélectionnez l’icône appropriée ou accédez à menu paramètres du Guide de **format**  >  .

La boîte de dialogue **paramètres du repère** a les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Repères de mise en page**|Affiche les paramètres des repères de mise en page.|
|**Aucun**|Masque les outils de disposition.|
|**Règles et repères**|Lorsque cette option est activée, ajoute des règles aux outils de disposition et permet de placer les repères dans les règles. Les repères par défaut sont les marges.|
|**Grid**|Crée une grille de disposition. Les nouveaux contrôles s’alignent automatiquement sur la grille.|
|**espacement de la grille**|Affiche les paramètres de l’espacement de la grille en unités de boîte de dialogue (DLU).|
|**Largeur : dlu**|Définit la largeur de la grille de disposition dans des unités de configuration. Un DLU horizontal est la largeur moyenne de la police de la boîte de dialogue divisée par 4.|
|**Hauteur : dlu**|Définit la hauteur de la grille de disposition dans des unités de configuration. Une DLU verticale est la hauteur moyenne de la police de la boîte de dialogue divisée par 8.|

### <a name="guides-and-margins"></a>Repères et marges

Que vous déplaciez des contrôles, ajoutiez des contrôles ou réorganisiez une disposition actuelle, les repères et les marges peuvent vous aider à aligner les contrôles avec précision dans une boîte de dialogue.

Lorsque vous créez une boîte de dialogue, quatre repères modifiés appelés marges sont fournis et apparaissent sous forme de lignes en pointillés bleus.

- Pour déplacer des marges, faites glisser la marge vers la nouvelle position.

- Pour faire disparaître une marge, déplacez la marge vers la position zéro.

- Pour rétablir la marge, placez le pointeur sur la position zéro de la marge et déplacez la marge dans la position.

Les repères apparaissent sous forme de lignes en pointillés bleus dans la boîte de dialogue affichée dans l’éditeur et les flèches correspondantes dans les règles situées en haut et sur le côté gauche de l' **éditeur de boîtes de dialogue**. Les poignées de dimensionnement des contrôles s’alignent sur des repères lorsque les contrôles sont déplacés, et les repères sont alignés sur les contrôles si aucun contrôle n’a été précédemment aligné sur le repère. Quand un repère est déplacé, les contrôles qui y sont alignés se déplacent également. Les contrôles alignés sur plusieurs guides sont redimensionnés lorsque l’un des repères est déplacé.

- Pour créer un repère dans la règle, sélectionnez une fois pour créer un repère, ou double-cliquez pour ouvrir la boîte de dialogue **paramètres du repère** dans laquelle vous pouvez spécifier les paramètres du repère.

- Pour définir un repère sur la boîte de dialogue, sélectionnez le repère et faites-le glisser vers une nouvelle position, ou sélectionnez la flèche dans la règle pour faire glisser le repère associé.

   Les coordonnées du repère s’affichent dans la barre d’État en bas de la fenêtre et dans la règle ou déplacent le pointeur sur la flèche dans la règle pour afficher la position exacte du repère.

- Pour supprimer un repère, faites-le glisser hors de la boîte de dialogue ou faites glisser la flèche correspondante en dehors de la règle.

Les graduations des règles qui déterminent l’espacement des repères et des contrôles sont définies par les unités de boîte de dialogue (DLU). Un DLU est basé sur la taille de la police de la boîte de dialogue, en général 8 points MS Shell Dlg. Un DLU horizontal est la largeur moyenne de la police de la boîte de dialogue divisée par quatre. Une DLU verticale est la hauteur moyenne de la police divisée par 8.

- Pour modifier l’intervalle des graduations, accédez à menu paramètres du Guide de **format**  >  , puis, dans le champ **espacement** de la grille, spécifiez une nouvelle largeur et une nouvelle hauteur dans la variable dlu.

### <a name="layout-grid"></a>Grille de disposition

Lorsque vous placez ou réorganisez des contrôles dans une boîte de dialogue, utilisez la grille de disposition pour un positionnement plus précis. Lorsque la grille est activée, les contrôles s’alignent sur les lignes en pointillés de la grille comme si elles étaient magnétisées.

- Pour activer ou désactiver la grille de disposition, accédez à menu **format**  >  **paramètres du repère** , puis activez ou désactivez la case à cocher **grille** .

   Vous pouvez toujours contrôler la grille dans les fenêtres de l' **éditeur de boîtes de dialogue** individuelles à l’aide du bouton Activer la **grille** de la [barre d’outils](./dialog-editor.md)de l’éditeur de boîtes de dialogue.

- Pour modifier la taille de la grille de disposition, accédez à menu **format**  >  **paramètres du repère** et tapez la hauteur et la largeur des cellules de la grille. La hauteur ou la largeur minimale est 4.

### <a name="disable-guides"></a>Désactiver les repères

Vous pouvez utiliser des touches spéciales conjointement avec la souris pour désactiver l’effet d’alignement des repères. L’utilisation de la touche **ALT** désactive les effets d’alignement du repère sélectionné. En déplaçant un repère avec la touche **MAJ** , vous empêchez les contrôles alignés de se déplacer avec le repère.

- Pour désactiver l’effet d’alignement des repères, faites-le glisser tout en maintenant la touche **ALT** enfoncée.

- Pour déplacer des repères sans déplacer les contrôles alignés, faites glisser le repère tout en maintenant la touche **MAJ** enfoncée.

- Pour désactiver les repères, accédez à menu **format**  >  **paramètres du guide**. Ensuite, sous **repères de mise en page**, sélectionnez **aucun**.

   > [!TIP]
   > Vous pouvez également utiliser le raccourci dans le menu **mise en forme** des  >  **repères**.

## <a name="select-controls"></a>Sélectionner des contrôles

Sélectionnez des contrôles pour les dimensionner, les aligner, les déplacer, les copier ou les supprimer, puis terminez l’opération souhaitée. Dans la plupart des cas, vous devez sélectionner plusieurs contrôles pour utiliser les outils de dimensionnement et d’alignement sur la [barre d’outils](./dialog-editor.md)de l’éditeur de boîtes de dialogue.

Lorsqu’un contrôle est sélectionné, il est entouré d’une bordure grise avec des poignées de redimensionnement Unies (actives) ou vides (inactives), de petits carrés qui apparaissent dans la bordure de sélection. Lorsque plusieurs contrôles sont sélectionnés, le contrôle dominant a des poignées de redimensionnement solides et tous les autres contrôles sélectionnés ont des poignées de dimensionnement creuses.

- Pour sélectionner des contrôles, dans la [fenêtre boîte à outils](/visualstudio/ide/reference/toolbox), sélectionnez l’outil **pointeur** et utilisez l’une des étapes suivantes pour effectuer votre sélection :

  - Faites glisser le pointeur pour dessiner une zone de sélection autour des contrôles que vous souhaitez sélectionner dans votre boîte de dialogue. Lorsque vous relâchez le bouton de la souris, tous les contrôles à l’intérieur et à l’intersection de la zone de sélection sont sélectionnés.

  - Maintenez la touche **MAJ** enfoncée et sélectionnez les contrôles que vous souhaitez inclure dans la sélection.

  - Maintenez la touche **CTRL** enfoncée et sélectionnez les contrôles que vous souhaitez inclure dans la sélection.

- Pour ajouter ou supprimer un contrôle du groupe de contrôles sélectionnés, maintenez la touche **MAJ** enfoncée et sélectionnez le contrôle que vous souhaitez ajouter ou supprimer.

### <a name="dominant-controls"></a>Contrôles dominant

Lorsque vous dimensionnez ou Alignez plusieurs contrôles, l' **éditeur de boîtes de dialogue** utilise le contrôle dominant pour déterminer comment les autres contrôles sont dimensionnés ou alignés. Par défaut, le contrôle dominant est le premier contrôle sélectionné.

- Pour spécifier le contrôle dominant, maintenez la touche **CTRL** enfoncée et sélectionnez le contrôle que vous souhaitez utiliser pour influencer d' *abord* la taille ou l’emplacement des autres contrôles. Si vous maintenez la touche **CTRL** enfoncée et que vous sélectionnez un contrôle dans une sélection, cela permet également de contrôler le contrôle dominant dans cette sélection.

- Pour modifier le contrôle dominant, effacez la sélection actuelle en sélectionnant l’extérieur de tous les contrôles actuellement sélectionnés et répétez la procédure ci-dessus, en sélectionnant d' *abord* un autre contrôle.

> [!NOTE]
> Les poignées de redimensionnement du contrôle dominant sont solides, tandis que les poignées des contrôles subordonnés sont vides. Tout redimensionnement ou alignement supplémentaire est basé sur le contrôle dominant.

## <a name="size-controls"></a>Contrôles de taille

Utilisez les poignées de redimensionnement pour redimensionner un contrôle. Lorsque le pointeur est positionné sur une poignée de dimensionnement, il change de forme pour indiquer les directions dans lesquelles le contrôle peut être redimensionné. Les poignées de dimensionnement actives sont solides et si une poignée de redimensionnement est vide, le contrôle ne peut pas être redimensionné sur cet axe.

- Pour dimensionner un contrôle, sélectionnez le contrôle, puis faites glisser les poignées de redimensionnement pour modifier la taille.

  - Les poignées de taille situées en haut et les côtés modifient la taille horizontale ou verticale.

  - Les poignées de taille au niveau des angles modifient à la fois les tailles horizontale et verticale.

   > [!TIP]
   > Vous pouvez redimensionner le contrôle d’une unité de boîte de dialogue (DLU) à la fois en maintenant la touche **MAJ** enfoncée et en utilisant les touches de direction **droite** et **bas** .

- Pour dimensionner automatiquement un contrôle en fonction du texte qu’il contient, accédez à menu **format** ou cliquez avec le bouton droit sur le contrôle, puis choisissez **taille du contenu**.

- Pour que les contrôles aient la même taille, sélectionnez les contrôles que vous souhaitez redimensionner et accédez à **format** de menu  >  , définissez la **même taille**, puis sélectionnez **les deux**, la **hauteur** ou la **largeur**.

   Vous redimensionnez un groupe de contrôles en fonction de la taille du contrôle dominant, qui est le contrôle sélectionné en premier dans la série. La taille finale des contrôles dans le groupe dépend de la taille du contrôle dominant.

- Pour dimensionner un groupe de contrôles avec des repères, vous pouvez aligner un côté du contrôle (ou des contrôles) sur un repère, puis faire glisser un repère de l’autre côté du contrôle (ou des contrôles). Vous pouvez maintenant déplacer l’un ou l’autre guide pour dimensionner le contrôle (ou les contrôles).

   Si nécessaire avec plusieurs contrôles, redimensionnez-les pour les aligner sur le deuxième repère.

### <a name="other-controls"></a>Autres contrôles

Vous pouvez dimensionner une zone de liste déroulante lorsque vous l’ajoutez à la boîte de dialogue. Vous pouvez également spécifier la taille de la zone de liste déroulante. Pour plus d’informations, consultez [Ajout de valeurs à un contrôle de zone de liste déroulante](./defining-mnemonics-access-keys.md).

1. Sélectionnez le bouton de la flèche déroulante à droite de la zone de liste déroulante.

   ![Flèche d'un contrôle zone de liste déroulante dans un projet MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Le contour du contrôle change pour afficher la taille de la zone de liste déroulante avec la zone de liste déroulante étendue.

1. Utilisez la poignée de redimensionnement inférieure pour modifier la taille initiale de la zone de liste déroulante.

   ![Dimensionnement de zone de&#45;de liste déroulante dans un projet MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Sélectionnez de nouveau la flèche déroulante pour fermer la partie de liste déroulante de la zone de liste déroulante.

> [!NOTE]
> Quand vous ajoutez une zone de liste avec une barre de défilement horizontale à une boîte de dialogue à l’aide de MFC, la barre de défilement ne s’affiche pas automatiquement dans votre application.
>
> Définissez une largeur maximale pour l’élément le plus large en appelant [CListBox :: SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) dans votre code. Si cette valeur n’est pas définie, la barre de défilement ne s’affiche pas, même lorsque les éléments de la zone de liste sont plus larges que la zone.

## <a name="align-controls"></a>Aligner les contrôles

- Pour aligner les contrôles, sélectionnez les contrôles que vous souhaitez aligner. Accédez à **format** du menu  >  **Aligner** et choisissez l’un des alignements suivants :

   |Alignment|Description|
   |-----|-----------|
   |**Les côtés gauches**|Aligne les contrôles sélectionnés sur leurs côtés gauches.|
   |**Ateliers**|Aligne horizontalement les contrôles sélectionnés sur leurs points centraux.|
   |**Droits**|Aligne les contrôles sélectionnés sur leurs côtés droits.|
   |**Sommets**|Aligne les contrôles sélectionnés sur leurs bords supérieurs.|
   |**Les milieux**|Aligne verticalement les contrôles sélectionnés sur leurs points centraux.|
   |**Les bases**|Aligne les contrôles sélectionnés sur leurs bords inférieurs.|

   Veillez à sélectionner le contrôle à dominer en premier ou à le définir comme étant le contrôle dominant avant d’exécuter la commande d’alignement ou de dimensionnement, car la position finale du groupe de contrôles dépend de la position du contrôle dominant.

- Pour espacer uniformément les contrôles, sélectionnez les contrôles que vous souhaitez réorganiser. Accédez à l’espace de **format** de menu  >  **uniformément** et choisissez l’un des alignements suivants :

   |Espacement|Description|
   |---|---|
   |**Horizontalement**|Espace les contrôles uniformément entre le contrôle le plus à gauche et le contrôle le plus à droite sélectionné.|
   |**Descendre**|Espacer les contrôles uniformément entre le contrôle le plus haut et le contrôle le plus bas sélectionné.|

- Pour centrer les contrôles, sélectionnez le ou les contrôles que vous souhaitez réorganiser. Accédez **au menu**  >  **Centre de la boîte de dialogue** et choisissez l’une des options suivantes :

   |Disposition|Description|
   |---|---|
   |**Vertical**|Centrer les contrôles verticalement dans la boîte de dialogue.|
   |**Horizontal**|Centrer les contrôles horizontalement dans la boîte de dialogue.|

- Pour aligner les boutons de commande, sélectionnez un ou plusieurs boutons de commande. Accédez au menu **format**  >  des **boutons**, puis choisissez l’une des options suivantes :

   |Disposition|Description|
   |---|---|
   |**Right**|Aligne les boutons de commande le long du bord droit de la boîte de dialogue.|
   |**Bas**|Aligne les boutons de commande le long du bord inférieur de la boîte de dialogue.|

   Si vous sélectionnez un contrôle autre qu’un bouton de commande, sa position n’est pas affectée.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Gérer les contrôles de boîte de dialogue](controls-in-dialog-boxes.md)<br/>
[Comment : ajouter, modifier ou supprimer des contrôles](adding-editing-or-deleting-controls.md)<br/>
[Comment : définir l’accès aux contrôles et les valeurs](defining-mnemonics-access-keys.md)<br/>
