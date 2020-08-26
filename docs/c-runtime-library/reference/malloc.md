---
title: malloc
ms.date: 4/2/2020
api_name:
- malloc
- _o_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: a093dbdbc4849b1c2f3d86e85a5e2b25a7b988e2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836658"
---
# <a name="malloc"></a>malloc

Alloue des blocs de mémoire.

## <a name="syntax"></a>Syntaxe

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Octets à allouer.

## <a name="return-value"></a>Valeur renvoyée

**malloc** retourne un pointeur void vers l’espace alloué, ou **null** si la mémoire disponible est insuffisante. Pour retourner un pointeur vers un type autre que **`void`** , utilisez un cast de type sur la valeur de retour. L’espace de stockage désigné par la valeur de retour est obligatoirement correctement aligné pour le stockage de tout type d’objet dont la spécification d’alignement est inférieure ou égale à celle de l’alignement fondamental. (Dans Visual C++, l’alignement fondamental est l’alignement requis pour un **`double`** , ou 8 octets. Dans le code qui cible les plateformes 64 bits, il s’agit de 16 octets.) Utilisez [_aligned_malloc](aligned-malloc.md) pour allouer du stockage pour les objets qui ont une exigence d’alignement plus grande, par exemple, les types SSE [__m128](../../cpp/m128.md) et **`__m256`** , et les types qui sont déclarés à l’aide de `__declspec(align( n ))` où **n** est supérieur à 8. Si la *taille* est égale à 0, **malloc** alloue un élément de longueur zéro dans le tas et retourne un pointeur valide vers cet élément. Vérifiez toujours le retour de **malloc**, même si la quantité de mémoire demandée est faible.

## <a name="remarks"></a>Notes

La fonction **malloc** alloue un bloc de mémoire d’au moins octets de *taille* . Le bloc peut être supérieur à la *taille* en octets en raison de l’espace requis pour les informations d’alignement et de maintenance.

**malloc** affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour obtenir des informations sur ce code de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Le code de démarrage utilise **malloc** pour allouer le stockage pour les variables **_environ**, *envp*et *argv* . Les fonctions suivantes et leurs équivalents à caractères larges appellent également **malloc**.

:::row:::
   :::column span="":::
      [calloc](calloc.md)\
      [fonctions _exec](../../c-runtime-library/exec-wexec-functions.md)\
      [fgetc](fgetc-fgetwc.md)\
      [_fgetchar](fgetc-fgetwc.md)\
      [fgets](fgets-fgetws.md)\
      [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)\
      [fputc](fputc-fputwc.md)\
      [_fputchar](fputc-fputwc.md)\
      [fputs](fputs-fputws.md)\
      [fread](fread.md)
   :::column-end:::
   :::column span="":::
      [fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)\
      [fseek](fseek-fseeki64.md)\
      [fsetpos](fsetpos.md)\
      [_fullpath](fullpath-wfullpath.md)\
      [fwrite](fwrite.md)\
      [GETC](getc-getwc.md)\
      [GetChar](getc-getwc.md)\
      [_getcwd](getcwd-wgetcwd.md)\
      [_getdcwd](getcwd-wgetcwd.md)\
      [définit](../../c-runtime-library/gets-getws.md)
   :::column-end:::
   :::column span="":::
      [_getw](getw.md)\
      [_popen](popen-wpopen.md)\
      [printf](printf-printf-l-wprintf-wprintf-l.md)\
      [putc](putc-putwc.md)\
      [putchar](putc-putwc.md)\
      [_putenv](putenv-wputenv.md)\
      [tour](puts-putws.md)\
      [_putw](putw.md)\
      [scanf](scanf-scanf-l-wscanf-wscanf-l.md)
   :::column-end:::
   :::column span="":::
      [_searchenv](searchenv-wsearchenv.md)\
      [setvbuf](setvbuf.md)\
      [fonctions _spawn](../../c-runtime-library/spawn-wspawn-functions.md)\
      [_strdup](strdup-wcsdup-mbsdup.md)\
      [requise](system-wsystem.md)\
      [_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)\
      [ungetc](ungetc-ungetwc.md)\
      [vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)\
      [vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)
   :::column-end:::
:::row-end:::

La fonction C++ [_set_new_mode](set-new-mode.md) définit le mode de nouveau gestionnaire pour **malloc**. Le nouveau mode de gestionnaire indique si, en cas d’échec, **malloc** est appelé à appeler la routine de nouveau gestionnaire telle qu’elle est définie par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec d’allocation de mémoire. Vous pouvez remplacer ce comportement par défaut de sorte que, quand **malloc** ne parvient pas à allouer de la mémoire, **malloc** appelle la routine de nouveau gestionnaire de la même façon que l' **`new`** opérateur quand il échoue pour la même raison. Pour remplacer la valeur par défaut, appelez au `_set_new_mode(1)` début de votre programme ou liez-la à NEWMODE. OBJ (consultez [options de liaison](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version de débogage des bibliothèques Runtime C, **malloc** se résout en [_malloc_dbg](malloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** est marqué `__declspec(noalias)` et `__declspec(restrict)` ; cela signifie que la fonction est garantie de ne pas modifier les variables globales et que le pointeur retourné n’a pas d’alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**malloc**|\<stdlib.h> et \<malloc.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_malloc.c
// This program allocates memory with
// malloc, then frees the memory with free.

#include <stdlib.h>   // For _MAX_PATH definition
#include <stdio.h>
#include <malloc.h>

int main( void )
{
   char *string;

   // Allocate space for a path name
   string = malloc( _MAX_PATH );

   // In a C++ file, explicitly cast malloc's return.  For example,
   // string = (char *)malloc( _MAX_PATH );

   if( string == NULL )
      printf( "Insufficient memory available\n" );
   else
   {
      printf( "Memory space allocated for path name\n" );
      free( string );
      printf( "Memory freed\n" );
   }
}
```

```Output
Memory space allocated for path name
Memory freed
```

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Gratuit](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
