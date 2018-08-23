---
title: Conversion de Bitmaps en barres d’outils | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5524b1d5ecb3fa4de38f46706f26d2a318fe5ef
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602398"
---
# <a name="converting-bitmaps-to-toolbars"></a>Conversion de bitmaps en barres d'outils

Vous pouvez créer une nouvelle barre d’outils en convertissant une image bitmap. Le graphique à partir de l’image bitmap convertit les images du bouton d’une barre d’outils. L’image bitmap contient généralement plusieurs images de bouton sur une seule bitmap, avec une seule image pour chaque bouton. Images peuvent être n’importe quelle taille ; la valeur par défaut est 16 pixels de large et la hauteur de l’image. Vous pouvez spécifier la taille des images de bouton dans le [boîte de dialogue Nouvelle ressource de barre d’outils](../windows/new-toolbar-resource-dialog-box.md) lorsque vous choisissez **barre d’outils Éditeur** à partir de la **Image** menu dans l’éditeur d’images.

### <a name="to-convert-bitmaps-to-a-toolbar"></a>Pour convertir des bitmaps en une barre d’outils

1. Ouvrez une ressource bitmap existante dans le [Éditeur d’images](../windows/image-editor-for-icons.md). (Si la bitmap n’est pas déjà dans votre fichier .rc, cliquez sur le fichier .rc, choisissez **importation** dans le menu contextuel, accédez à l’image bitmap que vous souhaitez ajouter à votre fichier .rc, puis cliquez sur **Open**.)

2. À partir de la **Image** menu, choisissez **barre d’outils Éditeur**.

   Le [boîte de dialogue Nouvelle ressource de barre d’outils](../windows/new-toolbar-resource-dialog-box.md) s’affiche. Vous pouvez modifier la largeur et la hauteur des images d’icône pour faire correspondre l’image bitmap. L’image de la barre d’outils s’affiche ensuite dans l’éditeur de la barre d’outils.

3. Pour terminer la conversion, modifiez la commande **ID** du bouton en utilisant la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Tapez le nouveau **ID** ou sélectionnez un **ID** dans la liste déroulante.

   > [!TIP]
   > Le **propriétés** fenêtre contient un bouton punaise dans la barre de titre. Cliquez sur ce bouton Active ou désactive **Masquer automatiquement** pour la fenêtre. Pour parcourir rapidement toutes les propriétés de bouton de barre d’outils sans rouvrir les fenêtres de propriétés individuelles, activer **Masquer automatiquement** désactivé afin que la **propriétés** fenêtre reste visible.

Vous pouvez également modifier les ID de commande des boutons sur la nouvelle barre d’outils à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Pour plus d’informations sur la modification de la nouvelle barre d’outils, consultez [création, déplacement et modification de boutons de barre d’outils](../windows/creating-moving-and-editing-toolbar-buttons.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Création de nouvelles barres d’outils](../windows/creating-new-toolbars.md)  
[Éditeur de barres d’outils](../windows/toolbar-editor.md)