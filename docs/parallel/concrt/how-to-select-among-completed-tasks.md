---
title: 'Comment : sélectionner parmi les tâches terminées | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a485eb87f2caa62a382983c1cda2b9c098742d42
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-select-among-completed-tasks"></a>Comment : effectuer une sélection parmi les tâches terminées
Cet exemple montre comment utiliser le [classes concurrency::choice](../../parallel/concrt/reference/choice-class.md) et [concurrency::join](../../parallel/concrt/reference/join-class.md) des classes pour sélectionner la première tâche afin de terminer un algorithme de recherche.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant effectue deux algorithmes de recherche en parallèle et sélectionne le premier algorithme à terminer. Cet exemple définit le `employee` type, qui conserve un identificateur numérique et un salaire pour un employé. Le `find_employee` fonction recherche le premier employé qui a l’identificateur fourni ou le salaire fourni. Le `find_employee` fonction gère également le cas où aucun employé n’a l’identificateur ou salaire fourni. Le `wmain` fonction crée un tableau de `employee` objets et recherche plusieurs valeurs de salaire et d’identificateur.  
  
 L’exemple utilise un `choice` objet à sélectionner parmi les cas suivants :  
  
1.  Il existe un employé qui a l’identificateur fourni.  
  
2.  Il existe un employé qui a le salaire fourni.  
  
3.  Aucun employé qui a l’identificateur fourni ou le salaire n’existe.  
  
 Les deux premiers cas, l’exemple utilise un [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) pour contenir l’identificateur et un autre objet `single_assignment` objet pour stocker le salaire. L’exemple utilise un `join` objet pour le troisième cas. Le `join` objet est composé de deux autres `single_assignment` objets, un pour le cas où aucun employé qui a l’identificateur fourni n’existe et un pour le cas où aucun employé qui a le salaire fourni n’existe. Le `join` objet envoie un message lorsque chacun de ses membres reçoit un message. Dans cet exemple, le `join` objet envoie un message lorsque aucun employé qui a l’identificateur fourni ou salaire existe.  
  
 L’exemple utilise un [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objet pour exécuter les deux algorithmes de recherche en parallèle. Chaque tâche de recherche écrit dans l’un de le `single_assignment` objets pour indiquer si l’employé donné existe. L’exemple utilise le [concurrency::receive](reference/concurrency-namespace-functions.md#receive) fonction pour obtenir l’index de la première mémoire tampon qui contient un message et un `switch` bloc pour imprimer le résultat.  
  
 [!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]  
  
 Cet exemple produit la sortie suivante.  
  
```Output  
Employee with id 14758 has salary 27780.00.  
Employee with salary 29150.00 has id 84345.  
Employee with id 61935 has salary 29905.00.  
No employee has id 899 or salary 31223.00.  
```  
  
 Cet exemple utilise le [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) fonction d’assistance pour créer `choice` objets et la [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) fonction d’assistance pour créer `join` objets.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `find-employee.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /EHsc find-Employee.cpp**  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)   
 [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)   
 [Classe Choice](../../parallel/concrt/reference/choice-class.md)   
 [join, classe](../../parallel/concrt/reference/join-class.md)
