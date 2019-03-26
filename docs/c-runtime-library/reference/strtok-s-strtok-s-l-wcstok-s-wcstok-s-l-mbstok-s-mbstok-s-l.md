---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 03/25/2019
apiname:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: e2c237927aa133d33085be40b88789c1024d6b34
ms.sourcegitcommit: 6e4dd21759caaed262a7255735cf8d6e8fb9f4d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476888"
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Recherche le prochain jeton dans une chaîne en utilisant les paramètres régionaux actifs ou les paramètres régionaux qui ont été transmis. Ces versions de [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s** et **_mbstok_s_l** ne peut pas être utilisé dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Chaîne contenant l’ou les jetons à rechercher.

*delimiters*<br/>
Le jeu de caractères de séparation à utiliser.

*context*<br/>
Utilisé pour stocker les informations de position entre les appels à la fonction.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le prochain jeton trouvé dans *str*. Retourne **NULL** lorsque plus aucun jeton ne se trouvent. Chaque appel modifie *str* en remplaçant un caractère null pour le premier délimiteur qui se produit après le jeton retourné.

### <a name="error-conditions"></a>Conditions d’erreur

|*str*|*delimiters*|*context*|Valeur de retour|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|any|pointeur vers un pointeur Null|**NULL**|**EINVAL**|
|any|**NULL**|any|**NULL**|**EINVAL**|
|any|any|**NULL**|**NULL**|**EINVAL**|

Si *str* est **NULL** mais *contexte* est un pointeur vers un pointeur de contexte valide, il n’existe aucune erreur.

## <a name="remarks"></a>Notes

Le **strtok_s** famille de fonctions recherche le prochain jeton dans *str*. Le jeu de caractères dans *délimiteurs* spécifie les délimiteurs possibles du jeton doit être recherché dans *str* lors de l’appel actuel. **wcstok_s** et **_mbstok_s** sont des versions à caractères larges et à caractères multioctets de **strtok_s**. Les arguments et les valeurs de retour de **wcstok_s** et **_wcstok_s_l** sont des caractères larges chaînes ; ceux de **_mbstok_s** et **_mbstok_s_l**sont des chaînes de caractères multioctets. Ces fonctions se comportent sinon de façon identique.

Cette fonction valide ses paramètres. Lorsqu’une condition d’erreur se produit, comme indiqué dans le tableau de Conditions d’erreur, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourner **NULL**.

Sur le premier appel à **strtok_s**, la fonction ignore les délimiteurs de début et retourne un pointeur désignant le premier jeton dans *str*, le jeton par un caractère null de fin d’exécution. Plus de jetons peuvent être tirés de la suite de *str* par une série d’appels à **strtok_s**. Chaque appel à **strtok_s** modifie *str* en insérant un caractère null après le jeton retourné par cet appel. Le *contexte* pointeur effectue le suivi de chaîne est en cours de lecture et où la chaîne où le prochain jeton doit être lu. Pour lire le prochain jeton à partir de *str*, appelez **strtok_s** avec un **NULL** valeur pour le *str* argument, puis passez le même  *contexte* paramètre. Le **NULL** *str* argument causes **strtok_s** pour rechercher le prochain jeton dans le texte modifié *str*. Le *délimiteurs* argument peut prendre n’importe quelle valeur à partir d’un seul appel à l’autre afin que l’ensemble de délimiteurs peut varier.

Dans la mesure où le *contexte* paramètre remplace les mémoires tampons statiques utilisées dans **strtok** et **_strtok_l**, il est possible d’analyser deux chaînes simultanément dans le même thread.

La valeur de sortie est affectée par la valeur de la **LC_CTYPE** paramètre de catégorie de paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md).

Les versions de ces fonctions sans le **_l** suffixe utiliser des paramètres régionaux du thread actuel pour ce comportement dépendant des paramètres régionaux. Les versions avec le **_l** suffixe sont identiques, à ceci près qu’ils utilisent à la place les paramètres régionaux spécifiés par le *paramètres régionaux* paramètre. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> ou \<wchar.h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|\_UNICODE & \_MBCS non définis|\_MBCS défini|_UNICODE défini|
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

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
