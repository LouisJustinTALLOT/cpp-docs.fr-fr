---
description: 'En savoir plus sur : quand les gestionnaires de mise à jour sont appelés'
title: Quand les gestionnaires de mise à jour sont-ils appelés ?
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- command routing [MFC], update commands
- toolbar buttons [MFC], enabling
- disabling toolbar buttons
- menus [MFC], initializing
- update handlers [MFC]
- disabling menu items
- toolbars [MFC], updating
- menus [MFC], updating as context changes
- toolbar controls [MFC], updated during OnIdle method [MFC]
- menu items, enabling
- command routing [MFC], update handlers
- update handlers, calling
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
ms.openlocfilehash: ee5d402eea4121c9ceb4bcbd48e752549c55b1c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297172"
---
# <a name="when-update-handlers-are-called"></a>Quand les gestionnaires de mise à jour sont-ils appelés ?

Supposons que l’utilisateur clique sur la souris dans le menu fichier, ce qui génère un message de WM_INITMENUPOPUP. Le mécanisme de mise à jour de l’infrastructure met à jour tous les éléments du menu fichier avant le menu déroulant pour que l’utilisateur puisse le voir.

Pour ce faire, l’infrastructure achemine les commandes de mise à jour pour tous les éléments de menu dans le menu contextuel, le long du routage de commandes standard. Les cibles de commande sur le routage ont la possibilité de mettre à jour tous les éléments de menu en faisant correspondre la commande de mise à jour avec une entrée de table des messages appropriée (sous la forme `ON_UPDATE_COMMAND_UI` ) et en appelant une fonction « gestionnaire de mise à jour ». Ainsi, pour un menu avec six éléments de menu, six commandes Update sont envoyées. Si un gestionnaire de mise à jour existe pour l’ID de commande de l’élément de menu, il est appelé pour effectuer la mise à jour. Si ce n’est pas le cas, le Framework vérifie l’existence d’un gestionnaire pour cet ID de commande et active ou désactive l’élément de menu comme il convient.

Si le Framework ne trouve pas d' `ON_UPDATE_COMMAND_UI` entrée au cours du routage des commandes, il active automatiquement l’objet de l’interface utilisateur s’il existe une `ON_COMMAND` entrée avec le même ID de commande. Dans le cas contraire, il désactive l’objet interface utilisateur. Par conséquent, pour vous assurer qu’un objet d’interface utilisateur est activé, fournissez un gestionnaire pour la commande que l’objet génère ou fournissez un gestionnaire de mise à jour pour celui-ci. Consultez la figure dans la rubrique [objets de l’interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md).

Il est possible de désactiver la désactivation par défaut des objets de l’interface utilisateur. Pour plus d’informations, consultez le membre [m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) de `CFrameWnd` la classe dans la *référence MFC*.

L’initialisation de menu est automatique dans le Framework, qui se produit lorsque l’application reçoit un message de WM_INITMENUPOPUP. Pendant la boucle inactive, l’infrastructure recherche les gestionnaires de mise à jour de bouton dans le routage des commandes, à peu près de la même façon que pour les menus.

## <a name="see-also"></a>Voir aussi

[Comment : mettre à jour des objets User-Interface](../mfc/how-to-update-user-interface-objects.md)
