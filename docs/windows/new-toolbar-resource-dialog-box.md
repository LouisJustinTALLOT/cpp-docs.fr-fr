---
title: Nouvelle ressource de barre d’outils, boîte de dialogue | Microsoft Docs
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
ms.openlocfilehash: 6952fa51115d5bec9650ef6d6012e3c7aff2d127
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602168"
---
# <a name="new-toolbar-resource-dialog-box"></a>Nouvelle ressource de barre d'outils (boîte de dialogue)

Le **nouvelle ressource de barre d’outils** boîte de dialogue vous permet de spécifier la largeur et la hauteur des boutons que vous ajoutez à une ressource de barre d’outils. La valeur par défaut est 16 x 15 pixels.

Une image bitmap qui sert à créer une barre d’outils a une largeur maximale de 2048. Par conséquent, si vous définissez la **la largeur du bouton** à 512, vous ne pouvez avoir quatre boutons. Si vous définissez la largeur à 513, peut uniquement avoir trois boutons.

### <a name="button-width"></a>Largeur du bouton

Fournit un espace vous permettant d’entrer la largeur pour les boutons de barre d’outils que vous convertissez à partir d’une ressource bitmap à une ressource de barre d’outils. Les images sont rognées à la largeur et la hauteur spécifiée, et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).

### <a name="button-height"></a>Hauteur du bouton

Fournit un espace vous permettant d’entrer la hauteur pour les boutons de barre d’outils que vous convertissez à partir d’une ressource bitmap à une ressource de barre d’outils. Les images sont rognées à la largeur et la hauteur spécifiée, et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[propriétés d’un bouton de barre d’outils](../windows/toolbar-button-properties.md)  
[Conversion de bitmaps en barres d’outils](../windows/converting-bitmaps-to-toolbars.md)  
[Éditeur de barres d’outils](../windows/toolbar-editor.md)