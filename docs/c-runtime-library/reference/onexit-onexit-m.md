---
description: 'En savoir plus sur : _onexit, _onexit_m'
title: _onexit, _onexit_m
ms.date: 11/04/2016
api_name:
- _onexit
- _onexit_m
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
ms.openlocfilehash: 0b79c521b04a4cb1597dda7c7ed2a19ae2dcf905
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151695"
---
# <a name="_onexit-_onexit_m"></a>_onexit, _onexit_m

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

## <a name="return-value"></a>Valeur renvoyée

**_onexit** retourne un pointeur vers la fonction en cas de réussite ou **null** s’il n’y a pas d’espace pour stocker le pointeur de fonction.

## <a name="remarks"></a>Notes

La fonction **_onexit** reçoit l’adresse d’une fonction (*Function*) à appeler lorsque le programme se termine normalement. Les appels successifs à **_onexit** créent un registre des fonctions qui sont exécutées dans l’ordre LIFO (dernier entré, premier sorti). Les fonctions passées à **_onexit** ne peuvent pas prendre de paramètres.

Dans le cas où **_onexit** est appelé à partir d’une dll, les routines inscrites avec **_onexit** s’exécutent sur le déchargement d’une dll après l’appel de **DllMain** avec DLL_PROCESS_DETACH.

**_onexit** est une extension Microsoft. Pour la portabilité ANSI, utilisez [atexit](atexit.md). La version **_onexit_m** de la fonction est destinée à une utilisation en mode mixte.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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

### <a name="output"></a>Output

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
