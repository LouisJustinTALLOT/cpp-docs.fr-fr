---
title: _lsearch
ms.date: 11/04/2016
api_name:
- _lsearch
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
ms.openlocfilehash: 6dc610c4ab120d81bfb2b3b5e64a54a104bea97f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438148"
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

*number*<br/>
Nombre d'éléments.

*width*<br/>
Largeur de chaque élément du tableau.

*compare*<br/>
Pointeur désignant la routine de comparaison. Le premier paramètre est un pointeur désignant la clé pour la recherche. Le second paramètre est un pointeur désignant un élément de tableau à comparer à la clé.

## <a name="return-value"></a>Valeur de retour

Si la clé est trouvée, **_lsearch** retourne un pointeur vers l’élément du tableau au niveau de *base* qui correspond à la *clé*. Si la clé est introuvable, **_lsearch** retourne un pointeur vers l’élément qui vient d’être ajouté à la fin du tableau.

## <a name="remarks"></a>Notes

La fonction **_lsearch** effectue une recherche linéaire sur la *clé* de valeur dans un tableau d’éléments *Number* , chacun d’octets de *largeur* . Contrairement à **ensuite bsearch**, **_lsearch** ne nécessite pas le tri du tableau. Si la *clé* est introuvable, **_lsearch** l’ajoute à la fin du tableau et incrémente le *nombre*.

L’argument de *comparaison* est un pointeur vers une routine fournie par l’utilisateur qui compare deux éléments de tableau et retourne une valeur spécifiant leur relation. **_lsearch** appelle la routine de *comparaison* une ou plusieurs fois pendant la recherche, en passant des pointeurs à deux éléments de tableau à chaque appel. *compare* doit comparer les éléments et retourner une valeur différente de zéro (ce qui signifie que les éléments sont différents) ou 0 (ce qui signifie que les éléments sont identiques).

Cette fonction valide ses paramètres. Si *compare*, *Key* ou *Number* a la **valeur null**, ou si *base* a la **valeur null** et que le *nombre* est différent de zéro, ou si *Width* est inférieur à zéro, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Pour plus d’informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
