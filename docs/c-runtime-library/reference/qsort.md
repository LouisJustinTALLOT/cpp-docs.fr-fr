---
title: qsort
description: Décrit l’API de tri rapide Microsoft C Runtime `qsort`
ms.date: 10/23/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c658ffae69cd662809eb4dac09c06b6a13f4e051
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639118"
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

*`base`*\
Début du tableau cible.

*`number`*\
Taille du tableau dans les éléments.

*`width`*\
Taille d’élément en octets.

*`compare`*\
Pointeur désignant une routine fournie par l’utilisateur qui compare deux éléments de tableau et retourne une valeur qui spécifie leur relation.

## <a name="remarks"></a>Notes

La **`qsort`** fonction implémente un algorithme de tri rapide pour trier un tableau d' *`number`* éléments, chacun de ces *`width`* octets. L’argument *`base`* est un pointeur vers la base du tableau à trier. **`qsort`** remplace ce tableau à l’aide des éléments triés.

**`qsort`** appelle la *`compare`* routine une ou plusieurs fois pendant le tri, et passe des pointeurs à deux éléments de tableau à chaque appel. Si *`compare`* indique que deux éléments sont identiques, leur ordre dans le tableau trié résultant n’est pas spécifié.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

La routine compare les éléments et retourner l’une des valeurs suivantes.

|Valeur de retour de la fonction compare|Description|
|-----------------------------------|-----------------|
|< 0|**`elem1`** inférieur à **`elem2`**|
|0|**`elem1`** équivalent à **`elem2`**|
|> 0|**`elem1`** supérieur à **`elem2`**|

Le tableau est trié par ordre croissant, comme défini par la fonction de comparaison. Pour trier un tableau par ordre décroissant, changez le sens de « supérieur à » et « inférieur à » dans la fonction de comparaison.

Cette fonction valide ses paramètres. Si *`compare`* ou *`number`* a la valeur **`NULL`** , ou si a la valeur et que est différent de *`base`* **`NULL`** *`number`* zéro, ou si *`width`* est inférieur à zéro, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne et **`errno`** prend la valeur **`EINVAL`** .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**`qsort`**|\<stdlib.h> et \<search.h>|

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

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)\
[`bsearch`](bsearch.md)\
[`_lsearch`](lsearch.md)
