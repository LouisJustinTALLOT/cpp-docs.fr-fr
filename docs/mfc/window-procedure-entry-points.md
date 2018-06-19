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
ms.openlocfilehash: 1095061cce8ff8f189984aca99a06eb741a46e83
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382071"
---
# <a name="window-procedure-entry-points"></a>Procédure de fenêtre, points d'entrée
Pour protéger les procédures de fenêtre MFC, un module statique se lie à une implémentation de procédure de fenêtre spéciale. La liaison se produit automatiquement lorsque le module est lié à MFC. Cette procédure de fenêtre utilise la `AFX_MANAGE_STATE` macro pour définir correctement l’état du module effectif, ensuite, il appelle **AfxWndProc**, qui à son tour délègue à la `WindowProc` fonction membre de la `CWnd`-dérivée objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

