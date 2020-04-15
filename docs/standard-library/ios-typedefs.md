---
title: '&lt;ios&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 0f63f65fb4c10fbe2ad538852222e6468b9061d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375398"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt;, typedefs

## <a name="ios"></a><a name="ios"></a>Ios

Prend en charge la classe ios de l'ancienne bibliothèque iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_ios](../standard-library/basic-ios-class.md), spécialisé pour les éléments de type **char** avec des traits de caractère par défaut.

## <a name="streamoff"></a><a name="streamoff"></a>streamoff

Prend en charge les opérations internes.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Notes

Le type est un entier signé qui décrit un objet capable de stocker un décalage d’octet impliqué dans différentes opérations de positionnement de flux. Sa représentation a au moins 32 bits de valeur. Elle n’est pas nécessairement assez grande pour représenter une position d’octet arbitraire dans un flux. La `streamoff(-1)` valeur indique généralement une compensation erronée.

## <a name="streampos"></a><a name="streampos"></a>streampos

Contient la position actuelle du pointeur de mémoire tampon ou du pointeur de fichier.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Notes

Le type est synonyme de [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

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
   cout << y << endl;
}
```

```Output
7
```

## <a name="streamsize"></a><a name="streamsize"></a>streamsize

Indique la taille du flux.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Notes

Le type est un entier signé qui décrit un objet capable de stocker le nombre d’éléments impliqués dans différentes opérations de flux. Sa représentation a au moins 16 bits. Elle n’est pas nécessairement assez grande pour représenter une position d’octet arbitraire dans un flux.

### <a name="example"></a>Exemple

Après avoir compilé et exécuté le programme suivant, examinez le fichier test.txt pour voir l’effet du paramètre `streamsize`.

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

## <a name="wios"></a><a name="wios"></a>wios

Prend en charge la classe wios de l'ancienne bibliothèque iostream.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_ios](../standard-library/basic-ios-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="wstreampos"></a><a name="wstreampos"></a>wstreampos wstreampos

Contient la position actuelle du pointeur de mémoire tampon ou du pointeur de fichier.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Notes

Le type est synonyme de [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

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
