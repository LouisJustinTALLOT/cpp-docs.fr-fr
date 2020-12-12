---
description: 'En savoir plus sur les éléments suivants : sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l'
title: sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
ms.date: 06/23/2020
api_name:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: 12c7560a57c126e2e35cf78b0d11b1262c14a9e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292206"
---
# <a name="sprintf-_sprintf_l-swprintf-_swprintf_l-__swprintf_l"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

Écrire des données mises en forme dans une chaîne. Il existe des versions plus sécurisées de certaines de ces fonctions. Consultez [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md). Les versions sécurisées de **swprintf** et **_swprintf_l** prennent la taille de la mémoire tampon en tant que paramètre.

## <a name="syntax"></a>Syntaxe

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Emplacement de stockage pour la sortie

*count*<br/>
Nombre maximal de caractères à stocker dans la version Unicode de cette fonction.

*format*<br/>
Chaîne de contrôle de format

*argument*<br/>
Arguments facultatifs

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d’informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur renvoyée

Nombre de caractères écrits, ou-1 si une erreur s’est produite. Si la *mémoire tampon* ou le *format* est un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

**sprintf** retourne le nombre d’octets stockés dans la *mémoire tampon*, sans compter le caractère null de fin. **swprintf** retourne le nombre de caractères larges stockés dans la *mémoire tampon*, sans compter le caractère élargi de la valeur null de fin.

## <a name="remarks"></a>Notes

La fonction **sprintf** met en forme et stocke une série de caractères et de valeurs dans *buffer*. Chaque *argument* (le cas échéant) est converti et sorti selon la spécification de format correspondante au *format*. Le format se compose de caractères ordinaires et a la même forme et fonction que l’argument *format* pour [printf](printf-printf-l-wprintf-wprintf-l.md). Un caractère null est ajouté après le dernier caractère écrit. Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

> [!IMPORTANT]
> À l’aide de **sprintf**, il n’existe aucun moyen de limiter le nombre de caractères écrits, ce qui signifie que le code utilisant **sprintf** est vulnérable aux dépassements de mémoire tampon. Envisagez d’utiliser la fonction related [_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), qui spécifie un nombre maximal de caractères à écrire dans la *mémoire tampon*, ou utilisez [_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md) pour déterminer la taille nécessaire d’une mémoire tampon. En outre, assurez-vous que *format* n’est pas une chaîne définie par l’utilisateur.

**swprintf** est une version à caractères larges de **sprintf**; les arguments de pointeur vers **swprintf** sont des chaînes à caractères larges. La détection des erreurs d’encodage dans **swprintf** peut différer de **sprintf**. **swprintf** et **fwprintf** se comportent de la même manière, sauf que **swprintf** écrit la sortie dans une chaîne plutôt que dans une destination de type **file**, et **swprintf** nécessite que le paramètre *Count* spécifie le nombre maximal de caractères à écrire. Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

**swprintf** est conforme à la norme ISO C, qui exige le deuxième paramètre, *Count*, de type **size_t**. Pour forcer l’ancien comportement non standard, définissez **_CRT_NON_CONFORMING_SWPRINTFS**. Sachant que l'ancien comportement risque d'être retiré dans une version ultérieure, il est conseillé de modifier le code pour utiliser le nouveau comportement conforme.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**sprintf**, **_sprintf_l**|\<stdio.h>|
|**swprintf**, **_swprintf_l**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example-use-sprintf-to-format-data"></a>Exemple : utilisation de sprintf pour mettre en forme des données

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example-error-code-handling"></a>Exemple : gestion de code d’erreur

```C
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
