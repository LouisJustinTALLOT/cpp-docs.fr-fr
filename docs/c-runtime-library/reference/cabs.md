---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cabs
helpviewer_keywords:
- cabs function
- absolute values
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: ba24b10fb267c9b54ec4944704de988128b4b419
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443050"
---
# <a name="_cabs"></a>_cabs

Calcule la valeur absolue d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Paramètres

*Lettre*<br/>
Nombre complexe.

## <a name="return-value"></a>Valeur de retour

**_cabs** retourne la valeur absolue de son argument en cas de réussite. En cas de dépassement, **_cabs** retourne **HUGE_VAL** et définit **errno** sur **ERANGE**. Vous pouvez modifier la gestion des erreurs avec [_matherr](matherr.md).

## <a name="remarks"></a>Notes

La fonction **_cabs** calcule la valeur absolue d’un nombre complexe, qui doit être une structure de type [_complex](../../c-runtime-library/standard-types.md). La structure *z* est composée d’un composant réel *x* et d’un composant imaginaire *y*. Un appel à **_cabs** produit une valeur équivalant à celle de l’expression `sqrt( z.x * z.x + z.y * z.y )`.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Pour plus d’informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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