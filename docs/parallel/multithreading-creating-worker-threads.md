---
title: 'Multithreading : Création de Threads de travail dans MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
ms.openlocfilehash: 54bea7b42018637bf868dfdd923b94dd75aa2307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559482"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>Multithreading : Création de Threads de travail dans MFC

Un thread de travail est couramment utilisé pour gérer les tâches en arrière-plan qui l’utilisateur ne doit pas avoir à attendre pour continuer à utiliser votre application. Tâches telles que le recalcul et l’impression en arrière-plan sont de bons exemples de threads de travail. Cette rubrique décrit en détail les étapes nécessaires pour créer un thread de travail. Les rubriques traitées ici sont les suivantes :

- [Démarrage du thread](#_core_starting_the_thread)

- [Implémentation de la fonction de contrôle](#_core_implementing_the_controlling_function)

- [Exemple](#_core_controlling_function_example)

Création d’un thread de travail est une tâche relativement simple. Seuls deux étapes sont nécessaires pour obtenir de l’exécution du thread : implémentation de la fonction de contrôle et le démarrage du thread. Il n’est pas nécessaire de dériver une classe de [CWinThread](../mfc/reference/cwinthread-class.md). Vous pouvez dériver une classe si vous avez besoin d’une version spéciale de `CWinThread`, mais il n’est pas requis pour la plupart des threads de travail simples. Vous pouvez utiliser `CWinThread` sans modification.

##  <a name="_core_starting_the_thread"></a> Démarrage du Thread

Il existe deux versions surchargées de `AfxBeginThread`: un qui peut seulement créer des threads de travail et un qui peut créer des threads d’interface utilisateur et de threads de travail. Pour commencer l’exécution de votre thread de travail à l’aide de la première surcharge, appelez [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), fournissant les informations suivantes :

- L’adresse de la fonction de contrôle.

- Le paramètre à passer à la fonction de contrôle.

- (Facultatif) La priorité voulue du thread. La valeur par défaut est une priorité normale. Pour plus d’informations sur les niveaux de priorité disponibles, consultez [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

- (Facultatif) La taille de pile pour le thread. La valeur par défaut est la même taille de pile du thread parent.

- (Facultatif) CREATE_SUSPENDED si vous souhaitez que le thread peut être créé dans un état suspendu. La valeur par défaut est 0, ou démarrez le thread normalement.

- (Facultatif) Les attributs de sécurité souhaité. La valeur par défaut est le même accès que le thread parent. Pour plus d’informations sur le format de ces informations de sécurité, consultez [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) dans le SDK Windows.

`AfxBeginThread` Crée et initialise un `CWinThread` objet pour vous, il démarre et retourne son adresse afin de vous y référer ultérieurement. S’assurer que tous les objets sont libérés correctement doit échouer de n’importe quelle partie de la création, les vérifications sont effectuées tout au long de la procédure.

##  <a name="_core_implementing_the_controlling_function"></a> Implémentation de la fonction de contrôle

La fonction de contrôle définit le thread. Lorsque cette fonction est entrée, le thread démarre, et quand il s’arrête, le thread s’arrête. Cette fonction doit avoir le prototype suivant :

```
UINT MyControllingFunction( LPVOID pParam );
```

Le paramètre est une valeur unique. La valeur de que la fonction reçoit dans ce paramètre est la valeur qui a été passée au constructeur lors de l’objet thread a été créé. La fonction de contrôle peut interpréter cette valeur d’une manière quelconque. Il peut être traité comme une valeur scalaire ou un pointeur vers une structure contenant plusieurs paramètres, ou il peut être ignoré. Si le paramètre fait référence à une structure, la structure peut être utilisée pour passer des données à partir de l’appelant au thread, mais également pour passer des données du thread à l’appelant. Si vous utilisez une telle structure pour repasser les données à l’appelant, le thread doit notifier l’appelant quand les résultats sont prêts. Pour plus d’informations sur la communication entre le thread de travail à l’appelant, consultez [Multithreading : conseils de programmation](multithreading-programming-tips.md).

Lorsque la fonction se termine, elle doit retourner une valeur UINT indiquant la raison de l’arrêt. En règle générale, ce code de sortie est 0 pour indiquer la réussite avec d’autres valeurs indiquant les différents types d’erreurs. Il s’agit purement dépend de l’implémentation. Certains threads peuvent mettre à jour les compteurs d’utilisation des objets et retourner le nombre actuel d’utilisations de cet objet. Pour voir comment les applications peuvent récupérer cette valeur, consultez [Multithreading : arrêt de Threads](multithreading-terminating-threads.md).

Il existe certaines restrictions sur ce que vous pouvez faire dans un programme multithread écrit avec la bibliothèque MFC. Pour obtenir une description de ces restrictions et d’autres conseils concernant l’utilisation des threads, consultez [Multithreading : conseils de programmation](multithreading-programming-tips.md).

##  <a name="_core_controlling_function_example"></a> Contrôle de l’exemple de fonction

L’exemple suivant montre comment définir une fonction de contrôle et l’utiliser à partir d’une autre partie du programme.

```
UINT MyThreadProc( LPVOID pParam )
{
    CMyObject* pObject = (CMyObject*)pParam;

    if (pObject == NULL ||
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))
    return 1;   // if pObject is not valid

    // do something with 'pObject'

    return 0;   // thread completed successfully
}

// inside a different function in the program
.
.
.
pNewObject = new CMyObject;
AfxBeginThread(MyThreadProc, pNewObject);
.
.
.
```

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Multithreading : création de threads d’interface utilisateur](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>Voir aussi

[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)