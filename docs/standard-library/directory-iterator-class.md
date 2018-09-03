---
title: directory_iterator, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
dev_langs:
- C++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.workload:
- cplusplus
ms.openlocfilehash: b46e4d8fc7b59f8b4919a7e36a85f29f626aa80b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845828"
---
# <a name="directoryiterator-class"></a>directory_iterator, classe

Décrit un itérateur d’entrée qui parcourt en séquence les noms de fichiers dans un répertoire. Pour un itérateur X, l’expression *X correspond à un objet de la classe directory_entry qui inclut dans un wrapper le nom de fichier et tout ce qui est connu sur son état.

La classe stocke un objet de type chemin, appelé ici mydir, qui représente le nom du répertoire à parcourir en séquence, et un objet de type directory_entry appelé myentry, qui représente le nom de fichier actuel dans la séquence du répertoire. Un objet construit par défaut de type directory_entry a un nom de chemin mydir vide et représente l’itérateur de fin de séquence.

Par exemple, étant donné le répertoire abc avec les entrées def et ghi, le code :

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

appelle visit avec les arguments path("abc/def") et path("abc/ghi").

Pour plus d’informations et pour obtenir des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_iterator;
```

## <a name="directoryiteratordirectoryiterator"></a>directory_iterator::directory_iterator

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

Le premier constructeur produit un itérateur de fin de séquence. Les deuxième et troisième constructeurs stockent pval dans mydir, puis tentent d’ouvrir et lire mydir en tant que répertoire. En cas de réussite, ils stockent le premier nom de fichier du répertoire dans myentry ; dans le cas contraire, ils produisent un itérateur de fin de séquence.

Les constructeurs par défaut se comporte comme prévu.

## <a name="directoryiteratorincrement"></a>directory_iterator::increment

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

La fonction tente d’accéder au nom de fichier suivant dans le répertoire. En cas de réussite, elle stocke ce nom de fichier dans myentry ; dans le cas contraire, elle génère un itérateur de fin de séquence.

## <a name="directoryiteratoroperator"></a>directory_iterator::operator!=

```cpp
bool operator!=(const directory_iterator& right) const;
```

L’opérateur membre retourne !(*this == right).

## <a name="directoryiteratoroperator"></a>directory_iterator::operator=

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

## <a name="directoryiteratoroperator"></a>directory_iterator::operator==

```cpp
bool operator==(const directory_iterator& right) const;
```

L’opérateur membre retourne true seulement si *this et right sont des itérateurs de fin de séquence ou si les deux ne sont pas des itérateurs de fin de séquence.

## <a name="directoryiteratoroperator"></a>directory_iterator::operator*

```cpp
const directory_entry& operator*() const;
```

L’opérateur membre retourne myentry.

## <a name="directoryiteratoroperator-"></a>directory_iterator::operator->

```cpp
const directory_entry * operator->() const;
```

La fonction membre retourne &**this.

## <a name="directoryiteratoroperator"></a>directory_iterator::operator++

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

La première fonction membre appelle increment(), puis retourne *this. La deuxième fonction membre effectue une copie de l’objet, appelle increment(), puis retourne la copie.

## <a name="requirements"></a>Spécifications

**En-tête :** \<experimental/filesystem>

**Espace de noms :** std::experimental::filesystem

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)<br/>
