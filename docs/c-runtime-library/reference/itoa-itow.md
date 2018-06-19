---
title: _itoa, les fonctions _itow | Documents Microsoft
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
dev_langs:
- C++
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95aa140eae6d8a06eff84d03cbb562444c3bd552
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405534"
---
# <a name="itoa-itoa-ltoa-ltoa-ultoa-ultoa-i64toa-ui64toa-itow-ltow-ultow-i64tow-ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Convertit un entier en chaîne. Des versions plus sécurisées de ces fonctions sont disponibles. consultez [_itoa_s, _itow_s fonctions](itoa-s-itow-s.md).

## <a name="syntax"></a>Syntaxe

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These Posix versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>Paramètres

*valeur*<br/>
Nombre à convertir.

*buffer*<br/>
Mémoire tampon qui conserve le résultat de la conversion.

*radix*<br/>
La base à utiliser pour la conversion de *valeur*, qui doit être comprise entre 2-36.

*size*<br/>
Longueur de la mémoire tampon dans les unités de type de caractère. Ce paramètre est déduit à partir de la *tampon* argument en C++.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers *tampon*. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Le **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, et **_ui64toa** fonctions convertissent les chiffres de la donnée *valeur* argument à une chaîne de caractères terminée par null et le magasin le résultat (près de 33 caractères pour **_itoa**, **_ltoa**, et  **_ultoa**et 65 pour **_i64toa** et **_ui64toa**) dans *tampon*. Si *radix* est égal à 10 et *valeur* est négatif, le premier caractère de la chaîne stockée est le signe moins (**-**). Le **_itow**, **_ltow**, **_ultow**, **_i64tow**, et **_ui64tow** les fonctions sont des caractères larges les versions de **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, et **_ui64toa**, respectivement.

> [!IMPORTANT]
> Ces fonctions peuvent écrire au-delà de la fin d’une mémoire tampon est trop petite. Pour éviter les dépassements de mémoire tampon, vérifiez que *tampon* est suffisamment grande pour contenir les chiffres convertis ainsi que le caractère null de fin et un caractère de signe. Utilisation incorrecte de ces fonctions peut entraîner des problèmes de sécurité graves dans votre code.

En raison de leur risque de problèmes de sécurité, par défaut, ces fonctions provoquent avertissement de désapprobation [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **cette fonction ou une variable peut présenter un risque. Envisagez d’utiliser** *safe_function* **à la place. Pour désactiver la désapprobation, utilisez _CRT_SECURE_NO_WARNINGS.** Nous vous recommandons de modifier votre code source à utiliser le *safe_function* suggérée par le message d’avertissement. Les fonctions plus sécurisées n’écrivent pas plus de caractères que la taille de mémoire tampon spécifiée. Pour plus d’informations, consultez [_itoa_s, _itow_s fonctions](itoa-s-itow-s.md).

Pour utiliser ces fonctions sans l’avertissement de désapprobation, définir le **_CRT_SECURE_NO_WARNINGS** macro de préprocesseur avant d’inclure des en-têtes CRT. Cela en ajoutant la ligne de commande dans une invite de commandes développeur la **/D_CRT_SECURE_NO_WARNINGS** l’option du compilateur le **cl** commande. Sinon, définissez la macro dans vos fichiers sources. Si vous utilisez des en-têtes précompilés, définissez la macro en haut de l’en-tête précompilé inclure le fichier, généralement stdafx.h. Pour définir la macro dans votre code source, utilisez un **#define** directive avant d’inclure n’importe quel en-tête de la bibliothèque CRT, comme dans cet exemple :

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents et plus sûres. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Les noms Posix **itoa**, **ltoa**, et **ultoa** existe en tant qu’alias pour la **_itoa**, **_ltoa**, et **_ultoa** fonctions. Les noms Posix sont déconseillées, car ils ne suivent pas les conventions de nom de ISO C. spécifique à l’implémentation (fonction) Par défaut, ces fonctions provoquent avertissement de désapprobation [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **nom le POSIX pour cet élément est déconseillé. Au lieu de cela, utilisez le nom conforme ISO C et C++ :** *nouveau_nom*. Nous vous recommandons de modifier votre code source afin d’utiliser les versions plus sécurisées de ces fonctions, **_itoa_s**, **_ltoa_s**, ou **_ultoa_s**. Pour plus d’informations, consultez [_itoa_s, _itow_s fonctions](itoa-s-itow-s.md).

Pour la portabilité du code source, vous pouvez conserver les noms Posix dans votre code. Pour utiliser ces fonctions sans l’avertissement de désapprobation, définir les deux le **_CRT_NONSTDC_NO_WARNINGS** et **_CRT_SECURE_NO_WARNINGS** des macros de préprocesseur avant d’inclure des en-têtes CRT. Cela en ajoutant la ligne de commande dans une invite de commandes développeur la **/D_CRT_SECURE_NO_WARNINGS** et **/D_CRT_NONSTDC_NO_WARNINGS** les options du compilateur pour le **cl**commande. Sinon, définissez les macros dans vos fichiers sources. Si vous utilisez des en-têtes précompilés, définir les macros en haut de l’en-tête précompilé incluent le fichier, généralement stdafx.h. Pour définir les macros dans votre code source, utilisez **#define** directives avant d’inclure n’importe quel en-tête de la bibliothèque CRT, comme dans cet exemple :

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Macros de nombre maximal de conversion

Pour vous aider à créer des tampons sécurisés pour les conversions, la bibliothèque CRT inclut des macros pratiques. Définir la taille de la mémoire tampon requise pour convertir la valeur la plus longue possible de chaque type d’entier, y compris le terminateur null et les signer caractère, pour plusieurs bases de common. Pour vous assurer que votre mémoire tampon est assez grande pour recevoir une conversion dans la base spécifiée par *radix*, utilisez une de ces défini macros lorsque vous allouez de la mémoire tampon. Cela contribue à éviter les erreurs de dépassement de mémoire tampon lors de la conversion de types intégraux en chaînes. Ces macros sont définies lorsque vous incluez stdlib.h ou wchar.h dans votre source.

Pour utiliser une de ces macros dans une fonction de conversion de chaîne, déclarer votre mémoire tampon de conversion du type de caractère approprié et utiliser la valeur de la macro pour le type entier et la base que la dimension de la mémoire tampon. Ce tableau répertorie les macros appropriées pour chaque fonction pour les bases des listés :

||||
|-|-|-|
|Fonctions|radix|Macros|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

Cet exemple utilise une macro de conversion de nombre pour définir une mémoire tampon suffisamment grande pour contenir un **unsigned long long** 2 de base :

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h> ou \<wchar.h>|

Ces fonctions et les macros sont spécifiques à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple illustre l’utilisation de certaines fonctions de conversion d’entier. Notez l’utilisation de la **_CRT_SECURE_NO_WARNINGS** macro progressivement avertissement C4996.

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s, _itow_s fonctions](itoa-s-itow-s.md)<br/>
