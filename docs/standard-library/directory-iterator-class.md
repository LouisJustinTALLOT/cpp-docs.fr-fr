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
ms.openlocfilehash: 8c6dcce3de32c7e25d2489cb508454dff500a1a6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454428"
---
# <a name="directoryiterator-class"></a>directory_iterator, classe

Décrit un itérateur d’entrée qui parcourt en séquence les noms de fichiers dans un répertoire. Pour un itérateur `X`, l’expression `*X` prend la valeur d’un objet de `directory_entry` classe qui encapsule le nom de fichier et tout ce qui est connu sur son état.

La classe stocke un objet de `path`type, `mydir` appelé ici pour les besoins de l’exposition, qui représente le nom du répertoire à séquencer et un objet de type `directory_entry` appelé `myentry` ici, qui représente le actuel. nom de fichier dans la séquence de répertoires. Un objet construit par défaut de `directory_entry` type a un `mydir` nom de chemin d’accès vide et représente l’itérateur de fin de séquence.

Par exemple, étant donné le `abc` répertoire contenant `def` les `ghi`entrées et, le code:

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
|[lier](#increment)|Tente d’avancer jusqu’au nom de fichier suivant dans le répertoire.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[!=, opérateur](#op_neq)|Retourne `!(*this == right)`.|
|[operator=](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|
|[operator==](#op_eq)|Retourne la **valeur true** uniquement `*this` si les itérateurs de fin de *séquence et les* deux ne sont pas des itérateurs de fin de séquence.|
|[operator*](#op_star)|Retourne `myentry`.|
|[operator->](#op_cast)|Retourne `&**this`.|
|[operator++](#op_increment)|Appelle `increment()`, retourne `*this`, ou effectue une copie de l’objet, appelle `increment()`, puis retourne la copie.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<experimental/filesystem>

**Espace de noms :** std::experimental::filesystem

## <a name="directory_iterator"></a>directory_iterator::d irectory_iterator

Le premier constructeur produit un itérateur de fin de séquence. Les deuxième et troisième constructeurs stockent *pval* dans `mydir`, puis essaient d’ouvrir et de `mydir` lire en tant que répertoire. En cas de réussite, ils stockent le premier nom de `myentry`fichier dans le répertoire dans; dans le cas contraire, ils produisent un itérateur de fin de séquence.

Les constructeurs par défaut se comporte comme prévu.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*pval*\
Chemin d’accès au nom de fichier stocké.

*EC*\
Code d’erreur de l’État.

*directory_iterator*\
Objet stocké.

## <a name="increment"></a>directory_iterator:: incrément

La fonction tente d’accéder au nom de fichier suivant dans le répertoire. En cas de réussite, elle stocke `myentry`ce nom de fichier dans; sinon, elle produit un itérateur de fin de séquence.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a> directory_iterator::operator!=

L’opérateur membre retourne `!(*this == right)`.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_iterator](../standard-library/directory-iterator-class.md) comparé à `directory_iterator`.

## <a name="op_as"></a> directory_iterator::operator=

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_iterator](../standard-library/directory-iterator-class.md) copié dans le `directory_iterator`.

## <a name="op_eq"></a> directory_iterator::operator==

L’opérateur membre retourne **true** uniquement si les `*this` itérateurs de fin de séquence et *droits* sont tous les deux des itérateurs de fin de séquence ou si les deux ne sont pas des itérateurs de fin de séquence.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_iterator](../standard-library/directory-iterator-class.md) comparé à `directory_iterator`.

## <a name="op_star"></a>directory_iterator:: Operator *

L’opérateur membre retourne `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> directory_iterator::operator->

La fonction membre retourne `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>directory_iterator:: Operator + +

La première fonction membre appelle `increment()`, puis retourne `*this`. La deuxième fonction membre effectue une copie de l’objet, appelle `increment()`, puis retourne la copie.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Paramètres

*tiers*\
Nombre d’incréments.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)
