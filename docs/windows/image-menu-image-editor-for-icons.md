---
title: Menu image (Éditeur d’images C++ pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
helpviewer_keywords:
- Image menu
- Grid Settings dialog box [C++]
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
ms.openlocfilehash: e7d7d92401d5910cbb8aba8ab4c6000eca45cb01
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849728"
---
# <a name="image-menu-c-image-editor-for-icons"></a>Menu image (Éditeur d’images C++ pour les icônes)

Le **Image** menu qui s’affiche uniquement lorsque le **Image** éditeur est actif, qu’il dispose des commandes pour modifier les images, la gestion des palettes de couleurs et la définition **Éditeur d’images** fenêtre Options. En outre, les commandes pour l’utilisation des images de périphérique sont disponibles lorsque vous travaillez avec des icônes et des curseurs.

|Commande|Description|
|---|---|
|**Couleurs inversées**|Inverse les couleurs. Pour plus d’informations, consultez [inversion des couleurs dans une sélection](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).|
|**Symétrie horizontale**|Retourne l'image ou la sélection horizontalement. Pour plus d’informations, consultez [retournement d’une Image](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Symétrie verticale**|Retourne l'image ou la sélection verticalement. Pour plus d’informations, consultez [retournement d’une Image](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Faire pivoter de 90 degrés**|Fait pivoter l'image ou la sélection de 90 degrés. Pour plus d’informations, consultez [retournement d’une Image](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Afficher la fenêtre couleurs**|Ouvre le [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md), dans laquelle vous pouvez choisir les couleurs à utiliser pour votre image. Pour plus d’informations, consultez [utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md).|
|**Utiliser la sélection comme pinceau**|Vous permet de créer un pinceau personnalisé à partir d’une partie d’une image. Votre sélection devient un pinceau personnalisé qui distribue les couleurs dans la sélection sur l’image. Copies de la sélection sont laissées sur le tracé de glissement. Vous faites glisser plus lentement, le nombre de copies est effectuées. Pour plus d’informations, consultez [création d’un pinceau personnalisé](../windows/creating-a-custom-brush-image-editor-for-icons.md).|
|**Copie et sélection de la structure**|Crée une copie de la sélection actuelle et met un contour. Si la couleur d’arrière-plan est contenue dans la sélection actuelle, celle-ci sera exclue si vous avez [transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) sélectionné.
|**Ajuster les couleurs**|Ouvre le [sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), qui vous permet de personnaliser les couleurs à utiliser pour votre image. Pour plus d’informations, consultez [personnalisation ou modification des couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md).|
|**Charger la Palette**|Ouvre le [boîte de dialogue Charger la Palette de couleurs](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), ce qui vous permet de charger la palette de couleurs précédemment enregistré dans un fichier .pal.|
|**Enregistrer la Palette**|Enregistre la palette de couleurs d’un fichier .pal.|
|**Dessin Opaque**|Cette option convertit la sélection actuelle opaque. Lorsqu’elle est désactivée, rend transparente la sélection actuelle. Pour plus d’informations, consultez [en choisissant un arrière-plan Transparent ou Opaque](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|**Éditeur de barres d’outils**|Ouvre le [boîte de dialogue Nouvelle ressource de barre d’outils](../windows/new-toolbar-resource-dialog-box.md).|
|**Paramètres de la grille**|Ouvre le **paramètres de la grille** boîte de dialogue dans laquelle vous pouvez spécifier des grilles pour votre image.|
|**Nouveau Type d’Image**|Ouvre le [New \<appareil > boîte de dialogue Type d’Image](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Une ressource icône unique peut contenir plusieurs images de différentes tailles et windows puisse utiliser la taille d’icône appropriée en fonction de la façon dont elle va être affiché. Un nouveau type d’appareil ne modifie pas la taille de l’icône, mais crée une nouvelle image au sein de l’icône. S’applique uniquement aux icônes et des curseurs.|
|**Type d’Image icône/curseur actuel**|Ouvre un sous-menu qui répertorie les premier curseur ou icône images disponibles (les neuf premières). La dernière commande dans le sous-menu, **plus...** , ouvre le [Open \<appareil > boîte de dialogue Image](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Supprimer le Type d’Image**|Supprime l’image de périphérique sélectionné.|
|**Outils**|Lance un sous-menu contenant tous les outils disponibles à partir de la [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md).|

Le **paramètres de la grille** boîte de dialogue vous permet de spécifier les paramètres de grille pour votre image et affiche les lignes de la grille sur l’image modifiée. Les lignes sont utiles pour la modification de l’image, mais ne sont pas enregistrées dans le cadre de l’image elle-même.

|Propriété|Description|
|---|---|
|**Grille de pixels**|Lorsqu’elle est activée, affiche une grille autour de chaque pixel dans l’éditeur d’images. La grille s’affiche uniquement 4 × et résolutions plus élevées.|
|**Grille mosaïque**|Lorsque sélectionné, affiche une grille autour des blocs de pixels dans l’éditeur d’images, spécifié par les valeurs d’espacement de grille.|
|**Width**|Spécifie la largeur de chaque bloc. Cette propriété est utile lors du dessin de bitmaps qui contiennent plusieurs images sont organisées à intervalles réguliers.|
|**Height**|Spécifie la hauteur de chaque bloc. Cette propriété est utile lors du dessin de bitmaps qui contiennent plusieurs images sont organisées à intervalles réguliers.|

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Redimensionnement d’une Image](../windows/resizing-an-image-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)