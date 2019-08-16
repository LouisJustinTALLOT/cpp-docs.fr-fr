---
title: 'Multithreading : Comment utiliser les classes de synchronisation MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 26a059e378edb92f5ff7f4e788ded90678e0c129
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511867"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>Multithreading : Comment utiliser les classes de synchronisation MFC

La synchronisation de l’accès aux ressources entre les threads est un problème courant lors de l’écriture d’applications multithread. Le fait d’avoir au moins deux threads accédant simultanément aux mêmes données peut entraîner des résultats indésirables et imprévisibles. Par exemple, un thread peut mettre à jour le contenu d’une structure alors qu’un autre thread lit le contenu de la même structure. Les données reçues par le thread de lecture sont inconnues: les anciennes données, les données récemment écrites, ou éventuellement une combinaison des deux. MFC fournit un certain nombre de classes d’accès de synchronisation et de synchronisation pour faciliter la résolution de ce problème. Cette rubrique explique les classes disponibles et comment les utiliser pour créer des classes thread-safe dans une application multithread classique.

Une application multithread classique a une classe qui représente une ressource à partager entre les threads. Une classe correctement conçue et entièrement thread-safe ne vous oblige pas à appeler des fonctions de synchronisation. Tout est géré en interne à la classe, ce qui vous permet de vous concentrer sur l’utilisation optimale de la classe, et non sur la manière dont elle peut être endommagée. Une technique efficace pour créer une classe entièrement thread-safe consiste à fusionner la classe de synchronisation dans la classe de ressource. La fusion des classes de synchronisation dans la classe partagée est un processus simple.

Par exemple, prenez une application qui gère une liste liée de comptes. Cette application permet d’examiner jusqu’à trois comptes dans des fenêtres distinctes, mais une seule peut être mise à jour à un moment donné. Lorsqu’un compte est mis à jour, les données mises à jour sont envoyées sur le réseau à une archive de données.

Cet exemple d’application utilise les trois types de classes de synchronisation. Étant donné qu’il permet d’examiner jusqu’à trois comptes à la fois, il utilise [CSemaphore](../mfc/reference/csemaphore-class.md) pour limiter l’accès à trois objets de vue. Lorsqu’une tentative d’affichage d’un quatrième compte se produit, l’application attend jusqu’à ce que l’une des trois premières fenêtres soit fermée ou qu’elle échoue. Lorsqu’un compte est mis à jour, l’application utilise [CCriticalSection](../mfc/reference/ccriticalsection-class.md) pour s’assurer qu’un seul compte est mis à jour à la fois. Une fois la mise à jour réussie, elle signale [CEvent](../mfc/reference/cevent-class.md), qui libère un thread en attente de signalement de l’événement. Ce thread envoie les nouvelles données à l’archive de données.

##  <a name="_mfc_designing_a_thread.2d.safe_class"></a>Conception d’une classe thread-safe

Pour rendre une classe entièrement thread-safe, ajoutez d’abord la classe de synchronisation appropriée aux classes partagées en tant que membre de données. Dans l’exemple de gestion de compte précédent, `CSemaphore` un membre de données est ajouté à la classe de vue `CCriticalSection` , un membre de données est ajouté à la classe de liste liée, `CEvent` et un membre de données est ajouté à la classe de stockage de données.

Ensuite, ajoutez des appels de synchronisation à toutes les fonctions membres qui modifient les données dans la classe ou accèdent à une ressource contrôlée. Dans chaque fonction, vous devez créer un objet [CSingleLock](../mfc/reference/csinglelock-class.md) ou [CMultiLock](../mfc/reference/cmultilock-class.md) et appeler la fonction de `Lock` cet objet. Lorsque l’objet Lock est hors de portée et est détruit, le destructeur de l’objet vous `Unlock` appelle pour vous, libérant ainsi la ressource. Bien entendu, vous pouvez appeler `Unlock` directement si vous le souhaitez.

La conception de votre classe thread-safe de cette manière permet de l’utiliser dans une application multithread aussi facilement qu’une classe non thread-safe, mais avec un niveau de sécurité plus élevé. L’encapsulation de l’objet de synchronisation et de l’objet d’accès de synchronisation dans la classe de la ressource offre tous les avantages de la programmation entièrement thread-safe sans l’inconvénient de conserver le code de synchronisation.

L’exemple de code suivant illustre cette méthode à l’aide d’un `m_CritSection` membre de données `CCriticalSection`, (de type), déclaré dans la classe `CSingleLock` de ressources partagées et un objet. La synchronisation de la ressource partagée (dérivée `CWinThread`de) est tentée en `CSingleLock` créant un objet à l’aide `m_CritSection` de l’adresse de l’objet. Une tentative de verrouillage de la ressource a été effectuée et, une fois obtenue, le travail est effectué sur l’objet partagé. Une fois le travail terminé, la ressource est déverrouillée à l' `Unlock`aide d’un appel à.

```
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection`, contrairement aux autres classes de synchronisation MFC, n’a pas l’option d’une demande de verrou chronométré. La période d’attente pour qu’un thread devienne libre est infinie.

L’inconvénient de cette approche est que la classe sera légèrement plus lente que la même classe sans les objets de synchronisation ajoutés. De même, s’il existe un risque que plusieurs threads puissent supprimer l’objet, l’approche fusionnée ne fonctionnera peut-être pas toujours. Dans ce cas, il est préférable de gérer des objets de synchronisation distincts.

Pour plus d’informations sur la détermination de la classe de synchronisation à utiliser [dans différentes situations, consultez Multithreading: Quand utiliser les classes](multithreading-when-to-use-the-synchronization-classes.md)de synchronisation. Pour plus d’informations sur la synchronisation, consultez [synchronisation](/windows/win32/Sync/synchronization) dans le SDK Windows. Pour plus d’informations sur la prise en charge du multithreading dans MFC, consultez Multithreading [ C++ avec et MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)
