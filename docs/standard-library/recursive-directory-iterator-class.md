---
title: recursive_directory_iterator, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
dev_langs:
- C++
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3765f57ee299a70a54e3b69dbaee0e0687a64c
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691651"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator, classe

Décrit un itérateur d’entrée qui parcourt les noms de fichiers dans un répertoire, y compris dans les sous-répertoires de manière récursive. Pour un itérateur `X`, l’expression `*X` prend la valeur d’un objet de classe `directory_entry` qui encapsule le nom de fichier et tout élément connu sur son état.

Pour plus d’informations et pour obtenir des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Notes

La classe de modèle stocke ce qui suit :

1. un objet de type `stack<pair<directory_iterator, path>>`, appelée `mystack` ici pour à des fins de démonstration, qui représente l’imbrication des répertoires à séquencer

1. un objet de type `directory_entry` appelé `myentry` ici, qui représente le nom de fichier actuel dans la séquence de répertoires

1. un objet de type **bool**, appelée `no_push` ici, qui enregistre si dans les sous-répertoires est désactivé.

1. un objet de type `directory_options`, appelée `myoptions` ici, qui enregistre les options établies au moment de la construction

Un objet construit par défaut de type `recursive_directory_entry` a un itérateur de fin de séquence à `mystack.top().first` et représente l’itérateur de fin de séquence. Par exemple, étant donné le répertoire `abc` avec entrées `def` (répertoire), `def/ghi`, et `jkl`, le code :

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

appelle visit avec les arguments `path("abc/def/ghi")` et `path("abc/jkl")`. Vous pouvez qualifier le séquencement via une sous-arborescence de répertoires de deux manières :

1. Un lien symbolique directory est analysé uniquement si vous construisez un `recursive_directory_iterator` avec un `directory_options` argument dont la valeur est `directory_options::follow_directory_symlink`.

1. Si vous appelez `disable_recursion_pending` répertoire suivant rencontré durant l’incrémentation ne sera pas analysé de manière récursive.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Construit un objet `recursive_directory_iterator`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[profondeur](#depth)|Retourne `mystack.size() - 1`, de sorte que `pval` est à la profondeur zéro.|
|[disable_recursion_pending](#disable_recursion_pending)|Magasins **true** dans `no_push`.|
|[Incrément](#increment)|Avance au nom de fichier suivant dans la séquence.|
|[options](#options)|Retourne `myoptions`.|
|[pop](#pop)|Retourne l’objet suivant.|
|[recursion_pending](#recursion_pending)|Retourne `!no_push`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator!=](#op_neq)|Retourne `!(*this == right)`.|
|[operator=](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|
|[operator==](#op_eq)|Retourne **true** uniquement si les deux `*this` et *droit* sont des itérateurs de fin de séquence ou les deux ne sont pas fin-de-séquence-itérateurs.|
|[operator*](#op_multiply)|Retourne `myentry`.|
|[operator->](#op_cast)|Retourne `&**this`.|
|[operator++](#op_increment)|Incrémente le `recursive_directory_iterator`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<filesystem >

**Espace de noms :** std::tr2::sys

## <a name="depth"></a> recursive_directory_iterator::Depth

Retourne `mystack.size() - 1`, de sorte que `pval` est à la profondeur zéro.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a> recursive_directory_iterator::disable_recursion_pending

Magasins **true** dans `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a> recursive_directory_iterator::Increment

Avance au nom de fichier suivant dans la séquence.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Paramètres

*EC*<br/>
Code d’erreur spécifié.

### <a name="remarks"></a>Notes

La fonction tente d’accéder au nom de fichier suivant dans la séquence imbriquée. Si réussie, elle stocke ce nom de fichier dans `myentry`; sinon, il génère un itérateur de fin de séquence.

## <a name="op_neq"></a> recursive_directory_iterator::operator ! =

Retourne `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pour la comparaison.

## <a name="op_as"></a> recursive_directory_iterator::operator =

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Paramètres

*recursive_directory_iterator*<br/>
Le [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) copié dans le `recursive_directory_iterator`.

## <a name="op_eq"></a> recursive_directory_iterator::operator ==

Retourne **true** uniquement si les deux `*this` et *droit* sont des itérateurs de fin de séquence ou les deux ne sont pas fin-de-séquence-itérateurs.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) pour la comparaison.

## <a name="op_multiply"></a> recursive_directory_iterator::operator *

Retourne `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> recursive_directory_iterator::operator ->

Retourne `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> recursive_directory_iterator::operator ++

Incrémente le `recursive_directory_iterator`.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Paramètres

*int*<br/>
L’incrément spécifié.

### <a name="remarks"></a>Notes

La première fonction membre appelle `increment()`, puis retourne `*this`. La deuxième fonction membre effectue une copie de l’objet, les appels `increment()`, puis retourne la copie.

## <a name="options"></a> recursive_directory_iterator::options

Retourne `myoptions`.

```cpp
directory_options options() const;
```

## <a name="pop"></a> recursive_directory_iterator::POP

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

*PVal*<br/>
Chemin d'accès spécifié.

*error_code*<br/>
Le code d’erreur spécifié.

*OPTS*<br/>
Les options d’annuaire spécifié.

*recursive_directory_iterator*<br/>
`recursive_directory_iterator` dont le `recursive_directory_iterator` construit doit être une copie.

### <a name="remarks"></a>Notes

Le premier constructeur produit un itérateur de fin de séquence. Les deuxième et troisième constructeurs stockent **false** dans `no_push` et `directory_options::none` dans `myoptions`, puis essayez d’ouvrir et lire *pval* en tant que répertoire. Si la réussite, ils initialisent `mystack` et `myentry` pour désigner le premier nom de fichier non-directory dans la séquence imbriquée ; sinon, ils produisent un itérateur de fin de séquence.

Les quatrième et cinquième constructeurs comportent comme les deuxième et troisième, sauf qu’ils stockent tout d’abord *opts* dans `myoptions`. Les constructeurs par défaut se comporte comme prévu.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)<br/>
