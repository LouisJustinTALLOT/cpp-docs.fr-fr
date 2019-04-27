---
title: 'Procédure : Fournir des fonctions de travail aux Classes call et transformer'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: c41c29dae277105f268171503e662e2a02e3857e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205788"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Procédure : Fournir des fonctions de travail aux Classes call et transformer

Cette rubrique illustre plusieurs méthodes pour fournir des fonctions de travail pour le [concurrency::call](../../parallel/concrt/reference/call-class.md) et [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) classes.

Le premier exemple montre comment passer une expression lambda à une `call` objet. Le deuxième exemple montre comment passer un objet de fonction à un `call` objet. Le troisième exemple montre comment lier une méthode de classe pour un `call` objet.

À titre d’illustration, chaque exemple dans cette rubrique utilise le `call` classe. Pour obtenir un exemple qui utilise le `transformer` de classe, consultez [Comment : Utiliser la classe transformer dans un Pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example"></a>Exemple

L’exemple suivant montre une façon courante d’utiliser la `call` classe. Cet exemple passe une fonction lambda à la `call` constructeur.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
13 squared is 169.
```

## <a name="example"></a>Exemple

L’exemple suivant ressemble au précédent, sauf qu’elle utilise le `call` classe avec un objet de fonction (functor).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant ressemble au précédent, sauf qu’elle utilise le [std::bind1st](../../standard-library/functional-functions.md#bind1st) et [std::mem_fun](../../standard-library/functional-functions.md#mem_fun) fonctions pour lier un `call` objet à une méthode de classe.

Utilisez cette technique si vous avez besoin de lier un `call` ou `transformer` objet à une méthode de classe spécifique au lieu de l’opérateur d’appel de fonction, `operator()`.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Vous pouvez également affecter le résultat de la `bind1st` fonctionner à un [std::function](../../standard-library/function-class.md) ou d’utiliser le `auto` mot clé, comme illustré dans l’exemple suivant.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `call.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc call.cpp**

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Guide pratique pour utiliser la classe transformer dans un pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call, classe](../../parallel/concrt/reference/call-class.md)<br/>
[transformer, classe](../../parallel/concrt/reference/transformer-class.md)
