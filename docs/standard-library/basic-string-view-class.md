---
title: Classe basic_string_view
ms.date: 04/20/2019
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: ac65dca931f821c717e9c081c8d3479fd0b3bb0e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364891"
---
# <a name="basic_string_view-class"></a>Classe basic_string_view

Le modèle `basic_string_view<charT>` de classe a été ajouté dans le C 17 pour servir de moyen sûr et efficace pour une fonction d’accepter divers types de chaînes sans rapport avec la fonction devant être templatisée sur ces types. La classe détient un pointeur non-propriétaire à une séquence contigu de données de caractère, et une longueur qui spécifie le nombre de caractères dans la séquence. Aucune hypothèse n’est faite quant à savoir si la séquence est annulée.

La bibliothèque standard définit plusieurs spécialisations en fonction du type d’éléments :

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

Dans ce document, le terme « string_view » désigne généralement l’un ou l’autre de ces types.

Un string_view décrit l’interface commune minimale nécessaire pour lire les données de chaîne. Il donne un accès de cône aux données sous-jacentes; il ne fait aucune `copy` copie (sauf pour la fonction). Les données peuvent ou non contenir des valeurs nulles («0») à n’importe quelle position. Un string_view n’a aucun contrôle sur la durée de vie de l’objet. Il incombe à l’appelant de s’assurer que les données de chaîne sous-jacentes sont valides.

Une fonction qui accepte un paramètre de type string_view peut être faite pour fonctionner avec n’importe quel type de chaîne, sans faire de la fonction dans un modèle, ou de limiter la fonction à un sous-ensemble particulier de types de chaînes. La seule exigence est qu’une conversion implicite existe du type de chaîne à string_view. Tous les types de chaînes standard sont implicitement convertibles à un string_view qui contient le même type d’élément. En d’autres `std::string` termes, `string_view` a est `wstring_view`convertible à un mais pas à un .

L’exemple suivant montre une `f` fonction non-modèle `wstring_view`qui prend un paramètre de type . Il peut être appelé `std::wstring`avec `wchar_t*`des `winrt::hstring`arguments de type , , et .

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>Paramètres

*CharType CharType*\
Le type de caractères qui sont stockés dans le string_view. La Bibliothèque standard de CMD fournit les types suivants pour les spécialisations de ce modèle.

- [string_view](../standard-library/string-view-typedefs.md#string_view) pour les éléments de type **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), pour **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) pour **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) pour **char32_t**.

*Traits*\
Par défaut pour [char_traits](char-traits-struct.md)<*> CharType.*

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_string_view](#basic_string_view)|Construit un string_view vide ou bien pointe vers tout ou partie des données d’un autre objet de chaîne, ou à un tableau de caractère de type C.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|**const_iterator**|Itérateur d’accès aléatoire qui peut lire les éléments **de const.**|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Itérateur**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointeur**|`using pointer = value_type*;`|
|**Référence**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Opérateurs membres

|Opérateur|Description|
|-|-|
|[opérateur](#op_eq)|Assigne un objet de chaîne string_view ou convertible à un autre string_view.|
|[Opérateur\[\]](#op_at)|Retourne l'élément à l'index spécifié.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[À](#at)|Retourne une const_reference à l’élément à un endroit précis.|
|[Précédent](#back)|Retourne un const_reference au dernier élément.|
|[Commencer](#begin)|Retourne un itérateur de cônes adressant le premier élément. (string_views sont immuables.)|
|[cbegin](#cbegin)|Même chose que [commencer](#begin).|
|[cend](#cend)|Retourne un itérateur de const qui indique un passé le dernier élément.|
|[Copie](#copy)|Copies tout au plus d’un nombre spécifié de caractères à partir d’une position indexée dans une source string_view à un tableau de caractère cible. (Non recommandé. Utilisez _Copy_s à la place.)|
|[_Copy_s](#_copy_s)|Fonction de copie CRT sécurisée.|
|[Comparer](#compare)|Compare une string_view avec un string_view spécifié pour déterminer si elles sont égales ou si l’une est moins lexicographique que l’autre.|
|[crbegin](#crbegin)|Identique à [rbegin](#rbegin).|
|[crend](#crend)|Identique à [rend](#rend).|
|[data](#data)|Retourne un pointeur brut non-propriétaire à la séquence de caractère.|
|[Vide](#empty)|Teste si le string_view contient des caractères.|
|[Fin](#end)|Identique à [cend](#cend).|
|[Trouver](#find)|Recherche dans une direction vers l’avant pour la première occurrence d’un sous-corde qui correspond à une séquence spécifiée de caractères.|
|[find_first_not_of](#find_first_not_of)|Recherche le premier personnage qui n’est pas un élément d’un objet de chaîne string_view ou convertible spécifié.|
|[find_first_of](#find_first_of)|Recherche le premier personnage qui correspond à n’importe quel élément d’un objet de chaîne string_view ou convertible spécifié.|
|[find_last_not_of](#find_last_not_of)|Recherche le dernier personnage qui n’est pas un élément d’un objet de chaîne string_view ou convertible spécifié.|
|[find_last_of](#find_last_of)|Recherche le dernier personnage qui est un élément d’un objet de chaîne string_view ou convertible spécifié.|
|[Avant](#front)|Retourne un const_reference au premier élément.|
|[length](#length)|Retourne le nombre actuel d’éléments.|
|[max_size](#max_size)|Retourne le nombre maximum de caractères qu’une string_view pourrait contenir.|
|[rbegin](#rbegin)|Retourne un itérateur de cône qui aborde le premier élément dans un string_view inversé.|
|[remove_prefix](#remove_prefix)|Déplace le pointeur vers l’avant par le nombre spécifié d’éléments.|
|[remove_suffix](#remove_suffix)|Réduit la taille de la vue par le nombre spécifié d’éléments à partir de l’arrière.|
|[rend](#rend)|Retourne un itérateur de const qui indique un passé le dernier élément dans un string_view inversé.|
|[rfind](#rfind)|Recherche un string_view en marche arrière pour la première occurrence d’un sous-corde qui correspond à une séquence spécifiée de caractères.|
|[Taille](#size)|Retourne le nombre actuel d’éléments.|
|[substr](#substr)|Renvoie une sous-corde d’une longueur spécifiée à partir d’un index spécifié.|
|[swap](#swap)|Échangez le contenu de deux string_views.|

## <a name="remarks"></a>Notes

Si une fonction doit générer une séquence supérieure à [max_size](#max_size) éléments, la fonction signale une erreur de longueur en levant un objet de type [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Spécifications

[std:c 17](../build/reference/std-specify-language-standard-version.md) ou plus tard

**En-tête:** \<string_view>

**Espace de noms :** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view::à

Retourne une const_reference au personnage à l’indice spécifié à 0.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Paramètres

*Compenser*\
L’index de l’élément à référer.

### <a name="return-value"></a>Valeur de retour

Une const_reference au caractère à la position spécifiée par l’index de paramètres.

### <a name="remarks"></a>Notes

Le premier élément a un indice de zéro et les éléments suivants sont indexés consécutivement par les intégrés positifs, de sorte qu’un string_view de longueur *n* a *un*n th élément indexé par le nombre n *-* 1. **à** jette une exception pour les indices invalides, contrairement à [l’opérateur\[](#op_at).

En général, nous **at** recommandons que pour `std::vector` les séquences telles que et string_view ne devrait jamais être utilisé. Un index invalide passé à une séquence est une erreur logique qui doit être découverte et corrigée pendant le développement. Si un programme n’est pas absolument certain que ses indices sont valides, il devrait les tester, ne pas appeler à() et compter sur des exceptions pour se défendre contre la programmation négligente.

Voir [basic_string_view::opérateur\[ ](#op_at) pour plus d’informations.

### <a name="example"></a>Exemple

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view::retour

Retourne un const_reference au dernier élément.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Valeur de retour

Un const_reference au dernier élément de la string_view.

### <a name="remarks"></a>Notes

Jetez une exception si le string_view est vide.

Gardez à l’esprit qu’après une string_view `remove_suffix`est modifiée, par exemple en appelant, l’élément retourné par cette fonction n’est plus le dernier élément dans les données sous-jacentes.

### <a name="example"></a>Exemple

Un string_view qui est construit avec un littéral de chaîne C n’inclut `back` pas la fin nulle et donc dans l’exemple suivant retourne 'p' et non '0'.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

Les nulls intégrés sont traités comme n’importe quel autre personnage :

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view::basic_string_view

Construit un string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Paramètres

*Str*\
Le pointeur des valeurs de caractère.

*Len*\
Le nombre de caractères à inclure dans la vue.

## <a name="remarks"></a>Notes

Les constructeurs avec un paramètre charTMD supposent que l’entrée est non terminée, mais la fin nulle n’est pas incluse dans le string_view.

Vous pouvez également construire un string_view avec un littéral. Voir [opérateur""sv](string-view-operators.md#op_sv).

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view::commencer

Comme [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne une const_iterator abordant le premier élément.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view::cbegin

Retourne un const_iterator qui répond au premier élément de la plage.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un **itérateur d’accès** aléatoire const qui pointe au premier élément de la plage, ou l’emplacement juste au-delà de la fin d’une plage vide (pour une plage vide, `cbegin() == cend()`).

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view::cend

Retourne un const_iterator qui s’adresse à l’emplacement juste au-delà du dernier élément d’une plage.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un **itérateur d’accès** aléatoire const qui pointe juste au-delà de la fin de la plage.

### <a name="remarks"></a>Notes

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view::comparer

Effectue une comparaison sensible avec un string_view spécifié (ou un type de chaîne convertible) pour déterminer si les deux objets sont égaux ou si l’un est lexicographiquement moins que l’autre. Les [ \<string_view> opérateurs](string-view-operators.md) utilisent cette fonction de membre pour effectuer des comparaisons.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Paramètres

*strv*\
Le string_view qui est à comparer à cette string_view.

*Pos*\
L’indice de ce string_view auquel commence la comparaison.

*Num*\
Le nombre maximum de caractères de cette string_view à comparer.

*num2 (num2)*\
Le nombre maximum de caractères de *strv* à comparer.

*Compenser*\
L’indice de *strv* auquel commence la comparaison.

*Ptr*\
La chaîne C à comparer à cette string_view.

### <a name="return-value"></a>Valeur de retour

Une valeur négative si cette string_view est inférieure *à strv* ou *ptr;* zéro si les deux séquences de caractères sont égales; ou une valeur positive si cette string_view est supérieure *à strv* ou *ptr*.

### <a name="remarks"></a>Notes

Les `compare` fonctions du membre effectuent une comparaison sensible aux cas de la totalité ou d’une partie de chaque séquence de caractère.

### <a name="example"></a>Exemple

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are"
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are"
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a)
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view::copie

Copies tout au plus d’un nombre spécifié de caractères à partir d’une position indexée dans une source string_view à un tableau de caractère cible. Nous vous recommandons d’utiliser la fonction sécurisée [basic_string_view::_Copy_s](#_copy_s) à la place.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*Ptr*\
Tableau de caractères cible dans lequel les éléments doivent être copiés.

*Compter*\
Le nombre de caractères à copier, tout au plus, à partir de la source string_view.

*Compenser*\
La position de début à la source string_view à partir de laquelle des copies doivent être faites.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés.

### <a name="remarks"></a>Notes

Un caractère null n’est pas ajouté à la fin de la copie.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view::_Copy_s

Fonction de copie CRT sécurisée à utiliser au lieu de [copier](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Paramètres

*Dest*\
Tableau de caractères cible dans lequel les éléments doivent être copiés.

*dest_size*\
La taille de *dest*.

*Compter* Le nombre de caractères à copier, tout au plus, à partir de la chaîne source.

*_Off*\
Position de début dans la chaîne source à partir de laquelle les copies doivent être effectuées.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés.

### <a name="remarks"></a>Notes

Un caractère null n’est pas ajouté à la fin de la copie.

Pour plus d’informations, voir [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view::crbegin

Retourne un const_reverse_iterator qui aborde le premier élément d’un string_view inversé.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un const_reverse_iterator qui aborde le premier élément d’un string_view inversé.

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view::crend

Identique à [rend](#rend).

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne un const_reverse_iterator qui aborde un passé la fin d’un string_view inversé.

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view::data

Retourne un pointeur brut non-propriétaire à la séquence de caractère const de l’objet qui a été utilisé pour construire le string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur-à-const au premier élément de la séquence de caractère.

### <a name="remarks"></a>Notes

Le pointeur ne peut pas modifier les caractères.

Une séquence de caractères string_view n’est pas nécessairement annulée. Le type `data` de retour pour n’est pas une chaîne valide C, parce qu’aucun caractère nul est annexé. Le caractère nul '0' n’a pas de signification particulière dans un objet de type string_view et peut faire partie de l’objet string_view comme n’importe quel autre personnage.

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view::vide

Teste si le string_view contient des caractères ou non.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si l’objet string_view ne contient pas de caractères; **faux** s’il a au moins un personnage.

### <a name="remarks"></a>Notes

La fonction membre est équivalente à [la taille](#size)() 0.

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view::fin

Retourne un const_iterator d’accès aléatoire qui indique un dernier élément passé.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne un const_iterator d’accès aléatoire qui indique un dernier élément passé.

### <a name="remarks"></a>Notes

`end`est utilisé pour vérifier si un const_iterator a atteint la fin de son string_view. La valeur retournée par `end` ne doit pas être déréférencée.

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view::trouver

Recherche un string_view dans une direction vers l’avant pour la première occurrence d’un personnage ou d’un sous-corde qui correspond à une séquence spécifiée de caractères.s).

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*Str*\
La string_view pour laquelle la fonction de membre est de rechercher.

*chVal (en)*\
Valeur de caractère que la fonction membre doit rechercher.

*Compenser*\
Index auquel la recherche doit commencer.

*Ptr*\
La chaîne C pour laquelle la fonction de membre est de rechercher.

*Compter*\
Le nombre de personnages en *ptr*, comptant vers l’avant à partir du premier personnage.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view::find_first_not_of

Recherche le premier personnage qui n’est pas un élément d’un objet de chaîne string_view ou convertible spécifié.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*Str*\
La string_view pour laquelle la fonction de membre est de rechercher.

*chVal (en)*\
Valeur de caractère que la fonction membre doit rechercher.

*Compenser*\
Index auquel la recherche doit commencer.

*Ptr*\
La chaîne C pour laquelle la fonction de membre est de rechercher.

*Compter*\
Le nombre de caractères, comptant vers l’avant à partir du premier personnage, dans la chaîne C pour laquelle la fonction de membre est de rechercher.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view::find_first_of

Recherche le premier personnage qui correspond à n’importe quel élément d’un string_view spécifié.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*chVal (en)*\
Valeur de caractère que la fonction membre doit rechercher.

*Compenser*\
Index auquel la recherche doit commencer.

*Ptr*\
La chaîne C pour laquelle la fonction de membre est de rechercher.

*Compter*\
Le nombre de caractères, comptant vers l’avant à partir du premier personnage, dans la chaîne C pour laquelle la fonction de membre est de rechercher.

*Str*\
La string_view pour laquelle la fonction de membre est de rechercher.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view::find_last_not_of

Recherche le dernier personnage qui n’est pas un élément d’une string_view spécifiée.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*Str*\
La string_view pour laquelle la fonction de membre est de rechercher.

*chVal (en)*\
Valeur de caractère que la fonction membre doit rechercher.

*Compenser*\
Index auquel la recherche doit se terminer.

*Ptr*\
La chaîne C pour laquelle la fonction de membre est de rechercher.

*Compter*\
Le nombre de personnages, comptant en avant à partir du premier personnage, en *ptr*.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `string_view::npos`.

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view::find_last_of

Recherche le dernier personnage qui correspond à n’importe quel élément d’un string_view spécifié.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*Str*\
La string_view pour laquelle la fonction de membre est de rechercher.

*chVal (en)*\
Valeur de caractère que la fonction membre doit rechercher.

*Compenser*\
Index auquel la recherche doit se terminer.

*Ptr*\
La chaîne C pour laquelle la fonction de membre est de rechercher.

*Compter*\
Le nombre de caractères, comptant vers l’avant à partir du premier personnage, dans la chaîne C pour laquelle la fonction de membre est de rechercher.

### <a name="return-value"></a>Valeur de retour

Index du dernier caractère de la sous-chaîne recherchée en cas de réussite ; sinon, `npos`.

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view::avant

Retourne un const_reference au premier élément.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Valeur de retour

Un const_reference au premier élément.

### <a name="remarks"></a>Notes

Jetez une exception si le string_view est vide.

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view::longueur

Retourne le nombre actuel d’éléments.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre est identique à [size](#size).

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view::max_size

Retourne le nombre maximum de caractères qu’une string_view peut contenir.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximum de caractères qu’une string_view peut contenir.

### <a name="remarks"></a>Notes

Une exception de type [length_error](../standard-library/length-error-class.md) est jetée lorsqu’une opération produit un `max_size()`string_view avec une longueur supérieure à .

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view::opérateur

Assigne un objet de chaîne string_view ou convertible à un autre string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Exemple

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view::opérateur[]

Fournit un const_reference au personnage avec un index spécifié.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Paramètres

*Compenser*\
L’index de l’élément à référer.

### <a name="return-value"></a>Valeur de retour

Une const_reference au caractère à la position spécifiée par l’index de paramètres.

### <a name="remarks"></a>Notes

Le premier élément a un indice de zéro, et les éléments suivants sont indexés consécutivement par les intégrés positifs, de sorte qu’un string_view de longueur *n* a un *n*th élément indexé par le nombre *n* - 1.

`operator[]`est plus rapide que la fonction du membre [pour](#at) fournir un accès de lecture aux éléments d’un string_view.

`operator[]`ne vérifie pas si l’index adopté en tant qu’argument est valide. Un index invalide passé pour les `operator[]` résultats dans un comportement indéfini.

La référence retournée peut être invalidée si les données de chaîne sous-jacentes sont modifiées ou supprimées par l’objet propriétaire.

Lors de la compilation avec [ \_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) réglé à 1 ou 2, une erreur de temps d’exécution se produira si vous essayez d’accéder à un élément en dehors des limites de la string_view. Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view::rbegin

Renvoie un itérateur de const au premier élément d’une string_view inversée.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Renvoie un itérateur d’accès aléatoire au premier élément d’une string_view inversée, en abordant ce qui serait le dernier élément de la string_view non inversée correspondante.

### <a name="remarks"></a>Notes

`rbegin`est utilisé avec un string_view inversé tout comme [le début](#begin) est utilisé avec un string_view. `rbegin`peut être utilisé pour initialiser une itération vers l’arrière.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view::remove_prefix

Déplace le pointeur vers l’avant par le nombre spécifié d’éléments.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Notes

Laisse les données sous-jacentes inchangées. Déplace le pointeur string_view vers l’avant `size` par n éléments et définit le membre de données privé à la taille - n.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view::remove_suffix

Réduit la taille de la vue par le nombre spécifié d’éléments à partir de l’arrière.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Notes

Laisse les données sous-jacentes et le pointeur à elle inchangée. Définit le `size` membre privé des données à la taille - n.

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view::rend

Retourne un itérateur de const qui indique un passé le dernier élément dans un string_view inversé.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un inverse inverse inverse l’itérateur d’accès aléatoire qui indique un passé le dernier élément dans un string_view inversé.

### <a name="remarks"></a>Notes

`rend`est utilisé avec un string_view inversé tout comme [l’extrémité](#end) est utilisée avec un string_view. `rend`peut être utilisé pour vérifier si un itérateur inversé a atteint la fin de son string_view. La valeur retournée par `rend` ne doit pas être déréférencée.

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view::rfind

Recherche un string_view en marche arrière pour un sous-cordon qui correspond à une séquence spécifiée de caractères.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*chVal (en)*\
Valeur de caractère que la fonction membre doit rechercher.

*Compenser*\
Index auquel la recherche doit commencer.

*Ptr*\
La chaîne C pour laquelle la fonction de membre est de rechercher.

*Compter*\
Le nombre de caractères, comptant vers l’avant à partir du premier personnage, dans la chaîne C pour laquelle la fonction de membre est de rechercher.

*Str*\
La string_view pour laquelle la fonction de membre est de rechercher.

### <a name="return-value"></a>Valeur de retour

L’index du premier caractère du sous-corde en cas de succès; autrement `npos`.

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view::taille

Retourne le nombre d’éléments dans le string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

La longueur de la string_view.

### <a name="remarks"></a>Notes

Un string_view peut modifier sa longueur, `remove_prefix` `remove_suffix`par exemple par et . Étant donné que cela ne modifie pas les données de chaîne sous-jacentes, la taille d’un string_view n’est pas nécessairement la taille des données sous-jacentes.

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view::substr

Renvoie une string_view qui représente (tout au plus) le nombre spécifié de caractères à partir d’une position spécifiée.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Paramètres

*Compenser*\
Un index localisant l’élément à la position à partir de laquelle la copie est faite, avec une valeur par défaut de 0.

*Compter*\
Le nombre de caractères à inclure dans le sous-corde, s’ils sont présents.

### <a name="return-value"></a>Valeur de retour

Un objet string_view qui représente la sous-séquence spécifiée des éléments.

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view::swap

Échange deux string_views, c’est-à-dire les indications sur les données de chaîne sous-jacentes et les valeurs de taille.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Paramètres

*Sv*\
La source string_view dont les valeurs de pointeur et de taille doivent être échangées avec celle de la destination string_view.

## <a name="see-also"></a>Voir aussi

[\<string_view>](../standard-library/string-view.md)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)
