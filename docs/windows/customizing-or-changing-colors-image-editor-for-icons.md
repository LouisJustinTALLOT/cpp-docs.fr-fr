---
title: Personnalisation ou modification des couleurs (Éditeur d'images pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.customcolorselector
helpviewer_keywords:
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
ms.assetid: e58f6b32-f435-4d9a-a570-7569433661ae
ms.openlocfilehash: 7ab353ad0aa22c74eeba58e9310d9bc0f8d5a832
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560281"
---
# <a name="customizing-or-changing-colors-image-editor-for-icons"></a>Personnalisation ou modification des couleurs (Éditeur d'images pour les icônes)

Le **Image** mot du rédacteur [palette de couleurs](../windows/colors-window-image-editor-for-icons.md) affiche initialement 16 couleurs standard. Avec les couleurs affichées, vous pouvez également créer vos propres couleurs personnalisées. Vous pouvez ensuite [enregistrer et charger une palette de couleurs personnalisée](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md).

Le **sélecteur de couleurs personnalisées** boîte de dialogue vous permet de personnaliser les couleurs à utiliser pour votre image. Les propriétés suivantes incluses sont :

|Propriété|Description|
|---|---|
|**Affichage de la couleur de dégradé**|Modifie les valeurs de la couleur sélectionnée. Positionner la croix sur la couleur que vous souhaitez modifier. Puis déplacez le curseur que vers le haut ou bas pour modifier la luminosité ou les valeurs RVB de la couleur.|
|**Barre de luminosité**|Définit la luminosité de la couleur que vous sélectionnez dans la **affichage des dégradés de couleur** boîte. Sélectionnez et faites glisser la flèche blanche de la barre de luminosité supérieure ou vers le bas à moindre coût. Le **couleur** zone affiche la couleur que vous avez sélectionné et l’effet de la luminosité que vous définissez.|
|**Color**|Répertorie la teinte (valeur de roue de couleur) de la couleur que vous définissez. Les valeurs comprises entre 0 et 240, où 0 est rouge, 60 est jaune, 120 est vert, 180 est cyan, 200 est magenta et 240 est bleu.|
|**HUE**|Répertorie la teinte (valeur de roue de couleur) de la couleur que vous définissez. Les valeurs comprises entre 0 et 240, où 0 est rouge, 60 est jaune, 120 est vert, 180 est cyan, 200 est magenta et 240 est bleu.|
|**Sat**|Spécifie la valeur de saturation de la couleur que vous définissez. Saturation correspond à la quantité de couleur dans une teinte spécifiée. Les valeurs comprises entre 0 et 240.|
|**Lum**|Répertorie la luminosité de la couleur que vous définissez. Les valeurs comprises entre 0 et 240.|
|**Rouge**|Spécifie la valeur rouge de la couleur que vous définissez. Les valeurs comprises entre 0 et 255.|
|**Vert**|Spécifie la valeur verte de la couleur que vous définissez. Les valeurs comprises entre 0 et 255.|
|**Blue**|Spécifie la valeur bleue de la couleur que vous définissez. Les valeurs comprises entre 0 et 255.|

## <a name="to-change-colors-on-the-colors-palette"></a>Pour changer les couleurs de la palette de couleurs

1. À partir de la **Image** menu, choisissez **ajuster les couleurs**.

1. Dans le **sélecteur de couleurs personnalisées** boîte de dialogue zone, définir la couleur en tapant des valeurs RVB ou TSL dans les zones appropriées ou choisissez une couleur dans le **affichage des dégradés de couleur** boîte.

1. Définissez la luminosité en déplaçant le curseur le **luminosité** barre.

1. De nombreuses couleurs personnalisées sont tramées. Si vous souhaitez la couleur unie la plus proche de la couleur tramée, double-cliquez sur le **couleur** boîte.

   Si vous décidez plus tard vous voulez que la couleur tramée, déplacez le curseur le **luminosité** à barres ou déplacez le réticule le **affichage des dégradés de couleur** boîte afin de rétablir le dégradé.

1. Sélectionnez **OK** pour ajouter la nouvelle couleur.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Menu image](../windows/image-menu-image-editor-for-icons.md)<br/>
[Fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md)