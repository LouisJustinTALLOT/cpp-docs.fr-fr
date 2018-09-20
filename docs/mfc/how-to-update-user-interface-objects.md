---
title: 'Comment : mettre à jour des objets d’Interface utilisateur | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8afe8f6f7594c2dff75125aa56a210505bf5301d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410583"
---
# <a name="how-to-update-user-interface-objects"></a>Comment : mettre à jour des objets d'interface utilisateur

En règle générale, les éléments de menu et boutons de barre d’outils ont plusieurs États. Par exemple, un élément de menu est grisé (grisé) si elle n’est pas disponible dans le contexte actuel. Éléments de menu peuvent également être activée ou désactivée. Un bouton de barre d’outils peut également être désactivé si elle est indisponible, ou il peut être vérifié.

Qui met à jour l’état de ces éléments comme programme logiquement, les conditions changent si un élément de menu génère une commande qui est gérée par, par exemple, un document, il est judicieux pour que le document à mettre à jour l’élément de menu. Le document contient probablement les informations sur laquelle repose la mise à jour.

Si une commande a plusieurs objets d’interface utilisateur (peut-être un élément de menu et un bouton de barre d’outils), les deux sont acheminées vers la même fonction de gestionnaire. Cela englobe votre code de mise à jour d’interface utilisateur pour tous les objets d’interface utilisateur équivalente dans un emplacement unique.

Le framework fournit une interface pratique pour mettre à jour automatiquement les objets d’interface utilisateur. Vous pouvez choisir d’effectuer la mise à jour d’une autre manière, mais l’interface fournie est efficace et facile à utiliser.

Les rubriques suivantes expliquent l’utilisation des gestionnaires de mise à jour :

- [Quand les gestionnaires de mise à jour sont appelés](../mfc/when-update-handlers-are-called.md)

- [La macro ON_UPDATE_COMMAND_UI](../mfc/on-update-command-ui-macro.md)

- [CCmdUI, classe](../mfc/the-ccmdui-class.md)

## <a name="see-also"></a>Voir aussi

[Menus](../mfc/menus-mfc.md)

