---
title: Dimensionnement de contrôles individuels | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 20dc5eb7af4195c9861d09761da245cdd5d3217d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652212"
---
# <a name="sizing-individual-controls"></a>Dimensionnement de contrôles individuels
Utilisez les poignées de redimensionnement pour redimensionner un contrôle. Lorsque le pointeur est positionné sur une poignée de redimensionnement, il change de forme pour indiquer les sens dans lequel le contrôle peut être redimensionné. Poignées de redimensionnement active sont correctes ; Si une poignée de redimensionnement est vide, le contrôle ne peut pas être redimensionné le long de cet axe.  
  
 Vous pouvez également modifier la taille d’un contrôle par le contrôle à des guides ou les marges d’alignement, ou en déplaçant un accroché guide en dehors d’un autre et contrôle.  
  
### <a name="to-size-a-control"></a>Pour dimensionner un contrôle  
  
1.  Sélectionnez le contrôle.  
  
2.  Faites glisser les poignées de redimensionnement pour modifier la taille du contrôle :  
  
    -   Poignées de redimensionnement en haut et côtés modifier la taille horizontale ou verticale.  
  
    -   Poignées de redimensionnement dans les angles modifier la taille horizontale et verticale.  
  
    > [!TIP]
    >  Vous pouvez redimensionner le contrôle d’unité une boîte de dialogue (DLU) à la fois en maintenant enfoncée la **MAJ** clés et à l’aide la **flèche droite** et **bas** clés.  
  
### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Pour dimensionner automatiquement un contrôle pour s’adapter au texte qu’il contient  
  
1.  Choisissez **ajuster au contenu** à partir de la **Format** menu.  
  
 \- ou -  
  
-   Cliquez sur le contrôle et choisissez **ajuster au contenu** dans le menu contextuel.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Contrôles](../mfc/controls-mfc.md)