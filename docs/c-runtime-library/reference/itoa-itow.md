---
title: _itoa, _itow fonctions
ms.date: 4/2/2020
api_name:
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
- _o__i64toa
- _o__i64tow
- _o__itoa
- _o__itow
- _o__ltoa
- _o__ltow
- _o__ui64toa
- _o__ui64tow
- _o__ultoa
- _o__ultow
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 0cc084076c5e39843ecc1afa08671ce6b2f06d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342712"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Convertit un entier en chaîne. Des versions plus sécurisées de ces fonctions sont disponibles; voir [_itoa_s, _itow_s fonctions](itoa-s-itow-s.md).

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

// These POSIX versions of the functions have deprecated names:
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

*value*<br/>
Nombre à convertir.

*buffer*<br/>
Tampon qui détient le résultat de la conversion.

*Radix*<br/>
La base à utiliser pour la conversion de la *valeur*, qui doit être dans la gamme 2-36.

*Taille*<br/>
Longueur du tampon dans les unités du type de personnage. Ce paramètre est déduit de l’argument *du tampon* dans l’argument de la zone tampon.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions renvoie un pointeur à *tampon .* Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Les **fonctions _itoa**, **_ltoa**, **_ultoa**, **_i64toa**, et **_ui64toa** de convertir les chiffres de l’argument de *valeur* donnée à une chaîne de caractères non terminée et stocker le résultat (jusqu’à 33 caractères pour **_itoa**, **_ltoa**, et **_ultoa**, et 65 pour **_i64toa** et **_ui64toa**) dans *le tampon*. Si *le radix* est égal à 10 et que la *valeur* **-** est négative, le premier caractère de la chaîne stockée est le signe moins (). Les **fonctions _itow**, **_ltow**, **_ultow**, **_i64tow**, et **_ui64tow** sont des versions à caractère large de **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, et **_ui64toa**, respectivement.

> [!IMPORTANT]
> Ces fonctions peuvent écrire au-delà de la fin d’un tampon qui est trop petit. Pour éviter les dépassements de mémoire tampon, assurez-vous que le *tampon* est assez grand pour tenir les chiffres convertis ainsi que le caractère nul de fuite et un caractère de signe. L’utilisation abusive de ces fonctions peut causer de graves problèmes de sécurité dans votre code.

En raison de leur potentiel de problèmes de sécurité, par défaut, ces fonctions provoquent l’avertissement de dépréciation [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Cette fonction ou cette variable peut être dangereuse. Envisagez plutôt d’utiliser** *safe_function.* ** Pour désactiver la dépréciation, utilisez _CRT_SECURE_NO_WARNINGS.** Nous vous recommandons de modifier votre code source pour utiliser les *safe_function* suggérées par le message d’avertissement. Les fonctions les plus sécurisées n’écrivent pas plus de caractères que la taille spécifiée du tampon. Pour plus d’informations, voir [_itoa_s, _itow_s fonctions](itoa-s-itow-s.md).

Pour utiliser ces fonctions sans l’avertissement de dépréciation, définissez le **_CRT_SECURE_NO_WARNINGS** macro préprocesseur avant d’inclure les en-têtes CRT. Vous pouvez le faire sur la ligne de commande dans une invite de commande développeur en ajoutant **l’option de** compilateur /D_CRT_SECURE_NO_WARNINGS à la commande **cl.** Sinon, définissez la macro dans vos fichiers sources. Si vous utilisez des en-têtes précompilés, définissez la macro en haut de l’en-tête précompilé inclure fichier, *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt). Pour définir la macro dans votre code source, utilisez une directive **#define** avant d’inclure un en-tête CRT, comme dans cet exemple :

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

Dans le C, ces fonctions ont des surcharges de modèles qui invoquent leurs homologues plus sûrs. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les noms POSIX **itoa**, **ltoa**, et **ultoa** existent comme alias pour le **_itoa**, **_ltoa**, et **_ultoa** fonctions. Les noms POSIX sont dépréciés parce qu’ils ne suivent pas les conventions de nom de fonction globale spécifiques à la mise en œuvre de l’ISO C. Par défaut, ces fonctions provoquent l’avertissement de dépréciation [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **Le nom POSIX pour cet article est déprécié. Utilisez plutôt le nom conformant ISO C et CMD :** *new_name*. Nous vous recommandons de modifier votre code source pour utiliser les versions plus sûres de ces fonctions, **_itoa_s**, **_ltoa_s**, ou **_ultoa_s**. Pour plus d’informations, voir [_itoa_s, _itow_s fonctions](itoa-s-itow-s.md).

Pour la portabilité du code source, vous préférerez peut-être conserver les noms POSIX dans votre code. Pour utiliser ces fonctions sans l’avertissement de dépréciation, définissez à la fois les macros **_CRT_NONSTDC_NO_WARNINGS** et **_CRT_SECURE_NO_WARNINGS** préprocesseur avant d’inclure les en-têtes CRT. Vous pouvez le faire sur la ligne de commande dans une invite de commande de développeur en ajoutant les options **de compilateur /D_CRT_SECURE_NO_WARNINGS** et **/D_CRT_NONSTDC_NO_WARNINGS** à la commande **cl.** Sinon, définissez les macros dans vos fichiers sources. Si vous utilisez des en-têtes précompilés, définissez les macros en haut de l’en-tête précompilé inclure le fichier. Pour définir les macros de votre code source, utilisez **#define** directives avant d’inclure un en-tête CRT, comme dans cet exemple :

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Macros de nombre de conversions maximales

Pour vous aider à créer des tampons sécurisés pour les conversions, le CRT inclut des macros pratiques. Ceux-ci définissent la taille du tampon nécessaire pour convertir la plus longue valeur possible de chaque type d’intégrateur, y compris le terminateur et le caractère de signe nuls, pour plusieurs bases communes. Pour vous assurer que votre tampon de conversion est suffisamment grand pour recevoir toute conversion dans la base spécifiée par *radix*, utilisez l’une de ces macros définies lorsque vous allouez le tampon. Cela permet d’éviter les erreurs de dépassement de mémoire tampon lorsque vous convertissez les types intégral en chaînes. Ces macros sont définies lorsque vous incluez stdlib.h ou wchar.h dans votre source.

Pour utiliser l’une de ces macros dans une fonction de conversion de chaîne, déclarez votre tampon de conversion du type de personnage approprié et utilisez la valeur macro pour le type et la base de l’intégrage comme dimension tampon. Ce tableau répertorie les macros qui conviennent à chaque fonction pour les bases énumérées :

||||
|-|-|-|
|Fonctions|radix|Macros|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

Cet exemple utilise une macro de nombre de conversions pour définir un tampon assez grand pour contenir un long de base **non signé long** dans la base 2 :

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

Ces fonctions et macros sont spécifiques à Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet échantillon démontre l’utilisation de certaines des fonctions de conversion de l’intégrant. Notez l’utilisation de la **macro _CRT_SECURE_NO_WARNINGS** pour faire taire l’avertissement C4996.

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
