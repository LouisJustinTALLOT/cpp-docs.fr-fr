---
title: Ancrer et rendre flottantes les barres d'outils
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: 30113565167b96b0df84a65768a1dfabe92ceffe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369776"
---
# <a name="docking-and-floating-toolbars"></a>Ancrer et rendre flottantes les barres d'outils

La Bibliothèque de classe Microsoft Foundation prend en charge les barres d’outils amarables. Une barre d’outils amarrée peut être fixée, ou amarrée, de n’importe quel côté de sa fenêtre parente, ou elle peut être détachée, ou flottée, dans sa propre fenêtre à mini-cadre. Cet article explique comment utiliser des barres d’outils dockables dans vos applications.

Si vous utilisez l’Assistant d’Application pour générer le squelette de votre application, il vous est demandé de choisir si vous voulez des barres d’outils dockables. Par défaut, l’Assistant d’Application génère le code qui effectue les trois actions nécessaires pour placer une barre d’outils amarable dans votre application :

- [Activez l’amarrage dans une fenêtre de cadre.](#_core_enabling_docking_in_a_frame_window)

- [Activez l’amarrage d’une barre d’outils.](#_core_enabling_docking_for_a_toolbar)

- [Amarrez la barre d’outils (à la fenêtre du cadre)](#_core_docking_the_toolbar).

Si l’une de ces étapes est manquante, votre application affichera une barre d’outils standard. Les deux dernières étapes doivent être effectuées pour chaque barre d’outils dockable dans votre application.

Voici d’autres sujets abordés dans cet article :

- [Flottant la barre d’outils](#_core_floating_the_toolbar)

- [Resizing dynamiquement la barre d’outils](#_core_dynamically_resizing_the_toolbar)

- [Réglage des positions d’enveloppe pour une barre d’outils de style fixe](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Consultez l’échantillon général du MFC [DOCKTOOL](../overview/visual-cpp-samples.md) à titre d’exemple.

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Permettre l’amarrage dans une fenêtre de cadre

Pour amarrer les barres d’outils à une fenêtre de cadre, la fenêtre de cadre (ou destination) doit être activée pour permettre l’amarrage. Ceci est fait en utilisant la fonction [CFrameWnd::EnableDocking,](../mfc/reference/cframewnd-class.md#enabledocking) qui prend un paramètre *DWORD* qui est un ensemble de bits de style indiquant de quel côté de la fenêtre de cadre accepte l’amarrage. Si une barre d’outils est sur le point d’être amarré et qu’il `EnableDocking` y a plusieurs côtés auxquels elle pourrait être amarré, les côtés indiqués dans le paramètre passé sont utilisés dans l’ordre suivant : en haut, en bas, à gauche, à droite. Si vous voulez être en mesure d’arrimer des `EnableDocking`barres de contrôle n’importe où, passer **CBRS_ALIGN_ANY** à .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Permettre l’amarrage pour une barre d’outils

Après avoir préparé la destination pour l’amarrage, vous devez préparer la barre d’outils (ou la source) d’une manière similaire. Appelez [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) pour chaque barre d’outils que vous souhaitez amarrer, en spécifiant les côtés de destination vers lesquels la barre d’outils doit accoster. Si aucun des côtés spécifiés dans l’appel pour correspondre aux `CControlBar::EnableDocking` côtés activés pour l’amarrage dans la fenêtre du cadre, la barre d’outils ne peut pas accoster - il flottera. Une fois qu’il a été flotté, il reste une barre d’outils flottante, incapable de s’amarrer à la fenêtre du cadre.

Si l’effet que vous voulez est `EnableDocking` une barre d’outils flottante en permanence, appelez avec un paramètre de 0. Puis appelez [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). La barre d’outils reste flottante, incapable de s’amarrer n’importe où.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Amarrage de la barre d’outils

Le cadre appelle [CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) lorsque l’utilisateur tente de laisser tomber la barre d’outils sur un côté de la fenêtre de cadre qui permet l’amarrage.

En outre, vous pouvez appeler cette fonction à tout moment pour amarrer des barres de contrôle à la fenêtre du cadre. Cela se fait normalement lors de l’initialisation. Plus d’une barre d’outils peut être amarrée à un côté particulier de la fenêtre du cadre.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Flottant la barre d’outils

Le détachement d’une barre d’outils amarrée de la fenêtre du cadre est appelé flottant la barre d’outils. Appelez [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) pour ce faire. Spécifiez la barre d’outils à flotter, le point où elle doit être placée, et un style d’alignement qui détermine si la barre d’outils flottante est horizontale ou verticale.

Le cadre appelle cette fonction lorsqu’un utilisateur traîne une barre d’outils hors de son emplacement amarré et la dépose dans un endroit où l’amarrage n’est pas activé. Cela peut être n’importe où à l’intérieur ou à l’extérieur de la fenêtre du cadre. Comme `DockControlBar`avec , vous pouvez également appeler cette fonction lors de l’initialisation.

La mise en œuvre des barres d’outils dockables MFC ne fournit pas certaines des fonctionnalités étendues trouvées dans certaines applications qui prennent en charge les barres d’outils dockables. Les fonctionnalités telles que les barres d’outils personnalisables ne sont pas fournies.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Resizing dynamiquement la barre d’outils

À partir de la version 4.0 Visual CD, vous pouvez permettre aux utilisateurs de votre application de resize les barres d’outils flottantes de manière dynamique. Typiquement, une barre d’outils a une forme longue et linéaire, affichée horizontalement. Mais vous pouvez changer l’orientation de la barre d’outils et sa forme. Par exemple, lorsque l’utilisateur amarre une barre d’outils contre l’un des côtés verticaux de la fenêtre du cadre, la forme change de disposition verticale. Il est également possible de remodeler la barre d’outils en un rectangle avec plusieurs rangées de boutons.

Vous pouvez :

- Spécifier le dimensionnement dynamique comme une caractéristique de barre d’outils.

- Spécifier le dimensionnement fixe comme une caractéristique de barre d’outils.

Pour fournir ce support, il existe deux nouveaux styles de barre d’outils pour une utilisation dans vos appels à la [CToolBar::Créer](../mfc/reference/ctoolbar-class.md#create) la fonction membre. Il s'agit de :

- **CBRS_SIZE_DYNAMIC** La barre de contrôle est dynamique.

- **CBRS_SIZE_FIXED** La barre de contrôle est fixe.

Le style dynamique de taille permet à votre utilisateur de resize la barre d’outils pendant qu’elle flotte, mais pas pendant qu’elle est amarré. La barre d’outils «enveloppe» là où nécessaire pour changer de forme que l’utilisateur traîne ses bords.

Le style fixe de taille conserve les états d’enveloppe d’une barre d’outils, fixant la position des boutons dans chaque colonne. L’utilisateur de votre application ne peut pas changer la forme de la barre d’outils. La barre d’outils s’enroule à des endroits désignés, tels que l’emplacement des séparateurs entre les boutons. Il maintient cette forme si la barre d’outils est amarré ou flottant. L’effet est une palette fixe avec plusieurs colonnes de boutons.

Vous pouvez également utiliser [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) pour retourner un état et un style pour les boutons sur vos barres d’outils. Le style d’un bouton détermine comment le bouton apparaît et comment il répond à l’entrée de l’utilisateur; l’état indique si le bouton est dans un état enveloppé.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Définir des positions d’enveloppe pour une barre d’outils de style fixe

Pour une barre d’outils avec le style fixe de taille, désignez les index de bouton de barre d’outils à laquelle la barre d’outils s’enveloppera. Le code suivant montre comment le faire dans `OnCreate` la dérogation de votre fenêtre de cadre principal :

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

L’échantillon général de MFC [DOCKTOOL](../overview/visual-cpp-samples.md) montre comment utiliser les fonctions des membres des classes [CControlBar](../mfc/reference/ccontrolbar-class.md) et [CToolBar](../mfc/reference/ctoolbar-class.md) pour gérer la disposition dynamique d’une barre d’outils. Voir le fichier EDITBAR. CPP à DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Principes fondamentaux de la barre d’outils](../mfc/toolbar-fundamentals.md)

- [Info-bulles de barre d'outils](../mfc/toolbar-tool-tips.md)

- [Utilisation de vos anciennes barres d'outils](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d'outils MFC](../mfc/mfc-toolbar-implementation.md)
