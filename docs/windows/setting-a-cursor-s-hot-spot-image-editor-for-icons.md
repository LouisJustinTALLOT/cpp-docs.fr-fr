---
title: Définition d’un curseur&#39;s Hot Spot (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], hot spots
- hot spots
ms.assetid: a610388a-45c8-43cd-98a2-fd31f29238b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe80ae0d4045514c22c40af38deeeecbbfecc363
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316378"
---
# <a name="setting-a-cursor39s-hot-spot-image-editor-for-icons"></a>Définition d’un curseur&#39;s Hot Spot (Éditeur d’images pour les icônes)

La zone réactive d’un [curseur](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md) est le point qui se réfère Windows pour suivre la position du curseur. Par défaut, la zone réactive est définie à l’angle supérieur gauche du curseur (coordonnées 0,0). Le **Hotspot** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) affiche les coordonnées de la zone réactive.

### <a name="to-set-a-cursors-hot-spot"></a>Pour définir la zone réactive d’un curseur

1. Sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md), cliquez sur le **définir la zone réactive** outil.

2. Cliquez sur le pixel que vous souhaitez désigner comme zone réactive du curseur.

   Le **Hotspot** propriété dans le **propriétés** fenêtre affiche les nouvelles coordonnées.

   > [!TIP]
   > Info-bulles s’affichent lorsque vous placez votre curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)  
[Icônes et curseurs : ressources Image pour les périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)