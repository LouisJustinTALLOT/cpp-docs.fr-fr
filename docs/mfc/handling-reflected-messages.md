---
description: En savoir plus sur la gestion des messages réfléchis
title: Gestion des messages réfléchis
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 4093c2feaa263470bc07df6feec32b12fea01542
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254909"
---
# <a name="handling-reflected-messages"></a>Gestion des messages réfléchis

La réflexion de message vous permet de gérer des messages pour un contrôle, tels que **WM_CTLCOLOR**, **WM_COMMAND** et **WM_NOTIFY**, dans le contrôle lui-même. Le contrôle est ainsi plus autonome et portable. Le mécanisme fonctionne avec les contrôles communs Windows, ainsi qu’avec les contrôles ActiveX (anciennement appelés contrôles OLE).

La réflexion de message vous permet de réutiliser vos `CWnd` classes dérivées plus facilement. La réflexion de message fonctionne via [CWnd :: OnChildNotify](reference/cwnd-class.md#onchildnotify), en utilisant des entrées de table des messages **ON_XXX_REFLECT** spéciales : par exemple, **ON_CTLCOLOR_REFLECT** et **ON_CONTROL_REFLECT**. La [note technique 62](tn062-message-reflection-for-windows-controls.md) explique plus en détail la réflexion des messages.

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [En savoir plus sur la réflexion de message](tn062-message-reflection-for-windows-controls.md)

- [Implémenter la réflexion de message pour un contrôle commun](tn062-message-reflection-for-windows-controls.md)

- [Implémenter la réflexion de message pour un contrôle ActiveX](mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](declaring-message-handler-functions.md)
