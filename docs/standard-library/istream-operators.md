---
title: '&lt;istream&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 3b9521fde1b5a03389bfc1ad3e35fa407d9d6ac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363036"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt;, opérateurs

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>Opérateur&gt;&gt;

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

*Ch*\
Un caractère.

*Istr (Istr)*\
Flux.

*Str*\
Une chaîne.

*Val*\
Type.

### <a name="return-value"></a>Valeur de retour

Flux.

### <a name="remarks"></a>Notes

La classe `basic_istream` définit également plusieurs opérateurs d’extraction. Pour plus d’informations, consultez [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

Le modèle de fonction :

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extraits jusqu’à `N - 1` éléments et les stocke dans le tableau à partir *de str*. Si `Istr.` [la largeur](../standard-library/ios-base-class.md#width) est supérieure à zéro, *N* est `Istr.width`; sinon, c’est la taille de `Elem` la plus grande gamme de qui peut être déclaré. La fonction stocke `Elem()` toujours la valeur après les éléments extraits qu’elle stocke. L’extraction s’arrête tôt sur la `Elem(0)` fin du fichier, sur un personnage avec une valeur (qui n’est pas extrait), ou sur n’importe quel élément (qui n’est pas extrait) qui serait jeté par [ws](../standard-library/istream-functions.md#ws). Si la fonction n’extrait `Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`aucun élément, elle appelle . En tout cas, `Istr.width(0)` il appelle et renvoie *Istr*.

**Note de sécurité** La chaîne non terminée extraite du flux d’entrée ne doit pas dépasser la taille de la *zone*tampon de destination. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

Le modèle de fonction :

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrait un élément, si possible, et le stocke dans *Ch*. Sinon, il `is.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`appelle . En tout cas, il retourne *Istr*.

Le modèle de fonction :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

Retourne `Istr >> ( char * ) str`.

Le modèle de fonction :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

Retourne `Istr >> ( char& ) Ch`.

Le modèle de fonction :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

Retourne `Istr >> ( char * ) str`.

Le modèle de fonction :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

Retourne `Istr >> ( char& ) Ch`.

Le modèle de fonction :

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

retourne `Istr >> val` (et convertit une référence `Istr` rvalue à une lvalue dans le processus).

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

[\<>istream](../standard-library/istream.md)
