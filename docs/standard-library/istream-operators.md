---
title: '&lt;istream&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::operator&gt;&gt;
dev_langs:
- C++
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5068c0bd540b1c44d2cdc484c2e511276bd12666
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853058"
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

`Ch` Un caractère.

`Istr` Flux de données.

`str` Une chaîne.

`val` Un type.

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

extrait jusqu’à *N* - 1 éléments et les stocke dans le tableau en commençant à _ *Str*. Si `Istr`. [width](../standard-library/ios-base-class.md#width) est supérieure à zéro, *N* est `Istr`. **width**. Sinon, il est égal à la taille du plus grand tableau **Elem** qui peut être déclaré. La fonction stocke toujours la valeur **Elem()** après tout élément extrait qu’elle stocke. L’extraction s’arrête dès la fin du fichier, sur un caractère avec la valeur **Elem**(0) (qui n’est pas extrait), ou sur tout élément (qui n’est pas extrait) qui serait ignoré par [ws](../standard-library/istream-functions.md#ws). Si la fonction n’extrait aucun élément, elle appelle `Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Dans tous les cas, elle appelle `Istr`. **width**(0) et retourne `Istr`.

**Note de sécurité** La chaîne terminée par Null qui est extraite du flux d’entrée ne doit pas dépasser la taille de la mémoire tampon de destination `str`. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](http://msdn.microsoft.com/library/windows/desktop/ms717795).

La fonction de modèle

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrait un élément, si c’est possible, et le stocke dans `Ch`. Sinon, elle appelle **is**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Dans tous les cas, elle retourne `Istr`.

La fonction de modèle

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

retourne `Istr` >> ( `char`**\***) `str`.

La fonction de modèle

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

retourne `Istr` >> ( **char&**) `Ch`.

La fonction de modèle

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

retourne `Istr` >> ( **char \***) `str`.

La fonction de modèle :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

retourne `Istr` >> ( **char&**) `Ch`.

La fonction de modèle

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

retourne `Istr` `>>` `val` (et convertit un `rvalue reference` à `Istr` en un `lvalue` dans le même temps).

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
