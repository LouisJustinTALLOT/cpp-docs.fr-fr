---
title: 'Multithreading : Quand utiliser les Classes de synchronisation MFC | Microsoft Docs'
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d88bb98388aaedac9499ab91ad94bef085c0b702
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132264"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>Multithreading : Quand utiliser les Classes de synchronisation MFC
Les classes multithread fournies avec MFC se répartissent en deux catégories : les objets de synchronisation ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [ CCriticalSection](../mfc/reference/ccriticalsection-class.md), et [CEvent](../mfc/reference/cevent-class.md)) et accéder aux objets de synchronisation ([CMultiLock](../mfc/reference/cmultilock-class.md) et [CSingleLock](../mfc/reference/csinglelock-class.md)).  
  
Classes de synchronisation sont utilisées lors de l’accès à une ressource doit être contrôlé pour garantir l’intégrité de la ressource. Classes d’accès de synchronisation sont utilisées pour accéder à ces ressources contrôlées. Cette rubrique explique quand utiliser chaque classe.  
  
Pour déterminer quelle classe de synchronisation que vous devez utiliser, demandez à la série de questions suivante :  
  
1. L’application doit attendre que quelque chose se produise avant d’accéder à la ressource (par exemple, données doivent être reçues à partir d’un port de communication avant de pouvoir écrire dans un fichier) ?  
  
     Si Oui, utilisez `CEvent`.  
  
2. Pouvez plusieurs threads dans le même accès aux applications cette ressource en même temps (par exemple, votre application autorise jusqu'à cinq fenêtres avec des vues sur le même document) ?  
  
     Si Oui, utilisez `CSemaphore`.  
  
3. Plusieurs applications permettent de cette ressource (par exemple, la ressource est dans une DLL) ?  
  
     Si Oui, utilisez `CMutex`.  
  
     Sinon, utilisez `CCriticalSection`.  
  
`CSyncObject` est jamais utilisé directement. Il est la classe de base pour les quatre autres classes de synchronisation.  
  
## <a name="example-1-using-three-synchronization-classes"></a>Exemple 1 : Utilisation de trois Classes de synchronisation  
 
Par exemple, prenez une application qui gère une liste liée de comptes. Cette application permet jusqu'à trois comptes doit être examinée dans des fenêtres distinctes, mais seul l’un peut être mis à jour à un moment donné. Lorsqu’un compte est mis à jour, les données mises à jour sont envoyées sur le réseau à une archive de données.  
  
Cet exemple d’application utilise les trois types de classes de synchronisation. Comme il autorise jusqu'à trois comptes doit être examinée à la fois, il utilise `CSemaphore` pour limiter l’accès à trois objets de vue. Lorsqu’une tentative d’afficher un quatrième compte se produit, l’application attend jusqu'à ce qu’une des trois premières fenêtres se ferme ou elle échoue. Lorsqu’un compte est mis à jour, l’application utilise `CCriticalSection` pour vous assurer qu’un seul compte est mis à jour à la fois. Une fois la mise à jour réussit, il signale `CEvent`, ce qui libère un thread en attente de l’événement soit signalé. Ce thread envoie les nouvelles données à l’archive de données.  
  
## <a name="example-2-using-synchronization-access-classes"></a>Exemple 2 : Utilisation des Classes d’accès de synchronisation  
 
Choisir les classes d’accès de synchronisation à utiliser sont encore plus simple. Si votre application est concernée par l’accès à une seule ressource contrôlée, utilisez `CSingleLock`. Si elle a besoin d’accéder à l’une des nombreuses ressources contrôlées, utilisez `CMultiLock`. Dans l’exemple 1, `CSingleLock` aurait été utilisé, car dans chaque cas qu’une seule ressource est nécessaire à un moment donné.  
  
Pour plus d’informations sur l’utilisation des classes de synchronisation, consultez [Multithreading : comment utiliser les Classes de synchronisation](multithreading-how-to-use-the-synchronization-classes.md). Pour plus d’informations sur la synchronisation, consultez [synchronisation](/windows/desktop/Sync/synchronization) dans le SDK Windows. Pour plus d’informations sur la prise en charge le multithreading dans MFC, consultez [Multithreading à l’aide de C++ et MFC](multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 
[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)