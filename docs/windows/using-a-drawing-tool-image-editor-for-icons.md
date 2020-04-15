---
title: 'Comment : Utiliser un outil de dessin'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: b0041124c35414a0c1c998642b5321319602c872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359854"
---
# <a name="how-to-use-a-drawing-tool"></a>Comment : Utiliser un outil de dessin

**L’éditeur d’images** dispose d’outils de dessin et d’effacement à main levée qui fonctionnent tous de la même manière. Vous sélectionnez l’outil et, si nécessaire, [sélectionnez les couleurs de premier plan et de fond](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) et les options de taille et de forme. Vous déplacez ensuite le pointeur vers l’image et cliquez ou faites glisser pour dessiner et effacer.

## <a name="drawing-tools"></a>Outils de dessin

Vous pouvez sélectionner des outils de dessin à partir de la barre d’outils **Image Editor** ou du menu **Image.** Lorsque vous sélectionnez **l’outil Eraser,** **l’outil Brosse** ou **l’outil aérographe,** le sélecteur d’options affiche les options de cet outil.

> [!TIP]
> Des conseils d’outils apparaissent lorsque vous planez votre curseur sur les boutons de la [barre d’outils Image Editor](../windows/toolbar-image-editor-for-icons.md). Ces conseils vous aideront à identifier les boutons spécifiques mentionnés ici.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Sélectionner et utiliser un outil de dessin à partir de la barre d’outils Image Editor

1. Sélectionnez un bouton sur la barre **d’outils Image Editor.**

   - **L’outil Eraser** peint sur l’image avec la couleur de fond actuelle lorsque vous appuyez sur le bouton de la souris gauche.

      > [!TIP]
      > Au lieu d’utiliser **l’outil Eraser,** vous pouvez trouver plus pratique de dessiner dans la couleur de fond avec l’un des outils de dessin.

   - **L’outil Crayon** dessine à main levée dans une largeur constante d’un pixel.

   - **L’outil Brosse** a différentes formes et tailles.

   - **L’outil Airbrush** distribue au hasard des pixels de couleur autour du centre de la brosse.

1. Si nécessaire, sélectionnez les couleurs et un pinceau :

   - Dans la [palette Couleurs](../windows/colors-window-image-editor-for-icons.md), sélectionnez le bouton de la souris gauche pour sélectionner une couleur de premier plan ou le bouton de la souris droite pour sélectionner une couleur de fond.

   - Dans le [sélecteur Options](../windows/toolbar-image-editor-for-icons.md), sélectionnez une forme représentant le pinceau que vous souhaitez utiliser.

1. Pointez vers l’endroit sur l’image où vous voulez commencer à dessiner ou à peindre. Le pointeur change de forme en fonction de l’outil que vous avez choisi.

1. Appuyez sur le bouton de la souris gauche (pour la couleur du premier plan) ou le bouton de la souris droite (pour la couleur de fond), et maintenez-le vers le bas pendant que vous dessinez.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Sélectionner et utiliser un outil de dessin du menu Image

1. Aller au menu **Image** > **Tools**.

1. Sur le sous-mois en cascade, choisissez l’outil que vous souhaitez utiliser.

## <a name="lines-or-closed-figures"></a>Lignes ou chiffres fermés

Les outils **Image Editor** pour tracer des lignes et des figures fermées fonctionnent tous de la même manière : vous placez le point d’insertion à un moment donné et faites glisser vers un autre. Pour les lignes, ces points sont les points de terminaison. Pour les chiffres fermés, ces points sont opposés coins d’un rectangle délimitant la figure.

Les lignes sont dessinées dans une largeur déterminée par la sélection actuelle de brosse, et les figures encadrées sont dessinées dans une largeur déterminée par la sélection de largeur de courant. Les lignes et tous les personnages, encadrés et remplis, sont dessinés dans la couleur de premier plan actuelle si vous appuyez sur le bouton de la souris gauche, ou dans la couleur de fond actuelle si vous appuyez sur le bouton de la souris droite.

### <a name="to-draw-a-line"></a>Pour tracer une ligne

1. Utilisez la [barre d’outils Image Editor](../windows/toolbar-image-editor-for-icons.md) ou allez au menu Outils **d’image**> **Tools** et choisissez l’outil **Line.**

1. Si nécessaire, sélectionnez les couleurs et un pinceau :

   - Dans la [palette Couleurs](../windows/colors-window-image-editor-for-icons.md), sélectionnez le bouton de la souris gauche pour sélectionner une couleur de premier plan ou le bouton de la souris droite pour sélectionner une couleur de fond.

   - Dans le [sélecteur Options](../windows/toolbar-image-editor-for-icons.md), sélectionnez une forme représentant le pinceau que vous souhaitez utiliser.

1. Placez le pointeur au point de départ de la ligne.

1. Faites glisser jusqu’au point de terminaison de la ligne.

### <a name="to-draw-a-closed-figure"></a>Pour dessiner un chiffre fermé

1. Utilisez la barre **d’outils Image Editor** ou rendez-vous dans le menu Outils **d’image** > **Tools** et sélectionnez un outil de dessin à **figure fermée.**

   Les outils **de dessin à figure fermée** créent des chiffres indiqués sur leurs boutons respectifs.

1. Si nécessaire, sélectionnez les couleurs et une largeur de ligne.

1. Déplacez le pointeur à un coin de la zone rectangulaire dans laquelle vous voulez dessiner la figure.

1. Faites glisser le pointeur vers le coin en diagonale opposée.

## <a name="custom-brushes"></a>Brosses personnalisées

Un pinceau personnalisé est une partie rectangulaire d’une image que vous prenez et utilisez comme l’un des pinceaux prêts à l’emploi de **l’éditeur**d’images. Toutes les opérations que vous pouvez effectuer sur une sélection, vous pouvez effectuer sur un pinceau personnalisé ainsi.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Créer un pinceau personnalisé à partir d’une partie d’une image

1. Sélectionnez la partie de l’image que vous souhaitez utiliser pour un pinceau.

1. Maintenez la clé **Shift** vers le bas, choisissez dans la sélection et faites-la glisser à travers l’image, ou allez à la sélection **d’utilisation d’image** > de menu**comme brosse**.

   Votre sélection devient un pinceau personnalisé qui distribue les couleurs dans la sélection à travers l’image. Des copies de la sélection sont laissées le long du chemin de traînage. Plus vous faites glisser lentement, plus d’exemplaires sont faits.

   > [!NOTE]
   > Sélectionner **l’utiliser comme brosse** sans d’abord sélectionner une partie de l’image utilisera l’image entière comme un pinceau. Le résultat de l’utilisation d’un pinceau personnalisé dépendra également si vous avez sélectionné un [fond opaque ou transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Les pixels dans un pinceau personnalisé qui correspondent à la couleur de fond actuelle sont normalement transparents : ils ne peignent pas sur l’image existante. Vous pouvez modifier ce comportement de sorte que les pixels couleur de fond peignent sur l’image existante.

Vous pouvez utiliser le pinceau personnalisé comme un timbre ou un pochoir pour créer différents effets spéciaux.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Pour dessiner des formes de pinceau personnalisées dans la couleur de fond

1. Sélectionnez un arrière-plan opaque ou transparent.

1. Réglez la couleur de fond à la couleur dans laquelle vous voulez dessiner.

1. Placez le pinceau personnalisé où vous voulez dessiner.

1. Sélectionnez le bouton de la souris droite. Toutes les régions opaques de la brosse personnalisée sont dessinées dans la couleur de fond.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Pour doubler ou réduire de moitié la taille personnalisée de la brosse

Appuyez sur**+** le signe **Plus** ( ) clé pour**-** doubler la taille du pinceau, ou le signe **Minus** ( ) clé pour le réduire de moitié.

### <a name="to-cancel-the-custom-brush"></a>Annuler la brosse personnalisée

Appuyez sur **Esc** ou choisissez un autre outil de dessin.

## <a name="requirements"></a>Spécifications

None

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Comment : Créer une icône ou une autre image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Comment: Modifier une image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Comment: Travailler avec la couleur](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Clés d’accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
