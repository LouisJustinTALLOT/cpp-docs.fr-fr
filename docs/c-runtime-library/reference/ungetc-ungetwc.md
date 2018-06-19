---
title: ungetc, ungetwc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ungetwc
- ungetc
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ungettc
- ungetwc
- ungetc
dev_langs:
- C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6618e3e92d605d9e706331b44b352b41d29d6a61
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414580"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Renvoie un caractère dans le flux via une transmission de type push.

## <a name="syntax"></a>Syntaxe

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à renvoyer (transmission push).

*Flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Si réussite, chacune de ces fonctions retourne l’argument de caractère *c*. Si *c* ne peut pas être déplacées ou si aucun caractère n’a été lu, le flux d’entrée est inchangé et **ungetc** retourne ** EOF`; **ungetwc` retourne **WEOF**. Si *flux* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **EOF** ou **WEOF** est retourné et **errno** a la valeur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **ungetc** fonction transmet le caractère *c* sur *flux* et efface l’indicateur de fin de fichier. Le flux doit être ouvert pour lecture. Opération de lecture suivante sur *flux* commence par *c*. Une tentative de push **EOF** sur le flux de données à l’aide de **ungetc** est ignoré.

Caractères placés sur le flux **ungetc** peuvent être effacées si **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**, ou [rembobiner](rewind.md) est appelée avant que le caractère est en lecture à partir du flux. L’indicateur de position de fichier prend alors la valeur qui était la sienne avant que les caractères soient renvoyés via la transmission push. Le stockage externe correspondant au flux est inchangé. Sur la réussite **ungetc** appel par rapport à un flux de texte, l’indicateur de position de fichier n’est pas spécifié jusqu'à ce que tous les caractères différée de l’objet d’un push sont lues ou ignorées. Sur chaque réussie **ungetc** appel par rapport à un flux binaire, l’indicateur de position de fichier est décrémenté ; si sa valeur était 0 avant un appel, la valeur n’est pas définie après l’appel.

Les résultats sont imprévisibles si **ungetc** est appelée deux fois sans une lecture ou d’une opération de positionnement de fichier entre les deux appels. Après un appel à **fscanf**, un appel à **ungetc** peuvent échouer sauf si une autre opération de lecture (telles que **getc**) a été effectuée. C’est parce que **fscanf** à son tour appelle **ungetc**.

**ungetwc** est une version à caractères larges de **ungetc**. Toutefois, sur chaque réussie **ungetwc** appel par rapport à un flux de texte ou binaire, la valeur de l’indicateur de position de fichier n’est pas spécifié jusqu'à ce que tous les caractères différée de l’objet d’un push sont lues ou ignorées.

Ces fonctions sont thread-safe et verrouillent les données sensibles pendant l’exécution. Pour une version sans verrouillage, consultez [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> ou \<wchar.h>|

La console n’est pas pris en charge dans les applications de plateforme Windows universelle (UWP). Les descripteurs de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions d’exécution C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
