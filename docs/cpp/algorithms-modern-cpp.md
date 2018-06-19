---
title: Algorithmes (Modern C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdd5742bb86992ce20f5a52f587c8557d46a97eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412294"
---
# <a name="algorithms-modern-c"></a>Algorithmes (Modern C++)
Pour la programmation C++ moderne, nous vous recommandons d’utiliser les algorithmes dans le [bibliothèque Standard C++](../standard-library/cpp-standard-library-reference.md). Voici quelques exemples importants :  
  
-   `for_each`, qui est l’algorithme de parcours par défaut. (Également `transform` pour la sémantique de déplacement n’est pas.)  
  
-   `find_if`, qui est l’algorithme de recherche par défaut.  
  
-   `sort`, `lower_bound`, ainsi que les autres trier et parcourir des algorithmes.  
  
 Pour écrire un comparateur, utilisez strict `<` et utiliser *nommé lambdas* lorsque vous le pouvez.  
  
```cpp  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
```  
  
## <a name="loops"></a>Boucles  
 Si possible, utilisez basée sur une plage `for` boucles ou des appels de l’algorithme ou à la fois, au lieu de boucles écrit manuellement.`copy`, `transform`, `count_if`, `remove_if`, et d’autres, comme les sont préférables aux boucles manuscrites, car leur intention n’est évidente et elles rendent plus faciles à écrire du code sans aucun bogue. En outre, de nombreux algorithmes de bibliothèque Standard C++ ont des optimisations de mise en œuvre qui les rendent plus efficace.  
  
 À la place des anciens C++ comme suit :  
  
```cpp  
for ( auto i = strings.begin(); i != strings.end(); ++i ) {  
   /* ... */  
}  
  
auto i = v.begin();  
  
for ( ; i != v.end(); ++i ) {  
  if (*i > x && *i < y) break;  
}  
```  
  
 Utilisez le C++ moderne, comme suit :  
  
```cpp  
for_each( begin(strings), end(strings), [](string& s) {  
   // ...  
} );  
  
auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );  
```  
  
### <a name="range-based-for-loops"></a>En fonction de plage pour les boucles  
 Basée sur la plage `for` boucle est une fonctionnalité de 11 langage C ++, pas un algorithme de la bibliothèque C++ Standard. Mais qu’ils méritent une mention dans cette discussion sur les boucles. Basée sur une plage `for` boucles sont une extension de la `for` (mot clé) et offrent un moyen pratique et plus efficace pour écrire des boucles itérer sur une plage de valeurs. Conteneurs de bibliothèque C++ Standard, les chaînes et les tableaux sont prêts à l’emploi pour basée sur une plage `for` boucles. Pour activer cette nouvelle syntaxe d’itération pour votre type défini par l’utilisateur, ajoutez la prise en charge suivante :  
  
-   A `begin` méthode qui retourne un itérateur au début de la structure et un `end` méthode qui retourne un itérateur à la fin de la structure.  
  
-   Prise en charge dans l’itérateur de ces méthodes : `operator*`, `operator!=`, et `operator++` (version de préfixe).  
  
 Ces méthodes peuvent être des membres ou des fonctions autonomes.  
  
## <a name="random-numbers"></a>Nombres aléatoires  
 Il n’est un secret qui le CRT ancien `rand()` fonction a de nombreuses failles, qui ont été présentées en détail dans la Communauté C++. En C++ moderne, vous n’êtes pas obligé de gérer ces défauts, ni d’inventer votre propre générateur de nombres aléatoires distribué de manière uniforme, car les outils permettant de rapidement et facilement les créer sont disponibles dans la bibliothèque C++ Standard, comme indiqué dans [ \<aléatoire >](../standard-library/random.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)