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
ms.openlocfilehash: c1b68aefd44d8f0ac60c36307dee93333d801bb9
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342985"
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
|[directory_entry](#directory_entry)|Les constructeurs par défaut se comportent comme prévu. Le quatrième constructeur initialise `mypath` à *pval*, `mystat` à *stat_arg*, et `mysymstat` à *symstat_arg*.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[assign](#assign)|La fonction membre assigne *pval* à `mypath`, *stat* à `mystat`, et *symstat* à `mysymstat`.|
|[path](#path)|La fonction membre retourne `mypath`.|
|[replace_filename](#replace_filename)|La fonction membre remplace `mypath` avec `mypath.parent_path()`  /  *pval*, `mystat` avec *stat_arg*, et `mysymstat` avec *symstat_arg*|
|[status](#status)|Les deux fonctions membres retournent `mystat` éventuellement modifié.|
|[symlink_status](#symlink_status)|Les deux fonctions membres retournent `mysymstat` éventuellement modifié.|

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
|[opérateur const path_type &](#path_type)|Retourne `mypath`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<expérimentale/filesystem&gt;

**Espace de noms :** std::experimental::filesystem

## <a name="assign"></a> assign

La fonction membre assigne *pval* à `mypath`, *stat_arg* à `mystat`, et *symstat_arg* à `mysymstat`.

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Paramètres

*pval*<br/>
Le chemin d’accès de nom de fichier stocké.

*stat_arg*<br/>
État du nom de fichier stocké.

*symstat_arg*<br/>
L’état du lien symbolique du nom de fichier stocké.

## <a name="directory_entry"></a> directory_entry

Les constructeurs par défaut se comportent comme prévu. Le quatrième constructeur initialise `mypath` à *pval*, `mystat` à *stat_arg*, et `mysymstat` à *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Paramètres

*pval*<br/>
Le chemin d’accès de nom de fichier stocké.

*stat_arg*<br/>
État du nom de fichier stocké.

*symstat_arg*<br/>
L’état du lien symbolique du nom de fichier stocké.

## <a name="op_neq"></a> operator!=

La fonction membre retourne `!(*this == right)`.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_entry](../standard-library/directory-entry-class.md) qui est comparée à la `directory_entry`.

## <a name="op_as"></a> operator=

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_entry](../standard-library/directory-entry-class.md) copié dans le `directory_entry`.

## <a name="op_eq"></a> operator==

La fonction membre retourne `mypath == right.mypath`.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_entry](../standard-library/directory-entry-class.md) qui est comparée à la `directory_entry`.

## <a name="op_lt"></a>, opérateur&lt;

La fonction membre retourne `mypath < right.mypath`.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_entry](../standard-library/directory-entry-class.md) qui est comparée à la `directory_entry`.

## <a name="op_lteq"></a> Opérateur&lt;=

La fonction membre retourne `!(right < *this)`.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_entry](../standard-library/directory-entry-class.md) qui est comparée à la `directory_entry`.

## <a name="op_gt"></a>, opérateur&gt;

La fonction membre retourne `right < *this`.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_entry](../standard-library/directory-entry-class.md) qui est comparée à la `directory_entry`.

## <a name="op_gteq"></a> Opérateur&gt;=

La fonction membre retourne `!(*this < right)`.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_entry](../standard-library/directory-entry-class.md) qui est comparée à la `directory_entry`.

## <a name="path_type"></a> opérateur const path_type &

L’opérateur membre retourne `mypath`.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a> Chemin d’accès

La fonction membre retourne `mypath`.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a> replace_filename

La fonction membre remplace `mypath` avec `mypath.parent_path()`  /  *pval*, `mystat` avec *stat_arg*, et `mysymstat` avec *symstat_arg*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Paramètres

*pval*<br/>
Le chemin d’accès de nom de fichier stocké.

*stat_arg*<br/>
État du nom de fichier stocké.

*symstat_arg*<br/>
L’état du lien symbolique du nom de fichier stocké.

## <a name="status"></a> État

Les deux fonctions membres retournent `mystat` éventuellement modifié comme suit :

1. Si `status_known(mystat)` , ne rien faire.

1. Sinon, si `!status_known(mysymstat) && !is_symlink(mysymstat)` puis `mystat = mysymstat`.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Paramètres

*ec*<br/>
Le code d’erreur état.

## <a name="symlink_status"></a> symlink_status

Les deux fonctions membres retournent `mysymstat` éventuellement modifié comme suit : Si `status_known(mysymstat)` , ne rien faire. Sinon, `mysymstat = symlink_status(mypval)`.

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Paramètres

*ec*<br/>
Le code d’erreur état.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem&gt;](../standard-library/filesystem.md)<br/>
