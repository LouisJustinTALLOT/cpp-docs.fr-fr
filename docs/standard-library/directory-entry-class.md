---
description: 'En savoir plus sur : classe directory_entry'
title: directory_entry, classe
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.openlocfilehash: a4a4b69e9f568c19eefae79554838fac5781f3f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324546"
---
# <a name="directory_entry-class"></a>directory_entry, classe

Décrit un objet qui est retourné par `*X`, où *X* est un [directory_iterator](../standard-library/directory-iterator-class.md) ou un [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_entry;
```

## <a name="remarks"></a>Notes

La classe stocke un objet de type [path](../standard-library/path-class.md). Le `path` stocké peut être une instance de la [classe path](../standard-library/path-class.md) ou d’un type dérivé de `path`. Elle stocke également deux valeurs [file_type](../standard-library/filesystem-enumerations.md#file_type) ; une qui représente ce qui est connu de l’état du nom du fichier stocké et une autre qui représente ce qui est connu de l’état du lien symbolique du nom de fichier.

Pour obtenir plus d’informations et des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[directory_entry](#directory_entry)|Les constructeurs par défaut se comportent comme prévu. Le quatrième constructeur initialise `mypath` à *pval*, `mystat` à *stat_arg* et `mysymstat` à *symstat_arg*.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[assign](#assign)|La fonction membre affecte *pval* à `mypath` , *Stat* à `mystat` et *symstat* à `mysymstat` .|
|[path](#path)|La fonction membre retourne `mypath`.|
|[replace_filename](#replace_filename)|La fonction membre remplace `mypath` par `mypath.parent_path()`  /  *pval*, `mystat` avec *stat_arg* et `mysymstat` avec *symstat_arg*|
|[statut](#status)|Les deux fonctions membres retournent `mystat` éventuellement la première modification.|
|[symlink_status](#symlink_status)|Les deux fonctions membres retournent `mysymstat` éventuellement la première modification.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur ! =](#op_neq)|Remplace les éléments de la liste par une copie d'une autre liste.|
|[opérateur =](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|
|[opérateur = =](#op_eq)|Retourne `mypath == right.mypath`.|
|[<d’opérateur ](#op_lt)|Retourne `mypath < right.mypath`.|
|[<opérateur =](#op_lteq)|Retourne `!(right < *this)`.|
|[>d’opérateur ](#op_gt)|Retourne `right < *this`.|
|[>opérateur =](#op_gteq)|Retourne `!(*this < right)`.|
|[path_type const, opérateur&](#path_type)|Retourne `mypath`.|

## <a name="requirements"></a>Spécifications

**En-tête :** \< expérimental/système de fichiers&gt;

**Espace de noms :** std::experimental::filesystem

## <a name="assign"></a><a name="assign"></a> assignés

La fonction membre affecte *pval* à `mypath` , *stat_arg* à `mystat` et *symstat_arg* à `mysymstat` .

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Paramètres

*pval*\
Chemin d’accès au nom de fichier stocké.

*stat_arg*\
État du nom de fichier stocké.

*symstat_arg*\
État du lien symbolique du nom de fichier stocké.

## <a name="directory_entry"></a><a name="directory_entry"></a> directory_entry

Les constructeurs par défaut se comportent comme prévu. Le quatrième constructeur initialise `mypath` à *pval*, `mystat` à *stat_arg* et `mysymstat` à *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Paramètres

*pval*\
Chemin d’accès au nom de fichier stocké.

*stat_arg*\
État du nom de fichier stocké.

*symstat_arg*\
État du lien symbolique du nom de fichier stocké.

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

La fonction membre retourne `!(*this == right)`.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparée à `directory_entry` .

## <a name="operator"></a><a name="op_as"></a> opérateur =

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) copié dans le `directory_entry` .

## <a name="operator"></a><a name="op_eq"></a> opérateur = =

La fonction membre retourne `mypath == right.mypath`.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparée à `directory_entry` .

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

La fonction membre retourne `mypath < right.mypath`.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparée à `directory_entry` .

## <a name="operatorlt"></a><a name="op_lteq"></a> and&lt;=

La fonction membre retourne `!(right < *this)`.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparée à `directory_entry` .

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

La fonction membre retourne `right < *this`.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparée à `directory_entry` .

## <a name="operatorgt"></a><a name="op_gteq"></a> and&gt;=

La fonction membre retourne `!(*this < right)`.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparée à `directory_entry` .

## <a name="operator-const-path_type"></a><a name="path_type"></a> path_type const, opérateur&

L’opérateur membre retourne `mypath`.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a><a name="path"></a> d

La fonction membre retourne `mypath`.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a><a name="replace_filename"></a> replace_filename

La fonction membre remplace `mypath` par `mypath.parent_path()`  /  *pval*, `mystat` avec *stat_arg* et `mysymstat` avec *symstat_arg*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Paramètres

*pval*\
Chemin d’accès au nom de fichier stocké.

*stat_arg*\
État du nom de fichier stocké.

*symstat_arg*\
État du lien symbolique du nom de fichier stocké.

## <a name="status"></a><a name="status"></a> statu

Les deux fonctions membres retournent `mystat` éventuellement la première modification comme suit :

1. Si `status_known(mystat)` ce n’est pas le cas,

1. Sinon, si ce n’est pas le cas `!status_known(mysymstat) && !is_symlink(mysymstat)` `mystat = mysymstat` .

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Paramètres

*EC*\
Code d’erreur de l’État.

## <a name="symlink_status"></a><a name="symlink_status"></a> symlink_status

Les deux fonctions membres retournent `mysymstat` éventuellement la première modification comme suit : Si vous `status_known(mysymstat)` ne faites rien. Sinon, `mysymstat = symlink_status(mypval)`.

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Paramètres

*EC*\
Code d’erreur de l’État.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<FileSystem&gt;](../standard-library/filesystem.md)
