---
title: exit, fonction
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
ms.openlocfilehash: 82c9d00a49c8a080d893a51052739a0265ad0860
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154436"
---
# <a name="exit-function"></a>exit, fonction

Le **quitter** fonction, déclarée dans le fichier include standard \<stdlib.h >, met fin à un programme C++.

La valeur fournie en tant qu’argument à **quitter** est retourné au système d’exploitation en tant que code retour de code ou de sortie du programme. Par convention, un code de retour égal à zéro signifie que le programme s'est terminé correctement.

> [!NOTE]
>  Vous pouvez utiliser les constantes EXIT_FAILURE et EXIT_SUCCESS, défini dans \<stdlib.h >, pour indiquer la réussite ou l’échec de votre programme.

Émission d’un **retourner** instruction à partir de la `main` fonction équivaut à appeler le **quitter** fonction avec la valeur de retour comme argument.

Pour plus d’informations, consultez [quitter](../c-runtime-library/reference/exit-exit-exit.md) dans le *Run-Time Library Reference*.

## <a name="see-also"></a>Voir aussi

[Terminaison du programme](../cpp/program-termination.md)