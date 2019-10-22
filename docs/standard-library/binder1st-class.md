---
title: binder1st, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder1st
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
ms.openlocfilehash: 15b704134d47b7bf7d8857bf380c756b0b03a1b0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688388"
---
# <a name="binder1st-class"></a>binder1st, classe

Modèle de classe fournissant un constructeur qui convertit un objet de fonction binaire en objet de fonction unaire en liant le premier argument de la fonction binaire à une valeur spécifiée. Déconseillé dans C++ 11 au profit de [Bind](functional-functions.md#bind)et supprimé en c++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& binary_fn,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>Paramètres

*binary_fn* \
Objet de fonction binaire à convertir en un objet de fonction unaire.

\ *gauche*
Valeur à laquelle le premier argument de l’objet de fonction binaire doit être lié.

\ *droit*
Valeur de l’argument que l’objet binaire adapté compare à la valeur fixe du deuxième argument.

## <a name="return-value"></a>Valeur de retour

Objet de fonction unaire qui résulte de la liaison du premier argument de l’objet de fonction binaire à la valeur *restante*.

## <a name="remarks"></a>Notes

Le modèle de classe stocke une copie d’un objet de fonction binaire *binary_fn* dans `op`, et une copie de *Left* dans `value`. Elle définit sa fonction membre `operator()` comme retournant `op(value, right)`.

Si *binary_fn* est un objet de type `Operation` et que `c` est une constante, `bind1st(binary_fn, c)` est un équivalent plus pratique de `binder1st<Operation>(binary_fn, c)`. Pour plus d’informations, consultez [bind1st](../standard-library/functional-functions.md#bind1st).

## <a name="example"></a>Exemple

```cpp
// functional_binder1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(),
        binder1st<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare use of binder2nd fixing 2nd argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder2nd<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
