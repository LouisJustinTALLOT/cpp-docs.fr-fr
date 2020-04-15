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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: afe9264351110bc062d6168ef803fa6fb796538a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341576"
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

*Taille*<br/>
Octets à allouer.

## <a name="return-value"></a>Valeur de retour

**malloc** renvoie un pointeur vide à l’espace alloué, ou **NULL** s’il n’y a pas suffisamment de mémoire disponible. Pour retourner un pointeur à un type autre que **le vide,** utilisez un type de distribution sur la valeur de retour. L’espace de stockage désigné par la valeur de retour est obligatoirement correctement aligné pour le stockage de tout type d’objet dont la spécification d’alignement est inférieure ou égale à celle de l’alignement fondamental. (Dans Visual C, l’alignement fondamental est l’alignement requis pour un **double,** ou 8 octets. Dans le code qui cible les plates-formes 64 bits, c’est 16 octets.) Utilisez [_aligned_malloc](aligned-malloc.md) pour allouer le stockage pour les objets qui ont une exigence d’alignement plus grande, par exemple, les types SSE [__m128](../../cpp/m128.md) et **__m256,** et les types qui sont déclarés en utilisant `__declspec(align( n ))` où **n** est supérieur à 8. Si *la taille* est de 0, **malloc** alloue un élément de longueur zéro dans le tas et renvoie un pointeur valide à cet élément. Vérifiez toujours le retour de **malloc**, même si la quantité de mémoire demandée est faible.

## <a name="remarks"></a>Notes

La fonction **malloc** alloue un bloc de mémoire d’au moins les octets de *taille.* Le bloc peut être plus grand que les octets de *taille* en raison de l’espace nécessaire pour l’alignement et l’information de maintenance.

**malloc** définit **errno** à **ENOMEM** si une allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour obtenir des informations sur ce code de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Le code de démarrage utilise **malloc** pour allouer le stockage pour les **variables _environ**, *envp*, et *argv.* Les fonctions suivantes et leurs homologues à caractère large appellent également **malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec, fonctions](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[fonctions _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[système](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[Getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[obtient](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

La fonction C++ [_set_new_mode](set-new-mode.md) définit le mode de nouveau gestionnaire pour **malloc**. Le nouveau mode de manutention indique si, en cas de défaillance, **malloc** est d’appeler la nouvelle routine de gestionnaire tel que défini par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la nouvelle routine de gestionnaire sur l’omission d’allouer la mémoire. Vous pouvez passer outre à ce comportement par défaut de sorte que, lorsque **malloc** ne parvient pas à allouer la mémoire, **malloc** appelle la nouvelle routine de gestionnaire de la même manière que le **nouvel** opérateur fait quand il échoue pour la même raison. Pour remplacer la valeur `_set_new_mode(1)` par défaut, appelez tôt dans votre programme ou établiez un lien avec NEWMODE. OBJ (voir [Options de lien](../../c-runtime-library/link-options.md)).

Lorsque l’application est liée à une version débogéque des bibliothèques C run-time, **malloc** se résout à [_malloc_dbg](malloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** est `__declspec(noalias)` `__declspec(restrict)`marqué et; cela signifie que la fonction est garantie de ne pas modifier les variables globales, et que le pointeur retourné n’est pas alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

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
