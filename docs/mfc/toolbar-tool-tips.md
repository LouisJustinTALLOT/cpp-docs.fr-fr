---
title: Barre d’outils, info-bulles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90f325df3825b3546616ce145d4477322a1b4eed
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956292"
---
# <a name="toolbar-tool-tips"></a>Info-bulles de barre d'outils
Info-bulles sont des petites fenêtres contextuelles qui présentent une courte description de l’objectif d’un bouton barre d’outils lorsque vous placez la souris sur un bouton pour une période donnée. Lorsque vous créez une application avec l’Assistant Application qui possède une barre d’outils, outil tip est prise en charge pour vous. Cet article explique l’outil Conseil charge créé par l’Assistant Application et comment ajouter la prise en charge du Conseil outils à votre application.  
  
 Cet article couvre les sujets suivants :  
  
-   [Activation des info-bulles](#_core_activating_tool_tips)  
  
-   [Mises à jour de barre d’état flyby](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a> Activation des info-bulles  
 Pour activer les info-bulles dans votre application, vous devez effectuer deux choses :  
  
-   Ajoutez le style CBRS_TOOLTIPS aux autres styles (comme WS_CHILD, WS_VISIBLE et d’autres **CBRS_** styles) passé en tant que le *dwStyle* paramètre à la [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) fonction ou dans [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).  
  
-   Comme décrit dans la procédure ci-dessous, ajoutez le texte d’info-bulle de barre d’outils, séparé par un caractère de saut de ligne ('\n'), à la ressource de chaîne contenant l’invite de ligne de commande pour la commande de barre d’outils. La ressource chaîne partage l’ID du bouton de barre d’outils.  
  
#### <a name="to-add-the-tool-tip-text"></a>Pour ajouter le texte info-bulle  
  
1.  Lorsque vous modifiez la barre d’outils dans l’éditeur de la barre d’outils, ouvrez le **propriétés de bouton de barre d’outils** fenêtre pour un bouton donné.  
  
2.  Dans le **invite** , spécifiez le texte que vous souhaitez voir apparaître dans l’info-bulle de ce bouton.  
  
> [!NOTE]
>  Définir le texte comme une propriété de bouton dans l’éditeur de la barre d’outils remplace la procédure précédente, dans lesquelles vous deviez ouvrir et modifier la ressource de chaîne.  
  
 Si une barre de contrôle avec des info-bulles activé a placé sur les contrôles enfants, la barre de contrôle affiche une info-bulle pour chaque contrôle enfant sur la barre de contrôle tant qu’il répond aux critères suivants :  
  
-   L’ID du contrôle n’est pas - 1.  
  
-   L’entrée de table de chaînes avec le même ID que le contrôle enfant dans le fichier de ressources possède une chaîne d’info-bulle outil.  
  
##  <a name="_core_fly_by_status_bar_updates"></a> Mises à jour de la barre d’état  
 Une fonctionnalité associée aux info-bulles est mise à jour de la barre d’état « Survoler ». Par défaut, le message dans la barre d’état décrit uniquement un bouton de barre d’outils spécifique lorsque le bouton est activé. En incluant CBRS_FLYBY dans votre liste de styles passée à `CToolBar::Create`, vous pouvez disposer de messages mis à jour lorsque le curseur de souris passe sur la barre d’outils sans devoir activer le bouton.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Implémentation de barre d’outils MFC (informations de vue d’ensemble des barres d’outils)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Ancrer et rendre flottantes les barres d’outils](../mfc/docking-and-floating-toolbars.md)  
  
-   Le [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) classes  
  
-   [Utilisation du contrôle de barre d’outils](../mfc/working-with-the-toolbar-control.md)  
  
-   [À l’aide de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de la barre d’outils MFC](../mfc/mfc-toolbar-implementation.md)

