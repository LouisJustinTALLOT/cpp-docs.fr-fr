---
title: Instructions try, throw et catch (C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
ms.openlocfilehash: 03f7f6f5a1a2842ad7fb0ba2715fada130277e70
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187984"
---
# <a name="try-throw-and-catch-statements-c"></a>Instructions try, throw et catch (C++)

Pour implémenter la gestion C++des exceptions dans, vous utilisez des expressions **try**, **throw**et **catch** .

Tout d’abord, utilisez un bloc **try** pour encadrer une ou plusieurs instructions susceptibles de lever une exception.

Une expression **throw** signale qu’une condition exceptionnelle (souvent, une erreur) s’est produite dans un bloc **try** . Vous pouvez utiliser un objet de n’importe quel type comme opérande d’une expression **throw** . En général, cet objet est utilisé pour transmettre des informations sur l'erreur. Dans la plupart des cas, nous vous recommandons d’utiliser la classe [std :: exception](../standard-library/exception-class.md) ou l’une des classes dérivées qui sont définies dans la bibliothèque standard. Si l'une de celles-ci est inadéquate, nous vous recommandons de dériver votre propre classe d'exceptions de `std::exception`.

Pour gérer les exceptions qui peuvent être levées, implémentez un ou plusieurs blocs **catch** immédiatement après un bloc **try** . Chaque bloc **catch** spécifie le type d’exception qu’il peut gérer.

Cet exemple montre un bloc **try** et ses gestionnaires. Supposons que `GetNetworkResource()` acquiert des données via une connexion réseau et que les deux types d'exception sont des classes définies par l'utilisateur qui dérivent de `std::exception`. Notez que les exceptions sont interceptées par une référence **const** dans l’instruction **catch** . Nous vous recommandons de lever des exceptions par valeur et de les intercepter par référence const.

## <a name="example"></a>Exemple

```cpp
MyData md;
try {
   // Code that could throw an exception
   md = GetNetworkResource();
}
catch (const networkIOException& e) {
   // Code that executes when an exception of type
   // networkIOException is thrown in the try block
   // ...
   // Log error message in the exception object
   cerr << e.what();
}
catch (const myDataFormatException& e) {
   // Code that handles another exception type
   // ...
   cerr << e.what();
}

// The following syntax shows a throw expression
MyData GetNetworkResource()
{
   // ...
   if (IOSuccess == false)
      throw networkIOException("Unable to connect");
   // ...
   if (readError)
      throw myDataFormatException("Format error");
   // ...
}
```

## <a name="remarks"></a>Notes

Le code qui suit la clause **try** est la section protégée du code. L' **throw** expression Throw *lève*, en d’autres termes, une exception. Le bloc de code après la clause **catch** est le gestionnaire d’exceptions. Il s’agit du gestionnaire qui *intercepte* l’exception levée si les types des expressions **throw** et **catch** sont compatibles. Pour obtenir la liste des règles qui régissent la correspondance des types dans les blocs **catch** , consultez [la rubrique évaluation des blocs catch](../cpp/how-catch-blocks-are-evaluated-cpp.md). Si l’instruction **catch** spécifie des points de suspension (...) au lieu d’un type, le bloc **catch** gère chaque type d’exception. Quand vous compilez avec l’option [/EHa](../build/reference/eh-exception-handling-model.md) , celles-ci peuvent inclure des exceptions structurées en C et des exceptions asynchrones générées par le système ou générées par l’application, telles que la protection de la mémoire, la division par zéro et les violations de virgule flottante. Étant donné que les blocs **catch** sont traités dans l’ordre du programme pour trouver un type correspondant, un gestionnaire de points de suspension doit être le dernier gestionnaire du bloc **try** associé. Utilisez `catch(...)` avec précaution ; n'autorisez pas un programme à continuer sans que le bloc catch sache comment gérer l'exception spécifique qui est interceptée. En général, un bloc `catch(...)` est utilisé pour enregistrer des erreurs et effectuer un nettoyage spécial avant l'arrêt de l'exécution du programme.

Une expression **throw** qui n’a pas d’opérande lève de nouveau l’exception en cours de traitement. Nous recommandons ce format lorsqu'une exception est levée à nouveau, car celui-ci préserve les informations de type polymorphe de l'exception d'origine. Une telle expression doit uniquement être utilisée dans un gestionnaire **catch** ou dans une fonction appelée à partir d’un gestionnaire **catch** . L'objet d'une exception levée à nouveau est l'objet de l'exception d'origine, pas une copie.

```cpp
try {
   throw CSomeOtherException();
}
catch(...) {
   // Catch all exceptions - dangerous!!!
   // Respond (perhaps only partially) to the exception, then
   // re-throw to pass the exception to some other handler
   // ...
   throw;
}
```

## <a name="see-also"></a>Voir aussi

[Meilleures C++ pratiques modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Exceptions C++ non gérées](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
