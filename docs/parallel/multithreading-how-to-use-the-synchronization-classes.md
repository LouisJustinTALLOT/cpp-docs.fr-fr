---
title: 'Multithreading : Comment utiliser les Classes de synchronisation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 49b0737a794216c4899b280bc049a1cdc0fe0948
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689023"
---
# <a name="multithreading-how-to-use-the-synchronization-classes"></a>Multithreading : comment utiliser les classes de synchronisation
La synchronisation de l’accès aux ressources entre les threads d’est un problème courant lors de l’écriture d’applications multithread. Avoir deux ou plusieurs threads qui accèdent simultanément que les mêmes données peuvent entraîner des résultats indésirables et inattendus. Par exemple, un thread peut être mise à jour le contenu d’une structure lors d’un autre thread lit le contenu de la même structure. On ne sait pas quelles données reçoit le thread de lecture : les anciennes données, les données qui vient d’être écrites ou éventuellement un mélange des deux. MFC fournit un nombre de synchronisation et les classes d’accès de synchronisation à l’aide pour résoudre ce problème. Cette rubrique explique les classes disponibles et comment les utiliser pour créer des classes thread-safe dans une application multithread standard.  
  
 Une application multithread standard possède une classe qui représente une ressource à partager entre les threads. Une classe correctement conçue et complètement thread-safe ne nécessite pas d’appeler des fonctions de synchronisation. Tout est géré en interne à la classe, ce qui vous permet de vous concentrer sur la façon d’utiliser au mieux la classe, pas sur la façon dont il risque d’être altérée. Une technique efficace pour la création d’une classe complètement thread-safe consiste à fusionner la classe de synchronisation dans la classe de ressource. La fusion des classes de synchronisation dans la classe partagée est un processus simple.  
  
 Par exemple, prenez une application qui gère une liste liée de comptes. Cette application permet jusqu'à trois comptes doit être examinée dans des fenêtres distinctes, mais une seule peut être mis à jour à un moment donné. Lorsqu’un compte est mis à jour, les données mises à jour sont envoyées sur le réseau à une archive de données.  
  
 Cet exemple d’application utilise les trois types de classes de synchronisation. Étant donné qu’il autorise jusqu'à trois comptes doit être examinée à la fois, il utilise [CSemaphore](../mfc/reference/csemaphore-class.md) pour limiter l’accès à trois objets de vue. Lorsqu’une tentative d’afficher un quatrième compte se produit, l’application attend jusqu'à ce qu’un des trois premières fenêtres se ferme ou elle échoue. Lorsqu’un compte est mis à jour, l’application utilise [CCriticalSection](../mfc/reference/ccriticalsection-class.md) pour vous assurer qu’un seul compte est mis à jour à la fois. Une fois la mise à jour réussit, il signale [CEvent](../mfc/reference/cevent-class.md), ce qui libère un thread en attente de l’événement soit signalé. Ce thread envoie les nouvelles données à l’archive de données.  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> Conception d’une classe à Thread sécurisée  
 Pour créer une classe complètement thread-safe, ajoutez tout d’abord la classe de synchronisation appropriée aux classes partagées en tant qu’un membre de données. Dans l’exemple précédent de la gestion des comptes, un **CSemaphore** membre de données est ajouté à la classe d’affichage, un `CCriticalSection` membre de données est ajouté à la classe de liste liée et un `CEvent` membre de données est ajouté aux données classe de stockage.  
  
 Ensuite, ajoutez des appels de synchronisation pour toutes les fonctions de membre, modifient les données dans la classe ou d’accéder à une ressource contrôlée. Dans chaque fonction, vous devez créer un [CSingleLock](../mfc/reference/csinglelock-class.md) ou [CMultiLock](../mfc/reference/cmultilock-class.md) et appeler l’objet `Lock` (fonction). Lorsque l’objet de verrouillage devient hors de portée et est détruit, le destructeur de l’objet appelle `Unlock` , libérer la ressource. Bien entendu, vous pouvez appeler `Unlock` directement si vous le souhaitez.  
  
 Conception de votre classe à thread sécurisée de cette manière permet de pouvoir être utilisé dans une application multithread aussi facilement qu’une classe non thread-safe, mais avec un niveau plus élevé de sécurité. L’encapsulation de l’objet de synchronisation et d’un objet de synchronisation d’accès dans la classe de la ressource offre tous les avantages de la programmation complètement thread-safe sans l’inconvénient de la gestion d’un code de synchronisation.  
  
 L’exemple de code suivant illustre cette méthode à l’aide d’un membre de données, `m_CritSection` (de type `CCriticalSection`), déclarés dans la classe de ressources partagées et un `CSingleLock` objet. La synchronisation de la ressource partagée (dérivée de `CWinThread`) est tentée en créant un `CSingleLock` de l’objet à l’aide de l’adresse de le `m_CritSection` objet. Une tentative est effectuée pour verrouiller la ressource et, une fois obtenu, le travail est effectué sur l’objet partagé. Lorsque le travail est terminé, la ressource est déverrouillée par un appel à `Unlock`.  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
>  `CCriticalSection`, contrairement aux autres classes de synchronisation MFC, n’a pas la possibilité d’une demande de verrou a expiré. Le délai d’attente d’un thread se libèrent est infini.  
  
 Les inconvénients de cette approche sont que la classe sera légèrement plus lente que la même classe sans les objets de synchronisation ajoutés. En outre, s’il est probable que plusieurs threads risque de supprimer l’objet, l’approche de fusion ne fonctionne pas toujours. Dans ce cas, il est préférable de conserver les objets de synchronisation distinct.  
  
 Pour plus d’informations sur les classes de synchronisation à utiliser dans différentes situations, consultez [Multithreading : quand utiliser les Classes de synchronisation](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Pour plus d’informations sur la synchronisation, consultez [synchronisation](http://msdn.microsoft.com/library/windows/desktop/ms686353) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Pour plus d’informations sur la prise en charge le multithreading dans MFC, consultez [Multithreading à l’aide de C++ et MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C++ et de MFC](../parallel/multithreading-with-cpp-and-mfc.md)