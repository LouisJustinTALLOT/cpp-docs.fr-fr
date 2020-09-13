---
title: basic_string, classe
description: Référence d’API pour la `basic_string` classe, qui est la classe de chaîne C++ standard.
ms.date: 9/10/2020
f1_keywords:
- xstring/std::basic_string
- xstring/std::basic_string::allocator_type
- xstring/std::basic_string::const_iterator
- xstring/std::basic_string::const_pointer
- xstring/std::basic_string::const_reference
- xstring/std::basic_string::const_reverse_iterator
- xstring/std::basic_string::difference_type
- xstring/std::basic_string::iterator
- xstring/std::basic_string::npos
- xstring/std::basic_string::pointer
- xstring/std::basic_string::reference
- xstring/std::basic_string::reverse_iterator
- xstring/std::basic_string::size_type
- xstring/std::basic_string::traits_type
- xstring/std::basic_string::value_type
- xstring/std::basic_string::append
- xstring/std::basic_string::assign
- xstring/std::basic_string::at
- xstring/std::basic_string::back
- xstring/std::basic_string::begin
- xstring/std::basic_string::c_str
- xstring/std::basic_string::capacity
- xstring/std::basic_string::cbegin
- xstring/std::basic_string::cend
- xstring/std::basic_string::clear
- xstring/std::basic_string::compare
- xstring/std::basic_string::copy
- xstring/std::basic_string::crbegin
- xstring/std::basic_string::crend
- xstring/std::basic_string::_Copy_s
- xstring/std::basic_string::data
- xstring/std::basic_string::empty
- xstring/std::basic_string::end
- xstring/std::basic_string::erase
- xstring/std::basic_string::find
- xstring/std::basic_string::find_first_not_of
- xstring/std::basic_string::find_first_of
- xstring/std::basic_string::find_last_not_of
- xstring/std::basic_string::find_last_of
- xstring/std::basic_string::front
- xstring/std::basic_string::get_allocator
- xstring/std::basic_string::insert
- xstring/std::basic_string::length
- xstring/std::basic_string::max_size
- xstring/std::basic_string::pop_back
- xstring/std::basic_string::push_back
- xstring/std::basic_string::rbegin
- xstring/std::basic_string::rend
- xstring/std::basic_string::replace
- xstring/std::basic_string::reserve
- xstring/std::basic_string::resize
- xstring/std::basic_string::rfind
- xstring/std::basic_string::shrink_to_fit
- xstring/std::basic_string::size
- xstring/std::basic_string::substr
- xstring/std::basic_string::ends_with
- xstring/std::basic_string::starts_with
- xstring/std::basic_string::swap
helpviewer_keywords:
- std::basic_string [C++]
- std::basic_string [C++], allocator_type
- std::basic_string [C++], const_iterator
- std::basic_string [C++], const_pointer
- std::basic_string [C++], const_reference
- std::basic_string [C++], const_reverse_iterator
- std::basic_string [C++], difference_type
- std::basic_string [C++], iterator
- std::basic_string [C++], npos
- std::basic_string [C++], pointer
- std::basic_string [C++], reference
- std::basic_string [C++], reverse_iterator
- std::basic_string [C++], size_type
- std::basic_string [C++], traits_type
- std::basic_string [C++], value_type
- std::basic_string [C++], append
- std::basic_string [C++], assign
- std::basic_string [C++], at
- std::basic_string [C++], back
- std::basic_string [C++], begin
- std::basic_string [C++], c_str
- std::basic_string [C++], capacity
- std::basic_string [C++], cbegin
- std::basic_string [C++], cend
- std::basic_string [C++], clear
- std::basic_string [C++], compare
- std::basic_string [C++], copy
- std::basic_string [C++], crbegin
- std::basic_string [C++], crend
- std::basic_string [C++], _Copy_s
- std::basic_string [C++], data
- std::basic_string [C++], empty
- std::basic_string [C++], end
- std::basic_string [C++], erase
- std::basic_string [C++], find
- std::basic_string [C++], find_first_not_of
- std::basic_string [C++], find_first_of
- std::basic_string [C++], find_last_not_of
- std::basic_string [C++], find_last_of
- std::basic_string [C++], front
- std::basic_string [C++], get_allocator
- std::basic_string [C++], insert
- std::basic_string [C++], length
- std::basic_string [C++], max_size
- std::basic_string [C++], pop_back
- std::basic_string [C++], push_back
- std::basic_string [C++], rbegin
- std::basic_string [C++], rend
- std::basic_string [C++], replace
- std::basic_string [C++], reserve
- std::basic_string [C++], resize
- std::basic_string [C++], rfind
- std::basic_string [C++], shrink_to_fit
- std::basic_string [C++], size
- std::basic_string [C++], starts_with
- std::basic_string [C++], ends_with
- std::basic_string [C++], substr
- std::basic_string [C++], swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 9012fc8203bf8b54e87e2c21f47f2ef6ef764c2d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040309"
---
# <a name="basic_string-class"></a>basic_string, classe

Les séquences contrôlées par un objet de type `basic_string` sont la classe de chaîne C++ standard et sont généralement appelées chaînes, mais elles ne doivent pas être confondues avec les chaînes de style C se terminant par un caractère null utilisées dans l’ensemble de la bibliothèque standard C++. La chaîne C++ Standard est un conteneur qui permet d’utiliser les chaînes comme types normaux, par exemple pour les opérations de comparaison et de concaténation, les itérateurs, les algorithmes de la bibliothèque C++ Standard, ainsi que les opérations de copie et d’assignation avec la mémoire gérée par la classe allocator. Si vous devez convertir une chaîne C++ Standard en chaîne de style C se terminant par un caractère null, utilisez le membre [basic_string::c_str](#c_str).

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_string;
```

### <a name="parameters"></a>Paramètres

*CharType*\
Type de données d'un seul caractère à stocker dans la chaîne. La bibliothèque C++ standard fournit des spécialisations de ce modèle de classe, avec la [chaîne](../standard-library/string-typedefs.md#string) des définitions de type pour les éléments de type **`char`** , [wstring](../standard-library/string-typedefs.md#wstring), pour **`wchar_t`** , [u16string](../standard-library/string-typedefs.md#u16string) pour **`char16_t`** et [u32string](../standard-library/string-typedefs.md#u32string) pour **`char32_t`** .

*Caractéristiques*\
Plusieurs propriétés importantes des `CharType` éléments d’une spécialisation basic_string sont décrites par la classe `Traits` . La valeur par défaut est `char_traits`< `CharType`>.

*Allocateur*\
Type qui représente l'objet allocateur stocké qui contient des informations sur l'allocation et la libération de mémoire de la chaîne. La valeur par défaut est `allocator<CharType>`.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_string](#basic_string)|Construit une chaîne vide ou initialisée par des caractères spécifiques, ou qui représente une copie complète ou partielle d'un autre objet string ou d'une autre chaîne de style C.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe `allocator` d'un objet string.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur à accès aléatoire qui peut accéder à un **`const`** élément dans la chaîne et le lire.|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur vers un **`const`** élément d’une chaîne.|
|[const_reference](#const_reference)|Type qui fournit une référence à un **`const`** élément stocké dans une chaîne pour la lecture et l’exécution d' **`const`** opérations.|
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur à accès aléatoire capable de lire un **`const`** élément de la chaîne.|
|[difference_type](#difference_type)|Type qui fournit la différence entre deux itérateurs qui font référence aux éléments d'une même chaîne.|
|[répétiteur](#iterator)|Type qui fournit un itérateur à accès aléatoire pouvant lire ou modifier un élément d'une chaîne.|
|[npos](#npos)|Valeur intégrale non signée initialisée à-1 qui indique « introuvable » ou « tous les caractères restants » quand une fonction de recherche échoue.|
|[dirigé](#pointer)|Type qui fournit un pointeur vers un élément caractère d'une chaîne ou d'un tableau de caractères.|
|[reference](#reference)|Type qui fournit une référence à un élément stocké dans une chaîne.|
|[reverse_iterator](#reverse_iterator)|Type qui fournit un itérateur à accès aléatoire pouvant lire ou modifier un élément d'une chaîne inversée.|
|[size_type](#size_type)|Type intégral non signé pour le nombre d'éléments d'une chaîne.|
|[traits_type](#traits_type)|Type pour les caractéristiques de caractère des éléments stockés dans une chaîne.|
|[value_type](#value_type)|Type qui représente le type des caractères stockés dans une chaîne.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[append](#append)|Ajoute des caractères à la fin d'une chaîne.|
|[assign](#assign)|Assigne de nouvelles valeurs de caractère au contenu d'une chaîne.|
|[at](#at)|Retourne une référence à l'élément à un emplacement spécifié dans la chaîne.|
|[Précédent](#back)||
|[commencer](#begin)|Retourne un itérateur qui traite le premier élément de la chaîne.|
|[c_str](#c_str)|Convertit le contenu d'une chaîne en chaîne de style C se terminant par un caractère Null.|
|[maximale](#capacity)|Retourne le plus grand nombre d'éléments qui peuvent être stockés dans une chaîne sans augmenter l'allocation de mémoire de la chaîne.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément de la chaîne.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement situé après le dernier élément d'une chaîne.|
|[clear](#clear)|Efface tous les éléments d'une chaîne.|
|[compar](#compare)|Compare une chaîne à une chaîne spécifique pour déterminer si les deux chaînes sont équivalentes, ou si l'une est inférieure à l'autre d'un point de vue lexicographique.|
|[copy](#copy)|Copie tout au plus un nombre spécifique de caractères d'une position indexée dans une chaîne source vers un tableau de caractères cible. Action déconseillée. Utilisez [basic_string::_Copy_s](#copy_s) à la place.|
|[crbegin](#crbegin)|Retourne un itérateur const qui traite le premier élément d'une chaîne inversée.|
|[crend](#crend)|Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'une chaîne inversée.|
|[_Copy_s](#copy_s)|Copie tout au plus un nombre spécifique de caractères d'une position indexée dans une chaîne source vers un tableau de caractères cible.|
|[data](#data)|Convertit le contenu d'une chaîne en tableau de caractères.|
|[empty](#empty)|Effectue un test pour déterminer si la chaîne contient des caractères.|
|[end](#end)|Retourne un itérateur qui traite l'emplacement qui suit le dernier élément d'une chaîne.|
|[ends_with](#ends_with)<sup>c++ 20</sup>|Vérifie si la chaîne se termine par le suffixe spécifié.|
|[erase](#erase)|Supprime un élément ou une plage d'éléments dans une chaîne à partir de l'emplacement spécifié.|
|[find](#find)|Recherche une chaîne vers l'avant pour trouver la première occurrence d'une sous-chaîne qui correspond à une séquence spécifique de caractères.|
|[find_first_not_of](#find_first_not_of)|Recherche dans une chaîne le premier caractère qui n’est pas un élément d’une chaîne spécifiée.|
|[find_first_of](#find_first_of)|Recherche dans une chaîne le premier caractère qui correspond à un élément de la chaîne spécifiée.|
|[find_last_not_of](#find_last_not_of)|Recherche dans une chaîne le dernier caractère qui n’est pas un élément d’une chaîne spécifiée.|
|[find_last_of](#find_last_of)|Recherche dans une chaîne le dernier caractère qui est un élément de la chaîne spécifiée.|
|[frontal](#front)|Retourne une référence au premier élément d'une chaîne.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` utilisé pour construire la chaîne.|
|[insert](#insert)|Insère un élément, un certain nombre d'éléments ou une plage d'éléments dans la chaîne à la position spécifiée.|
|[length](#length)|Retourne le nombre actuel d'éléments contenus dans une chaîne.|
|[max_size](#max_size)|Retourne le nombre maximal de caractères qu'une chaîne peut contenir.|
|[pop_back](#pop_back)|Efface le dernier élément de la chaîne.|
|[push_back](#push_back)|Ajoute un élément à la fin de la chaîne.|
|[rbegin](#rbegin)|Retourne un itérateur au premier élément d'une chaîne inversée.|
|[rend](#rend)|Retourne un itérateur qui pointe juste après le dernier élément d'une chaîne inversée.|
|[replace](#replace)|Remplace les éléments d'une chaîne à la position spécifiée par des caractères spécifiques ou des caractères copiés à partir d'autres plages, chaînes ou chaînes de style C.|
|[reserve](#reserve)|Définit la capacité de la chaîne en fonction d'un nombre au moins aussi grand que le nombre spécifié.|
|[redimensionner](#resize)|Spécifie une nouvelle taille pour une chaîne, en ajoutant ou en effaçant des éléments selon les besoins.|
|[rfind](#rfind)|Recherche une chaîne vers l'arrière pour trouver la première occurrence d'une sous-chaîne qui correspond à une séquence spécifique de caractères.|
|[shrink_to_fit](#shrink_to_fit)|Ignore la capacité excédentaire de la chaîne.|
|[size](#size)|Retourne le nombre actuel d'éléments contenus dans une chaîne.|
|[starts_with](#starts_with)<sup>c++ 20</sup>|Vérifie si la chaîne commence par le préfixe spécifié.|
|[substr](#substr)|Copie une sous-chaîne d'un certain nombre de caractères dans une chaîne qui commence à la position spécifiée.|
|[swap](#swap)|Échange le contenu de deux chaînes.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur + =](#op_add_eq)|Ajoute des caractères à une chaîne.|
|[opérateur =](#op_eq)|Assigne de nouvelles valeurs de caractère au contenu d'une chaîne.|
|[operator&#91;&#93;](#op_at)|Fournit une référence au caractère situé à l'index spécifié dans une chaîne.|

## <a name="remarks"></a>Remarques

Si une fonction doit générer une séquence supérieure à [max_size](#max_size) éléments, la fonction signale une erreur de longueur en levant un objet de type [length_error](../standard-library/length-error-class.md).

Les références, les pointeurs et les itérateurs qui désignent des éléments de la séquence contrôlée peuvent devenir non valides après tout appel à une fonction qui modifie la séquence contrôlée, ou après le premier appel à une **`const`** fonction non membre.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<string>

**Espace de noms :** std

## <a name="basic_stringallocator_type"></a><a name="allocator_type"></a> basic_string :: allocator_type

Type qui représente la classe allocator d’un objet string.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Remarques

Le type est un synonyme du paramètre de modèle `Allocator`.

### <a name="example"></a>Exemple

```cpp
// basic_string_allocator_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringappend"></a><a name="append"></a> basic_string :: Append

Ajoute des caractères à la fin d'une chaîne.

```cpp
basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& append(
    size_type count,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& append(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& append(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& append(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Chaîne C à ajouter.

*Str*\
Chaîne dont les caractères sont à ajouter.

*décalage*\
Index de la partie de la chaîne source fournissant les caractères à ajouter.

*saut*\
Nombre de caractères à ajouter, au maximum, à partir de la chaîne source.

*char_value*\
Valeur du caractère à ajouter.

*premier*\
Itérateur d’entrée qui cible le premier élément de la plage à ajouter.

*famille*\
Itérateur d’entrée, const_pointer ou const_iterator, qui cible la position juste après le dernier élément dans la plage à ajouter.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet string ajouté avec les caractères transmis par la fonction membre.

### <a name="remarks"></a>Remarques

Les caractères peuvent être ajoutés à une chaîne à l’aide de l' [opérateur + =](#op_add_eq) ou des fonctions membres `append` ou [push_back](#push_back). `operator+=` Ajoute des valeurs à argument unique tandis que la fonction membre à plusieurs arguments `append` permet de spécifier une partie spécifique d’une chaîne pour l’ajout de.

### <a name="example"></a>Exemple

```cpp
// basic_string_append.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a C-string to a string
   string str1a ( "Hello " );
   cout << "The original string str1 is: " << str1a << endl;
   const char *cstr1a = "Out There ";
   cout << "The C-string cstr1a is: " << cstr1a << endl;
   str1a.append ( cstr1a );
   cout << "Appending the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function
   // appending part of a C-string to a string
   string str1b ( "Hello " );
   cout << "The string str1b is: " << str1b << endl;
   const char *cstr1b = "Out There ";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.append ( cstr1b , 3 );
   cout << "Appending the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function
   // appending part of one string to another
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.append ( str2c , 5 , 5 );
   cout << "The appended string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World " );
   cout << "The  string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;

   // The fifth member function
   // appending characters to a string
   string str1e ( "Hello " );
   str1e.append ( 4 , '!' );
   cout << "The string str1 appended with exclamations is: "
        << str1e << endl << endl;

   // The sixth member function
   // appending a range of one string to another
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.append ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The appended string str1 is: "
        << str1f << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The C-string cstr1a is: Out There
Appending the C-string cstr1a to string str1 gives: Hello Out There .

The string str1b is: Hello
The C-string cstr1b is: Out There
Appending the 1st part of the C-string cstr1b to string str1 gives: Hello Out.

The string str2c is: Wide World
The appended string str1 is: Hello World.

The  string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World .

The string str1 appended with exclamations is: Hello !!!!

The string str2f is: Wide World
The appended string str1 is: Hello World.
```

## <a name="basic_stringassign"></a><a name="assign"></a> basic_string :: assign

Assigne de nouvelles valeurs de caractère au contenu d'une chaîne.

```cpp
basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type off,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& assign(
    size_type count,
    value_type char_value);

template <class InIt>
basic_string<CharType, Traits, Allocator>& assign(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& assign(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& assign(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Pointeur vers les caractères de la chaîne C à assigner à la chaîne cible.

*saut*\
Nombre de caractères à assigner, à partir de la chaîne source.

*Str*\
Chaîne source dont les caractères doivent être assignés à la chaîne cible.

*char_value*\
Valeur du caractère à assigner.

*premier*\
Itérateur d’entrée, const_pointer ou const_iterator, qui cible le premier caractère de la plage de la chaîne source à assigner à la plage cible.

*famille*\
Itérateur d’entrée, const_pointer ou const_iterator, qui cible la position juste après le dernier caractère de la plage de la chaîne source à assigner à la plage cible.

*préférable*\
Position à laquelle les nouveaux caractères commencent à être assignés.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet string auquel la fonction membre assigne les nouveaux caractères.

### <a name="remarks"></a>Remarques

Les chaînes peuvent recevoir de nouvelles valeurs de caractère. La nouvelle valeur peut être une chaîne et une chaîne C, ou un caractère unique. L' [opérateur =](#op_eq) peut être utilisé si la nouvelle valeur peut être décrite par un seul paramètre ; dans le cas contraire, la fonction membre `assign` , qui a plusieurs paramètres, peut être utilisée pour spécifier la partie de la chaîne qui doit être assignée à une chaîne cible.

### <a name="example"></a>Exemple

```cpp
// basic_string_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning the
   // characters of a C-string to a string
   string str1a;
   const char *cstr1a = "Out There";
   cout << "The C-string cstr1a is: " << cstr1a <<  "." << endl;
   str1a.assign ( cstr1a );
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function assigning a specific
   // number of the of characters a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.assign ( cstr1b , 3 );
   cout << "Assigning the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function assigning a specific number
   // of the characters from one string to another string
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.assign ( str2c , 5 , 5 );
   cout << "The newly assigned string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1d ( "Hello" ), str2d ( "Wide" ), str3d ( "World" );
   cout << "The original string str1 is: " << str1d << "." << endl;
   cout << "The string str2d is: " << str2d << endl;
   str1d.assign ( str2d );
   cout << "The string str1 newly assigned with string str2d is: "
        << str1d << "." << endl;
   cout << "The string str3d is: " << str3d << "." << endl;
   str1d = str3d;
   cout << "The string str1 reassigned with string str3d is: "
        << str1d << "." << endl << endl;

   // The fifth member function assigning a specific
   // number of characters of a certain value to a string
   string str1e ( "Hello " );
   str1e.assign ( 4 , '!' );
   cout << "The string str1 assigned with eclamations is: "
        << str1e << endl << endl;

   // The sixth member function assigning the value from
   // the range of one string to another string
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.assign ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The string str1 assigned a range of string str2f is: "
        << str1f << "." << endl << endl;
}
```

```Output
The C-string cstr1a is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The C-string cstr1b is: Out There
Assigning the 1st part of the C-string cstr1b to string str1 gives: Out.

The string str2c is: Wide World
The newly assigned string str1 is: World.

The original string str1 is: Hello.
The string str2d is: Wide
The string str1 newly assigned with string str2d is: Wide.
The string str3d is: World.
The string str1 reassigned with string str3d is: World.

The string str1 assigned with eclamations is: !!!!

The string str2f is: Wide World
The string str1 assigned a range of string str2f is: World.
```

## <a name="basic_stringat"></a><a name="at"></a> basic_string :: à

Fournit une référence au caractère situé à l'index spécifié dans une chaîne.

```cpp
const_reference at(size_type offset) const;

reference at(size_type offset);
```

### <a name="parameters"></a>Paramètres

*décalage*\
Index de la position de l’élément à référencer.

### <a name="return-value"></a>Valeur de retour

Référence au caractère de la chaîne à la position spécifiée par l’index de paramètre.

### <a name="remarks"></a>Remarques

Le premier élément de la chaîne a un index égal à zéro et les éléments suivants sont indexés consécutivement par les entiers positifs, de sorte qu’une chaîne de longueur *n* a un *n*ième élément indexé par le nombre *n-* 1.

L' [opérateur membre&#91;&#93;](#op_at) est plus rapide que la fonction membre `at` pour fournir un accès en lecture et en écriture aux éléments d’une chaîne.

Le membre `operator[]` ne vérifie pas si l’index passé comme paramètre est valide, mais la fonction membre `at` ne doit pas être utilisée si la validité n’est pas certaine. Un index non valide, qui est un index inférieur à zéro ou supérieur ou égal à la taille de la chaîne, passé à la fonction membre `at` lève une exception de [classe out_of_range](../standard-library/out-of-range-class.md) . Un index non valide passé à `operator[]` entraîne un comportement indéfini, mais l’index égal à la longueur de la chaîne est un index valide pour les chaînes const, et l’opérateur retourne le caractère null quand il reçoit cet index.

La référence retournée peut être invalidée par des réallocations de chaînes ou des modifications pour les chaînes non- **`const`** .

### <a name="example"></a>Exemple

```cpp
// basic_string_at.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string  cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringback"></a><a name="back"></a> basic_string :: Back

Retourne une référence au dernier élément de la chaîne.

```cpp
const_reference back() const;

reference back();
```

### <a name="return-value"></a>Valeur de retour

Référence au dernier élément de la chaîne, qui doit être non vide.

### <a name="remarks"></a>Remarques

## <a name="basic_stringbasic_string"></a><a name="basic_string"></a> basic_string :: basic_string

Construit une chaîne vide, initialisée par des caractères spécifiques ou qui représente une copie complète ou partielle d'un autre objet String ou d'une autre chaîne de style C (non terminée par la valeur null).

```cpp
basic_string();

explicit basic_string(
    const allocator_type& alloc_type);

basic_string(
    const basic_string& right);

basic_string(
    basic_string&& right);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count = npos);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr,
    size_type count);

basic_string(
    const value_type* ptr,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr);

basic_string(
    const value_type* ptr,
    const allocator_type& alloc_type);

basic_string(
    size_type count,
    value_type char_value);

basic_string(
    size_type count,
    value_type char_value,
    const allocator_type& alloc_type);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last,
    const allocator_type& alloc_type);

basic_string(
    const_pointer first,
    const_pointer last);

basic_string(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Chaîne C dont les caractères doivent être utilisés pour initialiser le `string` en cours de construction. Cette valeur ne peut pas être un pointeur null.

*alloc_type*\
Classe d'allocateur de stockage pour l'objet String en cours de construction.

*saut*\
Nombre de caractères à initialiser.

*Oui*\
Chaîne pour initialiser la chaîne en cours de construction.

*right_offset*\
Index d'un caractère dans une chaîne qui est le premier à être utilisé pour initialiser les valeurs de caractère de la chaîne en cours de construction.

*char_value*\
Valeur de caractère à copier dans la chaîne en cours de construction.

*premier*\
Itérateur d'entrée, const_pointer ou const_iterator qui traite le premier élément dans la plage source à insérer.

*famille*\
Itérateur d'entrée, const_pointer ou const_iterator qui traite la position de l'objet au-delà du dernier élément dans la plage source à insérer.

### <a name="return-value"></a>Valeur de retour

Référence à l'objet String qui est construit par les constructeurs.

### <a name="remarks"></a>Remarques

Tous les constructeurs stockent un [basic_string::allocator_type](#allocator_type) et initialisent la séquence contrôlée. L'objet allocateur est l'argument `al`, s'il est présent. Pour le constructeur de copie, il s’agit de `right.` [basic_string :: get_allocator](#get_allocator) `()` . Sinon, l’allocateur est `Alloc()` .

La séquence contrôlée est initialisée avec une copie de la séquence d'opérandes spécifiée par les opérandes restants. Un constructeur sans séquence d’opérandes spécifie une séquence contrôlée initiale vide. Si `InputIterator` est un type entier dans un constructeur de modèle, la séquence d’opérande `first,  last` se comporte de la même façon que `(size_type) first, (value_type) last` .

### <a name="example"></a>Exemple

```cpp
// basic_string_ctor.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function initializing with a C-string
   const char *cstr1a = "Hello Out There.";
   basic_string <char> str1a ( cstr1a , 5);
   cout << "The string initialized by C-string cstr1a is: "
        << str1a << "." << endl;

   // The second member function initializing with a string
   string  str2a ( "How Do You Do" );
   basic_string <char> str2b ( str2a , 7 , 7 );
   cout << "The string initialized by part of the string cstr2a is: "
        << str2b << "." << endl;

   // The third member function initializing a string
   // with a number of characters of a specific value
   basic_string <char> str3a ( 5, '9' );
   cout << "The string initialized by five number 9s is: "
        << str3a << endl;

   // The fourth member function creates an empty string
   // and string with a specified allocator
   basic_string <char> str4a;
   string str4b;
   basic_string <char> str4c ( str4b.get_allocator( ) );
   if (str4c.empty ( ) )
      cout << "The string str4c is empty." << endl;
   else
      cout << "The string str4c is not empty." << endl;

   // The fifth member function initializes a string from
   // another range of characters
   string str5a ( "Hello World" );
   basic_string <char> str5b ( str5a.begin ( ) + 5 , str5a.end ( ) );
   cout << "The string initialized by another range is: "
        << str5b << "." << endl;
}
```

## <a name="basic_stringbegin"></a><a name="begin"></a> basic_string :: Begin

Retourne un itérateur qui traite le premier élément de la chaîne.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur d’accès aléatoire qui cible le premier élément de la séquence ou la position juste après la fin d’une séquence vide.

### <a name="example"></a>Exemple

```cpp
// basic_string_begin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator strp_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.begin ( );
   cout << "The first character of the string str1 is: "
        << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'G';
   cout << "The first character of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The full modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'g';

   // For an empty string, begin is equivalent to end
   if (  str2.begin ( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The string str2 is not empty." << endl;
}
```

## <a name="basic_stringc_str"></a><a name="c_str"></a> basic_string :: c_str

Convertit le contenu d’une chaîne en chaîne de style C se terminant par un caractère null.

```cpp
const value_type *c_str() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la version de style C de la chaîne d’appel.  La valeur du pointeur n’est pas valide après l’appel d’une fonction non const, y compris le destructeur, dans la classe basic_string de l’objet.

### <a name="remarks"></a>Remarques

Les objets de type chaîne appartenant au modèle de classe basic_string ne \<char> sont pas nécessairement terminés par null. Le caractère null « \0 » est utilisé comme caractère spécial dans une chaîne C pour marquer la fin de la chaîne, mais il n’a aucune signification particulière dans un objet de type chaîne et peut faire partie de la chaîne comme tout autre caractère. Il existe une conversion automatique de **const char** <strong>\*</strong> en chaînes, mais la classe String ne fournit pas de conversion automatique des chaînes de style C en objets de type **basic_string \<char> **.

La chaîne de style C retournée ne doit pas être modifiée, car cela peut invalider le pointeur vers la chaîne, ou supprimé, car la chaîne a une durée de vie limitée et appartient à la chaîne de la classe.

### <a name="example"></a>Exemple

```cpp
// basic_string_c_str.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringcapacity"></a><a name="capacity"></a> basic_string :: Capacity

Retourne le plus grand nombre d'éléments qui peuvent être stockés dans une chaîne sans augmenter l'allocation de mémoire de la chaîne.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Valeur de retour

Taille du stockage actuellement alloué dans la mémoire pour contenir la chaîne.

### <a name="remarks"></a>Remarques

La fonction membre retourne le stockage actuellement alloué pour contenir la séquence contrôlée, une valeur au moins aussi grande que [size](#size).

### <a name="example"></a>Exemple

```cpp
// basic_string_capacity.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringcbegin"></a><a name="cbegin"></a> basic_string :: cbegin

Retourne un **`const`** itérateur qui traite le premier élément de la plage.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

**`const`** Itérateur à accès aléatoire qui pointe vers le premier élément de la plage, ou vers l’emplacement situé juste après la fin d’une plage vide (pour une plage vide, `cbegin() == cend()` ).

### <a name="remarks"></a>Remarques

Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `begin()` et `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="basic_stringcend"></a><a name="cend"></a> basic_string :: CEND

Retourne un **`const`** itérateur qui traite l’emplacement juste après le dernier élément d’une plage.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

**`const`** Itérateur à accès aléatoire qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Remarques

`cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `end()` et `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="basic_stringclear"></a><a name="clear"></a> basic_string :: Clear

Efface tous les éléments d'une chaîne.

```cpp
void clear();
```

### <a name="remarks"></a>Remarques

La chaîne sur laquelle la fonction membre est appelée est vide.

### <a name="example"></a>Exemple

```cpp
// basic_string_clear.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world"), str2;
   basic_string <char>::iterator str_Iter;
   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   str1.clear ( );
   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   //For an empty string, begin is equivalent to end
   if ( str1.begin ( ) == str1.end ( ) )
      cout << "Nothing printed above because "
           << "the string str1 is empty." << endl;
   else
      cout << "The string str1 is not empty." << endl;
}
```

```Output
The original string str1 is: Hello world
The modified string str1 is:
Nothing printed above because the string str1 is empty.
```

## <a name="basic_stringcompare"></a><a name="compare"></a> basic_string :: compare

Effectue une comparaison sensible à la casse entre une chaîne et une chaîne spécifiée pour déterminer si les deux chaînes sont équivalentes ou si l’une est inférieure à l’autre d’un point de vue lexicographique.

```cpp
int compare(
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count) const;

int compare(
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr
    size_type number_2) const;
```

### <a name="parameters"></a>Paramètres

*Str*\
Chaîne à comparer à la chaîne d’opérande.

*position_1*\
Index de la chaîne d’opérande à partir duquel commence la comparaison.

*number_1*\
Nombre maximal de caractères de la chaîne d’opérande à comparer.

*number_2*\
Nombre maximal de caractères de la chaîne de paramètre à comparer.

*décalage*\
Index de la chaîne de paramètre à partir duquel commence la comparaison.

*saut*\
Nombre maximal de caractères de la chaîne de paramètre à comparer.

*effectués*\
Chaîne C à comparer à la chaîne d’opérande.

### <a name="return-value"></a>Valeur de retour

Valeur négative si la chaîne d’opérande est inférieure à la chaîne de paramètre ; zéro si les deux chaînes sont égales ; ou valeur positive si la chaîne d’opérande est supérieure à la chaîne de paramètre.

### <a name="remarks"></a>Remarques

Les `compare` fonctions membres comparent la totalité ou une partie du paramètre et des chaînes d’opérande en fonction de ce qui est utilisé.

La comparaison effectuée respecte la casse.

### <a name="example"></a>Exemple

```cpp
// basic_string_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function compares
   // an operand string to a parameter string
   int comp1;
   string s1o ( "CAB" );
   string s1p ( "CAB" );
   cout << "The operand string is: " << s1o << endl;
   cout << "The parameter string is: " << s1p << endl;
   comp1 = s1o.compare ( s1p );
   if ( comp1 < 0 )
      cout << "The operand string is less than "
           << "the parameter string." << endl;
   else if ( comp1 == 0 )
      cout << "The operand string is equal to "
           << "the parameter string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The second member function compares part of
   // an operand string to a parameter string
   int comp2a, comp2b;
   string s2o ( "AACAB" );
   string s2p ( "CAB" );
   cout << "The operand string is: " << s2o << endl;
   cout << "The parameter string is: " << s2p << endl;
   comp2a = s2o.compare (  2 , 3 , s2p );
   if ( comp2a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;

   comp2b = s2o.compare (  0 , 3 , s2p );
   if ( comp2b < 0 )
      cout << "The first three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2b == 0 )
      cout << "The first three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The first three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The third member function compares part of
   // an operand string to part of a parameter string
   int comp3a;
   string s3o ( "AACAB" );
   string s3p ( "DCABD" );
   cout << "The operand string is: " << s3o << endl;
   cout << "The parameter string is: " << s3p << endl;
   comp3a = s3o.compare (  2 , 3 , s3p , 1 , 3 );
   if ( comp3a < 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are less than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else if ( comp3a == 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are equal to\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else
      cout << "The three characters from position 2 of "
           << "the operand string is greater than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   cout << endl;

   // The fourth member function compares
   // an operand string to a parameter C-string
   int comp4a;
   string s4o ( "ABC" );
   const char* cs4p = "DEF";
   cout << "The operand string is: " << s4o << endl;
   cout << "The parameter C-string is: " << cs4p << endl;
   comp4a = s4o.compare ( cs4p );
   if ( comp4a < 0 )
      cout << "The operand string is less than "
           << "the parameter C-string." << endl;
   else if ( comp4a == 0 )
      cout << "The operand string is equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The fifth member function compares part of
   // an operand string to a parameter C-string
   int comp5a;
   string s5o ( "AACAB" );
   const char* cs5p = "CAB";
   cout << "The operand string is: " << s5o << endl;
   cout << "The parameter string is: " << cs5p << endl;
   comp5a = s5o.compare (  2 , 3 , s2p );
   if ( comp5a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter C-string." << endl;
   else if ( comp5a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The sixth member function compares part of
   // an operand string to part of an equal length of
   // a parameter C-string
   int comp6a;
   string s6o ( "AACAB" );
   const char* cs6p = "ACAB";
   cout << "The operand string is: " << s6o << endl;
   cout << "The parameter C-string is: " << cs6p << endl;
   comp6a = s6o.compare (  1 , 3 , cs6p , 3 );
   if ( comp6a < 0 )
      cout << "The 3 characters from position 1 of "
           << "the operand string are less than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   else if ( comp6a == 0 )
      cout << "The 3 characters from position 2 of "
           << "the operand string are equal to\n "
           << "the first 3 characters of the parameter C-string."
           <<  endl;
   else
      cout << "The 3 characters from position 2 of "
           << "the operand string is greater than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   cout << endl;
}
```

```Output
The operand string is: CAB
The parameter string is: CAB
The operand string is equal to the parameter string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter string.
The first three characters of the operand string
are less than the parameter string.

The operand string is: AACAB
The parameter string is: DCABD
The three characters from position 2 of the operand string are equal to
the 3 characters parameter string from position 1.

The operand string is: ABC
The parameter C-string is: DEF
The operand string is less than the parameter C-string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter C-string.

The operand string is: AACAB
The parameter C-string is: ACAB
The 3 characters from position 2 of the operand string are equal to
the first 3 characters of the parameter C-string.
```

## <a name="basic_stringconst_iterator"></a><a name="const_iterator"></a> basic_string :: const_iterator

Type qui fournit un itérateur à accès aléatoire qui peut accéder à un **`const`** élément dans la chaîne et le lire.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Remarques

Un type `const_iterator` ne peut pas être utilisé pour modifier la valeur d’un caractère et est utilisé pour itérer sur une chaîne vers l’avant.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `const_iterator`, consultez l’exemple relatif à [begin](#begin).

## <a name="basic_stringconst_pointer"></a><a name="const_pointer"></a> basic_string :: const_pointer

Type qui fournit un pointeur vers un **`const`** élément d’une chaîne.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarques

Le type est un synonyme de `allocator_type::const_pointer`.

Pour `string` le type, son équivalent à **`char*`** .

Les pointeurs déclarés comme const doivent être initialisés au moment de la déclaration. Les pointeurs const pointent toujours vers le même emplacement de mémoire et peuvent pointer vers des données constantes ou non-constantes.

### <a name="example"></a>Exemple

```cpp
// basic_string_const_ptr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::const_pointer pstr1a = "In Here";
   const char *cstr1c = "Out There";

   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1c is: " << cstr1c << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1c is: Out There.
```

## <a name="basic_stringconst_reference"></a><a name="const_reference"></a> basic_string :: const_reference

Type qui fournit une référence à un **`const`** élément stocké dans une chaîne pour la lecture et l’exécution d' **`const`** opérations.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="remarks"></a>Remarques

Un type `const_reference` ne peut pas être utilisé pour changer la valeur d'un élément.

Le type est un synonyme de `allocator_type::const_reference`. Pour String `type` , il est équivalent à const `char&` .

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `const_reference`, consultez l’exemple relatif à [at](#at).

## <a name="basic_stringconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> basic_string :: const_reverse_iterator

Type qui fournit un itérateur à accès aléatoire capable de lire un **`const`** élément de la chaîne.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Remarques

Un type `const_reverse_iterator` ne peut pas changer la valeur d’un caractère. Il sert à itérer sur une chaîne dans l’ordre inverse.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `const_reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="basic_stringcopy"></a><a name="copy"></a> basic_string :: copier

Copie tout au plus un nombre spécifique de caractères d'une position indexée dans une chaîne source vers un tableau de caractères cible.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes. Utilisez [basic_string::_Copy_s](#copy_s) à la place.

```cpp
size_type copy(
    value_type* ptr,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*effectués*\
Tableau de caractères cible dans lequel les éléments doivent être copiés.

*nombre* Nombre de caractères à copier, au maximum, à partir de la chaîne source.

*décalage*\
Position de début dans la chaîne source à partir de laquelle les copies doivent être effectuées.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés.

### <a name="remarks"></a>Remarques

Un caractère NULL n’est pas ajouté à la fin de la copie.

### <a name="example"></a>Exemple

```cpp
// basic_string_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello World" );
   basic_string <char>::iterator str_Iter;
   char array1 [ 20 ] = { 0 };
   char array2 [ 10 ] = { 0 };
   basic_string <char>:: pointer array1Ptr = array1;
   basic_string <char>:: value_type *array2Ptr = array2;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   basic_string <char>:: size_type nArray1;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray1 = str1.copy ( array1Ptr , 12 );  // C4996
   cout << "The number of copied characters in array1 is: "
        << nArray1 << endl;
   cout << "The copied characters array1 is: " << array1 << endl;

   basic_string <char>:: size_type nArray2;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray2 = str1.copy ( array2Ptr , 5 , 6  );  // C4996
   cout << "The number of copied characters in array2 is: "
           << nArray2 << endl;
   cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringcrbegin"></a><a name="crbegin"></a> basic_string :: crbegin

Retourne un itérateur const qui traite le premier élément d'une chaîne inversée.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur inverse qui pointe juste après la fin de la chaîne. La position désigne le début de la chaîne inverse.

## <a name="basic_stringcrend"></a><a name="crend"></a> basic_string :: crend

Retourne un itérateur const qui traite l'emplacement qui suit le dernier élément d'une chaîne inversée.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur inversé const qui traite l'emplacement qui suit le dernier élément d'une chaîne inversée (emplacement qui précédait celui du premier élément de la chaîne non inversée).

### <a name="remarks"></a>Remarques

## <a name="basic_string_copy_s"></a><a name="copy_s"></a> basic_string :: _Copy_s

Copie tout au plus un nombre spécifique de caractères d'une position indexée dans une chaîne source vers un tableau de caractères cible.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*dest*\
Tableau de caractères cible dans lequel les éléments doivent être copiés.

*dest_size*\
La taille de *dest*.

*nombre* Nombre de caractères à copier, au maximum, à partir de la chaîne source.

*décalage*\
Position de début dans la chaîne source à partir de laquelle les copies doivent être effectuées.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères réellement copiés.

### <a name="remarks"></a>Remarques

Un caractère NULL n’est pas ajouté à la fin de la copie.

### <a name="example"></a>Exemple

```cpp
// basic_string__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;
    string str1("Hello World");
    basic_string<char>::iterator str_Iter;
    const int array1_size = 20;
    char array1[array1_size] = { 0 };
    const int array2_size = 10;
    char array2[array2_size] = { 0 };
    basic_string<char>:: pointer array1Ptr = array1;
    basic_string<char>:: value_type *array2Ptr = array2;

    cout << "The original string str1 is: ";
    for (str_Iter = str1.begin(); str_Iter != str1.end(); str_Iter++)
        cout << *str_Iter;
    cout << endl;

    basic_string<char>::size_type nArray1;
    nArray1 = str1._Copy_s(array1Ptr, array1_size, 12);
    cout << "The number of copied characters in array1 is: "
         << nArray1 << endl;
    cout << "The copied characters array1 is: " << array1 << endl;

    basic_string<char>:: size_type nArray2;
    nArray2 = str1._Copy_s(array2Ptr, array2_size, 5, 6);
    cout << "The number of copied characters in array2 is: "
         << nArray2 << endl;
    cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringdata"></a><a name="data"></a> basic_string ::d ATA

Convertit le contenu d’une chaîne en tableau de caractères se terminant par le caractère null.

```cpp
const value_type *data() const noexcept;
value_type *data() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le premier élément du tableau terminé par le caractère null qui contient le contenu de la chaîne. Pour une chaîne vide, le pointeur pointe vers un caractère null unique égal à `value_type()` .

### <a name="remarks"></a>Remarques

Pointeur retourné par `data` points dans une plage valide `[data(), data() + size()]` . Chaque élément de la plage correspond aux données actuelles de la chaîne. Autrement dit, pour chaque décalage valide *n* dans la plage, `data() + n == addressof(operator[](n))` .

Si vous modifiez le contenu de la chaîne retournée par la **`const`** surcharge de `data` , le comportement n’est pas défini. Vous bénéficiez également d’un comportement indéfini si le caractère null du terminal est remplacé par une autre valeur. Le pointeur retourné peut être invalidé si une référence non const à la chaîne est passée à une fonction de bibliothèque standard. Elle peut également être invalidée par un appel à une fonction membre non const. Les appels aux membres,,,,,, `at` `back` `begin` `end` `front` `rbegin` `rend` et `operator[]` n’invalident pas le pointeur.

Avant C++ 11, `data` n’a pas garanti que la chaîne retournée était terminée par un caractère null. Depuis C++ 11, `data` et `c_str` retournent toutes deux une chaîne terminée par le caractère null, et sont effectivement identiques.

La surcharge non const est une nouveauté dans C++ 17. Pour l’utiliser, spécifiez l’option de compilateur **/std : c++ 17** ou **/std : c + + latest** .

### <a name="example"></a>Exemple

```cpp
// basic_string_data.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringdifference_type"></a><a name="difference_type"></a> basic_string ::d ifference_type

Type qui fournit la différence entre deux itérateurs qui font référence aux éléments d'une même chaîne.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Remarques

Le type d'entier signé décrit un objet qui peut représenter la différence entre les adresses de deux éléments quelconques dans la séquence contrôlée.

Pour `string` le type, son équivalent à `ptrdiff_t` .

### <a name="example"></a>Exemple

```cpp
// basic_string_diff_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "quintillion" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexChFi, indexChLi;

   indexChFi = str1.find_first_of ( "i" );
   indexChLi = str1.find_last_of ( "i" );
   basic_string<char>::difference_type diffi = indexChLi - indexChFi;

   cout << "The first character i is at position: "
        << indexChFi << "." << endl;
   cout << "The last character i is at position: "
        << indexChLi << "." << endl;
   cout << "The difference is: " << diffi << "." << endl;
}
```

```Output
The original string str1 is: quintillion
The first character i is at position: 2.
The last character i is at position: 8.
The difference is: 6.
```

## <a name="basic_stringempty"></a><a name="empty"></a> basic_string :: Empty

Vérifie si la chaîne contient ou non des caractères.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si l’objet String ne contient pas de caractères ; **`false`** si elle comporte au moins un caractère.

### <a name="remarks"></a>Remarques

La fonction membre est équivalente à [size](#size) == 0.

### <a name="example"></a>Exemple

```cpp
// basic_string_empty.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   bool b1, b2;

   string str1 ("Hello world");
   cout << "The original string object str1 is: " << str1 << endl;
   b1 = str1.empty();
   if (b1)
      cout << "The string object str1 is empty." << endl;
   else
      cout << "The string object str1 is not empty." << endl;
   cout << endl;

   // An example of an empty string object
   string str2;
   b2 = str2.empty();
   if (b2)
      cout << "The string object str2 is empty." << endl;
   else
      cout << "The string object str2 is not empty." << endl;
}
```

## <a name="basic_stringend"></a><a name="end"></a> basic_string :: fin

Retourne un itérateur qui traite l'emplacement qui suit le dernier élément d'une chaîne.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valeur de retour

Retourne un itérateur d’accès aléatoire qui cible l’emplacement situé après le dernier élément d’une chaîne.

### <a name="remarks"></a>Remarques

`end` est souvent utilisé pour tester si un itérateur a atteint la fin de sa chaîne. La valeur retournée par `end` ne doit pas être déréférencée.

Si la valeur de retour de `end` est assignée à un `const_iterator`, l’objet de chaîne ne peut pas être modifié. Si la valeur de retour de `end` est assignée à `iterator` , l’objet String peut être modifié.

### <a name="example"></a>Exemple

```cpp
// basic_string_end.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator str_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.end ( );
   str1_Iter--;
   str1_Iter--;
   cout << "The last character-letter of the string str1 is: " << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // end used to test when an iterator has reached the end of its string
   cout << "The string is now: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
   *str1_Iter = 'T';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.begin( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the string str1 is: t
The full original string str1 is: No way out.
The string is now: No way out.
The last character-letter of the modified str1 is now: T
The modified string str1 is now: No way ouT.
The string str2 is empty.
```

## <a name="basic_stringends_with"></a><a name="ends_with"></a> basic_string :: ends_with

Vérifiez si la chaîne se termine par le suffixe spécifié.

```cpp
bool ends_with(const CharType c) const noexcept;
bool ends_with(const CharType* const x) const noexcept;
bool ends_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>Paramètres

*secteur*\
Suffixe à un seul caractère à rechercher.

*Ed*\
Vue de chaîne contenant le suffixe à rechercher. \
Vous pouvez passer un `std::basic_string` , qui convertit en vue de chaîne.

*x*\
Chaîne de caractères se terminant par un caractère null qui contient le suffixe à rechercher.

### <a name="return-value"></a>Valeur de retour

`true` Si la chaîne se termine par le suffixe spécifié ; `false` sinon,.

### <a name="remarks"></a>Remarques

`ends_with()` est nouveau dans C++ 20. Pour l’utiliser, spécifiez l’option de compilateur [/std : c + + latest](../build/reference/std-specify-language-standard-version.md) .

Consultez [starts_with](#starts_with) pour vérifier si une chaîne commence par le préfixe spécifié.

### <a name="example"></a>Exemple

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::basic_string<char> str = "abcdefg";

    std::cout << std::boolalpha; // so booleans show as 'true'/'false'
    std::cout << str.ends_with('g') << '\n';
    std::cout << str.ends_with("eFg") << '\n';

    std::basic_string<char> str2 = "efg";
    std::cout << str.ends_with(str2);

    return 0;
}
```

```Output
true
false
true
```

## <a name="basic_stringerase"></a><a name="erase"></a> basic_string :: Erase

Supprime un élément ou une plage d'éléments dans une chaîne à partir de l'emplacement spécifié.

```cpp
iterator erase(
    iterator first,
    iterator last);

iterator erase(
    iterator iter);

basic_string<CharType, Traits, Allocator>& erase(
    size_type offset = 0,
    size_type count = npos);
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur qui cible la position du premier élément de la plage à effacer.

*famille*\
Itérateur qui cible la position juste après le dernier élément de la plage à effacer.

*ITER*\
Itérateur qui cible la position de l’élément de la chaîne à effacer.

*décalage*\
Index du premier caractère de la chaîne à supprimer.

*saut*\
Nombre d’éléments qui seront supprimés s’il y en a autant dans la plage de la chaîne commençant par *offset*.

### <a name="return-value"></a>Valeur de retour

Pour les deux premières fonctions membres, un itérateur qui cible le premier caractère après le dernier caractère supprimé par la fonction membre. Pour la troisième fonction membre, une référence à l’objet de chaîne à partir duquel les éléments ont été effacés.

### <a name="remarks"></a>Remarques

La troisième fonction membre retourne ** \* This**.

### <a name="example"></a>Exemple

```cpp
// basic_string_erase.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The 1st member function using a range demarcated
   // by iterators
   string str1 ( "Hello world" );
   basic_string <char>::iterator str1_Iter;
   cout << "The original string object str1 is: "
        << str1 << "." << endl;
   str1_Iter = str1.erase ( str1.begin ( ) + 3 , str1.end ( ) - 1 );
   cout << "The first element after those removed is: "
        << *str1_Iter << "." << endl;
   cout << "The modified string object str1 is: " << str1
           << "." << endl << endl;

   // The 2nd member function erasing a char pointed to
   // by an iterator
   string str2 ( "Hello World" );
   basic_string <char>::iterator str2_Iter;
   cout << "The original string object str2 is: " << str2
        << "." << endl;
   str2_Iter = str2.erase ( str2.begin ( ) + 5 );
   cout << "The first element after those removed is: "
        << *str2_Iter << "." << endl;
   cout << "The modified string object str2 is: " << str2
        << "." << endl << endl;

   // The 3rd member function erasing a number of chars
   // after a char
   string str3 ( "Hello computer" ), str3m;
   basic_string <char>::iterator str3_Iter;
   cout << "The original string object str3 is: "
        << str3 << "." << endl;
   str3m = str3.erase ( 6 , 8 );
   cout << "The modified string object str3m is: "
        << str3m << "." << endl;
}
```

```Output
The original string object str1 is: Hello world.
The first element after those removed is: d.
The modified string object str1 is: Held.

The original string object str2 is: Hello World.
The first element after those removed is: W.
The modified string object str2 is: HelloWorld.

The original string object str3 is: Hello computer.
The modified string object str3m is: Hello .
```

## <a name="basic_stringfind"></a><a name="find"></a> basic_string :: find

Recherche une chaîne vers l'avant pour trouver la première occurrence d'une sous-chaîne qui correspond à une séquence spécifique de caractères.

```cpp
size_type find(
    value_type char_value,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*char_value*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index de la position à laquelle la recherche doit commencer.

*effectués*\
C-string que la fonction membre doit rechercher.

*saut*\
Nombre de caractères, en comptant à partir du premier caractère, dans le C-string que la fonction membre doit rechercher.

*Str*\
Chaîne que la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

### <a name="example"></a>Exemple

```cpp
// basic_string_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;

   indexCh1a = str1.find ( "e" , 3 );
   if (indexCh1a != string::npos )
      cout << "The index of the 1st 'e' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.find ( "x" );
   if (indexCh1b != string::npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.find ( cstr2 , 5 );
   if ( indexCh2a != string::npos )
      cout << "The index of the 1st element of 'perfect' "
           << "after\n the 5th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.find ( cstr2b , 0 );
   if (indexCh2b != string::npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "after\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "This is a sample string for this program" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "sample";
   indexCh3a = str3.find ( cstr3a );
   if ( indexCh3a != string::npos )
      cout << "The index of the 1st element of sample "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'perfect' was not found in str3 ."
           << endl;

   const char *cstr3b = "for";
   indexCh3b = str3.find ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != string::npos )
      cout << "The index of the next occurrence of 'for' is in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'for' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "clearly this perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.find ( str4a , 5 );
   if ( indexCh4a != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "after\n the 5th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl;

   string str4b ( "clear" );
   indexCh4b = str4.find ( str4b );
   if (indexCh4b != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found after the 3rd position in str1 is: 8
The Character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' after
the 5th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: This is a sample string for this program
The index of the 1st element of sample in str3 is: 10
The index of the next occurrence of 'for' is in str3 begins at: 24

The original string str4 is: clearly this perfectly unclear.
The index of the 1st element of 'clear' after
the 5th position in str4 is: 25
The index of the 1st element of 'clear' in str4 is: 0
```

## <a name="basic_stringfind_first_not_of"></a><a name="find_first_not_of"></a> basic_string :: find_first_not_of

Recherche dans une chaîne le premier caractère qui n’est pas un élément d’une chaîne spécifiée.

```cpp
size_type find_first_not_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*char_value*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index de la position à laquelle la recherche doit commencer.

*effectués*\
C-string que la fonction membre doit rechercher.

*saut*\
Nombre de caractères, en comptant à partir du premier caractère, dans le C-string que la fonction membre doit rechercher.

*Str*\
Chaîne que la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

### <a name="example"></a>Exemple

```cpp
// basic_string_find_first_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "xddd-1234-abcd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_not_of ( "d" , 2 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_not_of  ( "x" );
   if (indexCh1b != npos )
      cout << "The index of the 'non x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_not_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not"
           << "\n found in str2 after the 6th position."
           << endl;

   const char *cstr2b = "B2";
   indexCh2b = str2.find_first_not_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'B2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'B2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_first_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_first_not_of ( cstr3b , indexCh3a + 1 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '45G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_not_of ( str4a , 5 );
   if (indexCh4a != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'ba3' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_first_not_of ( str4b  );
   if (indexCh4b != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of '12' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12' were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: xddd-1234-abcd
The index of the 1st 'd' found after the 3rd position in str1 is: 4
The index of the 'non x' found in str1 is: 1

The original string str2 is: BBB-1111
Elements of the substring 'B1' were not
found in str2 after the 6th position.
The index of the 1st element of 'B2' after
the 0th position in str2 is: 3

The original string str3 is: 444-555-GGG
The index of the 1st occurrence of an element in str3
other than one of the characters in '45G' is: 3
The index of the second occurrence of an element of '45G' in str3
after the 0th position is: 7

The original string str4 is: 12-ab-12-ab
The index of the 1st non occurrence of an element of 'ba3' in str4 after
the 5th position is: 5
The index of the 1st non occurrence of an element of '12' in str4 after
the 0th position is: 2
```

## <a name="basic_stringfind_first_of"></a><a name="find_first_of"></a> basic_string :: find_first_of

Recherche dans une chaîne le premier caractère qui correspond à un élément de la chaîne spécifiée.

```cpp
size_type find_first_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Paramètres

*char_value*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index de la position à laquelle la recherche doit commencer.

*effectués*\
C-string que la fonction membre doit rechercher.

*saut*\
Nombre de caractères, en comptant à partir du premier caractère, dans le C-string que la fonction membre doit rechercher.

*Str*\
Chaîne que la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

### <a name="example"></a>Exemple

```cpp
// basic_string_find_first_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_of ( "d" , 5 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 5th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for any element of a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 after the 10th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_first_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for any element of a substring as specified by a C-string
   string str3 ( "123-abc-123-abc-456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "5G";
   indexCh3a = str3.find_first_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of '5G' in str3 after\n the 0th "
           << "position is: " << indexCh3a << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the 0th position."
           << endl;

   const char *cstr3b = "5GF";
   indexCh3b = str3.find_first_of  ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '5G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the first occurrrence."
           << endl << endl;

   // The fourth member function searches a string
   // for any element of a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_of ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_first_of ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'a2' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the 1st 'd' found after the 5th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the 1st occurrence of an element of 'B1' in str2 after
the 6th position is: 11
The index of the 1st element of 'D2' after
the 0th position in str2 is: 3

The original string str3 is: 123-abc-123-abc-456-EFG-456-EFG
The index of the 1st occurrence of an element of '5G' in str3 after
the 0th position is: 17
The index of the second occurrence of an element of '5G' in str3
after the 0th position is: 22

The original string str4 is: 12-ab-12-ab
The index of the 1st occurrence of an element of 'ba3' in str4 after
the 5th position is: 9
The index of the 1st occurrence of an element of 'a2' in str4 after
the 0th position is: 1
```

## <a name="basic_stringfind_last_not_of"></a><a name="find_last_not_of"></a> basic_string :: find_last_not_of

Recherche dans une chaîne le dernier caractère qui n’est pas un élément d’une chaîne spécifiée.

```cpp
size_type find_last_not_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*char_value*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index de la position à laquelle la recherche doit se terminer.

*effectués*\
C-string que la fonction membre doit rechercher.

*saut*\
Nombre de caractères, en comptant à partir du premier caractère, dans le C-string que la fonction membre doit rechercher.

*Str*\
Chaîne que la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index du premier caractère de la sous-chaîne recherchée en cas de succès ; dans le cas contraire, `npos`.

### <a name="example"></a>Exemple

```cpp
// basic_string_find_last_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "dddd-1dd4-abdd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_not_of ( "d" , 7 );
   if ( indexCh1a != npos )
      cout << "The index of the last non 'd'\n found before the "
           << "7th position in str1 is: " << indexCh1a << endl;
   else
      cout << "The non 'd' character was not found ." << endl;

   indexCh1b = str1.find_last_not_of  ( "d" );
   if ( indexCh1b != npos )
      cout << "The index of the non 'd' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_not_of  ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the last occurrence of a "
           << "element\n not of 'B1' in str2 before the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements not of the substring 'B1' were not "
           << "\n found in str2 before the 6th position."
           << endl;

   const char *cstr2b = "B-1";
   indexCh2b = str2.find_last_not_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element not "
           << "in 'B-1'\n is: "
           << indexCh2b << endl << endl;
   else
      cout << "The elements of the substring 'B-1' were "
           << "not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_last_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_last_not_of ( cstr3b , 6 , indexCh3a - 1 );
   if (indexCh3b != npos )
      cout << "The index of the penultimate occurrence of an "
           << "element\n not in '45G' in str3 is: "
           << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "b-a" );
   indexCh4a = str4.find_last_not_of  ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element not\n in 'b-a' in str4 before the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'b-a' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_last_not_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element not in '12'\n in str4 before the end "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12'\n were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: dddd-1dd4-abdd
The index of the last non 'd'
found before the 7th position in str1 is: 5
The index of the non 'd' found in str1 is: 11

The original string str2 is: BBB-1111
The index of the last occurrence of a element
not of 'B1' in str2 before the 6th position is: 3
The elements of the substring 'B-1' were not found in str2 .

The original string str3 is: 444-555-GGG
The index of the last occurrence of an element in str3
other than one of the characters in '45G' is: 7
The index of the penultimate occurrence of an element
not in '45G' in str3 is: 3

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element not
in 'b-a' in str4 before the 5th position is: 1
The index of the last occurrence of an element not in '12'
in str4 before the end position is: 10
```

## <a name="basic_stringfind_last_of"></a><a name="find_last_of"></a> basic_string :: find_last_of

Recherche dans une chaîne le dernier caractère qui correspond à un élément de la chaîne spécifiée.

```cpp
size_type find_last_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*char_value*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index de la position à laquelle la recherche doit se terminer.

*effectués*\
C-string que la fonction membre doit rechercher.

*saut*\
Nombre de caractères, en comptant à partir du premier caractère, dans le C-string que la fonction membre doit rechercher.

*Str*\
Chaîne que la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index du dernier caractère de la sous-chaîne recherchée en cas de réussite ; sinon, `npos`.

### <a name="example"></a>Exemple

```cpp
// basic_string_find_last_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_of ( "d" , 14 );
   if ( indexCh1a != npos )
      cout << "The index of the last 'd' found before the 14th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_of  ( cstr2 , 12 );
   if (indexCh2a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'B1' in str2 before\n the 12th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 before the 12th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_last_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a;

   const char *cstr3a = "5E";
   indexCh3a = str3.find_last_of ( cstr3a , 8 , 8 );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element of '5E' in str3 before\n the 8th "
           << "position is: " << indexCh3a << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n before the 8th position."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_last_of  ( str4a , 8 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'ba3' in str4 before\n the 8th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_last_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'a2' in str4 before\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the last 'd' found before the 14th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the last occurrence of an element of 'B1' in str2 before
the 12th position is: 11
The index of the last element of 'D2' after
the 0th position in str2 is: 16

The original string str3 is: 456-EFG-456-EFG
The index of the last occurrence of an element of '5E' in str3 before
the 8th position is: 4

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element of 'ba3' in str4 before
the 8th position is: 4
The index of the last occurrence of an element of 'a2' in str4 before
the 0th position is: 9
```

## <a name="basic_stringfront"></a><a name="front"></a> basic_string :: front

Retourne une référence au premier élément d'une chaîne.

```cpp
const_reference front() const;

reference front();
```

### <a name="return-value"></a>Valeur de retour

Référence au premier élément de la chaîne, qui doit être non vide.

### <a name="remarks"></a>Remarques

## <a name="basic_stringget_allocator"></a><a name="get_allocator"></a> basic_string :: get_allocator

Retourne une copie de l’objet allocateur utilisé pour construire la chaîne.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Allocateur utilisé par la chaîne.

### <a name="remarks"></a>Remarques

La fonction membre retourne l’objet d’allocateur stocké.

Les allocateurs de la classe string spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur sont suffisants pour la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.

### <a name="example"></a>Exemple

```cpp
// basic_string_get_allocator.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char> s2;
   basic_string <char, char_traits< char >, allocator< char > > s3;

   // s4 will use the same allocator class as s1
   basic_string <char> s4( s1.get_allocator ( ) );

   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringinsert"></a><a name="insert"></a> basic_string :: Insert

Insère un élément, un certain nombre d'éléments ou une plage d'éléments dans la chaîne à la position spécifiée.

```cpp
basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    size_type count,
    value_type char_value);

iterator insert(
    iterator iter);

iterator insert(
    iterator iter,
    value_type char_value)l
template <class InputIterator>
void insert(
    iterator iter,
    InputIterator first,
    InputIterator last);

void insert(
    iterator iter,
    size_type count,
    value_type char_value);

void insert(
    iterator iter,
    const_pointer first,
    const_pointer last);

void insert(
    iterator iter,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Paramètres

*endroit*\
Index de la position derrière le point d’insertion des nouveaux caractères.

*effectués*\
C-string à insérer en intégralité ou en partie dans la chaîne.

*saut*\
Nombre de caractères à insérer.

*Str*\
Chaîne à insérer en intégralité ou en partie dans la chaîne cible.

*décalage*\
Index de la partie de la chaîne source fournissant les caractères à ajouter.

*char_value*\
Valeur de caractère des éléments à insérer.

*ITER*\
Itérateur traitant la position derrière laquelle un caractère doit être inséré.

*premier*\
Itérateur d'entrée, const_pointer ou const_iterator qui traite le premier élément dans la plage source à insérer.

*famille*\
Itérateur d'entrée, const_pointer ou const_iterator qui traite la position de l'objet au-delà du dernier élément dans la plage source à insérer.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet string auquel la fonction membre affecte de nouveaux caractères ou, dans le cas d’insertions de caractères individuels, itérateur traitant la position du caractère inséré, ou aucune valeur, selon la fonction membre en question.

### <a name="example"></a>Exemple

```cpp
// basic_string_insert.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function inserting a C-string
   // at a given position
   basic_string <char> str1a ( "way" );
   const char *cstr1a = "a";
   str1a.insert ( 0, cstr1a );
   cout << "The string with a C-string inserted at position 0 is: "
        << str1a << "." << endl;

   // The second member function inserting a C-string
   // at a given position for a specified number of elements
   basic_string <char> str2a ( "Good" );
   const char *cstr2a = "Bye Bye Baby";
   str2a.insert ( 4, cstr2a ,3 );
   cout << "The string with a C-string inserted at the end is: "
        << str2a << "." << endl;

   // The third member function inserting a string
   // at a given position
   basic_string <char> str3a ( "Bye" );
   string str3b ( "Good" );
   str3a.insert ( 0, str3b );
   cout << "The string with a string inserted at position 0 is: "
        << str3a << "." << endl;

   // The fourth member function inserting part of
   // a string at a given position
   basic_string <char> str4a ( "Good " );
   string str4b ( "Bye Bye Baby" );
   str4a.insert ( 5, str4b , 8 , 4 );
   cout << "The string with part of a string inserted at position 4 is: "
        << str4a << "." << endl;

   // The fifth member function inserts a number of characters
   // at a specified position in the string
   string str5 ( "The number is: ." );
   str5.insert ( 15 , 3 , '3' );
   cout << "The string with characters inserted is: "
        << str5 << endl;

   // The sixth member function inserts a character
   // at a specified position in the string
   string str6 ( "ABCDFG" );
   basic_string <char>::iterator str6_Iter = ( str6.begin ( ) + 4 );
   str6.insert ( str6_Iter , 'e' );
   cout << "The string with a character inserted is: "
        << str6 << endl;

   // The seventh member function inserts a range
   // at a specified position in the string
   string str7a ( "ABCDHIJ" );
   string str7b ( "abcdefgh" );
   basic_string <char>::iterator str7a_Iter = (str7a.begin ( ) + 4 );
   str7a.insert ( str7a_Iter , str7b.begin ( ) + 4 , str7b.end ( ) -1 );
   cout << "The string with a character inserted from a range is: "
        << str7a << endl;

   // The eighth member function inserts a number of
   // characters at a specified position in the string
   string str8 ( "ABCDHIJ" );
   basic_string <char>::iterator str8_Iter = ( str8.begin ( ) + 4 );
   str8.insert ( str8_Iter , 3 , 'e' );
   cout << "The string with a character inserted from a range is: "
        << str8 << endl;
}
```

```Output
The string with a C-string inserted at position 0 is: away.
The string with a C-string inserted at the end is: GoodBye.
The string with a string inserted at position 0 is: GoodBye.
The string with part of a string inserted at position 4 is: Good Baby.
The string with characters inserted is: The number is: 333.
The string with a character inserted is: ABCDeFG
The string with a character inserted from a range is: ABCDefgHIJ
The string with a character inserted from a range is: ABCDeeeHIJ
```

## <a name="basic_stringiterator"></a><a name="iterator"></a> basic_string :: Iterator

Type qui fournit un itérateur à accès aléatoire qui peut accéder à un **`const`** élément dans la chaîne et le lire.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Remarques

Un type `iterator` peut être utilisé pour modifier la valeur d’un caractère et est utilisé pour itérer au sein d’une chaîne vers l’avant.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `iterator`, consultez l’exemple relatif à [begin](#begin).

## <a name="basic_stringlength"></a><a name="length"></a> basic_string :: length

Retourne le nombre actuel d'éléments contenus dans une chaîne.

```cpp
size_type length() const;
```

### <a name="remarks"></a>Remarques

La fonction membre est identique à [size](#size).

### <a name="example"></a>Exemple

```cpp
// basic_string_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringmax_size"></a><a name="max_size"></a> basic_string :: max_size

Retourne le nombre maximal de caractères qu'une chaîne peut contenir.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre maximal de caractères qu’une chaîne peut contenir.

### <a name="remarks"></a>Remarques

Une exception de type [classe length_error](../standard-library/length-error-class.md) est levée quand une opération produit une chaîne d’une longueur supérieure à la taille maximale.

### <a name="example"></a>Exemple

```cpp
// basic_string_max_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringnpos"></a><a name="npos"></a> basic_string :: NPOs

Valeur intégrale non signée initialisée à-1 qui indique « introuvable » ou « tous les caractères restants » quand une fonction de recherche échoue.

```cpp
static const size_type npos = -1;
```

### <a name="remarks"></a>Remarques

Lorsque la valeur de retour doit être vérifiée pour la `npos` valeur, elle peut ne pas fonctionner, sauf si la valeur de retour est de type [size_type](#size_type) et non **`int`** ou **`unsigned`** .

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [find](#find) pour savoir comment déclarer et utiliser `npos`.

## <a name="basic_stringoperator"></a><a name="op_add_eq"></a> basic_string :: Operator + =

Ajoute des caractères à une chaîne.

```cpp
basic_string<CharType, Traits, Allocator>& operator+=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator+=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator+=(
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*char_value*\
Caractère à ajouter.

*effectués*\
Caractères de la chaîne C à ajouter.

*Oui*\
Caractères de la chaîne à ajouter.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet string ajouté avec les caractères transmis par la fonction membre.

### <a name="remarks"></a>Remarques

Les caractères peuvent être ajoutés à une chaîne à l’aide de `operator+=`, ou des fonctions membres [append](#append) ou [push_back](#push_back). `operator+=` ajoute des valeurs à argument unique tandis que la fonction membre append à plusieurs arguments permet de spécifier une partie spécifique d’une chaîne à ajouter.

### <a name="example"></a>Exemple

```cpp
// basic_string_op_app.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a single character to a string
   string str1a ( "Hello" );
   cout << "The original string str1 is: " << str1a << endl;
   str1a +=  '!' ;
   cout << "The string str1 appended with an exclamation is: "
        << str1a << endl << endl;

   // The second member function
   // appending a C-string to a string
   string  str1b ( "Hello " );
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b +=  cstr1b;
   cout << "Appending the C-string cstr1b to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World" );
   cout << "The string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The string str1 appended with an exclamation is: Hello!

The C-string cstr1b is: Out There
Appending the C-string cstr1b to string str1 gives: Hello Out There.

The string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World.
```

## <a name="basic_stringoperator"></a><a name="op_eq"></a> basic_string :: Operator =

Assigne de nouvelles valeurs de caractère au contenu d'une chaîne.

```cpp
basic_string<CharType, Traits, Allocator>& operator=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>& right);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>Paramètres

*char_value*\
Valeur du caractère à assigner.

*effectués*\
Pointeur vers les caractères de la chaîne C à assigner à la chaîne cible.

*Oui*\
Chaîne source dont les caractères doivent être assignés à la chaîne cible.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet string auquel la fonction membre assigne les nouveaux caractères.

### <a name="remarks"></a>Remarques

Les chaînes peuvent recevoir de nouvelles valeurs de caractère. La nouvelle valeur peut être une chaîne et une chaîne C, ou un caractère unique. `operator=` peut être utilisé si la nouvelle valeur peut être décrite par un seul paramètre ; sinon la fonction membre [assign](#assign), qui possède plusieurs paramètres, peut être utilisée pour spécifier la partie de la chaîne qui doit être assignée à une chaîne cible.

### <a name="example"></a>Exemple

```cpp
// basic_string_op_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning a
   // character of a certain value to a string
   string str1a ( "Hello " );
   str1a = '0';
   cout << "The string str1 assigned with the zero character is: "
        << str1a << endl << endl;

   // The second member function assigning the
   // characters of a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b <<  "." << endl;
   str1b = cstr1b;
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1c ( "Hello" ), str2c ( "Wide" ), str3c ( "World" );
   cout << "The original string str1 is: " << str1c << "." << endl;
   cout << "The string str2c is: " << str2c << "." << endl;
   str1c.assign ( str2c );
   cout << "The string str1 newly assigned with string str2c is: "
        << str1c << "." << endl;
   cout << "The string str3c is: " << str3c << "." << endl;
   str1c = str3c;
   cout << "The string str1 reassigned with string str3c is: "
        << str1c << "." << endl << endl;
}
```

```Output
The string str1 assigned with the zero character is: 0

The C-string cstr1b is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The original string str1 is: Hello.
The string str2c is: Wide.
The string str1 newly assigned with string str2c is: Wide.
The string str3c is: World.
The string str1 reassigned with string str3c is: World.
```

## <a name="basic_stringoperator"></a><a name="op_at"></a> basic_string :: Operator []

Fournit une référence au caractère situé à l'index spécifié dans une chaîne.

```cpp
const_reference operator[](size_type offset) const;
reference operator[](size_type offset);
```

### <a name="parameters"></a>Paramètres

*décalage*\
Index de la position de l’élément à référencer.

### <a name="return-value"></a>Valeur de retour

Référence au caractère de la chaîne à la position spécifiée par l’index de paramètre.

### <a name="remarks"></a>Remarques

Le premier élément de la chaîne a un index égal à zéro et les éléments suivants sont indexés consécutivement par les entiers positifs, de sorte qu’une chaîne de longueur *n* a son *n*-ième élément indexé par le nombre *n* - 1.

`operator[]` est plus rapide que la fonction membre [at](#at) pour fournir un accès en lecture et en écriture aux éléments d’une chaîne.

`operator[]` ne vérifie pas si l’index passé comme paramètre est valide, mais que la fonction membre `at` ne doit pas être utilisée dans la validité. Un index non valide (un index inférieur à zéro ou supérieur ou égal à la taille de la chaîne) passé à la fonction membre `at` lève une exception de [classe out_of_range](../standard-library/out-of-range-class.md) . Un index non valide passé à `operator[]` entraîne un comportement indéfini, mais l’index égal à la longueur de la chaîne est un index valide pour les chaînes const, et l’opérateur retourne le caractère null quand il reçoit cet index.

La référence retournée peut être invalidée par des réallocations de chaînes ou des modifications pour les chaînes non- **`const`** .

Lors de la compilation avec un [ \_ \_ \_ niveau de débogage d’itérateur](../standard-library/iterator-debug-level.md) défini sur 1 ou 2, une erreur d’exécution se produit si vous tentez d’accéder à un élément en dehors des limites de la chaîne. Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

```cpp
// basic_string_op_ref.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non-const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index of 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringpointer"></a><a name="pointer"></a> basic_string ::p ointer

Type qui fournit un pointeur vers un élément caractère d'une chaîne ou d'un tableau de caractères.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Remarques

Le type est un synonyme de `allocator_type::pointer`.

Pour `string` le type, son équivalent à **`char`** <strong>\*</strong> .

### <a name="example"></a>Exemple

```cpp
// basic_string_pointer.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::pointer pstr1a = "In Here";
   char *cstr1b = "Out There";
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1b is: " << cstr1b << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1b is: Out There.
```

## <a name="basic_stringpop_back"></a><a name="pop_back"></a> basic_string ::p op_back

Efface le dernier élément de la chaîne.

```cpp
void pop_back();
```

### <a name="remarks"></a>Remarques

Cette fonction membre appelle `erase(size() - 1)` pour effacer le dernier élément de la séquence, qui ne doit pas être vide.

## <a name="basic_stringpush_back"></a><a name="push_back"></a> basic_string ::p ush_back

Ajoute un élément à la fin de la chaîne.

```cpp
void push_back(value_type char_value);
```

### <a name="parameters"></a>Paramètres

*char_value*\
Caractère à ajouter à la fin de la chaîne.

### <a name="remarks"></a>Remarques

La fonction membre appelle effectivement [Insert](#insert)( [end](#end), *char_value* ).

### <a name="example"></a>Exemple

```cpp
// basic_string_push_back.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "abc" );
   basic_string <char>::iterator str_Iter, str1_Iter;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // str1.push_back ( 'd' );
   str1_Iter = str1.end ( );
   str1_Iter--;
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;

   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;
}
```

```Output
The original string str1 is: abc
The last character-letter of the modified str1 is now: c
The modified string str1 is: abc
```

## <a name="basic_stringrbegin"></a><a name="rbegin"></a> basic_string :: rbegin

Retourne un itérateur au premier élément d'une chaîne inversée.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valeur de retour

Retourne un itérateur d’accès aléatoire vers le premier élément d’une chaîne inversée, qui cible le dernier élément de la chaîne non inversée correspondante.

### <a name="remarks"></a>Remarques

`rbegin` est utilisé avec une chaîne inversée, de la même façon que [begin](#begin) est utilisé avec une chaîne.

Si la valeur de retour de `rbegin` est assignée à un `const_reverse_iterator`, l’objet de chaîne ne peut pas être modifié. Si la valeur de retour de `rbegin` est assignée à un `reverse_iterator`, l’objet de chaîne peut être modifié.

`rbegin` peut être utilisé pour initialiser une itération au sein d’une chaîne vers l’arrière.

### <a name="example"></a>Exemple

```cpp
// basic_string_rbegin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Able was I ere I saw Elba" ), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rbegin ( );
   // str1_rIter--;
   cout << "The first character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'A';
   cout << "The first character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'A';

   // For an empty string, begin is equivalent to end
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The first character-letter of the reversed string str1 is: a
The full reversed string str1 is:
ablE was I ere I saw elbA
The first character-letter of the modified str1 is now: A
The full modified reversed string str1 is now:
AblE was I ere I saw elbA
The string str2 is empty.
```

## <a name="basic_stringreference"></a><a name="reference"></a> basic_string :: référence

Type qui fournit une référence à un élément stocké dans une chaîne.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="remarks"></a>Remarques

Un type `reference` peut être utilisé pour modifier la valeur d’un élément.

Le type est un synonyme de `allocator_type::reference`.

Pour `string` le type, son équivalent à `chr&` .

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `reference`, consultez l’exemple relatif à [at](#at).

## <a name="basic_stringrend"></a><a name="rend"></a> basic_string :: rend

Retourne un itérateur qui cible l’emplacement suivant le dernier élément d’une chaîne inversée.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valeur de retour

Retourne un itérateur d’accès aléatoire qui cible l’emplacement suivant le dernier élément d’une chaîne inversée.

### <a name="remarks"></a>Remarques

`rend` est utilisé avec une chaîne inversée, de la même façon que [end](#end) est utilisé avec une chaîne.

Si la valeur de retour de `rend` est assignée à un `const_reverse_iterator`, l’objet de chaîne ne peut pas être modifié. Si la valeur de retour de `rend` est assignée à un `reverse_iterator`, l’objet de chaîne peut être modifié.

`rend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de sa chaîne.

La valeur retournée par `rend` ne doit pas être déréférencée.

### <a name="example"></a>Exemple

```cpp
// basic_string_rend.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Able was I ere I saw Elba"), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rend ( );
   str1_rIter--;
   cout << "The last character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'o';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the reversed string str1 is: A
The full reversed string str1 is:
ablE was I ere I saw elbA
The last character-letter of the modified str1 is now: o
The full modified reversed string str1 is now:
ablE was I ere I saw elbo
The string str2 is empty.
```

## <a name="basic_stringreplace"></a><a name="replace"></a> basic_string :: replace

Remplace les éléments d'une chaîne à la position spécifiée par des caractères spécifiques ou des caractères copiés à partir d'autres plages, chaînes ou chaînes de style C.

```cpp
basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type position_2,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    size_type count,
    value_type char_value);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    size_type number_2,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Paramètres

*Str*\
Chaîne qui doit être une source de caractères pour la chaîne d’opérande.

*position_1*\
Index de la chaîne d’opérande à partir duquel commence le remplacement.

*number_1*\
Nombre maximal de caractères à remplacer dans la chaîne d’opérande.

*position_2*\
Index de la chaîne de paramètre à partir duquel commence la copie.

*number_2*\
Nombre maximal de caractères à utiliser de la chaîne C de paramètre.

*effectués*\
Chaîne C qui doit être une source de caractères pour la chaîne d’opérande.

*char_value*\
Caractère à copier dans la chaîne d’opérande.

*first0*\
Itérateur qui cible le premier caractère à supprimer dans la chaîne d’opérande.

*last0*\
Itérateur qui cible le dernier caractère à supprimer dans la chaîne d’opérande.

*premier*\
Itérateur, const_pointer ou const_iterator qui cible le premier caractère à copier dans la chaîne de paramètre.

*famille*\
Itérateur, const_pointer ou const_iterator qui cible le dernier caractère à copier dans la chaîne de paramètre.

*saut*\
Nombre de fois où *char_value* est copié dans la chaîne d’opérande.

### <a name="return-value"></a>Valeur de retour

Chaîne d’opérande avec le remplacement effectué.

### <a name="example"></a>Exemple

```cpp
// basic_string_replace.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first two member functions replace
   // part of the operand string with
   // characters from a parameter string or C-string
   string result1a, result1b;
   string s1o ( "AAAAAAAA" );
   string s1p ( "BBB" );
   const char* cs1p = "CCC";
   cout << "The operand string s1o is: " << s1o << endl;
   cout << "The parameter string s1p is: " << s1p << endl;
   cout << "The parameter C-string cs1p is: " << cs1p << endl;
   result1a = s1o.replace ( 1 , 3 , s1p );
   cout << "The result of s1o.replace ( 1 , 3 , s1p )\n is "
        << "the string: " << result1a << "." << endl;
   result1b = s1o.replace ( 5 , 3 , cs1p );
   cout << "The result of s1o.replace ( 5 , 3 , cs1p )\n is "
        << "the string: " << result1b << "." << endl;
   cout << endl;

   // The third & fourth member function replace
   // part of the operand string with characters
   // form part of a parameter string or C-string
   string result2a, result2b;
   string s2o ( "AAAAAAAA" );
   string s2p ( "BBB" );
   const char* cs2p = "CCC";
   cout << "The operand string s2o is: " << s2o << endl;
   cout << "The parameter string s1p is: " << s2p << endl;
   cout << "The parameter C-string cs2p is: " << cs2p << endl;
   result2a = s2o.replace ( 1 , 3 , s2p , 1 , 2 );
   cout << "The result of s2o.replace (1, 3, s2p, 1, 2)\n is "
        << "the string: " << result2a << "." << endl;
   result2b = s2o.replace ( 4 , 3 , cs2p , 1 );
   cout << "The result of s2o.replace (4 ,3 ,cs2p)\n is "
        << "the string: " << result2b << "." << endl;
   cout << endl;

   // The fifth member function replaces
   // part of the operand string with characters
   string result3a;
   string s3o ( "AAAAAAAA" );
   char ch3p = 'C';
   cout << "The operand string s3o is: " << s3o << endl;
   cout << "The parameter character c1p is: " << ch3p << endl;
   result3a = s3o.replace ( 1 , 3 , 4 , ch3p );
   cout << "The result of s3o.replace(1, 3, 4, ch3p)\n is "
        << "the string: " << result3a << "." << endl;
   cout << endl;

   // The sixth & seventh member functions replace
   // part of the operand string, delineated with iterators,
   // with a parameter string or C-string
   string s4o ( "AAAAAAAA" );
   string s4p ( "BBB" );
   const char* cs4p = "CCC";
   cout << "The operand string s4o is: " << s4o << endl;
   cout << "The parameter string s4p is: " << s4p << endl;
   cout << "The parameter C-string cs4p is: " << cs4p << endl;
   basic_string<char>::iterator IterF0, IterL0;
   IterF0 = s4o.begin ( );
   IterL0 = s4o.begin ( ) + 3;
   string result4a, result4b;
   result4a = s4o.replace ( IterF0 , IterL0 , s4p );
   cout << "The result of s1o.replace (IterF0, IterL0, s4p)\n is "
        << "the string: " << result4a << "." << endl;
   result4b = s4o.replace ( IterF0 , IterL0 , cs4p );
   cout << "The result of s4o.replace (IterF0, IterL0, cs4p)\n is "
        << "the string: " << result4b << "." << endl;
   cout << endl;

   // The 8th member function replaces
   // part of the operand string delineated with iterators
   // with a number of characters from a parameter C-string
   string s5o ( "AAAAAAAF" );
   const char* cs5p = "CCCBB";
   cout << "The operand string s5o is: " << s5o << endl;
   cout << "The parameter C-string cs5p is: " << cs5p << endl;
   basic_string<char>::iterator IterF1, IterL1;
   IterF1 = s5o.begin ( );
   IterL1 = s5o.begin ( ) + 4;
   string result5a;
   result5a = s5o.replace ( IterF1 , IterL1 , cs5p , 4 );
   cout << "The result of s5o.replace (IterF1, IterL1, cs4p ,4)\n is "
        << "the string: " << result5a << "." << endl;
   cout << endl;

   // The 9th member function replaces
   // part of the operand string delineated with iterators
   // with specified characters
   string s6o ( "AAAAAAAG" );
   char ch6p = 'q';
   cout << "The operand string s6o is: " << s6o << endl;
   cout << "The parameter character ch6p is: " << ch6p << endl;
   basic_string<char>::iterator IterF2, IterL2;
   IterF2 = s6o.begin ( );
   IterL2 = s6o.begin ( ) + 3;
   string result6a;
   result6a = s6o.replace ( IterF2 , IterL2 , 4 , ch6p );
   cout << "The result of s6o.replace (IterF1, IterL1, 4, ch6p)\n is "
        << "the string: " << result6a << "." << endl;
   cout << endl;

   // The 10th member function replaces
   // part of the operand string delineated with iterators
   // with part of a parameter string delineated with iterators
   string s7o ( "OOOOOOO" );
   string s7p ( "PPPP" );
   cout << "The operand string s7o is: " << s7o << endl;
   cout << "The parameter string s7p is: " << s7p << endl;
   basic_string<char>::iterator IterF3, IterL3, IterF4, IterL4;
   IterF3 = s7o.begin ( ) + 1;
   IterL3 = s7o.begin ( ) + 3;
   IterF4 = s7p.begin ( );
   IterL4 = s7p.begin ( ) + 2;
   string result7a;
   result7a = s7o.replace ( IterF3 , IterL3 , IterF4 , IterL4 );
   cout << "The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)\n is "
        << "the string: " << result7a << "." << endl;
   cout << endl;
}
```

```Output
The operand string s1o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs1p is: CCC
The result of s1o.replace ( 1 , 3 , s1p )
is the string: ABBBAAAA.
The result of s1o.replace ( 5 , 3 , cs1p )
is the string: ABBBACCC.

The operand string s2o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs2p is: CCC
The result of s2o.replace (1, 3, s2p, 1, 2)
is the string: ABBAAAA.
The result of s2o.replace (4 ,3 ,cs2p)
is the string: ABBAC.

The operand string s3o is: AAAAAAAA
The parameter character c1p is: C
The result of s3o.replace(1, 3, 4, ch3p)
is the string: ACCCCAAAA.

The operand string s4o is: AAAAAAAA
The parameter string s4p is: BBB
The parameter C-string cs4p is: CCC
The result of s1o.replace (IterF0, IterL0, s4p)
is the string: BBBAAAAA.
The result of s4o.replace (IterF0, IterL0, cs4p)
is the string: CCCAAAAA.

The operand string s5o is: AAAAAAAF
The parameter C-string cs5p is: CCCBB
The result of s5o.replace (IterF1, IterL1, cs4p ,4)
is the string: CCCBAAAF.

The operand string s6o is: AAAAAAAG
The parameter character ch6p is: q
The result of s6o.replace (IterF1, IterL1, 4, ch6p)
is the string: qqqqAAAAG.

The operand string s7o is: OOOOOOO
The parameter string s7p is: PPPP
The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)
is the string: OPPOOOO.
```

## <a name="basic_stringreserve"></a><a name="reserve"></a> basic_string :: Reserve

Définit la capacité de la chaîne en fonction d'un nombre au moins aussi grand que le nombre spécifié.

```cpp
void reserve(size_type count = 0);
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre de caractères pour lequel la mémoire est réservée.

### <a name="remarks"></a>Remarques

Il est important d’avoir une capacité suffisante, car les réallocations sont chronophages et invalident toutes les références, pointeurs et itérateurs qui référencent les caractères d’une chaîne.

Le concept de capacité pour les objets de type chaîne est le même que pour les objets de type vecteur. Contrairement au vecteur, la fonction membre `reserve` peut être appelée pour réduire la capacité d’un objet. La demande est non liante, et peut ou ne peut pas se produire. Comme la valeur par défaut du paramètre est zéro, un appel de `reserve` est une demande non liée à la réduction de la capacité de la chaîne pour qu’elle corresponde au nombre de caractères actuellement dans la chaîne. La capacité n’est jamais inférieure au nombre actuel de caractères.

L’appel à `reserve` est la seule façon possible de réduire la capacité d’une chaîne. Toutefois, comme indiqué ci-dessus, cette demande est non liante et peut ne pas se produire.

### <a name="example"></a>Exemple

```cpp
// basic_string_reserve.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1, sizerStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1, caprStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with added capacity
   str1.reserve ( 40 );
   sizerStr1 = str1.size ( );
   caprStr1 = str1.capacity ( );

   cout << "The string str1with augmented capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizerStr1 << "." << endl;
   cout << "The new capacity of string str1 is: "
        << caprStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with downsized capacity
   str1.reserve ( );
   basic_string <char>::size_type sizedStr1;
   basic_string <char>::size_type capdStr1;
   sizedStr1 = str1.size ( );
   capdStr1 = str1.capacity ( );

   cout << "The string str1 with downsized capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizedStr1 << "." << endl;
   cout << "The reduced capacity of string str1 is: "
        << capdStr1 << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The string str1with augmented capacity is: Hello world
The current size of string str1 is: 11.
The new capacity of string str1 is: 47.

The string str1 with downsized capacity is: Hello world
The current size of string str1 is: 11.
The reduced capacity of string str1 is: 47.
```

## <a name="basic_stringresize"></a><a name="resize"></a> basic_string :: Resize

Spécifie une nouvelle taille pour une chaîne, en ajoutant ou en effaçant des éléments selon les besoins.

```cpp
void resize(
    size_type count,);

void resize(
    size_type count,
    value_type char_value);
```

### <a name="parameters"></a>Paramètres

*saut*\
Nouvelle taille de la chaîne.

*char_value*\
Valeur avec laquelle les caractères ajoutés sont initialisés si des éléments supplémentaires sont nécessaires.

### <a name="remarks"></a>Remarques

Si la taille obtenue dépasse le nombre maximal de caractères, le formulaire lève `length_error`.

### <a name="example"></a>Exemple

```cpp
// basic_string_resize.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ( "Hello world" );
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 2 elements: exclamations
   str1.resize ( str1.size ( ) + 2 , '!' );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   cout << "The current size of resized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of resized string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 20 elements:
   str1.resize ( str1.size ( ) + 20 );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   // note capacity increases automatically as required
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to downsize by 28 elements:
   str1.resize ( str1.size ( ) - 28 );
   cout << "The downsized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   // Compare size & capacity of a string after downsizing
   cout << "The current size of downsized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of downsized string str1 is: "
        << capStr1 << "." << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of resized string str1 is: 13.
The capacity of resized string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of modified string str1 is: 33.
The capacity of modified string str1 is: 47.

The downsized string str1 is: Hello
The current size of downsized string str1 is: 5.
The capacity of downsized string str1 is: 47.
```

## <a name="basic_stringreverse_iterator"></a><a name="reverse_iterator"></a> basic_string :: reverse_iterator

Type qui fournit une référence à un élément stocké dans une chaîne.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Remarques

Un type `reverse_iterator` peut servir à changer la valeur d’un caractère. Il sert à itérer au sein d’une chaîne dans l’ordre inverse.

### <a name="example"></a>Exemple

Pour savoir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).

## <a name="basic_stringrfind"></a><a name="rfind"></a> basic_string :: RFind

Recherche une chaîne vers l'arrière pour trouver la première occurrence d'une sous-chaîne qui correspond à une séquence spécifique de caractères.

```cpp
size_type rfind(
    value_type char_value,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type rfind(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Paramètres

*char_value*\
Valeur de caractère que la fonction membre doit rechercher.

*décalage*\
Index de la position à laquelle la recherche doit commencer.

*effectués*\
C-string que la fonction membre doit rechercher.

*saut*\
Nombre de caractères, en comptant à partir du premier caractère, dans le C-string que la fonction membre doit rechercher.

*Str*\
Chaîne que la fonction membre doit rechercher.

### <a name="return-value"></a>Valeur de retour

Index de la dernière occurrence, dans une recherche inversée, du premier caractère de la sous-chaîne en cas de réussite ; sinon, `npos`.

### <a name="example"></a>Exemple

```cpp
// basic_string_rfind.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.rfind ( "e" , 9 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'e' found before the 9th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.rfind ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.rfind ( cstr2 , 30 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st element of 'perfect' "
           << "before\n the 30th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.rfind ( cstr2b , 30 );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "before\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "It is a nice day. I am happy." );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "nice";
   indexCh3a = str3.rfind ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st element of 'nice' "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'nice' was not found in str3 ."
           << endl;

   const char *cstr3b = "am";
   indexCh3b = str3.rfind ( cstr3b , indexCh3a + 25 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the next occurrence of 'am' in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'am' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "This perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.rfind ( str4a , 15 );
   if (indexCh4a != npos )
      cout << "The index of the 1st element of 'clear' "
           << "before\n the 15th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 "
           << "before the 15th position." << endl;

   string str4b ( "clear" );
   indexCh4b = str4.rfind ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found before the 9th position in str1 is: 8
The character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' before
the 30th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: It is a nice day. I am happy.
The index of the 1st element of 'nice' in str3 is: 8
The index of the next occurrence of 'am' in str3 begins at: 20

The original string str4 is: This perfectly unclear.
The substring 'clear' was not found in str4 before the 15th position.
The index of the 1st element of 'clear' in str4 is: 17
```

## <a name="basic_stringshrink_to_fit"></a><a name="shrink_to_fit"></a> basic_string :: shrink_to_fit

Ignore la capacité excédentaire de la chaîne.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Remarques

Cette fonction membre élimine tout stockage inutile dans le conteneur.

## <a name="basic_stringsize"></a><a name="size"></a> basic_string :: Size

Retourne le nombre actuel d'éléments contenus dans une chaîne.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur de la chaîne.

### <a name="example"></a>Exemple

```cpp
// basic_string_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringsize_type"></a><a name="size_type"></a> basic_string :: size_type

Type entier non signé qui peut représenter le nombre d’éléments et d’index dans une chaîne.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="remarks"></a>Remarques

elle est équivalente à `allocator_type::size_type` .

Pour `string` le type, son équivalent à `size_t` .

### <a name="example"></a>Exemple

```cpp
// basic_string_size_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" );

   basic_string <char>::size_type sizeStr1, capStr1;
   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   cout << "The current size of string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of string str1 is: " << capStr1
         << "." << endl;
}
```

```Output
The current size of string str1 is: 11.
The capacity of string str1 is: 15.
```

## <a name="basic_stringstarts_with"></a><a name="starts_with"></a> basic_string :: starts_with

Vérifiez si la chaîne commence par le préfixe spécifié.

```cpp
bool starts_with(const CharType c) const noexcept;
bool starts_with(const CharType* const x) const noexcept;
bool starts_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>Paramètres

*secteur*\
Préfixe à caractère unique à rechercher.

*Ed*\
Vue de chaîne contenant le préfixe à rechercher. \
Vous pouvez passer un `std::basic_string` , qui convertit en vue de chaîne.

*x*\
Chaîne de caractères se terminant par un caractère null qui contient le préfixe à rechercher.

### <a name="return-value"></a>Valeur de retour

`true` Si la chaîne commence par le préfixe spécifié ; `false` sinon,.

### <a name="remarks"></a>Remarques

`starts_with()` est nouveau dans C++ 20. Pour l’utiliser, spécifiez l’option de compilateur [/std : c + + latest](../build/reference/std-specify-language-standard-version.md) .

Consultez [ends_with](#ends_with) pour voir si une chaîne se termine par le suffixe spécifié.

### <a name="example"></a>Exemple

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::basic_string<char> str = "abcdefg";

    std::cout << std::boolalpha; // so booleans show as 'true'/'false'     
    std::cout << str.starts_with('b') << '\n';
    std::cout << str.starts_with("aBc") << '\n';

    std::basic_string<char> str2 = "abc";
    std::cout << str.starts_with(str2);

    return 0;
}
```

```Output
false
false
true
```

## <a name="basic_stringsubstr"></a><a name="substr"></a> basic_string :: substr

Copie une sous-chaîne d'un certain nombre de caractères dans une chaîne qui commence à la position spécifiée.

```cpp
basic_string<CharType, Traits, Allocator> substr(
    size_type offset = 0,
    size_type count = npos) const;
```

### <a name="parameters"></a>Paramètres

*décalage*\
Index situant l’élément à la position à partir de laquelle la copie de la chaîne est effectuée, avec une valeur par défaut égale à 0.

*saut*\
Nombre de caractères qui doivent être copiés s’ils sont présents.

### <a name="return-value"></a>Valeur de retour

Objet de sous-chaîne qui est une copie des éléments de l’opérande de chaîne commençant à la position spécifiée par le premier argument.

### <a name="example"></a>Exemple

```cpp
// basic_string_substr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ("Heterological paradoxes are persistent.");
   cout << "The original string str1 is: \n " << str1
        << endl << endl;

   basic_string <char> str2 = str1.substr ( 6 , 7 );
   cout << "The substring str1 copied is: " << str2
        << endl << endl;

   basic_string <char> str3 = str1.substr (  );
   cout << "The default substring str3 is: \n " << str3
        <<  "\n which is the entire original string." << endl;
}
```

```Output
The original string str1 is:
Heterological paradoxes are persistent.

The substring str1 copied is: logical

The default substring str3 is:
Heterological paradoxes are persistent.
which is the entire original string.
```

## <a name="basic_stringswap"></a><a name="swap"></a> basic_string :: swap

Échange le contenu de deux chaînes.

```cpp
void swap(
    basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Chaîne source dont les éléments doivent être échangés avec ceux de la chaîne de destination.

### <a name="remarks"></a>Remarques

Si les chaînes échangées ont le même objet allocateur, la fonction membre `swap` :

- Se produit en temps constant.

- Ne lève aucune exception.

- N’invalide aucune référence, pointeur ou itérateur qui désigne des éléments dans les deux chaînes.

Sinon, elle effectue un nombre d’affectations d’éléments et d’appels de constructeurs proportionnel au nombre d’éléments dans les deux séquences contrôlées.

### <a name="example"></a>Exemple

```cpp
// basic_string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;

   s1.swap ( s2 );
   cout << "After swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.
After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="basic_stringtraits_type"></a><a name="traits_type"></a> basic_string :: traits_type

Type pour les caractéristiques de caractère des éléments stockés dans une chaîne.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Remarques

Le type est un synonyme du deuxième paramètre de modèle `Traits` .

Pour `string` le type, il est équivalent **à \<char> char_traits**.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [copy](../standard-library/char-traits-struct.md#copy) pour savoir comment déclarer et utiliser `traits_type`.

## <a name="basic_stringvalue_type"></a><a name="value_type"></a> basic_string :: value_type

Type qui représente le type des caractères stockés dans une chaîne.

```cpp
typedef typename allocator_type::value_type value_type;
```

### <a name="remarks"></a>Remarques

Elle est équivalente à `traits_type::char_type` et équivaut à **`char`** pour les objets de type `string` .

### <a name="example"></a>Exemple

```cpp
// basic_string_value_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   basic_string<char>::value_type ch1 = 'G';

   char ch2 = 'H';

   cout << "The character ch1 is: " << ch1 << "." << endl;
   cout << "The character ch2 is: " << ch2 << "." << endl;
}
```

```Output
The character ch1 is: G.
The character ch2 is: H.
```

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
