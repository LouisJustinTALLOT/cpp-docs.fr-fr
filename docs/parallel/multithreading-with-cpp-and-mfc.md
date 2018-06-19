---
title: Multithreading à l’aide de C++ et MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 778602a0e9236ad8cc788d8a2306e8f2d143ec49
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688568"
---
# <a name="multithreading-with-c-and-mfc"></a>Multithreading à l'aide de C++ et de MFC
La bibliothèque Microsoft Foundation classes (MFC) prend en charge pour les applications multithread. Cette rubrique décrit les processus et threads et l’approche MFC au multithreading.  
  
 Un processus est une instance d’exécution d’une application. Par exemple, lorsque vous double-cliquez sur l’icône du bloc-notes, vous démarrez un processus qui exécute le bloc-notes.  
  
 Un thread est un chemin d’accès d’exécution dans un processus. Lorsque vous démarrez le bloc-notes, le système d’exploitation crée un processus et commence l’exécution du thread principal de ce processus. Lorsque ce thread se termine, par conséquent, ne le processus. Ce thread principal est fourni au système d’exploitation par le code de démarrage sous la forme d’une adresse de fonction. En règle générale, il est l’adresse de la **principal** ou `WinMain` fonction qui est fournie.  
  
 Si vous le souhaitez, vous pouvez créer des threads supplémentaires dans votre application. Vous pouvez souhaiter procéder ainsi pour gérer les tâches de maintenance ou en arrière-plan lorsque vous ne souhaitez pas que l’utilisateur d’attendre de leur exécution. Tous les threads dans les applications MFC sont représentés par [CWinThread](../mfc/reference/cwinthread-class.md) objets. Dans la plupart des cas, il est même inutile de créer explicitement ces objets ; à la place appeler la fonction d’assistance de framework [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), ce qui crée le `CWinThread` objet pour vous.  
  
 MFC distingue deux types de threads : les threads de travail et les threads d’interface utilisateur. Threads d’interface utilisateur sont généralement utilisés pour gérer l’entrée d’utilisateur et répondre aux événements et messages générés par l’utilisateur. Threads de travail sont couramment utilisés pour effectuer des tâches, telles que le recalcul, qui ne nécessitent pas d’entrée d’utilisateur. L’API Win32 ne fait pas la distinction entre les types de threads ; Il suffit de connaître l’adresse de départ du thread afin de pouvoir commencer à exécuter le thread. MFC gère les threads d’interface utilisateur en fournissant notamment une pompe de messages pour les événements dans l’interface utilisateur. `CWinApp` est un exemple d’un objet de thread d’interface utilisateur, car il dérive `CWinThread` et gère les événements et messages générés par l’utilisateur.  
  
 Une attention particulière convient aux situations où plusieurs threads peuvent nécessiter un accès au même objet. [Multithreading : Conseils de programmation](../parallel/multithreading-programming-tips.md) décrit les techniques que vous pouvez utiliser pour résoudre les problèmes susceptibles de survenir dans ces situations. [Multithreading : Comment utiliser les Classes de synchronisation](../parallel/multithreading-how-to-use-the-synchronization-classes.md) explique comment utiliser les classes qui sont disponibles pour synchroniser l’accès à partir de plusieurs threads à un objet unique.  
  
 L’écriture et la programmation multithread de débogage sont, par nature, une entreprise complexe et difficile, car vous devez vous assurer que les objets ne sont pas accessibles par plusieurs threads à la fois. Les rubriques de multithreading n’abordent pas les principes fondamentaux de la programmation multithread, comment utiliser les MFC dans un programme multithread. Les exemples MFC multithread inclus dans Visual C++ illustrent quelques Ajout de fonctionnalités et des API Win32 non comprises par MFC ; multithread Toutefois, ils sont uniquement destinés à être un point de départ.  
  
 Pour plus d’informations sur la façon dont le système d’exploitation gère les processus et les threads, consultez [processus et Threads](http://msdn.microsoft.com/library/windows/desktop/ms684841) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Pour plus d’informations sur la prise en charge du multithreading de MFC, consultez les rubriques suivantes :  
  
-   [Multithreading : création de threads d’interface utilisateur](../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [Multithreading : création de threads de travail](../parallel/multithreading-creating-worker-threads.md)  
  
-   [Multithreading : comment utiliser les classes de synchronisation](../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [Multithreading : arrêt d’exécution des threads](../parallel/multithreading-terminating-threads.md)  
  
-   [Multithreading : conseils de programmation](../parallel/multithreading-programming-tips.md)  
  
-   [Multithreading : quand utiliser les classes de synchronisation](../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge du multithreading pour le code plus ancien (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)