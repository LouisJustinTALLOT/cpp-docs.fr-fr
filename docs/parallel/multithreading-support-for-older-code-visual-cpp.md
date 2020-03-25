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
ms.openlocfilehash: 6f76ff42d2e28afe251ce234220051111736d3c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215083"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Prise en charge du multithreading pour le code plus ancien (Visual C++)

Visual C++ vous permet d’exécuter simultanément plusieurs threads d’exécution simultanés. Le traitement multithread vous permet de lancer des tâches en arrière-plan, de gérer des flux d’entrée simultanés, de gérer une interface utilisateur et bien plus encore.

## <a name="in-this-section"></a>Dans cette section

[Multithreading à l’aide de C et de Win32](multithreading-with-c-and-win32.md)<br/>
Prend en charge la création d’applications multithread avec Microsoft Windows

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)<br/>
Décrit ce que sont les processus et les threads et ce que fait l’approche MFC pour le multithreading.

[Multithreading et paramètres régionaux](multithreading-and-locales.md)<br/>
Décrit les problèmes qui surviennent lors de l’utilisation des fonctionnalités des paramètres régionaux de la bibliothèque Runtime C++ C et de la bibliothèque standard dans une application multithread.

## <a name="related-sections"></a>Sections connexes

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Représente un thread d'exécution dans une application.

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Décrit une classe virtuelle pure qui fournit une fonctionnalité commune aux objets de synchronisation dans Win32.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Représente un sémaphore, qui est un objet de synchronisation qui permet à un nombre limité de threads dans un ou plusieurs processus d’accéder à une ressource.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Représente un mutex, un objet de synchronisation qui permet à un thread l’accès mutuellement exclusif à une ressource.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Représente une section critique, qui est un objet de synchronisation qui permet à un thread à la fois d’accéder à une ressource ou à une section de code.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Représente un événement, qui est un objet de synchronisation qui permet à un thread de notifier à un autre thread qu’un événement s’est produit.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Représente le mécanisme de contrôle d'accès utilisé pour accéder aux ressources dans un programme multithread.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Représente le mécanisme de contrôle d'accès utilisé dans le contrôle de l'accès à une ressource dans un programme multithread.
