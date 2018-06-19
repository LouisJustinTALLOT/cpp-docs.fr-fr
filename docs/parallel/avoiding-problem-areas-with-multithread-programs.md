---
title: Éviter les problèmes avec les programmes Multithread | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5af4c1ca6a86b2cff457aee12e8337103ce7f42d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686612"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Comment éviter les sources d'incident dans les programmes multithread
Il existe plusieurs problèmes que vous pouvez rencontrer dans la création, la liaison ou l’exécution d’un programme multithread en langage C. Certains des problèmes plus courants sont décrits dans le tableau suivant. (Pour une description similaire à partir du point de vue MFC, consultez [Multithreading : conseils de programmation](../parallel/multithreading-programming-tips.md).)  
  
|Problème|Cause probable|  
|-------------|--------------------|  
|Vous obtenez un message indiquant que votre programme a provoqué une violation de protection.|De nombreuses erreurs de programmation Win32 provoquent des violations de protection. Une cause fréquente de violations de protection est l’affectation indirecte de données à des pointeurs null. Étant donné que cela entraîne de votre programme essaie d’accéder à la mémoire qui n’appartient pas à ce dernier, une violation de la protection est émise.<br /><br /> Un moyen simple de détecter la cause d’une violation de protection consiste à compiler votre programme avec des informations de débogage et exécutez-le via le débogueur dans l’environnement Visual C++. En cas de défaillance de la protection, Windows transfère le contrôle au débogueur, et le curseur est positionné sur la ligne qui a provoqué le problème.|  
|Votre programme génère de nombreuses erreurs de compilation et de liaison.|Vous pouvez éliminer les nombreux problèmes potentiels en définissant le niveau d’avertissement du compilateur à un de ses valeurs les plus élevées et en faisant attention les messages d’avertissement. En utilisant le niveau 3 ou les options au niveau Avertissement de niveau 4, vous pouvez détecter les conversions de données involontaires, les prototypes de fonction manquant et utilisation de fonctions non-ANSI.|  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C et de Win32](../parallel/multithreading-with-c-and-win32.md)