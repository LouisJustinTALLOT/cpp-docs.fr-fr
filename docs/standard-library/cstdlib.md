---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 298d6a512b2863a326bda0670f33fe8f1bda0688
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449410"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Inclut l’en-tête \<stdlib. > h de la bibliothèque standard C et ajoute les noms associés à l' `std` espace de noms. L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l' `std` en-tête de la bibliothèque standard C sont déclarés dans l’espace de noms.

> [!NOTE]
> \<stdlib. h > n’inclut pas le type **wchar_t**.

## <a name="requirements"></a>Configuration requise

**En-tête**: \<cstdlib >

**Espace de noms :** std

## <a name="namespace-and-macros"></a>Espace de noms et macros

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>Exposition uniquement les fonctions

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Fonctions de démarrage et d’arrêt

|Fonction|Description|
|-|-|
|[_Exit](#_exit)|Termine le programme sans utiliser de destructeurs ou de fonctions inscrites.|
|[abort](#abort)|Termine le programme sans utiliser de destructeurs.|
|[atexit](#atexit)|Inscrit la fonction pour l’arrêt du programme.|
|[exit](#exit)|Détruit les objets avec le stockage statique et le thread, puis retourne le contrôle.|
|[at_quick_exit](#at_quick_exit)|Inscrit la fonction sans arguments pour l’arrêt du programme.|
|[quick_exit](#quick_exit)|Inscrit la fonction avec des objets conservés pour l’arrêt du programme.|
|[getenv](#getenv)|Consultez Référence de la bibliothèque standard C.|
|[system](#system)|Consultez Référence de la bibliothèque standard C.|

### <a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Notes

Le programme est arrêté sans exécuter de destructeurs pour les objets de durée de stockage automatique, de thread ou statique et sans appel de fonctions `atexit()`passé à. La fonction `_Exit` est signal-safe.

### <a name="abort"></a>arrêté

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Notes

Le programme est arrêté sans exécuter de destructeurs pour les objets de durée de stockage automatique, de thread ou statique et sans appel de fonctions `atexit()`passé à. La fonction `abort` est signal-safe.

### <a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Valeur de retour

Zéro si l’inscription réussit, valeur différente de zéro en cas d’échec.

#### <a name="remarks"></a>Notes

Les `at_quick_exit()` fonctions inscrivent la fonction vers laquelle *pointe doit être* appelée sans arguments quand `quick_exit` est appelé. Il n’est pas spécifié si un appel `at_quick_exit()` à n’a pas lieu avant que `quick_exit` tous les appels à `at_quick_exit()` n’aboutissent et que les fonctions n’introduisent pas de concurrence de données. L’ordre d’enregistrement peut être indéterminé si `at_quick_exit` a été appelé à partir de plusieurs threads `at_quick_exit` et dans la mesure où les `atexit` inscriptions sont distinctes des inscriptions, les applications devront peut-être appeler les deux fonctions d’inscription avec le même argument. L’implémentation prend en charge l’inscription d’au moins 32 fonctions.

### <a name="atexit"></a>ATEX

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Notes

Les `atexit()` fonctions inscrivent la fonction désignée par *Func* pour être appelées sans arguments à l’arrêt normal du programme. Il n’est pas spécifié si un appel `atexit()` à n’a pas lieu avant la `exit()` fin d’un appel `atexit()` à, et les fonctions n’introduisent pas de concurrence de données. L’implémentation prend en charge l’inscription d’au moins 32 fonctions.

#### <a name="return-value"></a>Valeur de retour

Retourne zéro si l’inscription réussit, différente de zéro en cas d’échec.

### <a name="exit"></a>terminer

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Notes

Tout d’abord, les objets avec une durée de stockage de thread et associés au thread actuel sont détruits.

Ensuite, les objets avec une durée de stockage statique sont détruits et `atexit` les fonctions inscrites par l’appel de sont appelées. Les objets automatiques ne sont pas détruits à `exit()`la suite de l’appel de. Si le contrôle quitte une fonction inscrite `exit` appelée par, car la fonction ne fournit pas de gestionnaire pour `std::terminate()` une exception levée, doit être appelé. Une fonction est appelée pour chaque fois qu’elle est inscrite. Les objets avec une durée de stockage automatique sont tous détruits dans un programme dont la fonction principale ne contient pas d’objets `exit()`automatiques et exécute l’appel à. Le contrôle peut être transféré directement à une telle fonction principale en levant une exception interceptée dans main.

Ensuite, tous les flux c ouverts (tels que les signatures de fonctions déclarées <cstdio>dans) avec des données mises en mémoire tampon non écrites sont vidés, tous les flux c ouverts sont fermés, et `tmpfile()` tous les fichiers créés par l’appel à sont supprimés.

Enfin, le contrôle est retourné à l’environnement hôte. Si Status est égal à zéro ou EXIT_SUCCESS, une forme définie par l’implémentation de l’état d’arrêt réussi est retournée. Si l’État est EXIT_FAILURE, une forme définie par l’implémentation de l’état d’arrêt non réussi est retournée. Dans le cas contraire, l’état retourné est défini par l’implémentation.

### <a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Notes

Les fonctions inscrites par `at_quick_exit` les appels à sont appelées dans l’ordre inverse de leur inscription, à ceci près qu’une fonction sera appelée après toutes les fonctions précédemment inscrites qui avaient déjà été appelées au moment de son inscription. Les objets ne seront pas détruits à la suite `quick_exit`de l’appel de. Si le contrôle quitte une fonction inscrite `quick_exit` appelée par, car la fonction ne fournit pas de gestionnaire pour `std::terminate()` une exception levée, doit être appelé. Une fonction inscrite `at_quick_exit` via est appelée par le thread qui appelle `quick_exit`, qui peut être un thread différent de celui qui l’a inscrit. les fonctions inscrites ne doivent donc pas reposer sur l’identité des objets avec une durée de stockage de thread. Après avoir appelé des fonctions `quick_exit` inscrites `_Exit(status)`, appellera. Les mémoires tampons de fichier standard ne sont pas vidées. La fonction `quick_exit` est signalée comme étant sécurisée lorsque les `at_quick_exit` fonctions inscrites auprès de sont.

### <a name="system"></a>requise

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Fonctions d’allocation de mémoire

```cpp
void* aligned_alloc(size_t alignment, size_t size);
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

#### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C.

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>Fonctions de conversion de caractères et de chaînes multioctets/larges

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C.

## <a name="algorithm-functions"></a>Fonctions d’algorithme

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C.

## <a name="low-quality-random-number-generation-functions"></a>Fonctions de génération de nombres aléatoires de faible qualité

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C.

## <a name="absolute-values"></a>Valeurs absolues

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C.

## <a name="functions"></a>Fonctions

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque C++ Standard](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
