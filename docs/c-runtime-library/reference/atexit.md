---
description: 'En savoir plus sur : atexit'
title: atexit
ms.date: 11/04/2016
api_name:
- atexit
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: 82c0bbfdb9af62faff9239781b5db340183e25fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117534"
---
# <a name="atexit"></a>atexit

Traite la fonction spécifiée en sortie.

## <a name="syntax"></a>Syntaxe

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>Paramètres

*func*<br/>
Fonction à appeler.

## <a name="return-value"></a>Valeur renvoyée

**atexit** retourne 0 en cas de réussite, ou une valeur différente de zéro si une erreur se produit.

## <a name="remarks"></a>Notes

La fonction **atexit** reçoit l’adresse d’une fonction *Func* à appeler lorsque le programme se termine normalement. Les appels successifs à **atexient** créent un registre des fonctions qui sont exécutées dans l’ordre LIFO (dernier entré, premier sorti). Les fonctions passées à **atexient** ne peuvent pas prendre de paramètres. **atexit** et **_onexit** utiliser le tas pour contenir le registre des fonctions. Le nombre de fonctions pouvant être enregistrées n’est donc limité que par la mémoire de tas.

Le code de la fonction **atexit** ne doit pas contenir de dépendances sur une dll qui aurait pu être déjà déchargée lorsque la fonction **atexit** est appelée.

Pour générer une application conforme à la norme ANSI, utilisez la fonction **atexit** standard (au lieu de la fonction **_onexit** similaire).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Exemple

Ce programme exécute un push de quatre fonctions sur la pile de fonctions à exécuter lorsque **atexit** est appelé. Quand le programme s’arrête, ces programmes sont exécutés dans l’ordre « dernier entré, premier sorti ».

```C
// crt_atexit.c
#include <stdlib.h>
#include <stdio.h>

void fn1( void ), fn2( void ), fn3( void ), fn4( void );

int main( void )
{
   atexit( fn1 );
   atexit( fn2 );
   atexit( fn3 );
   atexit( fn4 );
   printf( "This is executed first.\n" );
}

void fn1()
{
   printf( "next.\n" );
}

void fn2()
{
   printf( "executed " );
}

void fn3()
{
   printf( "is " );
}

void fn4()
{
   printf( "This " );
}
```

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
