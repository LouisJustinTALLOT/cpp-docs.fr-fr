---
title: Implémentation de la barre d'outils MFC
ms.date: 11/04/2016
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
ms.openlocfilehash: 55c43c47b93cd21d86293706fc7c3eb5145c39fd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773175"
---
# <a name="mfc-toolbar-implementation"></a>Implémentation de la barre d'outils MFC

Une barre d’outils est un [barre de contrôle](../mfc/control-bars.md) qui contient les images bitmap des contrôles. Ces images peuvent se comporter comme des boutons de commande, des cases à cocher ou des cases d’option. MFC fournit la classe [CToolbar](../mfc/reference/ctoolbar-class.md) pour gérer les barres d’outils.

Si vous l’activez, les utilisateurs des barres d’outils MFC peuvent les ancrer sur le bord d’une fenêtre ou « flotter » les n’importe où dans la fenêtre d’application. MFC ne prend pas en charge les barres d’outils personnalisables telles que celles figurant dans l’environnement de développement.

MFC prend également en charge les info-bulles : petites fenêtres contextuelles qui décrivent l’objectif d’un bouton barre d’outils lorsque vous positionnez la souris sur le bouton. Par défaut, lorsque l’utilisateur appuie sur un bouton de barre d’outils, une chaîne d’état apparaît dans la barre d’état (le cas échéant). Vous pouvez activer « volée par » barre d’état mise à jour pour afficher la chaîne d’état lorsque la souris est positionnée sur le bouton sans appuyer sur celui-ci.

> [!NOTE]
>  Depuis la version 4.0 de MFC, les barres d’outils et les info-bulles sont implémentées à l’aide de Windows 95 et fonctionnalités plus loin au lieu de l’implémentation précédente spécifique à MFC.

Pour la compatibilité descendante, MFC conserve l’ancienne implémentation de barre d’outils dans la classe `COldToolBar`. La documentation pour les versions antérieures de MFC décrivent `COldToolBar` sous `CToolBar`.

Créez la première barre d’outils dans votre programme en sélectionnant l’option de barre d’outils dans l’Assistant Application. Vous pouvez également créer des barres d’outils supplémentaires.

Les éléments suivants sont présentés dans cet article :

- [Boutons de barre d’outils](#_core_toolbar_buttons)

- [Ancrer et rendre flottantes les barres d’outils](#_core_docking_and_floating_toolbars)

- [Barres d’outils et les info-bulles](#_core_toolbars_and_tool_tips)

- [Les classes CToolBar et CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [La bitmap de barre d’outils](#_core_the_toolbar_bitmap)

##  <a name="_core_toolbar_buttons"></a> Boutons de barre d’outils

Les boutons dans une barre d’outils sont analogues aux éléments dans un menu. Les deux types d’objets d’interface utilisateur génèrent des commandes que votre programme gère en fournissant des fonctions de gestionnaire. Souvent les boutons de barre d’outils dupliquent la fonctionnalité des commandes de menu, en fournissant une interface utilisateur alternative à la même fonctionnalité. Toute duplication est organisée simplement en fournissant le bouton et l’élément de menu le même ID.

Vous pouvez rendre les boutons dans une barre d’outils apparaissent et se comportent comme des boutons de commande, des cases à cocher ou des cases d’option. Pour plus d’informations, consultez la classe [CToolBar](../mfc/reference/ctoolbar-class.md).

##  <a name="_core_docking_and_floating_toolbars"></a> Ancrer et rendre flottantes les barres d’outils

Une barre d’outils MFC peut :

- Rester immobile sur un côté de sa fenêtre parente.

- Être déplacé et « fixé » ou attaché, par l’utilisateur à n’importe quel côté ou les côtés de la fenêtre parente que vous spécifiez.

- Être « flottante », ou détachée de la fenêtre frame, dans sa propre fenêtre mini-frame afin de l’utilisateur peut le déplacer vers une position.

- Être redimensionnée lorsqu’elle est flottante.

Pour plus d’informations, consultez l’article [ancrées et flottantes les barres d’outils](../mfc/docking-and-floating-toolbars.md).

##  <a name="_core_toolbars_and_tool_tips"></a> Barres d’outils et les info-bulles

Barres d’outils MFC peuvent également avoir lieu pour afficher des info-bulles » — petites fenêtres contextuelles contenant une courte description de l’objectif d’un bouton barre d’outils. Quand l’utilisateur déplace la souris sur un bouton de barre d’outils, la fenêtre de bulle de l’outil s’affiche pour offrir un indicateur. Pour plus d’informations, consultez l’article [info-bulles de barre d’outils](../mfc/toolbar-tool-tips.md).

##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> Les Classes de CToolBarCtrl CToolBar

Vous gérez des barres d’outils de votre application via la classe [CToolBar](../mfc/reference/ctoolbar-class.md). Depuis la version 4.0, MFC `CToolBar` a été réimplémentée pour utiliser le contrôle commun de barre d’outils disponible sous Windows 95 ou version ultérieure et Windows NT 3.51 ou version ultérieure.

Cette nouvelle implémentation entraîne moins de code MFC pour les barres d’outils, car MFC en fait une utilisation de la prise en charge du système d’exploitation. La nouvelle implémentation améliore également les fonctionnalités. Vous pouvez utiliser `CToolBar` fonctions membre pour manipuler des barres d’outils, ou vous pouvant obtenir une référence à sous-jacent [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) de l’objet et appeler ses fonctions membres pour la personnalisation de la barre d’outils et des fonctionnalités supplémentaires.

> [!TIP]
>  Si vous avez beaucoup investi dans l’ancienne implémentation MFC de `CToolBar`, que la prise en charge est toujours disponible. Consultez l’article [à l’aide de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md).

Consultez également l’exemple général MFC [DOCKTOOL](../overview/visual-cpp-samples.md).

##  <a name="_core_the_toolbar_bitmap"></a> La Bitmap de barre d’outils

Une fois construites, un `CToolBar` objet crée l’image de la barre d’outils en chargeant une seule bitmap qui contient une image pour chaque bouton. L’Assistant Application crée une bitmap de barre d’outils standard que vous pouvez personnaliser avec Visual C++ [éditeur de la barre d’outils](../windows/toolbar-editor.md).

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Principes de base de barre d’outils](../mfc/toolbar-fundamentals.md)

- [Ancrer et rendre flottantes les barres d’outils](../mfc/docking-and-floating-toolbars.md)

- [Info-bulles de barre d’outils](../mfc/toolbar-tool-tips.md)

- [Utilisation du contrôle ToolBar](../mfc/working-with-the-toolbar-control.md)

- [Utilisation de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md)

- Le [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) classes

## <a name="see-also"></a>Voir aussi

[Barres d’outils](../mfc/toolbars.md)<br/>
[Éditeur de barres d’outils](../windows/toolbar-editor.md)
