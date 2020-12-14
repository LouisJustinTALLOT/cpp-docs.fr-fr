---
description: 'En savoir plus sur : implémentation de la barre d’outils MFC'
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
ms.openlocfilehash: 0e6ecf0536c55163dd63d5f05e4c5c9f24f2c4cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251152"
---
# <a name="mfc-toolbar-implementation"></a>Implémentation de la barre d'outils MFC

Une barre d’outils est une [barre de contrôle](control-bars.md) qui contient les images bitmap des contrôles. Ces images peuvent se comporter comme des boutons de contrôle, des cases à cocher ou des cases d’option. MFC fournit la classe [CToolBar](reference/ctoolbar-class.md) pour gérer les barres d’outils.

Si vous l’activez, les utilisateurs des barres d’outils MFC peuvent les ancrer au bord d’une fenêtre ou les « flotter » n’importe où dans la fenêtre de l’application. MFC ne prend pas en charge les barres d’outils personnalisables telles que celles de l’environnement de développement.

MFC prend également en charge les info-bulles : petites fenêtres indépendantes qui décrivent le rôle d’un bouton de barre d’outils lorsque vous placez le pointeur de la souris sur le bouton. Par défaut, quand l’utilisateur appuie sur un bouton de barre d’outils, une chaîne d’État s’affiche dans la barre d’État (le cas échéant). Vous pouvez activer la mise à jour de la barre d’État « volé » pour afficher la chaîne d’État lorsque la souris est positionnée sur le bouton sans l’appuyer.

> [!NOTE]
> Depuis la version 4,0 de MFC, les barres d’outils et les info-bulles sont implémentées à l’aide de Windows 95 et des fonctionnalités ultérieures au lieu de l’implémentation précédente propre à MFC.

Pour la compatibilité descendante, MFC conserve l’ancienne implémentation de la barre d’outils dans la classe `COldToolBar` . La documentation relative aux versions antérieures de MFC décrit `COldToolBar` sous `CToolBar` .

Créez la première barre d’outils de votre programme en sélectionnant l’option barre d’outils dans l’Assistant Application. Vous pouvez également créer des barres d’outils supplémentaires.

Les éléments suivants sont présentés dans cet article :

- [Boutons de la barre d’outils](#_core_toolbar_buttons)

- [Ancrer et rendre flottantes les barres d'outils](#_core_docking_and_floating_toolbars)

- [Barres d’outils et info-bulles](#_core_toolbars_and_tool_tips)

- [Classes CToolBar et CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Bitmap de la barre d’outils](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a> Boutons de la barre d’outils

Les boutons d’une barre d’outils sont analogues aux éléments d’un menu. Les deux types d’objets d’interface utilisateur génèrent des commandes que votre programme gère en fournissant des fonctions de gestionnaire. Souvent, les boutons de barre d’outils dupliquent les fonctionnalités des commandes de menu, fournissant une interface utilisateur alternative à la même fonctionnalité. Une telle duplication est organisée simplement en donnant au bouton et à l’élément de menu le même ID.

Vous pouvez faire apparaître les boutons dans une barre d’outils et se comporter comme des boutons de bouton, des cases à cocher ou des cases d’option. Pour plus d’informations, consultez la classe [CToolBar](reference/ctoolbar-class.md).

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a> Barres d’outils ancrées et flottantes

Une barre d’outils MFC peut :

- Rester immobile le long d’un côté de sa fenêtre parente.

- Être glissées et « ancrées » ou attachées par l’utilisateur à n’importe quel côté ou côté de la fenêtre parente que vous spécifiez.

- Être « flottant », ou détaché de la fenêtre frame, dans sa propre fenêtre mini-frame afin que l’utilisateur puisse la déplacer vers n’importe quelle position pratique.

- Être redimensionnée en flottant.

Pour plus d’informations, consultez l’article sur les [barres d’outils ancrées et flottantes](docking-and-floating-toolbars.md).

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a> Barres d’outils et info-bulles

Les barres d’outils MFC peuvent également être affichées pour afficher des « info-bulles », une petite fenêtre contextuelle contenant une brève description de l’objectif d’un bouton de barre d’outils. Lorsque l’utilisateur déplace la souris sur un bouton de barre d’outils, la fenêtre d’info-bulle s’affiche pour offrir un indicateur. Pour plus d’informations, consultez les [astuces de la barre d’outils](toolbar-tool-tips.md)de l’article.

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> Classes CToolBar et CToolBarCtrl

Vous gérez les barres d’outils de votre application via la classe [CToolBar](reference/ctoolbar-class.md). Depuis la version 4,0 de MFC, `CToolBar` a été réimplémenté pour utiliser le contrôle commun de barre d’outils disponible sous windows 95 ou version ultérieure et Windows NT version 3,51 ou ultérieure.

Cette réimplémentation entraîne moins de code MFC pour les barres d’outils, car MFC utilise la prise en charge du système d’exploitation. La réimplémentation améliore également la fonctionnalité. Vous pouvez utiliser des `CToolBar` fonctions membres pour manipuler des barres d’outils, ou vous pouvez obtenir une référence à l’objet [CToolBarCtrl](reference/ctoolbarctrl-class.md) sous-jacent et appeler ses fonctions membres pour la personnalisation de barre d’outils et les fonctionnalités supplémentaires.

> [!TIP]
> Si vous avez investi beaucoup dans l’implémentation MFC plus ancienne de `CToolBar` , cette prise en charge est toujours disponible. Consultez l’article [utilisation de vos anciennes barres d’outils](using-your-old-toolbars.md).

Consultez également l’exemple général MFC [DOCKTOOL](../overview/visual-cpp-samples.md).

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a> Bitmap de la barre d’outils

Une fois construite, un `CToolBar` objet crée l’image de la barre d’outils en chargeant une seule bitmap qui contient une image pour chaque bouton. L’Assistant application crée une image bitmap de barre d’outils standard que vous pouvez personnaliser à l’aide de l' [éditeur de barres d’outils](../windows/toolbar-editor.md)Visual C++.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Notions de base de barre d'outils](toolbar-fundamentals.md)

- [Ancrer et rendre flottantes les barres d'outils](docking-and-floating-toolbars.md)

- [Info-bulles de barre d'outils](toolbar-tool-tips.md)

- [Utilisation du contrôle ToolBar](working-with-the-toolbar-control.md)

- [Utilisation de vos anciennes barres d’outils](using-your-old-toolbars.md)

- Classes [CToolBar](reference/ctoolbar-class.md) et [CToolBarCtrl](reference/ctoolbarctrl-class.md)

## <a name="see-also"></a>Voir aussi

[Barres d'outils](toolbars.md)<br/>
[Éditeur de barres d’outils](../windows/toolbar-editor.md)
