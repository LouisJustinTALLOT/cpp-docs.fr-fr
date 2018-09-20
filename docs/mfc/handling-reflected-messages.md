---
title: Gestion des Messages réfléchis | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99fc9c30ea85ba3f94fa811464f023da0eeea37e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438676"
---
# <a name="handling-reflected-messages"></a>Gestion des messages réfléchis

Message de la réflexion vous permet de traiter les messages pour un contrôle, tel que **WM_CTLCOLOR**, **WM_COMMAND**, et **WM_NOTIFY**, dans le contrôle lui-même. Cela rend le contrôle plus autonome et portable. Le mécanisme fonctionne avec les contrôles communs Windows ainsi qu’avec des contrôles ActiveX (anciennement contrôles OLE).

Message de la réflexion vous permet de réutiliser votre `CWnd`-plus facilement les classes dérivées. Message fonctionne de la réflexion via [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), à l’aide de spécial **ON_XXX_REFLECT** les entrées de mappage du message : par exemple, **ON_CTLCOLOR_REFLECT** et **ON_CONTROL_REFLECT**. [Note technique 62](../mfc/tn062-message-reflection-for-windows-controls.md) explique la réflexion de message plus en détail.

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [En savoir plus sur la réflexion de message](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implémenter la réflexion de message pour un contrôle commun](../mfc/tn062-message-reflection-for-windows-controls.md)

- [Implémenter la réflexion de message pour un contrôle ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)
