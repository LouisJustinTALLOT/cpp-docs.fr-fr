---
title: bsearch
ms.date: 4/2/2020
api_name:
- bsearch
- _o_bsearch
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: efad391eb2512cfa59cc3597430a84727676f27e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333802"
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

*Clé*\
Pointeur vers la clé à rechercher.

*Base*\
Pointeur vers la base des données de recherche.

*Nombre*\
Nombre d'éléments.

*Largeur*\
Largeur des éléments.

*Comparer*\
Fonction de rappel qui compare deux éléments. Le premier est un pointeur à la clé pour la recherche, et le second est un pointeur à l’élément de tableau à comparer avec la clé.

## <a name="return-value"></a>Valeur retournée

**bsearch renvoie** un pointeur à un événement de *la clé* dans le tableau pointé par *la base*. Si *la clé* n’est pas trouvée, la fonction renvoie **NULL**. Si le tableau n’est pas trié par ordre croissant ou qu’il contient des enregistrements en double avec des clés identiques, le résultat est imprévisible.

## <a name="remarks"></a>Notes

La fonction **de bsearch** effectue une recherche binaire d’un tableau trié d’éléments de *nombre,* chacun des octets de *largeur* dans la taille. La valeur *de base* est un pointeur à la base du tableau à rechercher, et la *clé* est la valeur recherchée. Le paramètre *de comparaison* est un pointeur à une routine fournie par l’utilisateur qui compare la clé demandée à un élément de tableau. Il renvoie l’une des valeurs suivantes qui spécifient leur relation :

|Valeur retournée par la routine *de comparaison*|Description|
|-----------------------------------------|-----------------|
|\< 0|La clé est inférieure à l’élément de tableau.|
|0|La clé est égale à l’élément de tableau.|
|> 0|La clé est supérieure à l’élément de tableau.|

Cette fonction valide ses paramètres. Si *comparer*, *clé* ou *numéro* est **NULL**, ou si *la base* est **NULL** et *le nombre* est nonzero, ou si la *largeur* est nulle, la fonction invoque le gestionnaire de paramètres invalides, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à `EINVAL` se poursuivre, **errno** est réglé et la fonction retourne **NULL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> et \<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
