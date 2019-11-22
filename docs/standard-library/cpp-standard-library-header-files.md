---
title: C++fichiers d’en-tête de bibliothèque standard
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 807e65c69e55d8790b77a493e4ae1878aa740557
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305404"
---
# <a name="c-standard-library-header-files"></a>C++fichiers d’en-tête de bibliothèque standard

Fichiers d’en- C++ tête pour la bibliothèque standard et les extensions, par catégorie.

## <a name="headers-by-category"></a>En-têtes par catégorie

::: moniker range=">=vs-2017"

| Catégorie | En-têtes |
| - | - |
| [Algorithmes](../cpp/algorithms-modern-cpp.md) | [algorithme de\<>](algorithm.md), [\<cstdlib >](cstdlib.md), [\<numérique >](numeric.md) |
| Opérations atomiques |  [\<atomic >](atomic.md)<sup>11</sup> |
| Wrappers de la bibliothèque C | [\<cassert >](cassert.md), [\<ccomplex >](ccomplex.md)<sup>11 a b</sup>, [\<cctype >](cctype.md), [\<cerrno >](cerrno.md), [\<cfenv >](cfenv.md)<sup>11</sup>, [\<cfloat >](cfloat.md), [\<cinttypes >](cinttypes.md)<sup>11</sup>, [\<ciso646 >](ciso646.md)<sup>b</sup>, [\<climits >](climits.md), [\<clocale >](clocale.md), [\<cmath >](cmath.md), [\<csetjmp >](csetjmp.md), [\<cSignal >](csignal.md), [\<cstdalign >](cstdalign.md)<sup>11 a b</sup>, [\<cstdarg >](cstdarg.md), [\<cstdbool >](cstdbool.md)<sup>11 a b</sup>, [\<cstddef >](cstddef.md), [\<cstdint >](cstdint.md)<sup>11</sup>, [\<cstdio >](cstdio.md), [\<cstdlib >](cstdlib.md), [\<CString >](cstring.md), [\<ctgmath >](ctgmath.md)<sup>11 a b</sup>, [\<ctime >](ctime.md), [\<cuchar >](cuchar.md)<sup>11</sup> , [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md) |
| Concepts | concepts de \<><sup>20</sup> |
| [Conteneurs](../cpp/containers-modern-cpp.md) | |
| Conteneurs de séquence | [\<array >](array.md)<sup>11</sup>, [\<deque >](deque.md), [\<](forward-list.md)forward_list ><sup>11</sup>, [\<List](list.md)>, [\<Vector](vector.md) > |
| Conteneurs associatifs ordonnés| [\<map>](map.md), [\<set>](set.md) |
| Conteneurs associatifs non ordonnés | [\<unordered_map >](unordered-map.md)<sup>11</sup>, [\<unordered_set](unordered-set.md)><sup>11</sup> |
| Adaptateurs de conteneur | [\<queue>](queue.md), [\<stack>](stack.md) |
| Vues de conteneur | \<étendue ><sup>20</sup> |
| [Erreurs et gestion des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert >](cassert.md), [\<exception >](exception.md), [\<stdexcept](stdexcept.md) [>,\<system_error >](system-error.md)<sup>11</sup> |
| Utilitaires généraux | \<les ><sup>17</sup>, [\<BitSet >](bitset.md), \<charconv ><sup>17</sup>, [\<cstdlib >](cstdlib.md), \<Execution ><sup>17</sup>, [\<Functional >](functional.md),\<[Memory >](memory.md), \<memory_resource ><sup>17</sup>, \<facultatif ><sup>17</sup>, [\<ratio >](ratio.md)<sup>11</sup>, [\<](scoped-allocator.md)scoped_allocator ><sup>11</sup>, [\<Tuple](tuple.md)><sup>11</sup>, [\<type_traits >](type-traits.md)<sup>11</sup>, [\<typeindex >](typeindex.md)<sup>11</sup>, [\<Utility >](utility.md), \<variant ><sup>17</sup> |
| [E/s et mise en forme](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes >](cinttypes.md)<sup>11</sup>, [\<cstdio >](cstdio.md), [\<FileSystem >](filesystem.md)<sup>17</sup>, [\<fstream >](fstream.md), [\<iomanip >](iomanip.md), [\<ios >](ios.md), [\<iosfwd >](iosfwd.md), [\<iostream >](iostream.md),\<[IStream >](istream.md), [\<ostream >](ostream.md), [\<sstream >](sstream.md), [\<streambuf >](streambuf.md), [\<strstream >](strstream.md)<sup>c </sup>, \<syncstream ><sup>20</sup> |
| Itérateurs | [\<iterator>](iterator.md) |
| Prise en charge linguistique | [\<cfloat >](cfloat.md), [\<climits >](climits.md), [\<codecvt >](codecvt.md)<sup>11 a</sup>, \<comparer ><sup>20</sup>, \<contrat ><sup>20</sup>, \<Coroutine ><sup>20</sup>, [\<csetjmp >](csetjmp.md), [\<cSignal >](csignal.md), [\<cstdarg >](cstdarg.md), [\<cstddef >](cstddef.md), [\<cstdint >](cstdint.md)<sup>11</sup>, [\<cstdlib >](cstdlib.md),\<[exception](exception.md) > , [\<initializer_list >](initializer-list.md)<sup>11</sup>, [\<limites >](limits.md), [\<new >](new.md), [\<TypeInfo >](typeinfo.md), \<version ><sup>20</sup> |
| Localisation | [\<clocale >](clocale.md), [\<codecvt >](codecvt.md)<sup>11 a</sup>, [\<CVT/wbuffer >](cvt-wbuffer.md), [\<CVT/wstring >](cvt-wstring.md), [\<paramètres régionaux >](locale.md) |
| Maths et numériques | \<bits ><sup>20</sup>, [\<cfenv >](cfenv.md)<sup>11</sup>, [\<cmath >](cmath.md), [\<> complexe](complex.md), [\<cstdlib >](cstdlib.md), [\<Limits >](limits.md),\<[Numeric](numeric.md)>, [\<> aléatoire](random.md)<sup>11</sup>,\<[ratio](ratio.md)><sup>11</sup>, [\<valarray >](valarray.md) |
| [Gestion de la mémoire](../cpp/smart-pointers-modern-cpp.md) | [\<allocators >](allocators-header.md), [\<de la mémoire >](memory.md), \<memory_resource ><sup>17</sup>\<[New >](new.md), [\<](scoped-allocator.md)scoped_allocator ><sup>11</sup> |
| Multithreading | [\<atomic >](atomic.md)<sup>11</sup>, [\<CONDITION_VARIABLE >](condition-variable.md)<sup>11</sup>, [\<future >](future.md)<sup>11</sup>, [\<mutex >](mutex.md)<sup>11</sup>, [\<](shared-mutex.md)shared_mutex ><sup>14</sup>, [\<thread >](thread.md)<sup>11</sup> |
| Plages | plages de \<><sup>20</sup> |
| Expressions régulières | [\<regex >](regex.md)<sup>11</sup> |
| Chaînes et données caractères | [\<cctype >](cctype.md), [\<cstdlib >](cstdlib.md), [\<cstring >](cstring.md), [\<cuchar >](cuchar.md)<sup>11</sup>, [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md), [\<Regex >](regex.md)<sup>11</sup>, [\<String >](string.md), [\<string_view >](string-view.md)<sup>17</sup> |
| réflexion | [\<chrono >](chrono.md)<sup>11</sup>, [\<ctime >](ctime.md) |

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
|Conteneurs de séquence|[\<array >](array.md), [\<deque >](deque.md), [\<forward_list >](forward-list.md), [\<List](list.md)>, [\<Vector](vector.md) >|
|Conteneurs associatifs ordonnés| [\<map>](map.md), [\<set>](set.md)|
|Conteneurs associatifs non ordonnés|[\<unordered_map >](unordered-map.md), [\<unordered_set](unordered-set.md) >|
|Conteneurs d’adaptateur|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Erreurs et gestion des exceptions](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<exception >](exception.md), [\<stdexcept >](stdexcept.md), [\<system_error >](system-error.md)|
|[E/s et mise en forme](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Itérateurs|[\<iterator>](iterator.md)|
|Localisation|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Maths et numériques|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[Gestion de la mémoire](../cpp/smart-pointers-modern-cpp.md)|[\<allocators >](allocators-header.md), [\<> de mémoire](memory.md), [\<nouvelle >](new.md) [\<scoped_allocator](scoped-allocator.md)|
|Multithreading|[\<atomic >](atomic.md), [\<condition_variable >](condition-variable.md), [\<> future](future.md)\<, > [mutex](mutex.md)\<[, shared_mutex >\<,](shared-mutex.md) [> thread](thread.md)|
|Autres utilitaires|[\<bitset >](bitset.md), [\<chrono >](chrono.md), [\<Functional >](functional.md) [,\<initializer_list >](initializer-list.md), [\<tuple >](tuple.md), [\<type_traits](type-traits.md)>, [\<TypeInfo >](typeinfo.md), [\<typeindex >](typeindex.md), [\<Utility >](utility.md)|
|Chaînes et données caractères|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Utilisation C++ d’en-têtes de bibliothèque](using-cpp-library-headers.md)\
[C++bibliothèque standard](cpp-standard-library-reference.md)
