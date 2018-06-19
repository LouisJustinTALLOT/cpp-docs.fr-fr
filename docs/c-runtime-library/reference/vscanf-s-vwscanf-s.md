---
title: vscanf_s, vwscanf_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- vscanf_s
- vwscanf_s
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
- _vtscanf_s
- vscanf_s
- vwscanf_s
dev_langs:
- C++
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c32d1e50f554c32917f9fa0450abba15463386ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415645"
---
# <a name="vscanfs-vwscanfs"></a>vscanf_s, vwscanf_s

Lit les données mises en forme du flux d'entrée standard. Ces versions de [vscanf, vwscanf](vscanf-vwscanf.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vscanf_s(
   const char *format,
   va_list arglist
);
int vwscanf_s(
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

Retourne le nombre de champs correctement convertis et assignés. La valeur de retour n'inclut pas les champs qui ont été lus mais pas assignés. La valeur de retour 0 indique qu'aucun champ n'a été assigné. La valeur de retour est **EOF** pour une erreur, ou si le caractère de fin de fichier ou le caractère de fin de chaîne est rencontré dans la première tentative de lecture d’un caractère. Si *format* est un **NULL** pointeur, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **vscanf_s** et **vwscanf_s** retourner **EOF** et **errno** à **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **vscanf_s** fonction lit les données à partir du flux d’entrée standard **stdin** et écrit les données dans les emplacements qui sont fournis par le *arglist* liste d’arguments. Chaque argument dans la liste doit être un pointeur vers une variable d’un type qui correspond à un spécificateur de type dans *format*. Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

**vwscanf_s** est une version à caractères larges de **vscanf_s**; le *format* argument **vwscanf_s** est une chaîne à caractères larges. **vwscanf_s** et **vscanf_s** se comportent de façon identique, si le flux est ouvert en mode ANSI. **vscanf_s** ne prend pas en charge d’entrée à partir d’un flux de données UNICODE.

Contrairement aux **vscanf** et **vwscanf**, **vscanf_s** et **vwscanf_s** nécessiter la taille de la mémoire tampon à être spécifiée pour tous les paramètres de type d’entrée **c**, **C**, **s**, **S**, ou qui sont inclus dans les jeux de contrôles de chaîne **[]**. La taille de la mémoire tampon en caractères est passée en tant que paramètre supplémentaire immédiatement après le pointeur vers la mémoire tampon ou la variable. La taille de mémoire tampon en caractères pour un **wchar_t** chaîne n’est pas identique à la taille en octets.

La taille de la mémoire tampon inclut le caractère Null de fin. Vous pouvez utiliser un champ de spécification de largeur pour être certain que le jeton lu tiendra dans la mémoire tampon. Si aucun champ de spécification de largeur n'est utilisé, et si le jeton lu est trop grand pour la mémoire tampon, aucune valeur n'est écrite dans cette mémoire tampon.

> [!NOTE]
> Le *taille* paramètre est de type **non signé**, et non **size_t**.

Pour plus d’informations, consultez [Spécification de largeur scanf](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtscanf_s**|**vscanf_s**|**vscanf_s**|**vwscanf_s**|

Pour plus d’informations, consultez [Champs de spécification de format : fonctions scanf et wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**vscanf_s**|\<stdio.h>|
|**wscanf_s**|\<stdio.h> ou \<wchar.h>|

La console n’est pas pris en charge dans les applications de plateforme Windows universelle (UWP). Les descripteurs de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions d’exécution C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_vscanf_s.c
// compile with: /W3
// This program uses the vscanf_s and vwscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vscanf_s(char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int call_vwscanf_s(wchar_t *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vwscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    int   i, result;
    float fp;
    char  c, s[81];
    wchar_t wc, ws[81];
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,
                           &wc, 1, s, _countof(s), ws, _countof(ws) );
    printf( "The number of fields input is %d\n", result );
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                            &wc, 1, s, _countof(s), ws, _countof(ws) );
    wprintf( L"The number of fields input is %d\n", result );
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

Quand l’entrée de l’exemple est communiquée à ce programme, il génère cette sortie :

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[vscanf, vwscanf](vscanf-vwscanf.md)<br/>
