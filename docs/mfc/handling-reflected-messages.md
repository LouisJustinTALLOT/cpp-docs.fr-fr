---
title: Gestion des messages réfléchis
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 8907b432cf4dabad33c0925b841f65dfc57c6295
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620140"
---
# <a name="handling-reflected-messages"></a>Gestion des messages réfléchis

La réflexion de message vous permet de gérer des messages pour un contrôle, tels que **WM_CTLCOLOR**, **WM_COMMAND**et **WM_NOTIFY**, dans le contrôle lui-même. Le contrôle est ainsi plus autonome et portable. Le mécanisme fonctionne avec les contrôles communs Windows, ainsi qu’avec les contrôles ActiveX (anciennement appelés contrôles OLE).

La réflexion de message vous permet de réutiliser vos `CWnd` classes dérivées plus facilement. La réflexion de message fonctionne via [CWnd :: OnChildNotify](reference/cwnd-class.md#onchildnotify), en utilisant des entrées de table des messages **ON_XXX_REFLECT** spéciales : par exemple, **ON_CTLCOLOR_REFLECT** et **ON_CONTROL_REFLECT**. La [note technique 62](tn062-message-reflection-for-windows-controls.md) explique plus en détail la réflexion des messages.

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [En savoir plus sur la réflexion de message](tn062-message-reflection-for-windows-controls.md)

- [Implémenter la réflexion de message pour un contrôle commun](tn062-message-reflection-for-windows-controls.md)

- [Implémenter la réflexion de message pour un contrôle ActiveX](mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](declaring-message-handler-functions.md)
