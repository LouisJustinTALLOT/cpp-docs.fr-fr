---
description: 'En savoir plus sur les outils suivants : info-bulles'
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
ms.openlocfilehash: bbf60246e778b60c2a6eacbcb55441806c00fad2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264282"
---
# <a name="toolbar-tool-tips"></a>Info-bulles de barre d'outils

Les info-bulles sont des fenêtres contextuelles minuscules qui présentent des descriptions courtes du rôle d’un bouton de barre d’outils lorsque vous placez le pointeur de la souris sur un bouton pendant une période donnée. Lorsque vous créez une application avec l’Assistant Application doté d’une barre d’outils, la prise en charge de l’info-bulle est fournie pour vous. Cet article explique la prise en charge des info-bulles créées par l’Assistant Application et comment ajouter la prise en charge des info-bulles à votre application.

Cet article couvre les points suivants :

- [Activation des info-bulles](#_core_activating_tool_tips)

- [Mises à jour de la barre d’État Flyby](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a> Activation des info-bulles

Pour activer les info-bulles dans votre application, vous devez effectuer deux opérations :

- Ajoutez le style CBRS_TOOLTIPS aux autres styles (tels que WS_CHILD, WS_VISIBLE et autres styles **CBRS_** ) passés comme paramètre *dwStyle* à la fonction [CToolBar :: Create](../mfc/reference/ctoolbar-class.md#create) ou à [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).

- Comme décrit dans la procédure ci-dessous, ajoutez le texte de l’info-bulle de la barre d’outils, séparé par un caractère de saut de ligne (« \n »), à la ressource de chaîne contenant l’invite de ligne de commande pour la commande de barre d’outils. La ressource de type chaîne partage l’ID du bouton de barre d’outils.

#### <a name="to-add-the-tool-tip-text"></a>Pour ajouter le texte d’info-bulle

1. Pendant que vous modifiez la barre d’outils dans l’éditeur de barres d’outils, ouvrez la fenêtre **Propriétés du bouton de barre d’outils** pour un bouton donné.

1. Dans la zone **invite** , spécifiez le texte que vous souhaitez voir apparaître dans l’info-bulle pour ce bouton.

> [!NOTE]
> La définition du texte en tant que propriété de bouton dans l’éditeur de barres d’outils remplace l’ancienne procédure, dans laquelle vous deviez ouvrir et modifier la ressource de type chaîne.

Si un contrôle enfant est placé sur une barre de contrôle avec des info-bulles, la barre de contrôle affiche une info-bulle pour chaque contrôle enfant de la barre de contrôles, à condition qu’elle réponde aux critères suivants :

- L’ID du contrôle n’est pas-1.

- L’entrée de table de chaînes avec le même ID que le contrôle enfant dans le fichier de ressources a une chaîne d’info-bulle.

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a> Mises à jour de la barre d’État Flyby

La mise à jour de la barre d’État « Flyby » est une fonctionnalité liée aux info-bulles. Par défaut, le message de la barre d’état décrit uniquement un bouton de barre d’outils particulier lorsque le bouton est activé. En incluant CBRS_FLYBY dans la liste des styles passés à `CToolBar::Create` , vous pouvez mettre ces messages à jour lorsque le curseur de la souris passe sur la barre d’outils sans réellement activer le bouton.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Implémentation de la barre d’outils MFC (informations générales sur les barres d’outils)](../mfc/mfc-toolbar-implementation.md)

- [Ancrer et rendre flottantes les barres d'outils](../mfc/docking-and-floating-toolbars.md)

- Classes [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Utilisation du contrôle de barre d'outils](../mfc/working-with-the-toolbar-control.md)

- [Utilisation de vos anciennes barres d'outils](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Voir aussi

[Implémentation de la barre d’outils MFC](../mfc/mfc-toolbar-implementation.md)
