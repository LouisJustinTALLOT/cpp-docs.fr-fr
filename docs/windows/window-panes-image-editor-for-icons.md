---
title: Volets de fenêtre (Éditeur d'images pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
ms.openlocfilehash: 72b7cf056147cdbd216d861f0e710da423951c5a
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560307"
---
# <a name="window-panes-image-editor-for-icons"></a>Volets de fenêtre (Éditeur d'images pour les icônes)

Le **Éditeur d’images** fenêtre affiche une image en général deux volets séparés par une barre de fractionnement. Une vue est la taille réelle et l’autre est agrandie (facteur d’agrandissement de la valeur par défaut est 6). Les vues dans ces deux volets sont mis à jour automatiquement : les modifications apportées dans un volet sont immédiatement répercutées dans l’autre. Les deux volets facilitent vous permettent de travailler sur une vue agrandie de votre image, dans laquelle vous pouvez distinguer les pixels et, en même temps, observer l’effet de votre travail sur la vue de la taille réelle de l’image.

Le volet gauche utilise autant d’espace nécessaire (la moitié de la **Image** fenêtre) pour afficher la vue 1:1 facteur d’agrandissement (il s’agit de la valeur par défaut) de votre image. Le volet droit affiche l’image agrandie (facteur d’agrandissement 6:1 par défaut). Vous pouvez modifier le facteur d’agrandissement dans chaque volet en utilisant le **Magnify** outil sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ou en utilisant les touches accélérateur.

Vous pouvez agrandir le volet de plus petites de la **Éditeur d’images** fenêtre et utiliser les deux volets pour afficher différentes zones d’une grande image. Sélectionnez cette option dans le volet pour le choisir.

Vous pouvez modifier les tailles relatives des volets en plaçant le pointeur sur la barre de fractionnement et de déplacement de la barre de fractionnement vers la droite ou la gauche. La barre de fractionnement peut déplacer jusqu’au côté, si vous souhaitez travailler sur un seul volet.

Si le **Éditeur d’images** est agrandie par un facteur de 4 ou version ultérieure, vous pouvez afficher une grille de pixels qui délimite les pixels individuels dans l’image.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-change-the-magnification-factor"></a>Pour modifier le facteur d’agrandissement

Par défaut, le **Image** éditeur affiche la vue dans le volet de gauche en taille réelle la vue dans le volet droit à 6 heures et taille réelle. Le facteur d’agrandissement (indiqué dans la barre d’état en bas de l’espace de travail) est le rapport entre la taille réelle de l’image et la taille affichée. Le facteur par défaut est 6 et la plage est comprise entre 1 et 10.

1. Sélectionnez le **Éditeur d’images** volet dont vous souhaitez modifier le facteur d’agrandissement.

1. Sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md), sélectionnez la flèche à droite de la [outil Loupe](../windows/toolbar-image-editor-for-icons.md) et sélectionnez le facteur d’agrandissement dans le sous-menu : **1 X**, **2 X**, **6 X**, ou **8 X**.

   > [!NOTE]
   > Pour sélectionner un facteur d’agrandissement autre que ceux répertoriés dans le **Magnify** outil, utilisez les touches accélérateur.

## <a name="to-display-or-hide-the-pixel-grid"></a>Pour afficher ou masquer la grille de pixels

Pour toutes les **Éditeur d’images** volets avec un facteur d’agrandissement ou supérieure à 4, vous pouvez afficher une grille qui délimite les pixels individuels dans l’image.

1. Sur le **Image** menu, sélectionnez **paramètres de la grille**.

1. Sélectionnez le **grille de pixels** case à cocher pour afficher la grille, ou désactivez la case pour masquer la grille.

> [!TIP]
> Info-bulles s’affichent lorsque vous placez votre curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)