---
title: Algorithmes
ms.date: 10/18/2018
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
ms.openlocfilehash: d363dc3f06222121ac5efc79b30516ebd55ff539
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456487"
---
# <a name="algorithms"></a>Algorithmes

Les algorithmes sont un élément fondamental de la bibliothèque C++ Standard. Ils ne fonctionnent pas avec des conteneurs proprement dits, mais plutôt avec des itérateurs. Par conséquent, le même algorithme peut être utilisé par la plupart des conteneurs de la bibliothèque C++ Standard (voire tous). Cette section traite des conventions et de la terminologie des algorithmes de la bibliothèque C++ Standard.

## <a name="remarks"></a>Notes

Les descriptions des fonctions de modèle d'algorithme emploient plusieurs expressions raccourcies :

- L’expression «dans la plage \[ *A*, *B*)» correspond à la séquence de zéro, une ou plusieurs valeurs discrètes commençant par *un* allant jusqu’à *b*non compris. Une plage est valide uniquement si *B* est accessible à partir de *.* vous pouvez stocker *un* dans un objet *n* (*n* = *a*), incrémenter l’objet zéro ou plusieurs fois (+ +*N*) et faire en sorte que l’objet soit égal à *B* après un nombre fini d’incréments (*N* == *B*).

- L’expression «chaque *N* dans la plage \[ *A*, *B*)» signifie que *N* commence par la valeur *a* et est incrémenté zéro, une ou plusieurs fois jusqu’à ce qu’il soit égal à la valeur *B*. Le cas *N* == *B* n’est pas dans la plage.

- L’expression «la plus petite valeur *de N* dans la \[plage *a*, *B*) telle *que x*» signifie que la condition *x* est déterminée pour chaque *N* dans la \[plage *a*, *b*) jusqu’à ce que le la condition *X* est remplie.

- L’expression «la valeur la plus élevée de *N* dans \[la plage *a*, *b*) telle que *x* signifie que *x* est déterminé pour chaque *N* dans \[la plage *a*, *b*). La fonction stocke dans *K* une copie de *N* chaque fois que la condition *X* est remplie. Si un tel magasin se produit, la fonction remplace la valeur finale de *N*, qui est égale à *B*, par la valeur de *K*. Pour un itérateur bidirectionnel ou d’accès aléatoire, toutefois, cela peut également signifier que *N* commence par la plus grande valeur de la plage et est décrémenté sur la plage jusqu’à ce que la condition *X* soit remplie.

- Les expressions comme *X* - *Y*, où *X* et *Y* peuvent être des itérateurs autres que des itérateurs d’accès aléatoire, doivent être interprétées au sens mathématique. La fonction n’évalue pas nécessairement **-** l’opérateur s’il doit déterminer une telle valeur. Cela vaut également pour les expressions comme *X* + *N* et *X* - *N*, où *N* est un type entier.

Plusieurs algorithmes utilisent un prédicat qui effectue une comparaison par paire, par exemple avec `operator==`, pour générer un résultat **bool** . La fonction de prédicat `operator==`, ou tout remplacement, ne doit pas modifier l'un de ses opérandes. Elle doit générer le même résultat **bool** chaque fois qu’elle est évaluée et doit générer le même résultat si une copie de l’un des opérandes est substituée à l’opérande.

Plusieurs algorithmes utilisent un prédicat qui doit imposer un classement faible strict sur des paires d’éléments d’une séquence. Pour le prédicat *prédit*(*X*, *Y*):

- Strict signifie que *prédit*(*x*, *x*) a la valeur false.

- Faible signifie que *X* et *Y* ont un ordre équivalent si \! *prédit*(*x*, *y*) & & \! *prédit*(*y*, *x*) (*x* == *y* ne doit être défini).

- Le classement signifie que *prédit*(*x*, *Y*) & & *prédit*(*Y*, *z*) implique *prédit*(*x*, *z*).

Certains de ces algorithmes utilisent implicitement le prédicat *X* \< *Y*. Les autres prédicats qui répondent en général à l’exigence de classement faible stricte sont *X* > *Y*, `less`(*x*, *y*) et `greater`(*x*, *y*). Notez cependant que des prédicats comme *X* \<= *Y* et *X* >= *Y* ne répondent pas à cet impératif.

Une séquence d’éléments désignée par des itérateurs dans la \[plage *First*, *Last*) est une séquence triée **<** par opérateur si, pour chaque *N* dans \[la plage 0, la *dernière* - *première* ) et pour chaque *M* dans la plage (*N*, *Last* - *First*) \!du prédicat\*((*First* + *M*) < \*(First + *N*)) a la valeur true. (Notez que les éléments sont triés par ordre croissant). La fonction de prédicat `operator<`, ou tout remplacement, ne doit pas modifier l'un de ses opérandes. Elle doit générer le même résultat **bool** chaque fois qu’elle est évaluée et doit générer le même résultat si une copie de l’un des opérandes est substituée à l’opérande. En outre, elle doit imposer un classement faible strict sur les opérandes qu’elle compare.

Une séquence d’éléments désignée par des itérateurs dans la \[plage `Last` `First`,) est un tas ordonné `operator<` par si, pour chaque *N* dans la \[plage 1, le *dernier* - *prénom*, le \!Predicate (\*_First_ *(First*N)) a la valeur true. +  < \* (Le premier élément est le plus grand.) Sa structure interne est également connue uniquement des fonctions de modèle [make_heap](../standard-library/algorithm-functions.md#make_heap), [pop_heap](../standard-library/algorithm-functions.md#pop_heap)et [push_heap](../standard-library/algorithm-functions.md#push_heap). Comme avec une séquence ordonnée, la fonction `operator<`de prédicat, ou tout remplacement, ne doit pas modifier l’un de ses opérandes et elle doit imposer un classement faible strict sur les opérandes qu’elle compare. Elle doit générer le même résultat **bool** chaque fois qu’elle est évaluée et doit générer le même résultat si une copie de l’un des opérandes est substituée à l’opérande.

Les algorithmes de la bibliothèque C++ Standard se trouvent dans les fichiers d’en-tête [\<algorithm>](../standard-library/algorithm.md) et [\<numeric>](../standard-library/numeric.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
