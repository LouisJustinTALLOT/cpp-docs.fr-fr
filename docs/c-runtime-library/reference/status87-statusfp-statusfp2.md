---
title: _status87, _statusfp, _statusfp2 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
dev_langs:
- C++
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e6028d98be0d3b5648018712b47d506f73550a6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="status87-statusfp-statusfp2"></a>_status87, _statusfp, _statusfp2

Obtient le mot d’état de virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>Paramètres

*px86*<br/>
Cette adresse est complétée avec le mot d’état de l’unité de virgule flottante x87.

*pSSE2*<br/>
Cette adresse est complétée avec le mot d’état de l’unité de virgule flottante SSE2.

## <a name="return-value"></a>Valeur de retour

Pour **_status87** et **_statusfp**, les bits de la valeur retournée indiquent l’état à virgule flottante. Consultez la valeur flottante. H à inclure pour une définition des bits retournés par **_statusfp**. Une part importante des fonctions de bibliothèque mathématique modifie le mot d’état de virgule flottante, avec des résultats imprévisibles. L’optimisation peut réorganiser, combiner et éliminer les opérations à virgule flottante autour des appels à **_status87**, **_statusfp**et des fonctions associées. Utilisez l’option du compilateur [/Od (Désactiver (Déboage))](../../build/reference/od-disable-debug.md) ou la directive pragma [fenv_access](../../preprocessor/fenv-access.md) pour éviter les optimisations qui réorganisent les opérations en virgule flottante. Valeurs de retour de **_clearfp** et **_statusfp**et également les paramètres de retournés de **_statusfp2**, sont plus fiables si moins d’opérations à virgule flottante sont effectuées. entre les états connus du mot d’état à virgule flottante.

## <a name="remarks"></a>Notes

Le **_statusfp** fonction obtient le mot d’état à virgule flottante. Le mot d’état est une combinaison de l’état du processeur de virgule flottante et d’autres conditions détectées par le gestionnaire d’exceptions de virgule flottante, par exemple le dépassement de capacité positif et négatif de pile en virgule flottante. Les exceptions démasquées sont vérifiées avant que le contenu du mot d’état soit retourné. Cela signifie que l’appelant est informé des exceptions en attente. Sur x86 plates-formes, **_statusfp** retourne une combinaison de la x87 et l’état de virgule flottante SSE2. Sur les plateformes X64, l’état retourné repose sur l’état MXCSR de SSE. Sur les plateformes ARM, **_statusfp** retourne l’état à partir du Registre fpscr.

**_statusfp** est une version portable indépendante de la plate-forme de **_status87**. Il est identique à **_status87** sur les plateformes Intel (x86) et est également pris en charge par le x64 et les plateformes ARM. Pour vous assurer que votre code à virgule flottante peut être utilisé dans toutes les architectures, utilisez **_statusfp**. Si vous ciblez uniquement x86 plateformes, vous pouvez utiliser **_status87** ou **_statusfp**.

Nous vous recommandons de **_statusfp2** pour les puces (par exemple, le vecteur d’initialisation Pentium) qui ont un x87 et un processeur à virgule flottante SSE2. Pour **_statusfp2**, les adresses sont remplis à l’aide du mot d’état à virgule flottante pour le x87 ou le processeur à virgule flottante SSE2. Pour un processeur qui prend en charge les x87 et les processeurs à virgule flottante SSE2, EM_AMBIGUOUS a la valeur 1 si **_statusfp** ou **_controlfp** est utilisé et l’action est AMBIGUE, car elle peut désigner le x87 ou le SSE2 mot d’état à virgule flottante. Le **_statusfp2** fonction est uniquement pris en charge sur x86 plateformes.

Ces fonctions ne sont pas utiles pour [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , car le common language runtime (CLR) prend uniquement en charge la précision en virgule flottante par défaut.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_status87**, **_statusfp**, **_statusfp2**|\<float.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_statusfp.c
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c
// This program creates various floating-point errors and
// then uses _statusfp to display messages that indicate these problems.

#include <stdio.h>
#include <float.h>
#pragma fenv_access(on)

double test( void )
{
   double a = 1e-40;
   float b;
   double c;

   printf("Status = 0x%.8x - clear\n", _statusfp());

   // Assignment into b is inexact & underflows:
   b = (float)(a + 1e-40);
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());

   // c is denormal:
   c = b / 2.0;
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",
            _statusfp());

   // Clear floating point status:
   _clearfp();
   return c;
}

int main(void)
{
   return (int)test();
}
```

```Output
Status = 0x00000000 - clear
Status = 0x00000003 - inexact, underflow
Status = 0x00080003 - inexact, underflow, denormal
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
