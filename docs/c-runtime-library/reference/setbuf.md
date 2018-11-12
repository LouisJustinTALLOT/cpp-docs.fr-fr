---
title: setbuf
ms.date: 11/04/2016
apiname:
- setbuf
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
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: 3b5fbccd304d406131b0c4f7d16a289f80484642
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440494"
---
# <a name="setbuf"></a>setbuf

Contrôle la mise en mémoire tampon de flux. Cette fonction est dépréciée. Utilisez à la place [setvbuf](setvbuf.md).

## <a name="syntax"></a>Syntaxe

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Paramètres

*flux de données*<br/>
Pointeur désignant la structure **FILE**.

*buffer*<br/>
Mémoire tampon allouée par l’utilisateur.

## <a name="remarks"></a>Notes

Le **setbuf** mise en mémoire tampon pour les contrôles de la fonction *flux*. Le *flux* argument doit faire référence à un fichier ouvert qui n’a pas été lues ou écrit. Si le *tampon* argument est **NULL**, le flux est non mis en mémoire tampon. Si non, la mémoire tampon doit pointer vers un tableau de caractères de longueur **BUFSIZ**, où **BUFSIZ** est la taille du tampon, tel que défini dans STDIO. H. La mémoire tampon spécifiée par l’utilisateur est utilisée pour la mise en mémoire tampon des E/S à la place de la mémoire tampon par défaut allouée par le système. Le **stderr** flux est non mis en mémoire tampon par défaut, mais vous pouvez utiliser **setbuf** pour assigner des mémoires tampon à **stderr**.

**setbuf** a été remplacé par [setvbuf](setvbuf.md), qui est la routine par défaut pour le nouveau code. **setbuf** est conservé pour la compatibilité avec le code existant.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
