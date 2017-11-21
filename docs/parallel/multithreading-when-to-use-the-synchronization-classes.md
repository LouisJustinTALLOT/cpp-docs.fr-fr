---
title: "Multithreading : Quand utiliser les Classes de synchronisation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b72b3ffac2c4c295aa997e43e52b0bf5e67fe985
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="multithreading-when-to-use-the-synchronization-classes"></a>Multithreading : quand utiliser les classes de synchronisation
Les classes multithreads fournies avec MFC se répartissent en deux catégories : les objets de synchronisation ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [ CCriticalSection](../mfc/reference/ccriticalsection-class.md), et [CEvent](../mfc/reference/cevent-class.md)) et accéder aux objets de synchronisation ([CMultiLock](../mfc/reference/cmultilock-class.md) et [CSingleLock](../mfc/reference/csinglelock-class.md)).  
  
 Classes de synchronisation sont utilisées lors de l’accès à une ressource doit être contrôlé pour garantir l’intégrité de la ressource. Classes d’accès de synchronisation sont utilisées pour accéder à ces ressources contrôlées. Cette rubrique explique quand utiliser chaque classe.  
  
 Pour déterminer les classes de synchronisation que vous devez utiliser, demandez à la série de questions suivante :  
  
1.  L’application doit attendre que quelque chose se produise avant d’accéder à la ressource (par exemple, données doivent être reçues à partir d’un port de communication avant qu’il peut être écrit dans un fichier) ?  
  
     Si Oui, utiliser `CEvent`.  
  
2.  Peut plusieurs threads dans le même accès à l’application cette ressource en même temps (par exemple, votre application autorise jusqu'à cinq fenêtres avec des vues sur le même document) ?  
  
     Si Oui, utiliser `CSemaphore`.  
  
3.  Plusieurs applications peuvent utiliser cette ressource (par exemple, la ressource est dans une DLL) ?  
  
     Si Oui, utiliser `CMutex`.  
  
     Sinon, utilisez `CCriticalSection`.  
  
 **CSyncObject** n’est jamais utilisée directement. Il est la classe de base pour les quatre autres classes de synchronisation.  
  
## <a name="example-1-using-three-synchronization-classes"></a>Exemple 1 : Utilisation de trois Classes de synchronisation  
 Par exemple, prenez une application qui gère une liste liée de comptes. Cette application permet jusqu'à trois comptes doit être examinée dans des fenêtres distinctes, mais une seule peut être mis à jour à un moment donné. Lorsqu’un compte est mis à jour, les données mises à jour sont envoyées sur le réseau à une archive de données.  
  
 Cet exemple d’application utilise les trois types de classes de synchronisation. Étant donné qu’il autorise jusqu'à trois comptes doit être examinée à la fois, il utilise `CSemaphore` pour limiter l’accès à trois objets de vue. Lorsqu’une tentative d’afficher un quatrième compte se produit, l’application attend jusqu'à ce qu’un des trois premières fenêtres se ferme ou elle échoue. Lorsqu’un compte est mis à jour, l’application utilise `CCriticalSection` pour vous assurer qu’un seul compte est mis à jour à la fois. Une fois la mise à jour réussit, il signale `CEvent`, ce qui libère un thread en attente de l’événement soit signalé. Ce thread envoie les nouvelles données à l’archive de données.  
  
## <a name="example-2-using-synchronization-access-classes"></a>Exemple 2 : Utilisation des Classes d’accès de synchronisation  
 Choisir les classes d’accès de synchronisation à utiliser sont encore plus simple. Si votre application est concernée par l’accès à une seule ressource contrôlée, utilisez `CSingleLock`. Si elle a besoin d’accéder à l’une des diverses ressources contrôlées, utilisez `CMultiLock`. Dans l’exemple 1, `CSingleLock` aurait été utilisé, car dans chaque cas, une seule ressource est nécessaire à un moment donné.  
  
 Pour plus d’informations sur l’utilisation des classes de synchronisation, consultez [Multithreading : comment utiliser les Classes de synchronisation](../parallel/multithreading-how-to-use-the-synchronization-classes.md). Pour plus d’informations sur la synchronisation, consultez [synchronisation](http://msdn.microsoft.com/library/windows/desktop/ms686353) dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Pour plus d’informations sur la prise en charge le multithreading dans MFC, consultez [Multithreading à l’aide de C++ et MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Multithreading à l’aide de C++ et de MFC](../parallel/multithreading-with-cpp-and-mfc.md)