---
title: match_results, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: c282791fb0ff85c0c8818c6905c51703614f4675
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689383"
---
# <a name="match_results-class"></a>match_results, classe

Contient une séquence de sous-correspondances.

## <a name="syntax"></a>Syntaxe

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Paramètres

@No__t_1 *bidit*
Type d'itérateur pour les sous-correspondances.

@No__t_1 *Alloc*
Type d'un allocateur pour la gestion du stockage.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui contrôle une séquence non modifiable d’éléments de type `sub_match<BidIt>` générés par une recherche d’expression régulière. Chaque élément pointe vers la sous-séquence qui correspond au groupe de capture correspondant à cet élément.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[match_results](#match_results)|Construit l’objet.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type d'un allocateur pour la gestion du stockage.|
|[char_type](#char_type)|Type d'un élément.|
|[const_iterator](#const_iterator)|Type d’itérateur const pour les sous-correspondances.|
|[const_reference](#const_reference)|Type d'une référence constante d'élément.|
|[difference_type](#difference_type)|Type d’une différence d’itérateur.|
|[iterator](#iterator)|Type d'itérateur pour les sous-correspondances.|
|[reference](#reference)|Type d’une référence d’élément.|
|[size_type](#size_type)|Type d’un nombre de sous-correspondances.|
|[string_type](#string_type)|Type d’une chaîne.|
|[value_type](#value_type)|Type d’une sous-correspondance.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[begin](#begin)|Désigne le début de la séquence de sous-correspondance.|
|[empty](#empty)|Vérifie l’absence de sous-correspondances.|
|[end](#end)|Désigne la fin de la séquence de sous-correspondance.|
|[format](#format)|Met en forme les sous-correspondances.|
|[get_allocator](#get_allocator)|Retourne l'allocateur stocké.|
|[length](#length)|Retourne la longueur d’une sous-correspondance.|
|[max_size](#max_size)|Obtient le plus grand nombre de sous-correspondances.|
|[endroit](#position)|Obtenez l’offset de démarrage d’un sous-groupe.|
|[céder](#prefix)|Obtient la séquence avant la première sous-correspondance.|
|[size](#size)|Compte le nombre de sous-correspondances.|
|[str](#str)|Retourne une sous-correspondance.|
|[suffixe](#suffix)|Obtient la séquence après la dernière sous-correspondance.|
|[swap](#swap)|Échange deux objets match_results.|

### <a name="operators"></a>Opérateurs

|opérateur|Description|
|-|-|
|[operator=](#op_eq)|Copier un objet match_results.|
|[operator\[\]](#op_at)|Accédez à un sous-objet.|

## <a name="requirements"></a>spécifications

**En-tête :** \<regex>

**Espace de noms :** std

## <a name="example"></a>Exemple

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="allocator_type"></a>  match_results::allocator_type

Type d'un allocateur pour la gestion du stockage.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de l’argument de modèle *Alloc*.

## <a name="begin"></a>  match_results::begin

Désigne le début de la séquence de sous-correspondance.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur d’accès aléatoire qui pointe vers le premier élément de la séquence (ou juste après la fin d’une séquence vide).

## <a name="char_type"></a>  match_results::char_type

Type d'un élément.

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme du type `iterator_traits<BidIt>::value_type`, qui est le type d’élément de la séquence de caractères recherchée.

## <a name="const_iterator"></a>  match_results::const_iterator

Type d’itérateur const pour les sous-correspondances.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Notes

Le typedef décrit un objet pouvant servir d’itérateur à accès aléatoire de constante pour la séquence contrôlée.

## <a name="const_reference"></a>  match_results::const_reference

Type d'une référence constante d'élément.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Notes

Le typedef décrit un objet pouvant servir de référence constante à un élément de la séquence contrôlée.

## <a name="difference_type"></a>  match_results::difference_type

Type d’une différence d’itérateur.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme du type `iterator_traits<BidIt>::difference_type`. Il décrit un objet capable de représenter la différence entre deux itérateurs qui pointent vers des éléments de la séquence contrôlée.

## <a name="empty"></a>  match_results::empty

Vérifie l’absence de sous-correspondances.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne true uniquement en cas d’échec de la recherche d’expression régulière.

## <a name="end"></a>  match_results::end

Désigne la fin de la séquence de sous-correspondance.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne un itérateur qui pointe juste après la fin de la séquence.

## <a name="format"></a>  match_results::format

Met en forme les sous-correspondances.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Paramètres

*Outlt* \
Type d'itérateur de sortie.

*out*\
Flux de sortie dans lequel écrire.

*fmt* \
Chaîne de format.

*indicateurs* \
Indicateurs de format.

### <a name="remarks"></a>Notes

Chaque fonction membre génère du texte mis en forme sous le contrôle du format *fmt*. La première fonction membre écrit le texte mis en forme dans la séquence définie par son argument out *et retourne.* La deuxième fonction membre retourne un objet chaîne contenant une copie du texte mis en forme.

Pour générer du texte mis en forme, le texte littéral dans la chaîne de format est habituellement copié dans la séquence cible. Chaque séquence d'échappement dans la chaîne de format est remplacée par le texte qu'elle représente. Les détails de la copie et du remplacement sont contrôlés par les indicateurs de format transmis à la fonction.

## <a name="get_allocator"></a>  match_results::get_allocator

Retourne l'allocateur stocké.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne une copie de l'objet allocateur utilisé par `*this` pour allouer ses objets `sub_match`.

## <a name="iterator"></a>  match_results::iterator

Type d'itérateur pour les sous-correspondances.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Notes

Le type décrit un objet pouvant servir d'itérateur à accès aléatoire pour la séquence contrôlée.

## <a name="length"></a>  match_results::length

Retourne la longueur d’une sous-correspondance.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Paramètres

*sous* \
Index de la sous-correspondance.

### <a name="remarks"></a>Notes

La fonction membre retourne `(*this)[sub].length()`.

## <a name="match_results"></a>  match_results::match_results

Construit l’objet.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Paramètres

\ *Alloc*
Objet allocateur à stocker.

\ *droit*
Objet match_results à copier.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet `match_results` qui ne contient aucune sous-correspondance. Le deuxième constructeur construit un objet `match_results` qui est une copie de *Right*.

## <a name="max_size"></a>  match_results::max_size

Obtient le plus grand nombre de sous-correspondances.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la longueur de la séquence la plus longue que l’objet peut contrôler.

## <a name="op_eq"></a>  match_results::operator=

Copier un objet match_results.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Paramètres

\ *droit*
Objet match_results à copier.

### <a name="remarks"></a>Notes

L’opérateur membre remplace la séquence contrôlée par `*this` par une copie de la séquence contrôlée par *Right*.

## <a name="op_at"></a>  match_results::operator[]

Accédez à un sous-objet.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Paramètres

*n*\
Index de la sous-correspondance.

### <a name="remarks"></a>Notes

La fonction membre retourne une référence à l’élément *n* de la séquence contrôlée, ou une référence à un objet `sub_match` vide si `size() <= n` ou si le groupe de capture *n* ne fait pas partie de la correspondance.

## <a name="position"></a>  match_results::position

Obtenez l’offset de démarrage d’un sous-groupe.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Paramètres

*sous* \
Index de la sous-correspondance.

### <a name="remarks"></a>Notes

La fonction membre retourne `std::distance(prefix().first, (*this)[sub].first)`, c’est-à-dire la distance entre le premier caractère de la séquence cible et le premier caractère de la sous-correspondance vers laquelle pointe l’élément `n` de la séquence contrôlée.

## <a name="prefix"></a>  match_results::prefix

Obtient la séquence avant la première sous-correspondance.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence à un objet de type `sub_match<BidIt>` qui pointe vers la séquence de caractères qui commence au début de la séquence cible et qui se termine à `(*this)[0].first`, c’est-à-dire qu’il pointe vers le texte qui précède la sous-séquence correspondante.

## <a name="reference"></a>  match_results::reference

Type d’une référence d’élément.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du type `const_reference`.

## <a name="size"></a>  match_results::size

Compte le nombre de sous-correspondances.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre de groupes de capture plus un dans l’expression régulière utilisée pour la recherche, ou zéro si aucune recherche n’a été effectuée.

## <a name="size_type"></a>  match_results::size_type

Type d’un nombre de sous-correspondances.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du type `Alloc::size_type`.

## <a name="str"></a>  match_results::str

Retourne une sous-correspondance.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Paramètres

*sous* \
Index de la sous-correspondance.

### <a name="remarks"></a>Notes

La fonction membre retourne `string_type((*this)[sub])`.

## <a name="string_type"></a>  match_results::string_type

Type d’une chaîne.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du type `basic_string<char_type>`.

## <a name="suffix"></a>  match_results::suffix

Obtient la séquence après la dernière sous-correspondance.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence à un objet de type `sub_match<BidIt>` , qui pointe vers la séquence de caractères qui commence à `(*this)[size() - 1].second` et qui se termine à la fin de la séquence cible. En d’autres termes, il pointe vers le texte qui suit la sous-séquence correspondante.

## <a name="swap"></a>  match_results::swap

Échange deux objets match_results.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Paramètres

\ *droit*
Objet match_results à échanger.

### <a name="remarks"></a>Notes

La fonction membre échange le contenu de `*this` et *juste* en temps constant et ne lève pas d’exceptions.

## <a name="value_type"></a>  match_results::value_type

Type d’une sous-correspondance.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme du type `sub_match<BidIt>`.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)
