---
title: __min
ms.date: 04/05/2018
api_name:
- __min
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
- __min
- min
- _min
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
ms.openlocfilehash: 6b5cc6517c125f91337ca0d9b12b7a49bd7c1753
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951736"
---
# <a name="__min"></a>__min

Macro de préprocesseur qui retourne la plus petite de deux valeurs.

## <a name="syntax"></a>Syntaxe

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>Paramètres

*a*, *b*<br/>
Valeurs de n’importe quel type **<** sur lequel l’opérateur travaille.

## <a name="return-value"></a>Valeur de retour

Le plus petit des deux arguments.

## <a name="remarks"></a>Notes

La macro **__min** compare deux valeurs et retourne la valeur de la plus petite. Les arguments peuvent être de n’importe quel type de données numérique, signé ou non signé. Les deux arguments et la valeur de retour doivent être du même type de données.

L’argument retourné est évalué deux fois par la macro. Cela peut entraîner des résultats inattendus si l’argument est une expression qui modifie sa valeur lors de son évaluation, par `*p++`exemple.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>Exemple

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
