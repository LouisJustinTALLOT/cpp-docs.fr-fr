---
description: 'En savoir plus sur les fonctions suivantes : &lt; ostream &gt;'
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
ms.openlocfilehash: fb99b713db4c29fe42b45858588181536aec4f5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280519"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt;, fonctions

Il s’agit des fonctions de modèle globales définies dans &lt; ostream &gt; . Pour les fonctions membres, consultez la documentation relative à la [classe basic_ostream](basic-ostream-class.md) .

[Endl](#endl)\
[fins](#ends)\
[postconsommation](#flush)\
[swap](#swap)

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
Caractéristiques de caractère.

### <a name="return-value"></a>Valeur renvoyée

Objet de type **basic_ostream**.

### <a name="remarks"></a>Notes

Le manipulateur appelle *OSTR*. [put](../standard-library/basic-ostream-class.md#put)(*OSTR*.[ Widening](../standard-library/basic-ios-class.md#widen)(' \n')), puis appelle *OSTR*. [vidage](../standard-library/basic-ostream-class.md#flush). Elle retourne *OSTR*.

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
Caractéristiques de caractère.

### <a name="return-value"></a>Valeur renvoyée

Objet de type `basic_ostream`.

### <a name="remarks"></a>Notes

Le manipulateur appelle *OSTR*. [put](../standard-library/basic-ostream-class.md#put)(*elem*(' \ 0 ')). Elle retourne *OSTR*.

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
Caractéristiques de caractère.

### <a name="return-value"></a>Valeur renvoyée

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
Caractéristiques de caractère.

*gauche*\
Référence lvalue à un objet `basic_ostream`.

*Oui*\
Référence lvalue à un objet `basic_ostream`.

### <a name="remarks"></a>Notes

La fonction de modèle `swap` exécute `left.swap(right)`.

## <a name="see-also"></a>Voir aussi

[\<ostream>](../standard-library/ostream.md)
