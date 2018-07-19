---
title: try, throw et catch instructions (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da07786c3aac6bfce2f74a16088b3c09184a8106
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942678"
---
# <a name="try-throw-and-catch-statements-c"></a>Instructions try, throw et catch (C++)
Pour implémenter la gestion des exceptions dans C++, vous utilisez **essayez**, **lever**, et **catch** expressions.  
  
 Tout d’abord, utilisez un **essayez** bloc pour encadrer une ou plusieurs instructions susceptibles de lever une exception.  
  
 Un **lever** expression indique qu’une condition exceptionnelle, souvent, une erreur, s’est produite dans un **essayez** bloc. Vous pouvez utiliser un objet de n’importe quel type comme opérande d’un **lever** expression. En général, cet objet est utilisé pour transmettre des informations sur l'erreur. Dans la plupart des cas, nous vous recommandons d’utiliser le [std::exception](../standard-library/exception-class.md) classe ou l’une des classes dérivées qui sont définis dans la bibliothèque standard. Si l'une de celles-ci est inadéquate, nous vous recommandons de dériver votre propre classe d'exceptions de `std::exception`.  
  
 Pour gérer les exceptions qui peuvent être levées, implémenter une ou plusieurs **catch** blocs qui suit immédiatement un **essayez** bloc. Chaque **catch** bloc spécifie le type d’exception qu’il peut gérer.  
  
 Cet exemple montre un **essayez** bloc et ses gestionnaires. Supposons que `GetNetworkResource()` acquiert des données via une connexion réseau et que les deux types d'exception sont des classes définies par l'utilisateur qui dérivent de `std::exception`. Notez que les exceptions sont interceptées par **const** référencer dans le **catch** instruction. Nous vous recommandons de lever des exceptions par valeur et de les intercepter par référence const.  
  
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
 Le code après le **essayez** clause est la section protégée du code. Le **lever** expression *lève*, autrement dit, déclenche : une exception. Le bloc de code après le **catch** clause est le Gestionnaire d’exceptions. Il s’agit du gestionnaire qui *intercepte* l’exception est levée si les types dans les **lever** et **catch** expressions sont compatibles. Pour obtenir la liste des règles qui régissent la correspondance des types dans **catch** blocs, consultez [comment les blocs Catch sont évalués](../cpp/how-catch-blocks-are-evaluated-cpp.md). Si le **catch** instruction spécifie les points de suspension (...) au lieu d’un type, le **catch** bloc gère chaque type d’exception. Lorsque vous compilez avec le [/EHa](../build/reference/eh-exception-handling-model.md) option, ils peuvent inclure des exceptions structurées par C et les exceptions asynchrones générées par le système ou générés par l’application telles que des violations de division par zéro et à virgule flottante de protection, de mémoire . Étant donné que **catch** blocs sont traités dans l’ordre de programme pour trouver un type correspondant, un gestionnaire de points de suspension doit être le dernier gestionnaire associé **essayez** bloc. Utilisez `catch(...)` avec précaution ; n'autorisez pas un programme à continuer sans que le bloc catch sache comment gérer l'exception spécifique qui est interceptée. En général, un bloc `catch(...)` est utilisé pour enregistrer des erreurs et effectuer un nettoyage spécial avant l'arrêt de l'exécution du programme.  
  
 Un **lever** expression sans opérande lève à nouveau l’exception en cours de traitement. Nous recommandons ce format lorsqu'une exception est levée à nouveau, car celui-ci préserve les informations de type polymorphe de l'exception d'origine. Une telle expression doit uniquement être utilisée dans un **catch** gestionnaire ou dans une fonction qui est appelée à partir d’un **catch** gestionnaire. L'objet d'une exception levée à nouveau est l'objet de l'exception d'origine, pas une copie.  
  
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
 [Gestion des exceptions C++](../cpp/cpp-exception-handling.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [Exceptions C++ non gérées](../cpp/unhandled-cpp-exceptions.md)   
 [__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)