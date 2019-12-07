---
title: path, classe
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 0bc26bb04464c52ed08d46e6a12c12cae6909d6f
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898799"
---
# <a name="path-class"></a>path, classe

La classe **path** stocke un objet de type `string_type`, appelé `myname` ici pour les besoins de l’exposition, pouvant être utilisé comme un nom de chemin d’accès. `string_type` est un synonyme de `basic_string<value_type>`, où `value_type` est un synonyme de **wchar_t** sur Windows ou **char** sur POSIX.

Pour obtenir plus d’informations et des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class path;
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[path](#path)|Construit un objet `path`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[const_iterator](#const_iterator)|Synonyme de `iterator`.|
|[iterator](#iterator)|Itérateur de constante bidirectionnel qui désigne les composants `path` de `myname`.|
|[string_type](#string_type)|Le type est un synonyme de `basic_string<value_type>`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[append](#append)|Ajoute la séquence spécifiée à `mypath`, convertie et insère un preferred_separator si nécessaire.|
|[assign](#assign)|Remplace `mypath` par la séquence spécifiée, convertie en fonction des besoins.|
|[begin](#begin)|Retourne un `path::iterator` désignant le premier élément de chemin d’accès dans le nom de chemin d’accès, le cas échéant.|
|[c_str](#c_str)|Retourne un pointeur vers le premier caractère de `mypath`.|
|[clear](#clear)|Exécute `mypath.clear()`.|
|[compare](#compare)|Retourne des valeurs de comparaison.|
|[concat](#compare)|Ajoute la séquence spécifiée à `mypath`, convertie (sans insertion d’un séparateur) selon les besoins.|
|[empty](#empty)|Renvoie `mypath.empty()`.|
|[end](#end)|Retourne un itérateur de fin de séquence de type `iterator`.|
|[extension](#extension)|Retourne le suffixe de `filename()`.|
|[filename](#filename)|Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.|
|[generic_string](#generic_string)|Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u16string](#generic_u16string)|Retourne `u16string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u32string](#generic_u32string)|Retourne `u32string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u8string](#generic_u8string)|Retourne `u8string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_wstring](#generic_wstring)|Retourne `wstring()` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[has_extension](#has_extension)|Renvoie `!extension().empty()`.|
|[has_filename](#has_filename)|Renvoie `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Renvoie `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Renvoie `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Renvoie `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Renvoie `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Renvoie `!root_path().empty()`.|
|[has_stem](#has_stem)|Renvoie `!stem().empty()`.|
|[is_absolute](#is_absolute)|Pour Windows, la fonction retourne `has_root_name() && has_root_directory()`. Pour POSIX, la fonction retourne `has_root_directory()`.|
|[is_relative](#is_relative)|Renvoie `!is_absolute()`.|
|[make_preferred](#make_preferred)|Convertit chaque séparateur en preferred_separator en fonction des besoins.|
|[native](#native)|Renvoie `myname`.|
|[parent_path](#parent_path)|Retourne le composant de chemin d’accès parent de `myname`.|
|[preferred_separator](#preferred_separator)|L’objet de constante donne le caractère préféré pour la séparation des composants du chemin, en fonction du système d’exploitation hôte. |
|[relative_path](#relative_path)|Retourne le composant de chemin d’accès relatif de `myname`. |
|[remove_filename](#remove_filename)|Supprime le nom de fichier.|
|[replace_extension](#replace_extension)|Remplace l’extension de `myname`. |
|[replace_filename](#replace_filename)|RReplaces le nom de fichier.|
|[root_directory](#root_directory)|Retourne le composant du répertoire racine de `myname`. |
|[root_name](#root_name)|Retourne le composant de nom racine de `myname`. |
|[root_path](#root_path)|Retourne le composant de chemin d’accès racine de `myname`.|
|[écoulement](#stem)|Retourne le composant `stem` de `myname`.|
|[string](#string)|Convertit la séquence stockée dans `mypath`.|
|[swap](#swap)|Exécute `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Convertit la séquence stockée dans `mypath` en UTF-16 et la retourne stockée dans un objet de type `u16string`.|
|[u32string](#u32string)|Convertit la séquence stockée dans `mypath` en UTF-32 et la retourne stockée dans un objet de type `u32string`.|
|[u8string](#u8string)|Convertit la séquence stockée dans `mypath` en UTF-8 et la retourne stockée dans un objet de type `u8string`.|
|[value_type](#value_type)|Le type décrit les éléments du chemin privilégiés par le système d’exploitation hôte.|
|[wstring](#wstring)|Convertit la séquence stockée dans `mypath` en l’encodage privilégié par le système hôte pour une séquence de `wchar_t` et la retourne stockée dans un objet de type `wstring`.|

### <a name="operators"></a>Opérateurs

|opérateur|Description|
|-|-|
|[operator=](#op_as)|Remplace les éléments du chemin d’accès par une copie d’un autre chemin d’accès.|
|[operator+=](#op_add)|Différentes expressions de `concat`.|
|[operator/=](#op_divide)|Différentes expressions de `append`.|
|[string_type d’opérateur](#op_string)|Renvoie `myname`.|

## <a name="requirements"></a>Configuration requise pour

**En-tête :** \<FileSystem >

**Espace de noms :** std::experimental::filesystem

## <a name="append"></a>chemin :: Append

Ajoute la séquence spécifiée à `mypath`, convertie et insère un `preferred_separator` si nécessaire.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parameters

\ *source*
Séquence spécifiée.

*premier*\
Début de la séquence spécifiée.

*dernier*\
Fin de la séquence spécifiée.

## <a name="assign"></a> path::assign

Remplace `mypath` par la séquence spécifiée, convertie en fonction des besoins.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parameters

\ *source*
Séquence spécifiée.

*premier*\
Début de la séquence spécifiée.

*dernier*\
Fin de la séquence spécifiée.

## <a name="begin"></a>chemin :: début

Retourne un `path::iterator` désignant le premier élément de chemin d’accès dans le nom de chemin d’accès, le cas échéant.

```cpp
iterator begin() const;
```

## <a name="c_str"></a>chemin :: c_str

Retourne un pointeur vers le premier caractère de `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>Path :: Clear

Exécute `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="compare"></a> path::compare

La première fonction retourne `mypath.compare(pval.native())`. La deuxième fonction retourne `mypath.compare(str)`. La troisième fonction retourne `mypath.compare(ptr)`.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parameters

\ *pval*
Chemin d’accès à comparer.

*str*\
Chaîne à comparer.

\ *ptr*
Pointeur à comparer.

## <a name="concat"></a> path::concat

Ajoute la séquence spécifiée à `mypath`, convertie (sans insertion d’un séparateur) selon les besoins.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parameters

\ *source*
Séquence spécifiée.

*premier*\
Début de la séquence spécifiée.

*dernier*\
Fin de la séquence spécifiée.

## <a name="const_iterator"></a> path::const_iterator

Synonyme de `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>chemin :: vide

Renvoie `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>chemin :: fin

Retourne un itérateur de fin de séquence de type `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a>Path :: extension

Retourne le suffixe de `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Notes

Retourne le suffixe de `filename() X` de manière à ce que :

Si `X == path(".") || X == path("..")` ou si `X` ne contient pas de point, le suffixe est vide.

Dans le cas contraire, le suffixe commence par (et inclut) le point le plus à droite.

## <a name="filename"></a>chemin :: NomFichier

Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.

```cpp
path filename() const;
```

## <a name="generic_string"></a>chemin :: generic_string

Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>chemin :: generic_u16string

Retourne `u16string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a>chemin :: generic_u32string

Retourne `u32string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a>chemin :: generic_u8string

Retourne `u8string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>chemin :: generic_wstring

Retourne `wstring()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>chemin :: has_extension

Renvoie `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a> path::has_filename

Renvoie `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a> path::has_parent_path

Renvoie `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a> path::has_relative_path

Renvoie `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>chemin :: has_root_directory

Renvoie `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>chemin :: has_root_name

Renvoie `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a> path::has_root_path

Renvoie `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>chemin :: has_stem

Renvoie `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>chemin :: is_absolute

Pour Windows, la fonction retourne `has_root_name() && has_root_directory()`. Pour POSIX, la fonction retourne `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>chemin :: is_relative

Renvoie `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>Path :: Iterator

Itérateur de constante bidirectionnel qui désigne les composants de chemin d’accès de `myname`.

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

La classe décrit un itérateur de constante bidirectionnelle qui désigne les composants `path` de `myname` dans la séquence :

1. le nom de la racine, s’il est présent

1. le répertoire racine, s’il est présent

1. les éléments de répertoire restants du `path`parent, s’ils sont présents, se terminant par le nom de fichier, s’il est présent

Pour `pval` un objet de type `path`:

1. `path::iterator X = pval.begin()` désigne le premier élément `path` dans le nom de chemin d’accès, le cas échéant.

1. `X == pval.end()` a la valeur true lorsque `X` pointe juste après la fin de la séquence de composants.

3. `*X` retourne une chaîne qui correspond au composant actuel.

1. `++X` désigne le composant suivant dans la séquence, s'il est présent.

1. `--X` désigne le composant précédent dans la séquence, s'il est présent.

1. La modification de `myname` invalide tous les itérateurs désignant les éléments dans `myname`.

## <a name="make_preferred"></a> path::make_preferred

Convertit chaque séparateur en `preferred_separator` en fonction des besoins.

```cpp
path& make_preferred();
```

## <a name="native"></a> path::native

Renvoie `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a> path::operator=

Remplace les éléments du chemin d’accès par une copie d’un autre chemin d’accès.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parameters

\ *droit*
[Chemin d’accès](../standard-library/path-class.md) copié dans le `path`.

\ *source*
Chemin source.

### <a name="remarks"></a>Notes

Le premier opérateur membre copie `right.myname` vers `myname`. Le deuxième opérateur membre déplace `right.myname` vers `myname`. Le troisième opérateur membre se comporte comme `*this = path(source)`.

## <a name="op_add"></a> path::operator+=

Différentes expressions de `concat`.

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

### <a name="parameters"></a>Parameters

\ *droit*
Chemin d’accès ajouté.

*str*\
Chaîne ajoutée.

\ *ptr*
Pointeur ajouté.

\ *elem*
`value_type` ou `Elem`ajouté.

\ *source*
Source ajoutée.

### <a name="remarks"></a>Notes

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a> path::operator/=

Différentes expressions de `append`.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parameters

\ *droit*
Chemin d’accès ajouté.

\ *source*
Source ajoutée.

### <a name="remarks"></a>Notes

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>Path :: Operator string_type

Renvoie `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a> path::parent_path

Retourne le composant de chemin d’accès parent de `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d’accès parent de `myname`, en particulier le préfixe de `myname` après la suppression de `filename().native()` et des séparateurs de répertoires qui précèdent immédiatement. (De même, si `begin() != end()`, il s’agit de la combinaison de tous les éléments de la plage `[begin(), --end())` en appliquant successivement `operator/=`.) Le composant peut être vide.

## <a name="path"></a> path::path

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

### <a name="parameters"></a>Parameters

\ *droit*
Chemin d’accès dont le chemin d’accès construit doit être une copie.

\ *source*
Source dont le chemin d’accès construit doit être une copie.

\ *loc*
Paramètres régionaux spécifiés.

*premier*\
Position du premier élément à copier.

*dernier*\
Position du dernier élément à copier.

### <a name="remarks"></a>Notes

Tous les constructeurs construisent tous les `myname` de différentes manières :

Pour `path()` il est `myname()`.

Pour `path(const path& right`), il est `myname(right.myname)`.

Pour `path(path&& right)` il est `myname(right.myname)`.

Pour `template<class Source> path(const Source& source)` il est `myname(source)`.

Pour `template<class Source> path(const Source& source, const locale& loc)` il est `myname(source)`, en obtenant toutes les facettes codecvt nécessaires à partir de `loc`.

Pour `template<class InIt> path(InIt first, InIt last)` il est `myname(first, last)`.

Pour `template<class InIt> path(InIt first, InIt last, const locale& loc)` il est `myname(first, last)`, en obtenant toutes les facettes codecvt nécessaires à partir de `loc`.

## <a name="preferred_separator"></a> path::preferred_separator

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

## <a name="relative_path"></a> path::relative_path

Retourne le composant de chemin d’accès relatif de `myname`.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d’accès relatif de `myname`, en particulier le suffixe de `myname` après la suppression de `root_path().native()` et des séparateurs de répertoire redondants immédiatement ultérieurs. Le composant peut être vide.

## <a name="remove_filename"></a> path::remove_filename

Supprime le nom de fichier.

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a> path::replace_extension

Remplace l’extension de `myname`.

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parameters

*newext*\
Nouvelle extension.

### <a name="remarks"></a>Notes

Supprime d’abord le suffixe `extension().native()` de `myname`. Puis, si `!newext.empty() && newext[0] != dot` (où `dot` est `*path(".").c_str()`), `dot` est ajouté à `myname`. Ensuite, *newext* est ajouté à `myname`.

## <a name="replace_filename"></a> path::replace_filename

Remplace le nom de fichier.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parameters

\ *pval*
Chemin d’accès au nom de fichier.

### <a name="remarks"></a>Notes

La fonction membre exécute :

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a> path::root_directory

Retourne le composant du répertoire racine de `myname`.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="root_name"></a> path::root_name

Retourne le composant de nom racine de `myname`.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="root_path"></a> path::root_path

Retourne le composant de chemin d’accès racine de `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d’accès racine de `myname`, spécifiquement `root_name()` / `root_directory`. Le composant peut être vide.

## <a name="stem"></a>chemin :: radical

Retourne le composant `stem` de `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Notes

Retourne le composant `stem` de `myname`, en particulier `filename().native()` avec les `extension().native()` de fin supprimés. Le composant peut être vide.

## <a name="string"></a>Path :: String

Convertit la séquence stockée dans `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Notes

La première fonction membre (de modèle) convertit la séquence stockée dans `mypath` de la même façon que :

1. `string()` pour `string<char, Traits, Alloc>()`

1. `wstring()` pour `string<wchar_t, Traits, Alloc>()`

1. `u16string()` pour `string<char16_t, Traits, Alloc>()`

1. `u32string()` pour `string<char32_t, Traits, Alloc>()`

La deuxième fonction membre convertit la séquence stockée dans `mypath` en l’encodage privilégié par le système hôte pour une séquence de **caractères** et la retourne stockée dans un objet de type `string`.

## <a name="string_type"></a> path::string_type

Le type est un synonyme de `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a> path::swap

Exécute `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>chemin :: u16string

Convertit la séquence stockée dans `mypath` en UTF-16 et la retourne stockée dans un objet de type `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>chemin :: u32string

Convertit la séquence stockée dans `mypath` en UTF-32 et la retourne stockée dans un objet de type `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>chemin :: u8string

Convertit la séquence stockée dans `mypath` en UTF-8 et la retourne stockée dans un objet de type `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a> path::value_type

Le type décrit les éléments `path` favorisés par le système d’exploitation hôte.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a> path::wstring

Convertit la séquence stockée dans `mypath` en l’encodage privilégié par le système hôte pour une séquence de **wchar_t** et la retourne stockée dans un objet de type `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
