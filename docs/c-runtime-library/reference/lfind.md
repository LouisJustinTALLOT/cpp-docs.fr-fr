---
description: 'En savoir plus sur : _lfind'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 50a3464f375e1f21f8afa2e57e76e910147ef3a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250359"
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

*number*<br/>
Nombre d’éléments de tableau.

*width*<br/>
Largeur des éléments du tableau.

*compar*<br/>
Pointeur désignant la routine de comparaison. Le premier paramètre est un pointeur désignant la clé pour la recherche. Le second paramètre est un pointeur désignant l’élément de tableau à comparer à la clé.

## <a name="return-value"></a>Valeur renvoyée

Si la clé est trouvée, **_lfind** retourne un pointeur vers l’élément du tableau au niveau de *base* qui correspond à la *clé*. Si la clé est introuvable, **_lfind** retourne la **valeur null**.

## <a name="remarks"></a>Notes

La fonction **_lfind** effectue une recherche linéaire sur la *clé* de valeur dans un tableau d’éléments *Number* , chacun d’octets de *largeur* . Contrairement à **ensuite bsearch**, **_lfind** ne nécessite pas le tri du tableau. L’argument de *base* est un pointeur vers la base du tableau dans lequel effectuer la recherche. L’argument de *comparaison* est un pointeur vers une routine fournie par l’utilisateur qui compare deux éléments de tableau, puis retourne une valeur spécifiant leur relation. **_lfind** appelle la routine de *comparaison* une ou plusieurs fois pendant la recherche, en passant des pointeurs à deux éléments de tableau à chaque appel. La routine de *comparaison* doit comparer les éléments, puis retourner une valeur différente de zéro (ce qui signifie que les éléments sont différents) ou 0 (ce qui signifie que les éléments sont identiques).

Cette fonction valide ses paramètres. Si *compare*, *Key* ou *Number* a la **valeur null**, ou si *base* a la **valeur null** et que le *nombre* est différent de zéro, ou si *Width* est inférieur à zéro, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
