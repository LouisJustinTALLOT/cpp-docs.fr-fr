---
title: strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
dev_langs:
- C++
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22adcaafc54a6b086629b7b9087b7088001bba85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417751"
---
# <a name="strnlen-strnlens-wcsnlen-wcsnlens-mbsnlen-mbsnlenl-mbstrnlen-mbstrnlenl"></a>strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l

Obtient la longueur d'une chaîne en utilisant les paramètres régionaux actuels ou ceux qui ont été passés. Il s’agit de versions plus sécurisées de [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).

> [!IMPORTANT]
> **_mbsnlen**, **_mbsnlen_l**, **_mbstrnlen**, et **_mbstrnlen_l** ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne terminée par un caractère Null.

*numberOfElements*<br/>
Taille de la mémoire tampon de chaîne.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Ces fonctions retournent le nombre de caractères dans la chaîne, sans le caractère Null de fin. S’il n’existe aucune marque de fin null au sein de la première *numberOfElements* octets de la chaîne (ou les caractères étendus pour **wcsnlen**), puis *numberOfElements* est retourné à indiquer la condition d’erreur ; chaîne terminée par null ont des longueurs qui sont strictement inférieure à *numberOfElements*.

**_mbstrnlen** et **_mbstrnlen_l** retourne -1 si la chaîne contient un caractère multioctet non valide.

## <a name="remarks"></a>Notes

> [!NOTE]
> **strnlen** n’est pas un remplacement pour **strlen**; **strnlen** est destinée à être utilisée uniquement pour calculer la taille des données non fiables entrantes dans une mémoire tampon de taille connue, par exemple, un paquet réseau. **strnlen** calcule la longueur mais ne continue pas après la fin de la mémoire tampon si la chaîne n’est pas terminée. Dans d’autres situations, utilisez **strlen**. (Le même s’applique aux **wcsnlen**, **_mbsnlen**, et **_mbstrnlen**.)

Chacune de ces fonctions retourne le nombre de caractères dans *str*, sans le caractère null de fin. Toutefois, **strnlen** et **strnlen_s** interpréter la chaîne comme une chaîne de caractères d’un octet et par conséquent, la valeur de retour est toujours égale au nombre d’octets, même si la chaîne contient multioctets caractères. **wcsnlen** et **wcsnlen_s** sont des versions à caractères larges de **strnlen** et **strnlen_s** respectivement ; les arguments pour **wcsnlen**  et **wcsnlen_s** sont des chaînes à caractères larges et le nombre de caractères dans des unités à caractères larges. Dans le cas contraire, **wcsnlen** et **strnlen** se comportent de la même façon, comme **strnlen_s** et **wcsnlen_s**.

**strnlen**, **wcsnlen**, et **_mbsnlen** ne vérifient pas leurs paramètres. Si *str* est **NULL**, une violation d’accès se produit.

**strnlen_s** et **wcsnlen_s** valident leurs paramètres. Si *str* est **NULL**, les fonctions retournent 0.

**_mbstrnlen** valide également ses paramètres. Si *str* est **NULL**, ou si *numberOfElements* est supérieur à **INT_MAX**, **_mbstrnlen** génère une exception de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_mbstrnlen** définit **errno** à **EINVAL** et retourne -1.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen** et **_mbstrnlen** retourner le nombre de caractères multioctets dans une chaîne de caractères multioctets. **_mbsnlen** reconnaît les séquences de caractères multioctets en fonction de la page de codes multioctets qui est actuellement en cours d’utilisation ou selon les paramètres régionaux qui sont passé ; il ne teste pas la validité de caractères multioctets. **_mbstrnlen** teste la validité des caractères multioctets et reconnaît les séquences de caractères multioctets. Si la chaîne est passée à **_mbstrnlen** contient un caractère multioctet non valide, **errno** a la valeur **EILSEQ**.

La valeur de sortie est affectée par la définition de la **LC_CTYPE** catégorie des paramètres régionaux ; consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md) pour plus d’informations. Les versions de ces fonctions sont identiques, sauf que ceux qui n’ont le **_l** suffixe utilisent les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux et les versions qui ont le **_l** suffixe au lieu de cela, utilisez les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strnlen**, **strnlen_s**|\<string.h>|
|**wcsnlen**, **wcsnlen_s**|\<string.h> ou \<wchar.h>|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
