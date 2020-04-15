---
title: fflush
ms.date: 4/2/2020
api_name:
- fflush
- _o_fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: 401f715e99e6304f0726c8b9c96a71d9582dbc1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347169"
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

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fflush** retourne 0 si le tampon a été rincé avec succès. La valeur 0 est également retournée si le flux spécifié n’a aucune mémoire tampon ou est ouvert en lecture seule. Une valeur de retour **d’EOF** indique une erreur.

> [!NOTE]
> Si **fflush** **renvoie EOF**, les données peuvent avoir été perdues en raison d’une défaillance d’écriture. Lors de la mise en place d’un gestionnaire d’erreur critique, il est plus sûr d’éteindre la mise en mémoire tampon avec la fonction **setvbuf** ou d’utiliser des routines I/O de bas niveau telles que **_open,** **_close,** et **_write** au lieu des fonctions I/O du flux.

## <a name="remarks"></a>Notes

La fonction **fflush** chasse le *flux*. Si le flux a été ouvert en mode d’écriture ou qu’il a été ouvert en mode de mise à jour et que la dernière opération était une écriture, le contenu de la mémoire tampon du flux est écrit dans le fichier ou périphérique sous-jacent et la mémoire tampon est abandonnée. Si le flux a été ouvert en mode lecture, ou si le flux n’a pas de tampon, l’appel à **fflush n’a** aucun effet, et tout tampon est conservé. Un appel à **fflush** annule l’effet de tout appel préalable à **ungetc** pour le flux. Le flux reste ouvert après l’appel.

Si *le flux* est **NULL**, le comportement est le même qu’un appel à **fflush** sur chaque flux ouvert. Tous les flux ouverts en mode d’écriture et tous les flux ouverts en mode de mise à jour où la dernière opération était une écriture sont vidés. L’appel n’a aucun effet sur les autres flux.

Les mémoires tampons sont normalement gérées par le système d’exploitation, qui détermine à quel moment les données doivent être automatiquement écrites sur le disque : quand une mémoire tampon est saturée, quand un flux est fermé ou quand un programme se termine normalement sans fermer le flux. La fonctionnalité de validation sur disque de la bibliothèque runtime garantit que les données critiques sont écrites directement sur le disque plutôt que dans les mémoires tampons du système d’exploitation. Sans réécrire un programme existant, vous pouvez activer cette fonctionnalité en liant les fichiers objets du programme avec COMMODE.OBJ. Dans le fichier exécutable qui en résulte, les appels pour **_flushall** écrire le contenu de tous les tampons sur disque. Seuls **_flushall** et **fflush** sont affectés par COMMODE.OBJ.

Pour plus d’informations sur le contrôle de la fonctionnalité de validation sur disque, consultez [E/S de flux](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) et [_fdopen](fdopen-wfdopen.md).

Cette fonction verrouille le thread appelant et est donc thread-safe. Pour une version non-locking, voir **_fflush_nolock**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fflush.c
// Compile with: cl /W4 crt_fflush.c
// This sample gets a number from the user, then writes it to a file.
// It ensures the write isn't lost on crash by calling fflush.
#include <stdio.h>

int * crash_the_program = 0;

int main(void)
{
    FILE * my_file;
    errno_t err = fopen_s(&my_file, "myfile.txt", "w");
    if (my_file && !err)
    {
        printf("Write a number: ");

        int my_number = 0;
        scanf_s("%d", &my_number);

        fprintf(my_file, "User selected %d\n", my_number);

        // Write data to a file immediately instead of buffering.
        fflush(my_file);

        if (my_number == 5)
        {
            // Without using fflush, no data was written to the file
            // prior to the crash, so the data is lost.
            *crash_the_program = 5;
        }

        // Normally, fflush is not needed as closing the file will write the buffer.
        // Note that files are automatically closed and flushed during normal termination.
        fclose(my_file);
    }
    return 0;
}
```

```Input
5
```

```myfile.txt
User selected 5
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
