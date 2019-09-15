---
title: malloc
ms.date: 11/04/2016
api_name:
- malloc
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
ms.openlocfilehash: 8001726bcc2f1b384d527c6f4edcbf8eb92b0d2a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952828"
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

## <a name="return-value"></a>Valeur de retour

**malloc** retourne un pointeur void vers l’espace alloué, ou **null** si la mémoire disponible est insuffisante. Pour retourner un pointeur vers un type autre que **void**, utilisez un cast de type sur la valeur de retour. L’espace de stockage désigné par la valeur de retour est obligatoirement correctement aligné pour le stockage de tout type d’objet dont la spécification d’alignement est inférieure ou égale à celle de l’alignement fondamental. (En Visual C++, l’alignement fondamental est l’alignement requis pour un **double**, ou 8 octets. Dans un code qui cible les plateformes 64 bits, il s’agit de 16 octets.) Utilisez [_aligned_malloc](aligned-malloc.md) pour allouer du stockage pour les objets qui ont une exigence d’alignement plus grande, par exemple les types SSE [__m128](../../cpp/m128.md) et **__m256**, ainsi que les `__declspec(align( n ))` types déclarés à l’aide de où **n** est supérieur à 8. Si la *taille* est égale à 0, **malloc** alloue un élément de longueur zéro dans le tas et retourne un pointeur valide vers cet élément. Vérifiez toujours le retour de **malloc**, même si la quantité de mémoire demandée est faible.

## <a name="remarks"></a>Notes

La fonction **malloc** alloue un bloc de mémoire d’au moins octets de *taille* . Le bloc peut être supérieur à la *taille* en octets en raison de l’espace requis pour les informations d’alignement et de maintenance.

**malloc** affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Le code de démarrage utilise **malloc** pour allouer le stockage pour les variables **_environ**, *envp*et *argv* . Les fonctions suivantes et leurs équivalents à caractères larges appellent également **malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec, fonctions](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[system](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[gets](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

La fonction C++ [_set_new_mode](set-new-mode.md) définit le mode de nouveau gestionnaire pour **malloc**. Le nouveau mode de gestionnaire indique si, en cas d’échec, **malloc** est appelé la routine de nouveau gestionnaire telle qu’elle est définie par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec d’allocation de mémoire. Vous pouvez remplacer ce comportement par défaut de sorte que, lorsque **malloc** ne parvient pas à allouer de la mémoire, **malloc** appelle la routine de nouveau gestionnaire de la même façon que l’opérateur **New** lorsqu’il échoue pour la même raison. Pour remplacer la valeur par défaut, `_set_new_mode(1)` appelez au début de votre programme ou liez-la à NEWMODE. OBJ (consultez [options de liaison](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version de débogage des bibliothèques Runtime C, **malloc** se résout en _ [malloc_dbg](malloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** est marqué `__declspec(noalias)` et `__declspec(restrict)`; cela signifie que la fonction est garantie de ne pas modifier les variables globales et que le pointeur retourné n’a pas d’alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

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
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
