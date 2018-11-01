---
title: Propriétés du bouton de barre d’outils (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
ms.openlocfilehash: f20556ac088180ceb1ed979c3e02ffc465b41c7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665368"
---
# <a name="toolbar-button-properties-c"></a>Propriétés du bouton de barre d’outils (C++)

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

[Modification des propriétés d’un bouton de barre d’outils](../windows/changing-the-properties-of-a-toolbar-button.md)<br/>
[Éditeur de barres d’outils](../windows/toolbar-editor.md)