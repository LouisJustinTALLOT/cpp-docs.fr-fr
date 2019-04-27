---
title: Écriture d'un filtre d'exception
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 2bc159247604877fb22ff6084e1fda36946561a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209375"
---
# <a name="writing-an-exception-filter"></a>Écriture d'un filtre d'exception

Vous pouvez gérer une exception en accédant au niveau du gestionnaire d'exceptions ou en reprenant l'exécution. Au lieu d’utiliser le code de gestionnaire d’exception à gérer l’exception et passer, vous pouvez utiliser *filtre* pour éliminer le problème et puis, en retournant -1, reprendre le flux normal sans nettoyer la pile.

> [!NOTE]
>  Certaines exceptions ne peuvent pas être continuées. Si *filtre* prend la valeur-1 pour cette exception, le système déclenche une exception. Lorsque vous appelez [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552), vous déterminez si l’exception va continuer.

Par exemple, le code suivant utilise un appel de fonction dans le *filtre* expression : cette fonction traite le problème, puis retourne -1 pour reprendre le flux de contrôle normal :

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

Il est judicieux d’utiliser un appel de fonction dans le *filtre* expression chaque fois que *filtre* doit effectuer des opérations complexes. L'évaluation de l'expression provoque l'exécution de la fonction, dans ce cas, `Eval_Exception`.

Notez l’utilisation de [GetExceptionCode](/windows/desktop/Debug/getexceptioncode) pour déterminer l’exception. Vous devez appeler cette fonction à l'intérieur du filtre lui-même. `Eval_Exception` Impossible d’appeler `GetExceptionCode`, mais elle doit avoir le code d’exception lui est passé.

Ce gestionnaire passe le contrôle à un autre gestionnaire sauf si l'exception est un dépassement d'entier ou de virgule flottante. Si tel est le cas, le gestionnaire appelle une fonction (`ResetVars` n'est qu'un exemple, pas une fonction API) pour réinitialiser des variables globales. *Instruction-block-2*, qui dans cet exemple est vide, peut jamais être exécuté car `Eval_Exception` ne retourne jamais EXCEPTION_EXECUTE_HANDLER (1).

Utilisation d'un appel de fonction est une bonne technique à usage général pour traiter des expressions de filtre complexes. Il y a deux autres fonctionnalités de langage C utiles :

- l'opérateur conditionnel ;

- l'opérateur virgule ;

L'opérateur conditionnel est souvent utile car il peut être utilisé pour rechercher un code de retour spécifique puis retourner l'une des deux valeurs différentes. Par exemple, le filtre dans le code suivant reconnaît l’exception uniquement si l’exception est STATUS_INTEGER_OVERFLOW :

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

Dans ce cas, l'objectif de l'opérateur conditionnel consiste principalement à assurer la clarté, car le code suivant produit les mêmes résultats :

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

L’opérateur conditionnel est plus utile dans les situations dans lesquelles vous pouvez le filtre doit évaluer sur -1, EXCEPTION_CONTINUE_EXECUTION.

L'opérateur virgule vous permet d'effectuer plusieurs opérations indépendantes dans une expression unique. Cela a pour effet approximatif d'exécuter plusieurs instructions puis de retourner la valeur de la dernière expression. Par exemple, le code suivant enregistre le code d'exception dans une variable puis le teste :

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)