---
title: _clear87, _clearfp
ms.date: 04/05/2018
api_name:
- _clearfp
- _clear87
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 4ca49895b881d9e307c1116681bc36f86b167c25
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942957"
---
# <a name="_clear87-_clearfp"></a>_clear87, _clearfp

Obtient et efface le mot d'état à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Valeur de retour

Les bits de la valeur retournée indiquent l’État à virgule flottante avant l’appel à **_clear87** ou **_clearfp**. Pour obtenir une définition complète des bits retournés par **_clear87**, consultez float. h. Une part importante des fonctions de bibliothèque mathématique modifie le mot d'état 8087/80287, avec des résultats imprévisibles. Les valeurs de retour de **_clear87** et **_status87** deviennent plus fiables, car moins d’opérations à virgule flottante sont effectuées entre les États connus du mot d’État à virgule flottante.

## <a name="remarks"></a>Notes

La fonction **_clear87** efface les indicateurs d’exception dans le mot d’État à virgule flottante, définit le bit occupé sur 0 et retourne le mot d’État. Le mot d'état à virgule flottante est une combinaison du mot d'état 8087/80287 et d'autres conditions détectées par le gestionnaire d'exceptions 8087/80287, telles que le dépassement de capacité positif et négatif de pile à virgule flottante.

**_clearfp** est une version portable, indépendante de la plateforme, de la routine **_clear87** . Elle est identique à **_clear87** sur les plateformes Intel (x86) et est également prise en charge par les plateformes x64 et ARM. Pour vous assurer que votre code à virgule flottante est portable vers x64 et ARM, utilisez **_clearfp**. Si vous ciblez uniquement des plateformes x86, vous pouvez utiliser **_clear87** ou **_clearfp**.

Ces fonctions sont déconseillées lors de la compilation avec [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , car la Common Language Runtime prend en charge uniquement la précision en virgule flottante par défaut.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp**|\<float.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

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
