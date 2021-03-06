---
description: En savoir plus sur l’écriture d’un filtre d’exceptions structurées.
title: Écriture d’un filtre d’exception
ms.date: 12/16/2020
helpviewer_keywords:
- exception handling [C++], filters
ms.openlocfilehash: 8b6706c7dfe0e96e26f77f1f3a452db638141803
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645057"
---
# <a name="writing-an-exception-filter"></a>Écriture d’un filtre d’exception

Vous pouvez gérer une exception en accédant au niveau du gestionnaire d'exceptions ou en reprenant l'exécution. Au lieu d’utiliser le code du gestionnaire d’exceptions pour gérer l’exception et tomber dans, vous pouvez utiliser une expression de *filtre* pour nettoyer le problème. Ensuite, en retournant `EXCEPTION_CONTINUE_EXECUTION` (-1), vous pouvez reprendre le déroulement normal sans effacer la pile.

> [!NOTE]
> Certaines exceptions ne peuvent pas être continuées. Si le *filtre* prend la valeur-1 pour une telle exception, le système déclenche une nouvelle exception. Lorsque vous appelez [`RaiseException`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) , vous déterminez si l’exception se poursuivra.

Par exemple, le code suivant utilise un appel de fonction dans l’expression de *filtre* : cette fonction gère le problème, puis retourne-1 pour reprendre le déroulement normal du contrôle :

```cpp
// exceptions_Writing_an_Exception_Filter.cpp
#include <windows.h>
int main() {
   int Eval_Exception( int );

   __try {}

   __except ( Eval_Exception( GetExceptionCode( ))) {
      ;
   }

}
void ResetVars( int ) {}
int Eval_Exception ( int n_except ) {
   if ( n_except != STATUS_INTEGER_OVERFLOW &&
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions
   return EXCEPTION_CONTINUE_SEARCH;

   // Execute some code to clean up problem
   ResetVars( 0 );   // initializes data to 0
   return EXCEPTION_CONTINUE_EXECUTION;
}
```

Il est judicieux d’utiliser un appel de fonction dans l’expression de *filtre* chaque fois que le *filtre* doit faire quelque chose de complexe. L'évaluation de l'expression provoque l'exécution de la fonction, dans ce cas, `Eval_Exception`.

Notez l’utilisation de [`GetExceptionCode`](/windows/win32/Debug/getexceptioncode) pour déterminer l’exception. Cette fonction doit être appelée à l’intérieur de l’expression de filtre de l' **`__except`** instruction. `Eval_Exception` Impossible `GetExceptionCode` d’appeler, mais le code d’exception doit lui être passé.

Ce gestionnaire passe le contrôle à un autre gestionnaire sauf si l'exception est un dépassement d'entier ou de virgule flottante. Si tel est le cas, le gestionnaire appelle une fonction (`ResetVars` n'est qu'un exemple, pas une fonction API) pour réinitialiser des variables globales. Le **`__except`** bloc d’instructions, qui, dans cet exemple, est vide, ne peut jamais être exécuté, car `Eval_Exception` ne retourne jamais `EXCEPTION_EXECUTE_HANDLER` (1).

Utilisation d'un appel de fonction est une bonne technique à usage général pour traiter des expressions de filtre complexes. Il y a deux autres fonctionnalités de langage C utiles :

- l'opérateur conditionnel ;

- l'opérateur virgule ;

L’opérateur conditionnel est souvent utile ici. Il peut être utilisé pour rechercher un code de retour spécifique, puis retourner l’une des deux valeurs différentes. Par exemple, le filtre dans le code suivant reconnaît l’exception uniquement si l’exception est `STATUS_INTEGER_OVERFLOW` :

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Dans ce cas, l'objectif de l'opérateur conditionnel consiste principalement à assurer la clarté, car le code suivant produit les mêmes résultats :

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

L’opérateur conditionnel est plus utile dans les situations où vous pouvez souhaiter que le filtre corresponde à-1, `EXCEPTION_CONTINUE_EXECUTION` .

L’opérateur virgule vous permet d’exécuter plusieurs expressions dans l’ordre. Elle retourne ensuite la valeur de la dernière expression. Par exemple, le code suivant enregistre le code d'exception dans une variable puis le teste :

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
