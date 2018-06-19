---
title: Propriétés de bouton de barre d’outils | Documents Microsoft
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
ms.openlocfilehash: 3e61ba7e8720c755ce26408826c56a5c1fc9d51e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890675"
---
# <a name="toolbar-button-properties"></a>Propriétés d'un bouton de barre d'outils
Les propriétés d’un bouton de barre d’outils sont :  
  
|Propriété|Description|  
|--------------|-----------------|  
|**ID**|Définit l’ID du bouton. La liste déroulante fournit commun **ID** noms.|  
|**Largeur**|Définit la largeur du bouton. valeur recommandée : 16 pixels.|  
|**Hauteur**|Définit la hauteur du bouton. Notez que la hauteur d’un bouton change la hauteur de tous les boutons de la barre d’outils. valeur recommandée : 15 pixels.|  
|**Invite**|Définit le message affiché dans la barre d’état. Ajout de \n et un nom d’ajoute une info-bulle à ce bouton de barre d’outils. Pour plus d’informations, consultez [création d’une info-bulle](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|  
  
 **Largeur** et **hauteur** s’appliquent à tous les boutons. Une image bitmap qui est utilisée pour créer une barre d’outils a une largeur maximale de 2048. Par conséquent, si vous définissez la largeur du bouton à 512, vous ne pouvez avoir quatre boutons et si vous définissez la largeur à 513, vous ne pouvez avoir trois boutons.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 MFC ou ATL  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des propriétés d’un bouton de barre d’outils](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [Éditeur de barres d’outils](../windows/toolbar-editor.md)

