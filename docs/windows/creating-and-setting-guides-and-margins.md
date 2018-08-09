---
title: Création et définition des repères et marges | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, clearing
- guides
- Dialog editor, guides and margins
- dialog box controls, placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
ms.assetid: fafa4545-8f00-436f-b590-300e76601156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11631a2ac6a2c83cd667d14a490c57b1a191c1a7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642556"
---
# <a name="creating-and-setting-guides-and-margins"></a>Création et définition des repères et des marges
Si vous déplacez des contrôles, ajout de contrôles, ou réorganiser une disposition en cours, guides peuvent aider à vous aligner précisément les contrôles dans une boîte de dialogue. Les repères s’affichent en bleu traits en pointillés dans la boîte de dialogue affichées dans l’éditeur et les flèches correspondantes dans les règles (en haut et le long du côté gauche de la **boîte de dialogue** éditeur).  
  
 Lorsque vous créez une boîte de dialogue, quatre marges sont fournies. Les marges sont des repères modifiés, apparaissant sous forme de lignes en pointillés bleues.  
  
### <a name="to-create-a-guide"></a>Pour créer un repère  
  
1.  Dans la règle, cliquez une fois pour créer un repère. (Un seul clic crée un nouveau guide ; double-cliquant lance le [repère, boîte de dialogue Paramètres](../windows/guide-settings-dialog-box.md) dans lequel vous pouvez spécifier les paramètres du guide.)  
  
### <a name="to-set-a-guide"></a>Pour définir un repère  
  
1.  Dans la boîte de dialogue, cliquez sur le guide et faites-le glisser vers une nouvelle position. (Vous pouvez également cliquer sur la flèche dans la règle à faire glisser le repère associé.)  
  
     Les coordonnées du guide sont affichées dans la barre d’état en bas de la fenêtre et dans la règle. Déplacez le pointeur sur la flèche dans la règle pour afficher la position exacte de ce guide.  
  
### <a name="to-delete-a-guide"></a>Pour supprimer un repère  
  
1.  Faites glisser le repère en dehors de la boîte de dialogue.  
  
 \- ou -  
  
-   Faites glisser la flèche correspondante hors de la règle.  
  
### <a name="to-move-margins"></a>Pour déplacer des marges  
  
1.  Faites glisser la marge à la nouvelle position.  
  
     Pour faire disparaître une marge, déplacez la marge à la position zéro. Pour ramener la marge, placez le pointeur sur la marge position zéro et déplacez la marge à la position.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [États d’éditeur de la boîte de dialogue (repères et grilles)](../windows/dialog-editor-states-guides-and-grids.md)   
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)