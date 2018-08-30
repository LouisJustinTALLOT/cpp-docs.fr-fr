---
title: rand_s | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- rand_s
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
- rand_s
dev_langs:
- C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c75b2988dd00d8141c25e67c29bcc0b082270ffe
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210160"
---
# <a name="rands"></a>rand_s

Génère un nombre pseudo-aléatoire. Il s’agit d’une version plus sécurisée de la fonction [rand](rand.md), avec les améliorations de sécurité comme décrit dans [des fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Paramètres

*randomValue*<br/>
Pointeur vers un entier pour contenir la valeur générée.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, code d’erreur dans un autre cas. Si le pointeur d’entrée _randomValue_ est un pointeur null, la fonction appelle un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne **EINVAL** et définit **errno** à **EINVAL**. Si la fonction échoue pour une raison quelconque, *_randomValue_ est définie sur 0.

## <a name="remarks"></a>Notes

Le **rand_s** fonction écrit un entier pseudo-aléatoire compris dans la plage 0 à **UINT_MAX** au pointeur d’entrée. Le **rand_s** fonction utilise le système d’exploitation pour générer des nombres aléatoires sécurisés par chiffrement. Il n’utilise pas la valeur de départ générée par le [srand](srand.md) (fonction), et n’affecte pas la séquence de nombres aléatoire utilisée par [rand](rand.md).

Le **rand_s** fonction exige que la constante **_CRT_RAND_S** soit définie avant l’instruction d’inclusion pour la fonction d’être déclarés, comme dans l’exemple suivant :

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** varie selon le [RtlGenRandom](/windows/desktop/api/ntsecapi/nf-ntsecapi-rtlgenrandom) API, qui est uniquement disponible dans Windows XP et versions ultérieures.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Pour plus d'informations, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number /
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>Résultat de l'exemple

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
