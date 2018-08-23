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
ms.openlocfilehash: 3533d57aa8230feb4d0e6fcb8689e0210c61bbd8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595502"
---
# <a name="guide-settings-dialog-box"></a>Paramètres du repère, boîte de dialogue

## <a name="layout-guides"></a>Repères de disposition

Affiche les paramètres pour les repères de disposition.

### <a name="none"></a>Aucun.

Masque les outils de disposition.

### <a name="rulers-and-guides"></a>Règles et repères

Lorsque l’option est activée, les règles sont ajoutées aux outils de disposition ; guides peuvent être placés dans les règles. Les guides par défaut sont les marges, qui peuvent être déplacés en faisant glisser. Cliquez dans les règles pour placer un guide. Contrôles « alignent » sur les repères lorsque les contrôles sont déplacées sur ou en regard. Contrôles sont également déplacés avec un repère une fois qu’ils sont attachés. Quand un contrôle est attaché à un repère de chaque côté et un guide est déplacé, le contrôle est redimensionné.

### <a name="grid"></a>Grille

Crée une grille de disposition. Nouveaux contrôles sont automatiquement alignés sur la grille.

## <a name="grid-spacing"></a>espacement de la grille

Affiche les paramètres pour l’espacement de la grille en unités de boîte de dialogue (DLU).

### <a name="width-dlus"></a>La largeur : DLU

Définit la largeur de la grille de disposition en DLU. Une DLU horizontale est la largeur moyenne de la police de la boîte de dialogue divisée en quatre parties.

### <a name="height-dlus"></a>Hauteur : DLU

Définit la hauteur de la grille de disposition dans DLU. Une DLU verticale correspond à la hauteur moyenne de la police de la boîte de dialogue divisée par huit.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Modification de la présentation grille](../windows/modifying-the-layout-grid.md)  
[États de l’Éditeur de boîtes de dialogue (repères et grilles)](../windows/dialog-editor-states-guides-and-grids.md)