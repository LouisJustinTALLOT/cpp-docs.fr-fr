---
title: 'Multithreading : Conseils de programmation MFC'
ms.date: 08/27/2018
helpviewer_keywords:
- multithreading [C++], programming tips
- handle maps [C++]
- access control [C++], multithreading
- objects [C++], multiple threads and
- non-MFC threads [C++]
- threading [MFC], programming tips
- critical sections [C++]
- synchronization [C++], multithreading
- programming [C++], multithreaded
- communications [C++], between threads
- threading [C++], best practices
- troubleshooting [C++], multithreading
- Windows handle maps [C++]
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
ms.openlocfilehash: 0fbee2e836c2e898488da348e4dec9ea00ac4370
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494276"
---
# <a name="multithreading-mfc-programming-tips"></a>Multithreading : Conseils de programmation MFC

Les applications multithread requièrent une attention plus stricte que les applications à thread unique pour vous assurer que les opérations se produisent dans l’ordre prévu, et toutes les données qui sont accessible par plusieurs threads ne sont pas endommagées. Cette rubrique explique les techniques permettant d’éviter les problèmes potentiels lors de la programmation d’applications multithread avec la bibliothèque Microsoft Foundation classes (MFC).

- [L’accès aux objets à partir de plusieurs Threads](#_core_accessing_objects_from_multiple_threads)

- [Accès aux objets MFC à partir de Threads Non MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Cartes de handles Windows](#_core_windows_handle_maps)

- [Communication entre les Threads](#_core_communicating_between_threads)

##  <a name="_core_accessing_objects_from_multiple_threads"></a> L’accès aux objets à partir de plusieurs Threads

Objets MFC ne sont pas thread-safe par eux-mêmes. Deux des threads distincts ne peuvent pas manipuler le même objet, sauf si vous utilisez les classes de synchronisation MFC et/ou les objets de synchronisation Win32 appropriés, tels que les sections critiques. Pour plus d’informations sur les sections critiques et d’autres des objets connexes, consultez [synchronisation](/windows/desktop/Sync/synchronization) dans le SDK Windows.

La bibliothèque de classes utilise des sections critiques en interne pour protéger les structures de données globales, telles que celles utilisées par l’allocation de mémoire de débogage.

##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Accès aux objets MFC à partir de Threads Non MFC

Si vous avez une application multithread qui crée un thread de manière qu’en utilisant un [CWinThread](../mfc/reference/cwinthread-class.md) de l’objet, vous ne pouvez pas accéder aux autres objets MFC à partir de ce thread. En d’autres termes, si vous souhaitez accéder à n’importe quel objet MFC à partir d’un thread secondaire, vous devez créer ce thread avec l’une des méthodes décrites dans [Multithreading : création de Threads d’Interface utilisateur](multithreading-creating-user-interface-threads.md) ou [Multithreading : Création de Threads de travail](multithreading-creating-worker-threads.md). Ces méthodes sont les seules personnes qui permettent la bibliothèque de classes initialiser les variables internes nécessaires pour gérer les applications multithread.

##  <a name="_core_windows_handle_maps"></a> Cartes de handles Windows

En règle générale, un thread peut accéder uniquement les objets MFC qu’il a créé. Il s’agit, car des cartes de handle Windows temporaires et permanents sont conservées dans le stockage local des threads pour aider à assurer la protection contre l’accès simultané de plusieurs threads. Par exemple, un thread de travail ne peut pas effectuer un calcul et appelez ensuite d’un document `UpdateAllViews` fonction membre pour que les fenêtres qui contiennent des vues sur les nouvelles données modifiées. Cela n’a aucun effet, car la carte à partir de `CWnd` objets à HWND est locale pour le thread principal. Cela signifie qu’un seul thread peut avoir un mappage à partir d’un handle Windows vers un objet C++, mais un autre thread peut mapper le même handle à un autre objet C++. Modifications apportées dans un thread n’aurait pas reflétées dans l’autre.

Il existe différentes façons de contourner ce problème. La première consiste à passer des handles (par exemple, un HWND) au lieu d’objets C++ au thread de travail. Le thread de travail ajoute ensuite ces objets à sa carte temporaire en appelant approprié `FromHandle` fonction membre. Vous pouvez également ajouter l’objet à la carte permanente du thread en appelant `Attach`, mais cela doit être effectuée uniquement si vous êtes sûr que l’objet existe plus longtemps que le thread.

Une autre méthode consiste à créer de nouveaux messages définis par l’utilisateur correspondant aux différentes tâches que vos threads de travail effectueront, validez ces messages à la fenêtre principale de l’application à l’aide de `::PostMessage`. Cette méthode de communication est similaire à deux applications différentes qui communiquent à ceci près que les deux threads sont exécutent dans le même espace d’adressage.

Pour plus d’informations sur les cartes de descripteurs, consultez [Technical Note 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Pour plus d’informations sur le stockage local des threads, consultez [stockage Local des threads](/windows/desktop/ProcThread/thread-local-storage) et [stockage Local des threads à l’aide de](/windows/desktop/ProcThread/using-thread-local-storage) dans le SDK Windows.

##  <a name="_core_communicating_between_threads"></a> Communication entre les Threads

MFC fournit plusieurs classes qui permettent aux threads de synchroniser l’accès aux objets pour maintenir la sécurité des threads. L’utilisation de ces classes est décrite dans [Multithreading : comment utiliser les Classes de synchronisation](multithreading-how-to-use-the-synchronization-classes.md) et [Multithreading : quand utiliser les Classes de synchronisation](multithreading-when-to-use-the-synchronization-classes.md). Pour plus d’informations sur ces objets, consultez [synchronisation](/windows/desktop/Sync/synchronization) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)