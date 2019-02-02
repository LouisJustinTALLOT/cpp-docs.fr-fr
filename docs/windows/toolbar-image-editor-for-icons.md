---
title: Barre d’outils (Éditeur d’images C++ pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
helpviewer_keywords:
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
ms.openlocfilehash: dfbd721afd997f3151b1c20a7e0e1fb60e0c83e4
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560320"
---
# <a name="toolbar-c-image-editor-for-icons"></a>Barre d’outils (Éditeur d’images C++ pour les icônes)

Le **Éditeur d’images** barre d’outils contient les outils de dessin, peinture, saisie de texte, effacer et manipulation des vues. Il contient également un sélecteur d’options, avec lequel vous pouvez sélectionner des options pour l’utilisation de chaque outil. Par exemple, vous pouvez choisir à partir de différentes largeurs de pinceau facteurs d’agrandissement et des styles de ligne.

> [!NOTE]
> Tous les outils disponibles sur le **Éditeur d’images** barre d’outils sont également disponibles à partir de la **Image** menu (sous le **outils** commande).

![Barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") barre d’outils Éditeur d’images

Pour utiliser le **Éditeur d’images** barre d’outils et **Option** sélecteur, sélectionnez l’outil ou l’option que vous souhaitez.

> [!TIP]
> Info-bulles s’affichent lorsque vous placez votre curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

Avec le **Option** sélecteur, vous pouvez spécifier la largeur d’une ligne, le trait de pinceau et bien plus encore. L’icône sur le **Option** sélecteur bouton change en fonction de l’outil que vous avez sélectionné.

![Dessin&#45;sélecteur de forme dans la barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") sélecteur d’options de la barre d’outils Éditeur d’images

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="use-the-text-tool-dialog-box"></a>Utilisez la boîte de dialogue Outil texte

Utilisez le **outil texte** boîte de dialogue pour ajouter du texte à une ressource curseur, bitmap ou icône.

Pour accéder à cette boîte de dialogue, ouvrez le [Éditeur d’images](../windows/window-panes-image-editor-for-icons.md). Sélectionnez **outils** à partir de la **Image** menu, puis sélectionnez le **outil texte** commande.

### <a name="font-button"></a>Bouton de police

Ouvre le **police de l’outil texte** boîte de dialogue, dans laquelle vous pouvez modifier la police, le style ou la taille de la police du curseur. Modifications sont appliquées au texte affiché dans le **texte** zone.

Pour accéder à cette boîte de dialogue, sélectionnez le **police** situé dans le **outil texte** boîte de dialogue. Les propriétés disponibles sont :

|Propriété|Description|
|---|---|
|**Police**|Répertorie les polices disponibles.|
|**Style de police**|Répertorie les styles disponibles pour la police spécifiée.|
|**Taille**|Répertorie les tailles disponibles pour la police spécifiée.|
|**Exemple**|Montre un exemple de comment le texte s’affiche avec les paramètres de police spécifiée.|
|**Script**|Répertorie les scripts de langue disponibles pour la police spécifiée. Lorsque vous sélectionnez un script de langue différente, le jeu de caractères pour cette langue devient disponible pour la création de documents multilingues.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Pour modifier la police du texte d’une image

La procédure suivante est un exemple montrant comment ajouter du texte à une icône dans une application Windows et de manipuler la police du texte.

1. Créez une Application de formulaires Windows de C++. Pour plus d’informations, consultez [création d’un projet d’Application Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5). Un *app.ico* fichier est ajouté à votre projet par défaut.

1. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier *app.ico*. Le [Éditeur d’images](../windows/image-editor-for-icons.md) s’ouvre.

1. À partir de la **Image** menu, sélectionnez **outils** , puis sélectionnez **outil texte**. Le **outil texte** boîte de dialogue s’affiche.

1. Dans le **outil texte** boîte de dialogue, tapez *C++* dans la zone de texte vide. Ce texte s’affiche dans une zone redimensionnable située dans le coin supérieur gauche de *app.ico*, dans le **Éditeur d’images**.

1. Dans le **Éditeur d’images**, faites glisser la zone redimensionnable au centre du fichier app.ico pour améliorer la lisibilité de votre texte.

1. Dans le **outil texte** boîte de dialogue, sélectionnez le **police** bouton. Le **police de l’outil texte** boîte de dialogue s’affiche.

1. Dans le **police de l’outil texte** boîte de dialogue, sélectionnez **Times New Roman** dans la liste des polices disponibles qui sont répertoriées dans le **police** zone de liste.

1. Sélectionnez **gras** dans la liste des styles de police disponibles répertoriées dans le **style de police** zone de liste.

1. Sélectionnez **10** à partir de la liste des disponibles point tailles répertoriées dans le **taille** zone de liste.

1. Sélectionnez le bouton **OK**. Le **police de l’outil texte** boîte de dialogue se ferme et les nouveaux paramètres de police s’appliquent à votre texte.

1. Sélectionnez le **fermer** bouton sur le **outil texte** boîte de dialogue. La zone redimensionnable autour du texte disparaît de la **Éditeur d’images**.

### <a name="text-area"></a>Zone de texte

Affiche le texte qui apparaît dans le cadre de la ressource. Initialement, cette zone est vide.

> [!NOTE]
> Si **arrière-plan Transparent** est défini, seul le texte sera placé dans l’image. Si **arrière-plan Opaque** est défini, un rectangle englobant, rempli avec les [couleur d’arrière-plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), seront placés derrière le texte. Pour plus d’informations, consultez [choix Opaque et arrière-plans transparents](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Vous pouvez avec le bouton droit sur le **outil texte** boîte de dialogue pour accéder à un menu de raccourci par défaut qui contient une liste de commandes Windows standard.

## <a name="to-display-or-hide-the-image-editor-toolbar"></a>Pour afficher ou masquer la barre d’outils Éditeur d’images

Dans la mesure où la plupart des outils de dessin sont disponibles à partir de la [clavier](../windows/accelerator-keys-image-editor-for-icons.md), il est parfois utile de masquer la **Éditeur d’images** barre d’outils.

Sur le **vue** menu, sélectionnez **barres d’outils** puis choisissez **Éditeur d’images**.

   > [!NOTE]
   > Éléments à partir de cette barre d’outils seront affiche pas disponibles quand un fichier image à partir du projet actuel ou la solution n’est pas ouverte dans le **Éditeur d’images**. Consultez [création d’une icône ou une autre Image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), pour plus d’informations sur l’ajout de fichiers image à vos projets.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md)<br/>
[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>