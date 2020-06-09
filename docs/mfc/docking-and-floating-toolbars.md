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
ms.openlocfilehash: f40d8860f2e514bf3c9e9364a664326250c9627a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615837"
---
# <a name="docking-and-floating-toolbars"></a>Ancrer et rendre flottantes les barres d'outils

Le bibliothèque MFC (Microsoft Foundation Class) prend en charge les barres d’outils ancrables. Une barre d’outils ancrable peut être attachée, ou ancrée, à n’importe quel côté de sa fenêtre parente, ou elle peut être détachée, ou flotter, dans sa propre fenêtre mini-frame. Cet article explique comment utiliser les barres d’outils ancrables dans vos applications.

Si vous utilisez l’Assistant application pour générer la structure de votre application, vous êtes invité à choisir si vous souhaitez des barres d’outils ancrables. Par défaut, l’Assistant application génère le code qui effectue les trois actions nécessaires pour placer une barre d’outils ancrable dans votre application :

- [Activez l’ancrage dans une fenêtre frame](#_core_enabling_docking_in_a_frame_window).

- [Activez l’ancrage pour une barre d’outils](#_core_enabling_docking_for_a_toolbar).

- [Ancrez la barre d’outils (dans la fenêtre frame)](#_core_docking_the_toolbar).

Si l’une de ces étapes est manquante, votre application affichera une barre d’outils standard. Les deux dernières étapes doivent être effectuées pour chaque barre d’outils ancrable dans votre application.

Les autres rubriques traitées dans cet article sont les suivantes :

- [Faire flotter la barre d’outils](#_core_floating_the_toolbar)

- [Redimensionnement dynamique de la barre d’outils](#_core_dynamically_resizing_the_toolbar)

- [Définition des positions de retour à la ligne pour une barre d’outils de style fixe](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Pour obtenir des exemples, consultez l’exemple général MFC [DOCKTOOL](../overview/visual-cpp-samples.md) .

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Activation de l’ancrage dans une fenêtre frame

Pour ancrer des barres d’outils à une fenêtre frame, la fenêtre frame (ou la destination) doit être activée pour permettre l’ancrage. Pour ce faire, utilisez la fonction [CFrameWnd :: EnableDocking](reference/cframewnd-class.md#enabledocking) , qui accepte un paramètre *DWORD* qui est un ensemble de bits de style indiquant le côté de la fenêtre frame qui accepte l’ancrage. Si une barre d’outils va être ancrée et qu’il y a plusieurs côtés sur lesquels elle pourrait être ancrée, les côtés indiqués dans le paramètre passé à `EnableDocking` sont utilisés dans l’ordre suivant : haut, bas, gauche, droite. Si vous souhaitez pouvoir ancrer des barres de contrôle n’importe où, transmettez **CBRS_ALIGN_ANY** à `EnableDocking` .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Activation de l’ancrage pour une barre d’outils

Une fois que vous avez préparé la destination pour l’ancrage, vous devez préparer la barre d’outils (ou la source) de la même manière. Appelez [CControlBar :: EnableDocking](reference/ccontrolbar-class.md#enabledocking) pour chaque barre d’outils que vous souhaitez ancrer, en spécifiant les côtés de destination auxquels la barre d’outils doit être ancrée. Si aucun des côtés spécifiés dans l’appel `CControlBar::EnableDocking` ne correspond aux côtés activés pour l’ancrage dans la fenêtre frame, la barre d’outils ne peut pas s’ancrer. Une fois qu’elle a été flottante, elle reste une barre d’outils flottante, impossible à ancrer à la fenêtre frame.

Si l’effet souhaité est une barre d’outils à virgule flottante permanente, appelez `EnableDocking` avec un paramètre de 0. Ensuite, appelez [CFrameWnd :: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar). La barre d’outils reste flottante et ne peut pas se connecter en permanence.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Ancrage de la barre d’outils

L’infrastructure appelle [CFrameWnd ::D ockcontrolbar](reference/cframewnd-class.md#dockcontrolbar) quand l’utilisateur tente de déposer la barre d’outils sur un côté de la fenêtre frame qui autorise l’ancrage.

En outre, vous pouvez appeler cette fonction à tout moment pour ancrer des barres de contrôle à la fenêtre frame. Cela se fait normalement pendant l’initialisation. Plusieurs barres d’outils peuvent être ancrées à un côté particulier de la fenêtre frame.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Faire flotter la barre d’outils

Le détachement d’une barre d’outils ancrable de la fenêtre frame est appelé flottante de la barre d’outils. Pour ce faire, appelez [CFrameWnd :: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar) . Spécifiez la barre d’outils à flotter, le point où elle doit être placée et un style d’alignement qui détermine si la barre d’outils flottante est horizontale ou verticale.

L’infrastructure appelle cette fonction lorsqu’un utilisateur fait glisser une barre d’outils hors de son emplacement d’ancrage et la dépose dans un emplacement où l’ancrage n’est pas activé. Cela peut se trouver à l’intérieur ou à l’extérieur de la fenêtre frame. Comme avec `DockControlBar` , vous pouvez également appeler cette fonction pendant l’initialisation.

L’implémentation MFC des barres d’outils ancrables ne fournit pas certaines des fonctionnalités étendues disponibles dans certaines applications qui prennent en charge les barres d’outils ancrables. Les fonctionnalités telles que les barres d’outils personnalisables ne sont pas fournies.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Redimensionnement dynamique de la barre d’outils

À partir de Visual C++ version 4,0, vous pouvez permettre aux utilisateurs de votre application de redimensionner dynamiquement les barres d’outils flottantes. En règle générale, une barre d’outils a une forme linéaire longue, affichée horizontalement. Toutefois, vous pouvez modifier l’orientation de la barre d’outils et sa forme. Par exemple, lorsque l’utilisateur ancre une barre d’outils sur l’un des côtés verticaux de la fenêtre frame, la forme est remplacée par une disposition verticale. Il est également possible de remodeler la barre d’outils dans un rectangle avec plusieurs lignes de boutons.

Vous pouvez :

- Spécifiez le dimensionnement dynamique sous la forme d’une caractéristique de barre d’outils.

- Spécifiez le dimensionnement fixe comme caractéristique de barre d’outils.

Pour fournir cette prise en charge, il existe deux nouveaux styles de barre d’outils à utiliser dans vos appels à la fonction membre [CToolBar :: Create](reference/ctoolbar-class.md#create) . Il s'agit de :

- **CBRS_SIZE_DYNAMIC** La barre de contrôle est dynamique.

- **CBRS_SIZE_FIXED** La barre de contrôle est fixe.

Le style dynamique de taille permet à votre utilisateur de redimensionner la barre d’outils quand elle est flottante, mais pas pendant qu’elle est ancrée. La barre d’outils « habille » si nécessaire pour modifier la forme lorsque l’utilisateur fait glisser ses bords.

Le style de taille fixe conserve les États de retour automatique à la ligne d’une barre d’outils, ce qui fixe la position des boutons dans chaque colonne. L’utilisateur de votre application ne peut pas modifier la forme de la barre d’outils. La barre d’outils est renvoyée à la ligne à des emplacements désignés, tels que les emplacements des séparateurs entre les boutons. Il gère cette forme si la barre d’outils est ancrée ou flottante. L’effet est une palette fixe avec plusieurs colonnes de boutons.

Vous pouvez également utiliser [CToolBar :: GetButtonStyle](reference/ctoolbar-class.md#getbuttonstyle) pour retourner un État et un style pour les boutons de vos barres d’outils. Le style d’un bouton détermine la façon dont le bouton apparaît et comment il répond aux entrées d’utilisateur ; l’état indique si le bouton est dans un état encapsulé.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Définition des positions de retour à la ligne pour une barre d’outils de style fixe

Pour une barre d’outils avec le style de taille fixe, indiquez les index de bouton de barre d’outils auxquels la barre d’outils sera renvoyée à la ligne. Le code suivant montre comment effectuer cette opération dans la substitution de la fenêtre frame principale `OnCreate` :

[!code-cpp[NVC_MFCDocViewSDI#10](codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

L’exemple général MFC [DOCKTOOL](../overview/visual-cpp-samples.md) indique comment utiliser les fonctions membres des classes [CControlBar](reference/ccontrolbar-class.md) et [CToolBar](reference/ctoolbar-class.md) pour gérer la disposition dynamique d’une barre d’outils. Consultez le fichier EDITBAR. CPP dans DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Notions de base de la barre d’outils](toolbar-fundamentals.md)

- [Info-bulles de barre d'outils](toolbar-tool-tips.md)

- [Utilisation de vos anciennes barres d'outils](using-your-old-toolbars.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d'outils MFC](mfc-toolbar-implementation.md)
