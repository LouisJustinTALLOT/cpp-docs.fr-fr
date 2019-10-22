---
title: tuple_element, classe
ms.date: 11/04/2016
f1_keywords:
- utility/std::tuple_element
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
ms.openlocfilehash: 21efed39fdaabe0f95f83e9dc5cdfcc508a147c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684462"
---
# <a name="tuple_element-class"></a>tuple_element, classe

Encapsule un élément `tuple` . Les spécialisations encapsulent des éléments `array` et des éléments `pair`.

## <a name="syntax"></a>Syntaxe

```cpp
// CLASS tuple_element (find element by index)
template <size_t Index, class Tuple>
   struct tuple_element;

// tuple_element for const
template <size_t Index, class Tuple>
   struct tuple_element<Index, const Tuple>;

// tuple_element for volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, volatile Tuple>;

// tuple_element for const volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, const volatile Tuple>;

// Helper typedef
template <size_t Index, class Tuple>
   using tuple_element_t = typename tuple_element<Index, Tuple>::type;

// Specialization for arrays
template <size_t Index, class Elem, size_t Size>
   struct tuple_element<Index, array<Elem, Size>>;

// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```

### <a name="parameters"></a>Paramètres

@No__t_1 d' *index*
Index de l’élément désigné.

@No__t_1 de *Tuple*
Type du tuple.

@No__t_1 *elem*
Type d’un élément de tableau.

*Taille* \
Taille du tableau.

@No__t_1 *T1*
Type du premier élément d’une paire.

*T2* \
Le type du second élément d’une paire.

## <a name="remarks"></a>Notes

Le modèle de classe `tuple_element` a un typedef imbriqué `type` qui est un synonyme du type à l' *index* de l’index du *Tuple*du type de Tuple.

Le typedef `tuple_element_t` est un alias pratique pour `tuple_element<Index, Tuple>::type`.

La spécialisation de modèle de classe pour les tableaux fournit une interface à un `array` en tant que tuple d’éléments `Size`, chacun d’entre eux ayant le même type. Chaque spécialisation a un typedef imbriqué `type` qui est un synonyme du type de l’élément *index* de l' `array`, avec des qualifications const-volatiles conservées.

Les spécialisations de modèle pour les types `pair` fournissent chacune un typedef de membre unique, `type`, qui est un synonyme du type de l’élément à la position spécifiée dans la paire, avec des qualifications const et/ou volatiles conservées. Le typedef `tuple_element_t` est un alias pratique pour `tuple_element<N, pair<T1, T2>>::type`.

Utilisez la [fonction obtenir &lt;utility &gt;](../standard-library/utility-functions.md#get) pour retourner l’élément à une position spécifiée ou d’un type spécifié.

## <a name="example"></a>Exemple

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;
typedef tuple<int, double, string> MyTuple;

int main() {
    MyTuple c0{ 0, 1.5, "Tail" };

    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type

    cout << val << " " << val2 << " " << val3 << endl;
}
```

```Output
0 1.5 Tail
```

## <a name="example"></a>Exemple

```cpp
#include <array>
#include <iostream>

using namespace std;
typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    for (const auto& e : c0)
    {
        cout << e << " ";
    }
    cout << endl;

    // display first element "0"
    tuple_element<0, MyArray>::type val = c0.front();
    cout << val << endl;
}
```

```Output
0 1 2 3
0
```

## <a name="example"></a>Exemple

```cpp
#include <utility>
#include <iostream>

using namespace std;

typedef pair<int, double> MyPair;
int main() {
    MyPair c0(0, 1.333);

    // display contents "0 1"
    cout << get<0>(c0) << " ";
    cout << get<1>(c0) << endl;

    // display first element "0 " by index
    tuple_element<0, MyPair>::type val = get<0>(c0);
    cout << val << " ";

    // display second element by type
    tuple_element<1, MyPair>::type val2 = get<double>(c0);
    cout << val2 << endl;
}
```

```Output
0 1.333
0 1.333
```

## <a name="requirements"></a>spécifications

**En-tête :** \<tuple>

**En-tête :** \<array> (pour la spécialisation de tableau)

**En-tête :** \<utility > (pour les spécialisations de paire)

**Espace de noms :** std
