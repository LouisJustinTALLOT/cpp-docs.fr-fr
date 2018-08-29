---
title: 'Multithreading : Comment utiliser les Classes de synchronisation MFC | Microsoft Docs'
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e36f63f74a0edc1f6cbcf28b85adceed954cce3d
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131260"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>Multithreading : Comment utiliser les Classes de synchronisation MFC
Synchronisation d’accès aux ressources entre les threads d’est un problème courant lors de l’écriture d’applications multithread. Avoir deux ou plusieurs threads qui accèdent simultanément que les mêmes données peuvent produire des résultats indésirables et inattendus. Par exemple, un seul thread peut être mise à jour le contenu d’une structure pendant un autre thread lit le contenu de la même structure. Il est inconnu à quelles données reçoit le thread de lecture : les anciennes données, les données qui vient d’être écrites ou éventuellement un mélange des deux. MFC fournit un nombre de synchronisation et les classes d’accès de synchronisation pour vous aider à résoudre ce problème. Cette rubrique explique les classes disponibles et comment les utiliser pour créer des classes thread-safe dans une application multithread standard.  
  
Une application multithread standard a une classe qui représente une ressource à partager entre les threads. Une classe correctement conçue et complètement thread-safe vous dispense d’appeler des fonctions de synchronisation. Tout est géré en interne à la classe, ce qui vous permet de vous concentrer sur la meilleure façon d’utiliser la classe, pas sur la façon dont il peut être corrompu. Une technique efficace pour la création d’une classe entièrement thread-safe consiste à fusionner la classe de synchronisation dans la classe de ressource. Fusionner les classes de synchronisation dans la classe partagée est un processus simple.  
  
Par exemple, prenez une application qui gère une liste liée de comptes. Cette application permet jusqu'à trois comptes doit être examinée dans des fenêtres distinctes, mais seul l’un peut être mis à jour à un moment donné. Lorsqu’un compte est mis à jour, les données mises à jour sont envoyées sur le réseau à une archive de données.  
  
Cet exemple d’application utilise les trois types de classes de synchronisation. Car elle autorise jusqu'à trois comptes doit être examinée à la fois, elle utilise [CSemaphore](../mfc/reference/csemaphore-class.md) pour limiter l’accès à trois objets de vue. Lorsqu’une tentative d’afficher un quatrième compte se produit, l’application attend jusqu'à ce qu’une des trois premières fenêtres se ferme ou elle échoue. Lorsqu’un compte est mis à jour, l’application utilise [CCriticalSection](../mfc/reference/ccriticalsection-class.md) pour vous assurer qu’un seul compte est mis à jour à la fois. Une fois la mise à jour réussit, il signale [CEvent](../mfc/reference/cevent-class.md), ce qui libère un thread en attente de l’événement soit signalé. Ce thread envoie les nouvelles données à l’archive de données.  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> Conception d’une classe Thread-Safe  
 
Pour rendre une classe entièrement thread-safe, ajoutez tout d’abord la classe de synchronisation appropriée aux classes partagées en tant qu’un membre de données. Dans l’exemple précédent de la gestion des comptes, un `CSemaphore` membre de données serait ajouté à la classe d’affichage, un `CCriticalSection` membre de données serait ajouté à la classe de liste liée et un `CEvent` membre de données serait ajouté à la classe de stockage de données.  
  
Ensuite, ajoutez des appels de synchronisation pour toutes les fonctions membres qui modifient les données dans la classe ou accéder à une ressource contrôlée. Dans chaque fonction, vous devez créer soit un [CSingleLock](../mfc/reference/csinglelock-class.md) ou [CMultiLock](../mfc/reference/cmultilock-class.md) et appeler l’objet `Lock` (fonction). Lorsque l’objet de verrouillage devient hors de portée et est détruit, le destructeur de l’objet appelle `Unlock` pour vous, libérer la ressource. Bien sûr, vous pouvez appeler `Unlock` directement si vous le souhaitez.  
  
Conception de votre classe de thread-safe de cette manière permet de pouvoir être utilisé dans une application multithread comme facilement une classe non thread-safe, mais avec un niveau plus élevé de sécurité. L’encapsulation de l’objet de synchronisation et l’objet d’accès de synchronisation dans la classe de la ressource offre tous les avantages de la programmation entièrement thread-safe sans l’inconvénient de la maintenance du code de synchronisation.  
  
L’exemple de code suivant illustre cette méthode à l’aide d’un membre de données, `m_CritSection` (de type `CCriticalSection`), déclarés dans la classe de ressources partagées et un `CSingleLock` objet. La synchronisation de la ressource partagée (dérivée de `CWinThread`) est tentée en créant un `CSingleLock` à l’aide de l’adresse de l’objet le `m_CritSection` objet. Une tentative est effectuée pour verrouiller la ressource et, une fois obtenu, le travail est effectué sur l’objet partagé. Lorsque le travail est terminé, la ressource est déverrouillée par un appel à `Unlock`.  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
> `CCriticalSection`, contrairement aux autres classes de synchronisation MFC, n’a pas la possibilité d’une demande de verrou a expiré. Le délai d’attente pour un thread se libèrent est infini.  
  
Les inconvénients de cette approche sont que la classe sera légèrement plus lente que la même classe sans les objets de synchronisation ajoutés. En outre, s’il est probable que plusieurs threads peuvent supprimer l’objet, l’approche de fusion ne fonctionne pas toujours. Dans ce cas, il est préférable de conserver les objets de synchronisation distinct.  
  
Pour plus d’informations sur la détermination de la classe de synchronisation à utiliser dans différentes situations, consultez [Multithreading : quand utiliser les Classes de synchronisation](multithreading-when-to-use-the-synchronization-classes.md). Pour plus d’informations sur la synchronisation, consultez [synchronisation](/windows/desktop/Sync/synchronization) dans le SDK Windows. Pour plus d’informations sur la prise en charge le multithreading dans MFC, consultez [Multithreading à l’aide de C++ et MFC](multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 
[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)