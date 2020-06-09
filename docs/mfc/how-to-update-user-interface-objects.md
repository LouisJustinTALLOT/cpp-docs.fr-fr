---
title: "Comment : mettre à jour des objets d'interface utilisateur"
ms.date: 11/04/2016
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
ms.openlocfilehash: aec4067a7b5854ef872cfcef19a15db8438dd795
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626390"
---
# <a name="how-to-update-user-interface-objects"></a>Comment : mettre à jour des objets d'interface utilisateur

En général, les éléments de menu et les boutons de barre d’outils ont plus d’un État. Par exemple, un élément de menu est grisé (grisé) s’il n’est pas disponible dans le contexte actuel. Les éléments de menu peuvent également être activés ou désactivés. Un bouton de barre d’outils peut également être désactivé s’il n’est pas disponible, ou il peut être vérifié.

Qui met à jour l’état de ces éléments au fur et à mesure que les conditions du programme changent logiquement, si un élément de menu génère une commande qui est gérée par, par exemple, un document, il est logique que le document met à jour l’élément de menu. Le document contient probablement les informations sur lesquelles la mise à jour est basée.

Si une commande possède plusieurs objets d’interface utilisateur (peut-être un élément de menu et un bouton de barre d’outils), tous deux sont acheminés vers la même fonction de gestionnaire. Cela encapsule votre code de mise à jour de l’interface utilisateur pour tous les objets d’interface utilisateur équivalents à un seul emplacement.

L’infrastructure fournit une interface pratique pour mettre à jour automatiquement les objets d’interface utilisateur. Vous pouvez choisir d’effectuer la mise à jour d’une autre façon, mais l’interface fournie est efficace et facile à utiliser.

Les rubriques suivantes expliquent l’utilisation des gestionnaires de mise à jour :

- [Quand les gestionnaires de mise à jour sont appelés](when-update-handlers-are-called.md)

- [Macro ON_UPDATE_COMMAND_UI](on-update-command-ui-macro.md)

- [Classe CCmdUI](the-ccmdui-class.md)

## <a name="see-also"></a>Voir aussi

[Menus](menus-mfc.md)
