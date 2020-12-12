---
description: 'En savoir plus sur : Comment : envoyer un message à intervalles réguliers'
title: 'Comment : envoyer un message à intervalles réguliers'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: f65226d8101ddbadaee97a16f63512b9c8dcb41e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197282"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Comment : envoyer un message à intervalles réguliers

Cet exemple montre comment utiliser la classe Concurrency ::[Timer](../../parallel/concrt/reference/timer-class.md) pour envoyer un message à intervalles réguliers.

## <a name="example"></a>Exemple

L’exemple suivant utilise un `timer` objet pour signaler la progression au cours d’une opération de longue durée. Cet exemple lie l' `timer` objet à un objet [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) . L' `call` objet affiche un indicateur de progression sur la console à intervalles réguliers. La méthode [Concurrency :: timer :: Start](reference/timer-class.md#start) exécute la minuterie sur un contexte distinct. La `perform_lengthy_operation` fonction appelle la fonction [Concurrency :: wait](reference/concurrency-namespace-functions.md#wait) sur le contexte principal pour simuler une opération qui prend du temps.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Cet exemple produit l’exemple de sortie suivant :

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `report-progress.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc report-progress. cpp**

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)
