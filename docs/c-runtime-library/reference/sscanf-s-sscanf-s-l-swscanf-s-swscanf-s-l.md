---
description: 'En savoir plus sur les éléments suivants : sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l'
title: sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l
ms.date: 11/04/2016
api_name:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
ms.openlocfilehash: 3f61292932ea6b77b4694588726094d78b8405cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171307"
---
# <a name="sscanf_s-_sscanf_s_l-swscanf_s-_swscanf_s_l"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l

Lit les données mises en forme d’une chaîne. Ces versions de [sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Données stockées

*format*<br/>
Chaîne de contrôle de format. Pour plus d’informations, consultez [Champs de spécification de format : fonctions scanf et wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*argument*<br/>
Arguments facultatifs

*locale*<br/>
Paramètres régionaux à utiliser

## <a name="return-value"></a>Valeur renvoyée

Chacune de ces fonctions retourne le nombre de champs correctement convertis et assignés. La valeur de retour n’inclut pas les champs qui ont été lus, mais pas assignés. La valeur de retour 0 indique qu'aucun champ n'a été assigné. La valeur de retour est **EOF** pour une erreur ou si la fin de la chaîne est atteinte avant la première conversion.

Si la *mémoire tampon* ou le *format* est un pointeur **null** , le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **sscanf_s** lit les données de la *mémoire tampon* dans l’emplacement donné par chaque *argument*. Les arguments qui suivent la chaîne de format spécifient des pointeurs vers des variables dont le type correspond à un spécificateur de type au *format*. Contrairement à la version moins sécurisée [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md), un paramètre de taille de mémoire tampon est requis lorsque vous utilisez les jeux de contrôles de type **c**, **c**, **s**, **s** ou String placés dans **[]**. La taille de mémoire tampon des caractères doit être fournie comme paramètre supplémentaire de suite après chaque paramètre de mémoire tampon qui le nécessite. Par exemple, si vous lisez une chaîne, la taille de la mémoire tampon pour cette chaîne est passée comme suit :

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

La taille de la mémoire tampon inclut le caractère Null de fin. Un champ de spécification de largeur peut être utilisé pour faire en sorte que le jeton lu tiendra dans la mémoire tampon. Si aucun champ de spécification de largeur n'est utilisé, et si le jeton lu est trop grand pour la mémoire tampon, aucune valeur n'est écrite dans cette mémoire tampon.

Dans le cas des caractères, un caractère unique peut être lu comme suit :

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

Cet exemple lit un caractère unique dans la chaîne d’entrée et le stocke dans une mémoire tampon à caractères larges. Quand vous lisez plusieurs caractères pour des chaînes qui ne se terminent pas par un caractère Null, des entiers non signés sont utilisés pour spécifier la largeur et la taille de la mémoire tampon.

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Pour plus d’informations, consultez [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) et [Caractères du champ de type scanf](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Le paramètre de taille est de type **`unsigned`** , et non **size_t**. Lors de la compilation pour les cibles 64 bits, utilisez un cast statique pour convertir **_countof** ou **`sizeof`** les résultats à la taille correcte.

L’argument *format* contrôle l’interprétation des champs d’entrée et a les mêmes forme et fonction que l’argument *format* pour la fonction **scanf_s** . Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

**swscanf_s** est une version à caractères larges de **sscanf_s**; les arguments de **swscanf_s** sont des chaînes à caractères larges. **sscanf_s** ne gère pas les caractères hexadécimaux multioctets. **swscanf_s** ne gère pas les caractères hexadécimaux ou « zone de compatibilité » Unicode à pleine chasse. Dans le cas contraire, **swscanf_s** et **sscanf_s** se comportent de la même façon.

Les versions de ces fonctions qui ont le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**sscanf_s**, **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**, **_swscanf_s_l**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
