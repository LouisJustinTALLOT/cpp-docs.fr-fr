---
title: 'Comment : utiliser un outil de dessin'
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
ms.openlocfilehash: 61c06ee3fecac18fb95663c0d13474b8bd3b94f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214381"
---
# <a name="how-to-use-a-drawing-tool"></a>Comment : utiliser un outil de dessin

L' **éditeur d’images** contient des outils de dessin et d’effacement FreeHand qui fonctionnent tous de la même façon. Vous sélectionnez l’outil et, si nécessaire, vous sélectionnez les couleurs de premier plan et d' [arrière-plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) , ainsi que les options de taille et de forme. Vous déplacez ensuite le pointeur vers l’image, puis cliquez ou faites glisser pour dessiner et effacer.

## <a name="drawing-tools"></a>Outils de dessin

Vous pouvez sélectionner des outils de dessin à partir de la barre d’outils **éditeur d’images** ou du menu **image** . Lorsque vous sélectionnez l’outil **gomme** , outil **pinceau** ou **aérographe** , le sélecteur d’option affiche les options de cet outil.

> [!TIP]
>  Les info-bulles s’affichent lorsque vous pointez votre curseur sur les boutons de la [barre d’outils de l’éditeur d’images](../windows/toolbar-image-editor-for-icons.md). Ces conseils vous aideront à identifier les boutons spécifiques mentionnés ici.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Pour sélectionner et utiliser un outil de dessin à partir de la barre d’outils de l’éditeur d’images

1. Sélectionnez un bouton dans la barre d’outils de l' **éditeur d’images** .

   - L’outil **gomme** peint sur l’image avec la couleur d’arrière-plan actuelle lorsque vous appuyez sur le bouton gauche de la souris.

      > [!TIP]
      > Au lieu d’utiliser l’outil **gomme** , il peut s’avérer plus pratique de dessiner dans la couleur d’arrière-plan avec l’un des outils de dessin.

   - L’outil **crayon** dessine FreeHand dans une largeur constante d’un pixel.

   - L’outil **pinceau** a différentes formes et tailles.

   - L’outil **aérographe** distribue aléatoirement les pixels de couleur autour du centre du pinceau.

1. Si nécessaire, sélectionnez les couleurs et un pinceau :

   - Dans la [palette de couleurs](../windows/colors-window-image-editor-for-icons.md), sélectionnez le bouton gauche de la souris pour sélectionner une couleur de premier plan ou le bouton droit de la souris pour sélectionner une couleur d’arrière-plan.

   - Dans le [Sélecteur d’options](../windows/toolbar-image-editor-for-icons.md), sélectionnez une forme représentant le pinceau que vous souhaitez utiliser.

1. Pointez sur l’emplacement de l’image où vous souhaitez commencer le dessin ou la peinture. Le pointeur change de forme en fonction de l’outil que vous avez sélectionné.

1. Appuyez sur le bouton gauche de la souris (pour la couleur de premier plan) ou sur le bouton droit de la souris (pour la couleur d’arrière-plan) et maintenez-le enfoncé pendant que vous dessinez.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Pour sélectionner et utiliser un outil de dessin à partir du menu image

1. Accédez à l' **image** de menu > **Outils**.

1. Dans le sous-menu en cascade, choisissez l’outil que vous souhaitez utiliser.

## <a name="lines-or-closed-figures"></a>Lignes ou figures fermées

Les outils de l' **éditeur d’images** permettant de dessiner des lignes et des figures fermées fonctionnent tous de la même façon : vous placez le point d’insertion à un point et faites glisser vers un autre. Pour les lignes, ces points sont les points de terminaison. Pour les figures fermées, ces points sont les angles opposés d’un rectangle englobant l’illustration.

Les lignes sont dessinées dans une largeur déterminée par la sélection de pinceau actuelle, et les figures encadrées sont dessinées dans une largeur déterminée par la sélection de largeur actuelle. Les lignes et toutes les figures, à la fois encadrées et remplies, sont dessinées dans la couleur de premier plan actuelle si vous appuyez sur le bouton gauche de la souris ou dans la couleur d’arrière-plan actuelle si vous appuyez sur le bouton droit de la souris.

### <a name="to-draw-a-line"></a>Pour dessiner une ligne

1. Utilisez la [barre d’outils de l’éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ou accédez à l' **image** de menu> **Outils** et choisissez l’outil **trait** .

1. Si nécessaire, sélectionnez les couleurs et un pinceau :

   - Dans la [palette de couleurs](../windows/colors-window-image-editor-for-icons.md), sélectionnez le bouton gauche de la souris pour sélectionner une couleur de premier plan ou le bouton droit de la souris pour sélectionner une couleur d’arrière-plan.

   - Dans le [Sélecteur d’options](../windows/toolbar-image-editor-for-icons.md), sélectionnez une forme représentant le pinceau que vous souhaitez utiliser.

1. Placez le pointeur au point de départ de la ligne.

1. Faites glisser vers le point de terminaison de la ligne.

### <a name="to-draw-a-closed-figure"></a>Pour dessiner une figure fermée

1. Utilisez la barre d’outils de l' **éditeur d’images** ou accédez à l' **image** de menu > **Outils** et sélectionnez un outil de **dessin de figure fermé** .

   Les outils de **dessin de la figure fermée** créent des figures comme indiqué sur leurs boutons respectifs.

1. Si nécessaire, sélectionnez les couleurs et une largeur de ligne.

1. Déplacez le pointeur vers un coin de la zone rectangulaire dans laquelle vous souhaitez dessiner la figure.

1. Faites glisser le pointeur vers le coin opposé en diagonale.

## <a name="custom-brushes"></a>Pinceaux personnalisés

Un pinceau personnalisé est une partie rectangulaire d’une image que vous sélectionnez et utilisez comme l’une des pinces prédéfinies de l' **éditeur d’images**. Toutes les opérations que vous pouvez effectuer sur une sélection, vous pouvez également effectuer sur un pinceau personnalisé.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Pour créer un pinceau personnalisé à partir d’une partie d’une image

1. Sélectionnez la partie de l’image que vous souhaitez utiliser pour un pinceau.

1. Maintenez la touche **MAJ** enfoncée, choisissez dans la sélection et faites-la glisser sur l’image, ou accédez à l' **image** de menu > **Utilisez la sélection comme pinceau**.

   Votre sélection devient un pinceau personnalisé qui répartit les couleurs de la sélection sur l’image. Les copies de la sélection sont conservées le long du tracé de glissement. Plus le déplacement est lent, plus les copies sont effectuées.

   > [!NOTE]
   > Si vous sélectionnez l’option **utiliser une sélection comme pinceau** sans sélectionner au préalable une partie de l’image, la totalité de l’image est utilisée comme pinceau. Le résultat de l’utilisation d’un pinceau personnalisé varie également selon que vous avez sélectionné un [arrière-plan opaque ou transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Les pixels d’un pinceau personnalisé qui correspondent à la couleur d’arrière-plan actuelle sont normalement transparents : ils ne se dessinent pas sur l’image existante. Vous pouvez modifier ce comportement afin que les pixels de couleur d’arrière-plan dessinent sur l’image existante.

Vous pouvez utiliser le pinceau personnalisé comme un tampon ou un gabarit pour créer différents effets spéciaux.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Pour dessiner des formes de pinceau personnalisées dans la couleur d’arrière-plan

1. Sélectionnez un arrière-plan opaque ou transparent.

1. Définissez la couleur d’arrière-plan sur la couleur dans laquelle vous souhaitez dessiner.

1. Placez le pinceau personnalisé à l’endroit où vous souhaitez dessiner.

1. Sélectionnez le bouton droit de la souris. Toutes les zones opaques du pinceau personnalisé sont dessinées dans la couleur d’arrière-plan.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Pour doubler ou diviser la taille de pinceau personnalisée

Appuyez sur la touche signe **plus** ( **+** ) pour doubler la taille du pinceau, ou sur la touche signe **moins** ( **-** ) pour la diviser.

### <a name="to-cancel-the-custom-brush"></a>Pour annuler le pinceau personnalisé

Appuyez sur **Échap** ou choisissez un autre outil de dessin.

## <a name="requirements"></a>Spécifications

None

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Comment : créer une icône ou une autre image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Comment : modifier une image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Comment : utiliser la couleur](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
