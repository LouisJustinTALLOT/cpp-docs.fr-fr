---
title: _lfind | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lfind
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
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lfind
- _lfind
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c3bfc7b6abe5f0d5902a02c88e7d5ba16cb24ab
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="lfind"></a>_lfind

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

*Nombre*<br/>
Nombre d’éléments de tableau.

*width*<br/>
Largeur des éléments du tableau.

*compare*<br/>
Pointeur désignant la routine de comparaison. Le premier paramètre est un pointeur désignant la clé pour la recherche. Le second paramètre est un pointeur désignant l’élément de tableau à comparer à la clé.

## <a name="return-value"></a>Valeur de retour

Si la clé est trouvée, **_lfind** retourne un pointeur vers l’élément du tableau à *base* qui correspond à *clé*. Si la clé est introuvable, **_lfind** retourne **NULL**.

## <a name="remarks"></a>Notes

Le **_lfind** fonction effectue une recherche linéaire pour la valeur *clé* dans un tableau de *nombre* éléments, chacun des *largeur* octets. Contrairement aux **bsearch**, **_lfind** ne nécessite pas de tableau à trier. Le *base* argument est un pointeur vers la base du tableau à rechercher. Le *comparer* argument est un pointeur vers une routine fournie par l’utilisateur qui compare deux éléments du tableau, puis retourne une valeur précisant leur relation. **_lfind** appelle la *comparer* routine une ou plusieurs fois lors de la recherche, le passage de pointeurs vers deux éléments de tableau à chaque appel. Le *comparer* routine doit comparer les éléments, puis revenez différente de zéro (ce qui signifie que les éléments sont différents), ou 0 (ce qui signifie que les éléments sont identiques).

Cette fonction valide ses paramètres. Si *comparer*, *clé* ou *nombre* est **NULL**, ou si *base* est **NULL**et *nombre* est différent de zéro, ou si *largeur* est inférieur à zéro, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **NULL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
