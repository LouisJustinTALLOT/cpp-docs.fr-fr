---
title: Écriture d’un programme Win32 multithread | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- thread stacks [C++]
- resources [C++], multithreading
- stacks [C++]
- shared resources [C++]
- threading [C++], sharing common resources
- multithreading [C++], thread stacks
- multithreading [C++], sharing common resources
- mutual exclusion [C++]
- communications [C++], between threads
- mutex [C++]
- threading [C++], thread stacks
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d88add7830316ae192a728f9c9ff10320657eaf
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="writing-a-multithreaded-win32-program"></a>Écriture d'un programme Win32 multithread
Lorsque vous écrivez un programme avec plusieurs threads, vous devez coordonner leur comportement et [d’utiliser les ressources du programme](#_core_sharing_common_resources_between_threads). Vous devez également vous assurer que chaque thread reçoit [sa propre pile](#_core_thread_stacks).  
  
##  <a name="_core_sharing_common_resources_between_threads"></a> Partager des ressources communes entre les Threads  
  
> [!NOTE]
>  Pour obtenir une description similaire à partir du point de vue MFC, consultez [Multithreading : conseils de programmation](../parallel/multithreading-programming-tips.md) et [Multithreading : quand utiliser les Classes de synchronisation](../parallel/multithreading-when-to-use-the-synchronization-classes.md).  
  
 Chaque thread possède sa propre pile et sa propre copie de l’UC est inscrit. Autres ressources, telles que les fichiers, les données statiques et le tas, sont partagées par tous les threads dans le processus. Les threads à l’aide de ces ressources communes doivent être synchronisés. Win32 fournit plusieurs méthodes de synchronisation des ressources, y compris les mutex, les sections critiques, les événements et les sémaphores.  
  
 Lorsque plusieurs threads accèdent à des données statiques, votre programme doit fournir les conflits de ressources possible. Considérons un programme où un thread met à jour une structure de données statiques contenant *x*,*y* coordonnées pour les éléments à afficher par un autre thread. Si le thread de mise à jour modifie le *x* coordonner et est interrompu avant d’avoir modifié le *y* coordonnée, le thread d’affichage peut être planifié avant les *y* coordonnée est mise à jour. L’élément sera affiché à l’emplacement approprié. Vous pouvez éviter ce problème à l’aide des sémaphores pour contrôler l’accès à la structure.  
  
 Un mutex (abréviation de *doivent*journalisation des accès utilisateur *ex*clusion) est un moyen de communication entre les threads ou processus qui sont exécutent de manière asynchrone des autres. Cette communication est généralement utilisée pour coordonner les activités de plusieurs threads ou processus, généralement en contrôlant l’accès à une ressource partagée par le verrouillage et déverrouillage de la ressource. Pour résoudre ce problème *x*,*y* problème de mise à jour de coordonnées, le thread de mise à jour définit un mutex indiquant que la structure de données est en cours d’utilisation avant d’effectuer la mise à jour. Il suffit de désactiver le mutex une fois les deux coordonnées avaient été traitées. Le thread d’affichage doit attendre le mutex ait été supprimé avant la mise à jour de l’affichage. Ce processus d’attente d’un mutex est souvent appelé blocage sur un mutex, car le processus est bloqué et ne peut pas continuer jusqu'à ce que la disparition du mutex.  
  
 Le programme Bounce.c affiché dans [exemple de programme multithread en langage C](../parallel/sample-multithread-c-program.md) utilise un mutex nommé `ScreenMutex` pour coordonner les mises à jour de l’écran. Chaque fois qu’un des threads de l’affichage est prêt à écrire vers l’écran, il appelle **WaitForSingleObject** avec le handle de `ScreenMutex` et constante **infinie** pour indiquer que le  **WaitForSingleObject** appel doit blocage sur le mutex et ne pas expirer. Si `ScreenMutex` est désactivée, la fonction d’attente définit le mutex afin d’autres threads ne peut pas interférer avec l’affichage et continue l’exécution du thread. Sinon, le thread se bloque jusqu'à ce que la disparition du mutex. Lorsque le thread termine la mise à jour de l’affichage, il libère le mutex en appelant **ReleaseMutex**.  
  
 Écran s’affiche et les données statiques ne sont que deux des ressources nécessitant une gestion. Par exemple, votre programme peut avoir plusieurs threads accèdent au même fichier. Comme un autre thread peut avoir déplacé le pointeur de fichier, chaque thread doit redéfinir le pointeur de fichier avant de lire ou écrire. En outre, chaque thread doit vérifier qu’il n’est pas interrompu entre l’heure qu'il positionne le pointeur et l’heure qu'il accède au fichier. Ces threads doivent utiliser un sémaphore pour coordonner l’accès au fichier en délimitant chaque accès de fichier avec **WaitForSingleObject** et **ReleaseMutex** appels. L’exemple de code suivant illustre cette technique :  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a> Piles des threads  
 Tout espace de pile par défaut d’une application est alloué au premier thread d’exécution, le thread 1. Par conséquent, vous devez spécifier la quantité de mémoire à allouer à une pile distincte pour chaque thread supplémentaire de votre programme a besoin. Le système d’exploitation alloue de l’espace de pile supplémentaire pour le thread, si nécessaire, mais vous devez spécifier une valeur par défaut.  
  
 Le premier argument de la `_beginthread` appel est un pointeur vers le **BounceProc** (fonction), qui exécute les threads. Le deuxième argument spécifie la taille de pile par défaut pour le thread. Le dernier argument est un numéro d’ID qui est passé à **BounceProc**. **BounceProc** utilise le numéro d’ID pour amorcer le Générateur de nombres aléatoires et sélectionner un attribut de couleur du thread et afficher de caractères.  
  
 Les threads qui effectuent des appels à la bibliothèque Runtime C ou à l’API Win32 doivent prévoir suffisamment d’espace pile pour la bibliothèque et les fonctions API qu’ils appellent. C `printf` fonction requiert plus de 500 octets d’espace de pile, et vous devez disposer de 2 Ko d’espace de pile lors de l’appel des routines de l’API Win32.  
  
 Étant donné que chaque thread possède sa propre pile, vous pouvez éviter les collisions potentielles sur les éléments de données à l’aide de peu de données statiques que possible. Concevez votre programme à utiliser des variables de pile automatiques pour toutes les données qui peuvent être privées à un thread. Les seules variables globales du programme Bounce.c sont soit les mutex soit les variables qui ne changent jamais une fois qu’elles sont initialisées.  
  
 Win32 fournit également un stockage Local des threads (TLS) pour stocker les données par thread. Pour plus d’informations, consultez [stockage Local des threads (TLS)](../parallel/thread-local-storage-tls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C et de Win32](../parallel/multithreading-with-c-and-win32.md)