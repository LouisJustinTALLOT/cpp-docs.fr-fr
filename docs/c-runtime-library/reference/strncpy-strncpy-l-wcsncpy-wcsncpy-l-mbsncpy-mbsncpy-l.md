---
title: strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l
ms.date: 11/04/2016
apiname:
- strncpy
- _strncpy_l
- _mbsncpy
- wcsncpy
- _mbsncpy_l
- _wcsncpy_l
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
- _fstrncpy
- strncpy
- _ftcsncpy
- _tcsnccpy_l
- _tcsnccpy
- _mbsncpy
- wcsncpy
- _tcsncpy
- _strncpy_l
- _mbsncpy_l
- _wcsncpy_l
helpviewer_keywords:
- wcsncpy_l function
- characters [C++], copying
- mbsncpy_l function
- strncpy_l function
- wcsncpy function
- tcsnccpy function
- ftcsncpy function
- copying characters of strings
- _wcsncpy_l function
- _tcsnccpy function
- _tcsnccpy_l function
- strncpy function
- _tcsncpy function
- mbsncpy function
- _fstrncpy function
- _mbsncpy_l function
- tcsncpy_l function
- tcsnccpy_l function
- fstrncpy function
- strings [C++], copying
- _ftcsncpy function
- _tcsncpy_l function
- _mbsncpy function
- tcsncpy function
- _strncpy_l function
ms.assetid: ac4345a1-a129-4f2f-bb8a-373ec58ab8b0
ms.openlocfilehash: 04ca1f0b689e68008b3b5a57d01e626ee92a60b9
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210430"
---
# <a name="strncpy-strncpyl-wcsncpy-wcsncpyl-mbsncpy-mbsncpyl"></a>strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l

Copie les caractères d'une chaîne vers une autre. Il existe des versions plus sécurisées de ces fonctions. Consultez [strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md).

> [!IMPORTANT]
> **_mbsncpy** et **_mbsncpy_l** ne peut pas être utilisé dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strncpy(
   char *strDest,
   const char *strSource,
   size_t count
);
char *_strncpy_l(
   char *strDest,
   const char *strSource,
   size_t count,
   locale_t locale
);
wchar_t *wcsncpy(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
wchar_t *_wcsncpy_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   locale_t locale
);
unsigned char *_mbsncpy(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count
);
unsigned char *_mbsncpy_l(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
char *strncpy(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
char *_strncpy_l(
   char (&strDest)[size],
   const char *strSource,
   size_t count,
   locale_t locale
); // C++ only
template <size_t size>
wchar_t *wcsncpy(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
wchar_t *_wcsncpy_l(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count,
   locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbsncpy(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncpy_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*strDest*<br/>
Chaîne de destination.

*strSource*<br/>
Chaîne source.

*count*<br/>
Nombre de caractères à copier.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne *strDest*. Aucune valeur de retour n'est réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

Le **strncpy** fonction copie initial *nombre* caractères de *strSource* à *strDest* et retourne *strDest* . Si *nombre* est inférieure ou égale à la longueur de *strSource*, un caractère null n’est pas automatiquement ajouté à la chaîne copiée. Si *nombre* est supérieur à la longueur de *strSource*, la chaîne de destination est remplie avec les caractères null sur toute longueur *nombre*. Le comportement de **strncpy** n’est pas défini si les chaînes source et de destination se chevauchent.

> [!IMPORTANT]
> **strncpy** ne vérifie pas suffisamment d’espace *strDest*; cela rend une cause potentielle de dépassements de mémoire tampon. Le *nombre* argument limite le nombre de caractères copiés ; il n’est pas une limite sur la taille de *strDest*. Lisez l'exemple suivant. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/desktop/SecBP/avoiding-buffer-overruns).

Si *strDest* ou *strSource* est un **NULL** pointeur, ou si *nombre* est inférieure ou égale à zéro, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent -1 et la valeur **errno** à **EINVAL**.

**wcsncpy** et **_mbsncpy** sont des versions à caractères larges et à caractères multioctets de **strncpy**. Les arguments et la valeur de retour de **wcsncpy** et **_mbsncpy** varient en conséquence. Sinon, ces six fonctions se comportent à l'identique.

Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’ils utilisent les paramètres régionaux passé au lieu des paramètres régionaux actuels pour leur comportement dépendant des paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncpy**|**strncpy**|**_mbsnbcpy**|**wcsncpy**|
|**_tcsncpy_l**|**_strncpy_l**|**_mbsnbcpy_l**|**_wcsncpy_l**|

> [!NOTE]
> **_strncpy_l** et **_wcsncpy_l** n’ont aucune dépendance vis-à-vis de paramètres régionaux ; elles sont uniquement fournies pour **_tcsncpy_l** et ne sont pas destinées à être appelées directement.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strncpy**|\<string.h>|
|**wcsncpy**|\<string.h> ou \<wchar.h>|
|**_mbsncpy**, **_mbsncpy_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité de plateforme, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de **strncpy** et comment elle peut être utilisée à mauvais escient pour entraîner des problèmes de sécurité et les bogues de programme. Le compilateur génère un avertissement pour chaque appel à **strncpy** similaire à **crt_strncpy_x86.c (15) : avertissement C4996 : 'strncpy' : Cette fonction ou cette variable peut être non sécurisée. Envisagez d’utiliser strncpy_s à la place. Pour désactiver le message déconseillant l’utilisation, utilisez _CRT_SECURE_NO_WARNINGS. Consultez l’aide en ligne pour plus d’informations.**

```C
// crt_strncpy_x86.c
// Use this command in an x86 developer command prompt to compile:
// cl /TC /W3 crt_strncpy_x86.c

#include <stdio.h>
#include <string.h>

int main() {
   char t[20];
   char s[20];
   char *p = 0, *q = 0;

   strcpy_s(s, sizeof(s), "AA BB CC");
   // Note: strncpy is deprecated; consider using strncpy_s instead
   strncpy(s, "aa", 2);     // "aa BB CC"         C4996
   strncpy(s + 3, "bb", 2); // "aa bb CC"         C4996
   strncpy(s, "ZZ", 3);     // "ZZ",              C4996
                            // count greater than strSource, null added
   printf("%s\n", s);

   strcpy_s(s, sizeof(s), "AA BB CC");
   p = strstr(s, "BB");
   q = strstr(s, "CC");
   strncpy(s, "aa", p - s - 1);   // "aa BB CC"   C4996
   strncpy(p, "bb", q - p - 1);   // "aa bb CC"   C4996
   strncpy(q, "cc",  q - s);      // "aa bb cc"   C4996
   strncpy(q, "dd", strlen(q));   // "aa bb dd"   C4996
   printf("%s\n", s);

   // some problems with strncpy
   strcpy_s(s, sizeof(s), "test");
   strncpy(t, "this is a very long string", 20 ); // C4996
   // Danger: at this point, t has no terminating null,
   // so the printf continues until it runs into one.
   // In this case, it will print "this is a very long test"
   printf("%s\n", t);

   strcpy_s(t, sizeof(t), "dogs like cats");
   printf("%s\n", t);

   strncpy(t + 10, "to chase cars.", 14); // C4996
   printf("%s\n", t);

   // strncpy has caused a buffer overrun and corrupted string s
   printf("Buffer overrun: s = '%s' (should be 'test')\n", s);
   // Since the stack grows from higher to lower addresses, buffer
   // overruns can corrupt function return addresses on the stack,
   // which can be exploited to run arbitrary code.
}
```

Sortie

```Output
ZZ
aa bb dd
this is a very long test
dogs like cats
dogs like to chase cars.
Buffer overrun: s = 'ars.' (should be 'test')
```

La structure des variables automatiques et le niveau de détection d'erreurs et de protection du code peuvent varier en modifiant les paramètres du compilateur. Cet exemple peut donner des résultats différents quand il est généré dans d'autres environnements de compilation ou avec d'autres options de compilateur.

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
