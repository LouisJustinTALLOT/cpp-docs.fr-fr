---
title: '&lt;ostream&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 8d93e46b0323058d93c6d0bd8c1ee566998aef61
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447195"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt;, fonctions

Il s’agit des fonctions de modèle globales&gt;définies dans &lt;ostream. Pour les fonctions membres, consultez la documentation de la [classe basic_ostream](basic-ostream-class.md) .

||||
|-|-|-|
|[endl](#endl)|[ends](#ends)|[flush](#flush)|
|[swap](#swap)|

## <a name="endl"></a>endl

Met fin à une ligne et vide la mémoire tampon.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Paramètres

*Elem*\
Type de l’élément.

*OSTR*\
Objet de type **basic_ostream**.

*TR*\
Caractéristiques du caractère.

### <a name="return-value"></a>Valeur de retour

Objet de type **basic_ostream**.

### <a name="remarks"></a>Notes

Le manipulateur appelle *OSTR*. [mettre](../standard-library/basic-ostream-class.md#put) (*OSTR*. [élargissement](../standard-library/basic-ios-class.md#widen) (' \n')), puis appelle *OSTR*. [vidage](../standard-library/basic-ostream-class.md#flush). Elle retourne *OSTR*.

### <a name="example"></a>Exemple

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>extrémités

Met fin à une chaîne.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Paramètres

*Elem*\
Type de l’élément.

*OSTR*\
Objet de type `basic_ostream`.

*TR*\
Caractéristiques du caractère.

### <a name="return-value"></a>Valeur de retour

Objet de type `basic_ostream`.

### <a name="remarks"></a>Notes

Le manipulateur appelle *OSTR*. [mettre](../standard-library/basic-ostream-class.md#put) (*Elem*(' \ 0 ')). Elle retourne *OSTR*.

### <a name="example"></a>Exemple

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>flush

Vide la mémoire tampon.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Paramètres

*Elem*\
Type de l’élément.

*OSTR*\
Objet de type `basic_ostream`.

*TR*\
Caractéristiques du caractère.

### <a name="return-value"></a>Valeur de retour

Objet de type `basic_ostream`.

### <a name="remarks"></a>Notes

Le manipulateur appelle *OSTR*. [vidage](../standard-library/basic-ostream-class.md#flush). Elle retourne *OSTR*.

### <a name="example"></a>Exemple

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>swap

Échange les valeurs de deux objets `basic_ostream`.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Paramètres

*Elem*\
Type de l’élément.

*TR*\
Caractéristiques du caractère.

*gauche*\
Référence lvalue à un objet `basic_ostream`.

*Oui*\
Référence lvalue à un objet `basic_ostream`.

### <a name="remarks"></a>Notes

La fonction de modèle `swap` exécute `left.swap(right)`.

## <a name="see-also"></a>Voir aussi

[\<ostream>](../standard-library/ostream.md)
