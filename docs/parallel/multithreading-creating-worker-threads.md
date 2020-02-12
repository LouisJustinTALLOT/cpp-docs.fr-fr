---
title: 'Multithreading : création de threads de travail dans MFC'
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
ms.openlocfilehash: ab5b05b64ebcfbd6d15bd2229ee19d18fa7f919d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140514"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>Multithreading : création de threads de travail dans MFC

Un thread de travail est couramment utilisé pour gérer les tâches en arrière-plan que l’utilisateur ne doit pas avoir à attendre pour continuer à utiliser votre application. Les tâches telles que le recalcul et l’impression en arrière-plan sont de bons exemples de threads de travail. Cette rubrique décrit en détail les étapes nécessaires à la création d’un thread de travail. Les sujets abordés sont les suivants :

- [Démarrage du thread](#_core_starting_the_thread)

- [Implémentation de la fonction de contrôle](#_core_implementing_the_controlling_function)

- [Exemple](#_core_controlling_function_example)

La création d’un thread de travail est une tâche relativement simple. Deux étapes sont nécessaires pour que votre thread s’exécute : l’implémentation de la fonction de contrôle et le démarrage du thread. Il n’est pas nécessaire de dériver une classe de [CWinThread](../mfc/reference/cwinthread-class.md). Vous pouvez dériver une classe si vous avez besoin d’une version spéciale de `CWinThread`, mais elle n’est pas requise pour la plupart des threads de travail simples. Vous pouvez utiliser `CWinThread` sans modification.

## <a name="_core_starting_the_thread"></a>Démarrage du thread

Il existe deux versions surchargées de `AfxBeginThread`: une qui peut uniquement créer des threads de travail et une qui peut créer des threads d’interface utilisateur et des threads de travail. Pour commencer l’exécution de votre thread de travail à l’aide de la première surcharge, appelez [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), en fournissant les informations suivantes :

- Adresse de la fonction de contrôle.

- Paramètre à passer à la fonction de contrôle.

- Facultatif Priorité souhaitée du thread. La valeur par défaut est la priorité normale. Pour plus d’informations sur les niveaux de priorité disponibles, consultez [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) dans le SDK Windows.

- Facultatif Taille de pile souhaitée pour le thread. La valeur par défaut est la même pile de taille que le thread de création.

- Facultatif CREATE_SUSPENDED si vous souhaitez que le thread soit créé dans un état suspendu. La valeur par défaut est 0 ou démarre le thread normalement.

- Facultatif Attributs de sécurité souhaités. La valeur par défaut est le même accès que le thread parent. Pour plus d’informations sur le format de ces informations de sécurité, consultez [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) dans le SDK Windows.

`AfxBeginThread` crée et initialise un objet `CWinThread` pour vous, le démarre et retourne son adresse afin que vous puissiez y faire référence ultérieurement. Les vérifications sont effectuées tout au long de la procédure pour s’assurer que tous les objets sont désalloués correctement en cas d’échec d’une partie de la création.

## <a name="_core_implementing_the_controlling_function"></a>Implémentation de la fonction de contrôle

La fonction de contrôle définit le thread. Lorsque cette fonction est entrée, le thread démarre et, lorsqu’il s’arrête, le thread se termine. Cette fonction doit avoir le prototype suivant :

```cpp
UINT MyControllingFunction( LPVOID pParam );
```

Le paramètre est une valeur unique. La valeur que la fonction reçoit dans ce paramètre est la valeur qui a été passée au constructeur lors de la création de l’objet thread. La fonction de contrôle peut interpréter cette valeur de la manière qu’elle choisit. Elle peut être traitée comme une valeur scalaire ou un pointeur vers une structure contenant plusieurs paramètres, ou elle peut être ignorée. Si le paramètre fait référence à une structure, la structure peut être utilisée non seulement pour passer des données de l’appelant au thread, mais également pour repasser les données du thread à l’appelant. Si vous utilisez une telle structure pour renvoyer des données à l’appelant, le thread doit notifier l’appelant lorsque les résultats sont prêts. Pour plus d’informations sur la communication du thread de travail à l’appelant, consultez [Multithreading : conseils de programmation](multithreading-programming-tips.md).

Lorsque la fonction se termine, elle doit retourner une valeur UINT indiquant la raison de l’arrêt. En général, ce code de sortie est 0 pour indiquer la réussite avec d’autres valeurs indiquant les différents types d’erreurs. Cela dépend purement de l’implémentation. Certains threads peuvent conserver le nombre d’utilisations des objets et retourner le nombre actuel d’utilisations de cet objet. Pour voir comment les applications peuvent récupérer cette valeur, consultez [Multithreading : arrêt des threads](multithreading-terminating-threads.md).

Il existe des restrictions sur ce que vous pouvez faire dans un programme multithread écrit avec la bibliothèque MFC. Pour obtenir une description de ces restrictions et d’autres conseils sur l’utilisation des threads, consultez [Multithreading : conseils de programmation](multithreading-programming-tips.md).

## <a name="_core_controlling_function_example"></a>Exemple de fonction de contrôle

L’exemple suivant montre comment définir une fonction de contrôle et l’utiliser à partir d’une autre partie du programme.

```cpp
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
