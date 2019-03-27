---
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
apiname:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 28697cac20181c3dda0581c7486ebb673aec1241
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508800"
---
# <a name="scanfs-scanfsl-wscanfs-wscanfsl"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

Lit les données mises en forme du flux d'entrée standard. Ces versions de [scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Paramètres

*format*<br/>
Format de la chaîne de contrôle.

*argument*<br/>
Arguments facultatifs.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne le nombre de champs correctement convertis et assignés. La valeur de retour n’inclut pas les champs qui ont été lus mais pas assignés. Une valeur de retour 0 indique aucune champs ont été affectées. La valeur de retour est **EOF** pour une erreur, ou si le caractère de fin de fichier ou le caractère de fin de chaîne est introuvable dans la première tentative de lecture d’un caractère. Si *format* est un **NULL** pointeur, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **scanf_s** et **wscanf_s** retourner **EOF** et définissez **errno** à **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **scanf_s** fonction lit les données à partir du flux d’entrée standard, **stdin**et l’écrit dans *argument*. Chaque *argument* doit être un pointeur vers un type de variable qui correspond au spécificateur de type dans *format*. Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

**wscanf_s** est une version à caractères larges de **scanf_s**; le *format* l’argument de **wscanf_s** est une chaîne de caractères larges. **wscanf_s** et **scanf_s** se comportent comme si le flux est ouvert en mode ANSI. **scanf_s** ne prend actuellement en charge d’entrée à partir d’un flux de données UNICODE.

Les versions de ces fonctions qui ont le **_l** suffixe sont identiques, à ceci près qu’ils utilisent le *paramètres régionaux* paramètre au lieu de paramètres régionaux du thread actuel.

Contrairement aux **scanf** et **wscanf**, **scanf_s** et **wscanf_s** nécessaire de spécifier les tailles des mémoires tampon pour certains paramètres. Spécifier les tailles pour toutes les **c**, **C**, **s**, **S**, ou jeu de contrôles de chaîne **[]** paramètres. La taille du tampon en caractères est passée comme paramètre supplémentaire. Il suit immédiatement le pointeur vers la mémoire tampon ou d’une variable. Par exemple, si vous lisez une chaîne, la taille du tampon pour cette chaîne est passée comme suit :

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

La taille du tampon inclut le terminal null de fin. Vous pouvez utiliser un champ de spécification de largeur pour garantir le jeton qui est lu s’adapte à la mémoire tampon. Lorsqu’un jeton est trop grand pour tenir, rien n’est écrit dans la mémoire tampon sauf s’il existe une spécification de largeur.

> [!NOTE]
> Le paramètre de taille est de type **non signé**, et non **size_t**. Utilisez un cast statique pour convertir un **size_t** valeur **non signé** pour 64 bits des configurations de build.

Le paramètre de taille de mémoire tampon décrit le nombre maximal de caractères, et non en octets. Dans cet exemple, la largeur du type de mémoire tampon ne correspond pas à la largeur du spécificateur de format.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

Le **S** spécificateur de format signifie utiliser la largeur des caractères « inverse » à la largeur par défaut pris en charge par la fonction. La largeur des caractères est le seul octet, mais la fonction prend en charge des caractères codés. Cet exemple lit une chaîne de jusqu'à neuf caractères de largeur de l’octet unique et les place dans une mémoire tampon de double-caractère octets. Les caractères sont traités comme des valeurs codées sur un octet. Les deux premiers caractères sont stockés dans `ws[0]`, alors que les deux derniers sont stockés dans `ws[1]`, et ainsi de suite.

Cet exemple lit un caractère unique :

```C
char c;
scanf_s("%c", &c, 1);
```

Lors de la lecture de plusieurs caractères pour les chaînes non nul, les entiers sont utilisés pour la spécification de largeur et la taille du tampon.

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

Pour plus d’informations, consultez [Spécification de largeur scanf](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

Pour plus d’informations, consultez [Champs de spécification de format : fonctions scanf et wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**scanf_s**, **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**, **_wscanf_s_l**|\<stdio.h> ou \<wchar.h>|

La console n’est pas pris en charge dans les applications Universal Windows Platform (UWP). Les handles de flux standard **stdin**, **stdout**, et **stderr** doivent être redirigés pour que les fonctions runtime C de les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

Ce programme génère la sortie suivante en fonction de ce qui est entré :

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
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
