---
title: '`<ios>`, typedefs'
description: Décrit les typedefs de la bibliothèque STL (Standard Template Library) C++ `<ios>` qui prennent en charge la `ios` classe de l’ancienne `iostream` bibliothèque.
ms.date: 11/06/2020
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.openlocfilehash: 4af9636ab3317e7b81eb73dc74aef065b1287e21
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381634"
---
# <a name="ios-typedefs"></a>`<ios>`, typedefs

## `ios`

Prend en charge la `ios` classe de l’ancienne `iostream` bibliothèque.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Remarques

Le type est un synonyme du modèle de classe [`basic_ios`](../standard-library/basic-ios-class.md) , spécialisé pour les éléments de type **`char`** avec des caractéristiques de caractère par défaut.

## `streamoff`

Prend en charge les opérations internes.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Remarques

Le type est un entier signé. Il décrit un objet qui peut stocker un décalage d’octet dans les opérations de positionnement de flux. Sa représentation a au moins 32 bits de valeur. Elle n’est pas nécessairement assez grande pour représenter une position d’octet arbitraire dans un flux. La valeur `streamoff(-1)` indique généralement un décalage erroné.

## `streampos`

Contient la position actuelle du pointeur de mémoire tampon ou du pointeur de fichier.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Remarques

Le type est un synonyme de [`fpos`](../standard-library/fpos-class.md) <  `mbstate_t`>.

### <a name="example"></a>Exemple

```cpp
// ios_streampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ofstream x( "iostream.txt" );
   x << "testing";
   streampos y = x.tellp( );
   cout << streamoff(y) << '\n';
}
```

```Output
7
```

## `streamsize`

Indique la taille du flux.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Remarques

Le type est un entier signé qui décrit un objet capable de stocker le nombre d’éléments impliqués dans différentes opérations de flux. Sa représentation a au moins 16 bits. Elle n’est pas nécessairement assez grande pour représenter une position d’octet arbitraire dans un flux.

### <a name="example"></a>Exemple

Après la compilation et l’exécution du programme suivant, examinez le fichier `test.txt` pour voir l’effet du paramètre `streamsize` .

```cpp
// ios_streamsize.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   char a[16] = "any such text";
   ofstream x( "test.txt" );
   streamsize y = 6;
   x.write( a, y );
}
```

## `wios`

Prend en charge la `wios` classe de l’ancienne `iostream` bibliothèque.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Remarques

Le type est un synonyme du modèle de classe [`basic_ios`](../standard-library/basic-ios-class.md) , spécialisé pour les éléments de type **`wchar_t`** avec des caractéristiques de caractère par défaut.

## `wstreampos`

Contient la position actuelle du pointeur de mémoire tampon ou du pointeur de fichier.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Remarques

Le type est un synonyme de [`fpos`](../standard-library/fpos-class.md) <  `mbstate_t`>.

### <a name="example"></a>Exemple

```cpp
// ios_wstreampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   wofstream xw( "wiostream.txt" );
   xw << L"testing";
   wstreampos y = xw.tellp( );
   cout << y << endl;
}
```

```Output
7
```
