---
title: '&lt;unordered_set&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 59a7154ed46ac788516bc9f42c3385ec8f07dcf1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890730"
---
# <a name="ltunordered_setgt-operators"></a>&lt;unordered_set&gt;, opérateurs

## <a name="op_neq"></a>opérateur ! =

Teste si l’objet [unordered_set](../standard-library/unordered-set-class.md) situé à gauche de l’opérateur n’est pas égal à l’objet unordered_set situé à droite.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `unordered_set`.

\ *droit*
Objet de type `unordered_set`.

### <a name="return-value"></a>Valeur de retour

**true** si les unordered_sets ne sont pas égaux ; **false** s’ils sont égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets unordered_set n’est pas affectée par l’ordre arbitraire dans lequel ils stockent leurs éléments. Deux objets unordered_set sont égaux s’ils ont le même nombre d’éléments et que les éléments d’un conteneur constituent une permutation des éléments de l’autre conteneur. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// unordered_set_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

**Output:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq"></a>opérateur = =

Teste si l’objet [unordered_set](../standard-library/unordered-set-class.md) situé à gauche de l’opérateur est égal à l’objet unordered_set situé à droite.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `unordered_set`.

\ *droit*
Objet de type `unordered_set`.

### <a name="return-value"></a>Valeur de retour

**true** si les unordered_sets sont égales ; **false** si elles ne sont pas égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets unordered_set n’est pas affectée par l’ordre arbitraire dans lequel ils stockent leurs éléments. Deux objets unordered_set sont égaux s’ils ont le même nombre d’éléments et que les éléments d’un conteneur constituent une permutation des éléments de l’autre conteneur. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// unordered_set_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```

## <a name="op_neq_unordered_multiset"></a>opérateur ! =

Teste si l’objet [unordered_multiset](../standard-library/unordered-multiset-class.md) situé à gauche de l’opérateur n’est pas égal à l’objet unordered_multiset situé à droite.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `unordered_multiset`.

\ *droit*
Objet de type `unordered_multiset`.

### <a name="return-value"></a>Valeur de retour

**true** si les unordered_multisets ne sont pas égaux ; **false** s’ils sont égaux.

### <a name="remarks"></a>Notes

La comparaison entre les objets unordered_multiset n’est pas affectée par l’ordre arbitraire dans lequel ils stockent leurs éléments. Deux objets unordered_multiset sont égaux s’ils ont le même nombre d’éléments et que les éléments d’un conteneur constituent une permutation des éléments de l’autre conteneur. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// unordered_multiset_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

```Output
c1 != c2: true
c1 != c3: false
c2 != c3: true
```

## <a name="op_eq_eq_unordered_multiset"></a>opérateur = =

Teste si l’objet [unordered_multiset](../standard-library/unordered-multiset-class.md) situé à gauche de l’opérateur est égal à l’objet unordered_multiset situé à droite.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Objet de type `unordered_multiset`.

\ *droit*
Objet de type `unordered_multiset`.

### <a name="return-value"></a>Valeur de retour

**true** si les unordered_multisets sont égales ; **false** si elles ne sont pas égales.

### <a name="remarks"></a>Notes

La comparaison entre les objets unordered_multiset n’est pas affectée par l’ordre arbitraire dans lequel ils stockent leurs éléments. Deux objets unordered_multiset sont égaux s’ils ont le même nombre d’éléments et que les éléments d’un conteneur constituent une permutation des éléments de l’autre conteneur. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// unordered_multiset_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```
