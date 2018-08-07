---
title: Guide de boîte de dialogue Paramètres | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- Dialog editor, snap to guides
- grid spacing
- guides, settings
- dialog units (DLUs)
- layout grid in Dialog Editor
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 265c6c1931b0e48399039e507be45c73c710142d
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568889"
---
# <a name="guide-settings-dialog-box"></a>Paramètres du repère, boîte de dialogue
## <a name="layout-guides"></a>Repères de disposition  
 Affiche les paramètres pour les repères de disposition.  
  
 **Aucun**  
  
 Masque les outils de disposition.  
  
 **Règles et repères**  
  
 Lorsque l’option est activée, les règles sont ajoutées aux outils de disposition ; guides peuvent être placés dans les règles. Les guides par défaut sont les marges, qui peuvent être déplacés en faisant glisser. Cliquez dans les règles pour placer un guide. Contrôles « alignent » sur les repères lorsque les contrôles sont déplacées sur ou en regard. Contrôles sont également déplacés avec un repère une fois qu’ils sont attachés. Quand un contrôle est attaché à un repère de chaque côté et un guide est déplacé, le contrôle est redimensionné.  
  
 **Grid**  
  
 Crée une grille de disposition. Nouveaux contrôles sont automatiquement alignés sur la grille.  
  
## <a name="grid-spacing"></a>espacement de la grille  
 Affiche les paramètres pour l’espacement de la grille en unités de boîte de dialogue (DLU).  
  
 **La largeur : DLU**  
  
 Définit la largeur de la grille de disposition en DLU. Une DLU horizontale est la largeur moyenne de la police de la boîte de dialogue divisée en quatre parties.  
  
 **Hauteur : DLU**  
  
 Définit la hauteur de la grille de disposition dans DLU. Une DLU verticale correspond à la hauteur moyenne de la police de la boîte de dialogue divisée par huit.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Modification de la grille de disposition](../windows/modifying-the-layout-grid.md)   
 [États de l’Éditeur de boîtes de dialogue (repères et grilles)](../windows/dialog-editor-states-guides-and-grids.md)