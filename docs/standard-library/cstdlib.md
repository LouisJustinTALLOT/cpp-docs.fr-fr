---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 70e05ad734fa49ba8cb96e4bf83bc05b99c5f55c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246529"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Inclut l’en-tête de bibliothèque C Standard \<stdlib.h > et ajoute les noms associés à la `std` espace de noms. Inclusion de cet en-tête garantit également que les noms déclarés à l’aide d’une liaison externe dans l’en-tête de la bibliothèque standard C sont déclarés dans le `std` espace de noms.

> [!NOTE]
> \<STDLIB.h > n’inclut pas le type **wchar_t**.

## <a name="requirements"></a>Configuration requise

**En-tête**: \<cstdlib >

**Espace de noms :** std

## <a name="namespace-and-macros"></a>Namespace et Macros

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

## <a name="exposition-only-functions"></a>Seules les fonctions démonstration

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Fonctions de démarrage et arrêt

|Fonction|Description|
|-|-|
|[_Exit](#_exit)|Met fin au programme sans utiliser de destructeurs ou fonctions inscrites.|
|[abort](#abort)|Met fin au programme sans utilisation de destructeurs.|
|[atexit](#atexit)|Fonction de registres pour l’arrêt du programme.|
|[exit](#exit)|Détruit les objets avec thread et de stockage statique, puis retourne le contrôle.|
|[at_quick_exit](#at_quick_exit)|Fonction de registres sans arguments pour l’arrêt du programme.|
|[quick_exit](#quick_exit)|Fonction de registres avec les objets conservés pour l’arrêt du programme.|
|[getenv](#getenv)|Consultez la référence de la bibliothèque standard C.|
|[system](#system)|Consultez la référence de la bibliothèque standard C.|

### <a name="_exit"></a> _Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Notes

Le programme se termine sans exécuter les destructeurs des objets automatique, le thread ou une durée de stockage statique et sans appel de fonctions passées à `atexit()`. La fonction `_Exit` est signal-safe.

### <a name="abort"></a> Abandonner

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Notes

Le programme se termine sans exécuter les destructeurs des objets automatique, le thread ou une durée de stockage statique et sans appel de fonctions passées à `atexit()`. La fonction `abort` est signal-safe.

### <a name="at_quick_exit"></a> at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Valeur de retour

Zéro si l’inscription réussit, zéro en cas d’échec.

#### <a name="remarks"></a>Notes

Le `at_quick_exit()` fonctions inscrire la fonction vers laquelle pointée *func* à être appelé sans arguments lorsque `quick_exit` est appelée. Il a n’est pas spécifié si un appel à `at_quick_exit()` qui ne se produit avant tous les appels à `quick_exit` réussit et le `at_quick_exit()` fonctions n’introduisent pas une concurrence de données. L’ordre de l’inscription peut être indéterminé si `at_quick_exit` a été appelée à partir de plus qu’un seul thread et depuis `at_quick_exit` inscriptions sont distinctes de la `atexit` inscriptions, applications devront peut-être appeler les deux fonctions d’inscription avec le même d’argument. L’implémentation doit prendre en charge l’inscription de fonctions au moins 32.

### <a name="atexit"></a> atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Notes

Le `atexit()` fonctions inscrire la fonction vers laquelle pointée *func* à être appelé sans arguments au niveau de l’arrêt normal du programme. Il a n’est pas spécifié si un appel à `atexit()` qui ne se produit avant un appel à `exit()` réussit et le `atexit()` fonctions n’introduisent pas une concurrence de données. L’implémentation doit prendre en charge l’inscription de fonctions au moins 32.

#### <a name="return-value"></a>Valeur de retour

Retourne zéro si l’inscription réussit, différente de zéro en cas d’échec.

### <a name="exit"></a> quitter

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Notes

Tout d’abord, objets avec une durée de stockage de thread et associé actuel thread sont détruits.

Ensuite, avec une durée de stockage statique, les objets sont détruits et fonctions enregistrées en appelant `atexit` sont appelées. Objets automatiques ne sont pas détruits suite à l’appel `exit()`. Si le contrôle quitte une fonction inscrite, appelée par `exit` , car la fonction ne fournit pas un gestionnaire pour une exception levée, `std::terminate()` doit être appelée. Une fonction est appelée pour chaque fois qu’il est inscrit. Les objets avec une durée de stockage automatique sont détruits dans un programme dont la fonction principale ne contient aucun objet automatique et exécute l’appel à `exit()`. Contrôle peut être transféré directement à une telle fonction principale en levant une exception est interceptée dans la fonction main.

Ensuite, tous les ouverts C flux (comme atténuées par les signatures de fonction déclarés dans <cstdio>) avec les données mises en mémoire tampon qui sont vidé, ouvrez tous les flux de C sont fermés et tous les fichiers créés en appelant `tmpfile()` sont supprimés.

Enfin, le contrôle est retourné à l’environnement hôte. Si l’état est égal à zéro ou EXIT_SUCCESS, un formulaire défini par l’implémentation de l’arrêt de réussite d’état est retourné. Si l’état est EXIT_FAILURE, un formulaire défini par l’implémentation de l’arrêt échoue d’état est retourné. Sinon, l’état retourné est défini par l’implémentation.

### <a name="getenv"></a> getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a> quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Notes

Fonctions enregistrées par des appels à `at_quick_exit` sont appelés dans l’ordre inverse de leur inscription, sauf qu’une fonction doit être appelée une fois que les inscrit précédemment des fonctions qui avaient déjà été appelées au moment où elle a été inscrite. Les objets ne sont pas détruits suite à l’appel `quick_exit`. Si le contrôle quitte une fonction inscrite, appelée par `quick_exit` , car la fonction ne fournit pas un gestionnaire pour une exception levée, `std::terminate()` doit être appelée. Une fonction enregistrée par le biais de `at_quick_exit` est appelé par le thread qui appelle `quick_exit`, ce qui peut être un autre thread que celui qui inscrit, inscrit par conséquent, les fonctions ne doivent pas s’appuient sur l’identité des objets avec une durée de stockage de thread. Après l’appel de fonctions inscrites, `quick_exit` appellera `_Exit(status)`. Les mémoires tampons de fichier standard ne sont pas vidées. La fonction `quick_exit` est signal sécurisé lorsque les fonctions enregistré avec `at_quick_exit` sont.

### <a name="system"></a> Système

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

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>Chaîne multioctet / large et les fonctions de conversion de caractère

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

## <a name="low-quality-random-number-generation-functions"></a>Fonctions de génération de nombres aléatoires basse qualité

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

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
