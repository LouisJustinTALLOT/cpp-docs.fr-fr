---
title: 'Comment : envoyer un Message à intervalles réguliers | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6903a7ec6b833f7591afe79dc91d453b3905cc79
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705248"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Comment : envoyer un message à intervalles réguliers
Cet exemple montre comment utiliser l’accès concurrentiel ::[classe timer](../../parallel/concrt/reference/timer-class.md) pour envoyer un message à intervalles réguliers.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise un `timer` objet pour signaler la progression pendant une longue opération. Cet exemple lie le `timer` de l’objet à un [concurrency::call](../../parallel/concrt/reference/call-class.md) objet. Le `call` objet imprime un indicateur de progression dans la console à intervalles réguliers. Le [Concurrency::Timer :: Start](reference/timer-class.md#start) méthode exécute la minuterie sur un contexte distinct. Le `perform_lengthy_operation` les appels de fonction le [concurrency::wait](reference/concurrency-namespace-functions.md#wait) fonction sur le contexte principal pour simuler une longue opération.  

  
 [!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
Performing a lengthy operation..........done.  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `report-progress.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /EHsc report-progress.cpp**  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)   
 [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)
