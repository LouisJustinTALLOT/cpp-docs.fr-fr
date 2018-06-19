---
title: Conversion de Bitmaps en barres d’outils | Documents Microsoft
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
ms.openlocfilehash: e80bee7ef9bfe52abf63ac959475c5d8dbcf0ece
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872625"
---
# <a name="converting-bitmaps-to-toolbars"></a>Conversion de bitmaps en barres d'outils
Vous pouvez créer une nouvelle barre d’outils en convertissant une image bitmap. Le graphique de la bitmap convertit les images du bouton d’une barre d’outils. L’image bitmap contient généralement plusieurs images de bouton dans une seule bitmap, avec une image pour chaque bouton. Les images peuvent être n’importe quelle taille ; la valeur par défaut est 16 pixels de large et la hauteur de l’image. Vous pouvez spécifier la taille des images de bouton dans le [boîte de dialogue Nouvelle ressource de barre d’outils](../windows/new-toolbar-resource-dialog-box.md) lorsque vous choisissez Éditeur de barre d’outils à partir de la **Image** menu dans l’éditeur d’images.  
  
### <a name="to-convert-bitmaps-to-a-toolbar"></a>Pour convertir des bitmaps en une barre d’outils  
  
1.  Ouvrez une ressource bitmap existante dans le [Éditeur d’images](../windows/image-editor-for-icons.md). (Si l’image bitmap n’est pas déjà dans votre fichier .rc, cliquez sur le fichier .rc, choisissez **importation** dans le menu contextuel, accédez à l’image bitmap que vous souhaitez ajouter à votre fichier .rc, puis cliquez sur **ouvrir**.)  
  
2.  À partir de la **Image** menu, choisissez **barre d’outils Éditeur**.  
  
     Le [boîte de dialogue Nouvelle ressource de barre d’outils](../windows/new-toolbar-resource-dialog-box.md) s’affiche. Vous pouvez modifier la largeur et la hauteur des images d’icône pour correspondre à l’image bitmap. L’image de la barre d’outils s’affiche ensuite dans l’éditeur de la barre d’outils.  
  
3.  Pour terminer la conversion, modifiez la commande **ID** du bouton en utilisant la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Tapez le nouveau **ID** ou sélectionnez un **ID** dans la liste déroulante.  
  
    > [!TIP]
    >  La fenêtre Propriétés contient un bouton punaise dans la barre de titre. Ce bouton Active ou désactive le masquage automatique de la fenêtre. Pour parcourir rapidement toutes les propriétés de bouton de barre d’outils sans rouvrir les fenêtres des propriétés individuelles, désactivez le masquage automatique afin que la fenêtre Propriétés reste visible.  
  
 Vous pouvez également modifier les ID de commande des boutons sur la nouvelle barre d’outils à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Pour plus d’informations sur la nouvelle barre d’outils, consultez [création, déplacement et modification de boutons de barre d’outils](../windows/creating-moving-and-editing-toolbar-buttons.md).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 MFC ou ATL  
  
## <a name="see-also"></a>Voir aussi  
 [Création de nouvelles barres d’outils](../windows/creating-new-toolbars.md)   
 [Éditeur de barres d’outils](../windows/toolbar-editor.md)

