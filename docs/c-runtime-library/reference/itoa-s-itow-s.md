---
title: _itoa_s, _itow_s functions
ms.date: 03/21/2018
apiname:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
- _itot_s
- _ltot_s
- _ultot_s
- _i64tot_s
- _ui64tot_s
- itoa_s
- ltoa_s
- ultoa_s
- i64toa_s
- ui64toa_s
- itow_s
- ltow_s
- ultow_s
- i64tow_s
- ui64tow_s
- itot_s
- ltot_s
- ultot_s
- i64tot_s
- ui64tot_s
helpviewer_keywords:
- _ui64toa_s function
- _itow_s function
- _i64tow_s function
- _itot_s function
- converting integers
- itow_s function
- i64toa_s function
- _ui64tow_s function
- integers, converting
- _i64tot_s function
- itoa_s function
- _itoa_s function
- ui64toa_s function
- i64tow_s function
- converting numbers, to strings
- _ui64tot_s function
- _i64toa_s function
ms.assetid: eb746581-bff3-48b5-a973-bfc0a4478ecf
ms.openlocfilehash: e534a9010f3f39c517b7b0f2bf50041190caf7d8
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210352"
---
# <a name="itoas-ltoas-ultoas-i64toas-ui64toas-itows--ltows--ultows-i64tows-ui64tows"></a>_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s,  _ltow_s,  _ultow_s, _i64tow_s, _ui64tow_s

Convertit un entier en chaîne. Il s’agit de versions de la [_itoa, les fonctions _itow](itoa-itow.md) intègrent les améliorations de sécurité comme décrit dans [des fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _itoa_s( int value, char * buffer, size_t size, int radix );
errno_t _ltoa_s( long value, char * buffer, size_t size, int radix );
errno_t _ultoa_s( unsigned long value, char * buffer, size_t size, int radix );
errno_t _i64toa_s( long long value, char *buffer,
   size_t size, int radix );
errno_t _ui64toa_s( unsigned long long value, char *buffer,
   size_t size, int radix );

errno_t _itow_s( int value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ltow_s( long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ultow_s( unsigned long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _i64tow_s( long long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ui64tow_s( unsigned long long value, wchar_t *buffer,
   size_t size, int radix
);

// These template functions are C++ only:
template <size_t size>
errno_t _itoa_s( int value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ltoa_s( long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ultoa_s( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _itow_s( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ltow_s( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ultow_s( unsigned long value, wchar_t (&buffer)[size], int radix );
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Nombre à convertir.

*buffer*<br/>
Mémoire tampon de sortie qui contient le résultat de la conversion.

*size*<br/>
Taille de *tampon* en caractères ou de caractères larges.

*radix*<br/>
La base ou une base numérique à utiliser pour convertir *valeur*, qui doit être comprise entre 2 et 36.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec. Si l’une des conditions suivantes s’applique, la fonction appelle un gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

### <a name="error-conditions"></a>Conditions d’erreur

|par défaut|buffer|size|radix|Retourner|
|-----------|------------|----------------------|-----------|------------|
|any|**NULL**|any|any|**EINVAL**|
|any|any|<=0|any|**EINVAL**|
|any|any|<= longueur de la chaîne de résultat requise|any|**EINVAL**|
|any|any|any|*radix* < 2 ou *radix* > 36|**EINVAL**|

### <a name="security-issues"></a>Problèmes de sécurité

Ces fonctions peuvent générer une violation d’accès si *tampon* ne pointe pas vers une mémoire valide et n’est pas **NULL**, ou si la longueur de la mémoire tampon n’est pas suffisante pour contenir la chaîne de résultat.

## <a name="remarks"></a>Notes

Sauf pour les paramètres et la valeur de retour, le **_itoa_s** et **_itow_s** familles de fonctions ont le même comportement que le correspondantes moins sécurisée **_itoa** et **_itow** versions.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Les versions debug des bibliothèques de ces fonctions remplissent d’abord la mémoire tampon avec 0xFD. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

La bibliothèque CRT inclut des macros pratiques pour définir la taille de la mémoire tampon nécessaire pour convertir la valeur la plus longue possible de chaque type d’entier, y compris le terminateur null et signer les caractères, pour plusieurs bases courants. Pour plus d’informations, consultez [macros de conversion de nombre Maximum](itoa-itow.md#maximum-conversion-count-macros).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot_s**|**_itoa_s**|**_itoa_s**|**_itow_s**|
|**_ltot_s**|**_ltoa_s**|**_ltoa_s**|**_ltow_s**|
|**_ultot_s**|**_ultoa_s**|**_ultoa_s**|**_ultow_s**|
|**_i64tot_s**|**_i64toa_s**|**_i64toa_s**|**_i64tow_s**|
|**_ui64tot_s**|**_ui64toa_s**|**_ui64toa_s**|**_ui64tow_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_itoa_s**, **_ltoa_s**, **_ultoa_s**, **_i64toa_s**, **_ui64toa_s**|\<stdlib.h>|
|**_itow_s**, **_ltow_s**, **_ultow_s**, **_i64tow_s**, **_ui64tow_s**|\<stdlib.h> ou \<wchar.h>|

Ces fonctions sont spécifiques à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple illustre l’utilisation de quelques-unes des fonctions de conversion d’entier. Notez que le [_countof](countof-macro.md) macro fonctionne uniquement pour déterminer la taille de mémoire tampon lors de la déclaration de tableau est visible par le compilateur et pas pour les paramètres qui ont cariés aux pointeurs.

```C
// crt_itoa_s.c
// Compile by using: cl /W4 crt_itoa_s.c
#include <stdlib.h>     // for _itoa_s functions, _countof, count macro
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen

int main( void )
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;
    for ( r = 10; r >= 2; --r )
    {
        _itoa_s( -1, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _i64toa_s( -1LL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _ui64toa_s( 0xffffffffffffffffULL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
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
[_itoa, _itow fonctions](itoa-itow.md)<br/>
