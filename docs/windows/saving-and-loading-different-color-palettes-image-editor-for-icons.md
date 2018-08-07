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
ms.openlocfilehash: 14cad19c53e8cd741bf16bab49420169e93f6af6
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606970"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Enregistrement et chargement de différentes palettes de couleurs (Éditeur d'images pour les icônes)
Vous pouvez enregistrer et charger une palette de couleurs qui contient [personnalisé couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Par défaut, la palette de couleurs utilisée en dernier est automatiquement chargée quand vous démarrez Visual Studio.)  
  
> [!TIP]
>  Dans la mesure où l'éditeur d'images n'a aucun moyen de rétablir la palette de couleurs par défaut, vous devez enregistrer la palette de couleurs par défaut sous un nom tel que standard.pal ou defaut.pal pour pouvoir restaurer facilement les paramètres par défaut.  
  
### <a name="to-save-a-custom-colors-palette"></a>Pour enregistrer une palette de couleurs personnalisées  
  
1.  À partir de la **Image** menu, choisissez **enregistrer la Palette**.  
  
2.  Accédez au répertoire où vous souhaitez enregistrer la palette, puis tapez le nom de cette dernière.  
  
3.  Cliquez sur **Enregistrer**.  
  
### <a name="to-load-a-custom-colors-palette"></a>Pour charger une palette de couleurs personnalisées  
  
1.  À partir de la **Image** menu, choisissez **charger la Palette**.  
  
2.  Dans le [boîte de dialogue Charger la Palette de couleurs](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), accédez au répertoire approprié et sélectionnez la palette à charger. Les palettes de couleurs sont enregistrées avec une extension de fichier .pal.  
  
## <a name="requirements"></a>Configuration requise  
  
 Aucun.  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md)