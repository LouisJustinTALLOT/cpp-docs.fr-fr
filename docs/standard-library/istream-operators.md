---
title: '&lt;istream&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 5ac5c61488530f99cdad38ca1bfca365b6ac0f8c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420126"
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

*Ch*\
Un caractère.

*Istr*\
Un flux.

*str*\
Une chaîne.

\ *Val*
Type.

### <a name="return-value"></a>Valeur de retour

Flux.

### <a name="remarks"></a>Notes

La classe `basic_istream` définit également plusieurs opérateurs d’extraction. Pour plus d’informations, consultez [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

Le modèle de fonction :

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extrait jusqu’à `N - 1` éléments et les stocke dans le tableau à partir de *Str*. Si `Istr.`[largeur](../standard-library/ios-base-class.md#width) est supérieure à zéro, *N* est `Istr.width`; dans le cas contraire, il s’agit de la taille du plus grand tableau de `Elem` qui peut être déclaré. La fonction stocke toujours la valeur `Elem()` après les éléments extraits qu’elle stocke. L’extraction s’arrête tôt à la fin du fichier, sur un caractère avec la valeur `Elem(0)` (qui n’est pas extraite) ou sur tout élément (qui n’est pas extrait) qui serait ignoré par [WS](../standard-library/istream-functions.md#ws). Si la fonction n’extrait aucun élément, elle appelle `Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. Dans tous les cas, il appelle `Istr.width(0)` et retourne *ISTR*.

**Note de sécurité** La chaîne terminée par le caractère null qui est extraite du flux d’entrée ne doit pas dépasser la taille de *la chaîne de la mémoire tampon*de destination. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

Le modèle de fonction :

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrait un élément, si possible, et le stocke dans *ch*. Dans le cas contraire, il appelle `is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. Dans tous les cas, elle retourne *ISTR*.

Le modèle de fonction :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

Retourne `Istr >> ( char * ) str`.

Le modèle de fonction :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

Retourne `Istr >> ( char& ) Ch`.

Le modèle de fonction :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

Retourne `Istr >> ( char * ) str`.

Le modèle de fonction :

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

Retourne `Istr >> ( char& ) Ch`.

Le modèle de fonction :

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

retourne `Istr >> val` (et convertit une référence rvalue en `Istr` en lvalue dans le processus).

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

[\<istream>](../standard-library/istream.md)
