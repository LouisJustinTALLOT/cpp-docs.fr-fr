---
title: Écriture d'un filtre d'exception
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: aaf0dc77207399d7c6be86127d7decf03895ced5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245986"
---
# <a name="writing-an-exception-filter"></a>Écriture d'un filtre d'exception

Vous pouvez gérer une exception en accédant au niveau du gestionnaire d'exceptions ou en reprenant l'exécution. Instead of using the exception handler code to handle the exception and falling through, you can use *filter* to clean up the problem and then, by returning -1, resume normal flow without clearing the stack.

> [!NOTE]
>  Certaines exceptions ne peuvent pas être continuées. If *filter* evaluates to -1 for such an exception, the system raises a new exception. When you call [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception), you determine whether the exception will continue.

For example, the following code uses a function call in the *filter* expression: this function handles the problem and then returns -1 to resume normal flow of control:

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

It is a good idea to use a function call in the *filter* expression whenever *filter* needs to do anything complex. L'évaluation de l'expression provoque l'exécution de la fonction, dans ce cas, `Eval_Exception`.

Note the use of [GetExceptionCode](/windows/win32/Debug/getexceptioncode) to determine the exception. Vous devez appeler cette fonction à l'intérieur du filtre lui-même. `Eval_Exception` cannot call `GetExceptionCode`, but it must have the exception code passed to it.

Ce gestionnaire passe le contrôle à un autre gestionnaire sauf si l'exception est un dépassement d'entier ou de virgule flottante. Si tel est le cas, le gestionnaire appelle une fonction (`ResetVars` n'est qu'un exemple, pas une fonction API) pour réinitialiser des variables globales. *Statement-block-2*, which in this example is empty, can never be executed because `Eval_Exception` never returns EXCEPTION_EXECUTE_HANDLER (1).

Utilisation d'un appel de fonction est une bonne technique à usage général pour traiter des expressions de filtre complexes. Il y a deux autres fonctionnalités de langage C utiles :

- l'opérateur conditionnel ;

- l'opérateur virgule ;

L'opérateur conditionnel est souvent utile car il peut être utilisé pour rechercher un code de retour spécifique puis retourner l'une des deux valeurs différentes. For example, the filter in the following code recognizes the exception only if the exception is STATUS_INTEGER_OVERFLOW:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Dans ce cas, l'objectif de l'opérateur conditionnel consiste principalement à assurer la clarté, car le code suivant produit les mêmes résultats :

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

The conditional operator is more useful in situations where you might want the filter to evaluate to -1, EXCEPTION_CONTINUE_EXECUTION.

L'opérateur virgule vous permet d'effectuer plusieurs opérations indépendantes dans une expression unique. Cela a pour effet approximatif d'exécuter plusieurs instructions puis de retourner la valeur de la dernière expression. Par exemple, le code suivant enregistre le code d'exception dans une variable puis le teste :

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Voir aussi

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)