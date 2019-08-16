---
title: 'Multithreading : Quand utiliser les classes de synchronisation MFC'
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
ms.openlocfilehash: cb68487e036093ce4718c39c18c9d1e75afe0f7c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512002"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>Multithreading : Quand utiliser les classes de synchronisation MFC

Les classes multithread fournies avec MFC se répartissent en deux catégories: les objets de synchronisation ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [CCriticalSection](../mfc/reference/ccriticalsection-class.md)et [CEvent](../mfc/reference/cevent-class.md)) et les objets d’accès de synchronisation ([ CMultiLock](../mfc/reference/cmultilock-class.md) et [CSingleLock](../mfc/reference/csinglelock-class.md)).

Les classes de synchronisation sont utilisées lorsque l’accès à une ressource doit être contrôlé pour garantir l’intégrité de la ressource. Les classes d’accès de synchronisation sont utilisées pour accéder à ces ressources contrôlées. Cette rubrique explique quand utiliser chaque classe.

Pour déterminer la classe de synchronisation que vous devez utiliser, posez-vous les questions suivantes:

1. L’application doit-elle attendre qu’un événement se produise avant de pouvoir accéder à la ressource (par exemple, les données doivent être reçues d’un port de communication avant d’être écrites dans un fichier)?

   Si c’est le `CEvent`cas, utilisez.

2. Plusieurs threads au sein d’une même application peuvent-ils accéder à cette ressource à un moment donné (par exemple, votre application autorise jusqu’à cinq fenêtres avec des vues sur le même document)?

   Si c’est le `CSemaphore`cas, utilisez.

3. Plusieurs applications peuvent-elles utiliser cette ressource (par exemple, la ressource se trouve dans une DLL)?

   Si c’est le `CMutex`cas, utilisez.

   Si ce n’est `CCriticalSection`pas le cas, utilisez.

`CSyncObject`n’est jamais utilisé directement. Il s’agit de la classe de base pour les quatre autres classes de synchronisation.

## <a name="example-1-using-three-synchronization-classes"></a>Exemple 1 : Utilisation de trois classes de synchronisation

Par exemple, prenez une application qui gère une liste liée de comptes. Cette application permet d’examiner jusqu’à trois comptes dans des fenêtres distinctes, mais une seule peut être mise à jour à un moment donné. Lorsqu’un compte est mis à jour, les données mises à jour sont envoyées sur le réseau à une archive de données.

Cet exemple d’application utilise les trois types de classes de synchronisation. Étant donné qu’il permet d’examiner jusqu’à trois comptes à la fois, il `CSemaphore` utilise pour limiter l’accès à trois objets de vue. Lorsqu’une tentative d’affichage d’un quatrième compte se produit, l’application attend jusqu’à ce que l’une des trois premières fenêtres soit fermée ou qu’elle échoue. Lorsqu’un compte est mis à jour, l' `CCriticalSection` application utilise pour s’assurer qu’un seul compte est mis à jour à la fois. Une fois la mise à jour effectuée, `CEvent`elle signale, ce qui libère un thread en attente de la signalisation de l’événement. Ce thread envoie les nouvelles données à l’archive de données.

## <a name="example-2-using-synchronization-access-classes"></a>Exemple 2 : Utilisation des classes d’accès de synchronisation

Le choix de la classe d’accès à la synchronisation à utiliser est encore plus simple. Si votre application s’occupe de l’accès à une seule ressource contrôlée, utilisez `CSingleLock`. S’il a besoin d’accéder à l’une des nombreuses ressources contrôlées, `CMultiLock`utilisez. Dans l’exemple 1 `CSingleLock` , aurait été utilisé, car dans chaque cas, une seule ressource est nécessaire à un moment donné.

Pour plus d’informations sur la façon dont les classes de [synchronisation sont utilisées, consultez Multithreading: Comment utiliser les classes](multithreading-how-to-use-the-synchronization-classes.md)de synchronisation. Pour plus d’informations sur la synchronisation, consultez [synchronisation](/windows/win32/Sync/synchronization) dans le SDK Windows. Pour plus d’informations sur la prise en charge du multithreading dans MFC, consultez Multithreading [ C++ avec et MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)
