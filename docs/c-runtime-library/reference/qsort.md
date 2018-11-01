---
title: qsort
ms.date: 11/04/2016
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
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: e912a7a53619e9347cf2c0cd40adf0f9162b314b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618489"
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

<br/>
Début du tableau cible.

*Nombre*<br/>
Taille du tableau dans les éléments.

*width*<br/>
Taille d’élément en octets.

*compare*<br/>
Pointeur désignant une routine fournie par l’utilisateur qui compare deux éléments de tableau et retourne une valeur qui spécifie leur relation.

## <a name="remarks"></a>Notes

Le **qsort** fonction implémente un algorithme de tri rapide pour trier un tableau de *nombre* éléments, chacun des *largeur* octets. L’argument *base* est un pointeur vers la base du tableau à trier. **qsort** remplace ce tableau en utilisant les éléments triés.

**qsort** appelle le *comparer* une routine ou plusieurs fois pendant le tri et transmet les pointeurs désignant deux éléments de tableau à chaque appel.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

La routine compare les éléments et retourner l’une des valeurs suivantes.

|Valeur de retour de la fonction compare|Description|
|-----------------------------------|-----------------|
|< 0|**elem1** inférieure à **elem2**|
|0|**elem1** équivalent à **elem2**|
|> 0|**elem1** supérieur **elem2**|

Le tableau est trié par ordre croissant, comme défini par la fonction de comparaison. Pour trier un tableau par ordre décroissant, changez le sens de « supérieur à » et « inférieur à » dans la fonction de comparaison.

Cette fonction valide ses paramètres. Si *comparer* ou *nombre* est **NULL**, ou si *base* est **NULL** et **nombre* est différent de zéro, ou si *largeur* est inférieur à zéro, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne et **errno** a la valeur **EINVAL**.

## <a name="requirements"></a>Configuration requise

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
