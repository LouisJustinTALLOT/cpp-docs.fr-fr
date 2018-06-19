---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
apitype: DLLExport
f1_keywords:
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
dev_langs:
- C++
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0200740df3b41e356bcf83f0756b8a5267b38166
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417789"
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

Écrire des données mises en forme dans une chaîne. Ces versions de [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int sprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   ...
);
int _sprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale,
   ...
);
int swprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   ...
);
int _swprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale,
   ...
);
template <size_t size>
int sprintf_s(
   char (&buffer)[size],
   const char *format,
   ...
); // C++ only
template <size_t size>
int swprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   ...
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Emplacement de stockage pour la sortie

*sizeOfBuffer*<br/>
Nombre maximal de caractères à stocker.

*format*<br/>
Chaîne de contrôle de format

*...*<br/>
Arguments facultatifs de mise en forme

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d'informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur de retour

Le nombre de caractères écrits, ou -1 si une erreur s’est produite. Si *tampon* ou *format* est un pointeur null, **sprintf_s** et **swprintf_s** retournent -1 et définissez **errno**à **EINVAL**.

**sprintf_s** retourne le nombre d’octets stockés dans *tampon*, sans compter le caractère null de fin. **swprintf_s** retourne le nombre de caractères larges stockés dans *tampon*, sans compter le caractère large null de fin.

## <a name="remarks"></a>Notes

Le **sprintf_s** fonction formate et stocke une série de caractères et les valeurs de *tampon*. Chaque *argument* (le cas échéant) est converti et sorti selon la spécification de format correspondante dans *format*. Le format se compose de caractères ordinaires et a la même forme et fonction que la *format* argument pour [printf](printf-printf-l-wprintf-wprintf-l.md). Un caractère null est ajouté après le dernier caractère écrit. Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

Une des principales différences entre **sprintf_s** et [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) qui est **sprintf_s** vérifie la chaîne de format pour les caractères de mise en forme valides, tandis que [ sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) vérifie uniquement si la chaîne de format ou de la mémoire tampon est **NULL** pointeurs. Si l’une des vérifications échoue, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Parameter Validation](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne -1 et définit **errno** à **EINVAL**.

L’autre différence principale entre **sprintf_s** et [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) qui est **sprintf_s** prend un paramètre de longueur spécifiant la taille de la mémoire tampon de sortie en caractères. Si la mémoire tampon est trop petite pour le texte mis en forme, y compris le caractère null, alors que la mémoire tampon est définie sur une chaîne vide en plaçant un caractère null à *tampon*[0], et le Gestionnaire de paramètre non valide est appelé. Contrairement aux **_snprintf**, **sprintf_s** garantit que la mémoire tampon sera être terminée par null à moins que la taille de mémoire tampon est égale à zéro.

**swprintf_s** est une version à caractères larges de **sprintf_s**; les arguments de pointeur de **swprintf_s** sont des chaînes à caractères larges. La détection des erreurs dans l’encodage **swprintf_s** peut différer de celle dans **sprintf_s**. Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle. Les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement, ce qui évite d’avoir à spécifier un argument taille, et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Il existe des versions de **sprintf_s** qui offrent un contrôle supplémentaire sur ce qui se produit si la mémoire tampon est trop petite. Pour plus d’informations, consultez [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**sprintf_s**, **_sprintf_s_l**|C : \<stdio.h><br /><br /> C++ : \<cstdio> ou \<stdio.h>|
|**swprintf_s**, **_swprintf_s_l**|C : \<stdio.h> ou \<wchar.h><br /><br /> C++ : \<cstdio>, \<cwchar>, \<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_sprintf_s.c
// This program uses sprintf_s to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );

   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );
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
// crt_swprintf_s.c
// wide character example
// also demonstrates swprintf_s returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf_s fails because string contains WEOF (\xffff)
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
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
