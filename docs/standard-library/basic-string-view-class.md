---
title: basic_string_view, classe
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
ms.openlocfilehash: 0ac5e3d528881f7b1caa0a1dcdae0161a6777e57
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346937"
---
# <a name="basicstringview-class"></a>basic_string_view, classe

Le modèle de classe `basic_string_view<charT>` a été ajouté dans C ++ 17 à utiliser comme un moyen sécurisé et efficace pour une fonction accepter différents sans rapport avec les types de chaîne sans la fonction d’avoir au transformer en modèle sur ces types. La classe conserve un pointeur non propriétaire à une séquence contiguë de données de caractères et une longueur qui spécifie le nombre de caractères dans la séquence. Aucune hypothèse n’est faite en ce qui concerne si la séquence est terminée.

La bibliothèque standard définit plusieurs spécialisations en fonction du type des éléments :

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

Dans ce document, le terme « string_view » fait généralement référence à un de ces typedefs.

Un string_view décrit l’interface commune minimale nécessaire pour lire les données de chaîne. Il fournit un accès const pour les données sous-jacentes ; Il ne rend aucune copie (à l’exception de la `copy` (fonction)). Les données peuvent ou ne peuvent pas contenir de valeurs null ('\0') à n’importe quelle position. Un string_view n’a aucun contrôle sur la durée de vie de l’objet. Il est responsable de l’appelant pour s’assurer que les données sous-jacentes de la chaîne sont valides.

Une fonction qui accepte un paramètre de type string_view possible de faire fonctionner avec n’importe quel type de chaîne de type, sans en définissant la fonction dans un modèle ou en limitant la fonction à un sous-ensemble de types de chaîne particulier. La seule exigence est qu’une conversion implicite existe à partir du type de chaîne pour string_view. Tous les types de chaîne standard sont implicitement convertibles en un string_view qui contient le même type d’élément. En d’autres termes, une `std::string` est convertible en un `string_view` mais pas à un `wstring_view`.

L’exemple suivant montre une fonction sans modèle `f` qui accepte un paramètre de type `wstring_view`. Elle peut être appelée avec des arguments de type `std::wstring`, `wchar_t*`, et `winrt::hstring`.

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

*CharType*<br/>
Le type de caractères qui sont stockés dans le string_view. Le C++ bibliothèque Standard fournit les typedefs suivants pour les spécialisations de ce modèle.
- [string_view](../standard-library/string-view-typedefs.md#string_view) pour les éléments de type **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), pour **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) pour **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) pour **char32_t**.

*Caractéristiques*<br/>
Valeur par défaut est [char_traits](char-traits-struct.md)<*CharType*>.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_string_view](#basic_string_view)|Construit un string_view qui est vide, sans quoi pointe à tout ou partie des données de certains autres chaîne l’objet, ou vers un tableau de caractères de style C.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|**const_iterator**|Itérateur d’accès aléatoire qui peut lire **const** éléments.|
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

### <a name="member-operators"></a>Opérateurs de membre

|Opérateur|Description|
|-|-|
|[operator=](#op_eq)|Assigne un objet de chaîne string_view ou convertible à un autre string_view.|
|[operator\[\]](#op_at)|Retourne l'élément à l'index spécifié.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[at](#at)|Retourne un const_reference à l’élément à un emplacement spécifié.|
|[back](#back)|Retourne un const_reference jusqu’au dernier élément.|
|[begin](#begin)|Retourne un itérateur const qui traite le premier élément. (string_views sont immuables).|
|[cbegin](#cbegin)|Identique à [commencer](#begin).|
|[cend](#cend)|Retourne un itérateur const qui pointe juste après le dernier élément.|
|[copy](#copy)|Copie au plus un nombre spécifié de caractères à partir d’une position indexée dans une source de string_view dans un tableau de caractères cible. (Non recommandé. Utilisez _Copy_s à la place.)|
|[_Copy_s](#_copy_s)|Fonction de copie sécurisée CRT.|
|[compare](#compare)|Compare un string_view avec un string_view spécifié pour déterminer s’ils sont égaux ou si un n’est pas inférieure à l’autre point de vue lexicographique.|
|[crbegin](#crbegin)|Identique à [rbegin](#rbegin).|
|[crend](#crend)|Identique à [rend](#rend).|
|[data](#data)|Retourne un pointeur brut non propriétaire à la séquence de caractères.|
|[empty](#empty)|Teste si le string_view contient des caractères.|
|[end](#end)|Identique à [cend](#cend).|
|[find](#find)|Recherche vers l’avant pour la première occurrence d’une sous-chaîne qui correspond à une séquence de caractères spécifiée.|
|[find_first_not_of](#find_first_not_of)|Recherche le premier caractère qui n’est pas un élément d’un objet de chaîne convertibles ou un string_view spécifié.|
|[find_first_of](#find_first_of)|Recherche le premier caractère qui correspond à n’importe quel élément d’un objet de chaîne convertibles ou un string_view spécifié.|
|[find_last_not_of](#find_last_not_of)|Recherche le dernier caractère qui n’est pas un élément d’un objet de chaîne convertibles ou un string_view spécifié.|
|[find_last_of](#find_last_of)|Recherche le dernier caractère qui est un élément d’un objet de chaîne convertibles ou un string_view spécifié.|
|[front](#front)|Retourne un const_reference vers le premier élément.|
|[length](#length)|Retourne le nombre actuel d’éléments.|
|[max_size](#max_size)|Retourne le nombre maximal de caractères qu'un string_view peut contenir.|
|[rbegin](#rbegin)|Retourne un itérateur const qui traite le premier élément dans un string_view inversé.|
|[remove_prefix](#remove_prefix)|Déplace le pointeur vers l’avant par le nombre spécifié d’éléments.|
|[remove_suffix](#remove_suffix)|Réduit la taille de la vue par le nombre spécifié d’éléments à partir de l’arrière.|
|[rend](#rend)|Retourne un itérateur const qui pointe juste après le dernier élément d’un string_view inversé.|
|[rfind](#rfind)|Recherche un string_view dans l’ordre inverse pour la première occurrence d’une sous-chaîne qui correspond à une séquence de caractères spécifiée.|
|[size](#size)|Retourne le nombre actuel d’éléments.|
|[substr](#substr)|Retourne une sous-chaîne d’une longueur spécifiée, en commençant à un index spécifié.|
|[swap](#swap)|Échange le contenu de deux string_views.|

## <a name="remarks"></a>Notes

Si une fonction doit générer une séquence supérieure à [max_size](#max_size) éléments, la fonction signale une erreur de longueur en levant un objet de type [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Configuration requise

[std : c ++ 17](../build/reference/std-specify-language-standard-version.md) ou version ultérieure

**En-tête :** \<string_view >

**Espace de noms :** std

## <a name="at"></a>  basic_string_view::at

Retourne un const_reference pour le caractère situé à l’index spécifié à partir de 0.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
L’index de l’élément à référencer.

### <a name="return-value"></a>Valeur de retour

Un const_reference pour le caractère situé à la position spécifiée par l’index de paramètre.

### <a name="remarks"></a>Notes

Le premier élément possède un index de zéro et les éléments suivants sont indexés consécutivement par les entiers positifs, afin qu’un string_view de longueur *n* a un *n*-ième élément indexé par le nombre *n -* 1. **à** lève une exception pour les index non valide, contrairement à [opérateur\[\]](#op_at). 

En règle générale, nous vous recommandons **à** pour les séquences comme `std::vector` et string_view ne doit jamais être utilisée. Un index non valide passé à une séquence est une erreur logique qui doit être détectée et résolue pendant le développement. Si un programme n’est pas absolument certain que ses index sont valides, testez-les, pas appeler at() et s’appuient sur les exceptions pour se défendre contre programmation négligents.

Consultez [basic_string_view::operator\[ \] ](#op_at) pour plus d’informations.

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

## <a name="back"></a>  basic_string_view::back

Retourne un const_reference jusqu’au dernier élément.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Valeur de retour

Un const_reference jusqu’au dernier élément dans le string_view.

### <a name="remarks"></a>Notes

Lève une exception si la string_view est vide.

N’oubliez pas que, après un string_view est modifiée, par exemple en appelant `remove_suffix`, puis l’élément retourné par cette fonction n’est plus le dernier élément dans les données sous-jacentes.

### <a name="example"></a>Exemple

Un string_view qui est construit avec un littéral de chaîne C n’inclut pas le caractère null de fin et par conséquent, dans l’exemple suivant `back` retourne « p » et pas « \0 ».

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

Valeurs null incorporées sont traités comme tout autre caractère :

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>  basic_string_view::basic_string_view

Construit un string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Pointeur vers les valeurs de caractère.

*len*<br/>
Le nombre de caractères à inclure dans la vue.

## <a name="remarks"></a>Notes

Les constructeurs avec un paramètre graphique * supposent que l’entrée est nul, mais que le caractère null de fin n’est pas inclus dans le string_view.

Vous pouvez également construire un string_view avec un littéral. Consultez [opérateur » « sv](string-view-operators.md#op_sv).

## <a name="begin"></a>  basic_string_view::begin

Identique à [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour
Retourne un const_iterator qui traite le premier élément.

## <a name="cbegin"></a>  basic_string_view::cbegin

Retourne un const_iterator qui traite le premier élément dans la plage.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un **const** itérateur à accès aléatoire qui pointe vers le premier élément de la plage ou l’emplacement juste après la fin d’une plage vide (pour une plage vide, `cbegin() == cend()`).

## <a name="cend"></a>  basic_string_view::cend

Retourne un const_iterator qui traite l’emplacement juste après le dernier élément dans une plage.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un **const** itérateur à accès aléatoire qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Notes

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="compare"></a> basic_string_view::compare

Effectue une comparaison respectant la casse avec un string_view spécifié (ou un type de chaîne convertibles) pour déterminer si les deux objets sont égaux ou si un n’est pas inférieure à l’autre point de vue lexicographique. Le [ \<string_view > opérateurs](string-view-operators.md) utiliser cette fonction membre pour effectuer des comparaisons.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Paramètres

*strv*<br/>
String_view qui consiste à comparer à cette string_view.

*pos*<br/>
Index de cette string_view à partir duquel commence la comparaison.

*num*<br/>
Le nombre maximal de caractères à partir de cette string_view à comparer.

*num2*<br/>
Le nombre maximal de caractères à partir de *strv* à comparer.

*offset*<br/>
L’index de *strv* au niveau duquel commence la comparaison.

*ptr*<br/>
La chaîne C à comparer à cette string_view.

### <a name="return-value"></a>Valeur de retour

Une valeur négative si cette string_view est inférieure à *strv* ou *ptr*; zéro si les séquences de deux caractères sont égales ; ou une valeur positive si cette string_view est supérieur à *strv*ou *ptr*.

### <a name="remarks"></a>Notes

Le `compare` des fonctions de membre effectuent une comparaison respectant la casse de tout ou partie de chaque séquence de caractères. 

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

## <a name="copy"></a>  basic_string_view::copy

Copie au plus un nombre spécifié de caractères à partir d’une position indexée dans une source de string_view dans un tableau de caractères cible. Nous vous recommandons d’utiliser la fonction sécurisée [basic_string_view::_Copy_s](#_copy_s) à la place.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
Tableau de caractères cible dans lequel les éléments doivent être copiés.

*count*<br/>
Le nombre de caractères à copier, au maximum, à partir de la source de string_view.

*offset*<br/>
Position de début dans la source de string_view à partir de laquelle les copies doivent être effectuées.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés.

### <a name="remarks"></a>Notes

Un caractère null n’est pas ajouté à la fin de la copie.

## <a name="_copy_s"></a>  basic_string_view::_Copy_s

Sécuriser la fonction de copie de CRT à être utilisée au lieu de [copie](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Paramètres

*dest*<br/>
Tableau de caractères cible dans lequel les éléments doivent être copiés.

*dest_size*<br/>
La taille de *dest*.

_ *Nombre* le nombre de caractères à copier, au maximum, à partir de la chaîne source.

*_Off*<br/>
Position de début dans la chaîne source à partir de laquelle les copies doivent être effectuées.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés.

### <a name="remarks"></a>Notes

Un caractère null n’est pas ajouté à la fin de la copie.

 Pour plus d’informations, consultez [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="crbegin"></a>  basic_string_view::crbegin

Retourne un const_reverse_iterator qui traite le premier élément dans un string_view inversé.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Const_reverse_iterator qui traite le premier élément dans un string_view inversé. 

## <a name="crend"></a>  basic_string_view::crend

Identique à [rend](#rend). 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne un const_reverse_iterator qui résout l’une après la fin d’un string_view inversé.

## <a name="data"></a>  basic_string_view::data

Retourne un pointeur brut non propriétaire à la séquence de caractères const de l’objet qui a été utilisé pour construire le string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Pointeur-à-const vers le premier élément de la séquence de caractères.

### <a name="remarks"></a>Notes

Le pointeur ne peut pas modifier les caractères.

Une séquence de caractères de string_view n’est pas nécessairement se terminant par null. Le type de retour pour `data` n’est pas une chaîne C valide, car aucun caractère null n’est ajouté. Le caractère null « \0 » n’a aucune signification spéciale dans un objet de type string_view et peut faire partie de l’objet de string_view juste comme tout autre caractère.

## <a name="empty"></a>  basic_string_view::empty

Teste si le string_view contient des caractères ou non.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’objet string_view ne contient aucun caractère ; **false** s’il a au moins un caractère.

### <a name="remarks"></a>Notes

La fonction membre est équivalente à [taille](#size)() == 0.

## <a name="end"></a>  basic_string_view::end

Retourne un const_iterator à accès aléatoire qui pointe juste après le dernier élément.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne un const_iterator à accès aléatoire qui pointe juste après le dernier élément.

### <a name="remarks"></a>Notes

`end` est utilisé pour déterminer si un const_iterator a atteint la fin de son string_view. La valeur retournée par `end` ne doit pas être déréférencée.

## <a name="find"></a>  basic_string_view::find

Recherche un string_view vers l’avant pour la première occurrence d’un caractère ou d’une sous-chaîne qui correspond à une séquence spécifique de caractères.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*str*<br/>
String_view pour laquelle la fonction membre doit rechercher.

*chVal*<br/>
Valeur de caractère que la fonction membre doit rechercher.

*offset*<br/>
Index au niveau duquel la recherche doit commencer.

*ptr*<br/>
La chaîne C pour laquelle la fonction membre doit rechercher.

*count*<br/>
Le nombre de caractères dans *ptr*, comptant à partir du premier caractère.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="find_first_not_of"></a>  basic_string_view::find_first_not_of

Recherche le premier caractère qui n’est pas un élément d’un objet de chaîne convertibles ou un string_view spécifié.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*str*<br/>
String_view pour laquelle la fonction membre doit rechercher.

*chVal*<br/>
Valeur de caractère que la fonction membre doit rechercher.

*offset*<br/>
Index au niveau duquel la recherche doit commencer.

*ptr*<br/>
La chaîne C pour laquelle la fonction membre doit rechercher.

*count*<br/>
Le nombre de caractères, en comptant à partir du premier caractère, dans la chaîne C pour laquelle la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="find_first_of"></a>  basic_string_view::find_first_of

Recherche le premier caractère qui correspond à n’importe quel élément d’un string_view spécifié.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*chVal*<br/>
Valeur de caractère que la fonction membre doit rechercher.

*offset*<br/>
Index au niveau duquel la recherche doit commencer.

*ptr*<br/>
La chaîne C pour laquelle la fonction membre doit rechercher.

*count*<br/>
Le nombre de caractères, en comptant à partir du premier caractère, dans la chaîne C pour laquelle la fonction membre doit rechercher.

*str*<br/>
String_view pour laquelle la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

## <a name="find_last_not_of"></a>  basic_string_view::find_last_not_of

Recherche le dernier caractère qui n’est pas un élément d’un string_view spécifié.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*str*<br/>
String_view pour laquelle la fonction membre doit rechercher.

*chVal*<br/>
Valeur de caractère que la fonction membre doit rechercher.

*offset*<br/>
Index au niveau duquel la recherche doit se terminer.

*ptr*<br/>
La chaîne C pour laquelle la fonction membre doit rechercher.

*count*<br/>
Le nombre de caractères, en comptant à partir du premier caractère, en *ptr*.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `string_view::npos`.

## <a name="find_last_of"></a>  basic_string_view::find_last_of

Recherche le dernier caractère qui correspond à n’importe quel élément d’un string_view spécifié.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*str*<br/>
String_view pour laquelle la fonction membre doit rechercher.

*chVal*<br/>
Valeur de caractère que la fonction membre doit rechercher.

*offset*<br/>
Index au niveau duquel la recherche doit se terminer.

*ptr*<br/>
La chaîne C pour laquelle la fonction membre doit rechercher.

*count*<br/>
Le nombre de caractères, en comptant à partir du premier caractère, dans la chaîne C pour laquelle la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index du dernier caractère de la sous-chaîne recherchée en cas de réussite ; sinon, `npos`.

## <a name="front"></a>  basic_string_view::front

Retourne un const_reference vers le premier élément.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Valeur de retour

Un const_reference vers le premier élément.

### <a name="remarks"></a>Notes

Lève une exception si la string_view est vide.

## <a name="length"></a> basic_string_view::length

Retourne le nombre actuel d’éléments.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre est identique à [size](#size).

## <a name="max_size"></a>  basic_string_view::max_size

Retourne le nombre maximal de caractères qu'un string_view peut contenir.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximal de caractères qu’une string_view peut contenir.

### <a name="remarks"></a>Notes

Une exception de type [length_error](../standard-library/length-error-class.md) est levée lorsqu’une opération engendre un string_view avec une longueur supérieure à `max_size()`.

## <a name="op_eq"></a>  basic_string_view::operator=

Assigne un objet de chaîne string_view ou convertible à un autre string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>Exemple

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>  basic_string_view::operator[]

Fournit un const_reference au caractère avec un index spécifié.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
L’index de l’élément à référencer.

### <a name="return-value"></a>Valeur de retour

Un const_reference pour le caractère situé à la position spécifiée par l’index de paramètre.

### <a name="remarks"></a>Notes

Le premier élément a un index égal à zéro, et les éléments suivants sont indexés consécutivement par les entiers positifs, afin qu’un string_view de longueur *n* a un *n*-ième élément indexé par le nombre *n* - 1.

`operator[]` est plus rapide que la fonction membre [à](#at) pour fournir un accès en lecture aux éléments d’un string_view.

`operator[]` ne vérifie pas si l’index passé comme un argument est valide. Un index non valide passé à `operator[]` entraîne un comportement non défini.

La référence retournée peut être invalidée si les données de chaîne sous-jacente sont modifiées ou supprimées par l’objet propriétaire.

Lors de la compilation avec [ \_ITÉRATEUR\_déboguer\_niveau](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produira si vous tentez d’accéder à un élément en dehors des limites de la string_view. Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="rbegin"></a>  basic_string_view::rbegin

Retourne un itérateur const vers le premier élément dans un string_view inversé.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Retourne un itérateur à accès aléatoire vers le premier élément dans un string_view inversé, qui cible le dernier élément dans le correspondantes string_view non inversé.

### <a name="remarks"></a>Notes

`rbegin` est utilisé avec un string_view inversé comme [commencer](#begin) est utilisé avec un string_view. `rbegin` peut être utilisé pour initialiser une itération vers l’arrière.

## <a name="remove_prefix"></a> basic_string_view::remove_prefix

Déplace le pointeur vers l’avant par le nombre spécifié d’éléments.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Notes

Laisse les données sous-jacentes inchangées. Déplace le pointeur de string_view transférer par n éléments et définit le privé `size` taille - n des données membres.

## <a name="remove_suffix"></a> basic_string_view::remove_suffix

Réduit la taille de la vue par le nombre spécifié d’éléments à partir de l’arrière.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Notes

Laisse les données sous-jacentes et le pointeur à inchangé. Définit le privé `size` taille - n des données membres.

## <a name="rend"></a>  basic_string_view::rend

Retourne un itérateur const qui pointe juste après le dernier élément d’un string_view inversé.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Itérateur d’accès aléatoire qui pointe juste après le dernier élément d’un string_view inversé inversé const.

### <a name="remarks"></a>Notes

`rend` est utilisé avec un string_view inversé comme [fin](#end) est utilisé avec un string_view. `rend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de son string_view. La valeur retournée par `rend` ne doit pas être déréférencée.

## <a name="rfind"></a>  basic_string_view::rfind

Recherche un string_view dans l’ordre inverse d’une sous-chaîne qui correspond à une séquence de caractères spécifiée.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*chVal*<br/>
Valeur de caractère que la fonction membre doit rechercher.

*offset*<br/>
Index au niveau duquel la recherche doit commencer.

*ptr*<br/>
La chaîne C pour laquelle la fonction membre doit rechercher.

*count*<br/>
Le nombre de caractères, en comptant à partir du premier caractère, dans la chaîne C pour laquelle la fonction membre doit rechercher.

*str*<br/>
String_view pour laquelle la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

L’index du premier caractère de la sous-chaîne en cas de réussite ; sinon `npos`.

## <a name="size"></a>  basic_string_view::size

Retourne le nombre d’éléments dans le string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

La longueur de la string_view.

### <a name="remarks"></a>Notes

Un string_view peut modifier sa longueur, par exemple en `remove_prefix` et `remove_suffix`. Étant donné que cela ne modifie pas les données sous-jacentes de la chaîne, la taille d’un string_view n’est pas nécessairement la taille des données sous-jacentes.

## <a name="substr"></a>  basic_string_view::substr

Retourne un string_view représentant (au plus) le nombre spécifié de caractères à partir d’une position spécifiée.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
Index situant l’élément à la position à partir de laquelle la copie est effectuée, avec la valeur par défaut 0.

*count*<br/>
Le nombre de caractères à inclure dans la sous-chaîne, s’ils sont présents.

### <a name="return-value"></a>Valeur de retour

Un objet de string_view qui représente la séquence d’éléments secondaires spécifiée.

## <a name="swap"></a>  basic_string_view::swap

Échange deux string_views, en d’autres termes les pointeurs vers les données de chaîne sous-jacentes et les valeurs de taille.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Paramètres

*sv*<br/>
La source string_view dont les valeurs de pointeur et la taille doivent être échangés avec celle de la destination de string_view.

## <a name="see-also"></a>Voir aussi

[\<string_view>](../standard-library/string-view.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
