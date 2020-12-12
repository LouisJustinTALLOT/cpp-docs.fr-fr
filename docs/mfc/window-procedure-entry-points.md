---
description: En savoir plus sur les points d’entrée de procédure de fenêtre
title: Procédure de fenêtre, points d'entrée
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 2c2e5dc5d37a2e6f187e694d39205c4cd95b3810
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214479"
---
# <a name="window-procedure-entry-points"></a>Procédure de fenêtre, points d'entrée

Pour protéger les procédures de fenêtre MFC, un module statique lie avec une implémentation de procédure de fenêtre spéciale. La liaison se produit automatiquement quand le module est lié à MFC. Cette procédure de fenêtre utilise la macro AFX_MANAGE_STATE pour définir correctement l’état du module effectif, puis appelle `AfxWndProc` , qui à son tour délègue à la `WindowProc` fonction membre de l' `CWnd` objet dérivé de approprié.

## <a name="see-also"></a>Voir aussi

[Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)
