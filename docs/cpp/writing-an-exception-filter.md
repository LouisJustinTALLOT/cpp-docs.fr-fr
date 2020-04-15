---
title: Écriture d’un filtre d’exception
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 05d3aa79d1293001e80a77b3171b7a4607cd81c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369485"
---
# <a name="writing-an-exception-filter"></a>Écriture d’un filtre d’exception

Vous pouvez gérer une exception en accédant au niveau du gestionnaire d'exceptions ou en reprenant l'exécution. Au lieu d’utiliser le code de gestionnaire d’exception pour gérer l’exception et de tomber à travers, vous pouvez utiliser *le filtre* pour nettoyer le problème, puis, en retournant -1, reprendre le flux normal sans effacer la pile.

> [!NOTE]
> Certaines exceptions ne peuvent pas être continuées. Si *le filtre* évalue à -1 pour une telle exception, le système soulève une nouvelle exception. Lorsque vous appelez [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception), vous déterminez si l’exception se poursuivra.

Par exemple, le code suivant utilise un appel de fonction dans l’expression du *filtre* : cette fonction gère le problème, puis renvoie -1 pour reprendre le flux normal de contrôle :

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

C’est une bonne idée d’utiliser un appel de fonction dans l’expression *de filtre* chaque fois que le *filtre* doit faire quelque chose de complexe. L'évaluation de l'expression provoque l'exécution de la fonction, dans ce cas, `Eval_Exception`.

Notez l’utilisation de [GetExceptionCode](/windows/win32/Debug/getexceptioncode) pour déterminer l’exception. Vous devez appeler cette fonction à l'intérieur du filtre lui-même. `Eval_Exception`ne `GetExceptionCode`peut pas appeler, mais il doit avoir le code d’exception transmis à elle.

Ce gestionnaire passe le contrôle à un autre gestionnaire sauf si l'exception est un dépassement d'entier ou de virgule flottante. Si tel est le cas, le gestionnaire appelle une fonction (`ResetVars` n'est qu'un exemple, pas une fonction API) pour réinitialiser des variables globales. *Déclaration-bloc-2*, qui dans cet exemple est vide, ne peut jamais être exécuté parce que `Eval_Exception` ne retourne jamais EXCEPTION_EXECUTE_HANDLER (1).

Utilisation d'un appel de fonction est une bonne technique à usage général pour traiter des expressions de filtre complexes. Il y a deux autres fonctionnalités de langage C utiles :

- l'opérateur conditionnel ;

- l'opérateur virgule ;

L'opérateur conditionnel est souvent utile car il peut être utilisé pour rechercher un code de retour spécifique puis retourner l'une des deux valeurs différentes. Par exemple, le filtre du code suivant ne reconnaît l’exception que si l’exception est STATUS_INTEGER_OVERFLOW :

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Dans ce cas, l'objectif de l'opérateur conditionnel consiste principalement à assurer la clarté, car le code suivant produit les mêmes résultats :

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

L’opérateur conditionnel est plus utile dans les situations où vous pourriez vouloir que le filtre évalue à -1, EXCEPTION_CONTINUE_EXECUTION.

L'opérateur virgule vous permet d'effectuer plusieurs opérations indépendantes dans une expression unique. Cela a pour effet approximatif d'exécuter plusieurs instructions puis de retourner la valeur de la dernière expression. Par exemple, le code suivant enregistre le code d'exception dans une variable puis le teste :

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Voir aussi

[Rédaction d’un gestionnaire d’exception](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
