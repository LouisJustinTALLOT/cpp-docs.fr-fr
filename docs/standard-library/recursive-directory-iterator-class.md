---
title: recursive_directory_iterator, classe
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 98eaf2494a3bc17c0f9d11683fc67fed433ba3a5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451707"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator, classe

Décrit un itérateur d’entrée qui parcourt les noms de fichiers dans un répertoire, éventuellement décroissant dans les sous-répertoires de manière récursive. Pour un itérateur `X`, l’expression `*X` prend la valeur d’un objet de `directory_entry` classe qui encapsule le nom de fichier et tout ce qui est connu sur son état.

Pour plus d’informations et pour obtenir des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Notes

La classe de modèle stocke ce qui suit :

1. objet de type `stack<pair<directory_iterator, path>>`, appelé `mystack` ici pour les besoins de l’exposition, qui représente l’imbrication des répertoires à séquencer.

1. objet de type `directory_entry` appelé `myentry` ici, qui représente le nom de fichier actuel dans la séquence de répertoires.

1. objet de type **bool**, appelé `no_push` ici, qui enregistre si la descente récursive dans les sous-répertoires est désactivée.

1. objet de type `directory_options`, appelé `myoptions` ici, qui enregistre les options établies au moment de la construction

Un objet construit par défaut de `recursive_directory_entry` type a un itérateur de fin de séquence à `mystack.top().first` et représente l’itérateur de fin de séquence. Par exemple, étant donné le `abc` répertoire avec `def` des entrées (répertoire) `def/ghi`, et `jkl`, le code:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

appellera Visit avec les arguments `path("abc/def/ghi")` et. `path("abc/jkl")` Vous pouvez qualifier le séquencement via une sous-arborescence de répertoires de deux façons:

1. Un symlink de répertoire est analysé uniquement si vous construisez un `recursive_directory_iterator` avec un `directory_options` argument dont la valeur `directory_options::follow_directory_symlink`est.

1. Si vous appelez `disable_recursion_pending` , un répertoire suivant rencontré lors d’un incrément ne sera pas analysé de manière récursive.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Construit un objet `recursive_directory_iterator`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[depth](#depth)|Retourne `mystack.size() - 1`, donc `pval` à la profondeur zéro.|
|[disable_recursion_pending](#disable_recursion_pending)|Stocke la `no_push` **valeur true** dans.|
|[lier](#increment)|Passe au nom de fichier suivant dans l’ordre.|
|[options](#options)|Retourne `myoptions`.|
|[pop](#pop)|Retourne l’objet suivant.|
|[recursion_pending](#recursion_pending)|Retourne `!no_push`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[!=, opérateur](#op_neq)|Retourne `!(*this == right)`.|
|[operator=](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|
|[operator==](#op_eq)|Retourne la **valeur true** uniquement `*this` si les itérateurs de fin de *séquence et les* deux ne sont pas des itérateurs de fin de séquence.|
|[operator*](#op_multiply)|Retourne `myentry`.|
|[operator->](#op_cast)|Retourne `&**this`.|
|[operator++](#op_increment)|Incrémente `recursive_directory_iterator`.|

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> de système de fichiers

**Espace de noms :** std::tr2::sys

## <a name="depth"></a>recursive_directory_iterator::d epth

Retourne `mystack.size() - 1`, donc `pval` à la profondeur zéro.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

Stocke la `no_push` **valeur true** dans.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator:: incrément

Passe au nom de fichier suivant dans l’ordre.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Paramètres

*EC*\
Code d’erreur spécifié.

### <a name="remarks"></a>Notes

La fonction tente d’accéder au nom de fichier suivant dans la séquence imbriquée. En cas de réussite, elle stocke `myentry`ce nom de fichier dans; sinon, elle produit un itérateur de fin de séquence.

## <a name="op_neq"></a> recursive_directory_iterator::operator!=

Retourne `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pour la comparaison.

## <a name="op_as"></a> recursive_directory_iterator::operator=

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*recursive_directory_iterator*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) copié dans le `recursive_directory_iterator`.

## <a name="op_eq"></a> recursive_directory_iterator::operator==

Retourne la **valeur true** uniquement `*this` si les itérateurs de fin de *séquence et les* deux ne sont pas des itérateurs de fin de séquence.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pour la comparaison.

## <a name="op_multiply"></a>recursive_directory_iterator:: Operator *

Retourne `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> recursive_directory_iterator::operator->

Retourne `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>recursive_directory_iterator:: Operator + +

Incrémente `recursive_directory_iterator`.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Paramètres

*tiers*\
Incrément spécifié.

### <a name="remarks"></a>Notes

La première fonction membre appelle `increment()`, puis retourne `*this`. La deuxième fonction membre effectue une copie de l’objet, appelle `increment()`, puis retourne la copie.

## <a name="options"></a>recursive_directory_iterator:: options

Retourne `myoptions`.

```cpp
directory_options options() const;
```

## <a name="pop"></a>recursive_directory_iterator::p op

Retourne l’objet suivant.

```cpp
void pop();
```

### <a name="remarks"></a>Notes

Si `depth() == 0` l’objet devient un itérateur de fin de séquence. Sinon, la fonction membre met fin à l’analyse du répertoire actif (le plus profond), et reprend au prochain niveau de profondeur.

## <a name="recursion_pending"></a> recursive_directory_iterator::recursion_pending

Retourne `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a> recursive_directory_iterator::recursive_directory_iterator

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

*Code_erreur*\
Code d’erreur spécifié.

*décide*\
Options de répertoire spécifiées.

*recursive_directory_iterator*\
`recursive_directory_iterator` dont le `recursive_directory_iterator` construit doit être une copie.

### <a name="remarks"></a>Notes

Le premier constructeur produit un itérateur de fin de séquence. Les deuxième et troisième constructeurs stockent  false `no_push` dans `directory_options::none` et `myoptions`dans, puis tentent d’ouvrir et de lire *pval* en tant que répertoire. En cas de réussite, ils `mystack` initialisent et `myentry` désignent le premier nom de fichier non-répertoire dans la séquence imbriquée; sinon, ils produisent un itérateur de fin de séquence.

Les quatrième et cinquième constructeurs se comportent de la même façon que le deuxième et le troisième, à ceci `myoptions`près qu’ils sont en premier *lieu dans le* magasin. Les constructeurs par défaut se comporte comme prévu.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)
