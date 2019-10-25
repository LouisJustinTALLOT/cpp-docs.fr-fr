---
title: bsearch
ms.date: 10/22/2019
api_name:
- bsearch
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: 6b476cbdd5e9c072cae03ad1091a96e2d0b7422b
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811090"
---
# <a name="bsearch"></a>bsearch

Effectue une recherche binaire dans un tableau trié. Une version plus sécurisée de cette fonction est disponible. Consultez [bsearch_s](bsearch-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>Paramètres

\ de *clé*
Pointeur vers la clé à rechercher.

*base*\
Pointeur vers la base des données de recherche.

*nombre*\
Nombre d'éléments.

*largeur*\
Largeur des éléments.

*comparer*\
Fonction de rappel qui compare deux éléments. Le premier est un pointeur vers la clé de la recherche, tandis que le second est un pointeur vers l’élément de tableau à comparer à la clé.

## <a name="return-value"></a>Valeur de retour

**ensuite bsearch** retourne un pointeur vers une occurrence de la *clé* dans le tableau désigné par *base*. Si la *clé* est introuvable, la fonction retourne la **valeur null**. Si le tableau n’est pas trié par ordre croissant ou qu’il contient des enregistrements en double avec des clés identiques, le résultat est imprévisible.

## <a name="remarks"></a>Notes

La fonction **ensuite bsearch** effectue une recherche binaire d’un tableau trié d’éléments Number, chacun d’un *nombre* d’octets de *largeur* . La valeur de *base* est un pointeur vers la base du tableau dans lequel effectuer la recherche, et *Key* est la valeur recherchée. Le paramètre de *comparaison* est un pointeur vers une routine fournie par l’utilisateur qui compare la clé demandée à un élément de tableau. Elle retourne l’une des valeurs suivantes qui spécifient leur relation :

|Valeur retournée par la routine de *comparaison*|Description|
|-----------------------------------------|-----------------|
|\< 0|La clé est inférieure à l’élément de tableau.|
|0|La clé est égale à l’élément de tableau.|
|> 0|La clé est supérieure à l’élément de tableau.|

Cette fonction valide ses paramètres. Si *compare*, *Key* ou *Number* a la **valeur null**, ou si *base* a la **valeur null** et que le *nombre* est différent de zéro, ou si *Width* est égal à zéro, la fonction appelle le gestionnaire de paramètre non valide, comme décrit dans le [paramètre Validation](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur `EINVAL` et la fonction retourne la **valeur null**.

## <a name="requirements"></a>spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> et \<search.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme trie un tableau de chaînes avec qsort et utilise ensuite bsearch pour rechercher le mot « cat ».

```C
// crt_bsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( char **arg1, char **arg2 )
{
   /* Compare all of both strings: */
   return _strcmpi( *arg1, *arg2 );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};
   char **result;
   char *key = "cat";
   int i;

   /* Sort using Quicksort algorithm: */
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const
   void*, const void*))compare );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),
                              sizeof( char * ), (int (*)(const void*, const void*))compare );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
