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
ms.openlocfilehash: 7a53a27e11088ab02f873613794d6799851ca373
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416184"
---
# <a name="basic_string_view-class"></a>Classe basic_string_view

Le modèle de classe `basic_string_view<charT>` a été ajouté en C++ 17 pour servir de moyen sûr et efficace pour une fonction d’accepter différents types de chaîne non liés sans que la fonction ne soit en cours d’utilisation sur ces types. La classe contient un pointeur non propriétaire vers une séquence contiguë de données de caractères, et une longueur qui spécifie le nombre de caractères dans la séquence. Aucune hypothèse n’est prise en ce qui concerne si la séquence se termine par un caractère null.

La bibliothèque standard définit plusieurs spécialisations basées sur le type des éléments :

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

Dans ce document, le terme « string_view » fait généralement référence à l’un de ces typedefs.

Une string_view décrit l’interface commune minimale nécessaire pour lire les données de chaîne. Il fournit un accès const aux données sous-jacentes ; Il n’effectue aucune copie (à l’exception de la fonction `copy`). Les données peuvent contenir ou non des valeurs null (' \ 0 ') à n’importe quelle position. Un string_view n’a aucun contrôle sur la durée de vie de l’objet. Il incombe à l’appelant de s’assurer que les données de chaîne sous-jacentes sont valides.

Une fonction qui accepte un paramètre de type string_view peut être faite pour fonctionner avec n’importe quel type de chaîne, sans faire passer la fonction dans un modèle ou contraindre la fonction à un sous-ensemble particulier de types chaîne. La seule exigence est qu’il existe une conversion implicite du type de chaîne en string_view. Tous les types de chaînes standard sont implicitement convertibles en string_view qui contient le même type d’élément. En d’autres termes, une `std::string` est convertible en `string_view` mais pas en `wstring_view`.

L’exemple suivant montre une fonction sans modèle `f` qui accepte un paramètre de type `wstring_view`. Elle peut être appelée avec des arguments de type `std::wstring`, `wchar_t*`et `winrt::hstring`.

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

*CharType*\
Type des caractères stockés dans le string_view. La C++ bibliothèque standard fournit les typedefs suivants pour les spécialisations de ce modèle.
- [string_view](../standard-library/string-view-typedefs.md#string_view) pour les éléments de type **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), par **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) pour **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) pour **char32_t**.

\ *traits*
La valeur par défaut est [char_traits](char-traits-struct.md)<> *CharType*.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_string_view](#basic_string_view)|Construit une string_view qui est vide ou qui pointe vers tout ou partie des données de l’objet String, ou vers un tableau de caractères de style C.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|**const_iterator**|Itérateur à accès aléatoire qui peut lire des éléments **const** .|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**reference**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Opérateurs membres

|Opérateur|Description|
|-|-|
|[operator=](#op_eq)|Assigne une string_view ou un objet de chaîne convertible à une autre string_view.|
|[operator\[\]](#op_at)|Retourne l'élément à l'index spécifié.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[at](#at)|Retourne un const_reference à l’élément à un emplacement spécifié.|
|[back](#back)|Retourne un const_reference au dernier élément.|
|[begin](#begin)|Retourne un itérateur const qui traite le premier élément. (string_views sont immuables.)|
|[cbegin](#cbegin)|Identique à [Begin](#begin).|
|[cend](#cend)|Retourne un itérateur const qui pointe vers un point après le dernier élément.|
|[copy](#copy)|Copie au plus un nombre spécifié de caractères à partir d’une position indexée dans un string_view source vers un tableau de caractères cible. (Non recommandé. Utilisez à la place _Copy_s.)|
|[_Copy_s](#_copy_s)|Fonction de copie sécurisée du CRT.|
|[compare](#compare)|Compare un string_view avec un string_view spécifié pour déterminer s’ils sont égaux ou s’il s’agit d’un vue lexicographique inférieur à l’autre.|
|[crbegin](#crbegin)|Identique à [rbegin](#rbegin).|
|[crend](#crend)|Identique à [rend](#rend).|
|[data](#data)|Retourne un pointeur brut non propriétaire vers la séquence de caractères.|
|[empty](#empty)|Teste si le string_view contient des caractères.|
|[end](#end)|Identique à [CEND](#cend).|
|[find](#find)|Recherche dans une direction vers l’avant la première occurrence d’une sous-chaîne qui correspond à une séquence de caractères spécifiée.|
|[find_first_not_of](#find_first_not_of)|Recherche le premier caractère qui n’est pas un élément d’une string_view ou d’un objet de chaîne convertible spécifié.|
|[find_first_of](#find_first_of)|Recherche le premier caractère qui correspond à n’importe quel élément d’un string_view ou d’un objet String convertible spécifié.|
|[find_last_not_of](#find_last_not_of)|Recherche le dernier caractère qui n’est pas un élément d’une string_view ou d’un objet de chaîne convertible spécifié.|
|[find_last_of](#find_last_of)|Recherche le dernier caractère qui est un élément d’un string_view ou d’un objet String convertible spécifié.|
|[front](#front)|Retourne un const_reference au premier élément.|
|[length](#length)|Retourne le nombre actuel d’éléments.|
|[max_size](#max_size)|Retourne le nombre maximal de caractères qu’un string_view peut contenir.|
|[rbegin](#rbegin)|Retourne un itérateur const qui traite le premier élément d’un string_view inversé.|
|[remove_prefix](#remove_prefix)|Déplace le pointeur vers l’avant par le nombre d’éléments spécifié.|
|[remove_suffix](#remove_suffix)|Réduit la taille de la vue par le nombre spécifié d’éléments à partir de l’arrière-plan.|
|[rend](#rend)|Retourne un itérateur const qui pointe vers un après le dernier élément d’un string_view inversé.|
|[rfind](#rfind)|Recherche une string_view en sens inverse pour la première occurrence d’une sous-chaîne qui correspond à une séquence de caractères spécifiée.|
|[size](#size)|Retourne le nombre actuel d’éléments.|
|[substr](#substr)|Retourne une sous-chaîne d’une longueur spécifiée commençant à un index spécifié.|
|[swap](#swap)|Échangez le contenu de deux string_views.|

## <a name="remarks"></a>Notes

Si une fonction doit générer une séquence supérieure à [max_size](#max_size) éléments, la fonction signale une erreur de longueur en levant un objet de type [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Spécifications

[std : c++ 17](../build/reference/std-specify-language-standard-version.md) ou version ultérieure

**En-tête :** \<string_view >

**Espace de noms :** std

## <a name="at"></a>basic_string_view :: à

Retourne un const_reference au caractère à l’index de base 0 spécifié.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Paramètres

*décalage*\
Index de l’élément à référencer.

### <a name="return-value"></a>Valeur de retour

Const_reference au caractère à la position spécifiée par l’index de paramètre.

### <a name="remarks"></a>Notes

Le premier élément a un index de zéro et les éléments suivants sont indexés consécutivement par les entiers positifs, de sorte qu’un string_view de longueur *n* a un *n*ième élément indexé par le nombre *n-* 1. **au niveau** de lève une exception pour les index non valides, contrairement à l' [opérateur\[\]](#op_at). 

En général, nous vous recommandons d' **utiliser des** séquences comme `std::vector` et string_view ne doivent jamais être utilisées. Un index non valide passé à une séquence est une erreur logique qui doit être détectée et corrigée pendant le développement. Si un programme n’est pas absolument sûr que ses index sont valides, il doit les tester, ne pas appeler at () et s’appuyer sur des exceptions pour se défendre contre la programmation incorrecte.

Pour plus d’informations, consultez [basic_string_view :: operator\[\]](#op_at) .

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

## <a name="back"></a>basic_string_view :: Back

Retourne un const_reference au dernier élément.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Valeur de retour

Const_reference au dernier élément du string_view.

### <a name="remarks"></a>Notes

Lève une exception si le string_view est vide.

Gardez à l’esprit qu’après la modification d’un string_view, par exemple en appelant `remove_suffix`, l’élément retourné par cette fonction n’est plus le dernier élément des données sous-jacentes.

### <a name="example"></a>Exemple

Une string_view construite avec un littéral de chaîne C n’inclut pas le caractère null de fin et, par conséquent, dans l’exemple suivant `back` retourne’p’et non' \ 0 '.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

Les valeurs NULL incorporées sont traitées comme n’importe quel autre caractère :

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>basic_string_view :: basic_string_view

Construit un string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Paramètres

*str*\
Pointeur vers les valeurs de caractère.

*len*\
Nombre de caractères à inclure dans la vue.

## <a name="remarks"></a>Notes

Les constructeurs avec un paramètre charT * supposent que l’entrée se termine par un caractère null, mais que la valeur null de fin n’est pas incluse dans la string_view.

Vous pouvez également construire un string_view avec un littéral. Consultez l' [opérateur «»](string-view-operators.md#op_sv).

## <a name="begin"></a>basic_string_view :: Begin

Identique à [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour
Retourne un const_iterator traitant le premier élément.

## <a name="cbegin"></a>basic_string_view :: cbegin

Retourne un const_iterator qui traite le premier élément de la plage.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur **const** à accès aléatoire qui pointe vers le premier élément de la plage, ou vers l’emplacement situé juste après la fin d’une plage vide (pour une plage vide, `cbegin() == cend()`).

## <a name="cend"></a>basic_string_view :: CEND

Retourne un const_iterator qui traite l’emplacement juste après le dernier élément d’une plage.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur **const** à accès aléatoire qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Notes

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="compare"></a>basic_string_view :: compare

Effectue une comparaison sensible à la casse avec un string_view spécifié (ou un type de chaîne convertible) pour déterminer si les deux objets sont égaux ou si l’un est vue lexicographique inférieur à l’autre. Les [opérateurs\<string_view >](string-view-operators.md) utilisent cette fonction membre pour effectuer des comparaisons.

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
String_view à comparer à ce string_view.

\ *pos*
Index de ce string_view à partir duquel la comparaison commence.

*nombre*\
Nombre maximal de caractères de cette string_view à comparer.

*num2*\
Nombre maximal de caractères de *Strv* à comparer.

*décalage*\
Index de *Strv* à partir duquel la comparaison commence.

\ *ptr*
Chaîne C à comparer à cette string_view.

### <a name="return-value"></a>Valeur de retour

Valeur négative si cette string_view est inférieure à *Strv* ou *ptr*; zéro si les deux séquences de caractères sont égales ; ou une valeur positive si cette string_view est supérieure à *Strv* ou *ptr*.

### <a name="remarks"></a>Notes

Les fonctions membres `compare` effectuent une comparaison qui respecte la casse de l’ensemble ou d’une partie de chaque séquence de caractères. 

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

## <a name="copy"></a>basic_string_view :: copier

Copie au plus un nombre spécifié de caractères à partir d’une position indexée dans un string_view source vers un tableau de caractères cible. Nous vous recommandons d’utiliser la fonction Secure [basic_string_view :: _Copy_s](#_copy_s) à la place.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Tableau de caractères cible dans lequel les éléments doivent être copiés.

*nombre*\
Nombre de caractères à copier, au maximum, à partir de la string_view source.

*décalage*\
Position de début dans le string_view source à partir de laquelle les copies doivent être effectuées.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés.

### <a name="remarks"></a>Notes

Un caractère null n’est pas ajouté à la fin de la copie.

## <a name="_copy_s"></a>basic_string_view :: _Copy_s

Fonction de copie sécurisée du CRT à utiliser à la place de [Copy](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Paramètres

*dest*\
Tableau de caractères cible dans lequel les éléments doivent être copiés.

*dest_size*\
La taille de *dest*.

_ *Count* nombre de caractères à copier, au maximum, à partir de la chaîne source.

*_Off*\
Position de début dans la chaîne source à partir de laquelle les copies doivent être effectuées.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés.

### <a name="remarks"></a>Notes

Un caractère null n’est pas ajouté à la fin de la copie.

Pour plus d’informations, consultez [c-Runtime-Library/Security-Features-in-the-CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="crbegin"></a>basic_string_view :: crbegin

Retourne un const_reverse_iterator qui traite le premier élément d’une string_view inversée.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Const_reverse_iterator qui traite le premier élément d’une string_view inversée. 

## <a name="crend"></a>basic_string_view :: crend

Identique à [rend](#rend). 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne un const_reverse_iterator qui traite un après la fin d’une string_view inversée.

## <a name="data"></a>basic_string_view ::d ATA

Retourne un pointeur non propriétaire brut à la séquence de caractères const de l’objet utilisé pour construire le string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers const qui pointe vers le premier élément de la séquence de caractères.

### <a name="remarks"></a>Notes

Le pointeur ne peut pas modifier les caractères.

Une séquence de caractères string_view ne se termine pas nécessairement par un caractère null. Le type de retour de `data` n’est pas une chaîne C valide, car aucun caractère NULL n’est ajouté. Le caractère null « \ 0 » n’a aucune signification particulière dans un objet de type string_view et peut faire partie de l’objet string_view comme n’importe quel autre caractère.

## <a name="empty"></a>basic_string_view :: Empty

Teste si le string_view contient des caractères ou non.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’objet string_view ne contient pas de caractères ; **false** si elle contient au moins un caractère.

### <a name="remarks"></a>Notes

La fonction membre est équivalente à [Size](#size)() = = 0.

## <a name="end"></a>basic_string_view :: fin

Retourne un const_iterator à accès aléatoire qui pointe vers l’un après le dernier élément.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne un const_iterator à accès aléatoire qui pointe vers l’un après le dernier élément.

### <a name="remarks"></a>Notes

`end` est utilisé pour déterminer si un const_iterator a atteint la fin de son string_view. La valeur retournée par `end` ne doit pas être déréférencée.

## <a name="find"></a>basic_string_view :: find

Recherche une string_view dans une direction vers l’avant pour la première occurrence d’un caractère ou d’une sous-chaîne qui correspond à une séquence de caractères spécifiée.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*str*\
String_view pour lequel la fonction membre doit effectuer une recherche.

*chVal*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index à partir duquel la recherche doit commencer.

\ *ptr*
Chaîne C pour laquelle la fonction membre doit effectuer une recherche.

*nombre*\
Nombre de caractères dans *ptr*, en comptant à partir du premier caractère.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="find_first_not_of"></a>basic_string_view :: find_first_not_of

Recherche le premier caractère qui n’est pas un élément d’une string_view ou d’un objet de chaîne convertible spécifié.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*str*\
String_view pour lequel la fonction membre doit effectuer une recherche.

*chVal*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index à partir duquel la recherche doit commencer.

\ *ptr*
Chaîne C pour laquelle la fonction membre doit effectuer une recherche.

*nombre*\
Nombre de caractères, en partant du premier caractère, dans la chaîne C pour laquelle la fonction membre doit être recherchée.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="find_first_of"></a>basic_string_view :: find_first_of

Recherche le premier caractère qui correspond à n’importe quel élément d’un string_view spécifié.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*chVal*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index à partir duquel la recherche doit commencer.

\ *ptr*
Chaîne C pour laquelle la fonction membre doit effectuer une recherche.

*nombre*\
Nombre de caractères, en partant du premier caractère, dans la chaîne C pour laquelle la fonction membre doit être recherchée.

*str*\
String_view pour lequel la fonction membre doit effectuer une recherche.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="find_last_not_of"></a>basic_string_view :: find_last_not_of

Recherche le dernier caractère qui n’est pas un élément d’un string_view spécifié.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*str*\
String_view pour lequel la fonction membre doit effectuer une recherche.

*chVal*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index à partir duquel la recherche doit se terminer.

\ *ptr*
Chaîne C pour laquelle la fonction membre doit effectuer une recherche.

*nombre*\
Nombre de caractères, en partant du premier caractère, dans *ptr*.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `string_view::npos`.

## <a name="find_last_of"></a>basic_string_view :: find_last_of

Recherche le dernier caractère qui correspond à n’importe quel élément d’un string_view spécifié.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*str*\
String_view pour lequel la fonction membre doit effectuer une recherche.

*chVal*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index à partir duquel la recherche doit se terminer.

\ *ptr*
Chaîne C pour laquelle la fonction membre doit effectuer une recherche.

*nombre*\
Nombre de caractères, en partant du premier caractère, dans la chaîne C pour laquelle la fonction membre doit être recherchée.

### <a name="return-value"></a>Valeur de retour

Index du dernier caractère de la sous-chaîne recherchée en cas de réussite ; sinon, `npos`.

## <a name="front"></a>basic_string_view :: front

Retourne un const_reference au premier élément.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Valeur de retour

Const_reference au premier élément.

### <a name="remarks"></a>Notes

Lève une exception si le string_view est vide.

## <a name="length"></a>basic_string_view :: length

Retourne le nombre actuel d’éléments.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre est identique à [size](#size).

## <a name="max_size"></a>basic_string_view :: max_size

Retourne le nombre maximal de caractères qu’un string_view peut contenir.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Nombre maximal de caractères qu’un string_view peut contenir.

### <a name="remarks"></a>Notes

Une exception de type [length_error](../standard-library/length-error-class.md) est levée lorsqu’une opération produit une string_view avec une longueur supérieure à `max_size()`.

## <a name="op_eq"></a>basic_string_view :: Operator =

Assigne une string_view ou un objet de chaîne convertible à une autre string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>Exemple

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>basic_string_view :: Operator []

Fournit une const_reference au caractère avec un index spécifié.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Paramètres

*décalage*\
Index de l’élément à référencer.

### <a name="return-value"></a>Valeur de retour

Const_reference au caractère à la position spécifiée par l’index de paramètre.

### <a name="remarks"></a>Notes

Le premier élément a un index égal à zéro et les éléments suivants sont indexés consécutivement par les entiers positifs, de sorte qu’une string_view de longueur *n* a un *n*ième élément indexé par le nombre *n* -1.

`operator[]` est plus rapide que [la fonction membre de pour](#at) fournir un accès en lecture aux éléments d’une string_view.

`operator[]` ne vérifie pas si l’index passé comme argument est valide. Un index non valide passé à `operator[]` entraîne un comportement indéfini.

La référence retournée peut être invalidée si les données de chaîne sous-jacentes sont modifiées ou supprimées par l’objet propriétaire.

Lors de la compilation avec [\_itérateur\_niveau de\_de débogage](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous tentez d’accéder à un élément situé en dehors des limites du string_view. Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="rbegin"></a>basic_string_view :: rbegin

Retourne un itérateur const vers le premier élément d’un string_view inversé.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne un itérateur à accès aléatoire au premier élément d’un string_view inversé, en traitant ce qui serait le dernier élément du string_view non inversé correspondant.

### <a name="remarks"></a>Notes

`rbegin` est utilisé avec un string_view inversé comme [Begin](#begin) est utilisé avec un string_view. `rbegin` peut être utilisé pour initialiser une itération vers l’arrière.

## <a name="remove_prefix"></a>basic_string_view :: remove_prefix

Déplace le pointeur vers l’avant par le nombre d’éléments spécifié.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Notes

Laisse les données sous-jacentes inchangées. Déplace le pointeur de string_view vers l’avant de n éléments et définit le membre de données `size` privé sur size-n.

## <a name="remove_suffix"></a>basic_string_view :: remove_suffix

Réduit la taille de la vue par le nombre spécifié d’éléments à partir de l’arrière-plan.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Notes

Laisse les données sous-jacentes et le pointeur vers elles inchangées. Définit le membre de données de `size` privé sur size-n.

## <a name="rend"></a>basic_string_view :: rend

Retourne un itérateur const qui pointe vers un après le dernier élément d’un string_view inversé.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur const inversé à accès aléatoire qui pointe vers l’un après le dernier élément d’un string_view inversé.

### <a name="remarks"></a>Notes

`rend` est utilisé avec un string_view inversé comme [end](#end) est utilisé avec un string_view. `rend` peut être utilisé pour tester si un itérateur inversé a atteint la fin de son string_view. La valeur retournée par `rend` ne doit pas être déréférencée.

## <a name="rfind"></a>basic_string_view :: RFind

Recherche une string_view en sens inverse pour une sous-chaîne qui correspond à une séquence de caractères spécifiée.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*chVal*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index à partir duquel la recherche doit commencer.

\ *ptr*
Chaîne C pour laquelle la fonction membre doit effectuer une recherche.

*nombre*\
Nombre de caractères, en partant du premier caractère, dans la chaîne C pour laquelle la fonction membre doit être recherchée.

*str*\
String_view pour lequel la fonction membre doit effectuer une recherche.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne en cas de réussite ; sinon `npos`.

## <a name="size"></a>basic_string_view :: Size

Retourne le nombre d’éléments dans le string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Longueur de la string_view.

### <a name="remarks"></a>Notes

Une string_view peut modifier sa longueur, par exemple en `remove_prefix` et `remove_suffix`. Étant donné que cela ne modifie pas les données de chaîne sous-jacentes, la taille d’un string_view n’est pas nécessairement la taille des données sous-jacentes.

## <a name="substr"></a>basic_string_view :: substr

Retourne un string_view qui représente (au plus) le nombre spécifié de caractères à partir d’une position spécifiée.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Paramètres

*décalage*\
Index qui localise l’élément à la position à partir de laquelle la copie est effectuée, avec une valeur par défaut de 0.

*nombre*\
Nombre de caractères à inclure dans la sous-chaîne, s’ils sont présents.

### <a name="return-value"></a>Valeur de retour

Objet string_view qui représente la sous-séquence spécifiée d’éléments.

## <a name="swap"></a>basic_string_view :: swap

Échange deux string_views, en d’autres termes, les pointeurs vers les données de chaîne sous-jacentes et les valeurs de taille.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Paramètres

\ *SV*
String_view source dont les valeurs de pointeur et de taille doivent être échangées avec celles du string_view de destination.

## <a name="see-also"></a>Voir aussi

[\<string_view >](../standard-library/string-view.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
