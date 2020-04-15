---
title: qsort
ms.date: 4/2/2020
api_name:
- qsort
- _o_qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: 09de57e206eb6fd4a75a0a9444332136aeee0e9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338245"
---
# <a name="qsort"></a>qsort

Effectue un tri rapide. Il existe une version plus sécurisée de cette fonction. Consultez [qsort_s](qsort-s.md).

## <a name="syntax"></a>Syntaxe

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>Paramètres

*base*<br/>
Début du tableau cible.

*nombre*<br/>
Taille du tableau dans les éléments.

*Largeur*<br/>
Taille d’élément en octets.

*Comparer*<br/>
Pointeur désignant une routine fournie par l’utilisateur qui compare deux éléments de tableau et retourne une valeur qui spécifie leur relation.

## <a name="remarks"></a>Notes

La fonction **qsort** implémente un algorithme de tri rapide pour trier un tableau d’éléments de *nombre,* chacun des octets de *largeur.* La *base* d’argument est un pointeur à la base du tableau à trier. **qsort** surmene ce tableau en utilisant les éléments triés.

**qsort** appelle la routine *de comparaison* une ou plusieurs fois au cours de la sorte, et passe des pointeurs à deux éléments de tableau sur chaque appel.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

La routine compare les éléments et retourner l’une des valeurs suivantes.

|Valeur de retour de la fonction compare|Description|
|-----------------------------------|-----------------|
|< 0|**elem1** moins **d’elem2**|
|0|**elem1** équivalent à **elem2**|
|> 0|**elem1** plus grand **qu’elem2**|

Le tableau est trié par ordre croissant, comme défini par la fonction de comparaison. Pour trier un tableau par ordre décroissant, changez le sens de « supérieur à » et « inférieur à » dans la fonction de comparaison.

Cette fonction valide ses paramètres. Si *la comparaison* ou le *nombre* est **NULL**, ou si *la base* est **NULL** et *le nombre* est nonzero, ou si la *largeur* est inférieure à zéro, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction revient et **errno** est réglé à **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
