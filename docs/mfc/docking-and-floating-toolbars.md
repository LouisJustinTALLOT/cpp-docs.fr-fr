---
title: Ancrer et rendre flottantes les barres d’outils | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 430af2344888696e3cbf053677ef59c7249b50bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352787"
---
# <a name="docking-and-floating-toolbars"></a>Ancrer et rendre flottantes les barres d'outils
La bibliothèque Microsoft Foundation Class prend en charge les barres d’outils ancrables. Une barre d’outils ancrable peut être attaché ou ancré, n’importe quel côté de sa fenêtre parente, ou il peut être détachée ou laisser flotter, dans sa propre fenêtre mini-frame. Cet article explique comment utiliser les barres d’outils ancrables dans vos applications.  
  
 Si vous utilisez l’Assistant Application pour générer le squelette de votre application, vous êtes invité à choisir si vous souhaitez que les barres d’outils ancrables. Par défaut, l’Assistant Application génère le code qui exécute les trois actions nécessaires pour placer une barre d’outils ancrable dans votre application :  
  
-   [Activez l’ancrage dans une fenêtre frame](#_core_enabling_docking_in_a_frame_window).  
  
-   [Activation de l’ancrage pour une barre d’outils](#_core_enabling_docking_for_a_toolbar).  
  
-   [Ancrer la barre d’outils (à la fenêtre frame)](#_core_docking_the_toolbar).  
  
 Si une de ces étapes sont manquante, votre application affiche une barre d’outils standard. Les deux dernières étapes doivent être effectués pour chaque barre d’outils ancrable dans votre application.  
  
 Autres sujets abordés dans cet article sont les suivantes :  
  
-   [La barre d’outils flottante](#_core_floating_the_toolbar)  
  
-   [Redimensionnement dynamique de la barre d’outils](#_core_dynamically_resizing_the_toolbar)  
  
-   [Positions de retour à la ligne de paramètre pour une barre d’outils de style fixe](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)  
  
 Consultez l’exemple général MFC [DOCKTOOL](../visual-cpp-samples.md) pour obtenir des exemples.  
  
##  <a name="_core_enabling_docking_in_a_frame_window"></a> Activation de l’ancrage dans une fenêtre Frame  
 Pour ancrer des barres d’outils dans une fenêtre frame, la fenêtre frame (ou la destination) doit être activée pour permettre l’ancrage. Cette opération est effectuée à l’aide de la [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) (fonction), qui prend un `DWORD` paramètre qui est un ensemble de style de bits indiquant quel côté de la fenêtre frame accepte l’ancrage. Si une barre d’outils est sur le point d’être ancrée et il n’y a plusieurs côtés il peut être ancré à, les côtés indiqués dans le paramètre passé à `EnableDocking` sont utilisés dans l’ordre suivant : haut, bas, gauche, droite. Si vous souhaitez être en mesure de pour ancrer le contrôle des barres de n’importe quel emplacement, passez `CBRS_ALIGN_ANY` à `EnableDocking`.  
  
##  <a name="_core_enabling_docking_for_a_toolbar"></a> Activation de l’ancrage pour une barre d’outils  
 Après avoir préparé la destination d’ancrage, vous devez préparer la barre d’outils (ou la source) de la même manière. Appelez [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) pour chaque barre d’outils que vous souhaitez ancrer, spécification de la destination côtés à laquelle la barre d’outils doit être ancrés. Si aucun des côtés spécifiés dans l’appel à `CControlBar::EnableDocking` ne correspond aux côtés activées pour l’ancrage dans la fenêtre frame, la barre d’outils ne peut pas ancrer — il flotte. Une fois qu’il a été affichée, il reste une barre d’outils flottante, incapable de s’ancrer à la fenêtre frame.  
  
 Si l’effet souhaité est une barre d’outils flottante définitivement, appelez `EnableDocking` avec un paramètre de 0. Appelez ensuite [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). La barre d’outils reste flottante, définitivement impossible ancrer n’importe où.  
  
##  <a name="_core_docking_the_toolbar"></a> Ancrage de la barre d’outils  
 Le framework appelle [CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) lorsque l’utilisateur tente de supprimer de la barre d’outils sur un côté de la fenêtre frame qui permet d’ancrage.  
  
 En outre, vous pouvez appeler cette fonction à tout moment pour ancrer des barres de contrôles dans la fenêtre frame. Ceci se fait normalement lors de l’initialisation. Plusieurs barres d’outils peuvent être ancrées à un même côté de la fenêtre frame.  
  
##  <a name="_core_floating_the_toolbar"></a> La barre d’outils flottante  
 Détachement d’une barre d’outils ancrable de la fenêtre frame est appelé à la barre d’outils flottante. Appelez [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) pour ce faire. Spécifiez la barre d’outils à laisser flotter, le point où il doit être placé et un style d’alignement qui détermine si la barre d’outils flottante est horizontal ou vertical.  
  
 L’infrastructure appelle cette fonction lorsqu’un utilisateur fait glisser une barre d’outils hors de son emplacement d’ancrage et le dépose dans un emplacement où d’ancrage n’est pas activé. Cela peut être n’importe où à l’intérieur ou à l’extérieur de la fenêtre frame. Comme avec `DockControlBar`, vous pouvez également appeler cette fonction lors de l’initialisation.  
  
 L’implémentation MFC des barres d’outils ancrables ne fournit pas certaines des fonctionnalités étendues de certaines applications qui prennent en charge les barres d’outils ancrables. Fonctionnalités telles que les barres d’outils personnalisables ne sont pas fournies.  
  
##  <a name="_core_dynamically_resizing_the_toolbar"></a> Redimensionnement dynamique de la barre d’outils  
 À compter de Visual C++ version 4.0, vous pouvez faciliter possibles pour les utilisateurs de votre application pour redimensionner dynamiquement les barres d’outils flottantes. En règle générale, une barre d’outils a une forme longue, linéaire affichée horizontalement. Mais vous pouvez modifier l’orientation de la barre d’outils et de sa forme. Par exemple, lorsque l’utilisateur ancre une barre d’outils à l’un des côtés verticales de la fenêtre frame, la forme change pour une disposition verticale. Il est également possible de transformer la barre d’outils dans un rectangle avec plusieurs lignes de boutons.  
  
 Vous pouvez :  
  
-   Spécifier un dimensionnement dynamique comme caractéristique d’une barre d’outils.  
  
-   Spécifier un dimensionnement fixe comme caractéristique d’une barre d’outils.  
  
 Pour fournir cette prise en charge, il existe deux nouveaux styles de barre d’outils à utiliser dans vos appels à la [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) fonction membre. Il s'agit des éléments suivants :  
  
-   **CBRS_SIZE_DYNAMIC** barre de contrôle est dynamique.  
  
-   **CBRS_SIZE_FIXED** barre de contrôle est fixe.  
  
 Le style de taille dynamique vous permet de redimensionner la barre d’outils lorsqu’elle est flottante mais pas lorsqu’elle est ancrée. La barre d’outils « enveloppe » lorsque cela est nécessaire pour modifier la forme que l’utilisateur fait glisser ses bords.  
  
 Le style de taille fixé conserve les États de retour à la ligne d’une barre d’outils, en fixant la position des boutons dans chaque colonne. Utilisateur de votre application ne peut pas modifier la forme de la barre d’outils. La barre d’outils encapsule dans des lieux désigné, telles que les emplacements des séparateurs entre les boutons. Il conserve cette forme, si la barre d’outils est ancré ou flottant. L’effet est une palette fixe avec plusieurs colonnes de boutons.  
  
 Vous pouvez également utiliser [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) pour retourner un état et le style des boutons de barres d’outils. Style d’un bouton détermine comment le bouton s’affiche et comment il répond aux entrées d’utilisateur ; l’état indique si le bouton est dans un état encapsulé.  
  
##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Positions de retour à la ligne de paramètre pour une barre d’outils de Style fixe  
 Pour une barre d’outils avec le style de taille fixé, désignez la barre d’outils index bouton encapsule la barre d’outils. Le code suivant montre comment effectuer cette opération dans votre fenêtre frame principale `OnCreate` remplacer :  
  
 [!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]  
  
 L’exemple général MFC [DOCKTOOL](../visual-cpp-samples.md) montre comment utiliser les fonctions membres des classes [CControlBar](../mfc/reference/ccontrolbar-class.md) et [CToolBar](../mfc/reference/ctoolbar-class.md) pour gérer la disposition dynamique d’une barre d’outils. Consultez le fichier EDITBAR. CPP dans DOCKTOOL.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Notions de base de barre d’outils](../mfc/toolbar-fundamentals.md)  
  
-   [Barre d’outils info-bulles](../mfc/toolbar-tool-tips.md)  
  
-   [À l’aide de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de la barre d’outils MFC](../mfc/mfc-toolbar-implementation.md)

