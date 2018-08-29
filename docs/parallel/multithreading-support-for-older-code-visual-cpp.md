---
title: Prise en charge le multithreading pour le Code plus ancien (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b1b301186036460acc07a526267503da8b97678
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132100"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Prise en charge du multithreading pour le code plus ancien (Visual C++)
Visual C++ vous permet d’avoir plusieurs threads simultanés d’exécution en cours d’exécution simultanément. Avec le multithreading, vous pouvez exécuter les tâches en arrière-plan, gérer des flux simultanés d’entrées, gérer une interface utilisateur et bien plus encore.  
  
## <a name="in-this-section"></a>Dans cette section  
 
[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)  
Fournit la prise en charge pour la création d’applications multithread avec Microsoft Windows  
  
[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)  
Décrit les processus et les threads et que l’approche MFC pour le multithreading est.  
  
[Multithreading et paramètres régionaux](multithreading-and-locales.md)  
Décrit les problèmes qui surviennent lors de l’utilisation de la fonctionnalité de paramètres régionaux de la bibliothèque Runtime C et la bibliothèque C++ Standard dans une application multithread.  
  
## <a name="related-sections"></a>Rubriques connexes  
 
[CWinThread](../mfc/reference/cwinthread-class.md)  
Représente un thread d'exécution dans une application.  
  
[CSyncObject](../mfc/reference/csyncobject-class.md)  
Décrit une classe virtuelle pure qui fournit une fonctionnalité commune aux objets de synchronisation dans Win32.  
  
[CSemaphore](../mfc/reference/csemaphore-class.md)  
Représente un sémaphore, ce qui est un objet de synchronisation qui permet à un nombre limité de threads dans un ou plusieurs processus pour accéder à une ressource.  
  
[CMutex](../mfc/reference/cmutex-class.md)  
Représente un mutex, un objet de synchronisation qui permet à un thread l’accès mutuellement exclusif à une ressource.  
  
[CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
Représente une section critique, ce qui est un objet de synchronisation qui permet à un seul thread à la fois pour accéder à une ressource ou une section de code.  
  
[CEvent](../mfc/reference/cevent-class.md)  
Représente un événement, qui est un objet de synchronisation qui permet à un thread de notifier à un autre un événement s’est produite.  
  
[CMultiLock](../mfc/reference/cmultilock-class.md)  
Représente le mécanisme de contrôle d'accès utilisé pour accéder aux ressources dans un programme multithread.  
  
[CSingleLock](../mfc/reference/csinglelock-class.md)  
Représente le mécanisme de contrôle d'accès utilisé dans le contrôle de l'accès à une ressource dans un programme multithread.  