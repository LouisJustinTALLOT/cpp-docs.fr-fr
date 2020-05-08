---
title: _lfind_s
ms.date: 4/2/2020
api_name:
- _lfind_s
- _o__lfind_s
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
- lfind_s
- _lfind_s
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 589a413c9f1fb49fbfe8cd1b5eacb9d452716523
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916512"
---
# <a name="_lfind_s"></a>_lfind_s

Effectue une recherche linéaire portant sur la clé spécifiée. Version de [_lfind](lfind.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lfind_s(
   const void *key,
   const void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Objet à rechercher.

*base*<br/>
Pointeur désignant la base de données de recherche.

*number*<br/>
Nombre d’éléments de tableau.

*size*<br/>
Taille des éléments de tableau en octets.

*compar*<br/>
Pointeur désignant la routine de comparaison. Le premier paramètre est le pointeur de *contexte* . Le deuxième paramètre est un pointeur désignant la clé pour la recherche. Le troisième paramètre est un pointeur désignant l’élément de tableau à comparer à la clé.

*context*<br/>
Pointeur désignant un objet accessible dans la fonction de comparaison.

## <a name="return-value"></a>Valeur de retour

Si la clé est trouvée, **_lfind_s** retourne un pointeur vers l’élément du tableau au niveau de *base* qui correspond à la *clé*. Si la clé est introuvable, **_lfind_s** retourne la **valeur null**.

Si des paramètres non valides sont passés à la fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**.

### <a name="error-conditions"></a>Conditions d'erreur

|key|base|compare|num|taille|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NUL**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL**|
|n'importe laquelle|**NUL**|n'importe laquelle|!= 0|n'importe laquelle|**EINVAL**|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|zéro|**EINVAL**|
|n'importe laquelle|n'importe laquelle|**NUL**|an|n'importe laquelle|**EINVAL**|

## <a name="remarks"></a>Notes 

La fonction **_lfind_s** effectue une recherche linéaire sur la *clé* de valeur dans un tableau d’éléments *Number* , chacun d’octets de *largeur* . Contrairement à **bsearch_s**, **_lfind_s** ne nécessite pas le tri du tableau. L’argument de *base* est un pointeur vers la base du tableau dans lequel effectuer la recherche. L’argument de *comparaison* est un pointeur vers une routine fournie par l’utilisateur qui compare deux éléments de tableau, puis retourne une valeur spécifiant leur relation. **_lfind_s** appelle la routine de *comparaison* une ou plusieurs fois pendant la recherche, en passant le pointeur de *contexte* et les pointeurs à deux éléments de tableau à chaque appel. La routine de *comparaison* doit comparer les éléments, puis retourner une valeur différente de zéro (ce qui signifie que les éléments sont différents) ou 0 (ce qui signifie que les éléments sont identiques).

**_lfind_s** est semblable à **_lfind** à l’exception de l’ajout du pointeur de *contexte* aux arguments de la fonction de comparaison et de la liste de paramètres de la fonction. Le pointeur de *contexte* peut être utile si la structure de données recherchée fait partie d’un objet et que la fonction de *comparaison* doit accéder aux membres de l’objet. La fonction *compare* peut effectuer un cast du pointeur void vers le type d’objet approprié et accéder aux membres de cet objet. L’ajout du paramètre de *contexte* rend **_lfind_s** plus sécurisé, car un contexte supplémentaire peut être utilisé pour éviter les bogues de réentrance associés à l’utilisation de variables statiques pour rendre les données disponibles pour la fonction de *comparaison* .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```cpp
// crt_lfind_s.cpp
// This program uses _lfind_s to search a string array,
// passing a locale as the context.
// compile with: /EHsc
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
// Codepage 850 is the OEM codepage used by the command line,
// so \x00e1 is the German Sharp S

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char *s1 = *(char**)str1;
    char *s2 = *(char**)str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

void find_it( char *key, char *array[], unsigned int num, locale &loc )
{
   char **result = (char **)_lfind_s( &key, array,
                      &num, sizeof(char *), compare, &loc );
   if( result )
      printf( "%s found\n", *result );
   else
      printf( "%s not found\n", key );
}

int main( )
{
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );
}
```

```Output
weit found
```

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
