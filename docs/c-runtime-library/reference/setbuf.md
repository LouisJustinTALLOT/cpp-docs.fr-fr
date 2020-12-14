---
description: 'En savoir plus sur : setbuf'
title: setbuf
ms.date: 4/2/2020
api_name:
- setbuf
- _o_setbuf
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: 756cb09fb35ed6e8cf6369f20693e2f0f0b7acaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211061"
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

*train*<br/>
Pointeur désignant la structure **FILE**.

*mémoire tampon*<br/>
Mémoire tampon allouée par l’utilisateur.

## <a name="remarks"></a>Notes

La fonction **setbuf** contrôle la mise en mémoire tampon pour le *flux*. L’argument *Stream* doit faire référence à un fichier ouvert qui n’a pas été lu ou écrit. Si l’argument de *mémoire tampon* a la **valeur null**, le flux n’est pas mis en mémoire tampon. Si ce n’est pas le cas, la mémoire tampon doit pointer vers un tableau de caractères de longueur **BUFSIZ**, où **BUFSIZ** est la taille de la mémoire tampon telle qu’elle est définie dans stdio. H. La mémoire tampon spécifiée par l’utilisateur est utilisée pour la mise en mémoire tampon des E/S à la place de la mémoire tampon par défaut allouée par le système. Le flux **stderr** n’est pas mis en mémoire tampon par défaut, mais vous pouvez utiliser **setbuf** pour assigner des mémoires tampons à **stderr**.

**setbuf** a été remplacé par [setvbuf](setvbuf.md), qui est la routine préférée pour le nouveau code. Contrairement à **setvbuf**, **setbuf** n’a aucun moyen de signaler des erreurs. **setvbuf** vous permet également de contrôler à la fois le mode de mise en mémoire tampon et la taille de la mémoire tampon. **setbuf** existe pour la compatibilité avec le code existant.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
