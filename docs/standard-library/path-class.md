---
title: path, classe
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: d7c8c739c3d235383ede0509cfa87b41200efeca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233000"
---
# <a name="path-class"></a>path, classe

La classe **path** stocke un objet de type `string_type` , appelé `myname` ici pour les besoins de l’exposition, pouvant être utilisé comme un nom de chemin d’accès. `string_type`est un synonyme de `basic_string<value_type>` , où `value_type` est un synonyme de **`wchar_t`** sur Windows ou **`char`** sur POSIX.

Pour plus d’informations et pour obtenir des exemples de code, consultez navigation dans le [système de fichiers (C++)](../standard-library/file-system-navigation.md).

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
|[répétiteur](#iterator)|Itérateur de constante bidirectionnel qui désigne les `path` composants de `myname` .|
|[string_type](#string_type)|Le type est un synonyme de `basic_string<value_type>`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[append](#append)|Ajoute la séquence spécifiée à `mypath` , convertie et insérant une preferred_separator si nécessaire.|
|[assign](#assign)|Remplace `mypath` par la séquence spécifiée, convertie en fonction des besoins.|
|[commencer](#begin)|Retourne une valeur `path::iterator` désignant le premier élément de chemin d’accès dans le nom de chemin d’accès, le cas échéant.|
|[c_str](#c_str)|Retourne un pointeur vers le premier caractère de `mypath` .|
|[clear](#clear)|Exécute `mypath.clear()` .|
|[compar](#compare)|Retourne des valeurs de comparaison.|
|[concat](#compare)|Ajoute la séquence spécifiée à `mypath` , convertie (sans insertion d’un séparateur) selon les besoins.|
|[empty](#empty)|Retourne `mypath.empty()`.|
|[end](#end)|Retourne un itérateur de fin de séquence de type `iterator` .|
|[poste](#extension)|Retourne le suffixe de `filename()` .|
|[extension](#filename)|Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.|
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
|[is_absolute](#is_absolute)|Pour Windows, la fonction retourne `has_root_name() && has_root_directory()` . Pour POSIX, la fonction retourne `has_root_directory()` .|
|[is_relative](#is_relative)|Retourne `!is_absolute()`.|
|[make_preferred](#make_preferred)|Convertit chaque séparateur en preferred_separator en fonction des besoins.|
|[native](#native)|Retourne `myname`.|
|[parent_path](#parent_path)|Retourne le composant de chemin d’accès parent de `myname` .|
|[preferred_separator](#preferred_separator)|L’objet de constante donne le caractère préféré pour la séparation des composants du chemin, en fonction du système d’exploitation hôte. |
|[relative_path](#relative_path)|Retourne le composant de chemin d’accès relatif de `myname` . |
|[remove_filename](#remove_filename)|Supprime le nom de fichier.|
|[replace_extension](#replace_extension)|Remplace l’extension de `myname` . |
|[replace_filename](#replace_filename)|RReplaces le nom de fichier.|
|[root_directory](#root_directory)|Retourne le composant du répertoire racine de `myname` . |
|[root_name](#root_name)|Retourne le composant de nom racine de `myname` . |
|[root_path](#root_path)|Retourne le composant de chemin d’accès racine de `myname` .|
|[stem](#stem)|Retourne le `stem` composant de `myname` .|
|[string](#string)|Convertit la séquence stockée dans `mypath` .|
|[swap](#swap)|Exécute `swap(mypath, right.mypath)` .|
|[u16string](#u16string)|Convertit la séquence stockée en `mypath` UTF-16 et la retourne stockée dans un objet de type `u16string` .|
|[u32string](#u32string)|Convertit la séquence stockée dans en `mypath` UTF-32 et la retourne stockée dans un objet de type `u32string` .|
|[u8string](#u8string)|Convertit la séquence stockée en `mypath` UTF-8 et la retourne stockée dans un objet de type `u8string` .|
|[value_type](#value_type)|Le type décrit les éléments du chemin privilégiés par le système d’exploitation hôte.|
|[wstring](#wstring)|Convertit la séquence stockée dans en `mypath` l’encodage privilégié par le système hôte pour une **`wchar_t`** séquence et la retourne stockée dans un objet de type `wstring` .|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#op_as)|Remplace les éléments du chemin d’accès par une copie d’un autre chemin d’accès.|
|[opérateur + =](#op_add)|Différentes `concat` expressions.|
|[opérateur/=](#op_divide)|Différentes `append` expressions.|
|[string_type d’opérateur](#op_string)|Retourne `myname`.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<filesystem>

**Espace de noms :** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a>chemin :: Append

Ajoute la séquence spécifiée à `mypath` , convertie et insérant `preferred_separator` si nécessaire.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*code*\
Séquence spécifiée.

*premier*\
Début de la séquence spécifiée.

*famille*\
Fin de la séquence spécifiée.

## <a name="pathassign"></a><a name="assign"></a>Path :: assign

Remplace `mypath` par la séquence spécifiée, convertie en fonction des besoins.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*code*\
Séquence spécifiée.

*premier*\
Début de la séquence spécifiée.

*famille*\
Fin de la séquence spécifiée.

## <a name="pathbegin"></a><a name="begin"></a>chemin :: début

Retourne une valeur `path::iterator` désignant le premier élément de chemin d’accès dans le nom de chemin d’accès, le cas échéant.

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>chemin :: c_str

Retourne un pointeur vers le premier caractère de `mypath` .

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>Path :: Clear

Exécute `mypath.clear()` .

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>chemin :: compare

La première fonction retourne `mypath.compare(pval.native())`. La deuxième fonction retourne `mypath.compare(str)`. La troisième fonction retourne `mypath.compare(ptr)` .

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Paramètres

*pval*\
Chemin d’accès à comparer.

*Str*\
Chaîne à comparer.

*effectués*\
Pointeur à comparer.

## <a name="pathconcat"></a><a name="concat"></a>Path :: Concat

Ajoute la séquence spécifiée à `mypath` , convertie (sans insertion d’un séparateur) selon les besoins.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Paramètres

*code*\
Séquence spécifiée.

*premier*\
Début de la séquence spécifiée.

*famille*\
Fin de la séquence spécifiée.

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>chemin :: const_iterator

Synonyme de `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>chemin :: vide

Retourne `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>chemin :: fin

Retourne un itérateur de fin de séquence de type `iterator` .

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>Path :: extension

Retourne le suffixe de `filename()` .

```cpp
path extension() const;
```

### <a name="remarks"></a>Notes

Retourne le suffixe de `filename() X` ce qui suit :

Si `X == path(".") || X == path("..")` ou si `X` ne contient pas de point, le suffixe est vide.

Dans le cas contraire, le suffixe commence par (et inclut) le point le plus à droite.

## <a name="pathfilename"></a><a name="filename"></a>chemin :: NomFichier

Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>chemin :: generic_string

Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>chemin :: generic_u16string

Retourne `u16string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>chemin :: generic_u32string

Retourne `u32string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>chemin :: generic_u8string

Retourne `u8string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>chemin :: generic_wstring

Retourne `wstring()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>chemin :: has_extension

Retourne `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>chemin :: has_filename

Retourne `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>chemin :: has_parent_path

Retourne `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>chemin :: has_relative_path

Retourne `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>chemin :: has_root_directory

Retourne `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>chemin :: has_root_name

Retourne `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>chemin :: has_root_path

Retourne `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>chemin :: has_stem

Retourne `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>chemin :: is_absolute

Pour Windows, la fonction retourne `has_root_name() && has_root_directory()` . Pour POSIX, la fonction retourne `has_root_directory()` .

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>chemin :: is_relative

Retourne `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>Path :: Iterator

Itérateur de constante bidirectionnel qui désigne les composants de chemin d’accès de `myname` .

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

La classe décrit un itérateur de constante bidirectionnel qui désigne les `path` composants de `myname` dans la séquence :

1. le nom de la racine, s’il est présent

1. le répertoire racine, s’il est présent

1. éléments de répertoire restants du parent `path` , le cas échéant, se terminant par le nom de fichier, s’il est présent

Pour `pval` un objet de type `path` :

1. `path::iterator X = pval.begin()`désigne le premier `path` élément dans le nom de chemin d’accès, le cas échéant.

1. `X == pval.end()`est true lorsque `X` pointe vers la fin de la séquence de composants.

1. `*X`retourne une chaîne qui correspond au composant actuel.

1. `++X` désigne le composant suivant dans la séquence, s'il est présent.

1. `--X` désigne le composant précédent dans la séquence, s'il est présent.

1. La modification `myname` invalide tous les itérateurs désignant les éléments dans `myname` .

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>chemin :: make_preferred

Convertit chaque séparateur en `preferred_separator` , si nécessaire.

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>chemin d’accès :: natif

Retourne `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>Path :: Operator =

Remplace les éléments du chemin d’accès par une copie d’un autre chemin d’accès.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Chemin d’accès](../standard-library/path-class.md) copié dans le `path` .

*code*\
Chemin source.

### <a name="remarks"></a>Notes

Le premier opérateur membre copie `right.myname` vers `myname` . Le deuxième opérateur membre se déplace `right.myname` vers `myname` . Le troisième opérateur membre se comporte de la même façon que `*this = path(source)` .

## <a name="pathoperator"></a><a name="op_add"></a>Path :: Operator + =

Différentes `concat` expressions.

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
Chemin d’accès ajouté.

*Str*\
Chaîne ajoutée.

*effectués*\
Pointeur ajouté.

*elem*\
Ajouté `value_type` ou `Elem` .

*code*\
Source ajoutée.

### <a name="remarks"></a>Notes

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a>Path :: Operator/=

Différentes `append` expressions.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Chemin d’accès ajouté.

*code*\
Source ajoutée.

### <a name="remarks"></a>Notes

Les fonctions membres se comportent comme les expressions correspondantes suivantes :

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a>Path :: Operator string_type

Retourne `myname`.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>chemin d’accès ::p arent_path

Retourne le composant de chemin d’accès parent de `myname` .

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d’accès parent de `myname` , en particulier le préfixe de `myname` après suppression `filename().native()` et les séparateurs de répertoire précédents. (De même, si `begin() != end()` , il s’agit de la combinaison de tous les éléments de la plage `[begin(), --end())` en appliquant successivement `operator/=` .) Le composant peut être vide.

## <a name="pathpath"></a><a name="path"></a>chemin d’accès ::p hemin

Construit un `path` de différentes façons.

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
Chemin d’accès dont le chemin d’accès construit doit être une copie.

*code*\
Source dont le chemin d’accès construit doit être une copie.

*Loc*\
Paramètres régionaux spécifiés.

*premier*\
Position du premier élément à copier.

*famille*\
Position du dernier élément à copier.

### <a name="remarks"></a>Notes

Les constructeurs sont tous construits `myname` de différentes manières :

`path()`C’est le cas `myname()` .

Pour `path(const path& right` ), il s’agit de `myname(right.myname)` .

`path(path&& right)`C’est le cas `myname(right.myname)` .

`template<class Source> path(const Source& source)`C’est le cas `myname(source)` .

Pour `template<class Source> path(const Source& source, const locale& loc)` ce faire `myname(source)` , vous obtenez toutes les facettes codecvt nécessaires à partir de `loc` .

`template<class InIt> path(InIt first, InIt last)`C’est le cas `myname(first, last)` .

Pour `template<class InIt> path(InIt first, InIt last, const locale& loc)` ce faire `myname(first, last)` , vous obtenez toutes les facettes codecvt nécessaires à partir de `loc` .

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>chemin d’accès ::p referred_separator

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

## <a name="pathrelative_path"></a><a name="relative_path"></a>chemin :: relative_path

Retourne le composant de chemin d’accès relatif de `myname` .

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d’accès relatif de `myname` , spécifiquement le suffixe de `myname` après suppression `root_path().native()` et les séparateurs de répertoire redondants immédiatement ultérieurs. Le composant peut être vide.

## <a name="pathremove_filename"></a><a name="remove_filename"></a>chemin :: remove_filename

Supprime le nom de fichier.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>chemin :: replace_extension

Remplace l’extension de `myname` .

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Paramètres

*newext*\
Nouvelle extension.

### <a name="remarks"></a>Notes

Supprime d’abord le suffixe `extension().native()` de `myname` . Puis `!newext.empty() && newext[0] != dot` , si (où `dot` est `*path(".").c_str()` ), `dot` est ajouté à `myname` . Ensuite, *newext* est ajouté à `myname` .

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>chemin :: replace_filename

Remplace le nom de fichier.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Paramètres

*pval*\
Chemin d’accès au nom de fichier.

### <a name="remarks"></a>Notes

La fonction membre exécute :

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a>chemin :: root_directory

Retourne le composant du répertoire racine de `myname` .

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="pathroot_name"></a><a name="root_name"></a>chemin :: root_name

Retourne le composant de nom racine de `myname` .

```cpp
path root_name() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="pathroot_path"></a><a name="root_path"></a>chemin :: root_path

Retourne le composant de chemin d’accès racine de `myname` .

```cpp
path root_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d’accès racine de `myname` , en particulier `root_name()`  /  `root_directory` . Le composant peut être vide.

## <a name="pathstem"></a><a name="stem"></a>chemin :: radical

Retourne le `stem` composant de `myname` .

```cpp
path stem() const;
```

### <a name="remarks"></a>Notes

Retourne le `stem` composant de `myname` , `filename().native()` en particulier avec les `extension().native()` suppressions de fin. Le composant peut être vide.

## <a name="pathstring"></a><a name="string"></a>Path :: String

Convertit la séquence stockée dans `mypath` .

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Notes

La première fonction membre (de modèle) convertit la séquence stockée de `mypath` la même façon que :

1. `string()` pour `string<char, Traits, Alloc>()`

1. `wstring()` pour `string<wchar_t, Traits, Alloc>()`

1. `u16string()` pour `string<char16_t, Traits, Alloc>()`

1. `u32string()` pour `string<char32_t, Traits, Alloc>()`

La deuxième fonction membre convertit la séquence stockée dans en `mypath` l’encodage privilégié par le système hôte pour une **`char`** séquence et la retourne stockée dans un objet de type `string` .

## <a name="pathstring_type"></a><a name="string_type"></a>chemin :: string_type

Le type est un synonyme de `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>Path :: swap

Exécute `swap(mypath, right.mypath)` .

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>chemin :: u16string

Convertit la séquence stockée en `mypath` UTF-16 et la retourne stockée dans un objet de type `u16string` .

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>chemin :: u32string

Convertit la séquence stockée dans en `mypath` UTF-32 et la retourne stockée dans un objet de type `u32string` .

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>chemin :: u8string

Convertit la séquence stockée en `mypath` UTF-8 et la retourne stockée dans un objet de type `u8string` .

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>chemin :: value_type

Le type décrit les `path` éléments favorisés par le système d’exploitation hôte.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>chemin :: wstring

Convertit la séquence stockée dans en `mypath` l’encodage privilégié par le système hôte pour une **`wchar_t`** séquence et la retourne stockée dans un objet de type `wstring` .

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
