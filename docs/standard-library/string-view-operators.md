---
title: '&lt;&gt;opérateurs string_view'
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: b0761c1af7b2ed9f34917d2e4165561b357f0a30
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833216"
---
# <a name="ltstring_viewgt-operators"></a>&lt;&gt;opérateurs string_view

Utilisez ces opérateurs pour comparer deux objets string_view, ou un string_view et un autre objet String (par exemple [std :: String](basic-string-class.md)ou **char \* **) pour lequel une conversion implicite est fournie.

[opérateur ! =](#op_neq)\
[and&gt;](#op_gt)\
[and&gt;=](#op_gt_eq)\
[and&lt;](#op_lt)\
[and&lt;&lt;](#op_lt_lt)\
[and&lt;=](#op_lt_eq)\
[opérateur = =](#op_eq_eq)\
[«», opérateur](#op_sv)

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

*Oui*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’objet situé à gauche de l’opérateur n’est pas vue lexicographique égal à l’objet situé à droite ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Une conversion implicite doit exister de *convertible_string_type* au string_view de l’autre côté.

La comparaison est basée sur une comparaison lexicographique par paire des séquences de caractères. S’ils ont le même nombre d’éléments et que les éléments sont tous égaux, les deux objets sont égaux. Sinon, elles sont inégales.

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si l’objet situé à gauche de l’opérateur est égal à l’objet situé à droite.

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

*Oui*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’objet situé à gauche de l’opérateur est vue lexicographique égal à l’objet situé à droite ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Une conversion implicite doit exister de *convertible_string_type* au string_view de l’autre côté.

La comparaison est basée sur une comparaison lexicographique par paire des séquences de caractères. S’ils ont le même nombre d’éléments et que les éléments sont tous égaux, les deux objets sont égaux.

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

Teste si l’objet situé à gauche de l’opérateur est inférieur à l’objet situé à droite sidestring_view

```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

*Oui*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’objet situé à gauche de l’opérateur est vue lexicographique inférieur à l’objet situé à droite ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Une conversion implicite doit exister de *convertible_string_type* au string_view de l’autre côté.

La comparaison est basée sur une comparaison lexicographique par paire des séquences de caractères. Lorsque la première paire inégale de caractères est rencontrée, le résultat de cette comparaison est retourné. Si aucun caractère inégal n’est trouvé, mais qu’une séquence est plus petite, la séquence la plus petite est inférieure à la plus longue. En d’autres termes, « cat » est inférieur à « chats ».

### <a name="example"></a>Exemple

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> and&lt;=

Teste si l’objet situé à gauche de l’opérateur est inférieur ou égal à l’objet situé à droite.

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

*Oui*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’objet situé à gauche de l’opérateur est vue lexicographique inférieur ou égal à l’objet situé à droite ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Consultez [Operator &lt; ](#op_lt).

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> and&lt;&lt;

Écrit un string_view dans un flux de sortie.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Paramètres

*OSTR*\
flux de sortie dans lequel l’écriture est effectuée.

*Str*\
String_view à entrer dans un flux de sortie.

### <a name="return-value"></a>Valeur renvoyée

flux de sortie dans lequel l’écriture est effectuée.

### <a name="remarks"></a>Notes

Utilisez cet opérateur pour insérer le contenu d’un string_view dans un flux de sortie, par exemple à l’aide de [std :: cout](iostream.md#cout).

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

Teste si l’objet situé à gauche de l’opérateur est supérieur à l’objet situé à droite.

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

*Oui*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’objet situé à gauche de l’opérateur est vue lexicographique supérieur à l’objet string_view situé à droite ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Consultez [Operator &lt; ](#op_lt).

## <a name="operatorgt"></a><a name="op_gt_eq"></a> and&gt;=

Teste si l’objet situé à gauche de l’opérateur est supérieur ou égal à l’objet situé à droite.

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

*Oui*\
Tout type de chaîne convertible ou objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’objet situé à gauche de l’opérateur est vue lexicographique supérieur ou égal à l’objet situé à droite ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Consultez [Operator &lt; ](#op_lt).

## <a name="operator-sv-string_view-literal"></a><a name="op_sv"></a> opérateur «» (string_view littéral)

Construit un string_view à partir d’un littéral de chaîne. Requiert un espace de noms `std::literals::string_view_literals` .

### <a name="example"></a>Exemple

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>Voir aussi

[\<string_view>](../standard-library/string-view.md)
