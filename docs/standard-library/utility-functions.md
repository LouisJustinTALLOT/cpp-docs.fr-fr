---
title: '&lt;utility&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
caps.latest.revision: 7
manager: ghogen
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.openlocfilehash: 20599ee24dbf8db033a91767ece30160c05cc8d8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ltutilitygt-functions"></a>&lt;utility&gt;, fonctions

||||
|-|-|-|
|[exchange](#exchange)|[forward](#forward)|[get, fonction &lt;utility&gt;](#get)|
|[make_pair](#make_pair)|[move](#move)|[swap](#swap)|

## <a name="exchange"></a>  exchange

**(C++14)** Assigne une nouvelle valeur à un objet et retourne son ancienne valeur.

```cpp
template <class T, class Other = T>
T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Paramètres

`val` Objet qui reçoit la valeur de new_val.

`new_val` Objet dont la valeur est copiée ou déplacée dans val.

### <a name="remarks"></a>Notes

Pour les types complexes, la fonction `exchange` évite d'avoir à copier l'ancienne valeur quand un constructeur move est disponible et à copier la nouvelle valeur si l'objet est temporaire ou est déplacé. De plus, elle accepte n'importe quel type comme nouvelle valeur, en utilisant l'un des opérateurs d'assignation de conversion disponibles. La fonction exchange est différente de [std::swap](../standard-library/algorithm-functions.md#swap), car l’argument de gauche n’est pas déplacé ni copié vers l’argument de droite.

### <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser `exchange`. En réalité, `exchange` est particulièrement utile avec les objets volumineux qui sont coûteux à copier :

```cpp
#include <utility>
#include <iostream>

using namespace std;

struct C
{
   int i;
   //...
};

int main()
{
   // Use brace initialization
   C c1{ 1 };
   C c2{ 2 };
   C result = exchange(c1, c2);
   cout << "The old value of c1 is: " << result.i << endl;
   cout << "The new value of c1 after exchange is: " << c1.i << endl;

   return 0;
}
```

```Output
The old value of c1 is: 1
The new value of c1 after exchange is: 2
```

## <a name="forward"></a>  forward

Convertit de manière conditionnelle son argument en une référence rvalue, si l’argument est une rvalue ou une référence rvalue. Cette opération restaure la nature rvalue d’un argument pour le transfert parfait.

```cpp
template <class Type>    // accepts lvalues
constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Type`|Type de la valeur passée dans `Arg`, qui peut être différent du type de `Arg`. Généralement déterminé par un argument template de la fonction de transfert.|
|`Arg`|Argument sur lequel effectuer un cast.|

### <a name="return-value"></a>Valeur de retour

Retourne une référence rvalue à `Arg` si la valeur passée dans `Arg` était à l'origine une rvalue ou une référence rvalue ; sinon, retourne `Arg` sans modifier son type.

### <a name="remarks"></a>Notes

Vous devez spécifier un argument template explicite pour appeler `forward`.

`forward` ne transfère pas son argument. En revanche, en convertissant son argument de manière conditionnelle en une référence rvalue, s'il s'agissait à l'origine d'une rvalue ou d'une référence rvalue, `forward` permet au compilateur d'effectuer une résolution de surcharge en connaissant le type d'origine de l'argument transféré. Le type apparent de l’argument d’une fonction de transfert peut être différent de son type d’origine ; par exemple, lorsqu’une rvalue est utilisée en tant qu’argument d’une fonction et qu’elle est liée à un nom de paramètre. Le fait d’avoir un nom en fait une lvalue, même si la valeur existe en tant que rvalue. `forward` restaure la nature rvalue de l’argument.

La restauration de la nature rvalue de la valeur d’origine d’un argument dans le but d’effectuer une résolution de surcharge se nomme *transfert parfait*. Le transfert parfait permet à une fonction de modèle d’accepter un argument de n’importe quel type référence et de restaurer sa nature rvalue si nécessaire, pour une résolution de surcharge appropriée. Le transfert parfait permet de préserver la sémantique de déplacement des rvalue et évite d’avoir à fournir des surcharges pour les fonctions qui varient uniquement par le type référence de leurs arguments.

## <a name="get"></a>  get

Obtient un élément d’un objet `pair` , par position d’index ou par type.

```cpp
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr tuple_element_t<Index, pair<T1, T2>>&
get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr const tuple_element_t<Index, pair<T1, T2>>&
get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr tuple_element_t<Index, pair<T1, T2>>&&
get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```

### <a name="parameters"></a>Paramètres

`Index` L’index de base 0 de l’élément désigné.

`T1` Le type du premier élément de la paire.

`T2` Le type du deuxième élément de la paire.

`pr` La paire de sélectionner à partir de.

### <a name="remarks"></a>Notes

Chaque fonction de modèle retourne une référence à un élément de son `pair` argument.

Pour les surcharges indexées, si la valeur de `Index` est 0, les fonctions retournent `pr.first` ; si la valeur de `Index` est 1, les fonctions retournent `pr.second`. Le type `RI` est le type de l’élément retourné.

Pour les surcharges qui n’ont pas de paramètre d’index, l’élément à retourner est déduit par l’argument du type. L’appel de `get<T>(Tuple)` génère une erreur de compilation si `pr` contient plus ou moins qu’un élément de type T.

### <a name="example"></a>Exemple

```cpp
#include <utility>
#include <iostream>
using namespace std;
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;

    /*
    Output:
    9 3.14
    1 0.27
    */

}
```

## <a name="make_pair"></a>  make_pair

Fonction de modèle que vous pouvez utiliser pour construire des objets de type `pair`, dont les types de composants sont sélectionnés automatiquement en fonction des types de données qui sont transmis comme paramètres.

```cpp
template <class T, class U>
pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
pair<T, U> make_pair(T&& Val1, U&& Val2);
```

### <a name="parameters"></a>Paramètres

`Val1` Valeur qui initialise le premier élément du `pair`.

`Val2` Valeur qui initialise le deuxième élément de `pair`.

### <a name="return-value"></a>Valeur de retour

Objet paire construit : `pair`< `T`, `U`>( `Val1`, `Val2`).

### <a name="remarks"></a>Notes

`make_pair` convertit un objet de type [reference_wrapper (classe)](../standard-library/reference-wrapper-class.md) en types référence et convertit des fonctions et des tableaux en décomposition en pointeurs.

Dans l'objet `pair` retourné, `T` est déterminé comme suit :

- Si le type d'entrée `T` a pour valeur `reference_wrapper<X>`, le type retourné `T` a pour valeur `X&`.

- Sinon, le type retourné `T` a pour valeur `decay<T>::type`. Si la [classe decay](../standard-library/decay-class.md) n’est pas prise en charge, le type retourné `T` est identique au type d’entrée `T`.

Le type retourné `U` est déterminé de façon similaire à partir du type d'entrée `U`.

Un avantage de `make_pair` est que les types d'objets stockés sont déterminés automatiquement par le compilateur et ne sont pas tenus d'être spécifiés explicitement. N'utilisez pas d'arguments template explicites, tels que `make_pair<int, int>(1, 2)`, lorsque vous utilisez `make_pair`, car cela est inutilement détaillé et ajoute des problèmes complexes de référence rvalue susceptibles de provoquer un échec de compilation. Pour cet exemple, la syntaxe correcte serait `make_pair(1, 2)`.

La fonction d'assistance `make_pair` permet également de transmettre deux valeurs à une fonction qui requiert une paire en tant que paramètre d'entrée.

### <a name="example"></a>Exemple

Pour obtenir un exemple illustrant comment utiliser la fonction d’assistance `make_pair` pour déclarer et initialiser une paire, consultez [pair, structure](../standard-library/pair-structure.md).

## <a name="move"></a>  move

Effectue un cast non conditionnel de son argument en une référence rvalue, et signale par là-même qu’elle peut être déplacée si son type prend en charge le mouvement.

```cpp
template <class Type>
constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Type`|Type déduit du type de l'argument transmis dans `Arg`, avec les règles de réduction de référence.|
|`Arg`|Argument sur lequel effectuer un cast. Bien que le type de `Arg` semble être spécifié en tant que référence rvalue, `move` accepte également les arguments lvalue, car les références lvalue peuvent être liées aux références rvalue.|

### <a name="return-value"></a>Valeur de retour

`Arg` en tant que référence rvalue, que son type soit un type référence ou non.

### <a name="remarks"></a>Notes

L'argument template `Type` n'est pas conçu pour être explicitement spécifié, mais pour être déduit du type de la valeur transmise dans `Arg`. Le type de `Type` est ajusté plus en détail en fonction des règles de réduction de référence.

`move` ne déplace pas son argument. Au lieu de cela, en effectuant un cast non conditionnel de son argument (qui peut être une lvalue) en une référence rvalue, elle permet au compilateur de déplacer ultérieurement, plutôt que de copier, la valeur transmise dans `Arg` si son type prend en charge le mouvement. Si son type ne prend pas en charge le mouvement, il est copié à la place.

Si la valeur transmise dans `Arg` est une lvalue (autrement dit, si elle a un nom ou que son adresse peut être prise), elle est invalidée lorsque le déplacement se produit. Ne faites pas référence à la valeur transmise dans `Arg` par son nom ou adresse après qu'elle a été déplacée.

## <a name="swap"></a>  swap

Échange les éléments de deux objets [pair (structure)](../standard-library/pair-structure.md).

```cpp
template <class T, class U>
void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`left`|Objet de type `pair`.|
|`right`|Objet de type `pair`.|

### <a name="remarks"></a>Notes

Un avantage de `swap` est que les types d'objets stockés sont déterminés automatiquement par le compilateur et ne sont pas tenus d'être spécifiés explicitement. N'utilisez pas d'arguments template explicites, tels que `swap<int, int>(1, 2)`, lorsque vous utilisez `swap`, car cela est inutilement détaillé et ajoute des problèmes complexes de référence rvalue susceptibles de provoquer un échec de compilation.

## <a name="see-also"></a>Voir aussi

[\<utility>](../standard-library/utility.md)<br/>
