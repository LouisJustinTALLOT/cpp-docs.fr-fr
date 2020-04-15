---
title: Info-bulles de barre d'outils
ms.date: 11/04/2016
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
ms.openlocfilehash: 1762931b75734801659fd6271377260bd0473614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373459"
---
# <a name="toolbar-tool-tips"></a>Info-bulles de barre d'outils

Conseils d’outil sont les minuscules fenêtres popup qui présentent de courtes descriptions de l’objectif d’un bouton de barre d’outils lorsque vous placez la souris sur un bouton pendant une période de temps. Lorsque vous créez une application avec l’Assistant d’Application qui dispose d’une barre d’outils, le support de pointe d’outil est fourni pour vous. Cet article explique à la fois le support de pointe d’outil créé par l’assistant d’application et comment ajouter le support de pointe d’outil à votre application.

Cet article couvre les points suivants :

- [Conseils d’outils d’activation](#_core_activating_tool_tips)

- [Mises à jour de la barre d’état Flyby](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a>Conseils d’outils d’activation

Pour activer des conseils d’outils dans votre application, vous devez faire deux choses :

- Ajoutez le style CBRS_TOOLTIPS aux autres styles (tels que WS_CHILD, WS_VISIBLE et d’autres styles **CBRS_)** passé comme le paramètre *dwStyle* à la [CToolBar::Créer](../mfc/reference/ctoolbar-class.md#create) la fonction ou dans [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).

- Comme décrit dans la procédure ci-dessous, appendicez le texte de pointe de la barre d’outils, séparé par un caractère newline ('n'), à la ressource de chaîne contenant l’invite de commande-ligne pour la commande de barre d’outils. La ressource de chaîne partage l’ID du bouton de la barre d’outils.

#### <a name="to-add-the-tool-tip-text"></a>Pour ajouter le texte de pointe d’outil

1. Pendant que vous modifiez la barre d’outils dans l’éditeur de la barre d’outils, ouvrez la fenêtre **Toolbar Button Properties** pour un bouton donné.

1. Dans la boîte **Prompt,** spécifiez le texte que vous souhaitez apparaître dans la pointe de l’outil pour ce bouton.

> [!NOTE]
> La définition du texte comme propriété boutonnée dans l’éditeur de barre d’outils remplace l’ancienne procédure, dans laquelle vous avez dû ouvrir et modifier la ressource de chaîne.

Si une barre de contrôle avec des bouts d’outils activés a des commandes d’enfant placées dessus, la barre de commande affichera une pointe d’outil pour chaque commande d’enfant sur la barre de commande aussi longtemps qu’elle répond aux critères suivants :

- L’ID du contrôle n’est pas - 1.

- L’entrée de table à cordes avec la même pièce d’identité que le contrôle de l’enfant dans le fichier de ressources a une chaîne de pointe d’outil.

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a>Mises à jour flyby Status Bar

Une fonctionnalité liée aux conseils d’outils est la mise à jour de la barre d’état « flyby ». Par défaut, le message sur la barre d’état ne décrit qu’un bouton de barre d’outils particulier lorsque le bouton est activé. En incluant CBRS_FLYBY dans votre liste `CToolBar::Create`de styles passés à , vous pouvez avoir ces messages mis à jour lorsque le curseur de souris passe sur la barre d’outils sans réellement activer le bouton.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Mise en œuvre de la barre d’outils MFC (informations d’aperçu sur les barres d’outils)](../mfc/mfc-toolbar-implementation.md)

- [Docking et barres d’outils flottantes](../mfc/docking-and-floating-toolbars.md)

- Les classes [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Utilisation du contrôle de barre d'outils](../mfc/working-with-the-toolbar-control.md)

- [Utilisation de vos anciennes barres d'outils](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d'outils MFC](../mfc/mfc-toolbar-implementation.md)
