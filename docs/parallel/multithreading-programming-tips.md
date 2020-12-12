---
description: 'En savoir plus sur le multithreading : conseils de programmation MFC'
title: 'Multithreading : conseils de programmation MFC'
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
ms.openlocfilehash: 5c7141462da21c6b9298f48ab85b3de06a039d08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149888"
---
# <a name="multithreading-mfc-programming-tips"></a>Multithreading : conseils de programmation MFC

Les applications multithread requièrent des soins plus stricts que les applications à thread unique pour s’assurer que les opérations se produisent dans l’ordre prévu, et que les données accessibles par plusieurs threads ne sont pas endommagées. Cette rubrique décrit les techniques permettant d’éviter des problèmes potentiels lors de la programmation d’applications multithread avec la bibliothèque MFC (Microsoft Foundation Class).

- [Accès aux objets à partir de plusieurs threads](#_core_accessing_objects_from_multiple_threads)

- [Accès aux objets MFC à partir de threads non-MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Mappages de handles Windows](#_core_windows_handle_maps)

- [Communication entre les threads](#_core_communicating_between_threads)

## <a name="accessing-objects-from-multiple-threads"></a><a name="_core_accessing_objects_from_multiple_threads"></a> Accès aux objets à partir de plusieurs threads

Les objets MFC ne sont pas thread-safe par eux-mêmes. Deux threads distincts ne peuvent pas manipuler le même objet, sauf si vous utilisez les classes de synchronisation MFC et/ou les objets de synchronisation Win32 appropriés, tels que les sections critiques. Pour plus d’informations sur les sections critiques et d’autres objets connexes, consultez [synchronisation](/windows/win32/Sync/synchronization) dans le SDK Windows.

La bibliothèque de classes utilise des sections critiques en interne pour protéger les structures de données globales, telles que celles utilisées par l’allocation de mémoire de débogage.

## <a name="accessing-mfc-objects-from-non-mfc-threads"></a><a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Accès aux objets MFC à partir de threads non-MFC

Si vous avez une application multithread qui crée un thread d’une manière autre que l’utilisation d’un objet [CWinThread](../mfc/reference/cwinthread-class.md) , vous ne pouvez pas accéder à d’autres objets MFC à partir de ce thread. En d’autres termes, si vous souhaitez accéder à un objet MFC à partir d’un thread secondaire, vous devez créer ce thread à l’aide de l’une des méthodes décrites dans [Multithreading : création de threads User-Interface](multithreading-creating-user-interface-threads.md) ou [Multithreading : création de threads de travail](multithreading-creating-worker-threads.md). Ces méthodes sont les seules à permettre à la bibliothèque de classes d’initialiser les variables internes nécessaires pour gérer les applications multithread.

## <a name="windows-handle-maps"></a><a name="_core_windows_handle_maps"></a> Mappages de handles Windows

En règle générale, un thread peut accéder uniquement aux objets MFC qu’il a créés. Cela est dû au fait que les mappages de descripteurs Windows temporaires et permanents sont conservés dans le stockage local des threads pour aider à maintenir la protection de l’accès simultané à partir de plusieurs threads. Par exemple, un thread de travail ne peut pas effectuer un calcul, puis appeler `UpdateAllViews` la fonction membre d’un document pour que les fenêtres qui contiennent des vues sur les nouvelles données soient modifiées. Cela n’a aucun effet, car la carte des `CWnd` objets aux HWND est locale par rapport au thread principal. Cela signifie qu’un thread peut avoir un mappage d’un handle Windows à un objet C++, mais un autre thread peut mapper ce même handle à un objet C++ différent. Les modifications apportées dans un thread ne sont pas reflétées dans l’autre.

Il existe plusieurs façons de contourner ce problème. La première consiste à passer des handles individuels (tels qu’un HWND) plutôt que des objets C++ au thread de travail. Le thread de travail ajoute ensuite ces objets à son mappage temporaire en appelant la `FromHandle` fonction membre appropriée. Vous pouvez également ajouter l’objet à la carte permanente du thread en appelant `Attach` , mais cette opération ne doit être effectuée que si vous êtes sûr que l’objet sera plus long que le thread.

Une autre méthode consiste à créer des messages définis par l’utilisateur correspondant aux différentes tâches que vos threads de travail exécuteront et à poster ces messages dans la fenêtre principale de l’application à l’aide de `::PostMessage` . Cette méthode de communication est semblable à celle de deux applications différentes, sauf que les deux threads s’exécutent dans le même espace d’adressage.

Pour plus d’informations sur les mappages de descripteurs, consultez [Technical Note 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Pour plus d’informations sur le stockage local des threads, consultez [stockage local](/windows/win32/ProcThread/thread-local-storage) des threads et [utilisation du stockage local des threads](/windows/win32/ProcThread/using-thread-local-storage) dans le SDK Windows.

## <a name="communicating-between-threads"></a><a name="_core_communicating_between_threads"></a> Communication entre les threads

MFC fournit un certain nombre de classes qui permettent aux threads de synchroniser l’accès aux objets pour maintenir la sécurité des threads. L’utilisation de ces classes est décrite dans [Multithreading : comment utiliser les classes de synchronisation](multithreading-how-to-use-the-synchronization-classes.md) et le [Multithreading : quand utiliser les classes de synchronisation](multithreading-when-to-use-the-synchronization-classes.md). Pour plus d’informations sur ces objets, consultez [synchronisation](/windows/win32/Sync/synchronization) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Multithreading à l'aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)
