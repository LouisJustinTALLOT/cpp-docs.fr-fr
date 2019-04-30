---
title: '&lt;string_view&gt; opérateurs'
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
ms.openlocfilehash: 1fbb7faf7d6fc92a053c0f4d47575c5c53c7968e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346917"
---
# <a name="ltstringviewgt-operators"></a>&lt;string_view&gt; opérateurs

Ces opérateurs permettent de comparer deux objets de string_view, ou un string_view et un autre objet de chaîne (par exemple [std::string](basic-string-class.md), ou **char\***) pour lequel une conversion implicite est fournie. 

||||
|-|-|-|
|[!=, opérateur](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|[opérateur « sv »](#op_sv)|

## <a name="op_neq"></a> operator!=

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

*left*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

*right*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet sur le côté gauche de l’opérateur n’est pas égal à l’objet sur le côté droit ; sinon de point de vue lexicographique **false**.

### <a name="remarks"></a>Notes

Une conversion implicite doit exister à partir de *convertible_string_type* à la string_view de l’autre côté. 

La comparaison est basée sur un par paire comparaison lexicographique des séquences de caractères. S’ils ont le même nombre d’éléments et les éléments sont toujours égaux, les deux objets sont égaux. Sinon, elles sont inégales.

## <a name="op_eq_eq"></a> operator==

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

*left*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

*right*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet sur le côté gauche de l’opérateur est égal à l’objet sur le côté droit ; sinon de point de vue lexicographique **false**.

### <a name="remarks"></a>Notes

Une conversion implicite doit exister à partir de *convertible_string_type* à la string_view de l’autre côté. 

La comparaison est basée sur un par paire comparaison lexicographique des séquences de caractères. S’ils ont le même nombre d’éléments et les éléments sont toujours égaux, les deux objets sont égaux.


## <a name="op_lt"></a>, opérateur&lt;

Teste si l’objet sur le côté gauche de l’opérateur est inférieur à l’objet sur la droite sidestring_view
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

*left*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

*right*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet sur le côté gauche de l’opérateur est inférieur point de vue lexicographique à l’objet sur le côté droit ; sinon **false**.

### <a name="remarks"></a>Notes

Une conversion implicite doit exister à partir de *convertible_string_type* à la string_view de l’autre côté. 

La comparaison est basée sur un par paire comparaison lexicographique des séquences de caractères. Lorsque la première paire inégale des caractères est rencontrée, le résultat de cette comparaison est retourné. Si aucun des caractères inégaux ne sont trouvés, mais une seule séquence est plus courte, la séquence la plus courte est inférieure à la plus longue. En d’autres termes, « cat » est inférieure à « chats ».

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

## <a name="op_lt_eq"></a> Opérateur&lt;=

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

*left*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

*right*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet sur le côté gauche de l’opérateur est lexicographiquement inférieur ou égal à l’objet situé à droite, sinon **false**.

### <a name="remarks"></a>Notes

Consultez [opérateur&lt;](#op_lt).

## <a name="op_lt_lt"></a> Opérateur&lt;&lt;

Écrit un string_view dans un flux de sortie.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Paramètres

*Ostr*<br/>
un flux de sortie en cours d’écriture.

*Str*<br/>
String_view à entrer dans un flux de sortie.

### <a name="return-value"></a>Valeur de retour

un flux de sortie en cours d’écriture.

### <a name="remarks"></a>Notes

Utilisez cet opérateur pour insérer le contenu d’un string_view dans un flux de sortie, par exemple à l’aide de [std::cout](iostream.md#cout).

## <a name="op_gt"></a>, opérateur&gt;

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

*left*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

*right*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet sur le côté gauche de l’opérateur est supérieur à l’objet de string_view sur le côté droit ; sinon de point de vue lexicographique **false**.

### <a name="remarks"></a>Notes

Consultez [opérateur&lt;](#op_lt).

## <a name="op_gt_eq"></a> Opérateur&gt;=

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

*left*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

*right*<br/>
N’importe quel type de chaîne convertibles ou un objet de type `basic_string_view` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet sur le côté gauche de l’opérateur est le point de vue lexicographique supérieur ou égal à l’objet sur le côté droit ; sinon **false**.

### <a name="remarks"></a>Notes

Consultez [opérateur&lt;](#op_lt).

## <a name="op_sv"></a> opérateur » » sv (string_view littéral)

Construit un string_view à partir d’un littéral de chaîne. Nécessite l’espace de noms `std::literals::string_view_literals`. 

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

[\<string_view>](../standard-library/string-view.md)<br/>
