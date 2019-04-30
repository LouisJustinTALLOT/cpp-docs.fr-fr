---
title: Prise en charge du multithreading pour le code plus ancien (Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: 649e26c3f0704dfd6740b1a250613545e29316a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407742"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Prise en charge du multithreading pour le code plus ancien (Visual C++)

Visual C++ vous permet d’avoir plusieurs threads simultanés d’exécution en cours d’exécution simultanément. Avec le multithreading, vous pouvez exécuter les tâches en arrière-plan, gérer des flux simultanés d’entrées, gérer une interface utilisateur et bien plus encore.

## <a name="in-this-section"></a>Dans cette section

[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)<br/>
Fournit la prise en charge pour la création d’applications multithread avec Microsoft Windows

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)<br/>
Décrit les processus et les threads et que l’approche MFC pour le multithreading est.

[Multithreading et paramètres régionaux](multithreading-and-locales.md)<br/>
Décrit les problèmes qui surviennent lors de l’utilisation de la fonctionnalité de paramètres régionaux de la bibliothèque Runtime C et la bibliothèque C++ Standard dans une application multithread.

## <a name="related-sections"></a>Rubriques connexes

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Représente un thread d'exécution dans une application.

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Décrit une classe virtuelle pure qui fournit une fonctionnalité commune aux objets de synchronisation dans Win32.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Représente un sémaphore, ce qui est un objet de synchronisation qui permet à un nombre limité de threads dans un ou plusieurs processus pour accéder à une ressource.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Représente un mutex, un objet de synchronisation qui permet à un thread l’accès mutuellement exclusif à une ressource.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Représente une section critique, ce qui est un objet de synchronisation qui permet à un seul thread à la fois pour accéder à une ressource ou une section de code.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Représente un événement, qui est un objet de synchronisation qui permet à un thread de notifier à un autre un événement s’est produite.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Représente le mécanisme de contrôle d'accès utilisé pour accéder aux ressources dans un programme multithread.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Représente le mécanisme de contrôle d'accès utilisé dans le contrôle de l'accès à une ressource dans un programme multithread.