---
title: Procédure de fenêtre, points d'entrée
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 9e395ff96d27476bc2869e23139cb2d1233f02ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500917"
---
# <a name="window-procedure-entry-points"></a>Procédure de fenêtre, points d'entrée

Pour protéger les procédures de fenêtre MFC, un module statique se lie à une implémentation de procédure de fenêtre spéciale. La liaison se produit automatiquement quand le module est lié à MFC. Cette procédure de fenêtre utilise la macro AFX_MANAGE_STATE pour définir correctement l’état du module effectif, ensuite, il appelle `AfxWndProc`, qui à son tour délègue à la `WindowProc` fonction membre d’approprié `CWnd`-objet dérivé.

## <a name="see-also"></a>Voir aussi

[Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

