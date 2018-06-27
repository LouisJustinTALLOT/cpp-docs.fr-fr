---
title: Points d’entrée de procédure de fenêtre | Documents Microsoft
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
ms.openlocfilehash: 315526a8f95a1d62ac89f3a76fab492c9b136715
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956380"
---
# <a name="window-procedure-entry-points"></a>Procédure de fenêtre, points d'entrée
Pour protéger les procédures de fenêtre MFC, un module statique se lie à une implémentation de procédure de fenêtre spéciale. La liaison se produit automatiquement lorsque le module est lié à MFC. Cette procédure de fenêtre utilise la macro AFX_MANAGE_STATE pour définir correctement l’état du module effectif, puis il appelle `AfxWndProc`, qui à son tour délègue à la `WindowProc` fonction membre d’approprié `CWnd`-objet dérivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

