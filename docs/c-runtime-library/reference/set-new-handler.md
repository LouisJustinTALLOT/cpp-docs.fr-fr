---
title: _set_new_handler
ms.date: 4/2/2020
api_name:
- _set_new_handler
- _o__set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: c3f1b9bd8bf2a4404e2239858e4c3c59b755bacd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332379"
---
# <a name="_set_new_handler"></a>_set_new_handler

Transfère le contrôle à votre mécanisme de gestion des erreurs si l’opérateur **new** ne peut pas allouer de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Paramètres

*pNewHandler (en)*<br/>
Pointeur vers la fonction de gestion de la mémoire fournie par l'application. L’argument 0 provoque la suppression du nouveau gestionnaire.

## <a name="return-value"></a>Valeur de retour

Renvoie un pointeur à la fonction de manipulation d’exception précédente enregistrée par **_set_new_handler**, de sorte que la fonction précédente peut être restaurée plus tard. Si aucune fonction antérieure n’a été définie, la valeur de retour peut être utilisée pour restaurer le comportement par défaut; cette valeur peut être **NULL**.

## <a name="remarks"></a>Notes

La fonction **de _set_new_handler** de Cmd spécifie une fonction de manipulation d’exception qui prend le contrôle si le **nouvel** opérateur ne parvient pas à allouer la mémoire. En **cas d’échec,** le système de temps d’exécution appelle automatiquement la fonction de manipulation d’exception qui a été adoptée comme argument à **_set_new_handler**. **_PNH**, défini dans New.h, est un pointeur à une fonction qui renvoie **int** type et prend un argument de type **size_t**. Utilisez **size_t** pour spécifier la quantité d’espace à allouer.

Il n'existe pas de gestionnaire par défaut.

**_set_new_handler** est essentiellement un système de collecte des ordures. Le système runtime réexécute l'allocation chaque fois que la fonction retourne une valeur différente de zéro, et échoue si votre fonction retourne 0.

L’apparition de la fonction **_set_new_handler** dans un programme enregistre la fonction de manipulation des exceptions spécifiée dans la liste d’argumentation avec le système de temps d’exécution :

```cpp
// set_new_handler1.cpp
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <new.h>

int handle_program_memory_depletion( size_t )
{
   // Your code
}

int main( void )
{
   _set_new_handler( handle_program_memory_depletion );
   int *pi = new int[BIG_NUMBER];
}
```

Vous pouvez enregistrer l’adresse de fonction qui a été passée pour la dernière fois à la fonction **_set_new_handler** et la rétablir plus tard :

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

La fonction C++ [_set_new_mode](set-new-mode.md) définit le mode de nouveau gestionnaire pour [malloc](malloc.md). Le nouveau mode de manutention indique si, en cas de défaillance, **malloc** est d’appeler la nouvelle routine de gestionnaire tel que défini par **_set_new_handler**. Par défaut, **malloc** n’appelle pas la nouvelle routine de gestionnaire sur l’omission d’allouer la mémoire. Vous pouvez passer outre à ce comportement par défaut de sorte que, lorsque **malloc** ne parvient pas à allouer la mémoire, **malloc** appelle la nouvelle routine de gestionnaire de la même manière que le **nouvel** opérateur fait quand il échoue pour la même raison. Pour substituer la valeur par défaut, appelez :

```cpp
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec Newmode.obj.

Si un utilisateur `operator new` défini est fourni, les nouvelles fonctions de gestionnaire ne sont pas automatiquement appelées sur défaillance.

Pour plus d’informations, voir [new](../../cpp/new-operator-cpp.md) et [delete](../../cpp/delete-operator-cpp.md) dans la *Référence du langage C++*.

Il existe un seul **gestionnaire _set_new_handler** pour tous les DLL ou exécutables liés dynamiquement; même si vous appelez **_set_new_handler** votre gestionnaire peut être remplacé par un autre ou que vous remplacez un gestionnaire défini par un autre DLL ou exécutoire.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Dans cet exemple, lorsque l'allocation échoue, le contrôle est transféré à MyNewHandler. L'argument passé à MyNewHandler est le nombre d'octets demandés. La valeur retournée par MyNewHandler est un indicateur qui spécifie si l'allocation doit être réexécutée : une valeur autre que zéro indique que l'allocation doit être réexécutée, une valeur zéro indique que l'allocation a échoué.

```cpp
// crt_set_new_handler.cpp
// compile with: /c
#include <stdio.h>
#include <new.h>
#define BIG_NUMBER 0x1fffffff

int coalesced = 0;

int CoalesceHeap()
{
   coalesced = 1;  // Flag RecurseAlloc to stop
   // do some work to free memory
   return 0;
}
// Define a function to be called if new fails to allocate memory.
int MyNewHandler( size_t size )
{
   printf("Allocation failed. Coalescing heap.\n");

   // Call a function to recover some heap space.
   return CoalesceHeap();
}

int RecurseAlloc() {
   int *pi = new int[BIG_NUMBER];
   if (!coalesced)
      RecurseAlloc();
   return 0;
}

int main()
{
   // Set the failure handler for new to be MyNewHandler.
   _set_new_handler( MyNewHandler );
   RecurseAlloc();
}
```

```Output
Allocation failed. Coalescing heap.

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Gratuit](free.md)<br/>
[realloc](realloc.md)<br/>
