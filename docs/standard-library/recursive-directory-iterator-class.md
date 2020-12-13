---
description: 'En savoir plus sur : classe recursive_directory_iterator'
title: recursive_directory_iterator, classe
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: b9b5909c62a745233362eeac1adb879c1585098c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337897"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator, classe

Décrit un itérateur d’entrée qui parcourt les noms de fichiers dans un répertoire, éventuellement décroissant dans les sous-répertoires de manière récursive. Pour un itérateur `X` , l’expression `*X` prend la valeur d’un objet de classe `directory_entry` qui encapsule le nom de fichier et tout ce qui est connu sur son état.

Pour obtenir plus d’informations et des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Notes

Le modèle de classe stocke :

1. objet de type `stack<pair<directory_iterator, path>>` , appelé `mystack` ici pour les besoins de l’exposition, qui représente l’imbrication des répertoires à séquencer.

1. objet de type `directory_entry` appelé `myentry` ici, qui représente le nom de fichier actuel dans la séquence de répertoires.

1. objet de type **`bool`** , appelé `no_push` ici, qui enregistre si la descente récursive dans les sous-répertoires est désactivée

1. objet de type `directory_options` , appelé `myoptions` ici, qui enregistre les options établies au moment de la construction

Un objet construit par défaut de type `recursive_directory_entry` a un itérateur de fin de séquence à `mystack.top().first` et représente l’itérateur de fin de séquence. Par exemple, étant donné le répertoire `abc` avec des entrées `def` (répertoire), `def/ghi` et `jkl` , le code :

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

appellera Visit avec les arguments `path("abc/def/ghi")` et `path("abc/jkl")` . Vous pouvez qualifier le séquencement via une sous-arborescence de répertoires de deux façons :

1. Un symlink de répertoire est analysé uniquement si vous construisez un `recursive_directory_iterator` avec un `directory_options` argument dont la valeur est `directory_options::follow_directory_symlink` .

1. Si vous appelez `disable_recursion_pending` , un répertoire suivant rencontré lors d’un incrément ne sera pas analysé de manière récursive.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Construit un objet `recursive_directory_iterator`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[profondeur](#depth)|Retourne `mystack.size() - 1` , donc `pval` à la profondeur zéro.|
|[disable_recursion_pending](#disable_recursion_pending)|Stocke **`true`** dans `no_push` .|
|[increment](#increment)|Passe au nom de fichier suivant dans l’ordre.|
|[options](#options)|Retourne `myoptions`.|
|[roulant](#pop)|Retourne l’objet suivant.|
|[recursion_pending](#recursion_pending)|Retourne `!no_push`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur ! =](#op_neq)|Retourne `!(*this == right)`.|
|[opérateur =](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|
|[opérateur = =](#op_eq)|Retourne **`true`** uniquement si les **`*this`** itérateurs de fin de séquence et sont tous les deux, ou *s’ils* ne sont pas des itérateurs de fin de séquence.|
|[and](#op_multiply)|Retourne `myentry`.|
|[>Operator ](#op_cast)|Retourne `&**this`.|
|[opérateur + +](#op_increment)|Incrémente `recursive_directory_iterator` .|

## <a name="requirements"></a>Spécifications

**En-tête :**\<filesystem>

**Espace de noms :** std::tr2::sys

## <a name="recursive_directory_iteratordepth"></a><a name="depth"></a> recursive_directory_iterator ::d epth

Retourne `mystack.size() - 1` , donc `pval` à la profondeur zéro.

```cpp
int depth() const;
```

## <a name="recursive_directory_iteratordisable_recursion_pending"></a><a name="disable_recursion_pending"></a> recursive_directory_iterator ::d isable_recursion_pending

Stocke **`true`** dans `no_push` .

```cpp
void disable_recursion_pending();
```

## <a name="recursive_directory_iteratorincrement"></a><a name="increment"></a> recursive_directory_iterator :: incrément

Passe au nom de fichier suivant dans l’ordre.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Paramètres

*EC*\
Code d’erreur spécifié.

### <a name="remarks"></a>Notes

La fonction tente d’accéder au nom de fichier suivant dans la séquence imbriquée. En cas de réussite, elle stocke ce nom de fichier dans `myentry` ; sinon, elle produit un itérateur de fin de séquence.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_neq"></a> recursive_directory_iterator :: Operator ! =

Retourne `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pour la comparaison.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_as"></a> recursive_directory_iterator :: Operator =

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*recursive_directory_iterator*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) copié dans le `recursive_directory_iterator` .

## <a name="recursive_directory_iteratoroperator"></a><a name="op_eq"></a> recursive_directory_iterator :: Operator = =

Retourne **`true`** uniquement si les **`*this`** itérateurs de fin de séquence et sont tous les deux, ou *s’ils* ne sont pas des itérateurs de fin de séquence.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pour la comparaison.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_multiply"></a> recursive_directory_iterator :: Operator *

Retourne `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="recursive_directory_iteratoroperator-"></a><a name="op_cast"></a> recursive_directory_iterator :: Operator->

Retourne `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="recursive_directory_iteratoroperator"></a><a name="op_increment"></a> recursive_directory_iterator :: Operator + +

Incrémente `recursive_directory_iterator` .

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Paramètres

*tiers*\
Incrément spécifié.

### <a name="remarks"></a>Notes

La première fonction membre appelle `increment()` , puis retourne **`*this`** . La deuxième fonction membre effectue une copie de l’objet, appelle `increment()` , puis retourne la copie.

## <a name="recursive_directory_iteratoroptions"></a><a name="options"></a> recursive_directory_iterator :: options

Retourne `myoptions`.

```cpp
directory_options options() const;
```

## <a name="recursive_directory_iteratorpop"></a><a name="pop"></a> recursive_directory_iterator ::p op

Retourne l’objet suivant.

```cpp
void pop();
```

### <a name="remarks"></a>Notes

Si `depth() == 0` l’objet devient un itérateur de fin de séquence. Sinon, la fonction membre met fin à l’analyse du répertoire actif (le plus profond), et reprend au prochain niveau de profondeur.

## <a name="recursive_directory_iteratorrecursion_pending"></a><a name="recursion_pending"></a> recursive_directory_iterator :: recursion_pending

Retourne `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iteratorrecursive_directory_iterator"></a><a name="recursive_directory_iterator"></a> recursive_directory_iterator :: recursive_directory_iterator

Construit un objet `recursive_directory_iterator`.

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*pval*\
Chemin d'accès spécifié.

*error_code*\
Code d’erreur spécifié.

*décide*\
Options de répertoire spécifiées.

*recursive_directory_iterator*\
`recursive_directory_iterator` dont le `recursive_directory_iterator` construit doit être une copie.

### <a name="remarks"></a>Notes

Le premier constructeur produit un itérateur de fin de séquence. Les deuxième et troisième constructeurs stockent **`false`** dans `no_push` et `directory_options::none` dans `myoptions` , puis tentent d’ouvrir et de lire *pval* en tant que répertoire. En cas de réussite, ils initialisent `mystack` et `myentry` désignent le premier nom de fichier non-répertoire dans la séquence imbriquée ; sinon, ils produisent un itérateur de fin de séquence.

Les quatrième et cinquième constructeurs se comportent de la même façon que le deuxième et le troisième, à ceci près qu’ils sont en premier *lieu dans le* magasin `myoptions` . Les constructeurs par défaut se comporte comme prévu.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)
