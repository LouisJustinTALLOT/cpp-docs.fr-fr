---
title: 'Comment : envoyer un message à intervalles réguliers'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: 05777b0c00f587f588a50733d5113d9a7362d247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549615"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Comment : envoyer un message à intervalles réguliers

Cet exemple montre comment utiliser l’accès concurrentiel ::[classe timer](../../parallel/concrt/reference/timer-class.md) pour envoyer un message à intervalles réguliers.

## <a name="example"></a>Exemple

L’exemple suivant utilise un `timer` objet pour signaler la progression pendant une longue opération. Cet exemple lie la `timer` de l’objet à un [concurrency::call](../../parallel/concrt/reference/call-class.md) objet. Le `call` objet imprime un indicateur de progression dans la console à intervalles réguliers. Le [Concurrency::Timer :: Start](reference/timer-class.md#start) méthode exécute la minuterie sur un contexte distinct. Le `perform_lengthy_operation` appels de fonction le [concurrency::wait](reference/concurrency-namespace-functions.md#wait) fonction sur le contexte principal pour simuler une opération longue.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Cet exemple produit la sortie suivante :

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `report-progress.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc report-progress.cpp**

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)
