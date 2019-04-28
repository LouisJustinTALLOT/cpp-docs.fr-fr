---
title: Comment éviter les sources d'incident dans les programmes multithread
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
ms.openlocfilehash: 3ceae832599243ffa0aad2b6fa67148e7ea30510
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237062"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Comment éviter les sources d'incident dans les programmes multithread

Il existe plusieurs problèmes que vous pouvez rencontrer dans la création, la liaison ou l’exécution d’un programme multithread en langage C. Certains des problèmes plus courants sont décrits dans le tableau suivant. (Pour une description similaire du point de vue MFC, consultez [Multithreading : Conseils de programmation](multithreading-programming-tips.md).)

|Problème|Cause probable|
|-------------|--------------------|
|Vous obtenez un message indiquant que votre programme a provoqué une violation de protection.|De nombreuses erreurs de programmation Win32 provoquent des violations de protection. Une cause courante de violations de protection est l’assignation indirecte des données vers des pointeurs null. Étant donné que cela entraîne dans votre programme tente d’accéder à la mémoire qui n’appartient pas à elle, une violation de la protection est émise.<br /><br /> Un moyen simple de détecter la cause d’une violation de protection consiste à compiler votre programme avec des informations de débogage, puis exécutez-le à nouveau par le biais du débogueur dans l’environnement Visual C++. En cas de défaillance de la protection, Windows transfère le contrôle au débogueur et le curseur est positionné sur la ligne qui a provoqué le problème.|
|Votre programme génère de nombreuses erreurs de compilation et de liaison.|Vous pouvez éliminer de nombreux problèmes potentiels en définissant le niveau d’avertissement du compilateur à un de ses valeurs les plus élevées et Devancez les messages d’avertissement. En utilisant le niveau 3 ou les options au niveau Avertissement de niveau 4, vous pouvez détecter les conversions de données involontaires, les prototypes de fonction manquant et utilisation de fonctions non-ANSI.|

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)
