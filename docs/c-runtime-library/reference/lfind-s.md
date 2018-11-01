---
title: _lfind_s
ms.date: 11/04/2016
apiname:
- _lfind_s
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
ms.openlocfilehash: 08c04d9d1ca69998d54304c96468298013907179
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648437"
---
# <a name="lfinds"></a>_lfind_s

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

*Nombre*<br/>
Nombre d’éléments de tableau.

*size*<br/>
Taille des éléments de tableau en octets.

*compare*<br/>
Pointeur désignant la routine de comparaison. Le premier paramètre est le *contexte* pointeur. Le deuxième paramètre est un pointeur désignant la clé pour la recherche. Le troisième paramètre est un pointeur désignant l’élément de tableau à comparer à la clé.

*context*<br/>
Pointeur désignant un objet accessible dans la fonction de comparaison.

## <a name="return-value"></a>Valeur de retour

Si la clé est trouvée, **_lfind_s** retourne un pointeur vers l’élément du tableau à *base* qui correspond à *clé*. Si la clé est introuvable, **_lfind_s** retourne **NULL**.

Si des paramètres non valides sont passés à la fonction, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **NULL**.

### <a name="error-conditions"></a>Conditions d’erreur

|clé|de base|compare|num|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|zéro|**EINVAL**|
|any|any|**NULL**|an|any|**EINVAL**|

## <a name="remarks"></a>Notes

Le **_lfind_s** fonction effectue une recherche linéaire portant sur la valeur *clé* dans un tableau de *nombre* éléments, chacun des *largeur* octets. Contrairement aux **bsearch_s**, **_lfind_s** ne nécessite pas de tableau à trier. Le *base* argument est un pointeur vers la base du tableau à rechercher. Le *comparer* argument est un pointeur désignant une routine fournie par l’utilisateur qui compare deux éléments de tableau, puis retourne une valeur spécifiant leur relation. **_lfind_s** appelle le *comparer* routines une ou plusieurs fois pendant la recherche, passant la *contexte* pointeur et des pointeurs vers deux éléments de tableau à chaque appel. Le *comparer* routine doit comparer les éléments, puis retourner différente de zéro (ce qui signifie que les éléments sont différents) ou 0 (ce qui signifie que les éléments sont identiques).

**_lfind_s** est similaire à **_lfind** à l’exception de l’ajout de la *contexte* pointeur vers les arguments de la fonction de comparaison et de la liste des paramètres de la fonction. Le *contexte* pointeur peut être utile si la structure de données explorée fait partie d’un objet et le *comparer* fonction doit accéder aux membres de l’objet. Le *comparer* fonction peut effectuer un cast du pointeur void vers l’objet approprié type et accéder aux membres de cet objet. L’ajout de la *contexte* paramètre rend **_lfind_s** plus sécurisé car un contexte supplémentaire peut être utilisé pour éviter les bogues de réentrance associés à l’utilisation de variables statiques et pour rendre les données accessibles à la *comparer* (fonction).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
