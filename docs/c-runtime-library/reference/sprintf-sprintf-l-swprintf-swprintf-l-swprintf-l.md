---
title: sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
ms.date: 11/04/2016
apiname:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: f32b1622539e73ab04c19d6d46ffdbc58b9961d6
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210846"
---
# <a name="sprintf-sprintfl-swprintf-swprintfl-swprintfl"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

Écrire des données mises en forme dans une chaîne. Il existe des versions plus sécurisées de certaines de ces fonctions. Consultez [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md). Les versions sécurisées de **swprintf** et **_swprintf_l** ne prennent pas une *nombre* paramètre.

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

*buffer*<br/>
Emplacement de stockage pour la sortie

*count*<br/>
Nombre maximal de caractères à stocker dans la version Unicode de cette fonction.

*format*<br/>
Chaîne de contrôle de format

*argument*<br/>
Arguments facultatifs

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d'informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur de retour

Le nombre de caractères écrits, ou -1 si une erreur s’est produite. Si *tampon* ou *format* est un pointeur null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent -1 et la valeur **errno** à **EINVAL**.

**sprintf** retourne le nombre d’octets stockés dans *tampon*, sans compter le caractère null de fin. **swprintf** retourne le nombre de caractères larges stockés dans *tampon*, sans compter le caractère large null de fin.

## <a name="remarks"></a>Notes

Le **sprintf** fonction met en forme et stocke une série de caractères et de valeurs dans *tampon*. Chaque *argument* (le cas échéant) est converti et sorti selon la spécification de format correspondante dans *format*. Le format se compose de caractères ordinaires et a les mêmes forme et fonction que le *format* argument pour [printf](printf-printf-l-wprintf-wprintf-l.md). Un caractère null est ajouté après le dernier caractère écrit. Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

> [!IMPORTANT]
> À l’aide de **sprintf**, il n’existe aucun moyen de limiter le nombre de caractères écrits, ce qui signifie qu’à l’aide de code **sprintf** est vulnérable à des dépassements de mémoire tampon. Envisagez d’utiliser la fonction related [_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), qui spécifie un nombre maximal de caractères à écrire dans *tampon*, ou utilisez [_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md) pour déterminer quelle taille un mémoire tampon est requise. En outre, vérifiez que *format* n’est pas une chaîne définie par l’utilisateur.

**swprintf** est une version à caractères larges de **sprintf**; les arguments de pointeur à **swprintf** sont des chaînes à caractères larges. Détection d’erreurs dans d’encodage **swprintf** peut différer de celle dans **sprintf**. **swprintf** et **fwprintf** ont un comportement identique, sauf que **swprintf** écrit la sortie vers une chaîne plutôt que vers une destination de type **fichier**et **swprintf** nécessite le *nombre* paramètre pour spécifier le nombre maximal de caractères à écrire. Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’ils utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

**swprintf** conforme au Standard ISO C, ce qui nécessite le deuxième paramètre, *nombre*, de type **size_t**. Pour forcer l’ancien comportement non standard, définissez **_CRT_NON_CONFORMING_SWPRINTFS**. Sachant que l'ancien comportement risque d'être retiré dans une version ultérieure, il est conseillé de modifier le code pour utiliser le nouveau comportement conforme.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

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

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

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
