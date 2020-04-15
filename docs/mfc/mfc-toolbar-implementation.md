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
ms.openlocfilehash: 38811be765d4427c4083b8f142b54fb67b9076a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359316"
---
# <a name="mfc-toolbar-implementation"></a>Implémentation de la barre d'outils MFC

Une barre d’outils est une [barre de contrôle](../mfc/control-bars.md) qui contient les images bitmap des commandes. Ces images peuvent se comporter comme des pushbuttons, des cases à cocher ou des boutons radio. MFC fournit la classe [CToolbar](../mfc/reference/ctoolbar-class.md) pour gérer les barres d’outils.

Si vous l’activez, les utilisateurs de barres d’outils MFC peuvent les amarrer au bord d’une fenêtre ou les « flotter » n’importe où dans la fenêtre d’application. MFC ne prend pas en charge les barres d’outils personnalisables comme celles de l’environnement de développement.

MFC prend également en charge les conseils d’outils : de petites fenêtres contextuaires qui décrivent le but d’un bouton de barre d’outils lorsque vous placez la souris sur le bouton. Par défaut, lorsque l’utilisateur appuie sur un bouton de barre d’outils, une chaîne de statut apparaît dans la barre d’état (s’il y en a une). Vous pouvez activer la mise à jour de la barre d’état « voler par » pour afficher la chaîne d’état lorsque la souris est positionnée sur le bouton sans la appuyer.

> [!NOTE]
> À partir de la version MFC 4.0, les barres d’outils et les conseils d’outils sont implémenté à l’aide de Windows 95 et de fonctionnalités ultérieures au lieu de la mise en œuvre précédente spécifique à MFC.

Pour la compatibilité vers l’arrière, MFC `COldToolBar`conserve l’ancienne mise en œuvre de la barre d’outils en classe . La documentation pour les versions `COldToolBar` `CToolBar`antérieures de MFC décrire sous .

Créez la première barre d’outils de votre programme en sélectionnant l’option Toolbar dans l’Assistant d’Application. Vous pouvez également créer des barres d’outils supplémentaires.

Les éléments suivants sont introduits dans cet article:

- [Boutons de barre d’outils](#_core_toolbar_buttons)

- [Docking et barres d’outils flottantes](#_core_docking_and_floating_toolbars)

- [Barres d’outils et conseils d’outils](#_core_toolbars_and_tool_tips)

- [Les classes CToolBar et CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Le bitmap Toolbar](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>Boutons de barre d’outils

Les boutons d’une barre d’outils sont analogues aux éléments d’un menu. Les deux types d’objets d’interface utilisateur génèrent des commandes, que votre programme gère en fournissant des fonctions de gestionnaire. Souvent, les boutons de barre d’outils dupliquer les fonctionnalités des commandes de menu, fournissant une interface utilisateur alternative à la même fonctionnalité. Une telle duplication est organisée simplement en donnant le bouton et l’élément de menu le même ID.

Vous pouvez faire apparaître les boutons d’une barre d’outils et vous comporter comme des boutons de cppuyez sur, de cocher ou de radio. Pour plus d’informations, voir classe [CToolBar](../mfc/reference/ctoolbar-class.md).

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>Barres d’outils d’amarrage et flottantes

Une barre d’outils MFC peut :

- Rester immobile le long d’un côté de sa fenêtre parente.

- Soyez traîné et « amarré », ou attaché, par l’utilisateur de n’importe quel côté ou côté de la fenêtre parente que vous spécifiez.

- Soyez «flotté», ou détaché de la fenêtre de cadre, dans sa propre fenêtre mini-cadre afin que l’utilisateur peut le déplacer à n’importe quelle position commode.

- Soyez resized tout en flottant.

Pour plus d’informations, voir l’article [Docking and Floating Toolbars](../mfc/docking-and-floating-toolbars.md).

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>Barres d’outils et conseils d’outils

Des barres d’outils MFC peuvent également être faites pour afficher des « conseils d’outil » — de minuscules fenêtres contextuelles contenant une courte description textuelle du but d’un bouton de barre d’outils. Comme l’utilisateur déplace la souris sur un bouton barre d’outils, la fenêtre de pointe de l’outil apparaît pour offrir un indice. Pour plus d’informations, voir l’article [Toolbar Tool Tips](../mfc/toolbar-tool-tips.md).

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>Les classes CToolBar et CToolBarCtrl

Vous gérez les barres d’outils de votre application via la classe [CToolBar](../mfc/reference/ctoolbar-class.md). En date de la version MFC 4.0, `CToolBar` a été réimpliste pour utiliser la barre d’outils contrôle commun disponible sous Windows 95 ou plus tard et Windows NT version 3.51 ou plus tard.

Cette réimplantation se traduit par moins de code MFC pour les barres d’outils, parce que MFC utilise le support du système d’exploitation. La réimplantation améliore également la capacité. Vous pouvez `CToolBar` utiliser les fonctions des membres pour manipuler les barres d’outils, ou vous pouvez obtenir une référence à l’objet [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) sous-jacent et appeler ses fonctions de membre pour la personnalisation des barres d’outils et des fonctionnalités supplémentaires.

> [!TIP]
> Si vous avez investi massivement dans `CToolBar`l’ancienne mise en œuvre de MFC, ce soutien est toujours disponible. Voir l’article [Using Your Old Toolbars](../mfc/using-your-old-toolbars.md).

Voir également l’échantillon général du MFC [DOCKTOOL](../overview/visual-cpp-samples.md).

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>Le Bitmap Toolbar

Une fois `CToolBar` construit, un objet crée l’image de la barre d’outils en chargeant une seule bitmap qui contient une image pour chaque bouton. L’Assistant d’Application crée un bitmap standard de barre d’outils que vous pouvez personnaliser avec l’éditeur visual CMD [toolbar](../windows/toolbar-editor.md).

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Principes fondamentaux de la barre d’outils](../mfc/toolbar-fundamentals.md)

- [Docking et barres d’outils flottantes](../mfc/docking-and-floating-toolbars.md)

- [Info-bulles de barre d'outils](../mfc/toolbar-tool-tips.md)

- [Travailler avec le contrôle de la barre d’outils](../mfc/working-with-the-toolbar-control.md)

- [Utilisation de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md)

- Les classes [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

## <a name="see-also"></a>Voir aussi

[Barres d'outils](../mfc/toolbars.md)<br/>
[Éditeur de barre d’outils](../windows/toolbar-editor.md)
