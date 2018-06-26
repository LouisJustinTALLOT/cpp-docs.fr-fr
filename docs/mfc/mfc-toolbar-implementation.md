---
title: Implémentation de barre d’outils MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d21bfa1dcc39e00de852203d05a2eae743b8a2f6
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929225"
---
# <a name="mfc-toolbar-implementation"></a>Implémentation de la barre d'outils MFC
Une barre d’outils est un [barre de contrôle](../mfc/control-bars.md) qui contient les images bitmap des contrôles. Ces images peuvent se comporter comme des boutons de commande, des cases à cocher ou des cases d’option. MFC fournit la classe [CToolbar](../mfc/reference/ctoolbar-class.md) pour gérer des barres d’outils.  
  
 Si vous l’activez, les utilisateurs des barres d’outils MFC ancrer les sur le bord d’une fenêtre ou « non » les n’importe où dans la fenêtre d’application. MFC ne prend pas en charge les barres d’outils personnalisables, comme celles figurant dans l’environnement de développement.  
  
 MFC prend également en charge les info-bulles : petites fenêtres contextuelles qui décrivent l’objectif d’un bouton barre d’outils lorsque vous placez la souris sur le bouton. Par défaut, lorsque l’utilisateur appuie sur un bouton de barre d’outils, une chaîne d’état s’affiche dans la barre d’état (le cas échéant). Vous pouvez activer la mise à jour pour afficher la chaîne d’état lorsque la souris est positionnée sur le bouton sans appuyer sur celui-ci de la barre d’état « Survoler ».  
  
> [!NOTE]
>  Depuis la version 4.0 de MFC, les barres d’outils et les info-bulles sont implémentées à l’aide de Windows 95 et fonctionnalités ultérieure au lieu de l’implémentation précédente spécifique à MFC.  
  
 Pour la compatibilité ascendante, MFC conserve l’implémentation de barre d’outils plus anciens dans la classe `COldToolBar`. La documentation pour les versions antérieures de MFC décrivent `COldToolBar` sous `CToolBar`.  
  
 Créez la première barre d’outils dans votre programme en sélectionnant l’option de la barre d’outils dans l’Assistant Application. Vous pouvez également créer des barres d’outils supplémentaires.  
  
 Les éléments suivants ont été introduites dans cet article :  
  
-   [Boutons de barre d’outils](#_core_toolbar_buttons)  
  
-   [Ancrer et rendre flottantes les barres d’outils](#_core_docking_and_floating_toolbars)  
  
-   [Barres d’outils et les info-bulles](#_core_toolbars_and_tool_tips)  
  
-   [Les classes CToolBar et CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)  
  
-   [La bitmap de barre d’outils](#_core_the_toolbar_bitmap)  
  
##  <a name="_core_toolbar_buttons"></a> Boutons de barre d’outils  
 Les boutons dans une barre d’outils sont similaires aux éléments dans un menu. Les deux types d’objets d’interface utilisateur génèrent des commandes que votre programme gère en fournissant des fonctions de gestionnaire. Fréquence à laquelle les boutons de barre d’outils dupliquent la fonctionnalité des commandes de menu, en fournissant une autre interface utilisateur pour la même fonctionnalité. Cette duplication est organisée simplement en fournissant le bouton et l’élément de menu le même ID.  
  
 Vous pouvez apporter les boutons dans une barre d’outils apparaissent et se comportent comme des boutons de commande, des cases à cocher ou des cases d’option. Pour plus d’informations, consultez la classe [CToolBar](../mfc/reference/ctoolbar-class.md).  
  
##  <a name="_core_docking_and_floating_toolbars"></a> Ancrer et rendre flottantes les barres d’outils  
 Une barre d’outils MFC peut :  
  
-   Rester immobile sur un côté de sa fenêtre parente.  
  
-   Déplacement et « ancré » ou attaché, par l’utilisateur à n’importe quel ou les côtés de la fenêtre parente que vous spécifiez.  
  
-   Être « flottante », ou détachée de la fenêtre frame, dans sa propre fenêtre mini-frame afin de l’utilisateur peut le déplacer à un emplacement approprié.  
  
-   Être redimensionnée lorsqu’elle est flottante.  
  
 Pour plus d’informations, consultez l’article [ancrées et flottantes les barres d’outils](../mfc/docking-and-floating-toolbars.md).  
  
##  <a name="_core_toolbars_and_tool_tips"></a> Barres d’outils et les info-bulles  
 Barres d’outils MFC peuvent également avoir lieu pour afficher les info-bulles » : petites fenêtres contextuelles comprenant une courte description de l’objectif d’un bouton barre d’outils. Lorsque l’utilisateur déplace la souris sur un bouton de barre d’outils, la fenêtre outil de Conseil s’affiche pour offrir un indicateur. Pour plus d’informations, consultez l’article [barre d’outils, info-bulles](../mfc/toolbar-tool-tips.md).  
  
##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> Les Classes de CToolBarCtrl CToolBar  
 Gérer des barres d’outils de votre application via la classe [CToolBar](../mfc/reference/ctoolbar-class.md). Depuis la version 4.0, MFC `CToolBar` a été réimplémentée pour utiliser le contrôle commun de barre d’outils disponible sous Windows 95 ou version ultérieure et Windows NT version 3.51 ou ultérieure.  
  
 Cette nouvelle implémentation entraîne moins de code MFC pour les barres d’outils, car MFC en fait une utilisation de la prise en charge du système d’exploitation. La nouvelle implémentation améliore également les fonctionnalités. Vous pouvez utiliser `CToolBar` des fonctions de membre pour manipuler des barres d’outils, ou vous peuvent obtenir une référence à sous-jacent [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) de l’objet et appeler ses fonctions membres pour la personnalisation de la barre d’outils et des fonctionnalités supplémentaires.  
  
> [!TIP]
>  Si vous avez beaucoup investi dans l’ancienne implémentation MFC de `CToolBar`, que le support est toujours disponible. Consultez l’article [à l’aide de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md).  
  
 Consultez également l’exemple général MFC [DOCKTOOL](../visual-cpp-samples.md).  
  
##  <a name="_core_the_toolbar_bitmap"></a> La Bitmap de barre d’outils  
 Une fois construite, un `CToolBar` objet crée l’image de la barre d’outils en chargeant une bitmap unique qui contient une image pour chaque bouton. L’Assistant Application crée une bitmap de barre d’outils standard que vous pouvez personnaliser avec Visual C++ [éditeur de barre d’outils](../windows/toolbar-editor.md).  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Notions de base de barre d’outils](../mfc/toolbar-fundamentals.md)  
  
-   [Ancrer et rendre flottantes les barres d’outils](../mfc/docking-and-floating-toolbars.md)  
  
-   [Barre d’outils info-bulles](../mfc/toolbar-tool-tips.md)  
  
-   [Utilisation du contrôle ToolBar](../mfc/working-with-the-toolbar-control.md)  
  
-   [Utilisation de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md)  
  
-   Le [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) classes  
  
## <a name="see-also"></a>Voir aussi  
 [Barres d’outils](../mfc/toolbars.md)   
 [Éditeur de barres d’outils](../windows/toolbar-editor.md)

