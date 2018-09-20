---
title: Points d’entrée de procédure de fenêtre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3226df51d2a83484de78d0d76c9af67e150e8eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403186"
---
# <a name="window-procedure-entry-points"></a>Procédure de fenêtre, points d'entrée

Pour protéger les procédures de fenêtre MFC, un module statique se lie à une implémentation de procédure de fenêtre spéciale. La liaison se produit automatiquement quand le module est lié à MFC. Cette procédure de fenêtre utilise la macro AFX_MANAGE_STATE pour définir correctement l’état du module effectif, ensuite, il appelle `AfxWndProc`, qui à son tour délègue à la `WindowProc` fonction membre d’approprié `CWnd`-objet dérivé.

## <a name="see-also"></a>Voir aussi

[Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

