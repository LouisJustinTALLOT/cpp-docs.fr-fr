---
title: directory_entry, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 9a55109683a18415638cacd9cd15dbcaa3164fc8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846930"
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

## <a name="assign"></a>assign

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

La fonction membre assigne pval à mypath, stat à mystat et symstat à mysymstat.

## <a name="directoryentry"></a>directory_entry

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

Les constructeurs par défaut se comportent comme prévu. Le quatrième constructeur initialise mypath avec pval, mystat avec stat_arg, et mysymstat avec symstat_arg.

## <a name="operator"></a>!=, opérateur

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

La fonction membre retourne !(*this == right).

## <a name="operator"></a>opérateur =

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

## <a name="operator"></a>operator==

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

La fonction membre retourne mypath == right.mypath.

## <a name="operatorlt"></a>(opérateur)&lt;

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

La fonction membre retourne mypath &lt; right.mypath.

## <a name="operatorlt"></a>operator&lt;=

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

La fonction membre retourne !(right \< *this).

## <a name="operatorgt"></a>(opérateur)&gt;

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

La fonction membre retourne right \< *this.

## <a name="operatorgt"></a>operator&gt;=

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

La fonction membre retourne ! (* cela \< droite).

## <a name="operator-const-pathtype"></a>const path_type&, opérateur

```cpp
operator const std::experimental::filesystem::path&() const;
```

L’opérateur membre retourne mypath.

## <a name="path"></a>path

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

La fonction membre retourne mypath.

## <a name="replacefilename"></a>replace_filename

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

La fonction membre remplace mypath par mypath.parent_path() / pval, mystat par stat_arg, et mysymstat par symstat_arg

## <a name="status"></a>statut

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

Les deux fonctions membres retournent mystat éventuellement modifié au préalable comme suit :

1. Si status_known(mystat), ne rien faire.

1. Sinon, si !status_known(mysymstat) && !is_symlink(mysymstat), mystat = mysymstat.

## <a name="symlinkstatus"></a>symlink_status

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

Les deux fonctions membres retournent mysymstat éventuellement modifié au préalable comme suit : si status_known(mysymstat), ne rien faire. Sinon, mysymstat = symlink_status(mypval).

## <a name="requirements"></a>Spécifications

**En-tête :** \<expérimentale/système de fichiers&gt;

**Espace de noms :** std::experimental::filesystem

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem&gt;](../standard-library/filesystem.md)<br/>
