---
title: qsort | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- qsort
dev_langs:
- C++
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac444680a22a99f292b1728181103789435a150
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="qsort"></a>qsort

Effectue un tri rapide. Il existe une version plus sécurisée de cette fonction. Consultez [qsort_s](qsort-s.md).

## <a name="syntax"></a>Syntaxe

```C
void qsort(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>Paramètres

*base* début du tableau cible.

*nombre* taille en éléments de tableau.

*largeur* taille en octets de l’élément.

*comparer* pointeur vers une routine fournie par l’utilisateur qui compare deux éléments du tableau et retourne une valeur qui indique leur relation.

## <a name="remarks"></a>Notes

Le **qsort** fonction implémente un algorithme de tri rapide pour trier un tableau de *nombre* éléments, chacun des *largeur* octets. L’argument *base* est un pointeur vers la base du tableau à trier. **qsort** remplace ce tableau à l’aide des éléments triés.

**qsort** appelle la *comparer* routine plusieurs fois pendant le tri et transmet les pointeurs à deux éléments de tableau à chaque appel.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

La routine compare les éléments et retourner l’une des valeurs suivantes.

|Valeur de retour de la fonction compare|Description|
|-----------------------------------|-----------------|
|< 0|**elem1** moins **elem2**|
|0|**elem1** équivaut à **elem2**|
|> 0|**elem1** supérieur **elem2**|

Le tableau est trié par ordre croissant, comme défini par la fonction de comparaison. Pour trier un tableau par ordre décroissant, changez le sens de « supérieur à » et « inférieur à » dans la fonction de comparaison.

Cette fonction valide ses paramètres. Si *comparer* ou *nombre* est **NULL**, ou si *base* est **NULL** et **nombre* est différent de zéro, ou si *largeur* est inférieur à zéro, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne et **errno** a la valeur **EINVAL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**qsort**|\<stdlib.h> et \<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_qsort.c
// arguments: every good boy deserves favor

/* This program reads the command-line
* parameters and uses qsort to sort them. It
* then displays the sorted arguments.
*/

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main( int argc, char **argv )
{
   int i;
   /* Eliminate argv[0] from sort: */
   argv++;
   argc--;

   /* Sort remaining args using Quicksort algorithm: */
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );

   /* Output sorted list: */
   for( i = 0; i < argc; ++i )
      printf( " %s", argv[i] );
   printf( "\n" );
}

int compare( const void *arg1, const void *arg2 )
{
   /* Compare all of both strings: */
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );
}
```

```Output
boy deserves every favor good
```

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
