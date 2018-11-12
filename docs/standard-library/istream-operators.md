---
title: '&lt;istream&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 05b10c27d8e0cf4c0300bb307d8b7ceda43ddb2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474085"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt;, opérateurs

## <a name="op_gt_gt"></a>  operator&gt;&gt;

Extrait des chaînes et des caractères à partir du flux.

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>Paramètres

*CH*<br/>
Un caractère.

*ISTR*<br/>
Un flux.

*str*<br/>
Chaîne.

*Val*<br/>
Type.

### <a name="return-value"></a>Valeur de retour

Flux.

### <a name="remarks"></a>Notes

La classe `basic_istream` définit également plusieurs opérateurs d’extraction. Pour plus d’informations, consultez [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

La fonction de modèle

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extrait jusqu’à *N* - 1 éléments et les stocke dans le tableau en commençant à _ *Str*. Si `Istr`. [width](../standard-library/ios-base-class.md#width) est supérieure à zéro, *N* est `Istr`. **largeur**; sinon, elle est la taille de la plus grande quantité de `Elem` qui peut être déclaré. La fonction stocke toujours la valeur `Elem()` après les éléments qu’elle stocke extraits. L’extraction s’arrête dès la fin du fichier, sur un caractère avec la valeur **Elem**(0) (qui n’est pas extrait), ou sur tout élément (qui n’est pas extrait) qui serait ignoré par [ws](../standard-library/istream-functions.md#ws). Si la fonction n’extrait aucun élément, elle appelle `Istr`. [SetState](../standard-library/basic-ios-class.md#setstate)(**failbit**). Dans tous les cas, elle appelle `Istr`. **largeur**(0) et retourne *Istr*.

**Note de sécurité** la chaîne se terminant par null qui est extraite du flux d’entrée ne doit pas dépasser la taille de la mémoire tampon de destination *str*. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/desktop/SecBP/avoiding-buffer-overruns).

La fonction de modèle

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrait un élément, s’il est possible et le stocke dans *Ch*. Sinon, elle appelle **is**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Dans tous les cas, elle retourne *Istr*.

La fonction de modèle

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

Retourne `Istr >> ( char * ) str`.

La fonction de modèle

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

Retourne `Istr >> ( char& ) Ch`.

La fonction de modèle

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

Retourne `Istr >> ( char * ) str`.

La fonction de modèle

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

Retourne `Istr >> ( char& ) Ch`.

La fonction de modèle

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

Retourne `Istr >> val` (et convertit une référence rvalue à `Istr` en lvalue dans le processus).

### <a name="example"></a>Exemple

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>Voir aussi

[\<istream>](../standard-library/istream.md)<br/>
