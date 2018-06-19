---
title: bsearch_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- bsearch_s
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
- bsearch_s
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2600b77031967bec5d5dd549a7dd8f34fc5c5e3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400614"
---
# <a name="bsearchs"></a>bsearch_s

Effectue une recherche binaire dans un tableau trié. Il s’agit d’une version de [bsearch](bsearch.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Objet à rechercher.

*base*<br/>
Pointeur vers la base de données de recherche.

*Nombre*<br/>
Nombre d'éléments.

*width*<br/>
Largeur des éléments.

*compare*<br/>
Fonction de rappel qui compare deux éléments. Le premier argument est le *contexte* pointeur. Le deuxième argument est un pointeur vers le *clé* pour la recherche. Le troisième argument est un pointeur vers l’élément de tableau à comparer avec *clé*.

*Contexte*<br/>
Pointeur vers un objet accessible dans la fonction de comparaison.

## <a name="return-value"></a>Valeur de retour

**bsearch_s** retourne un pointeur vers une occurrence de *clé* dans le tableau vers lequel pointé *base*. Si *clé* n’est trouvé, la fonction retourne **NULL**. Si le tableau n’est pas trié par ordre croissant ou qu’il contient des enregistrements en double avec des clés identiques, le résultat est imprévisible.

Si des paramètres non valides sont passés à la fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Parameter Validation](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **NULL**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d’erreur

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*compare*|*Nombre*|*width*|**errno**|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|= 0|**EINVAL**|
|any|any|**NULL**|an|any|**EINVAL**|

## <a name="remarks"></a>Notes

Le **bsearch_s** fonction effectue une recherche binaire dans un tableau trié de *nombre* éléments, chacun des *largeur* taille en octets. Le *base* valeur est un pointeur vers la base du tableau à rechercher, et *clé* est la valeur recherchée. Le *comparer* paramètre est un pointeur vers une routine fournie par l’utilisateur qui compare la clé demandée à un élément de tableau et retourne l’une des valeurs suivantes précisant leur relation :

|Valeur retournée par *comparer* routine|Description|
|-----------------------------------------|-----------------|
|\< 0|La clé est inférieure à l’élément de tableau.|
|0|La clé est égale à l’élément de tableau.|
|> 0|La clé est supérieure à l’élément de tableau.|

Le *contexte* pointeur peut être utile si la structure de données de recherche fait partie d’un objet, et la fonction de comparaison doit accéder aux membres de l’objet. Le *comparer* fonction peut effectuer un cast du pointeur void dans les membres de type et l’accès de l’objet approprié de cet objet. L’ajout de la *contexte* paramètre rend **bsearch_s** plus sécurisé, car un contexte supplémentaire permet d’éviter les bogues de réentrance associés à l’utilisation de variables statiques pour ces données à la *comparer* (fonction).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> et \<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme trie un tableau de chaînes avec [qsort_s](qsort-s.md) et utilise ensuite bsearch_s pour rechercher le mot « cat ».

```cpp
// crt_bsearch_s.cpp
// This program uses bsearch_s to search a string array,
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
#define ENGLISH_LOCALE "English_US.850"
#endif

#ifdef CODEPAGE_1252
#define ENGLISH_LOCALE "English_US.1252"
#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, char **str1, char **str2)
{
    char *s1 = *str1;
    char *s2 = *str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};

   char *key = "cat";
   char **result;
   int i;

   /* Sort using Quicksort algorithm: */
   qsort_s( arr,
            sizeof(arr)/sizeof(arr[0]),
            sizeof( char * ),
            (int (*)(void*, const void*, const void*))compare,
            &locale(ENGLISH_LOCALE) );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch_s( &key,
                                arr,
                                sizeof(arr)/sizeof(arr[0]),
                                sizeof( char * ),
                                (int (*)(void*, const void*, const void*))compare,
                                &locale(ENGLISH_LOCALE) );
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

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
