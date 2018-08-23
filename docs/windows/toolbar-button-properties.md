---
title: Propriétés de bouton de barre d’outils | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons (in Toolbar editor), setting properties
- Toolbar editor, toolbar button properties
- status bars, active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5377616bd026ad9045345a465749f58dc22edd57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592963"
---
# <a name="toolbar-button-properties"></a>Propriétés d'un bouton de barre d'outils

Les propriétés d’un bouton de barre d’outils sont :

|Propriété|Description|
|--------------|-----------------|
|**ID**|Définit l’ID du bouton. La liste déroulante fournit courantes **ID** noms.|
|**Largeur**|Définit la largeur du bouton. valeur recommandée : 16 pixels.|
|**Hauteur**|Définit la hauteur du bouton. Notez que la hauteur d’un bouton change la hauteur de tous les boutons de la barre d’outils. valeur recommandée : 15 pixels.|
|**Invite**|Définit le message affiché dans la barre d’état. Ajout de \n et un nom ajoute une info-bulle à ce bouton de barre d’outils. Pour plus d’informations, consultez [création d’une info-bulle](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Largeur** et **hauteur** s’appliquent à tous les boutons. Une image bitmap qui sert à créer une barre d’outils a une largeur maximale de 2048. Par conséquent, si vous définissez la largeur du bouton à 512, vous ne pouvez avoir que quatre boutons et si vous définissez la largeur à 513, vous ne pouvez avoir trois boutons.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Modification des propriétés d’un bouton de barre d’outils](../windows/changing-the-properties-of-a-toolbar-button.md)  
[Éditeur de barres d’outils](../windows/toolbar-editor.md)