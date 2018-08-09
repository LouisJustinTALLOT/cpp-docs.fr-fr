---
title: Affichage ou masquage de la barre d’outils Éditeur de boîte de dialogue | Microsoft Docs
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
ms.openlocfilehash: a8a19de393e7451f045d840552127743f87e00ba
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019171"
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar"></a>Affichage ou masquage de la barre d’outils Éditeur de boîtes de dialogue
Lorsque vous ouvrez le **boîte de dialogue** éditeur, le **boîte de dialogue Éditeur** barre d’outils s’affiche automatiquement en haut de votre solution.  
  
### <a name="dialog-editor-toolbar"></a>Barre d'outils de l'Éditeur de boîtes de dialogue  
  
|Icône|Signification|Icône|Signification|  
|----------|-------------|----------|-------------|  
|![Bouton de boîte de dialogue test](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Boîte de dialogue Test|![Bouton Espacer horizontalement](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalement|  
|![Aligner les côtés gauches bouton](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Aligner les côtés gauches|![Bouton Espacer verticalement](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Bas|  
|![Aligner le bouton droits](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Aligner les côtés droits|![Bouton de la largeur de marque](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Uniformiser la largeur|  
|![Bouton Aligner les sommets](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Aligner les sommets|![Bouton de même hauteur Make](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Uniformiser la hauteur|  
|![Bouton Aligner les bases](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Aligner les bases|![Bouton de taille de la même marque](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Uniformiser la taille|  
|![Bouton Centrer verticalement](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Bouton de grille bascule](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Activer/Désactiver la grille|  
|![Bouton Centrer horizontalement](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Bouton de Guides bascule](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Activer/Désactiver les repères|  
  
 Le **boîte de dialogue Éditeur** barre d’outils contient des boutons pour organiser la disposition des contrôles dans la boîte de dialogue, par exemple la taille et l’alignement. **Boîte de dialogue Éditeur** des boutons de barre d’outils correspondent à des commandes sur le **Format** menu. Pour plus d’informations, consultez [touches accélérateur pour l’éditeur de boîtes de dialogue](../windows/accelerator-keys-for-the-dialog-editor.md).  
  
 Lorsque vous êtes dans le **boîte de dialogue** éditeur, vous pouvez afficher ou masquer les le **boîte de dialogue Éditeur** la barre d’outils en le sélectionnant dans la liste des barres d’outils disponibles et windows.  
  
### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>Pour afficher ou masquer la barre d’outils Éditeur de boîte de dialogue  
  
1.  Sur le **vue** menu, cliquez sur **barres d’outils** puis choisissez **boîte de dialogue Éditeur** dans le sous-menu.  
  
    > [!NOTE]
    >  Le **boîte de dialogue Éditeur** barre d’outils s’affiche par défaut lorsque vous ouvrez une ressource de boîte de dialogue dans l’éditeur de boîtes de dialogue ; Toutefois, si vous fermez explicitement la barre d’outils, vous devez appeler la prochaine fois que vous ouvrez une ressource de boîte de dialogue.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Disposition des contrôles sur les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Comment : créer une ressource](../windows/how-to-create-a-resource.md)   
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeur de boîtes de dialogue](../windows/dialog-editor.md)