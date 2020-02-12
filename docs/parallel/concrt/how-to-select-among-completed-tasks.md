---
title: 'Comment : effectuer une sélection parmi les tâches terminées'
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 75ecac8dd0e8845401e3e287e8c95ea614055970
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142471"
---
# <a name="how-to-select-among-completed-tasks"></a>Comment : effectuer une sélection parmi les tâches terminées

Cet exemple montre comment utiliser les classes [Concurrency :: Choice](../../parallel/concrt/reference/choice-class.md) et [Concurrency :: Join](../../parallel/concrt/reference/join-class.md) pour sélectionner la première tâche afin de terminer un algorithme de recherche.

## <a name="example"></a>Exemple

L’exemple suivant exécute deux algorithmes de recherche en parallèle et sélectionne le premier algorithme à terminer. Cet exemple définit le type de `employee`, qui contient un identificateur numérique et un salaire pour un employé. La fonction `find_employee` recherche le premier employé qui a l’identificateur fourni ou le salaire fourni. La fonction `find_employee` gère également le cas où aucun employé n’a l’identificateur ou le salaire fourni. La fonction `wmain` crée un tableau d’objets `employee` et recherche plusieurs valeurs d’identificateur et de salaire.

L’exemple utilise un objet `choice` pour effectuer une sélection parmi les cas suivants :

1. Un employé qui a l’identificateur fourni existe.

1. Un employé qui a le salaire fourni existe.

1. Aucun employé ayant l’identificateur ou le salaire fourni n’existe.

Pour les deux premiers cas, l’exemple utilise un objet [Concurrency :: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) pour contenir l’identificateur et un autre objet `single_assignment` pour contenir le salaire. L’exemple utilise un objet `join` pour le troisième cas. L’objet `join` est composé de deux objets `single_assignment` supplémentaires, l’un pour le cas où aucun employé ayant l’identificateur fourni n’existe, et l’autre pour le cas où aucun employé ayant le salaire fourni n’existe. L’objet `join` envoie un message lorsque chacun de ses membres reçoit un message. Dans cet exemple, l’objet `join` envoie un message lorsqu’il n’existe aucun employé ayant l’identificateur ou le salaire fourni.

L’exemple utilise un objet [Concurrency :: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) pour exécuter les deux algorithmes de recherche en parallèle. Chaque tâche de recherche écrit dans l’un des objets `single_assignment` pour indiquer si l’employé donné existe. L’exemple utilise la fonction [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) pour obtenir l’index de la première mémoire tampon qui contient un message et un bloc `switch` pour imprimer le résultat.

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

Cet exemple utilise la fonction d’assistance [Concurrency :: make_choice](reference/concurrency-namespace-functions.md#make_choice) pour créer des objets `choice` et la fonction d’assistance [Concurrency :: make_join](reference/concurrency-namespace-functions.md#make_join) pour créer des objets `join`.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `find-employee.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Find-Employee. cpp**

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
[choice, classe](../../parallel/concrt/reference/choice-class.md)<br/>
[join, classe](../../parallel/concrt/reference/join-class.md)
