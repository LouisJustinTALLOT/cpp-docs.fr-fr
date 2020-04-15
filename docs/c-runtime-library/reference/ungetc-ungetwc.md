---
title: ungetc, ungetwc
ms.date: 4/2/2020
api_name:
- ungetwc
- ungetc
- _o_ungetc
- _o_ungetwc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: 484af7b72f860a8a9d12cf0b62444871caad4675
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361299"
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

*C*<br/>
Caractère à renvoyer (transmission push).

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

En cas de succès, chacune de ces fonctions renvoie l’argument de caractère *c*. Si *c* ne peut pas être repoussé ou si aucun personnage n’a été lu, le flux d’entrée est inchangé et **ungetc** renvoie **EOF**; **ungetwc** retourne **WEOF**. Si *le flux* est **NULL**, le gestionnaire de paramètres invalides est invoqué, tel que décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **EOF** ou **WEOF** est retourné et **errno** est réglé à **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **ungetc** repousse le personnage *c* sur le *flux* et efface l’indicateur de fin de fichier. Le flux doit être ouvert pour lecture. Une opération de lecture ultérieure sur *le flux* commence par *c*. Une tentative de pousser **EOF** sur le flux à l’aide **d’ungetc** est ignorée.

Les caractères placés sur le flux par **ungetc** peuvent être effacés si **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**, ou [rembobinage](rewind.md) est appelé avant que le personnage est lu à partir du flux. L’indicateur de position de fichier prend alors la valeur qui était la sienne avant que les caractères soient renvoyés via la transmission push. Le stockage externe correspondant au flux est inchangé. Lors **d’un appel nongetc** réussi contre un flux de texte, l’indicateur de position du fichier n’est pas spécifié jusqu’à ce que tous les caractères repoussés soient lus ou jetés. Sur chaque appel **ungetc** réussi contre un flux binaire, l’indicateur de position de fichier est décrète ; si sa valeur était de 0 avant un appel, la valeur n’est pas définie après l’appel.

Les résultats sont imprévisibles si **ungetc** est appelé deux fois sans une opération de lecture ou de positionnement de fichiers entre les deux appels. Après un appel à **fscanf**, un appel à **ungetc** peut échouer à moins qu’une autre opération de lecture (comme **getc**) a été effectuée. C’est parce que **fscanf** lui-même appelle **ungetc**.

**ungetwc** est une version à caractère large de **ungetc**. Cependant, sur chaque appel **ungetwc** réussi contre un texte ou un flux binaire, la valeur de l’indicateur de position de fichier n’est pas spécifiée jusqu’à ce que tous les caractères repoussés soient lus ou jetés.

Ces fonctions sont thread-safe et verrouillent les données sensibles pendant l’exécution. Pour une version sans verrouillage, consultez [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications Universal Windows Platform (UWP). Les poignées de flux standard qui sont associées à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions C run-time peuvent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
