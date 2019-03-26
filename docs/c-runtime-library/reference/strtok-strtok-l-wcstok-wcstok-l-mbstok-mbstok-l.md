---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 03/25/2019
apiname:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
apitype: DLLExport
f1_keywords:
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: 22dd01a0b2558c83ca1e25875a2ace7dd4ee15c0
ms.sourcegitcommit: 6e4dd21759caaed262a7255735cf8d6e8fb9f4d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476914"
---
# <a name="strtok-strtokl-wcstok-wcstokl-mbstok-mbstokl"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Recherche le prochain jeton dans une chaîne en utilisant les paramètres régionaux actifs ou les paramètres régionaux spécifiés qui ont été transmis. Il existe des versions plus sécurisées de ces fonctions. Consultez [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok** et **_mbstok_l** ne peut pas être utilisé dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*strToken*<br/>
Chaîne contenant le ou les jetons.

*strDelimit*<br/>
Jeu de caractères délimiteurs.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le prochain jeton trouvé dans *strToken*. Les fonctions retournent **NULL** lorsque plus aucun jeton ne se trouvent. Chaque appel modifie *strToken* en remplaçant un caractère null pour le premier délimiteur qui se produit après le jeton retourné.

## <a name="remarks"></a>Notes

Le **strtok** fonction recherche le prochain jeton dans *strToken*. Le jeu de caractères dans *strDelimit* spécifie les délimiteurs possibles du jeton doit être recherché dans *strToken* sur l’appel en cours. **wcstok** et **_mbstok** sont des versions à caractères larges et à caractères multioctets de **strtok**. Les arguments et la valeur de retour de **wcstok** sont des caractères larges chaînes ; ceux de **_mbstok** sont des chaînes de caractères multioctets. Ces trois fonctions se comportent sinon de façon identique.

> [!IMPORTANT]
> Ces fonctions sont exposées à une menace potentielle liée à un problème de dépassement de mémoire tampon. Les dépassements de mémoire tampon sont une méthode fréquente d'attaque du système, ce qui provoque une élévation des privilèges injustifiée. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/desktop/SecBP/avoiding-buffer-overruns).

Sur le premier appel à **strtok**, la fonction ignore les délimiteurs de début et retourne un pointeur désignant le premier jeton dans *strToken*, le jeton par un caractère null de fin d’exécution. Plus de jetons peuvent être tirés de la suite de *strToken* par une série d’appels à **strtok**. Chaque appel à **strtok** modifie *strToken* en insérant un caractère null après la **jeton** retourné par cet appel. Pour lire le prochain jeton à partir de *strToken*, appelez **strtok** avec un **NULL** valeur pour le *strToken* argument. Le **NULL** *strToken* argument causes **strtok** pour rechercher le prochain jeton dans le texte modifié *strToken*. Le *strDelimit* argument peut prendre n’importe quelle valeur à partir d’un seul appel à l’autre afin que l’ensemble de délimiteurs peut varier.

La valeur de sortie est affectée par la valeur de la **LC_CTYPE** paramètre de catégorie de paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md).

Les versions de ces fonctions sans le **_l** suffixe utiliser les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux. Les versions avec le **_l** suffixe sont identiques, sauf qu’ils utilisent les paramètres régionaux à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> Chaque fonction utilise une variable statique locale de thread pour analyser la chaîne en jetons. Par conséquent, plusieurs threads peuvent appeler simultanément ces fonctions sans effets indésirables. Cependant, dans un thread unique, il est très probable que l’entrelacement d’appels dans l’une de ses fonctions se traduise par une altération des données et des résultats imprécis. Quand il s’agit d’analyser différentes chaînes, terminez l’analyse d’une chaîne avant de débuter celle de la suivante. De même, tenez compte du risque potentiel que représente l’appel de l’une de ces fonctions dans une boucle pendant qu’une autre fonction est appelée. S l’une de ces fonctions met fin à l’autre fonction, une séquence entrelacée d’appels est générée, ce qui a pour conséquence d’altérer les données.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<string.h> ou \<wchar.h>|
|**_mbstok**, **_mbstok_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
