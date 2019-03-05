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
ms.openlocfilehash: bc56c71c4c3c1367d35dd5995054b1d7371ae9de
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283486"
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
