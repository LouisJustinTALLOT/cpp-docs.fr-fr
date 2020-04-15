---
title: Définissez vos préférences de codage CMD dans Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: e3a665ead7a314b343ec3320e95b189f83a38a47
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365388"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Définissez vos préférences de codage CMD dans Visual Studio

Vous pouvez rendre votre expérience de codage CMD plus pratique, productive et agréable en personnalisant Visual Studio. Vous pouvez :

- Personnalisez les menus et les barres d’outils.
- Disposer la disposition de la fenêtre.
- Définissez des thèmes de couleur.
- Spécifiez les règles de formatage de C, y compris plusieurs styles de ClangFormat.
- Créez des raccourcis clavier personnalisés.

Vous pouvez synchroniser vos préférences entre plusieurs machines, créer et stocker plusieurs ensembles de préférences et les partager avec vos coéquipiers. Vous pouvez installer des extensions à partir du Visual Studio Marketplace, vous donnant des options supplémentaires pour personnaliser le comportement. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Disposer la disposition de la fenêtre

Dans la fenêtre Visual Studio, l’espace est divisé en menu principal, la barre d’outils, l’éditeur de code (ou fenêtre de document), et les fenêtres d’outils (comme Solution Explorer et Liste d’erreurs). Certaines fenêtres se chevauchent dans la même position. Par exemple, Solution Explorer, Class View, Resource View et Source Control Explorer partagent tous la même position par défaut. Vous changez entre eux en sélectionnant les onglets au bas du cadre. Pour rendre deux ou plusieurs de ces fenêtres visibles en même temps, il suffit de glisser l’un d’eux par sa barre de titre à une nouvelle position. Vous pouvez l’amarrer contre l’une des bordures de fenêtre principale visual Studio, ou vous pouvez le faire flotter.

La capture d’écran suivante montre la fenêtre **Team Explorer** traîné de sa position par défaut à une nouvelle position amarrée sur le côté gauche de l’éditeur de code. La zone ombragée bleue indique où la fenêtre sera placée lorsque le bouton de la souris est libéré.

![Capture d’écran de visual Studio Team Explorer fenêtre, avec changement de mise en page mis en évidence](media/window-layout-move-team-explorer.png)

Dans la fenêtre de document, chaque fichier ouvert est contenu dans un cadre tablé. Vous pouvez flotter ou verrouiller ces onglets, tout comme les fenêtres d’outils. Pour plus d’informations, consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Pour masquer toutes les fenêtres d’outils et maximiser la fenêtre Code Editor, appuyez sur **Alt** + **Shift** + **Enter** pour basculer le mode *plein écran*.

## <a name="set-c-coding-styles-and-formatting"></a>Définissez les styles de codage et le formatage de CMD

Vous pouvez spécifier de nombreuses options de formatage de code individuels, telles que l’indentation et les positions d’accolade. Pour ce faire, rendez-vous sur **Tools** > **Options** > **Text Editor** > **C/CMMD** > **Formatting** (ou **tapez Ctrl et Q** et recherchez « Formatting »). Alternativement, vous pouvez spécifier l’un des styles [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (ou votre propre style personnalisé ClangFormat).

![Capture d’écran des options ClangFormat](media/clang-format-ide.png)

Pour plus d’informations sur toutes les options de formatage, voir [Options, Text Editor, C/C, Formatting](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Définir le thème de couleur

Pour définir un fond clair ou sombre, tapez **Ctrl et Q** et recherchez « Thème de couleur ». Vous pouvez également les trouver en allant à **Tools** > **Options** > **Environnement**, et en choisissant color **thème**.

![Capture d’écran des thèmes de couleur](media/tools-options-color-theme.png)

Par exemple, voici le thème sombre:

![Capture d’écran de Visual Studio avec le thème de couleur foncée](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Personnaliser la colorisation du code

Dans Visual Studio 2019, vous pouvez choisir parmi trois *schémas de couleurs*prédéfinis. Ceux-ci spécifient comment les éléments de code sont colorisés dans l’éditeur. Pour choisir un thème, rendez-vous sur **Tools** > **Options** > **Text Editor** > **C/CMD** > **View**, et choisissez Color **Scheme**:

![Capture d’écran des options de système de couleurs de C, avec amélioré mis en évidence](media/color-schemes.png)

Dans le schéma de couleurs appelé **Visual Studio 2017**, la plupart des éléments de code sont tout simplement noir. Dans le schéma de couleurs **améliorées,** les fonctions, les variables locales, les macros et autres éléments sont colorisés. Dans le schéma **Amélioré (Globals vs Membres),** les fonctions et les variables globales sont colorisées pour contraster avec les membres de la classe. Le mode par défaut est **amélioré**, et il ressemble à ceci:

![Capture d’écran du schéma de couleurs amélioré](media/color-scheme-enhanced.png)

Quel que soit le thème ou le schéma de couleur est actif, vous pouvez personnaliser la police et les couleurs pour les éléments de code individuels. Pour ce faire, rendez-vous sur **Tools** > **Options** > **Environment** > **Fonts and Colors** (ou **tapez Ctrl et Q** et recherchez des « Fonts »). Faites défiler la liste des éléments d’affichage jusqu’à ce que vous voyiez les options C.

![Capture d’écran des options de police et de couleurs de CMD](media/tools-options-cpp-colors.png)

Les couleurs que vous définissez ici remplacent les valeurs définies pour les schémas de couleurs. Si vous voulez revenir aux couleurs par défaut pour le schéma de couleur, remettre une couleur à **défaut**.

## <a name="customize-the-toolbars"></a>Personnaliser les barres d’outils

Les barres d’outils offrent un moyen pratique d’émettre des commandes en un seul clic, plutôt qu’en utilisant les menus ou les raccourcis clavier. Visual Studio comprend un ensemble standard de barres d’outils. Pour le développement standard de C, les barres d’outils les plus utiles sont probablement Standard, Text Editor, Build, Debug, Source Control et Compare Files. Pour le développement de Windows, l’éditeur Dialog et l’éditeur d’images sont utiles pour la pose de boîtes de dialogue et d’édition d’icônes.

Planer au-dessus des icônes dans la barre d’outils pour voir quelle commande il représente:

![Capture d’écran des icônes de barre d’outils, avec l’exemple d’informations de commande disponibles sur le vol stationnaire](media/toolbar-mouse-hover.png)

Vous pouvez ajouter ou supprimer des commandes, ou créer une barre d’outils personnalisée, en sélectionnant la flèche descendante. Pour déplacer la barre d’outils vers un nouvel emplacement, faites-la glisser près de la barre pointillée sur la gauche.

![Capture d’écran de la barre d’outils, avec down-arrow et barre pointillée surlignée](media/toolbar-move-edit.png).

Pour plus d’informations, voir [Comment personnaliser les menus et les barres d’outils dans Visual Studio](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio).

## <a name="show-or-hide-line-numbers"></a>Afficher ou cacher les numéros de ligne

Vous pouvez spécifier si les numéros de ligne s’affichent à gauche des fenêtres de l’éditeur. Dans **Options**, sous **C/C ,** sélectionnez **Général**. Dans la section **Paramètres,** sélectionnez ou effacez **les numéros de ligne,** selon vos préférences.

![Capture d’écran des options générales, avec des numéros de ligne mis en évidence](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Créer des raccourcis clavier

De nombreuses commandes de Visual Studio ont des *raccourcis clavier,* des combinaisons de clés avec les touches Ctrl, Alt et Shift. Vous pouvez modifier ces raccourcis clavier ou en créer de nouveaux dans Visual Studio. Rendez-vous sur **Tools** > **Options** > **Environment** > **Keyboard** (ou tapez **Ctrl et Q** et recherchez des « raccourcis »). Pour plus d’informations, voir [Identifier et personnaliser les raccourcis clavier dans Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
