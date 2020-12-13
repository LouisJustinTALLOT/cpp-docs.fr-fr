---
description: 'En savoir plus sur les éléments suivants : vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l'
title: vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l
ms.date: 09/12/2019
api_name:
- _vswprintf_s_l
- vsprintf_s
- vswprintf_s
- _vsprintf_s_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vswprintf_s
- vsprintf_s
- _vstprintf_s
helpviewer_keywords:
- _vstprintf_s_l function
- vsprintf_s_l function
- _vstprintf_s function
- vswprintf_s function
- vstprintf_s function
- vstprintf_s_l function
- vswprintf_s_l function
- vsprintf_s function
- _vsprintf_s_l function
- formatted text [C++]
- _vswprintf_s_l function
ms.assetid: 60e90518-57f0-4f1b-b732-f62a69702833
ms.openlocfilehash: 725962d2bb08515f60bf3b2ce3342534daaadfa7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342125"
---
# <a name="vsprintf_s-_vsprintf_s_l-vswprintf_s-_vswprintf_s_l"></a>vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l

Écrivez la sortie mise en forme en utilisant un pointeur désignant une liste d’arguments. Ces fonctions sont des versions de [vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, \_ _vswprintf_l](vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md) avec des améliorations de sécurité, comme décrit dans [fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vsprintf_s(
   char *buffer,
   size_t numberOfElements,
   const char *format,
   va_list argptr
);
int _vsprintf_s_l(
   char *buffer,
   size_t numberOfElements,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vswprintf_s(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *format,
   va_list argptr
);
int _vswprintf_s_l(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsprintf_s(
   char (&buffer)[size],
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int vswprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Emplacement de stockage pour la sortie.

*numberOfElements*<br/>
Taille de la *mémoire tampon* en caractères.

*format*<br/>
Spécification de format.

*argptr*<br/>
Pointeur vers la liste d'arguments.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**vsprintf_s** et **vswprintf_s** retournent le nombre de caractères écrits, à l’exclusion du caractère null de fin, ou une valeur négative si une erreur de sortie se produit. Si la *mémoire tampon* ou le *format* est un pointeur null, si *NumberOfElements* est égal à zéro, ou si la chaîne de format contient des caractères de mise en forme non valides, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions prend un pointeur désignant une liste d’arguments, puis met en forme et écrit les données fournies dans la mémoire vers laquelle pointe la *mémoire tampon*.

**vswprintf_s** est conforme à la norme ISO C pour **vswprintf**, qui requiert le deuxième paramètre, *Count*, de type **size_t**.

Ces fonctions se distinguent des versions non sécurisées uniquement par le fait que les versions sécurisées prennent en charge les paramètres positionnels. Pour plus d’informations, consultez [Paramètres positionnels printf_p](../../c-runtime-library/printf-p-positional-parameters.md).

Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle. Les surcharges peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Ils peuvent remplacer automatiquement les fonctions non sécurisées par leurs équivalents sécurisés. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstprintf_s**|**vsprintf_s**|**vsprintf_s**|**vswprintf_s**|
|**_vstprintf_s_l**|**_vsprintf_s_l**|**_vsprintf_s_l**|**_vswprintf_s_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**vsprintf_s**, **_vsprintf_s_l**|\<stdio.h> et \<stdarg.h>|\<varargs.h>*|
|**vswprintf_s**, **_vswprintf_s_l**|\<stdio.h> ou \<wchar.h> , et \<stdarg.h>|\<varargs.h>*|

\* Requis pour la compatibilité UNIX V.

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_vsprintf_s.c
// Compile with: cl /W4 crt_vsprintf_s.c
// This program uses vsprintf_s to write to a buffer.
// The size of the buffer is determined by _vscprintf.

#include <stdlib.h>
#include <stdio.h>
#include <stdarg.h>

void test( char const * const format, ... )
{
   va_list args;
   int len;
   char * buffer;

   va_start( args, format );
   len = _vscprintf( format, args ) // _vscprintf doesn't count
                               + 1; // terminating '\0'
   buffer = (char *) malloc( len * sizeof(char) );
   if ( NULL != buffer )
   {
      vsprintf_s( buffer, len, format, args );
      puts( buffer );
      free( buffer );
   }
   va_end( args );
}

int main( void )
{
   test( "%d %c %d", 123, '<', 456 );
   test( "%s", "This is a string" );
}
```

```Output
123 < 456
This is a string
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
[Syntaxe de spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)
