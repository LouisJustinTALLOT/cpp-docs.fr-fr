---
title: Spécifiant l’emplacement et la taille d’une boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, size
- dialog boxes, positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc4c6867f5ed3791414619257fec33db4c632553
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890575"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box"></a>Spécification de l'emplacement et de la taille d'une boîte de dialogue
L’emplacement et la taille d’une boîte de dialogue, ainsi que l’emplacement et la taille des contrôles qu’il contient, sont mesurés en unités de boîte de dialogue. Les valeurs pour les contrôles individuels et de la boîte de dialogue s’affichent dans le coin inférieur droit de l’état de Visual Studio lorsque vous les sélectionnez pas de la barre.  
  
 Il existe trois propriétés que vous pouvez définir dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour spécifier où une boîte de dialogue s’affiche à l’écran. La propriété Center est booléenne ; Si vous affectez la valeur True, la boîte de dialogue s’affiche toujours dans le centre de l’écran. Si vous la définissez sur False, vous pouvez ensuite définir les propriétés XPos et YPos pour définir explicitement l’emplacement à l’écran qu'apparaît dans la boîte de dialogue. Les propriétés de position sont des valeurs de décalage à partir de l’angle supérieur gauche de la zone d’affichage, qui est définie en tant que {X = 0, Y = 0}. La position est également basée sur la **Absolute Align** propriété : si la valeur est True, les coordonnées sont exprimées par rapport à l’écran ; si la valeur est False, les coordonnées sont exprimées par rapport à la fenêtre du propriétaire de la boîte de dialogue.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Contrôles](../mfc/controls-mfc.md)

