---
title: Enregistrement et chargement de différentes palettes de couleurs (Éditeur d'images pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.color
- vc.editors.loadcolorpalette
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
ms.openlocfilehash: fd2664407d33d8e3ed594921501b7f80e6c8850b
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560268"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Enregistrement et chargement de différentes palettes de couleurs (Éditeur d'images pour les icônes)

Vous pouvez enregistrer et charger un **couleurs** palette contienne [personnalisé couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Par défaut, le **couleurs** palette plus récemment utilisée est automatiquement chargé lorsque vous démarrez Visual Studio.)

> [!TIP]
> Dans la mesure où le **Image** éditeur n’a aucun moyen pour restaurer la valeur par défaut **couleurs** palette, vous devez enregistrer la valeur par défaut **couleurs** palette sous un nom tel que  *standard.PAL* ou *defaut.PAL* afin que vous pouvez facilement restaurer les paramètres par défaut.

Utiliser le **charger les couleurs de Palette** boîte de dialogue pour charger des palettes de couleurs spécial à utiliser dans votre projet C++. Les propriétés suivantes incluses sont :

|Propriété|Description|
|---|---|
|**Regarder dans**|Spécifie l’emplacement où vous souhaitez localiser un fichier ou dossier. Sélectionnez la flèche pour choisir un autre emplacement, ou sélectionnez l’icône de dossier dans la barre d’outils pour déplacer les niveaux.|
|**Nom de fichier**|Offre un espace vous permettant de taper le nom du fichier que vous souhaitez ouvrir. Pour trouver rapidement un fichier que vous avez déjà ouvert, sélectionnez le nom de fichier dans la liste déroulante, si elle est disponible.<br/><br/>Si vous recherchez un fichier, vous pouvez utiliser des astérisques (*) comme caractères génériques. Par exemple, vous pouvez taper \*.\* pour afficher la liste de tous les fichiers. Vous pouvez également taper le chemin d’accès complet d’un fichier, par exemple, C:\My Documents\MyColorPalette.PAL ou \\\NetworkServer\MyFolder\MyColorPalette.pal.|
|**Types de fichiers**|Répertorie les types de fichiers à afficher. Palette (* .pal) est le type de fichier par défaut pour les palettes de couleurs.|

## <a name="to-save-a-custom-colors-palette"></a>Pour enregistrer une palette de couleurs personnalisées

1. À partir de la **Image** menu, choisissez **enregistrer la Palette**.

1. Accédez au répertoire où vous souhaitez enregistrer la palette, puis tapez le nom de cette dernière.

1. Sélectionnez **Enregistrer**.

## <a name="to-load-a-custom-colors-palette"></a>Pour charger une palette de couleurs personnalisées

1. À partir de la **Image** menu, choisissez **charger la Palette**.

1. Dans le **charger la Palette de couleurs** boîte de dialogue zone, accédez au répertoire approprié et sélectionnez la palette à charger. **Couleur** palettes sont enregistrés avec une extension de fichier .pal.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)