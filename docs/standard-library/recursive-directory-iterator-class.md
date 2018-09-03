---
title: recursive_directory_iterator, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: cd876ec21379d59445b88bdc08a1c7b831cb94fa
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33954032"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator, classe

décrit un itérateur d’entrée qui permet de séquencer les noms de fichiers dans un répertoire, y compris dans les sous-répertoires, de façon récursive. Pour un itérateur X, l’expression *X correspond à un objet de la classe directory_entry, qui inclut dans un wrapper le nom de fichier et tout ce qui est connu sur son état.

Pour obtenir plus d’informations et des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Notes

La classe de modèle stocke ce qui suit :

1. un objet de type stack<pair\<directory_iterator, path>>, appelé ici mystack pour les besoins de la démonstration, qui représente l’imbrication des répertoires à séquencer ;

1. un objet de type directory_entry appelé ici myentry, qui représente le nom de fichier actuel dans la séquence de répertoires ;

1. un objet de type bool, appelé ici no_push, qui enregistre si la récursivité est désactivée dans les sous-répertoires ;

1. un objet de type directory_options, appelé ici myoptions, qui enregistre les options établies au moment de la construction ;

Un objet construit par défaut de type recursive_directory_entry a un itérateur de fin de séquence à mystack.top().first, et représente l’itérateur de fin de séquence. Si nous prenons l’exemple du répertoire abc avec les entrées def (répertoire), def/ghi et jkl, le code suivant :

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

appelle visit avec les arguments `path("abc/def/ghi") and path("abc/jkl").`Vous pouvez qualifier le séquencement via une sous-arborescence de répertoires de deux manières :

1. Un lien symbolique (symlink) de répertoire est analysé uniquement si vous construisez recursive_directory_iterator avec un argument directory_options dont la valeur est directory_options::follow_directory_symlink.

1. Si vous appelez disable_recursion_pending, le répertoire suivant rencontré durant l’incrémentation n’est pas analysé de manière récursive.

## <a name="recursivedirectoryiteratordepth"></a>recursive_directory_iterator::depth

```cpp
int depth() const;
```

Retourne mystack.size() - 1. Ainsi, pval est à la profondeur zéro.

## <a name="recursivedirectoryiteratordisablerecursionpending"></a>recursive_directory_iterator::disable_recursion_pending

```cpp
void disable_recursion_pending();
```

La fonction membre stocke la valeur true dans no_push.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator!=

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

L’opérateur membre retourne !(*this == right).

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator=

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

Les opérateurs d’assignation de membre par défaut se comportent comme prévu.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator==

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

L’opérateur membre retourne la valeur true seulement si *this et right sont des itérateurs de fin de séquence, ou si tous les deux ne sont pas des itérateurs de fin de séquence.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator*

```cpp
const directory_entry& operator*() const;
```

L’opérateur membre retourne myentry.

## <a name="recursivedirectoryiteratoroperator-"></a>recursive_directory_iterator::operator->

```cpp
const directory_entry * operator->() const;
```

Retourne &**this.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator++

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

La première fonction membre appelle increment(), puis retourne *this. La deuxième fonction membre effectue une copie de l’objet, appelle increment(), puis retourne la copie.

## <a name="recursivedirectoryiteratoroptions"></a>recursive_directory_iterator::options

```cpp
directory_options options() const;
```

Retourne myoptions.

## <a name="recursivedirectoryiteratorpop"></a>recursive_directory_iterator::pop

```cpp
void pop();
```

Si depth() == 0, l’objet devient un itérateur de fin de séquence. Sinon, la fonction membre met fin à l’analyse du répertoire actif (le plus profond), et reprend au prochain niveau de profondeur.

## <a name="recursivedirectoryiteratorrecursionpending"></a>recursive_directory_iterator::recursion_pending

```cpp
bool recursion_pending() const;
```

Retourne !no_push.

## <a name="recursivedirectoryiteratorrecursivedirectoryiterator"></a>recursive_directory_iterator::recursive_directory_iterator

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

Le premier constructeur produit un itérateur de fin de séquence. Les deuxième et troisième constructeurs stockent false dans no_push et directory_options::none dans myoptions, puis essaient d’ouvrir et de lire pval en tant que répertoire. En cas de réussite, ils initialisent mystack et myentry pour désigner le premier nom de fichier dans la séquence imbriquée. Sinon, ils produisent un itérateur de fin de séquence.

Les quatrième et cinquième constructeurs se comportent comme le deuxième et le troisième, à ceci près qu’ils stockent tout d’abord opts dans myoptions. Les constructeurs par défaut se comportent comme prévu.

## <a name="recursivedirectoryiteratorincrement"></a>recursive_directory_iterator::increment

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

La fonction tente d’accéder au nom de fichier suivant dans la séquence imbriquée. En cas de réussite, elle stocke ce nom de fichier dans myentry ; dans le cas contraire, elle génère un itérateur de fin de séquence.

## <a name="requirements"></a>Spécifications

**En-tête :** \<filesystem >

**Espace de noms :** std::tr2::sys

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)<br/>
