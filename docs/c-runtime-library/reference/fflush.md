---
title: fflush
ms.date: 11/04/2016
apiname:
- fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: d03d20ee5024915d0ca4c5a21db4159e8c4f876a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329109"
---
# <a name="fflush"></a>fflush

Vide un flux.

## <a name="syntax"></a>Syntaxe

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fflush** retourne 0 si la mémoire tampon a été vidée. La valeur 0 est également retournée si le flux spécifié n’a aucune mémoire tampon ou est ouvert en lecture seule. La valeur de retour **EOF** indique une erreur.

> [!NOTE]
> Si **fflush** retourne **EOF**, données ont peut-être été perdues en raison d’une erreur d’écriture. Lorsque vous configurez un gestionnaire d’erreurs critiques, il est plus sûr de désactiver la mise en mémoire tampon avec la **setvbuf** fonction ou d’utiliser des routines de bas niveau d’e/s comme **_open**, **_close**, et **_write** au lieu des fonctions de flux d’e/s.

## <a name="remarks"></a>Notes

Le **fflush** fonction vide le flux *flux*. Si le flux a été ouvert en mode d’écriture ou qu’il a été ouvert en mode de mise à jour et que la dernière opération était une écriture, le contenu de la mémoire tampon du flux est écrit dans le fichier ou périphérique sous-jacent et la mémoire tampon est abandonnée. Si le flux a été ouvert en mode lecture, ou si le flux n’a pas de mémoire tampon, l’appel à **fflush** n’a aucun effet, et toutes les mémoires tampons sont conservé. Un appel à **fflush** annule l’effet d’un appel antérieur à **ungetc** pour le flux. Le flux reste ouvert après l’appel.

Si *flux* est **NULL**, le comportement est identique à un appel à **fflush** sur chaque flux ouvert. Tous les flux ouverts en mode d’écriture et tous les flux ouverts en mode de mise à jour où la dernière opération était une écriture sont vidés. L’appel n’a aucun effet sur les autres flux.

Les mémoires tampons sont normalement gérées par le système d’exploitation, qui détermine à quel moment les données doivent être automatiquement écrites sur le disque : quand une mémoire tampon est saturée, quand un flux est fermé ou quand un programme se termine normalement sans fermer le flux. La fonctionnalité de validation sur disque de la bibliothèque runtime garantit que les données critiques sont écrites directement sur le disque plutôt que dans les mémoires tampons du système d’exploitation. Sans réécrire un programme existant, vous pouvez activer cette fonctionnalité en liant les fichiers objets du programme avec COMMODE.OBJ. Dans le fichier exécutable résultant, les appels à **_flushall** écrire le contenu de toutes les mémoires tampons sur le disque. Uniquement **_flushall** et **fflush** sont affectés par COMMODE.OBJ.

Pour plus d’informations sur le contrôle de la fonctionnalité de validation sur disque, consultez [E/S de flux](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) et [_fdopen](fdopen-wfdopen.md).

Cette fonction verrouille le thread appelant et est donc thread-safe. Pour obtenir une version sans verrouillage, consultez **_fflush_nolock**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fflush.c
#include <stdio.h>
#include <conio.h>

int main( void )
{
   int integer;
   char string[81];

   // Read each word as a string.
   printf( "Enter a sentence of four words with scanf: " );
   for( integer = 0; integer < 4; integer++ )
   {
      scanf_s( "%s", string, sizeof(string) );
      printf( "%s\n", string );
   }

   // You must flush the input buffer before using gets.
   // fflush on input stream is an extension to the C standard
   fflush( stdin );
   printf( "Enter the same sentence with gets: " );
   gets_s( string, sizeof(string) );
   printf( "%s\n", string );
}
```

```Input
This is a test
This is a test
```

```Output
Enter a sentence of four words with scanf: This is a test
This
is
a
test
Enter the same sentence with gets: This is a test
This is a test
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
