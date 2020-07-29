---
title: 'Comment : fournir des fonctions de travail aux classes call et transformer'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: cecb8b2e6ab3f3ac8b010007018b76e6f58e0ed8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205884"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Comment : fournir des fonctions de travail aux classes call et transformer

Cette rubrique illustre plusieurs façons de fournir des fonctions de travail aux classes [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) et [Concurrency :: transformer](../../parallel/concrt/reference/transformer-class.md) .

Le premier exemple montre comment passer une expression lambda à un `call` objet. Le deuxième exemple montre comment passer un objet de fonction à un `call` objet. Le troisième exemple montre comment lier une méthode de classe à un `call` objet.

À titre d’illustration, chaque exemple de cette rubrique utilise la `call` classe. Pour obtenir un exemple qui utilise la `transformer` classe, consultez [How to : Use transformer in a data pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre une méthode courante pour utiliser la `call` classe. Cet exemple passe une fonction lambda au `call` constructeur.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
13 squared is 169.
```

## <a name="example"></a>Exemple

L’exemple suivant ressemble au précédent, à la différence qu’il utilise la `call` classe avec un objet de fonction (functor).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant ressemble au précédent, à ceci près qu’il utilise les fonctions [std :: bind1st](../../standard-library/functional-functions.md#bind1st) et [std :: mem_fun](../../standard-library/functional-functions.md#mem_fun) pour lier un `call` objet à une méthode de classe.

Utilisez cette technique si vous devez lier un `call` objet ou `transformer` à une méthode de classe spécifique au lieu de l’opérateur d’appel de fonction, `operator()` .

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Vous pouvez également assigner le résultat de la `bind1st` fonction à un objet [std :: function](../../standard-library/function-class.md) ou utiliser le **`auto`** mot clé, comme indiqué dans l’exemple suivant.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `call.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Call. cpp**

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Comment : utiliser le transformateur dans un pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[Call (classe)](../../parallel/concrt/reference/call-class.md)<br/>
[transformer, classe](../../parallel/concrt/reference/transformer-class.md)
