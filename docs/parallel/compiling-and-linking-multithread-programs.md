---
title: Compilation et liaison de programmes multithread
ms.date: 11/04/2016
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
ms.openlocfilehash: 3d98f5341de1374c9119e2a4303c94fcfb005e29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558884"
---
# <a name="compiling-and-linking-multithread-programs"></a>Compilation et liaison de programmes multithread

Le programme Bounce.c est présenté dans [exemple de programme multithread en langage C](sample-multithread-c-program.md).

Les programmes sont compilés multithread par défaut.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Pour compiler et lier le programme multithread Bounce.c au sein de l’environnement de développement

1. Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.

1. Dans le **Types de projets** volet, cliquez sur **Win32**.

1. Dans le **modèles** volet, cliquez sur **Application Console Win32**, puis nommez le projet.

1. Ajoutez le fichier contenant le code source C pour le projet.

1. Sur le **Build** menu, générez le projet en cliquant sur le **Build** commande.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Pour compiler et lier le programme multithread Bounce.c à partir de la ligne de commande

1. Compilez et liez le programme :

    ```
    CL BOUNCE.C
    ```

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)