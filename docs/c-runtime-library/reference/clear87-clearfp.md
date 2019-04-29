---
title: _clear87, _clearfp
ms.date: 04/05/2018
apiname:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
ms.openlocfilehash: 4148f85d82a4210033686455c73046081832e3c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340546"
---
# <a name="clear87-clearfp"></a>_clear87, _clearfp

Obtient et efface le mot d'état à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Valeur de retour

Les bits dans la valeur retournée indiquent l’état à virgule flottante avant l’appel à **_clear87** ou **_clearfp**. Pour obtenir une définition complète des bits retournés par **_clear87**, consultez Float.h. Une part importante des fonctions de bibliothèque mathématique modifie le mot d'état 8087/80287, avec des résultats imprévisibles. Valeurs de retour de **_clear87** et **_status87** deviennent plus fiable que moins d’opérations à virgule flottante sont effectuées entre les états connus du mot d’état à virgule flottante.

## <a name="remarks"></a>Notes

Le **_clear87** fonction efface les indicateurs d’exception dans le mot d’état à virgule flottante, définit le bit occupé à 0 et retourne le mot d’état. Le mot d'état à virgule flottante est une combinaison du mot d'état 8087/80287 et d'autres conditions détectées par le gestionnaire d'exceptions 8087/80287, telles que le dépassement de capacité positif et négatif de pile à virgule flottante.

**_clearfp** est une version portable indépendante de la plateforme de la **_clear87** routine. Il est identique à **_clear87** sur les plateformes Intel (x86) et prend également en charge les x64 et les plateformes ARM. Pour vous assurer que votre code en virgule flottante peut être transféré à x64 et ARM, utilisez **_clearfp**. Si vous ciblez uniquement x86 plateformes, vous pouvez utiliser **_clear87** ou **_clearfp**.

Ces fonctions sont déconseillées lors de la compilation avec [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , car le common language runtime prend uniquement en charge la précision à virgule flottante par défaut.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp**|\<float.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_clear87.c
// compile with: /Od

// This program creates various floating-point
// problems, then uses _clear87 to report on these problems.
// Compile this program with Optimizations disabled (/Od).
// Otherwise the optimizer will remove the code associated with
// the unused floating-point values.
//

#include <stdio.h>
#include <float.h>

int main( void )
{
   double a = 1e-40, b;
   float x, y;

   printf( "Status: %.4x - clear\n", _clear87()  );

   // Store into y is inexact and underflows:
   y = a;
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );

   // y is denormal:
   b = y;
   printf( "Status: %.4x - denormal\n", _clear87() );
}
```

```Output
Status: 0000 - clear
Status: 0003 - inexact, underflow
Status: 80000 - denormal
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
