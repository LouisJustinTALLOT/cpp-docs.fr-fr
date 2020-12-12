---
description: 'En savoir plus sur le multithreading : quand utiliser les classes de synchronisation MFC'
title: 'Multithreading : quand utiliser les classes de synchronisation MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 02776bc61ed702ee81ce0f7373dd442a9fc3d446
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149849"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>Multithreading : quand utiliser les classes de synchronisation MFC

Les classes multithread fournies avec MFC se répartissent en deux catégories : les objets de synchronisation ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [CCriticalSection](../mfc/reference/ccriticalsection-class.md)et [CEvent](../mfc/reference/cevent-class.md)) et les objets d’accès de synchronisation ([CMultiLock](../mfc/reference/cmultilock-class.md) et [CSingleLock](../mfc/reference/csinglelock-class.md)).

Les classes de synchronisation sont utilisées lorsque l’accès à une ressource doit être contrôlé pour garantir l’intégrité de la ressource. Les classes d’accès de synchronisation sont utilisées pour accéder à ces ressources contrôlées. Cette rubrique explique quand utiliser chaque classe.

Pour déterminer la classe de synchronisation que vous devez utiliser, posez-vous les questions suivantes :

1. L’application doit-elle attendre qu’un événement se produise avant de pouvoir accéder à la ressource (par exemple, les données doivent être reçues d’un port de communication avant d’être écrites dans un fichier) ?

   Si c’est le cas, utilisez `CEvent` .

2. Plusieurs threads au sein d’une même application peuvent-ils accéder à cette ressource à un moment donné (par exemple, votre application autorise jusqu’à cinq fenêtres avec des vues sur le même document) ?

   Si c’est le cas, utilisez `CSemaphore` .

3. Plusieurs applications peuvent-elles utiliser cette ressource (par exemple, la ressource se trouve dans une DLL) ?

   Si c’est le cas, utilisez `CMutex` .

   Si ce n’est pas le cas, utilisez `CCriticalSection` .

`CSyncObject` n’est jamais utilisé directement. Il s’agit de la classe de base pour les quatre autres classes de synchronisation.

## <a name="example-1-using-three-synchronization-classes"></a>Exemple 1 : utilisation de trois classes de synchronisation

Par exemple, prenez une application qui gère une liste liée de comptes. Cette application permet d’examiner jusqu’à trois comptes dans des fenêtres distinctes, mais une seule peut être mise à jour à un moment donné. Lorsqu’un compte est mis à jour, les données mises à jour sont envoyées sur le réseau à une archive de données.

Cet exemple d’application utilise les trois types de classes de synchronisation. Étant donné qu’il permet d’examiner jusqu’à trois comptes à la fois, il utilise `CSemaphore` pour limiter l’accès à trois objets de vue. Lorsqu’une tentative d’affichage d’un quatrième compte se produit, l’application attend jusqu’à ce que l’une des trois premières fenêtres soit fermée ou qu’elle échoue. Lorsqu’un compte est mis à jour, l’application utilise `CCriticalSection` pour s’assurer qu’un seul compte est mis à jour à la fois. Une fois la mise à jour effectuée, elle signale `CEvent` , ce qui libère un thread en attente de la signalisation de l’événement. Ce thread envoie les nouvelles données à l’archive de données.

## <a name="example-2-using-synchronization-access-classes"></a>Exemple 2 : utilisation des classes d’accès de synchronisation

Le choix de la classe d’accès à la synchronisation à utiliser est encore plus simple. Si votre application s’occupe de l’accès à une seule ressource contrôlée, utilisez `CSingleLock` . S’il a besoin d’accéder à l’une des nombreuses ressources contrôlées, utilisez `CMultiLock` . Dans l’exemple 1, `CSingleLock` aurait été utilisé, car dans chaque cas, une seule ressource est nécessaire à un moment donné.

Pour plus d’informations sur la façon dont les classes de synchronisation sont utilisées, consultez [Multithreading : comment utiliser les classes de synchronisation](multithreading-how-to-use-the-synchronization-classes.md). Pour plus d’informations sur la synchronisation, consultez [synchronisation](/windows/win32/Sync/synchronization) dans le SDK Windows. Pour plus d’informations sur la prise en charge du multithreading dans MFC, consultez [Multithreading avec C++ et MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Voir aussi

[Multithreading à l'aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)
