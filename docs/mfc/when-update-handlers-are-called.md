---
title: Quand les gestionnaires de mise à jour sont appelés | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 462bdb99c4f17232405db9df8e5bcb0da9861b69
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397752"
---
# <a name="when-update-handlers-are-called"></a>Quand les gestionnaires de mise à jour sont-ils appelés ?

Supposons que l’utilisateur clique sur la souris dans le menu fichier, ce qui génère un message WM_INITMENUPOPUP. Mécanisme de mise à jour de l’infrastructure met à jour collectivement tous les éléments dans le menu fichier avant le menu déroulant pour que l’utilisateur peut la voir.

Pour ce faire, les itinéraires de framework mise à jour des commandes pour tous les éléments de menu dans le menu contextuel le long du routage des commandes standard. Cibles de commande sur le routage ont la possibilité de mettre à jour des éléments de menu en faisant correspondre la commande de mise à jour avec une entrée de table des messages appropriée (sous la forme `ON_UPDATE_COMMAND_UI`) et en appelant une fonction de « gestionnaire de mise à jour ». Par conséquent, pour un menu comportant six éléments, six commandes de mise à jour sont envoyés. Si un gestionnaire de mise à jour existe pour l’ID de commande de l’élément de menu, elle est appelée pour effectuer la mise à jour. Si ce n’est pas le cas, le framework vérifie l’existence d’un gestionnaire pour cet ID de commande et Active ou désactive l’élément de menu comme il convient.

Si le framework ne trouve pas un `ON_UPDATE_COMMAND_UI` entrée pendant le routage de commande, il active automatiquement l’objet d’interface utilisateur s’il existe un `ON_COMMAND` entrée quelque part avec le même ID de commande. Sinon, elle désactive l’objet d’interface utilisateur. Par conséquent, pour vous assurer qu’un objet d’interface utilisateur est activé, fournissez un gestionnaire pour la commande que génère l’objet ou de lui fournir un gestionnaire de mise à jour. Voir la figure dans la rubrique [objets d’Interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md).

Il est possible de désactiver la désactivation par défaut des objets d’interface utilisateur. Pour plus d’informations, consultez le [membre m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) membre de classe `CFrameWnd` dans le *référence MFC*.

L’initialisation de menu est automatique dans le framework, qui se produisent lors de l’application reçoit un message WM_INITMENUPOPUP. Au cours de la boucle inactive, l’infrastructure de recherche du routage des commandes pour les gestionnaires de mise à jour de bouton de la même façon comme il le fait pour les menus.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour mettre à jour des objets d’interface utilisateur](../mfc/how-to-update-user-interface-objects.md)

