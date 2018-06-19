---
title: Création de régions transparentes ou inversées dans des Images de périphérique (Éditeur d’images pour les icônes) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors, device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices, transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects, transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70fd2411eefba495478baaf5fb20fe7a27031001
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882548"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>Création de régions transparentes ou inversées dans des images de périphérique (Éditeur d'images pour les icônes)
Dans le [Éditeur d’images](../windows/image-editor-for-icons.md), l’image d’icône ou curseur a un attribut transparent. Bien que les images d’icône et de curseur sont rectangulaires, nombreux n’apparaissent pas, car les parties de l’image sont transparentes ; l’image sous-jacente à l’écran montre via l’icône ou le curseur. Lorsque vous faites glisser une icône, les parties de l’image peuvent apparaître dans une couleur inversée. Vous créez cet effet en définissant la couleur d’écran et inverse dans le [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).  
  
 Les couleurs de l’écran et inverse s’appliquent pour les icônes et curseurs mettre en forme et colorer l’image dérivée ou désignent les régions inversées. Les couleurs indiquent les parties de l’image qui possèdent ces attributs. Vous pouvez modifier les couleurs qui représentent les attributs de couleur d’écran et couleur inversée lors de la modification. Ces modifications n’affectent pas l’apparence de l’icône ou le curseur dans votre application.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-transparent-or-inverse-regions"></a>Pour créer des régions transparentes ou inversées  
  
1.  Dans le **couleurs** fenêtre, cliquez sur le **couleur d’écran** sélecteur ou **couleur inversée** sélecteur.  
  
2.  Appliquer l’écran ou la couleur inversée à votre image à l’aide d’un outil de dessin. Pour plus d’informations sur les outils de dessin, consultez [à l’aide d’un outil de dessin](using-a-drawing-tool-image-editor-for-icons.md).  
  
### <a name="to-change-the-screen-or-inverse-color"></a>Pour modifier la couleur d’écran ou inverse  
  
1.  Sélectionnez le **couleur d’écran** sélecteur ou **couleur inversée** sélecteur.  
  
2.  Choisissez une couleur dans le **couleurs** palette dans le **couleurs** fenêtre.  
  
     La couleur complémentaire est automatiquement désignée pour l’autre sélecteur.  
  
    > [!TIP]
    >  Si vous double-cliquez sur le sélecteur Couleur d’écran ou la couleur inversée, le [boîte de dialogue Sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) s’affiche.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Icônes et curseurs : ressources Image pour les périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

