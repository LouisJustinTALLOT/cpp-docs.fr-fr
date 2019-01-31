---
title: États d’éditeur de la boîte de dialogue (repères et grilles) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: dbacf9ef-e8b0-4125-a7ce-84911c482e98
ms.openlocfilehash: 52fc19d8a39680c16692177e2758fba78afc7d3a
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484992"
---
# <a name="dialog-editor-states-guides-and-grids-c"></a>États d’éditeur de la boîte de dialogue (repères et grilles) (C++)

Vous pouvez organiser les contrôles dans les boîtes de dialogue avec le **boîte de dialogue** editor dans un des trois états différents :

- Avec les guides et les marges (paramètre par défaut)

- Avec la grille de disposition sur

- Sans les fonctionnalités d’alignement

Le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) contient des boutons qui contrôlent l’état. Pour modifier l’état, cliquez sur l’icône appropriée. Vous pouvez également modifier des États à l’aide de la **Guide paramètres** commande sur le **Format** menu.

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

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="create-and-set-guides-and-margins"></a>Créer et définir des repères et marges

Si vous déplacez des contrôles, ajout de contrôles, ou réorganiser une disposition en cours, guides peuvent aider à vous aligner précisément les contrôles dans une boîte de dialogue. Les repères s’affichent en bleu traits en pointillés dans la boîte de dialogue affichées dans l’éditeur et les flèches correspondantes dans les règles en haut et sur le côté gauche de la **boîte de dialogue** éditeur.

Lorsque vous créez une boîte de dialogue, quatre marges sont fournies. Les marges sont des repères modifiés, apparaissant sous forme de lignes en pointillés bleues.

### <a name="to-create-a-guide"></a>Pour créer un repère

Dans la règle, cliquez une fois pour créer un repère. (Un seul clic crée un nouveau guide ; double-cliquant lance le **Guide paramètres** boîte de dialogue dans laquelle vous pouvez spécifier les paramètres du guide.)

### <a name="to-set-a-guide"></a>Pour définir un repère

Dans la boîte de dialogue, cliquez sur le guide et faites-le glisser vers une nouvelle position. (Vous pouvez également cliquer sur la flèche dans la règle à faire glisser le repère associé.)

Les coordonnées du guide sont affichées dans la barre d’état en bas de la fenêtre et dans la règle. Déplacez le pointeur sur la flèche dans la règle pour afficher la position exacte de ce guide.

### <a name="to-delete-a-guide"></a>Pour supprimer un repère

Faites glisser le repère en dehors de la boîte de dialogue.

\- ou -

Faites glisser la flèche correspondante hors de la règle.

### <a name="to-move-margins"></a>Pour déplacer des marges

Faites glisser la marge à la nouvelle position.

Pour faire disparaître une marge, déplacez la marge à la position zéro. Afin de rétablir la marge, placez le pointeur sur la marge position zéro et déplacez la marge à la position.

## <a name="align-controls-on-a-guide"></a>Aligner les contrôles sur un repère

Les poignées de redimensionnement de contrôles alignent sur les repères lorsque les contrôles sont déplacés et guides s’aligner sur les contrôles si aucun contrôle précédemment aligné sur le guide. Lorsqu’un repère est déplacé, les contrôles qui dépendent, sont également déplacent. Les contrôles alignés sur plusieurs repères sont redimensionnés lorsqu’un des guides est déplacé.

Les graduations dans les règles qui déterminent l’espacement des guides et des contrôles sont définies par les unités de boîte de dialogue (DLU). Une DLU est basée sur la taille de la police de la boîte de dialogue, normalement 8 points MS Shell Dlg. Une DLU horizontale est la largeur moyenne de la police de la boîte de dialogue divisée en quatre parties. Une DLU verticale est la hauteur moyenne de la police divisée par huit.

### <a name="to-size-a-group-of-controls-with-guides"></a>Pour dimensionner un groupe de contrôles avec les repères

1. À un repère d’alignement côté « un » de contrôle (ou des contrôles).

1. Faites glisser un guide pour l’autre côté du contrôle (ou des contrôles).

   Si nécessaire, avec plusieurs contrôles, taille de chacun d’eux à s’aligner sur le second guide.

1. Déplacez des repères de dimensionner le contrôle (ou les contrôles).

### <a name="to-change-the-intervals-of-the-tick-marks"></a>Pour modifier les intervalles entre les graduations

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue le **espacement de la grille** champ, spécifiez une nouvelle largeur et hauteur DLU.

## <a name="disable-guides"></a>Désactiver les repères

Vous pouvez utiliser les touches spéciales conjointement avec la souris pour désactiver l’alignement sur les guides. À l’aide de la **Alt** clé désactive les effets d’alignement du guide sélectionnée. Déplacement d’un repère avec le **MAJ** clé empêche le déplacement avec le guide de contrôles alignés.

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Pour désactiver l’alignement sur les repères

Faites glisser le contrôle tout en maintenant enfoncée la **Alt** clé.

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Pour déplacer des repères sans déplacer les contrôles alignés

Faites glisser le repère tout en maintenant enfoncée la **MAJ** clé.

### <a name="to-turn-off-the-guides"></a>Pour désactiver les repères

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue **repères de disposition**, sélectionnez **aucun**.

   > [!NOTE]
   > Vous pouvez également double-cliquer sur la règle pour accéder à la **Guide paramètres** boîte de dialogue.

\- ou -

Sur le **Format** menu, sélectionnez **activer/désactiver les repères**.

## <a name="modify-the-layout-grid"></a>Modifier la grille de disposition

Lorsque vous êtes placement ou réorganiser les contrôles dans une boîte de dialogue, vous pouvez utiliser la grille de disposition pour un positionnement plus précis. Lorsque la grille est activée, les contrôles apparaissent comme « aligne » sur les lignes en pointillés de la grille comme si elle était aimantée. Vous pouvez activer cette fonctionnalité « Aligner sur la grille » et de désactiver et modifier la taille des disposition des cellules de grille.

### <a name="to-turn-the-layout-grid-on-or-off"></a>Pour activer ou désactiver le la grille de disposition

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue, activez ou désactivez le **grille** bouton.

   Vous pouvez toujours contrôler la grille de l’individu **boîte de dialogue** fenêtres de l’éditeur à l’aide de la **bascule grille** bouton sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

### <a name="to-change-the-size-of-the-layout-grid"></a>Pour modifier la taille de la grille de disposition

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

1. Dans le **Guide paramètres** boîte de dialogue, tapez la hauteur et largeur dans DLU pour les cellules dans la grille. La largeur ou hauteur minimale est 4 DLU. Pour plus d’informations sur DLU, consultez [organisation des contrôles sur les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles (MFC)](../mfc/controls-mfc.md)<br/>
