---
title: path, classe
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 669dfd2c8cd8576ebfb6684bab7cf63cdd51babc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372106"
---
# <a name="path-class"></a>path, classe

La classe **de chemin** `string_type`stocke `myname` un objet de type , appelé ici pour les fins de l’exposition, approprié pour une utilisation comme nom de chemin. `string_type`est un synonyme `basic_string<value_type>`de `value_type` , où est un synonyme de **wchar_t** sur Windows ou **char** sur POSIX.

Pour plus d’informations et des exemples de code, voir La navigation du système de fichiers [( CMD).](../standard-library/file-system-navigation.md)

## <a name="syntax"></a>Syntaxe

```cpp
class path;
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[path](#path)|Construit un objet `path`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[const_iterator](#const_iterator)|Synonyme de `iterator`.|
|[Itérateur](#iterator)|Un itérateur bidirectionnel constant `path` qui `myname`désigne les composants de .|
|[string_type](#string_type)|Le type est un synonyme de `basic_string<value_type>`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Ajouter](#append)|Annexe la séquence spécifiée à `mypath`, converti et l’insertion d’un preferred_separator au besoin.|
|[Attribuer](#assign)|Remplace `mypath` par la séquence spécifiée, convertie au besoin.|
|[Commencer](#begin)|Retourne `path::iterator` une désignation du premier élément de chemin dans le nom de chemin, si présent.|
|[c_str](#c_str)|Retourne un pointeur au `mypath`premier personnage dans .|
|[Clair](#clear)|Exécute `mypath.clear()`.|
|[Comparer](#compare)|Retourne les valeurs de comparaison.|
|[Concat](#compare)|Annexe la séquence spécifiée à `mypath`, converti (mais ne pas insérer un séparateur) au besoin.|
|[Vide](#empty)|Retourne `mypath.empty()`.|
|[Fin](#end)|Retourne un itérateur de fin `iterator`de séquence de type .|
|[Extension](#extension)|Retourne le suffixe de `filename()`.|
|[Fichier](#filename)|Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.|
|[generic_string](#generic_string)|Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u16string](#generic_u16string)|Retourne `u16string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u32string](#generic_u32string)|Retourne `u32string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u8string](#generic_u8string)|Retourne `u8string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_wstring](#generic_wstring)|Retourne `wstring()` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[has_extension](#has_extension)|Retourne `!extension().empty()`.|
|[has_filename](#has_filename)|Retourne `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Retourne `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Retourne `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Retourne `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Retourne `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Retourne `!root_path().empty()`.|
|[has_stem](#has_stem)|Retourne `!stem().empty()`.|
|[is_absolute](#is_absolute)|Pour Windows, la `has_root_name() && has_root_directory()`fonction revient . Pour POSIX, la `has_root_directory()`fonction revient .|
|[is_relative](#is_relative)|Retourne `!is_absolute()`.|
|[make_preferred](#make_preferred)|Convertit chaque séparateur en preferred_separator au besoin.|
|[Natif](#native)|Retourne `myname`.|
|[parent_path](#parent_path)|Retourne la composante `myname`de chemin parent de .|
|[preferred_separator](#preferred_separator)|L’objet de constante donne le caractère préféré pour la séparation des composants du chemin, en fonction du système d’exploitation hôte. |
|[relative_path](#relative_path)|Retourne la composante `myname`relative du chemin de . |
|[remove_filename](#remove_filename)|Supprime le nom de fichier.|
|[replace_extension](#replace_extension)|Remplace l’extension `myname`de . |
|[replace_filename](#replace_filename)|RReplaces le nom de fichier.|
|[root_directory](#root_directory)|Retourne la composante d’annuaire racine de `myname`. |
|[root_name](#root_name)|Retourne le composant `myname`nom de racine de . |
|[root_path](#root_path)|Retourne la composante `myname`de chemin de racine de .|
|[stem](#stem)|Retourne `stem` la `myname`composante de .|
|[string](#string)|Convertit la séquence `mypath`stockée dans .|
|[swap](#swap)|Exécute `swap(mypath, right.mypath)`.|
|[u16string u16string u16string u1](#u16string)|Convertit la séquence `mypath` stockée dans UTF-16 et la `u16string`renvoie stockée dans un objet de type .|
|[u32string](#u32string)|Convertit la séquence `mypath` stockée dans UTF-32 et la `u32string`renvoie stockée dans un objet de type .|
|[u8string u8string u8string u8](#u8string)|Convertit la séquence `mypath` stockée dans UTF-8 et la `u8string`renvoie stockée dans un objet de type .|
|[value_type](#value_type)|Le type décrit les éléments du chemin privilégiés par le système d’exploitation hôte.|
|[wstring](#wstring)|Convertit la séquence `mypath` stockée dans l’encodage `wchar_t` favorisé par le système hôte `wstring`pour une séquence et la renvoie stockée dans un objet de type .|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur](#op_as)|Remplace les éléments du chemin par une copie d’un autre chemin.|
|[opérateur](#op_add)|Diverses `concat` expressions.|
|[opérateur/MD](#op_divide)|Diverses `append` expressions.|
|[string_type de l’opérateur](#op_string)|Retourne `myname`.|

## <a name="requirements"></a>Spécifications

**En-tête:** \<filesystem>

**Espace de noms :** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a>chemin::append

Annexe la séquence spécifiée à `mypath`, converti `preferred_separator` et l’insertion d’un au besoin.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*Source*\
Séquence spécifiée.

*Première*\
Début de séquence spécifiée.

*Dernière*\
Fin de séquence spécifiée.

## <a name="pathassign"></a><a name="assign"></a>chemin::assigner

Remplace `mypath` par la séquence spécifiée, convertie au besoin.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*Source*\
Séquence spécifiée.

*Première*\
Début de séquence spécifiée.

*Dernière*\
Fin de séquence spécifiée.

## <a name="pathbegin"></a><a name="begin"></a>chemin::commencer

Retourne `path::iterator` une désignation du premier élément de chemin dans le nom de chemin, si présent.

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>chemin::c_str

Retourne un pointeur au `mypath`premier personnage dans .

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>chemin::clair

Exécute `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>chemin::comparer

La première fonction retourne `mypath.compare(pval.native())`. La deuxième fonction retourne `mypath.compare(str)`. La troisième `mypath.compare(ptr)`fonction revient .

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Paramètres

*pval (pval)*\
Chemin à comparer.

*Str*\
Chaîne à comparer.

*Ptr*\
Pointeur à comparer.

## <a name="pathconcat"></a><a name="concat"></a>chemin::concat

Annexe la séquence spécifiée à `mypath`, converti (mais ne pas insérer un séparateur) au besoin.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*Source*\
Séquence spécifiée.

*Première*\
Début de séquence spécifiée.

*Dernière*\
Fin de séquence spécifiée.

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>chemin::const_iterator

Synonyme de `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>chemin::vide

Retourne `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>chemin::fin

Retourne un itérateur de fin `iterator`de séquence de type .

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>chemin::extension

Retourne le suffixe de `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Notes

Retourne le suffixe de `filename() X` telle sorte que:

Si `X == path(".") || X == path("..")` ou `X` si elle ne contient pas de point, le suffixe est vide.

Dans le cas contraire, le suffixe commence par (et inclut) le point le plus à droite.

## <a name="pathfilename"></a><a name="filename"></a>chemin::nom de fichier

Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>chemin::generic_string

Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>chemin::generic_u16string

Retourne `u16string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>chemin::generic_u32string

Retourne `u32string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>chemin::generic_u8string

Retourne `u8string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>chemin::generic_wstring

Retourne `wstring()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>chemin::has_extension

Retourne `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>chemin::has_filename

Retourne `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>chemin::has_parent_path

Retourne `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>chemin::has_relative_path

Retourne `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>chemin::has_root_directory

Retourne `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>chemin::has_root_name

Retourne `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>chemin::has_root_path

Retourne `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>chemin::has_stem

Retourne `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>chemin::is_absolute

Pour Windows, la `has_root_name() && has_root_directory()`fonction revient . Pour POSIX, la `has_root_directory()`fonction revient .

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>chemin::is_relative

Retourne `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>chemin::iterator

Un itérateur bidirectionnel constant qui désigne `myname`les composantes de chemin de .

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

### <a name="remarks"></a>Notes

La classe décrit un itérateur de constante `path` bidirectionnelle qui désigne les composants de `myname` la séquence :

1. le nom de la racine, s’il est présent

1. le répertoire racine, s’il est présent

1. les éléments d’annuaire `path`restants du parent, s’il est présent, se terminant par le nom de fichier, s’il est présent

Pour `pval` un objet `path`de type :

1. `path::iterator X = pval.begin()`désigne le `path` premier élément du nom du chemin, s’il est présent.

1. `X == pval.end()`est vrai `X` lorsque des points juste après la fin de la séquence des composants.

1. `*X`retourne une chaîne qui correspond à la composante actuelle

1. `++X` désigne le composant suivant dans la séquence, s'il est présent.

1. `--X` désigne le composant précédent dans la séquence, s'il est présent.

1. Modification `myname` invalide tous les itérateurs `myname`désignant des éléments dans .

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>chemin::make_preferred

Convertit chaque séparateur en un `preferred_separator` au besoin.

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>chemin::natif

Retourne `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>chemin::opérateur

Remplace les éléments du chemin par une copie d’un autre chemin.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Le [chemin](../standard-library/path-class.md) étant copié `path`dans le .

*Source*\
Le chemin source.

### <a name="remarks"></a>Notes

Le premier opérateur `right.myname` `myname`membre copie à . Le deuxième opérateur `right.myname` `myname`membre se déplace à . Le troisième opérateur membre se `*this = path(source)`comporte de la même façon que .

## <a name="pathoperator"></a><a name="op_add"></a>chemin::opérateur

Diverses `concat` expressions.

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

### <a name="parameters"></a>Paramètres

*Oui*\
Le chemin ajouté.

*Str*\
La ficelle ajoutée.

*Ptr*\
Le pointeur ajouté.

*Elem*\
`value_type` L’ajout `Elem`ou .

*Source*\
La source ajoutée.

### <a name="remarks"></a>Notes

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a>chemin::opérateur/

Diverses `append` expressions.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Le chemin ajouté.

*Source*\
La source ajoutée.

### <a name="remarks"></a>Notes

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a>chemin::opérateur string_type

Retourne `myname`.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>chemin::parent-path

Retourne la composante `myname`de chemin parent de .

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Notes

Retourne la composante `myname`de chemin parent `myname` de , `filename().native()` en particulier le préfixe de après l’enlèvement et tous les séparateurs d’annuaire immédiatement précédant. (De même, si `begin() != end()`, il s’agit `[begin(), --end())` de la `operator/=`combinaison de tous les éléments de la gamme en appliquant successivement .) Le composant peut être vide.

## <a name="pathpath"></a><a name="path"></a>chemin::path

Construit une `path` de différentes façons.

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

### <a name="parameters"></a>Paramètres

*Oui*\
Le chemin dont le chemin construit doit être une copie.

*Source*\
La source dont le chemin construit doit être une copie.

*Loc*\
Le lieu spécifié.

*Première*\
Position du premier élément à copier.

*Dernière*\
La position du dernier élément à copier.

### <a name="remarks"></a>Notes

Les constructeurs `myname` construisent tous de différentes manières :

Car `path()` il `myname()`est .

Pour `path(const path& right`) `myname(right.myname)`il est .

Car `path(path&& right)` il `myname(right.myname)`est .

Car `template<class Source> path(const Source& source)` il `myname(source)`est .

Pour `template<class Source> path(const Source& source, const locale& loc)` elle `myname(source)`est , l’obtention de `loc`toutes les facettes codecvt nécessaire à partir de .

Car `template<class InIt> path(InIt first, InIt last)` il `myname(first, last)`est .

Pour `template<class InIt> path(InIt first, InIt last, const locale& loc)` elle `myname(first, last)`est , l’obtention de `loc`toutes les facettes codecvt nécessaire à partir de .

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>chemin::preferred-separator

L’objet de constante donne le caractère préféré pour la séparation des composants du chemin, en fonction du système d’exploitation hôte.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Notes

Notez qu’il est également possible dans la plupart des contextes sous Windows d’utiliser à la place L'/'.

## <a name="pathrelative_path"></a><a name="relative_path"></a>chemin::relative_path

Retourne la composante `myname`relative du chemin de .

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Notes

Retourne la composante `myname`relative de chemin `myname` de , `root_path().native()` en particulier le suffixe d’après la suppression et les séparateurs d’annuaire redondant immédiatement ultérieurs. Le composant peut être vide.

## <a name="pathremove_filename"></a><a name="remove_filename"></a>chemin::remove_filename

Supprime le nom de fichier.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>chemin::replace_extension

Remplace l’extension `myname`de .

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Paramètres

*newext*\
La nouvelle extension.

### <a name="remarks"></a>Notes

Enlève d’abord `extension().native()` le `myname`suffixe de . Ensuite, `!newext.empty() && newext[0] != dot` si `dot` `*path(".").c_str()`(où est), `dot` `myname`puis est annexé à . Puis *newext* est annexé à `myname`.

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>chemin::replace_filename

Remplace le nom de fichier.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Paramètres

*pval (pval)*\
Le chemin du nom de fichier.

### <a name="remarks"></a>Notes

La fonction membre exécute :

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a>chemin::root_directory

Retourne la composante d’annuaire racine de `myname`.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="pathroot_name"></a><a name="root_name"></a>chemin::root_name

Retourne le composant `myname`nom de racine de .

```cpp
path root_name() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="pathroot_path"></a><a name="root_path"></a>chemin::root_path

Retourne la composante `myname`de chemin de racine de .

```cpp
path root_path() const;
```

### <a name="remarks"></a>Notes

Retourne la composante `myname`de `root_name()`  /  `root_directory`chemin de racine de , en particulier . Le composant peut être vide.

## <a name="pathstem"></a><a name="stem"></a>chemin::stem

Retourne `stem` la `myname`composante de .

```cpp
path stem() const;
```

### <a name="remarks"></a>Notes

Retourne `stem` le `myname`composant `filename().native()` de , `extension().native()` spécifiquement avec toute traînée enlevée. Le composant peut être vide.

## <a name="pathstring"></a><a name="string"></a>chemin::corde

Convertit la séquence `mypath`stockée dans .

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Notes

La première fonction membre (modèle) convertit la séquence stockée de `mypath` la même manière que :

1. `string()` pour `string<char, Traits, Alloc>()`

1. `wstring()` pour `string<wchar_t, Traits, Alloc>()`

1. `u16string()` pour `string<char16_t, Traits, Alloc>()`

1. `u32string()` pour `string<char32_t, Traits, Alloc>()`

La deuxième fonction de membre `mypath` convertit la séquence stockée dans l’encodage favorisé par le `string`système hôte pour une séquence **d’omble et** la renvoie stockée dans un objet de type .

## <a name="pathstring_type"></a><a name="string_type"></a>chemin::string_type

Le type est un synonyme de `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>chemin::swap

Exécute `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>chemin::u16string

Convertit la séquence `mypath` stockée dans UTF-16 et la `u16string`renvoie stockée dans un objet de type .

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>chemin::u32string

Convertit la séquence `mypath` stockée dans UTF-32 et la `u32string`renvoie stockée dans un objet de type .

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>chemin::u8string

Convertit la séquence `mypath` stockée dans UTF-8 et la `u8string`renvoie stockée dans un objet de type .

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>chemin::value_type

Le type décrit `path` les éléments favorisés par le système d’exploitation hôte.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>chemin::wstring

Convertit la séquence `mypath` stockée dans l’encodage favorisé par le système hôte pour une `wstring`séquence **wchar_t** et la renvoie stockée dans un objet de type .

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
