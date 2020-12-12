---
description: 'En savoir plus sur : objets de fonction dans la bibliothèque C++ standard'
title: Objets de fonction dans la bibliothèque C++ Standard
ms.date: 03/15/2019
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
ms.openlocfilehash: b87db43fbaabf1e9be18c56185ee190e3b2cbcac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324250"
---
# <a name="function-objects-in-the-c-standard-library"></a>Objets de fonction dans la bibliothèque C++ Standard

Un *objet de fonction*, ou *foncteur*, est n’importe quel type implémentant operator(). Cet opérateur est appelé *opérateur d’appel* ou parfois *opérateur d’application*. La bibliothèque C++ Standard utilise des objets de fonction essentiellement comme critère de tri pour les conteneurs et dans les algorithmes.

Les objets de fonctions offrent deux avantages par rapport à un appel de fonction direct. Le premier est qu’un objet de fonction peut contenir l’état. Le deuxième est qu’un objet fonction est aussi un type et peut donc être utilisé comme paramètre de modèle.

## <a name="creating-a-function-object"></a>Création d’un objet de fonction

Pour créer un objet de fonction, créez un type et implémentez operator(), par exemple :

```cpp
class Functor
{
public:
    int operator()(int a, int b)
    {
        return a < b;
    }
};

int main()
{
    Functor f;
    int a = 5;
    int b = 7;
    int ans = f(a, b);
}
```

La dernière ligne de la fonction `main` montre comment vous appelez l’objet de fonction. Cet appel ressemble à un appel à une fonction, mais il appelle en fait l’opérateur () du type functor. Cette similarité entre appeler un objet de fonction et la fonction, est comment le terme objet de fonction agit.

## <a name="function-objects-and-containers"></a>Objets de fonction et conteneurs

La bibliothèque C++ standard contient plusieurs objets de fonction dans le [\<functional>](../standard-library/functional.md) fichier d’en-tête. Une des utilisations de ces objets de fonction est de servir de critère de tri pour les conteneurs. Par exemple, le conteneur `set` est déclaré comme suit :

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

Le deuxième argument du modèle est l’objet de fonction `less`. Cet objet de fonction retourne **`true`** si le premier paramètre est inférieur au second paramètre. Comme certains conteneurs trient leurs éléments, le conteneur a besoin d’un moyen de comparer deux éléments. La comparaison est effectuée à l’aide de l’objet de fonction. Vous pouvez définir vos propres critères de tri pour les conteneurs en créant un objet de fonction et en le spécifiant dans la liste des modèles pour le conteneur.

## <a name="function-objects-and-algorithms"></a>Objets de fonction et algorithmes

Les objets de fonction sont également utilisés dans les algorithmes. Par exemple, l’algorithme `remove_if` est déclaré comme suit :

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

Le dernier argument de `remove_if` est un objet de fonction qui retourne une valeur booléenne (un *prédicat*). Si le résultat de l’objet de fonction est **`true`** , l’élément est supprimé du conteneur auquel accèdent les itérateurs `first` et `last` . Vous pouvez utiliser n’importe quel objet de fonction déclaré dans l' [\<functional>](../standard-library/functional.md) en-tête pour l’argument `pred` ou vous pouvez créer le vôtre.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
