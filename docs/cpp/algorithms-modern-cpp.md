---
title: Algorithmes (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
ms.openlocfilehash: b972e575c982ae2523ec560a6237eac76ceaf834
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220151"
---
# <a name="algorithms-modern-c"></a>Algorithmes (Modern C++)

Pour la programmation C++ moderne, nous vous recommandons d’utiliser les algorithmes dans le [bibliothèque Standard C++](../standard-library/cpp-standard-library-reference.md). Voici quelques exemples importants :

- **for_each**, qui est l’algorithme de traversée par défaut. (Également **transformer** pour la sémantique de déplacement non.)

- **find_if**, qui est l’algorithme de recherche par défaut.

- **tri**, **lower_bound**, ainsi que les autres tri et recherche des algorithmes.

Pour écrire un comparateur, utilisez strict **<** et utiliser *expressions lambda nommés* lorsque vous le pouvez.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="loops"></a>Boucles

Si possible, utilisez basé sur une plage **pour** boucles ou des appels d’algorithme ou les deux, au lieu de boucles écrites à la main. **copie**, **transformer**, **count_if**, **remove_if**, et d’autres, comme les sont préférables aux boucles manuscrites car leur intention est évident et ils rendent plus faciles à écrire du code exempte de bogues. En outre, de nombreux algorithmes de bibliothèque C++ Standard ont des optimisations d’implémentation qui les rendent plus efficace.

À la place de l’ancien C++ comme suit :

```cpp
for ( auto i = strings.begin(); i != strings.end(); ++i ) {
    /* ... */
}

auto i = v.begin();

for ( ; i != v.end(); ++i ) {
    if (*i > x && *i < y) break;
}
```

Utilisez le C++ moderne comme suit :

```cpp
for_each( begin(strings), end(strings), [](string& s) {
  // ...
} );

auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );
```

### <a name="range-based-for-loops"></a>Plage de boucles for basées

Basées sur la plage **pour** boucle est une fonctionnalité de 11 langage C ++, pas un algorithme de la bibliothèque C++ Standard. Mais il mérite d’être mentionné dans cette discussion sur les boucles. Basé sur une plage **pour** boucles sont une extension de la **pour** mot clé et fournissent un moyen pratique et efficace pour tracer des boucles qui itèrent sur une plage de valeurs. Conteneurs de bibliothèque C++ Standard, les chaînes et les tableaux sont prêtes à l’emploi pour basé sur une plage **pour** boucles. Pour activer cette nouvelle syntaxe d’itération pour votre type défini par l’utilisateur, ajoutez la prise en charge suivant :

- Un `begin` méthode qui retourne un itérateur au début de la structure et un `end` méthode qui retourne un itérateur à la fin de la structure.

- Prise en charge dans l’itérateur des méthodes suivantes : **opérateur**<strong>\*</strong>, **opérateur ! =**, et **operator ++** (version préfixée).

Ces méthodes peuvent être des membres ou des fonctions autonomes.

## <a name="random-numbers"></a>Nombres aléatoires

Il n’existe aucun secret que l’ancien CRT `rand()` fonction présente de nombreux défauts, qui ont été abordés en détail dans la Communauté C++. En C++ moderne, vous n’êtes pas obligé de gérer ces problèmes, ni d’inventer votre propre générateur de nombres aléatoires distribué de manière uniforme, car les outils pour créer rapidement et facilement les sont disponibles dans la bibliothèque C++ Standard, comme indiqué dans [ \<aléatoire >](../standard-library/random.md).

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++ (C++ moderne)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
