---
title: _cabs
ms.date: 11/04/2016
apiname:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cabsl
- _cabs
- _cabsl
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 3e95b6f568ce66b8e9e5483bd1dcbcfaa7af3d28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341065"
---
# <a name="cabs"></a>_cabs

Calcule la valeur absolue d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Paramètres

*z*<br/>
Nombre complexe.

## <a name="return-value"></a>Valeur de retour

**_cabs** retourne la valeur absolue de son argument en cas de réussite. En cas de dépassement, **_cabs** retourne **HUGE_VAL** et définit **errno** à **ERANGE**. Vous pouvez modifier la gestion des erreurs avec [_matherr](matherr.md).

## <a name="remarks"></a>Notes

Le **_cabs** fonction calcule la valeur absolue d’un nombre complexe, qui doit être une structure de type [_complex](../../c-runtime-library/standard-types.md). La structure *z* est composé d’un composant réel *x* et un composant imaginaire *y*. Un appel à **_cabs** génère une valeur équivalente à celle de l’expression `sqrt( z.x * z.x + z.y * z.y )`.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)