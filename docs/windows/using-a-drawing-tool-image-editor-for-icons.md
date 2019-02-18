---
title: 'Procédure : Utiliser un outil de dessin'
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
ms.openlocfilehash: 135509626e20044b0d4ec8e63d8916f4c537388e
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336551"
---
# <a name="how-to-use-a-drawing-tool"></a>Procédure : Utiliser un outil de dessin

Le **Image** mot du rédacteur à main levée de dessin et effacement outils fonctionnent tous de la même façon : vous sélectionnez l’outil et, si nécessaire, [sélectionner des couleurs de premier plan et arrière-plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) et options de taille et la forme. Vous placez le pointeur sur l’image et cliquez sur ou faites glisser pour dessiner et effacer.

## <a name="drawing-tools"></a>Outils de dessin

Lorsque vous sélectionnez le **gomme** outil, **pinceau** outil, ou **aérographe** outil, le sélecteur d’options affiche les options de l’outil.

> [!TIP]
> Au lieu d’utiliser le **gomme** outil, vous pouvez s’avérer plus commode de dessiner dans la couleur d’arrière-plan avec l’un des outils de dessin.

Vous pouvez sélectionner les outils de dessin à partir du **Éditeur d’images** barre d’outils ou le **Image** menu.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Pour sélectionner et utiliser un outil de dessin à partir de la barre d’outils Éditeur d’images

1. Sélectionnez un bouton sur le **Éditeur d’images** barre d’outils.

   - Le **gomme** outil peint sur l’image avec la couleur d’arrière-plan actuelle lorsque vous appuyez sur le bouton gauche de la souris.

   - Le **crayon** outil dessine à main levée avec une largeur constante d’un pixel.

   - Le **sélecteur d’options détermine la forme et la taille de l’outil pinceau**.

   - Le **aérographe** outil distribue aléatoirement des pixels de couleur autour du centre du pinceau.

        > [!TIP]
        >  Info-bulles s’affichent lorsque vous placez votre curseur sur les boutons sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md). Ces conseils vous aideront à identifier les différents boutons mentionnés ici.

1. Si nécessaire, sélectionnez les couleurs et un pinceau :

   - Dans le [palette de couleurs](../windows/colors-window-image-editor-for-icons.md), sélectionnez le bouton gauche de la souris pour sélectionner une couleur de premier plan ou le bouton droit de la souris pour sélectionner une couleur d’arrière-plan.

   - Dans le [sélecteur d’Options](../windows/toolbar-image-editor-for-icons.md), sélectionnez une forme qui représente le pinceau à utiliser.

1. Pointez vers l’emplacement sur l’image où vous souhaitez démarrer le dessin ou de la peinture. Le pointeur change de forme en fonction de l’outil que vous avez sélectionné.

1. Appuyez sur le bouton gauche de la souris (pour la couleur de premier plan) ou sur le bouton droit de la souris (pour la couleur d’arrière-plan) et maintenez-le enfoncé en tant que vous draw.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Pour sélectionner et utiliser un outil de dessin dans le menu Image

1. Sélectionnez le **Image** menu et sélectionnez le **outils** commande.

1. Dans le sous-menu en cascade, choisissez l’outil que vous souhaitez utiliser.

## <a name="lines-or-closed-figures"></a>Lignes ou Figures fermées

Outils de l’éditeur d’images pour dessiner des lignes et de figures fermées fonctionnent tous de la même façon : vous placez le point d’insertion à un moment donné et que vous faites glisser vers un autre. Pour les lignes, ces points sont les points de terminaison. Pour les figures fermées, ces points sont les angles opposés du rectangle englobant de la figure.

Les lignes sont dessinées dans une largeur déterminée par la sélection de pinceau actuelle et les figures encadrées sont dessinées dans une largeur déterminée par la sélection de la largeur actuelle. Toutes les figures, encadrées et remplies et les lignes sont dessinées dans la couleur de premier plan actuelle si vous appuyez sur le bouton gauche de la souris, ou dans la couleur d’arrière-plan actuelle si vous appuyez sur le bouton droit de la souris.

### <a name="to-draw-a-line"></a>Pour dessiner une ligne

1. Sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) (ou à partir de la **Image** menu, **outils** commande), choisissez le **ligne** outil.

1. Si nécessaire, sélectionnez les couleurs et un pinceau :

   - Dans le [palette de couleurs](../windows/colors-window-image-editor-for-icons.md), sélectionnez le bouton gauche de la souris pour sélectionner une couleur de premier plan ou le bouton droit de la souris pour sélectionner une couleur d’arrière-plan.

   - Dans le [sélecteur d’Options](../windows/toolbar-image-editor-for-icons.md), sélectionnez une forme qui représente le pinceau à utiliser.

1. Placez le pointeur au début de la ligne.

1. Faites glisser vers le point de terminaison de la ligne.

### <a name="to-draw-a-closed-figure"></a>Pour dessiner une figure fermée

1. Sur le **Éditeur d’images** barre d’outils (ou à partir de la **Image** menu, **outils** commande), sélectionnez un **Figure fermée dessin** outil.

   Le **Figure fermée dessin** outils créent des figures comme indiqué par leur bouton respectif.

1. Si nécessaire, sélectionnez les couleurs et une largeur de ligne.

1. Placez le pointeur sur un coin de la zone rectangulaire dans laquelle vous souhaitez dessiner la figure.

1. Faites glisser le pointeur vers le coin en diagonale opposé.

## <a name="custom-brushes"></a>Pinceaux personnalisés

Un pinceau personnalisé est une partie rectangulaire d’une image que vous sélectionnez et utilisez comme l’un de le **Image** pinceaux prêtes à l’emploi de l’éditeur. Toutes les opérations que vous pouvez effectuer sur une sélection, vous pouvez effectuer sur un pinceau personnalisé.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Pour créer un pinceau personnalisé à partir d’une partie d’une image

1. [Sélectionnez la partie de l’image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) que vous souhaitez utiliser pour un pinceau.

1. Maintenez la **MAJ** clé vers le bas, choisissez dans la sélection et faites-la glisser sur l’image. Ou à partir de la **Image** menu, choisissez **utiliser la sélection comme pinceau**.

   Votre sélection devient un pinceau personnalisé qui distribue les couleurs dans la sélection sur l’image. Copies de la sélection sont laissées sur le tracé de glissement. Vous faites glisser plus lentement, le nombre de copies est effectuées.

   > [!NOTE]
   > En sélectionnant le **utiliser une sélection comme pinceau** sans tout d’abord en sélectionnant une partie de l’image utilise l’image entière comme pinceau. Le résultat de l’utilisation d’un pinceau personnalisé varient également selon que vous avez sélectionné un [arrière-plan Opaque ou Transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Les pixels d’un pinceau personnalisé qui correspondent à la couleur d’arrière-plan actuelle sont transparents : ils ne recouvrir l’image existante. Vous pouvez modifier ce comportement afin que les pixels de la couleur d’arrière-plan recouvrir l’image existante.

Vous pouvez utiliser le pinceau personnalisé comme un tampon ou un stencil pour créer différents effets spéciaux.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Pour dessiner des formes de pinceau personnalisé dans la couleur d’arrière-plan

1. [Sélectionnez un arrière-plan transparent ou opaque](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

1. [Définir la couleur d’arrière-plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) à la couleur dans laquelle vous souhaitez dessiner.

1. Positionner le pinceau personnalisé où vous souhaitez dessiner.

1. Sélectionnez le bouton droit de la souris. Les zones opaques du pinceau personnalisé sont dessinées dans la couleur d’arrière-plan.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Double-cliquez ou sont divisés par deux la taille du pinceau personnalisé

Appuyez sur la **signe** (**+**) pour doubler la taille du pinceau, ou le **signe** (**-**) clé à diviser en deux .

### <a name="to-cancel-the-custom-brush"></a>Pour annuler un pinceau personnalisé

Appuyez sur **ÉCHAP** ou choisissez un autre outil de dessin.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md)