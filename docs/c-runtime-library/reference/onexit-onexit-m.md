---
title: _onexit, _onexit_m
ms.date: 11/04/2016
apiname:
- _onexit
- _onexit_m
apilocation:
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
apitype: DLLExport
f1_keywords:
- _onexit
- onexit_m
- onexit
- _onexit_m
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
ms.openlocfilehash: c190f777032904802f771bab9fc323ba305ff32e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156043"
---
# <a name="onexit-onexitm"></a>_onexit, _onexit_m

Inscrit une routine à appeler au moment de la sortie.

## <a name="syntax"></a>Syntaxe

```C
_onexit_t _onexit(
   _onexit_t function
);
_onexit_t_m _onexit_m(
   _onexit_t_m function
);
```

### <a name="parameters"></a>Paramètres

*function*<br/>
Pointeur désignant une fonction à appeler à la sortie.

## <a name="return-value"></a>Valeur de retour

**_onexit** retourne un pointeur vers la fonction en cas de réussite ou **NULL** s’il n’existe pas d’espace pour stocker le pointeur de fonction.

## <a name="remarks"></a>Notes

Le **_onexit** (fonction) est transmise à l’adresse d’une fonction (*fonction*) à appeler lorsque le programme se termine normalement. Les appels successifs à **_onexit** créent un registre des fonctions qui sont exécutées dans l’ordre LIFO (dernier-in-first-out). Les fonctions transmises à **_onexit** ne peut pas prendre de paramètres.

Dans le cas lorsque **_onexit** est appelée à partir d’une DLL, les routines inscrites avec **_onexit** s’exécutent sur une DLL du déchargement après **DllMain** est appelé avec DLL_PROCESS_DETACH.

**_onexit** est une extension Microsoft. Pour la portabilité ANSI, utilisez [atexit](atexit.md). Le **_onexit_m** version de la fonction concerne l’utilisation du mode mixte.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_onexit.c

#include <stdlib.h>
#include <stdio.h>

/* Prototypes */
int fn1(void), fn2(void), fn3(void), fn4 (void);

int main( void )
{
   _onexit( fn1 );
   _onexit( fn2 );
   _onexit( fn3 );
   _onexit( fn4 );
   printf( "This is executed first.\n" );
}

int fn1()
{
   printf( "next.\n" );
   return 0;
}

int fn2()
{
   printf( "executed " );
   return 0;
}

int fn3()
{
   printf( "is " );
   return 0;
}

int fn4()
{
   printf( "This " );
   return 0;
}
```

### <a name="output"></a>Sortie

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
