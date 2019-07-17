---
title: binder2nd, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder2nd
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
ms.openlocfilehash: 5f59887e6c9d2965a6c8680f17a40c5bd93869c0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243357"
---
# <a name="binder2nd-class"></a>binder2nd, classe

Classe de modèle fournissant un constructeur qui convertit un objet de fonction binaire en objet de fonction unaire en liant le second argument de la fonction binaire à une valeur spécifiée. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;
};
```

### <a name="parameters"></a>Paramètres

*Func*\
Objet de fonction binaire à convertir en un objet de fonction unaire.

*Oui*\
Valeur à laquelle le deuxième argument de l’objet de fonction binaire doit être lié.

*Gauche*\
Valeur de l’argument que l’objet binaire adapté compare à la valeur fixe du deuxième argument.

## <a name="return-value"></a>Valeur de retour

L’objet de fonction unaire qui résulte de la liaison le deuxième argument de l’objet de fonction binaire à la valeur *droit*.

## <a name="remarks"></a>Notes

La classe de modèle stocke une copie d’un objet de fonction binaire _ *Func* dans `op`et une copie de *droit* dans `value`. Elle définit sa fonction membre `operator()` comme retournant **op**(`left`, **valeur**).

Si `Func` est un objet de type `Operation` et c est une constante, puis [bind2nd](../standard-library/functional-functions.md#bind2nd) (`Func`, `c`) est équivalente à la `binder2nd` constructeur de classe `binder2nd` \<  **Opération**> (`Func`, `c`) et plus pratique.

## <a name="example"></a>Exemple

```cpp
// functional_binder2nd.cpp
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
        binder2nd<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare using binder1st fixing 1st argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder1st<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
