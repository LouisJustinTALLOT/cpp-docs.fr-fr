---
title: tuple_element, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- utility/std::tuple_element
dev_langs:
- C++
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b893b6b8c32be7bcd43acd4804694d997918177
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234253"
---
# <a name="tupleelement-class"></a>tuple_element, classe

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

*Index*<br/>
Index de l’élément désigné.

*Tuple*<br/>
Type du tuple.

*Elem*<br/>
Type d’un élément de tableau.

*Taille*<br/>
Taille du tableau.

*T1*<br/>
Le type du premier élément dans une paire.

*T2*<br/>
Le type du second élément d’une paire.

## <a name="remarks"></a>Notes

La classe de modèle `tuple_element` possède un typedef imbriqué `type` qui est un synonyme pour le type de l’index *Index* du type de tuple *Tuple*.

Le typedef `tuple_element_t` est un alias pratique pour `tuple_element<Index, Tuple>::type`.

La spécialisation de classe de modèle pour les tableaux fournit une interface vers un `array` en tant que tuple de `Size` éléments, chacun d’entre eux ayant le même type. Chaque spécialisation a un typedef imbriqué `type` qui est un synonyme pour le type de la *Index* élément de la `array`, avec des qualifications const-volatiles conservées.

Les spécialisations de modèle pour les types `pair` fournissent chacune un typedef de membre unique, `type`, qui est un synonyme du type de l’élément à la position spécifiée dans la paire, avec des qualifications const et/ou volatiles conservées. Le typedef `tuple_element_t` est un alias pratique pour `tuple_element<N, pair<T1, T2>>::type`.

Utilisez le [get, fonction &lt;utilitaire&gt; ](../standard-library/utility-functions.md#get) pour retourner l’élément à une position spécifiée, ou d’un type spécifié.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<tuple>

**En-tête :** \<array> (pour la spécialisation de tableau)

**En-tête :** \<utilitaire > (pour les spécialisations de paire)

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[tuple ](../standard-library/tuple-class.md)<br/>
