---
title: Affichage ou masquage de la barre d’outils Éditeur de boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog editor, showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad456d37252b40be72217e6cbc40a2a399bb34ef
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891592"
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar"></a>Affichage ou masquage de la barre d’outils Éditeur de boîtes de dialogue
Lorsque vous ouvrez l’éditeur de boîte de dialogue, la barre d’outils Éditeur de boîte de dialogue s’affiche automatiquement en haut de votre solution.  
  
### <a name="dialog-editor-toolbar"></a>Barre d'outils de l'Éditeur de boîtes de dialogue  
  
|Icône|Signification|Icône|Signification|  
|----------|-------------|----------|-------------|  
|![Bouton de boîte de dialogue test](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Boîte de dialogue Test|![Bouton Espacer horizontalement](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalement|  
|![Aligner les côtés gauches bouton](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Aligner les côtés gauches|![Bouton Espacer verticalement](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Bas|  
|![Bouton de droits Aligner](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Aligner les côtés droits|![Bouton de même largeur Vérifiez](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Uniformiser la largeur|  
|![Bouton Aligner les sommets](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Aligner les sommets|![Bouton de même hauteur Vérifiez](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Uniformiser la hauteur|  
|![Bouton Aligner les bases](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Aligner les bases|![Bouton de taille de la même marque](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Uniformiser la taille|  
|![Bouton Centrer verticalement](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Bouton de grille](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Activer/Désactiver la grille|  
|![Bouton Centrer horizontalement](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Bouton de Guides](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Activer/Désactiver les repères|  
  
 La barre d’outils Éditeur de boîte de dialogue contient des boutons pour organiser la disposition des contrôles dans la boîte de dialogue, par exemple la taille et alignement. Boutons de barre d’outils Éditeur de boîte de dialogue correspondent aux commandes du menu Format. Pour plus d’informations, consultez [touches accélérateur pour l’éditeur de boîte de dialogue](../windows/accelerator-keys-for-the-dialog-editor.md).  
  
 Lorsque vous êtes dans l’éditeur de boîte de dialogue, vous pouvez basculer l’affichage de la barre d’outils Éditeur de boîte de dialogue en la sélectionnant dans la liste des fenêtres et des barres d’outils disponibles.  
  
### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>Pour afficher ou masquer la barre d’outils Éditeur de boîte de dialogue  
  
1.  Sur le **vue** menu, cliquez sur **barres d’outils** puis **boîte de dialogue Éditeur** dans le sous-menu.  
  
    > [!NOTE]
    >  La barre d’outils Éditeur de boîte de dialogue s’affiche par défaut lorsque vous ouvrez une ressource de boîte de dialogue dans l’éditeur de boîte de dialogue ; Toutefois, si vous fermez la barre d’outils, vous devez appeler la prochaine fois que vous ouvrez une ressource de boîte de dialogue.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Organisation des contrôles dans les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Comment : créer une ressource](../windows/how-to-create-a-resource.md)   
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeur de boîtes de dialogue](../windows/dialog-editor.md)

