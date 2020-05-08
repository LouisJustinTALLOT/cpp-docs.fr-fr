---
title: rand_s
ms.date: 4/2/2020
api_name:
- rand_s
- _o_rand_s
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: cad1740e64c7bbda553ac1a6c777d7e2295152ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919544"
---
# <a name="rand_s"></a>rand_s

Génère un nombre pseudo-aléatoire. Il s’agit d’une version plus sécurisée de la fonction [Rand](rand.md), avec des améliorations de sécurité décrites dans [fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Paramètres

*randomValue*<br/>
Pointeur vers un entier destiné à contenir la valeur générée.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, code d’erreur dans un autre cas. Si le pointeur d’entrée _randomValue_ est un pointeur null, la fonction appelle un gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne **EINVAL** et définit **errno** sur **EINVAL**. Si la fonction échoue pour une autre raison, *_randomValue_ a la valeur 0.

## <a name="remarks"></a>Notes 

La fonction **rand_s** écrit un entier Pseudo-aléatoire compris entre 0 et **UINT_MAX** au pointeur d’entrée. La fonction **rand_s** utilise le système d’exploitation pour générer des nombres aléatoires sécurisés par chiffrement. Elle n’utilise pas la valeur de départ générée par la fonction [srand](srand.md) , pas plus qu’elle n’affecte la séquence de nombres aléatoires utilisée par [Rand](rand.md).

La fonction **rand_s** nécessite que la constante **_CRT_RAND_S** soit définie avant l’instruction d’inclusion de la fonction à déclarer, comme dans l’exemple suivant :

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** dépend de l’API [RtlGenRandom](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) , qui est disponible uniquement dans Windows XP et versions ultérieures.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a> Exemple

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

### <a name="sample-output"></a>Exemple de sortie

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
