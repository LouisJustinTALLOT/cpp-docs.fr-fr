---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 4/2/2020
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
- _o__mbstok_s
- _o__mbstok_s_l
- _o_strtok_s
- _o_wcstok_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
ms.openlocfilehash: 9fe89fb897a5459b16c49060359b4bb40bc062a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365222"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Recherche le prochain jeton dans une chaîne en utilisant les paramètres régionaux actifs ou les paramètres régionaux qui ont été transmis. Ces versions de [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s** et **_mbstok_s_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char* strtok_s(
   char* str,
   const char* delimiters,
   char** context
);

char* _strtok_s_l(
   char* str,
   const char* delimiters,
   char** context,
   _locale_t locale
);

wchar_t* wcstok_s(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context
);

wchar_t *_wcstok_s_l(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context,
   _locale_t locale
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context
);

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Une chaîne contenant le jeton ou les jetons à trouver.

*delimiters*<br/>
L’ensemble des caractères delimiter à utiliser.

*context*<br/>
Utilisé pour stocker des informations de position entre les appels à la fonction.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur au jeton suivant trouvé dans *str*. Retourne **NULL** lorsqu’il n’y a plus de jetons. Chaque appel modifie *str* en remplaçant un caractère nul pour le premier délimitant qui se produit après le jeton retourné.

### <a name="error-conditions"></a>Conditions d'erreur

|*Str*|*delimiters*|*context*|Valeur retournée|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**Null**|n'importe laquelle|pointeur vers un pointeur Null|**Null**|**EINVAL (EN)**|
|n'importe laquelle|**Null**|n'importe laquelle|**Null**|**EINVAL (EN)**|
|n'importe laquelle|n'importe laquelle|**Null**|**Null**|**EINVAL (EN)**|

Si *str* est **NULL** mais que *le contexte* est un pointeur vers un pointeur de contexte valide, il n’y a pas d’erreur.

## <a name="remarks"></a>Notes

La **famille strtok_s** de fonctions trouve le jeton suivant en *str*. L’ensemble de caractères dans *les délires* spécifie délimitations possibles du jeton à trouver dans *str* sur l’appel en cours. **wcstok_s** et **_mbstok_s** sont des versions à caractère large et multioctets de **strtok_s**. Les arguments et **les** valeurs de retour de wcstok_s et **de _wcstok_s_l** sont des chaînes de caractère large; ceux de **_mbstok_s** et **_mbstok_s_l** sont des cordes multioctets-caractères. Ces fonctions se comportent sinon de façon identique.

Cette fonction valide ses paramètres. Lorsqu’une condition d’erreur se produit, comme dans le tableau des conditions d’erreur, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [la validation des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retourner **NULL**.

Sur le premier appel à **strtok_s**, la fonction saute delimiters de premier plan et retourne un pointeur à la première jeton en *str*, mettant fin au jeton avec un caractère nul. Plus de jetons peuvent être brisés du reste de *str* par une série d’appels à **strtok_s**. Chaque appel à **strtok_s** modifie *str* en insérant un caractère nul après le jeton retourné par cet appel. Le pointeur de *contexte* garde une trace de la chaîne qui est lue et où dans la chaîne le jeton suivant doit être lu. Pour lire le jeton suivant à partir de *str*, appelez **strtok_s** avec une valeur **NULL** pour *l’argument str,* et passer le même paramètre *de contexte.* *L’argument STR* **NULL** provoque **strtok_s** à la recherche du jeton suivant dans la *str*modifiée . *L’argument des délimitations* peut prendre n’importe quelle valeur d’un appel à l’autre de sorte que l’ensemble des délimitations peut varier.

Étant donné que le paramètre de *contexte* remplace les tampons statiques utilisés dans **le strtok** et **_strtok_l,** il est possible d’analyser deux cordes simultanément dans le même thread.

La valeur de sortie est affectée par l’établissement de la **LC_CTYPE’établissement** de la catégorie du lieu. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md).

Les versions de ces fonctions sans le **suffixe _l** utilisent le thread local actuel pour ce comportement local-dépendant. Les versions avec le **suffixe _l** sont identiques, sauf qu’elles utilisent plutôt le lieu spécifié par le paramètre *local.* Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> ou \<wchar.h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|\_UNICODE & \_MBCS non défini|\_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

## <a name="example"></a>Exemple

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```

```Output
Tokens:
A
        Another
string
        string
of
        parsed
tokens
        at
and
        the
some
        same
more
        time.
tokens
```

## <a name="see-also"></a>Voir aussi

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
