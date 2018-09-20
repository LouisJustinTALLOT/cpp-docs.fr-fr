---
title: L’enregistrement et chargement de différentes Palettes de couleurs (Image éditeur pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50e74c65e080b11583e6ff1e591ef612b17e9533
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438884"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Enregistrement et chargement de différentes palettes de couleurs (Éditeur d'images pour les icônes)

Vous pouvez enregistrer et charger un **couleurs** palette contienne [personnalisé couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Par défaut, le **couleurs** palette plus récemment utilisée est automatiquement chargé lorsque vous démarrez Visual Studio.)

> [!TIP]
> Dans la mesure où le **Image** éditeur n’a aucun moyen pour restaurer la valeur par défaut **couleurs** palette, vous devez enregistrer la valeur par défaut **couleurs** palette sous un nom tel que  *standard.PAL* ou *defaut.PAL* afin que vous pouvez facilement restaurer les paramètres par défaut.

### <a name="to-save-a-custom-colors-palette"></a>Pour enregistrer une palette de couleurs personnalisées

1. À partir de la **Image** menu, choisissez **enregistrer la Palette**.

2. Accédez au répertoire où vous souhaitez enregistrer la palette, puis tapez le nom de cette dernière.

3. Cliquez sur **Enregistrer**.

### <a name="to-load-a-custom-colors-palette"></a>Pour charger une palette de couleurs personnalisées

1. À partir de la **Image** menu, choisissez **charger la Palette**.

2. Dans le [boîte de dialogue Charger la Palette de couleurs](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), accédez au répertoire approprié et sélectionnez la palette à charger. **Couleur** palettes sont enregistrés avec une extension de fichier .pal.

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md)