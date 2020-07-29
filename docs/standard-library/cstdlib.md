---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 1b20e13a43c5d223332af70a91e096cedc284a43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230050"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Inclut l’en-tête de la bibliothèque standard C \<stdlib.h> et ajoute les noms associés à l' `std` espace de noms. L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l’en-tête de la bibliothèque standard C sont déclarés dans l' `std` espace de noms.

> [!NOTE]
> \<stdlib.h>n’inclut pas le type **`wchar_t`** .

## <a name="requirements"></a>Spécifications

**En-tête**:\<cstdlib>

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
|[système](#system)|Consultez Référence de la bibliothèque standard C.|

### <a name="_exit"></a><a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Notes

Le programme est arrêté sans exécuter de destructeurs pour les objets de durée de stockage automatique, de thread ou statique et sans appel de fonctions passé à `atexit()` . La fonction `_Exit` est signal-safe.

### <a name="abort"></a><a name="abort"></a>arrêté

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Notes

Le programme est arrêté sans exécuter de destructeurs pour les objets de durée de stockage automatique, de thread ou statique et sans appel de fonctions passé à `atexit()` . La fonction `abort` est signal-safe.

### <a name="at_quick_exit"></a><a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Valeur de retour

Zéro si l’inscription réussit, valeur différente de zéro en cas d’échec.

#### <a name="remarks"></a>Notes

Les `at_quick_exit()` fonctions inscrivent une fonction *Func*, qui est appelée sans arguments quand `quick_exit` est appelé. Appel à `at_quick_exit()` qui ne se produit pas avant que tous les appels à `quick_exit` ne puissent pas être exécutés correctement. Les `at_quick_exit()` fonctions n’introduisent pas de concurrence de données. L’ordre d’enregistrement peut être indéterminé si `at_quick_exit` a été appelé à partir de plusieurs threads. Étant donné que `at_quick_exit` les inscriptions sont distinctes des `atexit` inscriptions, les applications peuvent avoir besoin d’appeler les deux fonctions d’inscription à l’aide du même argument. MSVC prend en charge l’inscription d’au moins 32 fonctions.

### <a name="atexit"></a><a name="atexit"></a>ATEX

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Notes

Les `atexit()` fonctions inscrivent la fonction désignée par *Func* pour être appelées sans arguments à l’arrêt normal du programme. Un appel à `atexit()` n’a pas lieu avant qu’un appel à n' `exit()` aboutisse. Les `atexit()` fonctions n’introduisent pas de concurrence de données.

#### <a name="return-value"></a>Valeur de retour

Retourne zéro si l’inscription réussit, différente de zéro en cas d’échec.

### <a name="exit"></a><a name="exit"></a>terminer

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Notes

Tout d’abord, les objets avec une durée de stockage de thread et associés au thread actuel sont détruits.

Ensuite, les objets avec une durée de stockage statique sont détruits et les fonctions inscrites par l’appel de `atexit` sont appelées. Les objets automatiques ne sont pas détruits lorsque `exit()` est appelé. Si le contrôle quitte une fonction inscrite appelée par `exit` , car la fonction ne fournit pas de gestionnaire pour une exception levée, `std::terminate()` est appelée. Une fonction est appelée une fois pour chaque fois qu’elle est inscrite. Les objets avec une durée de stockage automatique sont tous détruits dans un programme dont `main` la fonction ne contient pas d’objets automatiques et exécute l’appel à `exit()` . Le contrôle peut être transféré directement à une telle `main` fonction en levant une exception interceptée dans `main` .

Ensuite, tous les flux C ouverts (tels que les signatures de fonctions déclarées dans \<cstdio> ) avec des données mises en mémoire tampon non écrites sont vidés, tous les flux c ouverts sont fermés, et tous les fichiers créés par l’appel à `tmpfile()` sont supprimés.

Enfin, le contrôle est retourné à l’environnement hôte. Lorsque *Status* est égal à zéro ou EXIT_SUCCESS, une forme définie par l’implémentation de l’état arrêt réussi est retournée. MSVC retourne une valeur de zéro. Si l' *État* est EXIT_FAILURE, MSVC retourne la valeur 3. Sinon, MSVC retourne la valeur de paramètre d' *État* .

### <a name="getenv"></a><a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a><a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Notes

En règle générale, les fonctions inscrites par des appels à `at_quick_exit` sont appelées dans l’ordre inverse de leur inscription. Cet ordre ne s’applique pas aux fonctions inscrites après que d’autres fonctions inscrites ont déjà été appelées. Aucun objet n’est détruit lorsque `quick_exit` est appelé. Si le contrôle quitte une fonction inscrite appelée par `quick_exit` , car la fonction ne fournit pas de gestionnaire pour une exception levée, `std::terminate()` est appelée. Une fonction inscrite via `at_quick_exit` est appelée par le thread qui appelle `quick_exit` , qui peut être un thread différent de celui qui l’a inscrit. Cela signifie que les fonctions inscrites ne doivent pas reposer sur l’identité des objets qui ont une durée de stockage de thread. Après avoir appelé les fonctions inscrites, `quick_exit` appelle `_Exit(status)` . Les mémoires tampons de fichier standard ne sont pas vidées. La fonction `quick_exit` est signalée comme étant sécurisée lorsque les fonctions inscrites auprès de `at_quick_exit` sont.

### <a name="system"></a><a name="system"></a>requise

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Fonctions d’allocation de mémoire

```cpp
// void* aligned_alloc(size_t alignment, size_t size); // Unsupported in MSVC
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
```

### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C. MSVC ne prend pas en charge la `aligned_alloc` fonction. C11 spécifié d' `aligned_alloc()` une manière incompatible avec l’implémentation Microsoft de `free()` , à savoir, qui `free()` doit être en mesure de gérer des allocations hautement alignées.

## <a name="numeric-string-conversions"></a>Conversions de chaînes numériques

```cpp
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

### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C.

## <a name="multibyte--wide-string-and-character-conversion-functions"></a>Fonctions de conversion de caractères et de chaînes multioctets/larges

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
```

### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C.

## <a name="integer-division"></a>Division d'entier

```cpp
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Notes

Ces fonctions ont la sémantique spécifiée dans la bibliothèque standard C.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
