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
ms.openlocfilehash: 93d1e067777b1c6f4430fe9cc44ae531559b6962
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294669"
---
# <a name="docking-and-floating-toolbars"></a>Ancrer et rendre flottantes les barres d'outils

La bibliothèque Microsoft Foundation Class prend en charge les barres d’outils ancrables. Une barre d’outils ancrable peut être attaché ou ancrée, n’importe quel côté de sa fenêtre parente, ou il peut être détachée ou laisser flotter, dans sa propre fenêtre mini-frame. Cet article explique comment utiliser des barres d’outils ancrables dans vos applications.

Si vous utilisez l’Assistant Application pour générer le squelette de votre application, vous êtes invité à choisir si vous souhaitez que les barres d’outils ancrables. Par défaut, l’Assistant Application génère le code qui effectue les trois actions nécessaires pour placer une barre d’outils ancrable dans votre application :

- [Activation de l’ancrage dans une fenêtre frame](#_core_enabling_docking_in_a_frame_window).

- [Activation de l’ancrage pour une barre d’outils](#_core_enabling_docking_for_a_toolbar).

- [Ancrer la barre d’outils (à la fenêtre frame)](#_core_docking_the_toolbar).

Si une de ces étapes sont manquante, votre application affiche une barre d’outils standard. Les deux dernières étapes doivent être effectuées pour chaque barre d’outils ancrable dans votre application.

Autres sujets abordés dans cet article sont les suivantes :

- [La barre d’outils flottante](#_core_floating_the_toolbar)

- [Redimensionnement dynamique de la barre d’outils](#_core_dynamically_resizing_the_toolbar)

- [Positions de retour à la ligne de paramètre pour une barre d’outils de style fixe](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Consultez l’exemple général MFC [DOCKTOOL](../visual-cpp-samples.md) pour obtenir des exemples.

##  <a name="_core_enabling_docking_in_a_frame_window"></a> Activation de l’ancrage dans une fenêtre Frame

Pour ancrer des barres d’outils à une fenêtre frame, la fenêtre frame (ou la destination) doit être activée pour permettre d’ancrage. Cette opération est effectuée à l’aide de la [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) (fonction), qui prend un *DWORD* paramètre qui est un ensemble de style de bits indiquant quel côté de la fenêtre frame accepte l’ancrage. Si une barre d’outils est ancrée et il n’y a plusieurs côtés il peut être ancré à, les côtés indiqués dans le paramètre passé à `EnableDocking` sont utilisés dans l’ordre suivant : haut, bas, gauche, droite. Si vous souhaitez pouvoir pour ancrer le contrôle barres en tout lieu, transmettez **CBRS_ALIGN_ANY** à `EnableDocking`.

##  <a name="_core_enabling_docking_for_a_toolbar"></a> Activation de l’ancrage pour une barre d’outils

Une fois que vous avez préparé la destination d’ancrage, vous devez préparer la barre d’outils (ou source) de manière similaire. Appelez [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) pour chaque barre d’outils que vous souhaitez ancrer, spécification de la destination côtés à laquelle doit s’ancrer la barre d’outils. Si aucun des côtés spécifiés dans l’appel à `CControlBar::EnableDocking` correspond aux côtés activées pour l’ancrage dans la fenêtre frame, la barre d’outils ne peut pas ancrer, elle flotte. Une fois qu’elle flotte, elle reste une barre d’outils flottante, incapable de s’ancrer à la fenêtre frame.

Si l’effet souhaité est une barre d’outils flottante définitivement, appelez `EnableDocking` avec un paramètre de 0. Appelez ensuite [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). La barre d’outils reste flottante, définitivement impossible ancrer n’importe où.

##  <a name="_core_docking_the_toolbar"></a> Ancrage de la barre d’outils

Le framework appelle [CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) lorsque l’utilisateur tente de supprimer la barre d’outils sur un côté de la fenêtre frame qui permet d’ancrage.

En outre, vous pouvez appeler cette fonction à tout moment pour ancrer des barres de contrôles dans la fenêtre frame. Cela est normalement effectuée pendant l’initialisation. Plus d’une barre d’outils peut être ancrée à un côté particulier de la fenêtre frame.

##  <a name="_core_floating_the_toolbar"></a> La barre d’outils flottante

Détachement d’une barre d’outils ancrable à partir de la fenêtre frame est appelée à la barre d’outils flottante. Appelez [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) pour ce faire. Spécifiez la barre d’outils à laisser flotter, le point où il doit être placé et un style d’alignement qui détermine si la barre d’outils flottante est horizontal ou vertical.

L’infrastructure appelle cette fonction lorsqu’un utilisateur fait glisser une barre d’outils hors de son emplacement d’ancrage et le dépose dans un emplacement où d’ancrage n’est pas activé. Cela peut être n’importe où à l’intérieur ou en dehors de la fenêtre frame. Comme avec `DockControlBar`, vous pouvez également appeler cette fonction lors de l’initialisation.

L’implémentation MFC des barres d’outils ancrables ne fournit pas certaines des fonctionnalités étendues de certaines applications qui prennent en charge les barres d’outils ancrables. Fonctionnalités telles que les barres d’outils personnalisables ne sont pas fournies.

##  <a name="_core_dynamically_resizing_the_toolbar"></a> Redimensionnement dynamique de la barre d’outils

À compter de Visual C++ version 4.0, vous pouvez faciliter possible pour les utilisateurs de votre application pour redimensionner dynamiquement les barres d’outils flottantes. En règle générale, une barre d’outils a une forme longue, linéaire, affichée horizontalement. Mais vous pouvez modifier l’orientation de la barre d’outils et sa forme. Par exemple, lorsque l’utilisateur ancre une barre d’outils sur l’un des côtés verticales de la fenêtre frame, la forme devient une disposition verticale. Il est également possible de transformer la barre d’outils dans un rectangle avec plusieurs rangées de boutons.

Vous pouvez :

- Spécifier un dimensionnement dynamique comme caractéristique d’une barre d’outils.

- Spécifier un dimensionnement fixe comme caractéristique d’une barre d’outils.

Pour fournir cette prise en charge, il existe deux nouveaux styles de barre d’outils à utiliser dans vos appels à la [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) fonction membre. Il s'agit des éléments suivants :

- **CBRS_SIZE_DYNAMIC** barre de contrôle est dynamique.

- **CBRS_SIZE_FIXED** barre de contrôle est fixe.

Le style de taille dynamique vous permet de redimensionner la barre d’outils lorsqu’elle est flottante mais pas lorsqu’elle est ancrée. La barre d’outils « enveloppe » lorsque cela est nécessaire pour modifier la forme lorsque l’utilisateur fait glisser ses bords.

Le style de taille fixé conserve les États de retour à la ligne d’une barre d’outils, en fixant la position des boutons dans chaque colonne. Utilisateur de votre application ne peut pas modifier la forme de la barre d’outils. La barre d’outils inclut dans un wrapper dans des lieux désigné, telles que les emplacements des séparateurs entre les boutons. Il conserve cette forme, si la barre d’outils est ancré ou flottant. L’effet est une palette fixe avec plusieurs colonnes de boutons.

Vous pouvez également utiliser [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) pour retourner un état et le style des boutons de barres d’outils. Style d’un bouton détermine comment le bouton s’affiche et comment il répond aux entrées d’utilisateur ; l’état indique si le bouton est dans un état encapsulé.

##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Paramètre de type Wrap Positions pour une barre d’outils de Style fixe

Pour une barre d’outils avec le style de taille fixé, désignez la barre d’outils index bouton encapsule la barre d’outils. Le code suivant montre comment effectuer cette opération dans votre fenêtre frame principale `OnCreate` remplacer :

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

L’exemple général MFC [DOCKTOOL](../visual-cpp-samples.md) montre comment utiliser les fonctions membres de classes [CControlBar](../mfc/reference/ccontrolbar-class.md) et [CToolBar](../mfc/reference/ctoolbar-class.md) pour gérer la disposition dynamique d’une barre d’outils. Consultez le fichier EDITBAR. CPP dans DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Principes de base de barre d’outils](../mfc/toolbar-fundamentals.md)

- [Info-bulles de barre d’outils](../mfc/toolbar-tool-tips.md)

- [À l’aide de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d’outils MFC](../mfc/mfc-toolbar-implementation.md)
