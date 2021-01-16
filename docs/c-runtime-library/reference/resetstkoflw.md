---
description: 'En savoir plus sur : _resetstkoflw'
title: _resetstkoflw
ms.date: 1/14/2021
api_name:
- _resetstkoflw
- _o__resetstkoflw
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- resetstkoflw
- _resetstkoflw
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
ms.openlocfilehash: 092eea34de10ff77a31b5be35fa84dc1eb887328
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242967"
---
# `_resetstkoflw`

Récupère d'un dépassement de capacité de la pile.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la fonction réussit, zéro si elle échoue.

## <a name="remarks"></a>Remarques

La **`_resetstkoflw`** fonction récupère à partir d’une condition de dépassement de capacité de la pile, ce qui permet à un programme de continuer au lieu d’échouer avec une erreur d’exception irrécupérable. Si la **`_resetstkoflw`** fonction n’est pas appelée, il n’y a aucune page de garde après l’exception précédente. La prochaine fois qu’il y a un dépassement de capacité de la pile, il n’existe aucune exception et le processus se termine sans avertissement.

Si un thread dans une application provoque une **`EXCEPTION_STACK_OVERFLOW`** exception, le thread a quitté sa pile dans un état endommagé. Cela diffère des autres exceptions, telles que **`EXCEPTION_ACCESS_VIOLATION`** ou **`EXCEPTION_INT_DIVIDE_BY_ZERO`** , où la pile n’est pas endommagée. La pile est définie sur une valeur arbitrairement petite lorsque le programme est chargé pour la première fois. La pile se développe ensuite à la demande pour répondre aux besoins du thread. Cela est implémenté en plaçant une page avec un accès par PAGE_GUARD à la fin de la pile actuelle. Pour plus d’informations, consultez [Création de pages de garde](/windows/win32/Memory/creating-guard-pages).

Lorsque le code fait pointer le pointeur de pile vers une adresse sur cette page, une exception se produit et le système exécute les trois actions suivantes :

- Supprime la protection PAGE_GUARD sur la page de garde afin que le thread puisse lire et écrire des données dans la mémoire.

- Alloue une nouvelle page de garde située une page en dessous de la dernière.

- Réexécute l'instruction qui a déclenché l'exception.

Ainsi, le système peut augmenter automatiquement la taille de la pile pour le thread. Chaque thread d'un processus a une taille de pile maximale. La taille de la pile est définie au moment de la compilation par [ `/STACK` (allocations de la pile)](../../build/reference/stack-stack-allocations.md)ou par l' [`STACKSIZE`](../../build/reference/stacksize.md) instruction dans le `.def` fichier du projet.

Lorsque cette taille de pile maximale est dépassée, le système exécute les trois actions suivantes :

- Supprime la protection PAGE_GUARD sur la page de garde, comme décrit précédemment.

- Essaie d'allouer une nouvelle page de garde en dessous de la dernière. Toutefois, cela échoue car la taille de pile maximale a été dépassée.

- Lève une exception afin que le thread puisse la gérer dans le bloc d'exception.

À ce stade, la pile n’a plus de page de garde. La prochaine fois que le programme augmentera la pile jusqu'à la fin, où devra se trouver une page de garde, il écrira au-delà de la fin de la pile et provoquera une violation d'accès.

Appelez **`_resetstkoflw`** pour restaurer la page de garde chaque fois que la récupération est effectuée après une exception de dépassement de capacité de la pile. Cette fonction peut être appelée à l’intérieur du corps principal d’un **`__except`** bloc ou à l’extérieur d’un **`__except`** bloc. Toutefois, il existe quelques restrictions sur son utilisation. **`_resetstkoflw`** ne doit pas être appelé à partir de :

- Une expression de filtre.

- Une fonction de filtre.

- Une fonction appelée à partir d'une fonction de filtre.

- **`catch`** Bloc.

- **`__finally`** Bloc.

À ces points, la pile n’est pas encore suffisamment déroulée.

Les exceptions de dépassement de capacité de la pile sont générées comme des exceptions structurées, et non des exceptions C++, donc **`_resetstkoflw`** n’est pas utile dans un bloc ordinaire, **`catch`** car elle n’intercepte pas d’exception de dépassement de capacité de Toutefois, si [`_set_se_translator`](set-se-translator.md) est utilisé pour implémenter un traducteur d’exceptions structurées qui lève des exceptions c++ (comme dans le deuxième exemple), une exception de dépassement de capacité de la pile provoque une exception c++ qui peut être gérée par un bloc catch c++.

Il n’est pas sûr d’appeler **`_resetstkoflw`** dans un bloc catch C++ qui est atteint à partir d’une exception levée par la fonction de traduction d’exceptions structurées. Dans ce cas, l’espace de pile n’est pas libéré et le pointeur de pile n’est pas réinitialisé jusqu’à l’extérieur du bloc catch, même si des destructeurs ont été appelés pour tous les objets destructible avant le bloc catch. Cette fonction ne doit pas être appelée tant que l’espace de pile n’est pas libéré et que le pointeur de pile n’a pas été réinitialisé. Par conséquent, elle doit être appelée uniquement après avoir quitté le bloc catch. Le moins d’espace de pile possible doit être utilisé dans le bloc catch, car un dépassement de capacité de la pile qui se produit dans le bloc catch qui tente lui-même de récupérer à partir d’un dépassement de capacité de la pile précédent n’est pas récupérable et peut provoquer le blocage du programme lorsque le dépassement du bloc catch déclenche une exception qui est elle-même gérée par le même bloc catch

Dans certains cas **`_resetstkoflw`** , l’utilisation de peut échouer même si elle est utilisée dans un emplacement correct, par exemple dans un **`__except`** bloc. Si, même après le déroulement de la pile, l’espace de pile restant n’est toujours pas suffisant pour s’exécuter **`_resetstkoflw`** sans écrire dans la dernière page de la pile, **`_resetstkoflw`** ne parvient pas à réinitialiser la dernière page de la pile comme page de garde et retourne 0, ce qui indique un échec. L’utilisation sécurisée de cette fonction doit inclure la vérification de la valeur de retour au lieu de supposer que la pile peut être utilisée en toute sécurité.

La gestion structurée des exceptions n’intercepte pas d' **`STATUS_STACK_OVERFLOW`** exception quand l’application est compilée avec **`/clr`** (consultez [ `/clr ` (compilation du Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`_resetstkoflw`**|\<malloc.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

**Bibliothèques :** toutes les versions des [fonctionnalités de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

L’exemple suivant montre l’utilisation recommandée de la **`_resetstkoflw`** fonction.

```C
// crt_resetstkoflw.c
// Launch program with and without arguments to observe
// the difference made by calling _resetstkoflw.

#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void recursive(int recurse)
{
   _alloca(2000);
   if (recurse)
      recursive(recurse);
}

// Filter for the stack overflow exception.
// This function traps the stack overflow exception, but passes
// all other exceptions through.
int stack_overflow_exception_filter(int exception_code)
{
   if (exception_code == EXCEPTION_STACK_OVERFLOW)
   {
       // Do not call _resetstkoflw here, because
       // at this point, the stack isn't yet unwound.
       // Instead, signal that the handler (the __except block)
       // is to be executed.
       return EXCEPTION_EXECUTE_HANDLER;
   }
   else
       return EXCEPTION_CONTINUE_SEARCH;
}

int main(int ac)
{
   int i = 0;
   int recurse = 1, result = 0;

   for (i = 0 ; i < 10 ; i++)
   {
      printf("loop #%d\n", i + 1);
      __try
      {
         recursive(recurse);

      }

      __except(stack_overflow_exception_filter(GetExceptionCode()))
      {
         // Here, it is safe to reset the stack.

         if (ac >= 2)
         {
            puts("resetting stack overflow");
            result = _resetstkoflw();
         }
      }

      // Terminate if _resetstkoflw failed (returned 0)
      if (!result)
         return 3;
   }

   return 0;
}
```

Exemple de sortie sans argument de programme :

```Output
loop #1
```

Le programme cesse de répondre sans exécuter d'autres itérations.

Avec des arguments de programme :

```Output
loop #1
resetting stack overflow
loop #2
resetting stack overflow
loop #3
resetting stack overflow
loop #4
resetting stack overflow
loop #5
resetting stack overflow
loop #6
resetting stack overflow
loop #7
resetting stack overflow
loop #8
resetting stack overflow
loop #9
resetting stack overflow
loop #10
resetting stack overflow
```

### <a name="description"></a>Description

L’exemple suivant illustre l’utilisation recommandée de **`_resetstkoflw`** dans un programme où les exceptions structurées sont converties en exceptions C++.

### <a name="code"></a>Code

```cpp
// crt_resetstkoflw2.cpp
// compile with: /EHa
// _set_se_translator requires the use of /EHa
#include <malloc.h>
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class Exception { };

class StackOverflowException : Exception { };

// Because the overflow is deliberate, disable the warning that
// this function will cause a stack overflow.
#pragma warning (disable: 4717)
void CauseStackOverflow (int i)
{
    // Overflow the stack by allocating a large stack-based array
    // in a recursive function.
    int a[10000];
    printf("%d ", i);
    CauseStackOverflow (i + 1);
}

void __cdecl SEHTranslator (unsigned int code, _EXCEPTION_POINTERS*)
{
    // For stack overflow exceptions, throw our own C++
    // exception object.
    // For all other exceptions, throw a generic exception object.
    // Use minimal stack space in this function.
    // Do not call _resetstkoflw in this function.

    if (code == EXCEPTION_STACK_OVERFLOW)
        throw StackOverflowException ( );
    else
        throw Exception( );
}

int main ( )
{
    bool stack_reset = false;
    bool result = false;

    // Set up a function to handle all structured exceptions,
    // including stack overflow exceptions.
    _set_se_translator (SEHTranslator);

    try
    {
        CauseStackOverflow (0);
    }
    catch (StackOverflowException except)
    {
        // Use minimal stack space here.
        // Do not call _resetstkoflw here.
        printf("\nStack overflow!\n");
        stack_reset = true;
    }
    catch (Exception except)
    {
        // Do not call _resetstkoflw here.
        printf("\nUnknown Exception!\n");
    }
    if (stack_reset)
    {
        result = _resetstkoflw();
        // If stack reset failed, terminate the application.
        if (result == 0)
            exit(1);
    }

    void* pv = _alloca(100000);
    printf("Recovered from stack overflow and allocated 100,000 bytes"
           " using _alloca.");

    return 0;
}
```

```Output
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
Stack overflow!
Recovered from stack overflow and allocated 100,000 bytes using _alloca.
```

## <a name="see-also"></a>Voir aussi

[`_alloca`](alloca.md)<br/>
