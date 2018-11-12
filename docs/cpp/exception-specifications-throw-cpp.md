---
title: Spécifications d’exception (throw, noexcept) (C++)
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 9280f3d96088d988a9d5cfe0f3d56444b865167e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517336"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Spécifications d’exception (throw, noexcept) (C++)

Spécifications d’exceptions sont une fonctionnalité de langage C++ qui indiquent l’intention du programmeur sur les types d’exception qui peuvent être propagées par une fonction. Vous pouvez spécifier qu’une fonction peut ou ne peut pas quitter par une exception en utilisant un *spécification d’exception*. Le compilateur peut utiliser ces informations pour optimiser les appels à la fonction, et la fonction d’échappement pour mettre fin au programme si une exception inattendue.

Avant C ++ 17 a deux types de spécification d’exception. Le *noexcept spécification* est une nouveauté dans C ++ 11. Il spécifie si l’ensemble des exceptions potentielles qui peuvent échapper à la fonction est vide. Le *spécification d’exception dynamiques*, ou `throw(optional_type_list)` spécification, a été déconseillée dans C ++ 11 et supprimée dans C ++ 17, à l’exception de `throw()`, qui est un alias pour `noexcept(true)`. Cette spécification d’exception a été conçue pour fournir des informations résumées concernant les exceptions peuvent être levées en dehors d’une fonction, mais dans la pratique, il a été trouvé pour poser des problèmes. La spécification d’exception dynamique un qui s’est révélée quelque peu utile a été les inconditionnels `throw()` spécification. Par exemple, la déclaration de fonction :

```cpp
void MyFunction(int i) throw();
```
indique au compilateur que la fonction ne lève pas d'exception. Toutefois, dans **/std : c ++ 14** mode cela peut entraîner un comportement indéfini si la fonction lève une exception. Par conséquent, nous vous recommandons d’utiliser le [noexcept](../cpp/noexcept-cpp.md) opérateur au lieu de celui illustré ci-dessus :

```cpp
void MyFunction(int i) noexcept;
```
Le tableau suivant résume l’implémentation de Microsoft Visual C++ des spécifications d’exceptions :

|Spécification d'exception|Signification|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|La fonction ne lève pas d'exception. Dans [/std : c ++ 14](../build/reference/std-specify-language-standard-version.md) mode (qui est la valeur par défaut), `noexcept` et `noexcept(true)` sont équivalentes. Lorsqu’une exception est levée à partir d’une fonction qui est déclarée `noexcept` ou `noexcept(true)`, [std::terminate](../standard-library/exception-functions.md#terminate) est appelé. Lorsqu’une exception est levée à partir d’une fonction déclarée comme `throw()` dans **/std : c ++ 14** mode, le résultat est un comportement non défini. Aucune fonction spécifique n’est appelée. Il s’agit d’une divergence à partir de la norme C ++ 14, ce qui obligeait le compilateur à appeler [std::unexpected](../standard-library/exception-functions.md#unexpected).  <br/> **Visual Studio 2017 version 15.5 et versions ultérieure**: dans **/std : c ++ 17** mode, `noexcept`, `noexcept(true)`, et `throw()` sont toutes équivalentes. Dans **/std : c ++ 17** mode, `throw()` est un alias pour `noexcept(true)`. Dans **/std : c ++ 17** mode, lorsqu’une exception est levée à partir d’une fonction déclarée avec n’importe quelle de ces spécifications, [std::terminate](../standard-library/exception-functions.md#terminate) est appelé comme requis par la norme C ++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Aucune spécification|La fonction peut lever une exception de n’importe quel type.|
|`throw(type)`| (**C ++ 14 et versions antérieures**) la fonction peut lever une exception de type `type`. Le compilateur accepte la syntaxe, mais il l’interprète comme `noexcept(false)`. Dans **/std : c ++ 17** mode, le compilateur émet l’avertissement C5040.|

Si la gestion des exceptions sont utilisée dans une application, il doit être une fonction dans la pile des appels qui handles levées avant de quitter l’étendue externe d’une fonction marquées `noexcept`, `noexcept(true)`, ou `throw()`. Si toutes les fonctions appelée entre celle qui lève une exception et celui qui gère l’exception sont spécifiés en tant que `noexcept`, `noexcept(true)` (ou `throw()` dans **/std : c ++ 17** mode), le programme se termine lorsque le fonction noexcept propage l’exception.

Le comportement d’exception d’une fonction dépend des facteurs suivants :

- Qui [mode de compilation standard de langage](../build/reference/std-specify-language-standard-version.md) est définie.
- si vous compilez la fonction sous C ou C++ ;

- Qui [/EH](../build/reference/eh-exception-handling-model.md) option du compilateur que vous utilisez.

- si vous spécifiez de manière explicite la spécification d'exception.

Les spécifications d'exceptions explicites ne sont pas autorisées sur les fonctions C. Une fonction C est supposée ne pas pour lever des exceptions sous **/EHsc**et peut lever des exceptions structurées sous **/EHs**, **/EHa**, ou **/EHac**.

Le tableau suivant récapitule si une fonction C++ peut lever potentiellement sous différents du compilateur exceptions options :

|Fonction|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|Fonction C++ sans spécification d'exception|Oui|Oui|Oui|Oui|
|Fonction C++ avec `noexcept`, `noexcept(true)`, ou `throw()` spécification d’exception|Non|Non|Oui|Oui|
|Fonction C++ avec `noexcept(false)`, `throw(...)`, ou `throw(type)` spécification d’exception|Oui|Oui|Oui|Oui|

## <a name="example"></a>Exemple

```cpp
// exception_specification.cpp
// compile with: /EHs
#include <stdio.h>

void handler() {
   printf_s("in handler\n");
}

void f1(void) throw(int) {
   printf_s("About to throw 1\n");
   if (1)
      throw 1;
}

void f5(void) throw() {
   try {
      f1();
   }
   catch(...) {
      handler();
    }
}

// invalid, doesn't handle the int exception thrown from f1()
// void f3(void) throw() {
//   f1();
// }

void __declspec(nothrow) f2(void) {
   try {
      f1();
   }
   catch(int) {
      handler();
    }
}

// only valid if compiled without /EHc
// /EHc means assume extern "C" functions don't throw exceptions
extern "C" void f4(void);
void f4(void) {
   f1();
}

int main() {
   f2();

   try {
      f4();
   }
   catch(...) {
      printf_s("Caught exception from f4\n");
   }
   f5();
}
```

```Output
About to throw 1
in handler
About to throw 1
Caught exception from f4
About to throw 1
in handler
```

## <a name="see-also"></a>Voir aussi

[Instructions try, throw et catch (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[Gestion d’exceptions C++](../cpp/cpp-exception-handling.md)