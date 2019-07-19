---
title: C++fichiers d’en-tête de bibliothèque standard
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: dc337ef078108d86849aa7b7452512dfb69e6e18
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341128"
---
# <a name="c-standard-library-header-files"></a>C++fichiers d’en-tête de bibliothèque standard

Fichiers d’en- C++ tête pour la bibliothèque standard et les extensions, par catégorie.

## <a name="headers-by-category"></a>En-têtes par catégorie

::: moniker range=">=vs-2017"

| Catégorie | En-têtes |
| - | - |
| [Algorithmes](../cpp/algorithms-modern-cpp.md) | algorithme >, [ \<cstdlib >](cstdlib.md), [ \<Numeric >](numeric.md) [ \<](algorithm.md) |
| Opérations atomiques |  > atomique<sup>11</sup> [ \<](atomic.md) |
| Wrappers de la bibliothèque C | [ \<](cfenv.md)<sup></sup> [ \<](cerrno.md) [ \<cassert >](cctype.md), [ccomplex > 11 a b, cctype >, cerrno >, cfenv > 11, \<](ccomplex.md) [ \<](cassert.md)<sup></sup> [ \<cfloat >](cfloat.md),<sup></sup> [ \<cinttypes >](cinttypes.md)11, [ \<ciso646 >](ciso646.md)<sup>b</sup>, [ \<climits >](climits.md), [ \<clocale >](clocale.md), [ cmath\<>](cmath.md), [ csetjmp>,cSignal>,cstdalign>11ab,cstdarg>,\<](csetjmp.md) [ \<](cstdarg.md) [ \<](csignal.md) [ \<](cstdalign.md)<sup></sup> [ \<cstdbool >](cstdbool.md)<sup>11 a b</sup>, [ \<cstddef >](cstddef.md), [ \<cstdint >](cstdint.md)<sup>11</sup>, [ \<cstdio >](cstdio.md), [ \<cstdlib >](cstdlib.md), [ CString\<>](cstring.md),<sup></sup> [ \<](ctime.md)<sup></sup> [ \<](cuchar.md) [ \<](cwchar.md) [ ctgmath>11\<](ctgmath.md)a b, ctime >, cuchar > 11, cwchar >, [ cwctype\<>](cwctype.md) |
| Concepts | \<concepts ><sup>20</sup> |
| [Conteneurs](../cpp/containers-modern-cpp.md) | |
| Conteneurs de séquence | <sup></sup><sup></sup> [ tableau\<>](array.md)11, [ deque>,forward_list>11,List>,vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md) |
| Conteneurs associatifs ordonnés| [\<map>](map.md), [\<set>](set.md) |
| Conteneurs associatifs non ordonnés | unordered_map ><sup>11</sup>, [ unordered_set>\<](unordered-set.md)<sup>11</sup> [ \<](unordered-map.md) |
| Adaptateurs de conteneur | [\<queue>](queue.md), [\<stack>](stack.md) |
| Vues de conteneur | \<span ><sup>20</sup> |
| [Erreurs et gestion des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md) | <sup></sup> [ cassert\<>](cassert.md) [, exception\<>](exception.md) [, stdexcept\<>](stdexcept.md) [, system_error\<>](system-error.md)11 |
| Utilitaires généraux | \<tout ><sup>17</sup>, [ \<BitSet >](bitset.md), \<charconv ><sup>17</sup>, [ \<cstdlib >](cstdlib.md), \<exécution ><sup>17</sup>, [ \<> fonctionnelle](functional.md), [ Memory\<>](memory.md), \< [ \<](ratio.md)<sup></sup><sup></sup><sup></sup>memory_resource > 17, Optional > 17, ratio > 11, scoped_allocator > \< [ \< ](scoped-allocator.md) <sup>11</sup>,<sup></sup><sup></sup><sup></sup> [ Tuple\<>](tuple.md)11, [ type_traits>11,typeindex>11,utilitaire>,\<](type-traits.md) [ \<](typeindex.md) [ \<](utility.md) \<variante ><sup>17</sup> |
| [E/s et mise en forme](../cpp/string-and-i-o-formatting-modern-cpp.md) | <sup></sup><sup></sup> [ cinttypes\<>](cinttypes.md)11, [ cstdio>,FileSystem>17,FStream>,iomanip>,\<](cstdio.md) [ \<](filesystem.md) [ \<](fstream.md) [ \<](iomanip.md) [ iOS\<>](ios.md), [ iosfwd>,iostream>,IStream>,ostream>,sstream>\<](iosfwd.md) [ \<](iostream.md) [ \<](istream.md) [ \<](ostream.md) [ \<](sstream.md) \< [ ,\<streambuf >](streambuf.md) [ ,\<strstream >](strstream.md)<sup>c</sup>, SyncStream ><sup>20</sup> |
| Iterators | [\<iterator>](iterator.md) |
| Langages pris en charge | \< \< \< <sup></sup><sup></sup><sup></sup> [ cfloat\<>](cfloat.md) [, climits\<>](climits.md) [, codecvt\<>](codecvt.md)11 a, comparer > 20, contrat > 20, Coroutine ><sup>20</sup>, [ \<csetjmp >](csetjmp.md), [ \<cSignal >](csignal.md), [ \<cstdarg >](cstdarg.md), [ \<cstddef >](cstddef.md), [ \<cstdint > ](cstdint.md) <sup>11</sup><sup></sup> [, cstdlib\<>](cstdlib.md) [, exception\<>](exception.md) [, initializer_list\<>](initializer-list.md)11 [, limites>,\<](limits.md) [ \< nouvelle >](new.md), [ \<TypeInfo >](typeinfo.md), \<version ><sup>20</sup> |
| Localisation | [ \<](locale.md) <sup></sup> [ clocale>\<](cvt-wbuffer.md), [codecvt > 11 a, CVT/wbuffer >, CVT/wstring >, paramètres régionaux > \<](codecvt.md) [ \<](cvt-wstring.md) [ \<](clocale.md) |
| Maths et numériques | \<bit ><sup>20</sup>, [ \<cfenv >](cfenv.md)<sup>11</sup>, [ \<cmath >](cmath.md), [ \<Complex >](complex.md), [ \<cstdlib >](cstdlib.md), [ \<Limits >](limits.md), [ >\<numérique](numeric.md),<sup></sup><sup></sup> [ >\<aléatoire](random.md)11 [, ratio>11,valarray>\<](ratio.md) [ \<](valarray.md) |
| [Gestion de la mémoire](../cpp/smart-pointers-modern-cpp.md) | \< [ \<](memory.md)<sup></sup><sup></sup> [ \<](new.md) [ \<](scoped-allocator.md) [ allocators>,mémoire>,memory_resource>17,\<](allocators-header.md)New >, scoped_allocator > 11 |
| Multithreading | <sup></sup><sup></sup><sup></sup><sup></sup> [ Atomic\<>](atomic.md)11, [ CONDITION_VARIABLE>11,future>11,mutex>11,\<](condition-variable.md) [ \<](future.md) [ \<](mutex.md) [ \< shared_mutex >](shared-mutex.md)<sup>14</sup>, [ \<thread >](thread.md)<sup>11</sup> |
| Plages | \<plages ><sup>20</sup> |
| Expressions régulières | Regex ><sup>11</sup> [ \<](regex.md) |
| Chaînes et données caractères | <sup></sup> [ cctype\<>](cctype.md), [ cstdlib>,CString>,cuchar>11,cwchar>,cwctype\<](cstdlib.md) [ \<](cstring.md) [ \<](cuchar.md) [ \<](cwchar.md) [ \< >](cwctype.md) [ ,\<Regex >](regex.md)<sup>11</sup>, [ \<String >](string.md), [ \<string_view >](string-view.md)<sup>17</sup> |
| Temps | Chrono ><sup>11</sup>, [ ctime\<>](ctime.md) [ \<](chrono.md) |

<sup>11</sup> ajouté dans la norme c++ 11. \
<sup>14</sup> ajouté dans la norme c++ 14. \
<sup>17</sup> ajouté dans la norme c++ 17. \
<sup>20</sup> ajouté dans le brouillon c++ 20 standard. \
<sup>un</sup> déconseillé dans la norme c++ 17. \
<sup>b</sup> supprimé dans le brouillon c++ 20 standard. \
<sup>c</sup> déconseillé dans c++ 98 standard.

::: moniker-end

::: moniker range="vs-2015"

|Catégorie|En-têtes|
|-|-|
|[Algorithmes](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|Wrappers de la bibliothèque C|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[Conteneurs](../cpp/containers-modern-cpp.md)||
|Conteneurs de séquence|[ array\<>](array.md), [ deque>,forward_list>,List>,vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md)|
|Conteneurs associatifs ordonnés| [\<map>](map.md), [\<set>](set.md)|
|Conteneurs associatifs non ordonnés|unordered_map >, [ \<](unordered-map.md) [ unordered_set>\<](unordered-set.md)|
|Conteneurs d’adaptateur|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Erreurs et gestion des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md)|exception > [, stdexcept>\<](stdexcept.md), [ system_error\<>](system-error.md) [ \<](exception.md)|
|[E/s et mise en forme](../cpp/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iterators|[\<iterator>](iterator.md)|
|Localisation|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Maths et numériques|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[Gestion de la mémoire](../cpp/smart-pointers-modern-cpp.md)|allocators >, [ \<> de mémoire](memory.md), [ \<New >](new.md), [ \<scoped_allocator >](scoped-allocator.md) [ \<](allocators-header.md)|
|Multithreading|[ Atomic\<>](atomic.md), [ CONDITION_VARIABLE>,>future,mutex>,shared_mutex>,thread\<](condition-variable.md) [ \<](future.md) [ \<](mutex.md) [ \<](shared-mutex.md) [ \< >](thread.md)|
|Autres utilitaires|[ BitSet\<>](bitset.md), [ Chrono>,>fonctionnelle,initializer_list>,Tuple>,type_traits\<](chrono.md) [ \<](functional.md) [ \<](initializer-list.md) [ \<](tuple.md) [ \< >](type-traits.md) [ ,\<TypeInfo >](typeinfo.md), [ \<typeindex >](typeindex.md), [ \<Utility >](utility.md)|
|Chaînes et données caractères|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Utilisation C++ des en-têtes de bibliothèque](using-cpp-library-headers.md)\
[C++bibliothèque standard](cpp-standard-library-reference.md)
