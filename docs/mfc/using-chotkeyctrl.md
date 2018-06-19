---
title: Utilisation de CHotKeyCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CHotKeyCtrl
dev_langs:
- C++
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3678d95ff0748c1854e509d898dfa89778c9a5f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381801"
---
# <a name="using-chotkeyctrl"></a>Utilisation de CHotKeyCtrl
Un contrôle hot key, représenté par la classe [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), est une fenêtre qui affiche une représentation textuelle de la combinaison de touches l’utilisateur tape, telles que CTRL + MAJ + Q. Il gère également une représentation interne de cette touche sous la forme d’un code de touche virtuelle et un ensemble d’indicateurs qui représentent l’état du décalage. Le contrôle de touche à chaud ne définit pas la touche d’accès rapide, ce qui revient à votre programme. (Pour une liste des codes de touches virtuelles, consultez Winuser.h.)  
  
 Utilisez un contrôle de touche d’accès rapide pour obtenir une entrée utilisateur touche d’accès rapide à associer à une fenêtre ou un thread. Contrôles Hot key sont souvent utilisés dans les boîtes de dialogue, par exemple celle qui s’affiche lors de la demande de l’utilisateur auquel affecter une touche d’accès rapide. Il incombe de votre programme pour récupérer les valeurs décrivant la touche d’accès rapide à partir du contrôle de clé à chaud et à appeler les fonctions appropriées pour associer la touche d’accès rapide par une fenêtre ou un thread.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Utilisation d’un contrôle de touche d’accès rapide](../mfc/using-a-hot-key-control.md)  
  
-   [Définition d’une touche d’accès rapide](../mfc/setting-a-hot-key.md)  
  
-   [Touches globales d’accès rapide](../mfc/global-hot-keys.md)  
  
-   [Touches d’accès rapide propres aux threads](../mfc/thread-specific-hot-keys.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles](../mfc/controls-mfc.md)

