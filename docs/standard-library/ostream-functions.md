---
title: '&lt;ostream&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: d30ad23956c978ee47ef447463a0d5422a94d4b9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962320"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt;, fonctions

Ce sont les fonctions de modèle global définies dans &lt;ostream&gt;. Pour les fonctions membres, consultez la [basic_ostream, classe](basic-ostream-class.md) documentation.

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

*Elem* le type d’élément.

*Ostr* un objet de type **basic_ostream**.

*TR* traits de caractère.

### <a name="return-value"></a>Valeur de retour

Un objet de type **basic_ostream**.

### <a name="remarks"></a>Notes

Le manipulateur appelle *Ostr*.[ Put](../standard-library/basic-ostream-class.md#put)(*Ostr*.[ élargir](../standard-library/basic-ios-class.md#widen)('\n')), puis appelle *Ostr*.[ vider](../standard-library/basic-ostream-class.md#flush). Elle retourne *Ostr*.

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

## <a name="ends"></a>ends

Met fin à une chaîne.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Paramètres

*Elem* le type d’élément.

*Ostr* un objet de type `basic_ostream`.

*TR* traits de caractère.

### <a name="return-value"></a>Valeur de retour

Objet de type `basic_ostream`.

### <a name="remarks"></a>Notes

Le manipulateur appelle *Ostr*.[ Put](../standard-library/basic-ostream-class.md#put)(*Elem*('\0')). Elle retourne *Ostr*.

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

*Elem* le type d’élément.

*Ostr* un objet de type `basic_ostream`.

*TR* traits de caractère.

### <a name="return-value"></a>Valeur de retour

Objet de type `basic_ostream`.

### <a name="remarks"></a>Notes

Le manipulateur appelle *Ostr*.[ vider](../standard-library/basic-ostream-class.md#flush). Elle retourne *Ostr*.

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

*Elem* le type d’élément.

*TR* traits de caractère.

*gauche* référence lvalue à un `basic_ostream` objet.

*droit* référence lvalue à un `basic_ostream` objet.

### <a name="remarks"></a>Notes

La fonction de modèle `swap` exécute `left.swap(right)`.

## <a name="see-also"></a>Voir aussi

[\<ostream>](../standard-library/ostream.md)
