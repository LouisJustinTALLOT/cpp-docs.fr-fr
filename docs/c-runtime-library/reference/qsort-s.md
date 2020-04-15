---
title: qsort_s
ms.date: 4/2/2020
api_name:
- qsort_s
- _o_qsort_s
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
- qsort_s
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
ms.openlocfilehash: 6013098199e1b69d03dc9cf2780cbf4376abcc0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332972"
---
# <a name="qsort_s"></a>qsort_s

Effectue un tri rapide. Version de [qsort](qsort.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void qsort_s(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Paramètres

*base*<br/>
Début du tableau cible.

*nombre*<br/>
Taille du tableau dans les éléments.

*Largeur*<br/>
Taille d’élément en octets.

*Comparer*<br/>
Fonction de comparaison. Le premier argument est le pointeur de *contexte.* Le deuxième argument est un pointeur à la *clé* de la recherche. Le troisième argument est un pointeur à l’élément de tableau à comparer avec *la clé*.

*context*<br/>
Un pointeur vers un contexte, qui peut être n’importe quel objet que la routine *de comparaison* doit accéder.

## <a name="remarks"></a>Notes

La fonction **qsort_s** implémente un algorithme de tri rapide pour trier un tableau d’éléments de *nombre,* chacun des octets de *largeur.* La *base* d’argument est un pointeur à la base du tableau à trier. **qsort_s** surmene ce tableau avec les éléments triés. L’argument *comparer* est un pointeur à une routine fournie par l’utilisateur qui compare deux éléments de tableau et retourne une valeur spécifiant leur relation. **qsort_s** appelle la routine *de comparaison* une ou plusieurs fois au cours de la sorte, passant des pointeurs à deux éléments de tableau sur chaque appel:

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

La routine doit comparer les éléments et retourner l’une des valeurs suivantes :

|Valeur retournée|Description|
|------------------|-----------------|
|< 0|**elem1** moins **d’elem2**|
|0|**elem1** équivalent à **elem2**|
|> 0|**elem1** plus grand **qu’elem2**|

Le tableau est trié par ordre croissant, comme défini par la fonction de comparaison. Pour trier un tableau par ordre décroissant, changez le sens de « supérieur à » et « inférieur à » dans la fonction de comparaison.

Si des paramètres non valides sont passés à la fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, alors la fonction revient et **errno** est réglé à **EINVAL**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="error-conditions"></a>Conditions d'erreur

|key|base|compare|num|width|errno|
|---------|----------|-------------|---------|-----------|-----------|
|**Null**|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|
|n'importe laquelle|**Null**|n'importe laquelle|!= 0|n'importe laquelle|**EINVAL (EN)**|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|n'importe laquelle|<= 0|**EINVAL (EN)**|
|n'importe laquelle|n'importe laquelle|**Null**|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|

**qsort_s** a le même comportement que **qsort,** mais a le paramètre *de contexte* et définit **errno**. En passant un paramètre *de contexte,* les fonctions de comparaison peuvent utiliser un pointeur d’objet pour accéder à la fonctionnalité de l’objet ou à d’autres informations non accessibles via un pointeur d’élément. L’ajout du paramètre *contextuelle* rend **qsort_s** plus sûr parce que le *contexte* peut être utilisé pour éviter les bogues de réenterrabilité introduits en utilisant des variables statiques pour rendre les informations partagées disponibles à la fonction *de comparaison.*

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**qsort_s**|\<stdlib.h> et \<search.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliothèques :** toutes les versions des [fonctionnalités de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le paramètre *de contexte* dans la fonction **qsort_s.** Le paramètre *de contexte* facilite l’exécution de types de thread-safe. Au lieu d’utiliser des variables statiques qui doivent être synchronisées pour assurer la sécurité du thread, passez un paramètre *de contexte* différent dans chaque sorte. Dans cet exemple, un objet local est utilisé comme paramètre *de contexte.*

```cpp
// crt_qsort_s.cpp
// compile with: /EHsc /MT
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
// so \x00e1 is the German Sharp S in that codepage and \x00a4
// is the n tilde.

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.850"
#define SPANISH_LOCALE "Spanish_Spain.850"
#define ENGLISH_LOCALE "English_US.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S and \x001f for the n tilde.
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.1252"
#define SPANISH_LOCALE "Spanish_Spain.1252"
#define ENGLISH_LOCALE "English_US.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making sort_array vulnerable to thread
// conflicts.

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char s1[256];
    char s2[256];
    strcpy_s(s1, 256, *(char**)str1);
    strcpy_s(s2, 256, *(char**)str2);
    _strlwr_s( s1, sizeof(s1) );
    _strlwr_s( s2, sizeof(s2) );

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(s1,
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);

}

void sort_array(char *array[], int num, locale &loc)
{
    qsort_s(array, num, sizeof(char*), compare, &loc);
}

void print_array(char *a[], int c)
{
   for (int i = 0; i < c; i++)
      printf("%s ", a[i]);
   printf("\n");

}

void sort_german(void * Dummy)
{
   sort_array(array1, 6, locale(GERMAN_LOCALE));
}

void sort_spanish(void * Dummy)
{
   sort_array(array2, 3, locale(SPANISH_LOCALE));
}

void sort_english(void * Dummy)
{
   sort_array(array3, 3, locale(ENGLISH_LOCALE));
}

int main( )
{
   int i;
   HANDLE threads[3];

   printf("Unsorted input:\n");
   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);

   // Create several threads that perform sorts in different
   // languages at the same time.

   threads[0] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_german , 0, NULL));
   threads[1] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_spanish, 0, NULL));
   threads[2] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_english, 0, NULL));

   for (i = 0; i < 3; i++)
   {
      if (threads[i] == reinterpret_cast<HANDLE>(-1))
      {
         printf("Error creating threads.\n");
         exit(1);
      }
   }

   // Wait until all threads have terminated.
   WaitForMultipleObjects(3, threads, true, INFINITE);

   printf("Sorted output: \n");

   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);
}
```

### <a name="sample-output"></a>Exemple de sortie

```Output
Unsorted input:
weiß weis annehmen weizen Zeit weit
Español España espantado
table tableux tablet
Sorted output:
annehmen weiß weis weit weizen Zeit
España Español espantado
table tablet tableux
```

## <a name="see-also"></a>Voir aussi

[Recherche et tri](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
