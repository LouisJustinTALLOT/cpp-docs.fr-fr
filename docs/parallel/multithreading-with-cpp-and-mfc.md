---
title: Multithreading à l'aide de C++ et de MFC
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [C++], MFC
- worker threads [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], about threading
- CWinThread class, purpose of
- multithreading [C++], MFC
- threading [MFC]
- user interface threads [C++]
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
ms.openlocfilehash: c707c1c117bbc0005b2b3da4ed39f083ae407b27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643415"
---
# <a name="multithreading-with-c-and-mfc"></a>Multithreading à l'aide de C++ et de MFC

La bibliothèque Microsoft Foundation classes (MFC) prend en charge pour les applications multithread. Cette rubrique décrit les processus et threads ainsi que l’approche MFC en matière de multithreading.

Un processus est une instance en cours d’exécution d’une application. Par exemple, lorsque vous double-cliquez sur l’icône Bloc-notes, vous démarrez un processus qui exécute le bloc-notes.

Un thread est un chemin d’accès d’exécution dans un processus. Lorsque vous démarrez le bloc-notes, le système d’exploitation crée un processus et commence l’exécution du thread principal de ce processus. Lorsque ce thread se termine, tout comme le fait le processus. Ce thread principal est fourni au système d’exploitation par le code de démarrage sous la forme d’une adresse de fonction. En règle générale, il s’agit de l’adresse de la `main` ou `WinMain` (fonction) qui est fournie.

Si vous le souhaitez, vous pouvez créer des threads supplémentaires dans votre application. Vous souhaiterez peut-être procéder ainsi pour gérer des tâches d’arrière-plan ou de maintenance lorsque vous ne souhaitez pas que l’utilisateur d’attendre de leur exécution. Tous les threads dans les applications MFC sont représentés par [CWinThread](../mfc/reference/cwinthread-class.md) objets. Dans la plupart des cas, il est même inutile de créer explicitement ces objets ; à la place appeler la fonction d’assistance de framework [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), ce qui crée le `CWinThread` objet pour vous.

MFC distingue deux types de threads : threads d’interface utilisateur et les threads de travail. Threads d’interface utilisateur sont couramment utilisés pour gérer l’entrée d’utilisateur et répondre aux événements et messages générés par l’utilisateur. Threads de travail sont couramment utilisés pour effectuer des tâches, telles que le recalcul, qui ne nécessitent pas d’entrée d’utilisateur. L’API Win32 ne fait pas la distinction entre les types de threads ; Il a juste besoin de connaître l’adresse de départ du thread afin de pouvoir commencer à exécuter le thread. MFC gère les threads d’interface utilisateur en fournissant notamment une pompe de messages pour les événements dans l’interface utilisateur. `CWinApp` est un exemple d’un objet de thread d’interface utilisateur, car il dérive `CWinThread` et gère les événements et messages générés par l’utilisateur.

Une attention particulière convient aux situations où plusieurs threads peuvent nécessiter un accès au même objet. [Multithreading : Conseils de programmation](multithreading-programming-tips.md) décrit les techniques que vous pouvez utiliser pour contourner les problèmes qui peuvent survenir dans ces situations. [Multithreading : Comment utiliser les Classes de synchronisation](multithreading-how-to-use-the-synchronization-classes.md) explique comment utiliser les classes qui sont disponibles pour synchroniser l’accès à partir de plusieurs threads à un seul objet.

Écriture et débogage de programmes multithread sont par nature une entreprise complexe et épineuse, car vous devez vous assurer que les objets ne sont pas accessibles par plusieurs threads à la fois. Les rubriques de multithreading n’abordent pas les principes fondamentaux de la programmation multithread, mais que la manière d’utiliser MFC dans un programme multithread. Les exemples multithread MFC inclus dans Visual C++ illustrent quelques Adding Functionality et API Win32 non comprises dans la bibliothèque MFC ; multithread Toutefois, ils sont uniquement destinés à être un point de départ.

Pour plus d’informations sur la façon dont le système d’exploitation gère les processus et les threads, consultez [processus et Threads](/windows/desktop/ProcThread/processes-and-threads) dans le SDK Windows.

Pour plus d’informations sur la prise en charge du multithreading de MFC, consultez les rubriques suivantes :

- [Multithreading : création de threads d’interface utilisateur](multithreading-creating-user-interface-threads.md)

- [Multithreading : création de threads de travail](multithreading-creating-worker-threads.md)

- [Multithreading : comment utiliser les classes de synchronisation](multithreading-how-to-use-the-synchronization-classes.md)

- [Multithreading : arrêt d’exécution des threads](multithreading-terminating-threads.md)

- [Multithreading : conseils de programmation](multithreading-programming-tips.md)

- [Multithreading : quand utiliser les classes de synchronisation](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge du multithreading pour le code plus ancien (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)