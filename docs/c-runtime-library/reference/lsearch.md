---
title: _lsearch
ms.date: 4/2/2020
api_name:
- _lsearch
- _o__lsearch
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
- _lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: a6ef3d86ffe8f03da34d4a374bddda1452815672
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341639"
---
# <a name="_lsearch"></a>_lsearch

Effectue une recherche linéaire portant sur une valeur ; l’ajoute en fin de liste si elle est introuvable. Une version plus sécurisée de cette fonction est disponible. Consultez [_lsearch_s](lsearch-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Objet à rechercher.

*base*<br/>
Pointeur désignant la base du tableau à explorer.

*nombre*<br/>
Nombre d'éléments.

*Largeur*<br/>
Largeur de chaque élément du tableau.

*Comparer*<br/>
Pointeur désignant la routine de comparaison. Le premier paramètre est un pointeur désignant la clé pour la recherche. Le second paramètre est un pointeur désignant un élément de tableau à comparer à la clé.

## <a name="return-value"></a>Valeur de retour

Si la clé est trouvée, **_lsearch** renvoie un pointeur à l’élément du tableau à la *base* qui correspond à *la clé*. Si la clé n’est pas trouvée, **_lsearch** renvoie un pointeur à l’élément nouvellement ajouté à la fin du tableau.

## <a name="remarks"></a>Notes

La fonction **_lsearch** effectue une recherche linéaire de la *clé* de valeur dans un tableau d’éléments de *nombre,* chacun des octets de *largeur.* Contrairement à **bsearch**, **_lsearch** n’exige pas que le tableau soit trié. Si *la clé* n’est pas trouvée, **_lsearch** l’ajoute à la fin du tableau et le *nombre*d’incréments .

*L’argument de comparaison* est un pointeur à une routine fournie par l’utilisateur qui compare deux éléments de tableau et retourne une valeur spécifiant leur relation. **_lsearch** appelle la routine *de comparaison* une ou plusieurs fois au cours de la recherche, passant des pointeurs à deux éléments de tableau sur chaque appel. *comparer* doit comparer les éléments et retourner soit nonzero (ce qui signifie que les éléments sont différents) ou 0 (ce qui signifie que les éléments sont identiques).

Cette fonction valide ses paramètres. Si *comparer*, *clé* ou *numéro* est **NULL**, ou si *la base* est **NULL** et *le nombre* est nonzero, ou si la *largeur* est inférieure à zéro, le gestionnaire de paramètre invalide est invoqué, comme décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction renvoie **NULL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_lsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main(void)
{
   char * wordlist[4] = { "hello", "thanks", "bye" };
                            // leave room to grow...
   int n = 3;
   char **result;
   char *key = "extra";
   int i;

   printf( "wordlist before _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );

   result = (char **)_lsearch( &key, wordlist,
                      &n, sizeof(char *), compare );

   printf( "wordlist after _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );
}

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}
```

```Output
wordlist before _lsearch: hello thanks bye
wordlist after _lsearch: hello thanks bye extra
```

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
