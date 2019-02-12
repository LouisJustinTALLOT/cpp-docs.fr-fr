---
title: Organisation des contrôles dans les boîtes de dialogue (C++) | Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
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
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: 210fbf8e062b4dd8c469f9c40a015bbc19bc2843
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152740"
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

#### <a name="to-size-a-group-of-controls-with-guides"></a>Pour dimensionner un groupe de contrôles avec les repères

1. À un repère d’alignement côté « un » de contrôle (ou des contrôles).

1. Faites glisser un guide pour l’autre côté du contrôle (ou des contrôles).

   Si nécessaire, avec plusieurs contrôles, taille de chacun d’eux à s’aligner sur le second guide.

1. Déplacez des repères de dimensionner le contrôle (ou les contrôles).

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>Pour modifier les intervalles entre les graduations

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue le **espacement de la grille** champ, spécifiez une nouvelle largeur et hauteur DLU.

### <a name="disable-guides"></a>Désactiver les repères

Vous pouvez utiliser les touches spéciales conjointement avec la souris pour désactiver l’alignement sur les guides. À l’aide de la **Alt** clé désactive les effets d’alignement du guide sélectionnée. Déplacement d’un repère avec le **MAJ** clé empêche le déplacement avec le guide de contrôles alignés.

#### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Pour désactiver l’alignement sur les repères

Faites glisser le contrôle tout en maintenant enfoncée la **Alt** clé.

#### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Pour déplacer des repères sans déplacer les contrôles alignés

Faites glisser le repère tout en maintenant enfoncée la **MAJ** clé.

#### <a name="to-turn-off-the-guides"></a>Pour désactiver les repères

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue **repères de disposition**, sélectionnez **aucun**.

   > [!NOTE]
   > Vous pouvez également double-cliquer sur la règle pour accéder à la **Guide paramètres** boîte de dialogue.

\- ou -

Sur le **Format** menu, sélectionnez **activer/désactiver les repères**.

### <a name="modify-the-layout-grid"></a>Modifier la grille de disposition

Lorsque vous êtes placement ou réorganiser les contrôles dans une boîte de dialogue, vous pouvez utiliser la grille de disposition pour un positionnement plus précis. Lorsque la grille est activée, les contrôles apparaissent comme « aligne » sur les lignes en pointillés de la grille comme si elle était aimantée. Vous pouvez activer cette fonctionnalité « Aligner sur la grille » et de désactiver et modifier la taille des disposition des cellules de grille.

#### <a name="to-turn-the-layout-grid-on-or-off"></a>Pour activer ou désactiver le la grille de disposition

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue, activez ou désactivez le **grille** bouton.

   Vous pouvez toujours contrôler la grille de l’individu **boîte de dialogue** fenêtres de l’éditeur à l’aide de la **bascule grille** bouton sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

#### <a name="to-change-the-size-of-the-layout-grid"></a>Pour modifier la taille de la grille de disposition

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue, tapez la hauteur et largeur dans DLU pour les cellules dans la grille. La largeur ou hauteur minimale est 4 DLU.

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

## <a name="align-groups-of-controls"></a>Aligner des groupes de contrôles

Les procédures suivantes vous montrent comment aligner les contrôles :

### <a name="to-align-groups-of-controls"></a>Pour aligner des groupes de contrôles

1. [Sélectionnez les contrôles](../windows/selecting-multiple-controls.md) à aligner. Veillez à sélectionner le contrôle que vous souhaitez d’abord être le contrôle dominant ou définissez-le comme contrôle dominant avant d’exécuter l’alignement ou de dimensionnement de commande.

   La position finale du groupe de contrôles dépend de la position du contrôle dominant. Pour plus d’informations sur la sélection du contrôle dominant, consultez [spécification du contrôle Dominant](../windows/specifying-the-dominant-control.md).

1. À partir de la **Format** menu, choisissez **Align**, puis choisissez un des alignements suivants :

   - `Lefts`: aligne les contrôles sélectionnés sur leurs côtés gauches.

   - `Centers`: aligne les contrôles sélectionnés sur leur centre horizontalement.

   - `Rights`: aligne les contrôles sélectionnés sur leurs côtés.

   - `Tops`: aligne les contrôles sélectionnés sur leurs bords supérieurs.

   - `Middles`: aligne les contrôles sélectionnés verticalement sur leur milieu.

   - `Bottoms`: aligne les contrôles sélectionnés sur le bord inférieur.

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

## <a name="change-the-tab-order-of-controls"></a>Modifier l’ordre de tabulation des contrôles

L’ordre de tabulation est l’ordre dans lequel le **onglet** touche déplace le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue. Généralement, l’ordre de tabulation se déroule de gauche à droite et de haut en bas dans une boîte de dialogue. Chaque contrôle possède une **Tabstop** propriété qui détermine si un contrôle reçoit le focus d’entrée.

### <a name="to-set-input-focus-for-a-control"></a>Pour définir le focus d’entrée pour un contrôle

Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez **True** ou **False** dans le **Tabstop** propriété.

Même les contrôles qui n’ont pas la **Tabstop** propriété définie sur **True** doivent faire partie de l’ordre de tabulation. Ordre de tabulation est important, par exemple, lorsque vous [définir des touches d’accès rapide (mnémoniques)](../windows/defining-mnemonics-access-keys.md) pour les contrôles qui n’ont pas des légendes. Texte statique qui contient une clé d’accès pour un contrôle lié doit précéder immédiatement le contrôle concerné dans l’ordre de tabulation.

> [!NOTE]
> Si votre boîte de dialogue contient des contrôles qui se chevauchent, la modification de l’ordre de tabulation peut changer la façon des que contrôles sont affichés. Contrôles fournis plus loin dans l’ordre de tabulation sont toujours affichés au-dessus des contrôles superposés qui les précèdent dans l’ordre de tabulation.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Pour afficher l’ordre de tabulation actuel pour tous les contrôles dans une boîte de dialogue

Sur le **Format** menu, sélectionnez **l’ordre de tabulation**.

\- ou -

- Appuyez sur **Ctrl** + **D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Pour modifier l’ordre de tabulation pour tous les contrôles dans une boîte de dialogue

1. Sur le **Format** menu, sélectionnez **l’ordre de tabulation**.

   Un nombre dans le coin supérieur gauche de chaque contrôle affiche sa place dans l’ordre de tabulation en cours.

1. Définir l’ordre de tabulation en cliquant sur chaque contrôle dans l’ordre que vous souhaitez que le **onglet** clé à suivre.

1. Appuyez sur **entrée** pour quitter **l’ordre de tabulation** mode.

   > [!TIP]
   > Une fois que vous entrez **l’ordre de tabulation** mode, vous pouvez appuyer sur **ÉCHAP** ou **entrée** pour désactiver la possibilité de modifier l’ordre de tabulation.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Pour modifier l’ordre de tabulation pour deux ou plusieurs contrôles

1. À partir de la **Format** menu, choisissez **l’ordre de tabulation**.

1. Spécifier où commence la modification dans l’ordre. Maintenez tout d’abord le **Ctrl** de clé et sélectionnez le contrôle, puis sélectionnez celui dans lequel vous souhaitez modifier l’ordre.

   Par exemple, si vous souhaitez modifier l’ordre des contrôles `7` via `9`, maintenez la touche **Ctrl**, puis sélectionnez le contrôle `6` première.

   > [!NOTE]
   > Pour affecter à un contrôle spécifique numéro `1` (tout d’abord dans l’ordre de tabulation), double-cliquez sur le contrôle.

1. Mise en production la **Ctrl** de clé, puis sélectionnez les contrôles dans l’ordre que vous souhaitez que le **onglet** à partir de ce point.

1. Appuyez sur **entrée** pour quitter **l’ordre de tabulation** mode.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)