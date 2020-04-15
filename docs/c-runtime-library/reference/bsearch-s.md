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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ef8a68f0db45e718af6b17fe0d08c33a6fd61d6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333849"
---
# <a name="bsearch_s"></a>bsearch_s

Effectue une recherche binaire dans un tableau trié. Cette fonction est une version de [bsearch](bsearch.md) avec des améliorations de sécurité comme décrit dans [les fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Clé*\
Pointeur vers la clé à rechercher.

*Base*\
Pointeur vers la base des données de recherche.

*Nombre*\
Nombre d'éléments.

*Largeur*\
Largeur des éléments.

*Comparer*\
Fonction de rappel qui compare deux éléments. Le premier argument est le pointeur de *contexte.* Le deuxième argument est un pointeur à la *clé* de la recherche. Le troisième argument est un pointeur à l’élément de tableau à comparer avec *la clé*.

*Contexte*\
Pointeur vers un objet accessible dans la fonction de comparaison.

## <a name="return-value"></a>Valeur retournée

**bsearch_s** renvoie un pointeur à un événement de *la clé* dans le tableau pointé par *la base*. Si *la clé* n’est pas trouvée, la fonction renvoie **NULL**. Si le tableau n’est pas trié par ordre croissant ou qu’il contient des enregistrements en double avec des clés identiques, le résultat est imprévisible.

Si des paramètres non valides sont transmis à la fonction, il invoque le gestionnaire de paramètres invalide tel que décrit dans [la validation des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction renvoie **NULL**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Conditions d’erreur

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*Comparer*|*nombre*|*Largeur*|**errno**|
|**Null**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|
|n'importe laquelle|**Null**|n'importe laquelle|!= 0|n'importe laquelle|**EINVAL (EN)**|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|= 0|**EINVAL (EN)**|
|n'importe laquelle|n'importe laquelle|**Null**|an|n'importe laquelle|**EINVAL (EN)**|

## <a name="remarks"></a>Notes

La fonction **bsearch_s** effectue une recherche binaire d’un tableau trié d’éléments de *nombre,* chacun des octets de *largeur* dans la taille. La valeur *de base* est un pointeur à la base du tableau à rechercher, et la *clé* est la valeur recherchée. Le paramètre *de comparaison* est un pointeur à une routine fournie par l’utilisateur qui compare la clé demandée à un élément de tableau et renvoie l’une des valeurs suivantes spécifiant leur relation :

|Valeur retournée par la routine *de comparaison*|Description|
|-----------------------------------------|-----------------|
|\< 0|La clé est inférieure à l’élément de tableau.|
|0|La clé est égale à l’élément de tableau.|
|> 0|La clé est supérieure à l’élément de tableau.|

Le pointeur *de contexte* peut être utile si la structure de données recherchée fait partie d’un objet, et la fonction de comparaison doit accéder aux membres de l’objet. La fonction *de comparaison* peut jeter le pointeur vide dans le type d’objet approprié et accéder aux membres de cet objet. L’ajout du paramètre *contextuelle* rend **bsearch_s** plus sûr puisque le contexte supplémentaire peut être utilisé pour éviter les bogues de réenterrabilité associés à l’utilisation de variables statiques pour rendre les données disponibles à la fonction *de comparaison.*

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
