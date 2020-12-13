---
description: En savoir plus sur le multithreading à l’aide de C++ et de MFC
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
ms.openlocfilehash: a553f6364f52ce8d91e08e3bb5b0e83b48575fdc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149810"
---
# <a name="multithreading-with-c-and-mfc"></a>Multithreading à l'aide de C++ et de MFC

La bibliothèque MFC (Microsoft Foundation Class) assure la prise en charge des applications multithread. Cette rubrique décrit les processus et les threads et l’approche MFC pour le multithreading.

Un processus est une instance en cours d’exécution d’une application. Par exemple, lorsque vous double-cliquez sur l’icône bloc-notes, vous démarrez un processus qui exécute le bloc-notes.

Un thread est un chemin d’exécution au sein d’un processus. Lorsque vous démarrez le bloc-notes, le système d’exploitation crée un processus et commence à exécuter le thread principal de ce processus. Lorsque ce thread se termine, le processus est exécuté. Ce thread principal est fourni au système d’exploitation par le code de démarrage sous la forme d’une adresse de fonction. En règle générale, il s’agit de l’adresse de la `main` `WinMain` fonction ou fournie.

Si vous le souhaitez, vous pouvez créer des threads supplémentaires dans votre application. Vous pouvez effectuer cette opération pour gérer les tâches d’arrière-plan ou de maintenance lorsque vous ne souhaitez pas que l’utilisateur attende la fin de son exécution. Tous les threads des applications MFC sont représentés par des objets [CWinThread](../mfc/reference/cwinthread-class.md) . Dans la plupart des cas, vous n’avez même pas besoin de créer explicitement ces objets. au lieu de cela, appelez la fonction d’assistance du Framework [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), qui crée l' `CWinThread` objet pour vous.

MFC distingue deux types de threads : les threads d’interface utilisateur et les threads de travail. Les threads d’interface utilisateur sont généralement utilisés pour gérer les entrées d’utilisateur et répondre aux événements et messages générés par l’utilisateur. Les threads de travail sont couramment utilisés pour effectuer des tâches, telles que le recalcul, qui ne nécessitent pas d’intervention de l’utilisateur. L’API Win32 ne fait pas la distinction entre les types de threads. il doit simplement connaître l’adresse de départ du thread pour pouvoir commencer à exécuter le thread. MFC gère les threads d’interface utilisateur en particulier en fournissant une pompe de messages pour les événements dans l’interface utilisateur. `CWinApp` est un exemple d’objet thread d’interface utilisateur, car il dérive de `CWinThread` et gère les événements et les messages générés par l’utilisateur.

Une attention particulière doit être accordée aux situations où plusieurs threads peuvent nécessiter l’accès au même objet. [Multithreading : conseils de programmation](multithreading-programming-tips.md) décrit les techniques que vous pouvez utiliser pour résoudre les problèmes susceptibles de survenir dans ces situations. [Multithreading : comment utiliser les classes de synchronisation](multithreading-how-to-use-the-synchronization-classes.md) décrit comment utiliser les classes disponibles pour synchroniser l’accès de plusieurs threads à un seul objet.

L’écriture et le débogage de la programmation multithread sont fondamentalement une entreprise compliquée et délicate, car vous devez vous assurer que les objets ne sont pas accessibles par plus d’un thread à la fois. Les rubriques sur le multithreading n’enseignent pas les principes fondamentaux de la programmation multithread, mais uniquement comment utiliser MFC dans votre programme multithread. Les exemples MFC multithread inclus dans Visual C++ illustrent quelques fonctionnalités d’ajout multithread et d’API Win32 non comprises dans MFC. Toutefois, ils sont uniquement destinés à être un point de départ.

Pour plus d’informations sur la façon dont le système d’exploitation gère les processus et les threads, consultez [processus et threads](/windows/win32/ProcThread/processes-and-threads) dans le SDK Windows.

Pour plus d’informations sur la prise en charge des multithreads MFC, consultez les rubriques suivantes :

- [Multithreading : création de threads User-Interface](multithreading-creating-user-interface-threads.md)

- [Multithreading : création de threads de travail](multithreading-creating-worker-threads.md)

- [Multithreading : comment utiliser les classes de synchronisation](multithreading-how-to-use-the-synchronization-classes.md)

- [Multithreading : arrêt des threads](multithreading-terminating-threads.md)

- [Multithreading : conseils de programmation](multithreading-programming-tips.md)

- [Multithreading : quand utiliser les classes de synchronisation](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge du multithreading pour le code plus ancien (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)
