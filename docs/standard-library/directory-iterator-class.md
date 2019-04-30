---
title: directory_iterator, classe
ms.date: 09/10/2018
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
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
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
ms.openlocfilehash: 6763f2a96b771fadbec311cf8740352fff53e29a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413844"
---
# <a name="directoryiterator-class"></a>directory_iterator, classe

Décrit un itérateur d’entrée qui parcourt en séquence les noms de fichiers dans un répertoire. Pour un itérateur `X`, l’expression `*X` prend la valeur d’un objet de classe `directory_entry` qui encapsule le nom de fichier et tout élément connu sur son état.

La classe stocke un objet de type `path`, appelé `mydir` ici aux fins de démonstration, qui représente le nom du répertoire à séquencer, et un objet de type `directory_entry` appelé `myentry` ici, qui représente l’actuel nom de fichier dans la séquence de répertoires. Un objet construit par défaut de type `directory_entry` a vide `mydir` chemin d’accès et représente l’itérateur de fin de séquence.

Par exemple, étant donné le répertoire `abc` avec entrées `def` et `ghi`, le code :

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

appellera `visit` avec les arguments `path("abc/def")` et `path("abc/ghi")`.

Pour plus d’informations et pour obtenir des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[directory_iterator](#directory_iterator)|Construit un itérateur d’entrée qui parcourt les noms de fichiers dans un répertoire.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[increment](#increment)|Tente d’accéder au nom de fichier suivant dans le répertoire.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[!=, opérateur](#op_neq)|Retourne `!(*this == right)`.|
|[operator=](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|
|[operator==](#op_eq)|Retourne **true** uniquement si les deux `*this` et *droit* sont des itérateurs de fin de séquence ou les deux ne sont pas fin-de-séquence-itérateurs.|
|[operator*](#op_star)|Retourne `myentry`.|
|[operator->](#op_cast)|Retourne `&**this`.|
|[operator++](#op_increment)|Appels `increment()`, puis retourne `*this`, ou une copie de l’objet, les appels `increment()`, puis retourne la copie.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<experimental/filesystem>

**Espace de noms :** std::experimental::filesystem

## <a name="directory_iterator"></a> directory_iterator::directory_iterator

Le premier constructeur produit un itérateur de fin de séquence. Les deuxième et troisième constructeurs stockent *pval* dans `mydir`, puis essayez d’ouvrir et lire `mydir` en tant que répertoire. Si réussite, ils stockent le premier nom de fichier dans le répertoire dans `myentry`; sinon, ils produisent un itérateur de fin de séquence.

Les constructeurs par défaut se comporte comme prévu.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*pval*<br/>
Le chemin d’accès de nom de fichier stocké.

*ec*<br/>
Le code d’erreur état.

*directory_iterator*<br/>
L’objet stocké.

## <a name="increment"></a> directory_iterator::increment

La fonction tente d’accéder au nom de fichier suivant dans le répertoire. Si réussie, elle stocke ce nom de fichier dans `myentry`; sinon, il génère un itérateur de fin de séquence.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a> directory_iterator::operator!=

L’opérateur membre retourne `!(*this == right)`.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_iterator](../standard-library/directory-iterator-class.md) qui est comparée à la `directory_iterator`.

## <a name="op_as"></a> directory_iterator::operator=

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_iterator](../standard-library/directory-iterator-class.md) copié dans le `directory_iterator`.

## <a name="op_eq"></a> directory_iterator::operator==

L’opérateur membre retourne **true** uniquement si les deux `*this` et *droit* sont des itérateurs de fin de séquence ou les deux ne sont pas fin-de-séquence-itérateurs.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [directory_iterator](../standard-library/directory-iterator-class.md) qui est comparée à la `directory_iterator`.

## <a name="op_star"></a> directory_iterator::operator*

L’opérateur membre retourne `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> directory_iterator::operator->

La fonction membre retourne `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> directory_iterator::operator++

La première fonction membre appelle `increment()`, puis retourne `*this`. La deuxième fonction membre effectue une copie de l’objet, les appels `increment()`, puis retourne la copie.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Paramètres

*int*<br/>
Le nombre d’incréments.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)<br/>
