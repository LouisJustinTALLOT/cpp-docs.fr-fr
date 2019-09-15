---
title: sscanf, _sscanf_l, swscanf, _swscanf_l
ms.date: 08/29/2019
api_name:
- swscanf
- sscanf
- _sscanf_l
- _swscanf_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sscanf_l
- _stscanf
- swscanf
- _stscanf_l
- sscanf
- _swscanf_l
helpviewer_keywords:
- swscanf function
- _stscanf function
- sscanf function
- _stscanf_l function
- _sscanf_l function
- _swscanf_l function
- swscanf_l function
- strings [C++], reading data from
- stscanf function
- reading data, strings
- strings [C++], reading
- sscanf_l function
- stscanf_l function
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
ms.openlocfilehash: e3b453166278fff4c3230cb51895c487319e33d9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958228"
---
# <a name="sscanf-_sscanf_l-swscanf-_swscanf_l"></a>sscanf, _sscanf_l, swscanf, _swscanf_l

Lisent les données mises en forme d’une chaîne. Il existe des versions plus sécurisées de ces fonctions. Consultez [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int sscanf(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Données stockées

*format*<br/>
Chaîne de contrôle de format. Pour plus d'informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*argument*<br/>
Arguments facultatifs

*locale*<br/>
Paramètres régionaux à utiliser

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne le nombre de champs correctement convertis et assignés. La valeur de retour n’inclut pas les champs qui ont été lus, mais pas assignés. La valeur de retour 0 indique qu'aucun champ n'a été assigné. La valeur de retour est **EOF** pour une erreur ou si la fin de la chaîne est atteinte avant la première conversion.

Si la *mémoire tampon* ou le *format* est un pointeur **null** , le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **sscanf** lit les données de la *mémoire tampon* dans l’emplacement donné par chaque *argument*. Chaque *argument* doit être un pointeur vers une variable dont le type correspond à un spécificateur de type au *format*. L’argument *format* contrôle l’interprétation des champs d’entrée et a les mêmes forme et fonction que l’argument *format* pour la fonction **scanf** . Si la copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

Pour plus d’informations sur les caractères du champ de type scanf, consultez [caractères du champ de type scanf](../scanf-type-field-characters.md). Pour plus d’informations sur les champs de spécification de format scanf, consultez [champs de spécification de format](../format-specification-fields-scanf-and-wscanf-functions.md).

> [!IMPORTANT]
> Lors de la lecture d’une chaîne avec **sscanf**, spécifiez toujours une largeur pour le format **% s** (par exemple, **« % 32s »** au lieu de **« % s »** ); dans le cas contraire, une entrée mal mise en forme peut facilement provoquer un dépassement de mémoire tampon.

**swscanf** est une version à caractères larges de **sscanf**; les arguments de **swscanf** sont des chaînes à caractères larges. **sscanf** ne gère pas les caractères hexadécimaux multioctets. **swscanf** ne gère pas les caractères hexadécimaux ou « zone de compatibilité » Unicode à pleine chasse. Sinon, **swscanf** et **sscanf** se comportent de la même façon.

Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf**|**sscanf**|**sscanf**|**swscanf**|
|**_stscanf_l**|**_sscanf_l**|**_sscanf_l**|**_swscanf_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**sscanf**, **_sscanf_l**|\<stdio.h>|
|**swscanf**, **_swscanf_l**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_sscanf.c
// compile with: /W3
// This program uses sscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string:
   sscanf( tokenstring, "%80s", s ); // C4996
   sscanf( tokenstring, "%c", &c );  // C4996
   sscanf( tokenstring, "%d", &i );  // C4996
   sscanf( tokenstring, "%f", &fp ); // C4996
   // Note: sscanf is deprecated; consider using sscanf_s instead

   // Output the data read
   printf( "String    = %s\n", s );
   printf( "Character = %c\n", c );
   printf( "Integer:  = %d\n", i );
   printf( "Real:     = %f\n", fp );
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
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
