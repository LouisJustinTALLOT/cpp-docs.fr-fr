---
title: 'Comment : envoyer un message à intervalles réguliers'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: c51a5cab6fcae5eb45b9d9b54c0dad8e8ec393b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142461"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Comment : envoyer un message à intervalles réguliers

Cet exemple montre comment utiliser la classe Concurrency ::[Timer](../../parallel/concrt/reference/timer-class.md) pour envoyer un message à intervalles réguliers.

## <a name="example"></a>Exemple

L’exemple suivant utilise un objet `timer` pour signaler la progression d’une opération longue. Cet exemple lie l’objet `timer` à un objet [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) . L’objet `call` imprime un indicateur de progression sur la console à intervalles réguliers. La méthode [Concurrency :: timer :: Start](reference/timer-class.md#start) exécute la minuterie sur un contexte distinct. La fonction `perform_lengthy_operation` appelle la fonction [Concurrency :: wait](reference/concurrency-namespace-functions.md#wait) sur le contexte principal pour simuler une opération qui prend du temps.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Cet exemple produit l’exemple de sortie suivant :

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `report-progress.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc report-progress. cpp**

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)
