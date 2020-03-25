---
title: Spécifications d’exception (throw, noexcept)C++()
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 6f8f9466b867603738919c6210055d02d3c579ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180041"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Spécifications d’exception (throw, noexcept)C++()

Les spécifications d’exceptions C++ sont une fonctionnalité de langage qui indique à l’intention du programmeur d’utiliser les types d’exception qui peuvent être propagés par une fonction. Vous pouvez spécifier qu’une fonction peut ou non se terminer par une exception à l’aide d’une *spécification d’exception*. Le compilateur peut utiliser ces informations pour optimiser les appels à la fonction et arrêter le programme si une exception inattendue échappe à la fonction.

Avant C++ 17, il existait deux genres de spécifications d’exception. La *spécification noexcept* était une nouveauté dans c++ 11. Elle spécifie si le jeu d’exceptions potentielles qui peuvent échapper à la fonction est vide. La *spécification d’exception dynamique*, ou spécification de `throw(optional_type_list)`, a été dépréciée dans c++ 11 et supprimée dans c++ 17, à l’exception de `throw()`, qui est un alias pour `noexcept(true)`. Cette spécification d’exception a été conçue pour fournir des informations de synthèse sur les exceptions qui peuvent être levées à partir d’une fonction, mais dans la pratique, elle a été jugée problématique. La spécification d’exception dynamique qui s’est avérée très utile était la spécification de `throw()` non conditionnelle. Par exemple, la déclaration de fonction :

```cpp
void MyFunction(int i) throw();
```

indique au compilateur que la fonction ne lève pas d'exception. Toutefois, en mode **/std : c++ 14** , cela peut entraîner un comportement indéfini si la fonction lève une exception. Par conséquent, nous vous recommandons d’utiliser l’opérateur [noexcept](../cpp/noexcept-cpp.md) au lieu de celui-ci :

```cpp
void MyFunction(int i) noexcept;
```

Le tableau suivant résume l’implémentation Microsoft C++ des spécifications d’exception :

|Spécification d'exception|Signification|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|La fonction ne lève pas d'exception. Dans [/std : mode c++ 14](../build/reference/std-specify-language-standard-version.md) (valeur par défaut), `noexcept` et `noexcept(true)` sont équivalents. Quand une exception est levée à partir d’une fonction déclarée `noexcept` ou `noexcept(true)`, [std :: Terminate](../standard-library/exception-functions.md#terminate) est appelé. Quand une exception est levée à partir d’une fonction déclarée comme `throw()` dans **/std : le mode c++ 14** , le résultat est un comportement indéfini. Aucune fonction spécifique n’est appelée. Il s’agit d’une divergence par rapport à la norme C++ 14, qui exigeait que le compilateur appelle [std :: inattendue](../standard-library/exception-functions.md#unexpected).  <br/> **Visual Studio 2017 version 15,5 et versions ultérieures**: en mode **/std : c++ 17** , `noexcept`, `noexcept(true)`et `throw()` sont tous équivalents. En mode **/std : c++ 17** , `throw()` est un alias pour `noexcept(true)`. En mode **/std : c++ 17** , quand une exception est levée à partir d’une fonction déclarée avec l’une de ces spécifications, [std :: Terminate](../standard-library/exception-functions.md#terminate) est appelé comme requis par la norme c++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Aucune spécification|La fonction peut lever une exception de tout type.|
|`throw(type)`| (**C++ 14 et versions antérieures**) La fonction peut lever une exception de type `type`. Le compilateur accepte la syntaxe, mais l’interprète comme `noexcept(false)`. En mode **/std : c++ 17** , le compilateur émet un avertissement C5040.|

Si la gestion des exceptions est utilisée dans une application, il doit y avoir une fonction dans la pile des appels qui gère les exceptions levées avant de quitter la portée externe d’une fonction marquée `noexcept`, `noexcept(true)`ou `throw()`. Si des fonctions appelées entre celle qui lève une exception et celle qui gère l’exception sont spécifiées comme `noexcept`, `noexcept(true)` (ou `throw()` en mode **/std : c++ 17** ), le programme est arrêté lorsque la fonction noexcept propage l’exception.

Le comportement de l’exception d’une fonction dépend des facteurs suivants :

- Le [mode de compilation standard du langage](../build/reference/std-specify-language-standard-version.md) défini.
- si vous compilez la fonction sous C ou C++ ;

- L’option du compilateur [/Eh](../build/reference/eh-exception-handling-model.md) que vous utilisez.

- si vous spécifiez de manière explicite la spécification d'exception.

Les spécifications d'exceptions explicites ne sont pas autorisées sur les fonctions C. Une fonction C est supposée ne pas lever d’exceptions sous **/EHsc**et peut lever des exceptions structurées sous **/EHS**, **/EHa**ou **/EHac**.

Le tableau suivant résume si une fonction C++ peut potentiellement être levée sous diverses options de gestion des exceptions du compilateur :

|Fonction|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|Fonction C++ sans spécification d'exception|Oui|Oui|Oui|Oui|
|C++fonction avec `noexcept`, `noexcept(true)`ou `throw()` spécification d’exception|Non|Non|Oui|Oui|
|C++fonction avec `noexcept(false)`, `throw(...)`ou `throw(type)` spécification d’exception|Oui|Oui|Oui|Oui|

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
[Meilleures C++ pratiques modernes pour les exceptions et la gestion des erreurs](errors-and-exception-handling-modern-cpp.md)
