---
title: Fichiers d’en-tête de bibliothèque standard C++
description: Fichiers d’en-tête de bibliothèque C++ standard, catégorisés
ms.date: 08/31/2020
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 7d4978e7de75e5416ba2653a632d713f407d3677
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924818"
---
# <a name="c-standard-library-header-files"></a>Fichiers d’en-tête de bibliothèque standard C++

Fichiers d’en-tête pour la bibliothèque C++ standard et les extensions, par catégorie.

## <a name="headers-by-category"></a>En-têtes par catégorie

::: moniker range=">=msvc-150"

| Category | headers |
| - | - |
| [Algorithmes](./algorithms.md) | [\<algorithm>](algorithm.md), [\<cstdlib>](cstdlib.md), [\<numeric>](numeric.md) |
| Opérations atomiques |  [\<atomic>](atomic.md)<sup>11</sup> |
| Wrappers de la bibliothèque C | [\<cassert>](cassert.md), [\<ccomplex>](ccomplex.md) <sup>11 a b</sup>, [\<cctype>](cctype.md) , [\<cerrno>](cerrno.md) , [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cfloat>](cfloat.md) , [\<cinttypes>](cinttypes.md) <sup>11</sup>, [\<ciso646>](ciso646.md) <sup>b</sup>, [\<climits>](climits.md) ,,,,, [\<clocale>](clocale.md) [\<cmath>](cmath.md) [\<csetjmp>](csetjmp.md) [\<csignal>](csignal.md) [\<cstdalign>](cstdalign.md) <sup>11 a b</sup>, [\<cstdarg>](cstdarg.md) , [\<cstdbool>](cstdbool.md) <sup>11 a b</sup>, [\<cstddef>](cstddef.md) , [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdio>](cstdio.md) ,,, [\<cstdlib>](cstdlib.md) [\<cstring>](cstring.md) [\<ctgmath>](ctgmath.md) <sup>11 a b</sup>, [\<ctime>](ctime.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) ,[\<cwctype>](cwctype.md) |
| Concepts | \<concepts><sup>20</sup> |
| [Containers](./stl-containers.md) | |
| Conteneurs de séquence | [\<array>](array.md)<sup>11</sup>, [\<deque>](deque.md) , [\<forward_list>](forward-list.md) <sup>11</sup>, [\<list>](list.md) ,[\<vector>](vector.md) |
| Conteneurs associatifs ordonnés| [\<map>](map.md), [\<set>](set.md) |
| Conteneurs associatifs non ordonnés | [\<unordered_map>](unordered-map.md)<sup>11</sup>, [\<unordered_set>](unordered-set.md) <sup>11</sup> |
| Adaptateurs de conteneur | [\<queue>](queue.md), [\<stack>](stack.md) |
| Vues de conteneur | [\<span>](span.md)<sup>20</sup> |
| [Erreurs et gestion des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert>](cassert.md), [\<exception>](exception.md) , [\<stdexcept>](stdexcept.md) , [\<system_error>](system-error.md) <sup>11</sup> |
| Utilitaires généraux | \<any><sup>17</sup>, [\<bit>](bit.md) <sup>20</sup>, [\<bitset>](bitset.md) , [\<cstdlib>](cstdlib.md) , \<execution> <sup>17</sup>, [\<functional>](functional.md) , [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, \<optional> <sup>17</sup>, [\<ratio>](ratio.md) <sup>11</sup>, [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup>, [\<tuple>](tuple.md) <sup>11</sup>, [\<type_traits>](type-traits.md) <sup>11</sup>, [\<typeindex>](typeindex.md) <sup>11</sup>, [\<utility>](utility.md) , \<variant> <sup>17</sup> |
| [E/s et mise en forme](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes>](cinttypes.md)<sup>11</sup>, [\<cstdio>](cstdio.md) , [\<filesystem>](filesystem.md) <sup>17</sup>, [\<fstream>](fstream.md) , [\<iomanip>](iomanip.md) , [\<ios>](ios.md) , [\<iosfwd>](iosfwd.md) , [\<iostream>](iostream.md) , [\<istream>](istream.md) , [\<ostream>](ostream.md) , [\<sstream>](sstream.md) , [\<streambuf>](streambuf.md) , [\<strstream>](strstream.md) <sup>c</sup>, \<syncstream> <sup>20</sup> |
| Iterators | [\<iterator>](iterator.md) |
| Support multilingue | [\<cfloat>](cfloat.md), [\<climits>](climits.md) , [\<codecvt>](codecvt.md) <sup>11 a</sup>, 20, 20, \<compare> <sup>20</sup> \<contract> <sup>20</sup> \<coroutine> <sup>20</sup>,,,,, [\<csetjmp>](csetjmp.md) [\<csignal>](csignal.md) [\<cstdarg>](cstdarg.md) [\<cstddef>](cstddef.md) [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdlib>](cstdlib.md) , [\<exception>](exception.md) , [\<initializer_list>](initializer-list.md) <sup>11</sup>, [\<limits>](limits.md) , [\<new>](new.md) [\<typeinfo>](typeinfo.md) \<version> <sup>20</sup> ,, 20 |
| Localisation | [\<clocale>](clocale.md), [\<codecvt>](codecvt.md) <sup>11 a</sup>, [\<cvt/wbuffer>](cvt-wbuffer.md) , [\<cvt/wstring>](cvt-wstring.md) ,[\<locale>](locale.md) |
| Maths et numériques | \<bit><sup>20</sup>, [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cmath>](cmath.md) , [\<complex>](complex.md) , [\<cstdlib>](cstdlib.md) , [\<limits>](limits.md) , [\<numeric>](numeric.md) , [\<random>](random.md) <sup>11</sup>, [\<ratio>](ratio.md) <sup>11</sup>,[\<valarray>](valarray.md) |
| [Gestion de la mémoire](../cpp/smart-pointers-modern-cpp.md) | [\<allocators>](allocators-header.md), [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, [\<new>](new.md) , [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup> |
| Multithreading | [\<atomic>](atomic.md)<sup>11</sup>, [\<condition_variable>](condition-variable.md) <sup>11</sup>, [\<future>](future.md) <sup>11</sup>, [\<mutex>](mutex.md) <sup>11</sup>, [\<shared_mutex>](shared-mutex.md) <sup>14</sup>, [\<thread>](thread.md) <sup>11</sup> |
| Plages | \<ranges><sup>20</sup> |
| Expressions régulières | [\<regex>](regex.md)<sup>11</sup> |
| Chaînes et données caractères | [\<charconv>](charconv.md)<sup>17</sup>,,,, [\<cctype>](cctype.md) [\<cstdlib>](cstdlib.md) [\<cstring>](cstring.md) [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) , [\<cwctype>](cwctype.md) , [\<regex>](regex.md) <sup>11</sup>, [\<string>](string.md) , [\<string_view>](string-view.md) <sup>17</sup> |
| Temps | [\<chrono>](chrono.md)<sup>11</sup>, [\<ctime>](ctime.md) |

<sup>11</sup> ajouté dans la norme c++ 11. \
<sup>14</sup> ajouté dans la norme c++ 14. \
<sup>17</sup> ajouté dans la norme c++ 17. \
<sup>20</sup> ajouté dans le brouillon c++ 20 standard. \
<sup>un</sup> déconseillé dans la norme c++ 17. \
<sup>b</sup> supprimé dans le brouillon c++ 20 standard. \
<sup>c</sup> déconseillé dans c++ 98 standard.

::: moniker-end

::: moniker range="msvc-140"

|Category|headers|
|-|-|
|[Algorithmes](./algorithms.md)|[\<algorithm>](algorithm.md)|
|Wrappers de la bibliothèque C|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[Containers](./stl-containers.md)||
|Conteneurs de séquence|[\<array>](array.md), [\<deque>](deque.md), [\<forward_list>](forward-list.md), [\<list>](list.md), [\<vector>](vector.md)|
|Conteneurs associatifs ordonnés| [\<map>](map.md), [\<set>](set.md)|
|Conteneurs associatifs non ordonnés|[\<unordered_map>](unordered-map.md), [\<unordered_set>](unordered-set.md)|
|Conteneurs d’adaptateur|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Erreurs et gestion des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<exception>](exception.md), [\<stdexcept>](stdexcept.md), [\<system_error>](system-error.md)|
|[E/s et mise en forme](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iterators|[\<iterator>](iterator.md)|
|Localisation|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Maths et numériques|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[Gestion de la mémoire](../cpp/smart-pointers-modern-cpp.md)|[\<allocators>](allocators-header.md), [\<memory>](memory.md), [\<new>](new.md), [\<scoped_allocator>](scoped-allocator.md)|
|Multithreading|[\<atomic>](atomic.md), [\<condition_variable>](condition-variable.md), [\<future>](future.md), [\<mutex>](mutex.md), [\<shared_mutex>](shared-mutex.md), [\<thread>](thread.md)|
|Autres utilitaires|[\<bitset>](bitset.md), [\<chrono>](chrono.md), [\<functional>](functional.md), [\<initializer_list>](initializer-list.md), [\<tuple>](tuple.md), [\<type_traits>](type-traits.md), [\<typeinfo>](typeinfo.md), [\<typeindex>](typeindex.md), [\<utility>](utility.md)|
|Chaînes et données caractères|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Utilisation des en-têtes de la bibliothèque C++](using-cpp-library-headers.md)\
[Bibliothèque standard C++](cpp-standard-library-reference.md)
