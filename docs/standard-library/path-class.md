---
title: path, classe
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 10c865aa2bc2431850c69e9dfedbef37414b2cb9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455100"
---
# <a name="path-class"></a>path, classe

La classe **path** stocke un objet de `string_type`type, `myname` appelé ici pour les besoins de l’exposition, pouvant être utilisé comme un nom de chemin d’accès. `string_type`est un synonyme de `basic_string<value_type>`, où `value_type` est un synonyme de **wchar_t** sur Windows ou **char** sur POSIX.

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
|[iterator](#iterator)|Itérateur de constante bidirectionnel qui désigne les `path` composants de. `myname`|
|[string_type](#string_type)|Le type est un synonyme de `basic_string<value_type>`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[append](#append)|Ajoute la séquence spécifiée à `mypath`, convertie et insérant un preferred_separator en fonction des besoins.|
|[assign](#assign)|Remplace `mypath` par la séquence spécifiée, convertie en fonction des besoins.|
|[begin](#begin)|Retourne une `path::iterator` valeur désignant le premier élément de chemin d’accès dans le nom de chemin d’accès, le cas échéant.|
|[c_str](#c_str)|Retourne un pointeur vers le premier caractère de `mypath`.|
|[clear](#clear)|`mypath.clear()`Exécute.|
|[compare](#compare)|Retourne des valeurs de comparaison.|
|[concat](#compare)|Ajoute la séquence spécifiée à `mypath`, convertie (sans insertion d’un séparateur) selon les besoins.|
|[empty](#empty)|Retourne `mypath.empty()`.|
|[end](#end)|Retourne un itérateur de fin de séquence de type `iterator`.|
|[extension](#extension)|Retourne le suffixe `filename()`de.|
|[filename](#filename)|Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.|
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
|[is_absolute](#is_absolute)|Pour Windows, la fonction retourne `has_root_name() && has_root_directory()`. Pour POSIX, la fonction retourne `has_root_directory()`.|
|[is_relative](#is_relative)|Retourne `!is_absolute()`.|
|[make_preferred](#make_preferred)|Convertit chaque séparateur en preferred_separator en fonction des besoins.|
|[native](#native)|Retourne `myname`.|
|[parent_path](#parent_path)|Retourne le composant de chemin d' `myname`accès parent de.|
|[preferred_separator](#preferred_separator)|L’objet de constante donne le caractère préféré pour la séparation des composants du chemin, en fonction du système d’exploitation hôte. |
|[relative_path](#relative_path)|Retourne le composant de chemin d' `myname`accès relatif de. |
|[remove_filename](#remove_filename)|Supprime le nom de fichier.|
|[replace_extension](#replace_extension)|Remplace l’extension de `myname`. |
|[replace_filename](#replace_filename)|RReplaces le nom de fichier.|
|[root_directory](#root_directory)|Retourne le composant du répertoire racine `myname`de. |
|[root_name](#root_name)|Retourne le composant de nom racine `myname`de. |
|[root_path](#root_path)|Retourne le composant de chemin d' `myname`accès racine de.|
|[écoulement](#stem)|Retourne le `stem` composant de `myname`.|
|[string](#string)|Convertit la séquence stockée dans `mypath`.|
|[swap](#swap)|`swap(mypath, right.mypath)`Exécute.|
|[u16string](#u16string)|Convertit la séquence stockée en `mypath` UTF-16 et la retourne stockée dans un objet de type. `u16string`|
|[u32string](#u32string)|Convertit la séquence stockée dans `mypath` en UTF-32 et la retourne stockée dans un objet de type. `u32string`|
|[u8string](#u8string)|Convertit la séquence stockée en `mypath` UTF-8 et la retourne stockée dans un objet de type. `u8string`|
|[value_type](#value_type)|Le type décrit les éléments du chemin privilégiés par le système d’exploitation hôte.|
|[wstring](#wstring)|Convertit la séquence stockée dans `mypath` en l’encodage privilégié par le système hôte pour une `wchar_t` séquence et la retourne stockée dans un `wstring`objet de type.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#op_as)|Remplace les éléments du chemin d’accès par une copie d’un autre chemin d’accès.|
|[operator+=](#op_add)|Différentes `concat` expressions.|
|[operator/=](#op_divide)|Différentes `append` expressions.|
|[STRING_TYPE, opérateur](#op_string)|Retourne `myname`.|

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> de système de fichiers

**Espace de noms :** std::experimental::filesystem

## <a name="append"></a>chemin:: Append

Ajoute la séquence spécifiée à `mypath`, convertie et `preferred_separator` insérant si nécessaire.

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

## <a name="assign"></a> path::assign

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

## <a name="begin"></a>chemin:: début

Retourne une `path::iterator` valeur désignant le premier élément de chemin d’accès dans le nom de chemin d’accès, le cas échéant.

```cpp
iterator begin() const;
```

## <a name="c_str"></a>chemin:: c_str

Retourne un pointeur vers le premier caractère de `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>Path:: Clear

`mypath.clear()`Exécute.

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

### <a name="parameters"></a>Paramètres

*pval*\
Chemin d’accès à comparer.

*Str*\
Chaîne à comparer.

*effectués*\
Pointeur à comparer.

## <a name="concat"></a> path::concat

Ajoute la séquence spécifiée à `mypath`, convertie (sans insertion d’un séparateur) selon les besoins.

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

## <a name="const_iterator"></a> path::const_iterator

Synonyme de `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>chemin:: vide

Retourne `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>chemin:: fin

Retourne un itérateur de fin de séquence de type `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a>Path:: extension

Retourne le suffixe `filename()`de.

```cpp
path extension() const;
```

### <a name="remarks"></a>Notes

Retourne le suffixe `filename() X` de ce qui suit:

Si `X == path(".") || X == path("..")` ou si `X` ne contient pas de point, le suffixe est vide.

Dans le cas contraire, le suffixe commence par (et inclut) le point le plus à droite.

## <a name="filename"></a>chemin:: NomFichier

Retourne le composant du répertoire racine de myname, spécifiquement `empty() path() : *--end()`. Le composant peut être vide.

```cpp
path filename() const;
```

## <a name="generic_string"></a>chemin:: generic_string

Retourne `this->string<Elem, Traits, Alloc>(al)` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>chemin:: generic_u16string

Retourne `u16string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a>chemin:: generic_u32string

Retourne `u32string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a>chemin:: generic_u8string

Retourne `u8string()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>chemin:: generic_wstring

Retourne `wstring()` avec (sous Windows) les barres obliques inverses converties en barres obliques.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>chemin:: has_extension

Retourne `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a> path::has_filename

Retourne `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a> path::has_parent_path

Retourne `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a> path::has_relative_path

Retourne `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>chemin:: has_root_directory

Retourne `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>chemin:: has_root_name

Retourne `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a> path::has_root_path

Retourne `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>chemin:: has_stem

Retourne `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>chemin:: is_absolute

Pour Windows, la fonction retourne `has_root_name() && has_root_directory()`. Pour POSIX, la fonction retourne `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>chemin:: is_relative

Retourne `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>Path:: Iterator

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

La classe décrit un itérateur de constante bidirectionnel qui désigne les `path` composants de `myname` dans la séquence:

1. le nom de la racine, s’il est présent

1. le répertoire racine, s’il est présent

1. éléments de répertoire restants du `path`parent, le cas échéant, se terminant par le nom de fichier, s’il est présent

Pour `pval` un objet de type `path`:

1. `path::iterator X = pval.begin()`désigne le premier `path` élément dans le nom de chemin d’accès, le cas échéant.

1. `X == pval.end()`est true lorsque `X` pointe vers la fin de la séquence de composants.

3. `*X`retourne une chaîne qui correspond au composant actuel.

1. `++X` désigne le composant suivant dans la séquence, s'il est présent.

1. `--X` désigne le composant précédent dans la séquence, s'il est présent.

1. La modification invalide tous les itérateurs désignant les éléments `myname`dans. `myname`

## <a name="make_preferred"></a> path::make_preferred

Convertit chaque séparateur `preferred_separator` en, si nécessaire.

```cpp
path& make_preferred();
```

## <a name="native"></a> path::native

Retourne `myname`.

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

### <a name="parameters"></a>Paramètres

*Oui*\
[Chemin d’accès](../standard-library/path-class.md) copié dans le `path`.

*code*\
Chemin source.

### <a name="remarks"></a>Notes

Le premier opérateur membre copie `right.myname` vers `myname`. Le deuxième opérateur membre se `right.myname` déplace `myname`vers. Le troisième opérateur membre se comporte de la même façon `*this = path(source)`que.

## <a name="op_add"></a> path::operator+=

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
Ajouté `value_type` ou .`Elem`

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

## <a name="op_divide"></a> path::operator/=

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

## <a name="op_string"></a>Path:: Operator STRING_TYPE

Retourne `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a> path::parent_path

Retourne le composant de chemin d' `myname`accès parent de.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d' `myname`accès parent de, en `myname` particulier le `filename().native()` préfixe de après suppression et les séparateurs de répertoire précédents. (De même, `begin() != end()`si, il s’agit de la combinaison de tous les `[begin(), --end())` éléments de la plage `operator/=`en appliquant successivement.) Le composant peut être vide.

## <a name="path"></a> path::path

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

Les constructeurs sont tous construits `myname` de différentes manières:

C' `path()` est`myname()`le cas.

Pour `path(const path& right`), il `myname(right.myname)`s’agit de.

C' `path(path&& right)` est`myname(right.myname)`le cas.

C' `template<class Source> path(const Source& source)` est`myname(source)`le cas.

Pour `template<class Source> path(const Source& source, const locale& loc)` `loc`ce faire, vous obtenez toutes les facettes codecvt nécessaires à partir de. `myname(source)`

C' `template<class InIt> path(InIt first, InIt last)` est`myname(first, last)`le cas.

Pour `template<class InIt> path(InIt first, InIt last, const locale& loc)` `loc`ce faire, vous obtenez toutes les facettes codecvt nécessaires à partir de. `myname(first, last)`

## <a name="preferred_separator"></a> path::preferred_separator

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

## <a name="relative_path"></a> path::relative_path

Retourne le composant de chemin d' `myname`accès relatif de.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d' `myname`accès relatif de, spécifiquement `myname` le suffixe de après suppression `root_path().native()` et les séparateurs de répertoire redondants immédiatement ultérieurs. Le composant peut être vide.

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

### <a name="parameters"></a>Paramètres

*newext*\
Nouvelle extension.

### <a name="remarks"></a>Notes

Supprime d’abord le `extension().native()` suffixe de `myname`. Puis, `!newext.empty() && newext[0] != dot` si ( `dot` où `*path(".").c_str()`est), `dot` est ajouté à `myname`. Ensuite, *newext* est ajouté à `myname`.

## <a name="replace_filename"></a> path::replace_filename

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

## <a name="root_directory"></a> path::root_directory

Retourne le composant du répertoire racine `myname`de.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="root_name"></a> path::root_name

Retourne le composant de nom racine `myname`de.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Notes

Le composant peut être vide.

## <a name="root_path"></a> path::root_path

Retourne le composant de chemin d' `myname`accès racine de.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Notes

Retourne le composant de chemin d' `myname`accès racine `root_name()`de, en particulier  / . `root_directory` Le composant peut être vide.

## <a name="stem"></a>chemin:: radical

Retourne le `stem` composant de `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Notes

Retourne le `stem` composant de `myname`, en `filename().native()`particulieravec les suppressionsdefin.`extension().native()` Le composant peut être vide.

## <a name="string"></a>Path:: String

Convertit la séquence stockée dans `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Notes

La première fonction membre (de modèle) convertit la séquence `mypath` stockée de la même façon que:

1. `string()` pour `string<char, Traits, Alloc>()`

1. `wstring()` pour `string<wchar_t, Traits, Alloc>()`

1. `u16string()` pour `string<char16_t, Traits, Alloc>()`

1. `u32string()` pour `string<char32_t, Traits, Alloc>()`

La deuxième fonction membre convertit la séquence stockée dans `mypath` en l’encodage privilégié par le système hôte pour une séquence de **caractères** et la retourne stockée dans `string`un objet de type.

## <a name="string_type"></a> path::string_type

Le type est un synonyme de `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a> path::swap

`swap(mypath, right.mypath)`Exécute.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>chemin:: u16string

Convertit la séquence stockée en `mypath` UTF-16 et la retourne stockée dans un objet de type. `u16string`

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>chemin:: u32string

Convertit la séquence stockée dans `mypath` en UTF-32 et la retourne stockée dans un objet de type. `u32string`

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>chemin:: u8string

Convertit la séquence stockée en `mypath` UTF-8 et la retourne stockée dans un objet de type. `u8string`

```cpp
string u8string() const;
```

## <a name="value_type"></a> path::value_type

Le type décrit les `path` éléments favorisés par le système d’exploitation hôte.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a> path::wstring

Convertit la séquence stockée dans `mypath` en l’encodage privilégié par le système hôte pour une séquence **wchar_t** et la retourne stockée dans un `wstring`objet de type.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
