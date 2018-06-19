---
title: Test d’une boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes, testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57bb9e827caae0e328971077d902673f2428c80b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889539"
---
# <a name="testing-a-dialog-box"></a>Test d’une boîte de dialogue
Lorsque vous créez une boîte de dialogue, vous pouvez simuler et tester son comportement au moment de l’exécution sans compiler votre programme. Dans ce mode, vous pouvez :  
  
-   Taper du texte, effectuer des sélections dans des listes de zone de liste déroulante, activer ou désactiver des options, et choisir des commandes  
  
-   Tester l’ordre de tabulation  
  
-   Tester le groupement des contrôles tels que les cases à cocher et les cases d’option  
  
-   Tester les raccourcis clavier pour les contrôles dans la boîte de dialogue  
  
    > [!NOTE]
    >  Les connexions au code de boîte de dialogue effectuées à l’aide des Assistants ne sont pas incluses dans la simulation.  
  
 Quand vous testez une boîte de dialogue, elle s’affiche généralement à un emplacement qui est relatif à la fenêtre principale du programme. Si vous avez affecté la valeur True à la propriété Absolute Align de la boîte de dialogue, celle-ci s’affiche à une position relative au coin supérieur gauche de l’écran.  
  
### <a name="to-test-a-dialog-box"></a>Pour tester une boîte de dialogue  
  
1.  Lorsque l’Éditeur de boîtes de dialogue est la fenêtre active, dans la barre de menus, choisissez **Format**, **Tester la boîte de dialogue**.  
  
2.  Pour arrêter la simulation, appuyez sur Échap ou sélectionnez simplement le bouton **Fermer** dans la boîte de dialogue que vous testez.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index).  
  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Éditeur de boîte de dialogue](../windows/dialog-editor.md)   
 [Affichage ou masquage de la barre d’outils Éditeur de boîtes de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

