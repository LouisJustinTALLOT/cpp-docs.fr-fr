---
title: bsearch_s
ms.date: 4/2/2020
api_name:
- bsearch_s
- _o_bsearch_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: 91b015eb9005a9b447cdd9d74a38d7169bd90a73
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913393"
---
# <a name="bsearch_s"></a>bsearch_s

Effectue une recherche binaire dans un tableau trié. Cette fonction est une version de [ensuite bsearch](bsearch.md) avec des améliorations de sécurité, comme décrit dans [fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*key*\
Pointeur vers la clé à rechercher.

*base*\
Pointeur vers la base des données de recherche.

*number*\
Nombre d'éléments.

*Largeur*\
Largeur des éléments.

*compar*\
Fonction de rappel qui compare deux éléments. Le premier argument est le pointeur de *contexte* . Le deuxième argument est un pointeur vers la *clé* de la recherche. Le troisième argument est un pointeur vers l’élément de tableau à comparer à la *clé*.

*contexte*\
Pointeur vers un objet accessible dans la fonction de comparaison.

## <a name="return-value"></a>Valeur retournée

**bsearch_s** retourne un pointeur vers une occurrence de la *clé* dans le tableau désigné par *base*. Si la *clé* est introuvable, la fonction retourne la **valeur null**. Si le tableau n’est pas trié par ordre croissant ou qu’il contient des enregistrements en double avec des clés identiques, le résultat est imprévisible.

Si des paramètres non valides sont passés à la fonction, elle appelle le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne la **valeur null**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d’erreur

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*compar*|*number*|*width*|**errno**|
|**NUL**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL**|
|n'importe laquelle|**NUL**|n'importe laquelle|!= 0|n'importe laquelle|**EINVAL**|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|= 0|**EINVAL**|
|n'importe laquelle|n'importe laquelle|**NUL**|an|n'importe laquelle|**EINVAL**|

## <a name="remarks"></a>Notes 

La fonction **bsearch_s** effectue une recherche binaire d’un tableau trié d’éléments Number, chacun d’un *nombre* d’octets de *largeur* . La valeur de *base* est un pointeur vers la base du tableau dans lequel effectuer la recherche, et *Key* est la valeur recherchée. Le paramètre de *comparaison* est un pointeur vers une routine fournie par l’utilisateur qui compare la clé demandée à un élément de tableau et retourne l’une des valeurs suivantes en spécifiant leur relation :

|Valeur retournée par la routine de *comparaison*|Description|
|-----------------------------------------|-----------------|
|\< 0|La clé est inférieure à l’élément de tableau.|
|0|La clé est égale à l’élément de tableau.|
|> 0|La clé est supérieure à l’élément de tableau.|

Le pointeur de *contexte* peut être utile si la structure de données recherchée fait partie d’un objet et que la fonction de comparaison doit accéder aux membres de l’objet. La fonction *compare* peut effectuer un cast du pointeur void vers le type d’objet approprié et accéder aux membres de cet objet. L’ajout du paramètre de *contexte* rend **bsearch_s** plus sécurisé, car un contexte supplémentaire peut être utilisé pour éviter les bogues de réentrance associés à l’utilisation de variables statiques pour rendre les données disponibles pour la fonction de *comparaison* .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> et \<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a> Exemple

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

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
