---
title: Compilation et liaison de programmes Multithread | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c77cb217fe841e15f4c7470340bd3fbb502f6a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695731"
---
# <a name="compiling-and-linking-multithread-programs"></a>Compilation et liaison de programmes multithread
Le programme Bounce.c est présenté dans [exemple de programme multithread en langage C](../parallel/sample-multithread-c-program.md).  
  
 Les programmes sont compilés multithread par défaut.  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Pour compiler et lier le programme multithread Bounce.c dans l’environnement de développement  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans le **Types de projets** volet, cliquez sur **Win32**.  
  
3.  Dans le **modèles** volet, cliquez sur **Application Console Win32**, puis nommez le projet.  
  
4.  Ajoutez le fichier contenant le code source C pour le projet.  
  
5.  Sur le **générer** menu, générez le projet en cliquant sur le **générer** commande.  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Pour compiler et lier le programme multithread Bounce.c à partir de la ligne de commande  
  
1.  Compiler et lier le programme :  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C et de Win32](../parallel/multithreading-with-c-and-win32.md)