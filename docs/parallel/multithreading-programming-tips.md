---
title: 'Multithreading : Conseils de programmation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9c4241b9257244de840db1f57c5e7abcb32f206
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689985"
---
# <a name="multithreading-programming-tips"></a>Multithreading : conseils de programmation
Les applications multithread requièrent une attention plus stricte que les applications mono-lors de l’accès aux données. Car il existe plusieurs chemins d’accès indépendants de l’exécution dans utilisent simultanément dans les applications multithread, les algorithmes, les données ou les deux doivent être prenant en charge ces données peut être utilisé par plusieurs threads à la fois. Cette rubrique décrit des techniques permettant d’éviter les problèmes potentiels lors de la programmation d’applications multithread avec la bibliothèque Microsoft Foundation classes (MFC).  
  
-   [L’accès aux objets à partir de plusieurs Threads](#_core_accessing_objects_from_multiple_threads)  
  
-   [Accès aux objets MFC à partir de Threads Non MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
-   [Cartes de handles Windows](#_core_windows_handle_maps)  
  
-   [Communication entre les Threads](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> L’accès aux objets à partir de plusieurs Threads  
 Pour des raisons de performances et de taille, objets MFC ne sont pas thread-safe au niveau de l’objet, mais uniquement au niveau de la classe. Cela signifie que vous pouvez avoir deux threads distincts qui manipulent deux `CString` objets, mais pas deux threads manipulant le même `CString` objet. Si vous devez absolument avoir plusieurs threads manipulant le même objet, protégez un tel accès avec les mécanismes de synchronisation Win32 appropriés, tels que les sections critiques. Pour plus d’informations sur les sections critiques et d’autres des objets connexes, consultez [synchronisation](http://msdn.microsoft.com/library/windows/desktop/ms686353) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 La bibliothèque de classes utilise les sections critiques en interne pour protéger les structures de données globales, telles que celles utilisées par l’allocation de mémoire de débogage.  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Accès aux objets MFC à partir de Threads Non MFC  
 Si vous avez une application multithread qui crée un thread de manière qu’en utilisant un [CWinThread](../mfc/reference/cwinthread-class.md) de l’objet, vous ne peut pas accéder aux autres objets MFC à partir de ce thread. En d’autres termes, si vous souhaitez accéder à un objet MFC à partir d’un thread secondaire, vous devez créer ce thread avec l’une des méthodes décrites dans [Multithreading : création de Threads d’Interface utilisateur](../parallel/multithreading-creating-user-interface-threads.md) ou [Multithreading : Création de Threads de travail](../parallel/multithreading-creating-worker-threads.md). Ces méthodes sont les seules qui permettent la bibliothèque de classes initialiser les variables internes nécessaires pour gérer des applications multithread.  
  
##  <a name="_core_windows_handle_maps"></a> Cartes de handles Windows  
 En règle générale, un thread peut accéder uniquement les objets MFC qu’il a créées. Il s’agit, car des cartes de handles Windows temporaires et permanents sont conservées dans le stockage local des threads pour aider à assurer la protection contre l’accès simultané de plusieurs threads. Par exemple, un thread de travail ne peut pas effectuer un calcul et appelez ensuite d’un document `UpdateAllViews` fonction membre pour que les tables qui contiennent des vues sur les nouvelles données. Cela n’a aucun effet, car la carte de `CWnd` objets `HWND`est locale pour le thread principal. Cela signifie qu’un thread peut avoir un mappage à partir d’un handle Windows vers un objet C++, mais un autre thread peut mapper le même handle à un autre objet C++. Les modifications effectuées dans un thread apparaîtraient pas dans l’autre.  
  
 Il existe différentes façons de contourner ce problème. La première consiste à passer des handles (par exemple un `HWND`) plutôt que des objets C++ pour le thread de travail. Le thread de travail ajoute ensuite ces objets à sa carte temporaire en appelant approprié `FromHandle` fonction membre. Vous pouvez également ajouter l’objet à la carte permanente du thread en appelant **attacher**, mais cela doit être effectué uniquement si vous avez la garantie que l’objet existe plus longtemps que le thread.  
  
 Une autre méthode consiste à créer de nouveaux messages définis par l’utilisateur correspondant aux différentes tâches que vos threads de travail sera effectuant et valider ces messages à la fenêtre principale de l’application à l’aide de **:: PostMessage**. Cette méthode de communication est similaire à la conversation en cours, sauf que les deux threads sont exécutent dans le même espace d’adressage différentes applications.  
  
 Pour plus d’informations sur les cartes de descripteurs, consultez [Technical Note 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Pour plus d’informations sur le stockage local des threads, consultez [stockage Local des threads](http://msdn.microsoft.com/library/windows/desktop/ms686749) et [stockage Local des threads à l’aide de](http://msdn.microsoft.com/library/windows/desktop/ms686991) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
##  <a name="_core_communicating_between_threads"></a> Communication entre les Threads  
 MFC fournit plusieurs classes qui permettent aux threads synchroniser l’accès aux objets pour maintenir la sécurité des threads. L’utilisation de ces classes est décrite dans [Multithreading : comment utiliser les Classes de synchronisation](../parallel/multithreading-how-to-use-the-synchronization-classes.md) et [Multithreading : quand utiliser les Classes de synchronisation](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Pour plus d’informations sur ces objets, consultez [synchronisation](http://msdn.microsoft.com/library/windows/desktop/ms686353) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C++ et de MFC](../parallel/multithreading-with-cpp-and-mfc.md)