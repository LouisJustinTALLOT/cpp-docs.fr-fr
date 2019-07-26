---
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
ms.openlocfilehash: 35b0dc55bf5db2f799d9ade28cd5968ceab3332b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458957"
---
# <a name="directoryentry-class"></a>directory_entry, classe

Décrit un objet qui est retourné par `*X`, où *X* est un [directory_iterator](../standard-library/directory-iterator-class.md) ou un [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_entry;
```

## <a name="remarks"></a>Notes

La classe stocke un objet de type [path](../standard-library/path-class.md). Le `path` stocké peut être une instance de la [classe path](../standard-library/path-class.md) ou d’un type dérivé de `path`. Elle stocke également deux valeurs [file_type](../standard-library/filesystem-enumerations.md#file_type) ; une qui représente ce qui est connu de l’état du nom du fichier stocké et une autre qui représente ce qui est connu de l’état du lien symbolique du nom de fichier.

Pour plus d’informations et pour obtenir des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[directory_entry](#directory_entry)|Les constructeurs par défaut se comportent comme prévu. Le quatrième `mypath` constructeur initialise la valeur *pval*, `mystat` *stat_arg*et `mysymstat` *symstat_arg*.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[assign](#assign)|La fonction membre affecte *pval* à `mypath`, *Stat* à `mystat`et *symstat* à `mysymstat`.|
|[path](#path)|La fonction membre retourne `mypath`.|
|[replace_filename](#replace_filename)|La fonction membre remplace `mypath` par `mypath.parent_path()`  /  *pval* ,`mystat` avec *stat_arg* et`mysymstat` *symstat_arg*|
|[status](#status)|Les deux fonctions membres `mystat` retournent éventuellement la première modification.|
|[symlink_status](#symlink_status)|Les deux fonctions membres `mysymstat` retournent éventuellement la première modification.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[!=, opérateur](#op_neq)|Remplace les éléments de la liste par une copie d'une autre liste.|
|[operator=](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|
|[operator==](#op_eq)|Retourne `mypath == right.mypath`.|
|[operator<](#op_lt)|Retourne `mypath < right.mypath`.|
|[operator<=](#op_lteq)|Retourne `!(right < *this)`.|
|[operator>](#op_gt)|Retourne `right < *this`.|
|[operator>=](#op_gteq)|Retourne `!(*this < right)`.|
|[& Const, opérateur path_type](#path_type)|Retourne `mypath`.|

## <a name="requirements"></a>Configuration requise

**En-tête:** \<expérimental/système de fichiers&gt;

**Espace de noms :** std::experimental::filesystem

## <a name="assign"></a>assignés

La fonction membre affecte *pval* à `mypath`, *stat_arg* à `mystat`et *symstat_arg* à `mysymstat`.

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

## <a name="directory_entry"></a>directory_entry

Les constructeurs par défaut se comportent comme prévu. Le quatrième `mypath` constructeur initialise la valeur *pval*, `mystat` *stat_arg*et `mysymstat` *symstat_arg*.

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

## <a name="op_neq"></a>opérateur! =

La fonction membre retourne `!(*this == right)`.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparé à `directory_entry`.

## <a name="op_as"></a>opérateur =

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) copié dans le `directory_entry`.

## <a name="op_eq"></a> operator==

La fonction membre retourne `mypath == right.mypath`.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparé à `directory_entry`.

## <a name="op_lt"></a>, opérateur&lt;

La fonction membre retourne `mypath < right.mypath`.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparé à `directory_entry`.

## <a name="op_lteq"></a>and&lt;=

La fonction membre retourne `!(right < *this)`.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparé à `directory_entry`.

## <a name="op_gt"></a>, opérateur&gt;

La fonction membre retourne `right < *this`.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparé à `directory_entry`.

## <a name="op_gteq"></a>and&gt;=

La fonction membre retourne `!(*this < right)`.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_entry](../standard-library/directory-entry-class.md) comparé à `directory_entry`.

## <a name="path_type"></a>& Const, opérateur path_type

L’opérateur membre retourne `mypath`.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a>d

La fonction membre retourne `mypath`.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a>replace_filename

La fonction membre remplace `mypath` par `mypath.parent_path()`  /  *pval* ,`mystat` avec *stat_arg* et`mysymstat` *symstat_arg*

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

## <a name="status"></a>statu

Les deux fonctions membres `mystat` retournent éventuellement la première modification comme suit:

1. Si `status_known(mystat)` ce n’est pas le cas,

1. Sinon, si `!status_known(mysymstat) && !is_symlink(mysymstat)` ce `mystat = mysymstat`n’est pas le cas.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Paramètres

*EC*\
Code d’erreur de l’État.

## <a name="symlink_status"></a>symlink_status

Les deux fonctions membres `mysymstat` retournent éventuellement la première modification comme suit: Si `status_known(mysymstat)` ce n’est pas le cas, Sinon, `mysymstat = symlink_status(mypval)`.

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Paramètres

*EC*\
Code d’erreur de l’État.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem&gt;](../standard-library/filesystem.md)
