---
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
api_name:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
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
ms.openlocfilehash: 54faf70296ef41f2682f88a8edaa82ee0d2071d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958090"
---
# <a name="_status87-_statusfp-_statusfp2"></a>_status87, _statusfp, _statusfp2

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

Pour **_status87** et **_statusfp**, les bits de la valeur retournée indiquent l’État à virgule flottante. Voir la valeur FLOAT. Fichier include H pour une définition des bits retournés par **_statusfp**. Une part importante des fonctions de bibliothèque mathématique modifie le mot d’état de virgule flottante, avec des résultats imprévisibles. L’optimisation peut réorganiser, combiner et éliminer les opérations en virgule flottante concernant les appels à **_status87**, **_statusfp**et les fonctions associées. Utilisez l’option du compilateur [/Od (Désactiver (Déboage))](../../build/reference/od-disable-debug.md) ou la directive pragma [fenv_access](../../preprocessor/fenv-access.md) pour éviter les optimisations qui réorganisent les opérations en virgule flottante. Les valeurs de retour de **_clearfp** et **_statusfp**, ainsi que les paramètres de retour de **_statusfp2**, sont plus fiables si moins d’opérations en virgule flottante sont effectuées entre les États connus du mot d’État à virgule flottante.

## <a name="remarks"></a>Notes

La fonction **_statusfp** obtient le mot d’État à virgule flottante. Le mot d’état est une combinaison de l’état du processeur de virgule flottante et d’autres conditions détectées par le gestionnaire d’exceptions de virgule flottante, par exemple le dépassement de capacité positif et négatif de pile en virgule flottante. Les exceptions démasquées sont vérifiées avant que le contenu du mot d’état soit retourné. Cela signifie que l’appelant est informé des exceptions en attente. Sur les plateformes x86, **_statusfp** retourne une combinaison de l’état de virgule flottante X87 et SSE2. Sur les plateformes X64, l’état retourné repose sur l’état MXCSR de SSE. Sur les plateformes ARM, **_statusfp** retourne l’État à partir du registre Registre fpscr.

**_statusfp** est une version portable, indépendante de la plateforme, de **_status87**. Elle est identique à **_status87** sur les plateformes Intel (x86) et est également prise en charge par les plateformes x64 et ARM. Pour vous assurer que votre code à virgule flottante est portable pour toutes les architectures, utilisez **_statusfp**. Si vous ciblez uniquement des plateformes x86, vous pouvez utiliser **_status87** ou **_statusfp**.

Nous vous recommandons **_statusfp2** pour les puces (telles que le Pentium IV) qui ont à la fois un processeur à virgule flottante X87 et un processeur à virgule flottante SSE2. Pour **_statusfp2**, les adresses sont remplies en utilisant le mot d’État à virgule flottante pour le processeur à virgule flottante X87 ou SSE2. Pour un processeur qui prend en charge les processeurs à virgule flottante X87 et SSE2, EM_AMBIGUOUS a la valeur 1 si **_statusfp** ou _ **controlfp** est utilisé et que l’action était ambiguë car elle peut faire référence au mot d’état de virgule flottante X87 ou SSE2. La fonction **_statusfp2** est uniquement prise en charge sur les plateformes x86.

Ces fonctions ne sont pas utiles pour [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , car le Common Language Runtime (CLR) prend uniquement en charge la précision à virgule flottante par défaut.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_status87**, **_statusfp**, **_statusfp2**|\<float.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

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
