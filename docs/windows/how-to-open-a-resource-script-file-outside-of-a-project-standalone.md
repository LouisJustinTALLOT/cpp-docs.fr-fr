---
title: 'Comment : ouvrir un fichier de Script de ressources en dehors d’un projet (autonome) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- .rc files, viewing resources
- resource script files, viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87dd0cb1e54b6e74c9c4f4fd7d9baff6461ad470
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879163"
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-project-standalone"></a>Comment : ouvrir un fichier de script de ressources en dehors d'un projet (autonome)
Vous pouvez afficher les ressources contenues dans un fichier .rc sans ouvrir de projet. Le fichier .rc s’ouvre dans une fenêtre de document lieu dans le [affichage des ressources](../windows/resource-view-window.md) fenêtre (comme lorsque le fichier est ouvert dans un projet).  
  
> [!NOTE]
>  Cette distinction est importante, car certaines commandes ne sont disponibles qu'au moment où le fichier est ouvert en mode autonome (en dehors d'un projet). Par exemple, vous pouvez uniquement enregistrer un fichier dans un autre format ou sous un autre nom de fichier lorsque le fichier est ouvert en dehors d’un projet (la **Enregistrer sous** commande n’est pas disponible lorsqu’un fichier est ouvert dans un projet).  
  
### <a name="to-open-an-rc-file-outside-a-project"></a>Pour ouvrir un fichier .rc en dehors d'un projet  
  
1.  À partir de la **fichier** menu, choisissez **ouvrir**, puis cliquez sur **fichier**.  
  
2.  Dans le **ouvrir le fichier** boîte de dialogue, accédez au fichier de script de ressources vous souhaitez afficher, sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
    > [!NOTE]
    >  Si vous ouvrez d’abord (**fichier**, **ouvrir**, **projet**), certaines commandes ne seront pas disponibles. Ouvrir un fichier en mode « autonome » signifie l'ouvrir sans charger d'abord le projet.  
  
 Pour ouvrir et afficher le fichier de ressources au format texte, consultez [modification d’un Script de ressources (.rc) fichier](../windows/how-to-open-a-resource-script-file-in-text-format.md).  
  
#### <a name="to-open-multiple-rc-files-outside-a-project"></a>Pour ouvrir plusieurs fichiers .rc en dehors d'un projet  
  
1.  Ouvrez les deux fichiers de ressources en mode autonome. Par exemple, ouvrez Source1.rc et Source2.rc.  
  
    1.  À partir de la **fichier** menu, choisissez **ouvrir**, puis cliquez sur **fichier**.  
  
    2.  Dans le **ouvrir le fichier** boîte de dialogue zone, naviguez jusqu’au premier fichier de script de ressources que vous souhaitez ouvrir (Source1.rc), sélectionnez le fichier, puis cliquez sur **ouvrir**.  
  
    3.  Répétez l'étape précédente pour ouvrir le second fichier .rc (Source2.rc).  
  
         Les fichiers .rc sont désormais ouverts dans des fenêtres de documents distinctes.  
  
2.  Quand les deux fichiers .rc sont ouverts, disposez-les fenêtres en mosaïque pour pouvoir les afficher simultanément :  
  
    -   À partir de la **fenêtre** menu, choisissez **nouveau groupe d’onglets Horizontal** ou **nouveau groupe d’onglets Vertical**.  
  
         \- ou -  
  
    -   Cliquez sur l’un des fichiers .rc et choisissez **nouveau groupe d’onglets Horizontal** ou **nouveau groupe d’onglets Vertical** dans le menu contextuel.  
  
> [!NOTE]
>  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  

  
### <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)