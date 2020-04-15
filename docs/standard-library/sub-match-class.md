---
title: sub_match, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
ms.openlocfilehash: 460f79fe0f23643fafcebb64aecf2988bdb0debe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376582"
---
# <a name="sub_match-class"></a>sub_match, classe

Décrit une sous-correspondance.

## <a name="syntax"></a>Syntaxe

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Paramètres

*BidIt*\
Type d'itérateur pour les sous-correspondances.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui désigne une séquence de caractères qui correspondait à un groupe de capture dans un appel à [regex_match](../standard-library/regex-functions.md#regex_match) ou à [regex_search](../standard-library/regex-functions.md#regex_search). Les objets de type de [classe match_results](../standard-library/match-results-class.md) contiennent un tableau de ces objets, un pour chaque groupe de capture de l’expression régulière utilisée dans la recherche.

Si le groupe de capture n’a aucune correspondance, le membre de données `matched` de l’objet a la valeur false, et les deux itérateurs `first` et `second` (hérités du `std::pair`de base) sont égaux. Si le groupe de capture a une correspondance, `matched` a la valeur true et l’itérateur `first` pointe vers le premier caractère de la séquence cible correspondant au groupe de capture. En outre, l’itérateur `second` pointe vers la position située après le dernier caractère de la séquence cible correspondant au groupe de capture. Notez que pour une correspondance de longueur nulle, le membre `matched` a la valeur true. Par ailleurs, les deux itérateurs sont égaux et pointent vers la position de la correspondance.

Une correspondance de longueur nulle peut se produire quand un groupe de capture se compose uniquement d’une assertion, ou d’une répétition n’autorisant aucune répétition. Par exemple :

« ^ » correspond à la séquence cible « a ». L’objet `sub_match` correspondant au groupe de capture 0 contient les itérateurs qui pointent vers le premier caractère de la séquence.

« b(a*)b » correspond à la séquence cible « bb ». L’objet `sub_match` correspondant au groupe de capture 1 contient les itérateurs qui pointent vers le second caractère de la séquence.

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[difference_type](#difference_type)|Type d’une différence d’itérateur.|
|[Itérateur](#iterator)|Type d'un itérateur.|
|[value_type](#value_type)|Type d’un élément.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Comparer](#compare)|Comparer une sous-correspondance à une séquence.|
|[length](#length)|Retourne la longueur d'une sous-correspondance.|
|[Correspondait](#matched)|Indique si la correspondance a réussi.|
|[Str](#str)|Convertit la sous-correspondance en chaîne.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[>basic_string<de value_type l’opérateur](#op_basic_string_lt_value_type_gt)|Effectue un cast de la sous-correspondance en chaîne.|

## <a name="example"></a>Exemple

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>Spécifications

**En-tête :** \<regex>

**Espace de noms :** std

## <a name="sub_matchcompare"></a><a name="compare"></a>sub_match::comparer

Comparer une sous-correspondance à une séquence.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Sous-correspondance avec laquelle effectuer la comparaison.

*Str*\
Chaîne de comparaison.

*Ptr*\
Séquence terminée par un caractère null avec laquelle effectuer la comparaison.

### <a name="remarks"></a>Notes

La première fonction membre compare la séquence mise en correspondance `[first, second)` à la séquence mise en correspondance `[right.first, right.second)`. La deuxième fonction membre compare la séquence mise en correspondance `[first, second)` à la séquence de caractères `[right.begin(), right.end())`. La troisième fonction membre compare la séquence mise en correspondance `[first, second)` à la séquence de caractères `[right, right + std::char_traits<value_type>::length(right))`.

Chaque fonction retourne :

une valeur négative si la première valeur différente dans la séquence mise en correspondance est inférieure à l'élément correspondant dans la séquence d'opérande (comme déterminé par `std::char_traits<value_type>::compare`) ou si les deux valeurs ont un préfixe commun mais que la séquence cible est plus longue ;

zéro si les valeurs comparées sont égales élément par élément et qu'elles ont la même longueur ;

une valeur positive dans les autres cas.

## <a name="sub_matchdifference_type"></a><a name="difference_type"></a>sub_match::difference-type

Type d’une différence d’itérateur.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de `iterator_traits<BidIt>::difference_type`.

## <a name="sub_matchiterator"></a><a name="iterator"></a>sub_match::iterator

Type d'un itérateur.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de l'argument de type de modèle `Bidit`.

## <a name="sub_matchlength"></a><a name="length"></a>sub_match::longueur

Retourne la longueur d'une sous-correspondance.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence mise en correspondance, ou zéro en l'absence de séquence mise en correspondance.

## <a name="sub_matchmatched"></a><a name="matched"></a>sub_match::matched

Indique si la correspondance a réussi.

```cpp
bool matched;
```

### <a name="remarks"></a>Notes

Le membre **n’est vrai** que `*this` si le groupe de capture associé faisait partie du match d’expression régulière.

## <a name="sub_matchoperator-basic_stringltvalue_typegt"></a><a name="op_basic_string_lt_value_type_gt"></a>sub_match::opérateur basic_string&lt;value_type&gt;

Effectue un cast de la sous-correspondance en chaîne.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Notes

L’opérateur membre retourne `str()`.

## <a name="sub_matchstr"></a><a name="str"></a>sub_match::str

Convertit la sous-correspondance en chaîne.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne `basic_string<value_type>(first, second)`.

## <a name="sub_matchvalue_type"></a><a name="value_type"></a>sub_match::value_type

Type d’un élément.

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de `iterator_traits<BidIt>::value_type`.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)
