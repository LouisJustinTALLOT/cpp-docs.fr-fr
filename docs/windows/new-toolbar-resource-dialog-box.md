---
title: Nouvelle ressource de barre d’outils, boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newtoolbarresource
dev_langs:
- C++
helpviewer_keywords:
- New Toolbar Resource dialog box
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6662fcfab3c9bb1d805e39147bd2838e6bbce5b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877538"
---
# <a name="new-toolbar-resource-dialog-box"></a>Nouvelle ressource de barre d'outils (boîte de dialogue)
La boîte de dialogue Nouvelle ressource de barre d’outils vous permet de spécifier la largeur et la hauteur des boutons que vous ajoutez à une ressource de barre d’outils. La valeur par défaut est 16 x 15 pixels.  
  
 Une image bitmap qui est utilisée pour créer une barre d’outils a une largeur maximale de 2048. Par conséquent, si vous définissez la **largeur du bouton** à 512, vous ne pouvez avoir quatre boutons. Si vous définissez la largeur à 513, vous pouvez avoir uniquement trois boutons.  
  
 **Largeur du bouton**  
 Offre un espace vous permettant d’entrer la largeur pour les boutons de barre d’outils que vous convertissez une ressource bitmap à une ressource de barre d’outils. Les images sont rognées à la largeur et la hauteur spécifiées et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).  
  
 **Hauteur du bouton**  
 Offre un espace vous permettant d’entrer la hauteur pour les boutons de barre d’outils que vous convertissez une ressource bitmap à une ressource de barre d’outils. Les images sont rognées à la largeur et la hauteur spécifiées et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 MFC ou ATL  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de bouton de barre d’outils](../windows/toolbar-button-properties.md)   
 [Conversion de Bitmaps en barres d’outils](../windows/converting-bitmaps-to-toolbars.md)   
 [Éditeur de barres d’outils](../windows/toolbar-editor.md)

