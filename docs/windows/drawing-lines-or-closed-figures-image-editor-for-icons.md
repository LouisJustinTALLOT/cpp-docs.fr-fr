---
title: Dessin de ligne ou de figures fermées (Éditeur d'images pour les icônes)
ms.date: 11/04/2016
helpviewer_keywords:
- Image editor [C++], drawing lines
- shapes, drawing
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
ms.openlocfilehash: a33376529faadd2433f704505aa0be8d4cc03033
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449073"
---
# <a name="drawing-lines-or-closed-figures-image-editor-for-icons"></a>Dessin de ligne ou de figures fermées (Éditeur d'images pour les icônes)

Outils de l’éditeur d’images pour dessiner des lignes et de figures fermées fonctionnent tous de la même façon : vous placez le point d’insertion à un moment donné et que vous faites glisser vers un autre. Pour les lignes, ces points sont les points de terminaison. Pour les figures fermées, ces points sont les angles opposés du rectangle englobant de la figure.

Les lignes sont dessinées dans une largeur déterminée par la sélection de pinceau actuelle et les figures encadrées sont dessinées dans une largeur déterminée par la sélection de la largeur actuelle. Toutes les figures, encadrées et remplies et les lignes sont dessinées dans la couleur de premier plan actuelle si vous appuyez sur le bouton gauche de la souris, ou dans la couleur d’arrière-plan actuelle si vous appuyez sur le bouton droit de la souris.

### <a name="to-draw-a-line"></a>Pour dessiner une ligne

1. Sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) (ou à partir de la **Image** menu, **outils** commande), cliquez sur le **ligne** outil.

2. Si nécessaire, sélectionnez les couleurs et un pinceau :

   - Dans le [palette de couleurs](../windows/colors-window-image-editor-for-icons.md), cliquez sur le bouton gauche de la souris pour sélectionner une couleur de premier plan ou le bouton droit de la souris pour sélectionner une couleur d’arrière-plan.

   - Dans le [sélecteur d’Options](../windows/toolbar-image-editor-for-icons.md), cliquez sur une forme qui représente le pinceau à utiliser.

3. Placez le pointeur au début de la ligne.

4. Faites glisser vers le point de terminaison de la ligne.

### <a name="to-draw-a-closed-figure"></a>Pour dessiner une figure fermée

1. Sur le **Éditeur d’images** barre d’outils (ou à partir de la **Image** menu, **outils** commande), cliquez sur un **Figure fermée dessin** outil.

   Le **Figure fermée dessin** outils créent des figures comme indiqué par leur bouton respectif.

2. Si nécessaire, sélectionnez les couleurs et une largeur de ligne.

3. Placez le pointeur sur un coin de la zone rectangulaire dans laquelle vous souhaitez dessiner la figure.

4. Faites glisser le pointeur vers le coin en diagonale opposé.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md)