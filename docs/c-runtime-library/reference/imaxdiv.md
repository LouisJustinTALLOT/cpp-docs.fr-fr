---
title: imaxdiv | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- imaxdiv
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- imaxdiv
dev_langs:
- C++
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab39d68f733fdb7d078efdc058f09e30d0fd907b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="imaxdiv"></a>imaxdiv

Calcule le quotient et le reste de deux valeurs entières de n’importe quelle taille en une seule opération.

## <a name="syntax"></a>Syntaxe

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>Paramètres

*nombre*<br/>
Numérateur.

*denom*<br/>
Dénominateur.

## <a name="return-value"></a>Valeur de retour

**imaxdiv** appelée avec des arguments de type [intmax_t](../../c-runtime-library/standard-types.md) retourne une structure de type [imaxdiv_t](../../c-runtime-library/standard-types.md) qui comprend le quotient et le reste.

## <a name="remarks"></a>Notes

Le **imaxdiv** fonction divise *nombre* par *denom* et ce qui calcule le quotient et le reste. Le **imaxdiv_t** structure contient le quotient, **intmax_t** **quot**et le reste, **intmax_t** **rem**. Le signe du quotient est identique à celui du quotient mathématique. Sa valeur absolue est le plus grand entier qui est inférieur à la valeur absolue du quotient mathématique. Si le dénominateur est 0, le programme se termine par un message d’erreur.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

Quand la fonction est générée, puis appelée avec les paramètres de ligne de commande `9460730470000000 8766`, le code génère cette sortie :

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
