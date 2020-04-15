---
title: _lfind
ms.date: 4/2/2020
api_name:
- _lfind
- _o__lfind
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 287cbd8bc9cc567a4a0d5b9505d57098197bc545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342178"
---
# <a name="_lfind"></a>_lfind

Effectue une recherche linéaire portant sur la clé spécifiée. Une version plus sécurisée de cette fonction est disponible. Consultez [_lfind_s](lfind-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Objet à rechercher.

*base*<br/>
Pointeur désignant la base de données de recherche.

*nombre*<br/>
Nombre d’éléments de tableau.

*Largeur*<br/>
Largeur des éléments du tableau.

*Comparer*<br/>
Pointeur désignant la routine de comparaison. Le premier paramètre est un pointeur désignant la clé pour la recherche. Le second paramètre est un pointeur désignant l’élément de tableau à comparer à la clé.

## <a name="return-value"></a>Valeur de retour

Si la clé est trouvée, **_lfind** renvoie un pointeur à l’élément du tableau à la *base* qui correspond à *la clé*. Si la clé n’est pas trouvée, **_lfind** renvoie **NULL**.

## <a name="remarks"></a>Notes

La fonction **_lfind** effectue une recherche linéaire de la *clé* de valeur dans un tableau d’éléments de *nombre,* chacun des octets de *largeur.* Contrairement à **bsearch**, **_lfind** n’exige pas que le tableau soit trié. *L’argument de base* est un pointeur à la base du tableau à rechercher. *L’argument de comparaison* est un pointeur à une routine fournie par l’utilisateur qui compare deux éléments de tableau, puis retourne une valeur spécifiant leur relation. **_lfind** appelle la routine *de comparaison* une ou plusieurs fois au cours de la recherche, passant des pointeurs à deux éléments de tableau sur chaque appel. La routine *de comparaison* doit comparer les éléments, puis retourner nonzero (ce qui signifie que les éléments sont différents) ou 0 (ce qui signifie que les éléments sont identiques).

Cette fonction valide ses paramètres. Si *comparer*, *clé* ou *numéro* est **NULL**, ou si *la base* est **NULL** et *le nombre* est nonzero, ou si la *largeur* est inférieure à zéro, le gestionnaire de paramètre invalide est invoqué, comme décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction renvoie **NULL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
