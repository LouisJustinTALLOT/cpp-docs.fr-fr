---
title: checked_array_iterator, classe
ms.date: 03/27/2019
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
ms.openlocfilehash: 688b93902da5b4492812b4715a248db9561ec258
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379192"
---
# <a name="checkedarrayiterator-class"></a>checked_array_iterator, classe

La classe `checked_array_iterator` vous permet de transformer un tableau ou un pointeur en un itérateur vérifié. Utilisez cette classe comme wrapper (à l’aide de la fonction [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)) pour les pointeurs ou tableaux bruts comme un moyen ciblé d’exécuter des vérifications et de gérer les avertissements de pointeur non vérifié, au lieu de désactiver globalement ces avertissements. Si nécessaire, utilisez la version non vérifiée de cette classe, [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

> [!NOTE]
> Cette classe est une extension Microsoft de la bibliothèque C++ Standard. Le code implémenté à l’aide de cette fonction ne peut pas être utilisé dans les environnements de build C++ standard qui ne prennent pas en charge cette extension Microsoft. Pour savoir comment écrire du code qui ne requiert pas l'utilisation de cette classe, consultez le deuxième exemple ci-dessous.

## <a name="syntax"></a>Syntaxe

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Notes

Cette classe est définie dans l’espace de noms [stdext](../standard-library/stdext-namespace.md).

Pour plus d’informations et pour obtenir un exemple de code sur la fonctionnalité d’itérateur vérifié, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

## <a name="example"></a>Exemple

L'exemple suivant indique comment définir et utiliser un itérateur vérifié de tableau.

Si la destination n'est pas suffisamment grande pour contenir tous les éléments copiés, ce qui serait le cas si vous aviez modifié la ligne suivante :

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

à

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 4));
```

Une erreur d'exécution se produira.

```cpp
// compile with: /EHsc /W4 /MTd
#include <algorithm>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[]={0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;

   // constructor example
   checked_array_iterator<int*> checked_out_iter(b, 5);
   copy(a, a + 5, checked_out_iter);

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;
}
/* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*/
```

## <a name="example"></a>Exemple

Pour ne pas avoir besoin de la classe `checked_array_iterator` quand vous utilisez des algorithmes de bibliothèque C++ Standard, utilisez un `vector` au lieu d’un tableau alloué dynamiquement. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.

```cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    std::vector<int> v(10);
    int *arr = new int[10];
    for (int i = 0; i < 10; ++i)
    {
        v[i] = i;
        arr[i] = i;
    }

    // std::copy(v.begin(), v.end(), arr); will result in
    // warning C4996. To avoid this warning while using int *,
    // use the Microsoft extension checked_array_iterator.
    std::copy(v.begin(), v.end(),
              stdext::checked_array_iterator<int *>(arr, 10));

    // Instead of using stdext::checked_array_iterator and int *,
    // consider using std::vector to encapsulate the array. This will
    // result in no warnings, and the code will be portable.
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];
    std::copy(v.begin(), v.end(), arr2.begin());

    for (int j = 0; j < arr2.size(); ++j)
    {
        cout << " " << arr2[j];
    }
    cout << endl;

    return 0;
}
/* Output:
0 1 2 3 4 5 6 7 8 9
*/
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[checked_array_iterator](#checked_array_iterator)|Construit un `checked_array_iterator` par défaut ou un `checked_array_iterator` à partir d'un itérateur sous-jacent.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[difference_type](#difference_type)|Type qui fournit la différence entre deux objets `checked_array_iterator` se rapportant à des éléments dans le même conteneur.|
|[pointer](#pointer)|Type qui fournit un pointeur vers un élément traité par un `checked_array_iterator`.|
|[reference](#reference)|Type qui fournit une référence à un élément traité par un `checked_array_iterator`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[base](#base)|Récupère l'itérateur sous-jacent à partir de son `checked_array_iterator`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator==](#op_eq_eq)|Vérifie si deux objets `checked_array_iterator` sont égaux.|
|[!=, opérateur](#op_neq)|Vérifie si deux objets `checked_array_iterator` sont inégaux.|
|[operator<](#op_lt)|Vérifie si le `checked_array_iterator` à gauche de l'opérateur est inférieur au `checked_array_iterator` du côté droit.|
|[operator>](#op_gt)|Vérifie si le `checked_array_iterator` à gauche de l'opérateur est supérieur à l'objet `checked_array_iterator` du côté droit.|
|[operator<=](#op_lt_eq)|Vérifie si le `checked_array_iterator` à gauche de l'opérateur est inférieur ou égal au `checked_array_iterator` du côté droit.|
|[operator>=](#op_gt_eq)|Vérifie si le `checked_array_iterator` à gauche de l'opérateur est supérieur ou égal au `checked_array_iterator` du côté droit.|
|[operator*](#op_star)|Retourne l'élément traité par `checked_array_iterator`.|
|[operator->](#op_arrow)|Retourne un pointeur vers l'élément traité par le `checked_array_iterator`.|
|[operator++](#op_add_add)|Incrémente le `checked_array_iterator` à l'élément suivant.|
|[operator--](#operator--)|Décrémente le `checked_array_iterator` à l'élément précédent.|
|[operator+=](#op_add_eq)|Ajoute un décalage spécifié à un `checked_array_iterator`.|
|[operator+](#op_add)|Ajoute un décalage à un itérateur et retourne le nouvel `checked_array_iterator` qui se rapporte à l'élément inséré à la nouvelle position décalée.|
|[operator-=](#operator-_eq)|Décrémente un décalage spécifié d'un `checked_array_iterator`.|
|[operator-](#operator-)|Décrémente un décalage depuis un itérateur et retourne le nouveau `checked_array_iterator` qui traite l'élément inséré à la nouvelle position décalée.|
|[operator&#91;&#93;](#op_at)|Retourne une référence à un élément décalé d'un nombre donné de positions par rapport à l'élément auquel un `checked_array_iterator` se rapportait.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<iterator>

**Espace de noms :** stdext

## <a name="base"></a>  checked_array_iterator::base

Récupère l'itérateur sous-jacent à partir de son `checked_array_iterator`.

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_base.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main() {
   using namespace std;

   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   int* bpos;

   stdext::checked_array_iterator<int*> rpos(V1, 10);
   rpos++;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
/* Output:
The iterator underlying rpos is bpos & it points to: 1.
*/
```

## <a name="checked_array_iterator"></a>  checked_array_iterator::checked_array_iterator

Construit un `checked_array_iterator` par défaut ou un `checked_array _iterator` à partir d'un itérateur sous-jacent.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
Pointeur vers le tableau.

*size*<br/>
Taille du tableau.

*index*<br/>
(Facultatif) Un élément du tableau, pour initialiser l’itérateur.  Par défaut, l’itérateur est initialisé au niveau du premier élément du tableau.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_ctor.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   copy (a, a + 5, checked_output_iterator);
   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator2(b,5,3);
   cout << *checked_output_iterator2 << endl;
}
/* Output:
0 1 2 3 4
0 1 2 3 4
3
*/
```

## <a name="difference_type"></a>  checked_array_iterator::difference_type

Type qui fournit la différence entre deux objets `checked_array_iterator` se rapportant à des éléments dans le même conteneur.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Notes

Le type de différence entre objets `checked_array_iterator` est le même que le type de différence entre itérateurs.

Consultez [checked_array_iterator::operator[]](#op_at) pour obtenir un exemple de code.

Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

## <a name="op_eq_eq"></a>  checked_array_iterator::operator==

Vérifie si deux objets `checked_array_iterator` sont égaux.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
`checked_array_iterator` par rapport auquel vérifier l’égalité.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_opeq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="op_neq"></a>  checked_array_iterator::operator!=

Vérifie si deux objets `checked_array_iterator` sont inégaux.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
`checked_array_iterator` par rapport auquel vérifier l’inégalité.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_opneq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="op_lt"></a>  checked_array_iterator::operator&lt;

Vérifie si le `checked_array_iterator` à gauche de l'opérateur est inférieur au `checked_array_iterator` du côté droit.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
`checked_array_iterator` par rapport auquel vérifier l’inégalité.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_oplt.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is not less than checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="op_gt"></a>  checked_array_iterator::operator&gt;

Vérifie si le `checked_array_iterator` à gauche de l'opérateur est supérieur à l'objet `checked_array_iterator` du côté droit.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
`checked_array_iterator` avec lequel effectuer la comparaison.

### <a name="remarks"></a>Notes

Consultez [checked_array_iterator::operator&lt;](#op_lt) pour obtenir un exemple de code.

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_lt_eq"></a>  checked_array_iterator::operator&lt;=

Vérifie si le `checked_array_iterator` à gauche de l'opérateur est inférieur ou égal au `checked_array_iterator` du côté droit.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
`checked_array_iterator` avec lequel effectuer la comparaison.

### <a name="remarks"></a>Notes

Consultez [checked_array_iterator::operator&gt;=](#op_gt_eq) pour obtenir un exemple de code.

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_gt_eq"></a>  checked_array_iterator::operator&gt;=

Vérifie si le `checked_array_iterator` à gauche de l'opérateur est supérieur ou égal au `checked_array_iterator` du côté droit.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
`checked_array_iterator` avec lequel effectuer la comparaison.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_opgteq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is greater than or equal to checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="op_star"></a>  checked_array_iterator::operator*

Retourne l'élément traité par `checked_array_iterator`.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément ciblé par le `checked_array_iterator`.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   pair<int, int> c[1];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << endl;

    c[0].first = 10;
    c[0].second = 20;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*>::pointer p = &(*checked_output_iterator);
   checked_array_iterator<pair<int, int>*> chk_c(c, 1);
   checked_array_iterator<pair<int, int>*>::pointer p_c = &(*chk_c);

   cout << "b[0] = " << *p << endl;
   cout << "c[0].first = " << p_c->first << endl;
}
/* Output:
0
1
2
3
4
b[0] = 0
c[0].first = 10
*/
```

## <a name="op_arrow"></a>  checked_array_iterator::operator-&gt;

Retourne un pointeur vers l'élément traité par le `checked_array_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’élément ciblé par le `checked_array_iterator`.

### <a name="remarks"></a>Notes

Consultez [checked_array_iterator::pointer](#pointer) pour obtenir un exemple de code.

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_add_add"></a>  checked_array_iterator::operator++

Incrémente le `checked_array_iterator` à l'élément suivant.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>Valeur de retour

Le premier opérateur retourne le `checked_array_iterator` préincrémenté et le deuxième, l’opérateur de postincrémentation, retourne une copie du `checked_array_iterator` incrémenté.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_op_plus_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   ++checked_output_iterator;
   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
77
*/
```

## <a name="operator--"></a>  checked_array_iterator::operator--

Décrémente le `checked_array_iterator` à l'élément précédent.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>Valeur de retour

Le premier opérateur retourne le `checked_array_iterator` prédécrémenté et le deuxième, l’opérateur de postdécrémentation, retourne une copie du `checked_array_iterator` décrémenté.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_op_minus_minus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
   checked_output_iterator--;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
6
*/
```

## <a name="op_add_eq"></a>  checked_array_iterator::operator+=

Ajoute un décalage spécifié à un `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Paramètres

*_Off*<br/>
Décalage d’incrémentation de l’itérateur.

### <a name="return-value"></a>Valeur de retour

Référence vers l’élément ciblé par le `checked_array_iterator`.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_op_plus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="op_add"></a>  checked_array_iterator::operator+

Ajoute un décalage à un itérateur et retourne le nouvel `checked_array_iterator` qui se rapporte à l'élément inséré à la nouvelle position décalée.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Paramètres

*_Off*<br/>
Décalage à ajouter à `checked_array_iterator`.

### <a name="return-value"></a>Valeur de retour

`checked_array_iterator` se rapportant à l’élément de décalage.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_op_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator = checked_output_iterator + 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="operator-_eq"></a>  checked_array_iterator::operator-=

Décrémente un décalage spécifié d'un `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Paramètres

*_Off*<br/>
Décalage d’incrémentation de l’itérateur.

### <a name="return-value"></a>Valeur de retour

Référence vers l’élément ciblé par le `checked_array_iterator`.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_op_minus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
   checked_output_iterator -= 2;
   cout << *checked_output_iterator << endl;
}
/* Output:
199
3
*/
```

## <a name="operator-"></a>  checked_array_iterator::operator-

Décrémente un décalage depuis un itérateur et retourne le nouveau `checked_array_iterator` qui traite l'élément inséré à la nouvelle position décalée.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*_Off*<br/>
Décalage à décrémenter du `checked_array_iterator`.

### <a name="return-value"></a>Valeur de retour

`checked_array_iterator` se rapportant à l’élément de décalage.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="op_at"></a>  checked_array_iterator::operator[]

Retourne une référence à un élément décalé d'un nombre donné de positions par rapport à l'élément auquel un `checked_array_iterator` se rapportait.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Paramètres

*_Off*<br/>
Décalage par rapport au `checked_array_iterator` traité.

### <a name="return-value"></a>Valeur de retour

Référence au décalage de l’élément.

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// checked_array_iterators_op_diff.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   // Declare a difference type for a parameter
   stdext::checked_array_iterator<int*>::difference_type diff = 2;

   stdext::checked_array_iterator<int*> VChkIter(V1, 10);

   stdext::checked_array_iterator<int*>::reference refrpos = VChkIter [diff];

   cout << refrpos + 1 << endl;
}
/* Output:
3
*/
```

## <a name="pointer"></a>  checked_array_iterator::pointer

Type qui fournit un pointeur vers un élément traité par un `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Notes

Consultez [checked_array_iterator::operator*](#op_star) pour obtenir un exemple de code.

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="reference"></a>  checked_array_iterator::reference

Type qui fournit une référence à un élément traité par un `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Notes

Consultez [checked_array_iterator::operator[]](#op_at) pour obtenir un exemple de code.

Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
