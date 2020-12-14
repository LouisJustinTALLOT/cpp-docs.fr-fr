---
description: 'En savoir plus sur : classe directory_iterator'
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
ms.openlocfilehash: 1bc0ac1d2d7816986bca1f48a41316270e547834
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232783"
---
# <a name="directory_iterator-class"></a>directory_iterator, classe

Décrit un itérateur d’entrée qui parcourt en séquence les noms de fichiers dans un répertoire. Pour un itérateur `X` , l’expression `*X` prend la valeur d’un objet de classe `directory_entry` qui encapsule le nom de fichier et tout ce qui est connu sur son état.

La classe stocke un objet de type `path` , appelé `mydir` ici pour les besoins de l’exposition, qui représente le nom du répertoire à séquencer et un objet de type `directory_entry` appelé `myentry` ici, qui représente le nom de fichier actuel dans la séquence de répertoires. Un objet construit par défaut de type `directory_entry` a un `mydir` nom de chemin d’accès vide et représente l’itérateur de fin de séquence.

Par exemple, étant donné le répertoire `abc` contenant les entrées `def` et `ghi` , le code :

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

appellera `visit` avec les arguments `path("abc/def")` et `path("abc/ghi")` .

Pour obtenir plus d’informations et des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[directory_iterator](#directory_iterator)|Construit un itérateur d’entrée qui parcourt les noms de fichiers dans un répertoire.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[increment](#increment)|Tente d’avancer jusqu’au nom de fichier suivant dans le répertoire.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur ! =](#op_neq)|Retourne `!(*this == right)`.|
|[opérateur =](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|
|[opérateur = =](#op_eq)|Retourne **`true`** uniquement si les **`*this`** itérateurs de fin de séquence et sont tous les deux, ou *s’ils* ne sont pas des itérateurs de fin de séquence.|
|[and](#op_star)|Retourne `myentry`.|
|[>Operator ](#op_cast)|Retourne `&**this`.|
|[opérateur + +](#op_increment)|Appelle, `increment()` retourne **`*this`** , ou effectue une copie de l’objet, appelle `increment()` , puis retourne la copie.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<experimental/filesystem>

**Espace de noms :** std::experimental::filesystem

## <a name="directory_iteratordirectory_iterator"></a><a name="directory_iterator"></a> directory_iterator ::d irectory_iterator

Le premier constructeur produit un itérateur de fin de séquence. Les deuxième et troisième constructeurs stockent *pval* dans `mydir` , puis essaient d’ouvrir et de lire `mydir` en tant que répertoire. En cas de réussite, ils stockent le premier nom de fichier dans le répertoire dans ; dans le `myentry` cas contraire, ils produisent un itérateur de fin de séquence.

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

## <a name="directory_iteratorincrement"></a><a name="increment"></a> directory_iterator :: incrément

La fonction tente d’accéder au nom de fichier suivant dans le répertoire. En cas de réussite, elle stocke ce nom de fichier dans `myentry` ; sinon, elle produit un itérateur de fin de séquence.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="directory_iteratoroperator"></a><a name="op_neq"></a> directory_iterator :: Operator ! =

L’opérateur membre retourne `!(*this == right)`.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_iterator](../standard-library/directory-iterator-class.md) comparée à `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_as"></a> directory_iterator :: Operator =

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_iterator](../standard-library/directory-iterator-class.md) copié dans le `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_eq"></a> directory_iterator :: Operator = =

L’opérateur membre retourne **`true`** uniquement si **`*this`** et à *droite* sont des itérateurs de fin de séquence ou si les deux ne sont pas des itérateurs de fin de séquence.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Directory_iterator](../standard-library/directory-iterator-class.md) comparée à `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_star"></a> directory_iterator :: Operator *

L’opérateur membre retourne `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="directory_iteratoroperator-"></a><a name="op_cast"></a> directory_iterator :: Operator->

La fonction membre retourne `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="directory_iteratoroperator"></a><a name="op_increment"></a> directory_iterator :: Operator + +

La première fonction membre appelle `increment()` , puis retourne **`*this`** . La deuxième fonction membre effectue une copie de l’objet, appelle `increment()` , puis retourne la copie.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Paramètres

*tiers*\
Nombre d’incréments.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)
