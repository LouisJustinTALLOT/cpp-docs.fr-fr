---
title: 'Comment : fournir des fonctions de travail aux classes call et transformer'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: 4d2b7b3c88b51003a96526ef14d9940a8c26c3b3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142488"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Comment : fournir des fonctions de travail aux classes call et transformer

Cette rubrique illustre plusieurs façons de fournir des fonctions de travail aux classes [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) et [Concurrency :: transformer](../../parallel/concrt/reference/transformer-class.md) .

Le premier exemple montre comment passer une expression lambda à un objet `call`. Le deuxième exemple montre comment passer un objet de fonction à un objet `call`. Le troisième exemple montre comment lier une méthode de classe à un objet `call`.

À titre d’illustration, chaque exemple de cette rubrique utilise la classe `call`. Pour obtenir un exemple qui utilise la classe `transformer`, consultez [How to : Use transformer in a data pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre une méthode courante pour utiliser la classe `call`. Cet exemple passe une fonction lambda au constructeur `call`.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
13 squared is 169.
```

## <a name="example"></a>Exemple

L’exemple suivant ressemble au précédent, à ceci près qu’il utilise la classe `call` avec un objet de fonction (functor).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant ressemble au précédent, à ceci près qu’il utilise les fonctions [std :: bind1st](../../standard-library/functional-functions.md#bind1st) et [std :: mem_fun](../../standard-library/functional-functions.md#mem_fun) pour lier un objet `call` à une méthode de classe.

Utilisez cette technique si vous devez lier un objet `call` ou `transformer` à une méthode de classe spécifique au lieu de l’opérateur d’appel de fonction, `operator()`.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Vous pouvez également assigner le résultat de la fonction `bind1st` à un objet [std :: function](../../standard-library/function-class.md) ou utiliser le mot clé `auto`, comme indiqué dans l’exemple suivant.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `call.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Call. cpp**

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Guide pratique pour utiliser la classe transformer dans un pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call, classe](../../parallel/concrt/reference/call-class.md)<br/>
[transformer, classe](../../parallel/concrt/reference/transformer-class.md)
