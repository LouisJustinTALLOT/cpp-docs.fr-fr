---
title: vscanf, vwscanf | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- vscanf
- vwscanf
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
- vscanf
- vwscanf
- _vtscanf
dev_langs:
- C++
ms.assetid: d1df595b-11bc-4682-9441-a92616301e3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 825d0d61fccc6d0f83ae8b11648a3c7a3a9c50a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414322"
---
# <a name="vscanf-vwscanf"></a>vscanf, vwscanf

Lit les données mises en forme du flux d'entrée standard. Il existe des versions plus sécurisées de ces fonctions. Consultez [vscanf_s, vwscanf_s](vscanf-s-vwscanf-s.md).

## <a name="syntax"></a>Syntaxe

```C
int vscanf(
   const char *format,
   va_list arglist
);
int vwscanf(
   const wchar_t *format,
   va_list arglist
);

```

### <a name="parameters"></a>Paramètres

*format*<br/>
Format de la chaîne de contrôle.

*arglist*<br/>
Liste d’arguments de variable.

## <a name="return-value"></a>Valeur de retour

Retourne le nombre de champs correctement convertis et assignés. La valeur de retour n’inclut pas les champs qui ont été lus mais pas assignés. La valeur de retour 0 indique qu'aucun champ n'a été assigné.

Si *format* est un **NULL** pointeur, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EOF** et **errno** à **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **vscanf** fonction lit les données à partir du flux d’entrée standard **stdin** et écrit les données dans les emplacements qui sont fournis par le *arglist* liste d’arguments. Chaque argument dans la liste doit être un pointeur vers une variable d’un type qui correspond à un spécificateur de type dans *format*. Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

> [!IMPORTANT]
> Lorsque vous utilisez **vscanf** pour lire une chaîne, spécifiez toujours une largeur de la **%s** format (par exemple, **« % 32s »** au lieu de **« %s »**) ; Sinon, une entrée au format incorrect peut entraîner un dépassement de mémoire tampon. En guise d’alternative, vous pouvez utiliser [vscanf_s, vwscanf_s](vscanf-s-vwscanf-s.md) ou [fgets](fgets-fgetws.md).

**vwscanf** est une version à caractères larges de **vscanf**; le *format* argument **vwscanf** est une chaîne à caractères larges. **vwscanf** et **vscanf** se comportent de façon identique, si le flux est ouvert en mode ANSI. **vscanf** ne prend pas en charge d’entrée à partir d’un flux de données UNICODE.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtscanf**|**vscanf**|**vscanf**|**vwscanf**|

Pour plus d’informations, consultez [Champs de spécification de format : fonctions scanf et wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**vscanf**|\<stdio.h>|
|**vwscanf**|\<stdio.h> ou \<wchar.h>|

La console n’est pas pris en charge dans les applications de plateforme Windows universelle (UWP). Les descripteurs de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions d’exécution C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_vscanf.c
// compile with: /W3
// This program uses the vscanf and vwscanf functions
// to read formatted input.

#include <stdio.h>
#include <stdarg.h>

int call_vscanf(char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vscanf(format, arglist);
    va_end(arglist);
    return result;
}

int call_vwscanf(wchar_t *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vwscanf(format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    int   i, result;
    float fp;
    char  c, s[81];
    wchar_t wc, ws[81];
    result = call_vscanf( "%d %f %c %C %80s %80S", &i, &fp, &c, &wc, s, ws );
    printf( "The number of fields input is %d\n", result );
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
    result = call_vwscanf( L"%d %f %hc %lc %80S %80ls", &i, &fp, &c, &wc, s, ws );
    wprintf( L"The number of fields input is %d\n", result );
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}

```

```Output

      71 98.6 h z Byte characters
36 92.3 y n Wide charactersThe number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vscanf_s, vwscanf_s](vscanf-s-vwscanf-s.md)<br/>
