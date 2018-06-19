---
title: path, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::path
dev_langs:
- C++
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ea20d43e2679addc10465cfc549a64fc210274f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861686"
---
# <a name="path-class"></a>path, classe

La classe **path** stocke un objet de type string\_type, appelé ici myname à des fins de démonstration, qui peut être utilisé comme nom de chemin. string\_type est un synonyme de basic\_string\<value_type>, où value\_type est un synonyme de char sur Windows ou wchar_t sur Posix.

Pour obtenir plus d’informations et des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class path;
```

## <a name="pathappend"></a>path::append

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

Les fonctions membres ajoutent la séquence spécifiée à mypath convertie et en insérant un preferred_separator selon les besoins.

## <a name="pathassign"></a>path::assign

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

Les fonctions membres remplacent mypath par la séquence spécifiée, convertie selon les besoins.

## <a name="pathbegin"></a>path::begin

```cpp
iterator begin() const;
```

Retourne un path::iterator désignant le premier élément du chemin dans le nom du chemin, s’il est présent.

## <a name="pathcstr"></a>path::c_str

```cpp
const value_type& *c_str() const noexcept;
```

Retourne un pointeur vers le premier caractère de mypath.

## <a name="pathclear"></a>path::clear

```cpp
void clear() noexcept;
```

La fonction membre exécute mypath.clear()

## <a name="pathcompare"></a>path::compare

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

La première fonction retourne mypath.compare(pval.native()). La deuxième fonction retourne mypath.compare(str). La troisième fonction retourne mypath.compare(ptr).

## <a name="pathconcat"></a>path::concat

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

Les fonctions membres ajoutent la séquence spécifiée à mypath, convertie (pas en insérant un séparateur) selon les besoins.

## <a name="pathconstiterator"></a>path::const_iterator

```cpp
typedef iterator const_iterator;
```

Type est un synonyme de iterator.

## <a name="pathempty"></a>path::empty

```cpp
bool empty() const noexcept;
```

Retourne mypath.empty().

## <a name="pathend"></a>path::end

```cpp
iterator end() const;
```

Retourne un itérateur de fin de séquence de type iterator.

## <a name="pathextension"></a>path::extension

```cpp
path extension() const;
```

Retourne le suffixe de filename() X tel que :

Si X == path(".") &#124;&#124; X == path("..") ou si X ne contient pas de point, le suffixe est vide.

Dans le cas contraire, le suffixe commence par (et inclut) le point le plus à droite.

## <a name="pathfilename"></a>path::filename

```cpp
path filename() const;
```

Retourne le composant du répertoire racine de myname, spécifiquement `empty()  path() : *--end()`. Le composant peut être vide.

## <a name="pathgenericstring"></a>path::generic_string

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.

## <a name="pathgenericu16string"></a>path::generic_u16string

```cpp
u16string generic_u16string() const;
```

Retourne u16string() avec (sous Windows) les barres obliques inverses converties en barres obliques.

## <a name="pathgenericu32string"></a>path::generic_u32string

```cpp
u32string generic_u32string() const;
```

Retourne u32string() avec (sous Windows) les barres obliques inverses converties en barres obliques.

## <a name="pathgenericu8string"></a>path::generic_u8string

```cpp
string generic_u8string() const;
```

Retourne u8string() avec (sous Windows) les barres obliques inverses converties en barres obliques.

## <a name="pathgenericwstring"></a>path::generic_wstring

```cpp
wstring generic_wstring() const;
```

Retourne wstring() avec (sous Windows) les barres obliques inverses converties en barres obliques.

## <a name="pathhasextension"></a>path::has_extension

```cpp
bool has_extension() const;
```

Retourne !extension().empty().

## <a name="pathhasfilename"></a>path::has_filename

```cpp
bool has_filename() const;
```

Retourne !filename().empty().

## <a name="pathhasparentpath"></a>path::has_parent_path

```cpp
bool has_parent_path() const;
```

Retourne !parent_path().empty().

## <a name="pathhasrelativepath"></a>path::has_relative_path

```cpp
bool has_relative_path() const;
```

Retourne !relative_path().empty().

## <a name="pathhasrootdirectory"></a>path::has_root_directory

```cpp
bool has_root_directory() const;
```

Retourne !root_directory().empty().

## <a name="pathhasrootname"></a>path::has_root_name

```cpp
bool has_root_name() const;
```

Retourne !root_name().empty().

## <a name="pathhasrootpath"></a>path::has_root_path

```cpp
bool has_root_path() const;
```

Retourne !root_path().empty().

## <a name="pathhasstem"></a>path::has_stem

```cpp
bool has_stem() const;
```

Retourne !stem().empty().

## <a name="pathisabsolute"></a>path::is_absolute

```cpp
bool is_absolute() const;
```

Pour Windows, la fonction retourne has_root_name() && has_root_directory(). Pour Posix, la fonction retourne has_root_directory().

## <a name="pathisrelative"></a>path::is_relative

```cpp
bool is_relative() const;
```

Retourne !is_absolute().

## <a name="pathiterator"></a>path::iterator

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

Cette classe décrit un itérateur de constante bidirectionnel qui désigne les composants de chemin de myname dans la séquence :

1. le nom de la racine, s’il est présent

1. le répertoire racine, s’il est présent

1. les éléments du répertoire restants du chemin parent, s’il est présent, se terminant par le nom de fichier, s’il est présent

Pour pval, un objet de type path :

1. path::iterator X = pval.begin() désigne le premier élément du chemin dans le chemin, s’il est présent.

1. X == pval.end() a la valeur true quand X pointe juste après la fin de la séquence de composants.

3. *X retourne une chaîne qui correspond au composant actuel.

1. ++X désigne le composant suivant dans la séquence, s’il est présent.

1. --X désigne le composant précédent dans la séquence, s’il est présent.

1. La modification de myname invalide tous les itérateurs désignant des éléments dans myname.

## <a name="pathmakepreferred"></a>path::make_preferred

```cpp
path& make_preferred();
```

La fonction membre convertit chaque séparateur en un preferred_separator selon les besoins.

## <a name="pathnative"></a>path::native

```cpp
const string_type& native() const noexcept;
```

Retourne myname.

## <a name="pathoperator"></a>path::operator=

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

Le premier opérateur membre copie right.myname vers myname. Le deuxième opérateur membre copie right.myname vers myname. Le troisième opérateur membre se comporte comme *this = path(source).

## <a name="pathoperator"></a>path::operator+=

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. concat(right);

1. concat(path(str));

1. concat(ptr);

1. concat(string_type(1, elem));

1. concat(source);

1. concat(path(basic_string\<Elem>(1, elem)));

## <a name="pathoperator"></a>path::operator/=

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. append(right);

1. append(source);

## <a name="pathoperator-stringtype"></a>path::operator string_type

```cpp
operator string_type() const;
```

L’opérateur membre retourne myname.

## <a name="pathparentpath"></a>path::parent_path

```cpp
path parent_path() const;
```

Retourne le composant du chemin parent de myname, spécifiquement le préfixe de myname après suppression de filename().native() et des séparateurs de répertoire immédiatement précédents. (De même, si begin() ! = end(), il correspond à la combinaison de tous les éléments dans la plage [begin(), --end()) en appliquant successivement l’opérateur /=.) Le composant peut être vide.

## <a name="pathpath"></a>path::path

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

Tous les constructeurs construisent tous myname de différentes façons :

Pour path(), c’est myname().

Pour path(const path& right), c’est myname(right.myname).

Pour path(path&& right), c’est myname(right.myname).

Pour template\<class Source> path(const Source& source), c’est myname(source).

Pour template\<class Source> path(const Source& source, const locale& loc), c’est myname(source), en obtenant toutes les facettes codecvt nécessaires de loc.

Pour template\<class InIt> path(InIt first, InIt last), c’est myname(first, last).

Pour template\<class InIt> path(InIt first, InIt last, const locale& loc), c’est myname(first, last), en obtenant toutes les facettes codecvt nécessaires de loc.

## <a name="pathpreferredseparator"></a>path::preferred_separator

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

L’objet de constante donne le caractère préféré pour la séparation des composants du chemin, en fonction du système d’exploitation hôte. Notez qu’il est également possible dans la plupart des contextes sous Windows d’utiliser à la place L'/'.

## <a name="pathrelativepath"></a>path::relative_path

```cpp
path relative_path() const;
```

Retourne le composant du chemin relatif de myname, spécifiquement le suffixe de myname après suppression de root_path().native() et des séparateurs de répertoire redondants immédiatement suivants. Le composant peut être vide.

## <a name="pathremovefilename"></a>path::remove_filename

```cpp
path& remove_filename();
```

## <a name="pathreplaceextension"></a>path::replace_extension

```cpp
path& replace_extension(const path& newext = path());
```

La fonction membre supprime d’abord le suffixe extension().native() de myname. Ensuite, si !newext.empty() && newext[0] != dot (où dot est *path(".").c_str()), dot est ajouté à myname. Ensuite, newext est ajouté à myname.

## <a name="pathreplacefilename"></a>path::replace_filename

```cpp
path& replace_filename(const path& pval);
```

La fonction membre exécute :

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathrootdirectory"></a>path::root_directory

```cpp
path root_directory() const;
```

Retourne le composant du répertoire racine de myname. Le composant peut être vide.

## <a name="pathrootname"></a>path::root_name

```cpp
path root_name() const;
```

Retourne le composant du nom racine de myname. Le composant peut être vide.

## <a name="pathrootpath"></a>path::root_path

```cpp
path root_path() const;
```

Retourne le composant du nom racine de myname, c’est-à-dire root_name() / root_directory. Le composant peut être vide.

## <a name="pathstem"></a>path::stem

```cpp
path stem() const;
```

Retourne le composant stem de myname, c’est-à-dire filename().native() avec les extension().native() de fin supprimés. Le composant peut être vide.

## <a name="pathstring"></a>path::string

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

La première fonction membre (de modèle) convertit la séquence stockée dans mypath de la même façon que :

1. string() for string\<char, Traits, Alloc>()

1. wstring() for string\<wchar_t, Traits, Alloc>()

1. u16string() for string\<char16_t, Traits, Alloc>()

1. u32string() for string\<char32_t, Traits, Alloc>()

La deuxième fonction membre convertit la séquence stockée dans mypath dans l’encodage privilégié par le système hôte pour une séquence de caractères et la retourne stockée dans un objet de type string.

## <a name="pathstringtype"></a>path::string_type

```cpp
typedef basic_string<value_type> string_type;
```

Le type est un synonyme de basic_string<value_type>.

## <a name="pathswap"></a>path::swap

```cpp
void swap(path& right) noexcept;
```

Exécute swap(mypath, right.mypath).

## <a name="pathu16string"></a>path::u16string

```cpp
u16string u16string() const;
```

La fonction membre convertit la séquence stockée dans mypath en UTF-16 et la retourne stockée dans un objet de type u16string.

## <a name="pathu32string"></a>path::u32string

```cpp
u32string u32string() const;
```

La fonction membre convertit la séquence stockée dans mypath en UTF-32 et la retourne stockée dans un objet de type u32string.

## <a name="pathu8string"></a>path::u8string

```cpp
string u8string() const;
```

La fonction membre convertit la séquence stockée dans mypath en UTF-8 et la retourne stockée dans un objet de type u8string.

## <a name="pathvaluetype"></a>path::value_type

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

Le type décrit les éléments du chemin privilégiés par le système d’exploitation hôte.

## <a name="pathwstring"></a>path::wstring

```cpp
wstring wstring() const;
```

Convertit la séquence stockée dans mypath dans l’encodage privilégié par le système hôte pour une séquence wchar_t et la retourne stockée dans un objet de type wstring.

## <a name="requirements"></a>Spécifications

**En-tête :** \<filesystem >

**Espace de noms :** std::experimental::filesystem

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
