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
ms.openlocfilehash: 4559bec84d7e6051155ad73f68a1ef8ae13ca6cc
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104158"
---
# <a name="path-class"></a>path, classe

La classe **path** stocke un objet de type string\_type, appelé ici myname à des fins de démonstration, qui peut être utilisé comme nom de chemin. string\_type est un synonyme de basic\_string\<value_type>, où value\_type est un synonyme de char sur Windows ou wchar_t sur Posix.

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
|[iterator](#iterator)|Un itérateur de constante bidirectionnel qui désigne le `path` composants de `myname`.|
|[string_type](#string_type)|Le type est un synonyme de `basic_string<value_type>`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[append](#append)|Ajoute la séquence spécifiée à `mypath`, convertie et en insérant un preferred_separator selon les besoins.|
|[assign](#assign)|Remplace `mypath` avec la séquence spécifiée, convertie en fonction des besoins.|
|[begin](#begin)|Retourne un `path::iterator` désignant le premier élément de chemin d’accès dans le chemin d’accès, le cas échéant.|
|[c_str](#c_str)|Retourne un pointeur vers le premier caractère dans `mypath`.|
|[clear](#clear)|Exécute `mypath.clear()`.|
|[compare](#compare)|Retourne les valeurs de comparaison.|
|[concat](#compare)|Ajoute la séquence spécifiée à `mypath`, converti (mais ne pas en insérant un séparateur) en fonction des besoins.|
|[empty](#empty)|Retourne `mypath.empty()`.|
|[end](#end)|Retourne un itérateur de fin de séquence de type `iterator`.|
|[extension](#extension)|Retourne le suffixe de `filename()`.|
|[filename](#filename)|Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.|
|[generic_string](#generic_string)|Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u16string](#generic_u16string)|Retourne `u16string()` avec (sur Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u32string](#generic_u32string)|Retourne `u32string()` avec (sur Windows) les barres obliques inverses converties en barres obliques.|
|[generic_u8string](#generic_u8string)|Retourne `u8string()` avec (sur Windows) les barres obliques inverses converties en barres obliques.|
|[generic_wstring](#generic_wstring)|Retourne `wstring()` avec (sur Windows) les barres obliques inverses converties en barres obliques.|
|[has_extension](#has_extension)|Retourne `!extension().empty()`.|
|[has_filename](#has_filename)|Retourne `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Retourne `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Retourne `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Retourne `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Retourne `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Retourne `!root_path().empty()`.|
|[has_stem](#has_stem)|Retourne `!stem().empty()`.|
|[is_absolute](#is_absolute)|Pour Windows, la fonction retourne `has_root_name() && has_root_directory()`. Pour Posix, la fonction retourne `has_root_directory()`.|
|[is_relative.](#is_relative)|Retourne `!is_absolute()`.|
|[make_preferred](#make_preferred)|Convertit chaque séparateur en un preferred_separator selon les besoins.|
|[native](#native)|Retourne `myname`.|
|[parent_path](#parent_path)|Retourne le parent de composant de chemin d’accès de `myname`.|
|[preferred_separator](#preferred_separator)|L’objet de constante donne le caractère préféré pour la séparation des composants du chemin, en fonction du système d’exploitation hôte. |
|[RELATIVE_PATH](#relative_path)|Retourne le composant de chemin d’accès relatif de `myname`. |
|[remove_filename](#remove_filename)|Supprime le nom de fichier.|
|[replace_extension](#replace_extension)|Remplace l’extension de `myname`. |
|[replace_filename](#replace_filename)|RReplaces le nom de fichier.|
|[root_directory](#root_directory)|Retourne le composant du répertoire racine de `myname`. |
|[root_name](#root_name)|Retourne le composant de nom racine de `myname`. |
|[chemin_racine](#root_path)|Retourne le composant de chemin d’accès racine de `myname`.|
|[stem](#stem)|Retourne le `stem` composant de `myname`.|
|[string](#string)|Convertit la séquence stockée dans `mypath`.|
|[swap](#swap)|Exécute `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Convertit la séquence stockée dans `mypath` à UTF-16 et la retourne stockée dans un objet de type `u16string`.|
|[u32string](#u32string)|Convertit la séquence stockée dans `mypath` UTF-32 et la retourne stockée dans un objet de type `u32string`.|
|[u8string](#u8string)|Convertit la séquence stockée dans `mypath` à UTF-8 et la retourne stockée dans un objet de type `u8string`.|
|[value_type](#value_type)|Le type décrit les éléments du chemin privilégiés par le système d’exploitation hôte.|
|[wstring](#wstring)|Convertit la séquence stockée dans `mypath` dans l’encodage privilégié par le système hôte pour un `wchar_t` séquence et la retourne stockée dans un objet de type `wstring`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#op_as)|Remplace les éléments du chemin d’accès avec une copie d’un autre chemin d’accès.|
|[operator+=](#op_add)|Divers `concat` expressions.|
|[operator/=](#op_divide)|Divers `append` expressions.|
|[opérateur string_type](#op_string)|Retourne `myname`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<filesystem >

**Espace de noms :** std::experimental::filesystem

## <a name="append"></a> Path::Append

Ajoute la séquence spécifiée à `mypath`, converti et insérant un `preferred_separator` en fonction des besoins.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*source*<br/>
Séquence spécifiée.

*first*<br/>
Début de la séquence spécifiée.

*last*<br/>
Fin de la séquence spécifiée.

## <a name="assign"></a> Path::Assign

Remplace `mypath` avec la séquence spécifiée, convertie en fonction des besoins.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*source*<br/>
Séquence spécifiée.

*first*<br/>
Début de la séquence spécifiée.

*last*<br/>
Fin de la séquence spécifiée.

## <a name="begin"></a> Path::BEGIN

Retourne un `path::iterator` désignant le premier élément de chemin d’accès dans le chemin d’accès, le cas échéant.

```cpp
iterator begin() const;
```

## <a name="c_str"></a> Path::c_str

Retourne un pointeur vers le premier caractère dans `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a> Path::Clear

Exécute `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="compare"></a> Path::compare

La première fonction retourne `mypath.compare(pval.native())`. La deuxième fonction retourne `mypath.compare(str)`. La troisième fonction retourne `mypath.compare(ptr)`.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Paramètres

*PVal*<br/>
Chemin d’accès à comparer.

*str*<br/>
Chaîne à comparer.

*ptr*<br/>
Pointeur à comparer.

## <a name="concat"></a> Path::concat

Ajoute la séquence spécifiée à `mypath`, converti (mais ne pas en insérant un séparateur) en fonction des besoins.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*source*<br/>
Séquence spécifiée.

*first*<br/>
Début de la séquence spécifiée.

*last*<br/>
Fin de la séquence spécifiée.

## <a name="const_iterator"></a> Path::const_iterator

Synonyme de `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a> Path::Empty

Retourne `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a> Path::end

Retourne un itérateur de fin de séquence de type `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a> Path::extension

Retourne le suffixe de `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Notes

Retourne le suffixe de `filename() X` telles que :

Si `X == path(".") || X == path("..")` ou si `X` ne contient aucun point, le suffixe est vide.

Dans le cas contraire, le suffixe commence par (et inclut) le point le plus à droite.

## <a name="filename"></a> Path::filename

Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.

```cpp
path filename() const;
```

## <a name="generic_string"></a> Path::generic_string

Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a> Path::generic_u16string

Retourne `u16string()` avec (sur Windows) les barres obliques inverses converties en barres obliques.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a> Path::generic_u32string

Retourne `u32string()` avec (sur Windows) les barres obliques inverses converties en barres obliques.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a> Path::generic_u8string

Retourne `u8string()` avec (sur Windows) les barres obliques inverses converties en barres obliques.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a> Path::generic_wstring

Retourne `wstring()` avec (sur Windows) les barres obliques inverses converties en barres obliques.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a> Path::has_extension

Retourne `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a> Path::has_filename

Retourne `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a> Path::has_parent_path

Retourne `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a> Path::has_relative_path

Retourne `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a> Path::has_root_directory

Retourne `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a> Path::has_root_name

Retourne `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a> Path::has_root_path

Retourne `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a> Path::has_stem

Retourne `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a> Path::is_absolute

Pour Windows, la fonction retourne `has_root_name() && has_root_directory()`. Pour Posix, la fonction retourne `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a> Path::is_relative

Retourne `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a> Path::iterator

Un itérateur de constante bidirectionnel qui désigne les composants de chemin d’accès de `myname`.

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

La classe décrit un itérateur de constante bidirectionnel qui désigne le `path` composants de `myname` dans la séquence :

1. le nom de la racine, s’il est présent

1. le répertoire racine, s’il est présent

1. les éléments du répertoire restants du parent `path`, le cas échéant, se terminant par le nom de fichier, le cas échéant

Pour `pval` un objet de type `path`:

1. `path::iterator X = pval.begin()` désigne le premier `path` élément dans le chemin d’accès, le cas échéant.

1. `X == pval.end()` se produit lorsque `X` pointe juste après la fin de la séquence de composants.

3. `*X` Retourne une chaîne qui correspond au composant actuel

1. `++X` désigne le composant suivant dans la séquence, s'il est présent.

1. `--X` désigne le composant précédent dans la séquence, s'il est présent.

1. Modification `myname` invalide tous les itérateurs désignant des éléments dans `myname`.

## <a name="make_preferred"></a> Path::make_preferred

Convertit chaque séparateur en un preferred_separator selon les besoins.

```cpp
path& make_preferred();
```

## <a name="native"></a> Path::native

Retourne `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a> Path::operator =

Remplace les éléments du chemin d’accès avec une copie d’un autre chemin d’accès.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [chemin d’accès](../standard-library/path-class.md) copié dans le `path`.

*source*<br/>
Le chemin d’accès source.

### <a name="remarks"></a>Notes

Les copies d’opérateur membre premier `right.myname` à `myname`. Déplace le deuxième opérateur membre `right.myname` à `myname`. Le troisième opérateur membre comporte comme `*this = path(source)`.

## <a name="op_add"></a> Path::operator +=

Divers `concat` expressions.

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

*right*<br/>
Le chemin d’accès ajouté.

*str*<br/>
La chaîne ajoutée.

*ptr*<br/>
Le pointeur ajouté.

*Elem*<br/>
L’ajout `value_type` ou `Elem`.

*source*<br/>
La source ajoutée.

### <a name="remarks"></a>Notes

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string\<Elem>(1, elem)));`

## <a name="op_divide"></a> Path::operator / =

Divers `append` expressions.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le chemin d’accès ajouté.

*source*<br/>
La source ajoutée.

### <a name="remarks"></a>Notes

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a> Path::operator string_type

Retourne `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a> Path::parent_path

Retourne le parent de composant de chemin d’accès de `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Notes

Retourne le parent de composant de chemin d’accès de `myname`, spécifiquement le préfixe de `myname` après la suppression `filename().native()` et des séparateurs de répertoire immédiatement précédents. (De même, si `begin() != end()`, il correspond à la combinaison de tous les éléments dans la plage [begin(),--end()) en appliquant successivement l’opérateur / =.) Le composant peut être vide.

## <a name="path"></a> Path::path

Construit un `path` de différentes manières.

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

*right*<br/>
Le chemin d’accès sur lequel le chemin d’accès construit doit être une copie.

*source*<br/>
La source sur lequel le chemin d’accès construit doit être une copie.

*Loc*<br/>
Les paramètres régionaux spécifiés.

*first*<br/>
Position du premier élément à copier.

*last*<br/>
La position du dernier élément à copier.

### <a name="remarks"></a>Notes

Les constructeurs tout construire `myname` de différentes manières :

Pour `path()` doivent impérativement `myname()`.

Pour `path(const path& right`) il est `myname(right.myname)`.

Pour `path(path&& right)` doivent impérativement `myname(right.myname)`.

Pour `template<class Source> path(const Source& source)` doivent impérativement `myname(source)`.

Pour `template<class Source> path(const Source& source, const locale& loc)` doivent impérativement `myname(source)`, obtenant toutes facettes codecvt nécessaires de `loc`.

Pour `template<class InIt> path(InIt first, InIt last)` doivent impérativement `myname(first, last)`.

Pour `template<class InIt> path(InIt first, InIt last, const locale& loc)` doivent impérativement `myname(first, last)`, obtenant toutes facettes codecvt nécessaires de `loc`.

## <a name="preferred_separator"></a> Path::preferred_separator

L’objet de constante donne le caractère préféré pour la séparation des composants du chemin, en fonction du système d’exploitation hôte. 

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Notes

Notez qu’il est également possible dans la plupart des contextes sous Windows d’utiliser à la place L'/'.

## <a name="relative_path"></a> Path::RELATIVE_PATH

Retourne le composant de chemin d’accès relatif de `myname`. 

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d’accès relatif de `myname`, spécifiquement le suffixe de `myname` après la suppression `root_path().native()` et des séparateurs de répertoire redondants immédiatement suivants. Le composant peut être vide.

## <a name="remove_filename"></a> Path::remove_filename

Supprime le nom de fichier.

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a> Path::replace_extension

Remplace l’extension de `myname`. 

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Paramètres

*newext*<br/>
La nouvelle extension.

### <a name="remarks"></a>Notes

Supprime d’abord le suffixe `extension().native()` de `myname`. Ensuite si `!newext.empty() && newext[0] != dot` (où `dot` est `*path(".").c_str()`), puis `dot` est ajouté à `myname`. Puis `newext` est ajouté à `myname`.

## <a name="replace_filename"></a> Path::replace_filename

Remplace le nom de fichier.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Paramètres

*PVal*<br/>
Le chemin d’accès du nom de fichier.

### <a name="remarks"></a>Notes

La fonction membre exécute :

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a> Path::root_directory

Retourne le composant du répertoire racine de `myname`. 

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="root_name"></a> Path::root_name

Retourne le composant de nom racine de `myname`. 

```cpp
path root_name() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="root_path"></a> Path::root_path

Retourne le composant de chemin d’accès racine de `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d’accès racine de `myname`, root_name() / root_directory. Le composant peut être vide.

## <a name="stem"></a> Path::stem

Retourne le `stem` composant de `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Notes

Retourne le `stem` composant de `myname`, plus précisément `filename().native()` avec n’importe quel type de fin `extension().native()` supprimé. Le composant peut être vide.

## <a name="string"></a> Path::String

Convertit la séquence stockée dans `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Notes

La première fonction membre (de modèle) convertit la séquence stockée dans mypath de la même façon que :

1. `string()` pour `string<char, Traits, Alloc>()`

1. `wstring()` pour `string<wchar_t, Traits, Alloc>()`

1. `u16string()` pour `string<char16_t, Traits, Alloc>()`

1. `u32string()` pour `string<char32_t, Traits, Alloc>()`

La deuxième fonction membre convertit la séquence stockée dans `mypath` pour l’encodage privilégié par le système hôte pour une séquence de caractères et la retourne stockée dans un objet de type chaîne.

## <a name="string_type"></a> Path::STRING_TYPE

Le type est un synonyme de `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a> Path::swap

Exécute `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a> Path::u16string

Convertit la séquence stockée dans `mypath` à UTF-16 et la retourne stockée dans un objet de type `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a> Path::u32string

Convertit la séquence stockée dans `mypath` UTF-32 et la retourne stockée dans un objet de type `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a> Path::u8string

Convertit la séquence stockée dans `mypath` à UTF-8 et la retourne stockée dans un objet de type `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a> Path::Value_type

Le type décrit les éléments du chemin privilégiés par le système d’exploitation hôte.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a> Path::wstring

Convertit la séquence stockée dans `mypath` dans l’encodage privilégié par le système hôte pour un `wchar_t` séquence et la retourne stockée dans un objet de type `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
