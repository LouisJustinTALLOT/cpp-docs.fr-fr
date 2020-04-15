---
title: fputc, fputwc
ms.date: 4/2/2020
api_name:
- fputc
- fputwc
- _o_fputc
- _o_fputwc
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fputc
- fputwc
- _fputtc
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
ms.openlocfilehash: 289e1114a936bdaa41fc59a0526db006536461f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346267"
---
# <a name="fputc-fputwc"></a>fputc, fputwc

Écrit un caractère dans un flux.

## <a name="syntax"></a>Syntaxe

```C
int fputc(
   int c,
   FILE *stream
);
wint_t fputwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*C*<br/>
Caractère à écrire.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne le caractère écrit. Pour **fputc**, une valeur de retour de **EOF** indique une erreur. Pour **fputwc**, une valeur de retour de **WEOF** indique une erreur. Si *le flux* est **NULL**, ces fonctions invoquent le gestionnaire de paramètres invalides, tel que décrit dans La validation [des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ils retournent **EOF** et mettent **errno** à **EINVAL**.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

## <a name="remarks"></a>Notes

Chacune de ces fonctions écrit le caractère *unique c* à un fichier à la position indiquée par l’indicateur de position de fichier associé (si défini) et avance l’indicateur le cas échéant. Dans le cas de **fputc** et **fputwc**, le fichier est associé à *flux*. Si le fichier ne peut pas prendre en charge les demandes de positionnement ou a été ouvert en mode ajout, le caractère est ajouté à la fin du flux.

Les deux fonctions se comportent de la même façon si le flux est ouvert en mode ANSI. **fputc** ne prend actuellement pas en charge la production dans un flux UNICODE.

Les versions avec suffixe **_nolock** sont identiques, à ceci près qu’elles ne sont pas protégées contre les interférences avec d’autres threads. Pour plus d’informations, consultez [_fputc_nolock, _fputwc_nolock](fputc-nolock-fputwc-nolock.md).

Voici une série de notes spécifiques aux routines.

|Routine|Notes|
|-------------|-------------|
|**fputc**|Équivalent au **putc,** mais mis en œuvre uniquement comme une fonction, plutôt que comme une fonction et une macro.|
|**fputwc**|Version à caractère large de **fputc**. Écrit *c* comme un personnage multioctet ou un personnage large selon que le *flux* est ouvert en mode texte ou en mode binaire.|

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications Universal Windows Platform (UWP). Les poignées de flux standard qui sont associées à la console -**stdin**, **stdout**, et **stderr**- doivent être redirigées avant que les fonctions C run-time peuvent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fputc.c
// This program uses fputc
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of fputc!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of fputc!!
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
