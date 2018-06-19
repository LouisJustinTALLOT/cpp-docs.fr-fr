---
title: atexit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- atexit
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
- atexit
dev_langs:
- C++
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d66954348d5d812fac7eca0b231304267cc26157
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393132"
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

*Func*<br/>
Fonction à appeler.

## <a name="return-value"></a>Valeur de retour

**atexit** retourne 0 en cas de réussite, ou une valeur différente de zéro si une erreur se produit.

## <a name="remarks"></a>Notes

Le **atexit** fonction reçoit l’adresse d’une fonction *func* à appeler lorsque le programme se termine normalement. Les appels successifs à **atexit** créer un Registre de fonctions qui sont exécutées par ordre dernier entré, premier sorti (LIFO). Les fonctions passé à **atexit** ne peut pas prendre de paramètres. **atexit** et **_onexit** utiliser le segment de mémoire pour conserver l’historique des fonctions. Le nombre de fonctions pouvant être enregistrées n’est donc limité que par la mémoire de tas.

Le code dans le **atexit** fonction ne doit pas contenir une dépendance sur n’importe quelle DLL qui peut avoir déjà été déchargé lorsque le **atexit** est appelée.

Pour générer une application compatible ANSI, utilisez la norme ANSI **atexit** (fonction) (au lieu de la même **_onexit** fonction).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Exemple

Ce programme push quatre fonctions dans la pile de fonctions à exécuter lorsque **atexit** est appelée. Quand le programme s’arrête, ces programmes sont exécutés dans l’ordre « dernier entré, premier sorti ».

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
