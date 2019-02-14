---
title: Organisation des contrôles dans les boîtes de dialogue (C++) | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 99667898428fe9532d59277bfedafd24927304dc
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264879"
---
# <a name="arrangement-of-controls-on-dialog-boxes-c"></a>Organisation des contrôles dans les boîtes de dialogue (C++)

Le **boîte de dialogue** éditeur fournit des outils de disposition qui alignent et dimensionnent un contrôle automatiquement. Pour la plupart des tâches, vous pouvez utiliser la [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Tous les **boîte de dialogue Éditeur** des commandes de barre d’outils sont également disponibles sur le **Format** menu et la plupart ont [touches de raccourci](../windows/accelerator-keys-for-the-dialog-editor.md).

De nombreuses commandes de disposition pour les boîtes de dialogue sont disponibles uniquement lorsque plus d’un contrôle est sélectionné. Vous pouvez sélectionner un ou plusieurs contrôles, et lorsque plus d’un contrôle est sélectionné, le premier que vous sélectionnez est par défaut le contrôle « principal ». Pour plus d’informations sur la sélection des contrôles et le contrôle dominant, consultez [sélection de contrôles](../windows/selecting-controls.md).

L’emplacement, la hauteur et la largeur du contrôle actuel sont affichés dans le coin inférieur droit de la barre d’état. Lorsque la boîte de dialogue est activée, la barre d’état affiche la position de la boîte de dialogue sous la forme dans son ensemble et sa hauteur et sa largeur.

## <a name="dialog-editor-states-guides-and-grids"></a>États de l’éditeur de boîte de dialogue (repères et grilles)

Vous pouvez organiser les contrôles dans les boîtes de dialogue avec le **boîte de dialogue** editor dans un des trois états différents :

- Avec les guides et les marges (paramètre par défaut)

- Avec la grille de disposition sur

- Sans les fonctionnalités d’alignement

Le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) contient des boutons qui contrôlent l’état. Pour modifier l’état, sélectionnez l’icône appropriée. Vous pouvez également modifier des États à l’aide de la **Guide paramètres** commande sur le **Format** menu.

Le **Guide paramètres** boîte de dialogue a les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Repères de disposition**|Affiche les paramètres pour les repères de disposition.|
|**Aucun**|Masque les outils de disposition.|
|**Règles et repères**|Lorsque l’option est activée, les règles sont ajoutées aux outils de disposition ; guides peuvent être placés dans les règles. Les guides par défaut sont les marges, qui peuvent être déplacés en faisant glisser. Sélectionnez les règles pour placer un guide. Contrôles « alignent » sur les repères lorsque les contrôles sont déplacées sur ou en regard. Contrôles sont également déplacés avec un repère une fois qu’ils sont rattachés à ce dernier. Quand un contrôle est attaché à un repère de chaque côté et un guide est déplacé, le contrôle est redimensionné.|
|**Grid**|Crée une grille de disposition. Nouveaux contrôles sont automatiquement alignés sur la grille.|
|**Espacement de la grille**|Affiche les paramètres pour l’espacement de la grille en unités de boîte de dialogue (DLU).|
|**Largeur : DLU**|Définit la largeur de la grille de disposition en DLU. Une DLU horizontale est la largeur moyenne de la police de la boîte de dialogue divisée en quatre parties.|
|**Hauteur : DLU**|Définit la hauteur de la grille de disposition dans DLU. Une DLU verticale correspond à la hauteur moyenne de la police de la boîte de dialogue divisée par huit.|

### <a name="create-and-set-guides-and-margins"></a>Créer et définir des repères et marges

Si vous déplacez des contrôles, ajout de contrôles, ou réorganiser une disposition en cours, guides peuvent aider à vous aligner précisément les contrôles dans une boîte de dialogue. Les repères s’affichent en bleu traits en pointillés dans la boîte de dialogue affichées dans l’éditeur et les flèches correspondantes dans les règles en haut et sur le côté gauche de la **boîte de dialogue** éditeur.

Lorsque vous créez une boîte de dialogue, quatre marges sont fournies. Les marges sont des repères modifiés, apparaissant sous forme de lignes en pointillés bleues.

|Process|Étapes|
|----------------|----------------|
|Pour créer un repère|Dans la règle, sélectionnez une seule fois pour créer un repère. (Un seul clic crée un nouveau guide ; double-cliquant lance le **Guide paramètres** boîte de dialogue dans laquelle vous pouvez spécifier les paramètres du guide.)|
|Pour définir un repère|Dans la boîte de dialogue, cliquez sur le guide et faites-le glisser vers une nouvelle position. (Vous pouvez également cliquer sur la flèche dans la règle à faire glisser le repère associé.)<br/><br/>Les coordonnées du guide sont affichées dans la barre d’état en bas de la fenêtre et dans la règle. Déplacez le pointeur sur la flèche dans la règle pour afficher la position exacte de ce guide.|
|Pour supprimer un repère|Faites glisser le repère en dehors de la boîte de dialogue.<br/><br/>\- ou -<br/><br/>Faites glisser la flèche correspondante hors de la règle.|
|Pour déplacer des marges|Faites glisser la marge à la nouvelle position.<br/><br/>Pour faire disparaître une marge, déplacez la marge à la position zéro. Afin de rétablir la marge, placez le pointeur sur la marge position zéro et déplacez la marge à la position.|

### <a name="align-controls-on-a-guide"></a>Aligner les contrôles sur un repère

Les poignées de redimensionnement de contrôles alignent sur les repères lorsque les contrôles sont déplacés et guides s’aligner sur les contrôles si aucun contrôle précédemment aligné sur le guide. Lorsqu’un repère est déplacé, les contrôles qui dépendent, sont également déplacent. Les contrôles alignés sur plusieurs repères sont redimensionnés lorsqu’un des guides est déplacé.

Les graduations dans les règles qui déterminent l’espacement des guides et des contrôles sont définies par les unités de boîte de dialogue (DLU). Une DLU est basée sur la taille de la police de la boîte de dialogue, normalement 8 points MS Shell Dlg. Une DLU horizontale est la largeur moyenne de la police de la boîte de dialogue divisée en quatre parties. Une DLU verticale est la hauteur moyenne de la police divisée par huit.

Pour dimensionner un groupe de contrôles avec des guides :

1. À un repère d’alignement côté « un » de contrôle (ou des contrôles).

1. Faites glisser un guide pour l’autre côté du contrôle (ou des contrôles).

   Si nécessaire, avec plusieurs contrôles, taille de chacun d’eux à s’aligner sur le second guide.

1. Déplacez des repères de dimensionner le contrôle (ou les contrôles).

Pour modifier les intervalles des graduations :

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue le **espacement de la grille** champ, spécifiez une nouvelle largeur et hauteur DLU.

### <a name="disable-guides"></a>Désactiver les repères

Vous pouvez utiliser les touches spéciales conjointement avec la souris pour désactiver l’alignement sur les guides. À l’aide de la **Alt** clé désactive les effets d’alignement du guide sélectionnée. Déplacement d’un repère avec le **MAJ** clé empêche le déplacement avec le guide de contrôles alignés.

- Pour désactiver l’alignement sur les repères, faites glisser le contrôle tout en maintenant enfoncée la **Alt** clé.

- Pour déplacer des repères sans déplacer les contrôles alignés, faites glisser le repère tout en maintenant enfoncée la **MAJ** clé.

- Pour désactiver les repères, à partir de la **Format** menu, choisissez **Guide paramètres**. Ensuite, dans le **Guide paramètres** boîte de dialogue **repères de disposition**, sélectionnez **aucun**.

   > [!NOTE]
   > Vous pouvez également double-cliquer sur la règle pour accéder à la **Guide paramètres** boîte de dialogue.

> [!TIP]
> Un raccourci pour désactiver les repères se trouve sur le **Format** menu, sélectionnez **activer/désactiver les repères**.

### <a name="modify-the-layout-grid"></a>Modifier la grille de disposition

Lorsque vous êtes placement ou réorganiser les contrôles dans une boîte de dialogue, vous pouvez utiliser la grille de disposition pour un positionnement plus précis. Lorsque la grille est activée, les contrôles apparaissent comme « aligne » sur les lignes en pointillés de la grille comme si elle était aimantée. Vous pouvez activer cette fonctionnalité « Aligner sur la grille » et de désactiver et modifier la taille des disposition des cellules de grille.

Pour activer ou désactiver les la grille de disposition :

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue, activez ou désactivez le **grille** bouton.

   Vous pouvez toujours contrôler la grille de l’individu **boîte de dialogue** fenêtres de l’éditeur à l’aide de la **bascule grille** bouton sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Pour modifier la taille de la grille de disposition :

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue, tapez la hauteur et largeur dans DLU pour les cellules dans la grille. La largeur ou hauteur minimale est 4 DLU.

## <a name="selecting-controls"></a>Sélection de contrôles

Sélectionner des contrôles à la taille, aligner, déplacer, copier, ou supprimez-les, puis terminez l’opération que vous souhaitez. Dans la plupart des cas, vous devez sélectionner plusieurs contrôles à utiliser les outils de dimensionnement et d’alignement sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Lorsqu’un contrôle est sélectionné, elle comporte une bordure ombrée autour d’elle avec solide (actif) ou vides (inactives) « poignées de dimensionnement » petits carrés qui apparaissent dans la bordure de sélection. Lorsque plusieurs contrôles sont sélectionnés, le contrôle dominant doté de poignées de redimensionnement solide et tous les autres contrôles sélectionnés ont des poignées de redimensionnement creux.

Lorsque vous êtes de dimensionnement ou aligner plusieurs contrôles, la **boîte de dialogue** éditeur utilise le « contrôle dominant » pour déterminer comment les autres contrôles sont dimensionnés ou alignés. Par défaut, le contrôle dominant est le premier contrôle sélectionné.

### <a name="to-select-multiple-controls"></a>Pour sélectionner plusieurs contrôles

1. Dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox), sélectionnez le **pointeur** outil.

1. Utilisez une des étapes suivantes pour effectuer votre sélection :

   - Faites glisser le pointeur pour dessiner une zone de sélection autour des contrôles que vous souhaitez sélectionner dans votre boîte de dialogue. Lorsque vous relâchez le bouton de la souris, tous les contrôles à l’intérieur ou à l’intersection de la zone de sélection sont sélectionnés.

   - Maintenez la **MAJ** la clé, sélectionnez les contrôles que vous souhaitez inclure dans la sélection.

   - Maintenez la **Ctrl** la clé, sélectionnez les contrôles que vous souhaitez inclure dans la sélection.

### <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>Pour supprimer un contrôle d’un groupe de contrôles sélectionnés ou pour ajouter un contrôle à un groupe de contrôles sélectionnés

Avec un groupe de contrôles sélectionnés, maintenez la **MAJ** la clé, sélectionnez le contrôle que vous souhaitez supprimer ou ajouter à la sélection existante.

   > [!NOTE]
   > Maintenant enfoncé le **Ctrl** clé et la sélection d’un contrôle au sein d’une sélection rendra qui contrôlent le contrôle dominant dans cette sélection.

### <a name="to-specify-the-dominant-control"></a>Pour spécifier le contrôle dominant

Maintenez la **Ctrl** la clé, sélectionnez le contrôle que vous souhaitez utiliser pour influencer la taille ou l’emplacement d’autres contrôles *premier*.

> [!NOTE]
> Les poignées de redimensionnement du contrôle dominant sont pleines tandis que celles des contrôles secondaires sont vides. Le dimensionnement ou l’alignement est basé sur le contrôle dominant.

### <a name="to-change-the-dominant-control"></a>Pour modifier le contrôle dominant

1. Effacer la sélection actuelle, cliquez en dehors de tous les contrôles actuellement sélectionnés.

1. Répétez la procédure précédente, en sélectionnant un autre contrôle en premier.

## <a name="sizing-controls"></a>Dimensionnement de contrôles

Utilisez les poignées de redimensionnement pour redimensionner un contrôle. Lorsque le pointeur est positionné sur une poignée de redimensionnement, il change de forme pour indiquer les sens dans lequel le contrôle peut être redimensionné. Poignées de redimensionnement active sont correctes ; Si une poignée de redimensionnement est vide, le contrôle ne peut pas être redimensionné le long de cet axe.

Vous pouvez également modifier la taille d’un contrôle par le contrôle à des guides ou les marges d’alignement, ou en déplaçant un accroché guide en dehors d’un autre et contrôle.

### <a name="to-size-an-individual-control"></a>Pour dimensionner un contrôle individuel

1. Sélectionnez le contrôle.

1. Faites glisser les poignées de redimensionnement pour modifier la taille du contrôle :

   - Poignées de redimensionnement en haut et côtés modifier la taille horizontale ou verticale.

   - Poignées de redimensionnement dans les angles modifier la taille horizontale et verticale.

   > [!TIP]
   > Vous pouvez redimensionner le contrôle d’unité une boîte de dialogue (DLU) à la fois en maintenant enfoncée la **MAJ** clés et à l’aide la **flèche droite** et **bas** clés.

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Pour dimensionner automatiquement un contrôle pour s’adapter au texte qu’il contient

Choisissez **ajuster au contenu** à partir de la **Format** menu ou cliquez sur le contrôle et choisissez **ajuster au contenu** dans le menu contextuel.

### <a name="to-make-controls-the-same-width-height-or-size"></a>Pour rendre les contrôles la même largeur, hauteur ou taille

Vous pouvez redimensionner un groupe de contrôles en fonction de la taille du contrôle dominant.

1. Sélectionnez les contrôles que vous voulez redimensionner.

   Le contrôle sélectionné en premier dans la série est le contrôle dominant. La taille finale des contrôles dans le groupe dépend de la taille du contrôle dominant.

1. À partir de la **Format** menu, choisissez **Uniformiser la taille**, puis choisissez **à la fois**, **hauteur**, ou **largeur**.

### <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>Pour définir la taille de la liste déroulante de zone et sa liste déroulante

Vous pouvez dimensionner une zone de liste déroulante lorsque vous l’ajoutez à la boîte de dialogue. Vous pouvez également spécifier la taille de la zone de liste déroulante. Pour plus d’informations, consultez [Ajout de valeurs à un contrôle Combo Box](../windows/adding-values-to-a-combo-box-control.md).

#### <a name="to-size-a-combo-box"></a>Pour dimensionner une zone de liste déroulante

1. Sélectionnez le contrôle de zone de liste déroulante dans votre boîte de dialogue.

   Initialement, seuls les poignées de redimensionnement de gauche et droite sont actifs.

1. Utilisez les poignées de redimensionnement pour définir la largeur de la zone de liste déroulante.

Vous pouvez également définir la taille verticale de la partie de la liste déroulante de la zone de liste déroulante.

#### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Pour définir la taille de la liste déroulante zone de liste déroulante

1. Sélectionnez le bouton de flèche de déroulement à droite de la zone de liste déroulante.

   ![Flèche sur une zone de liste déroulante dans un projet MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Le contour du contrôle change pour afficher la taille de la zone de liste déroulante avec la zone de liste déroulante étendue.

1. Utilisez la poignée de redimensionnement inférieure pour modifier la taille initiale de la zone de liste déroulante.

   ![Liste déroulante&#45;redimensionnement de la zone dans un projet MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Sélectionnez la flèche déroulante à nouveau pour fermer la partie de la liste déroulante de la zone de liste déroulante.

### <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>Pour définir la largeur d’une barre de défilement horizontale et faire apparaître

Lorsque vous ajoutez une zone de liste avec une barre de défilement horizontale à une boîte de dialogue à l’aide des classes MFC, la barre de défilement ne s’affichent automatiquement dans votre application.

Définissez une largeur maximale pour l’élément le plus large en appelant [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) dans votre code.

   Sans cette valeur est définie, la barre de défilement ne s’affichent, même lorsque les éléments dans la zone de liste sont plus larges que la zone.

## <a name="group-radio-buttons-on-a-dialog-box"></a>Boutons de case d’option de groupe sur une boîte de dialogue

Lorsque vous ajoutez des cases d’option à une boîte de dialogue, traitez-les comme un groupe en définissant un **groupe** propriété dans le **propriétés** fenêtre pour le premier bouton dans le groupe. Un ID de contrôle pour cette case d’option apparaît alors dans [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md), ce qui vous permet d’ajouter une variable membre pour le groupe de cases d’option.

Vous pouvez ajouter plusieurs groupes de cases d’option à une boîte de dialogue. Pour ajouter chaque groupe, appliquez la procédure suivante.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Pour ajouter un groupe de cases d’option à une boîte de dialogue

1. Sélectionnez le contrôle de case d’option dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox) et choisissez l’emplacement dans la boîte de dialogue où vous souhaitez placer le contrôle.

1. Répétez l’étape 1 pour ajouter autant de cases d’option que vous le souhaitez. Assurez-vous que les cases d’option dans le groupe sont suivent dans l’ordre de tabulation.

1. Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), affectez la valeur **True** à la propriété *Groupe* de la **première**case d’option dans l’ordre de tabulation.

   L’affectation de la valeur **True** à la propriété **Groupe** ajoute le style WS_GROUP à l’entrée du bouton dans l’objet de boîte de dialogue du script de ressources et permet de s’assurer qu’un utilisateur ne peut sélectionner qu’une case d’option à la fois dans le groupe de boutons (quand l’utilisateur clique sur une case d’option, les autres cases dans le groupe sont désactivées).

   > [!NOTE]
   > La propriété **Groupe** de la première case d’option du groupe doit avoir la valeur **True**. Si vous avez d’autres contrôles qui ne font pas partie du groupe de cases d’option, affectez aussi la valeur **True** à la propriété *Groupe* du premier contrôle **qui est en dehors du groupe** . Vous pouvez rapidement identifier le premier contrôle en dehors du groupe en appuyant sur **Ctrl**+**D** pour afficher l’ordre de tabulation.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Pour ajouter une variable membre pour le groupe de cases d’option

1. Cliquez avec le bouton droit sur le premier contrôle de case d’option dans l’ordre de tabulation (le contrôle dominant et celui dont la propriété **Groupe** a la valeur True).

1. Choisissez **Ajouter une variable** dans le menu contextuel.

1. Dans l’ [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md), cochez la case **Variable de contrôle** , puis sélectionnez la case d’option **Valeur** .

1. Dans la zone **Nom de la variable** , tapez un nom pour la nouvelle variable membre.

1. Dans le **type de Variable** zone de liste, sélectionnez **int** ou type `int`.

1. Vous pouvez maintenant modifier votre code pour spécifier la case d’option qui doit apparaître sélectionnée. Par exemple, `m_radioBox1 = 0;` sélectionne le premier bouton de case d’option dans le groupe.

## <a name="to-align-groups-of-controls"></a>Pour aligner des groupes de contrôles

1. Sélectionnez les contrôles que vous souhaitez aligner. Veillez à sélectionner le contrôle que vous souhaitez d’abord être le contrôle dominant ou définissez-le comme contrôle dominant avant d’exécuter l’alignement ou de dimensionnement de commande.

   La position finale du groupe de contrôles dépend de la position du contrôle dominant. Pour plus d’informations sur la sélection du contrôle dominant, consultez [spécification du contrôle Dominant](../windows/specifying-the-dominant-control.md).

1. À partir de la **Format** menu, choisissez **Align**, puis choisissez un des alignements suivants :

   |Value|Description|
   |-----|-----------|
   |`Lefts`|Aligne les contrôles sélectionnés sur leurs côtés gauches.|
   |`Centers`|Aligne les contrôles sélectionnés sur leur centre horizontalement.|
   |`Rights`|Aligne les contrôles sélectionnés sur leurs côtés.|
   |`Tops`|Aligne les contrôles sélectionnés sur leurs bords supérieurs.|
   |`Middles`|Aligne les contrôles sélectionnés verticalement sur leur milieu.|
   |`Bottoms`|Aligne les contrôles sélectionnés sur le bord inférieur.|

### <a name="to-even-the-spacing-between-controls"></a>De même, l’espacement entre les contrôles

Le **boîte de dialogue** éditeur vous permet aux contrôles d’espace uniformément entre les contrôles extérieur sélectionnés.

1. Sélectionnez les contrôles que vous souhaitez réorganiser.

1. À partir de la **Format** menu, choisissez **Espace uniformément**, puis choisissez un des espacements suivants :

   - `Across`: espace les contrôles uniformément entre le plus à gauche et le plus à droite contrôle sélectionné.

   - `Down`: espace les contrôles uniformément entre le premier et le plus bas contrôle sélectionné.

### <a name="to-center-controls-in-a-dialog-box"></a>Pour centrer les contrôles dans une boîte de dialogue

1. Sélectionnez l’ou les contrôles que vous souhaitez réorganiser.

1. À partir de la **Format** menu, choisissez **Centrer dans la boîte de dialogue**, puis choisissez une des options suivantes :

   - `Vertical`: centre les contrôles verticalement dans la boîte de dialogue.

   - `Horizontal`: centre les contrôles horizontalement dans la boîte de dialogue.

### <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>Pour réorganiser les boutons de commande à droite ou en bas d’une boîte de dialogue

1. Sélectionnez un ou plusieurs boutons de commande.

1. À partir de la **Format** menu, choisissez **réorganiser les boutons**, puis choisissez une des options suivantes :

   - `Right`: aligne le bord droit de la boîte de dialogue de boutons.

   - `Bottom`: aligne le bord inférieur de la boîte de dialogue de boutons.

       Si vous sélectionnez un contrôle autre qu’un bouton de commande, sa position n’est pas affectée.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)