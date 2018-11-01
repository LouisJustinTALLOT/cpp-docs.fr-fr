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
ms.openlocfilehash: a0a1165d731e44568d530e3ed919d73e2a3e8e5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648026"
---
# <a name="algorithms"></a>Algorithmes

Les algorithmes sont un élément fondamental de la bibliothèque C++ Standard. Ils ne fonctionnent pas avec des conteneurs proprement dits, mais plutôt avec des itérateurs. Par conséquent, le même algorithme peut être utilisé par la plupart des conteneurs de la bibliothèque C++ Standard (voire tous). Cette section traite des conventions et de la terminologie des algorithmes de la bibliothèque C++ Standard.

## <a name="remarks"></a>Notes

Les descriptions des fonctions de modèle d'algorithme emploient plusieurs expressions raccourcies :

- L’expression « dans la plage \[ *A*, *B*) » désigne une séquence de zéro ou plusieurs valeurs discrètes commençant par *A* sans inclure *B* . Une plage est valide uniquement si *B* est accessible à partir de *A ;* vous pouvez stocker *A* dans un objet *N* (*N*  =  *A*), incrémenter l’objet zéro ou plusieurs fois (++*N*), et que l’objet de comparaison égal à *B* après un nombre fini d’incréments (*N*   ==  *B*).

- L’expression « chaque *N* dans la plage \[ *A*, *B*) » signifie que *N* commence par la valeur *un*et est incrémenté zéro ou plusieurs fois jusqu'à ce qu’elle est égale à la valeur *B*. Le cas *N* == *B* n’est pas dans la plage.

- La phrase « la valeur minimale de *N* dans la plage \[ *A*, *B*) telles que *X*» signifie que la condition *X* est déterminée pour chaque *N* dans la plage \[ *A*, *B*) jusqu'à ce que la condition *X*est remplie.

- La phrase « la valeur la plus élevée de *N* dans la plage \[ *A*, *B*) telles que *X* signifie que *X* est déterminée pour chaque *N* dans la plage \[ *A*, *B*). La fonction stocke dans *K* une copie de *N* chaque fois que la condition *X* est remplie. Si ce stockage se produit, la fonction remplace la valeur finale de *N*, qui est égale à *B*, avec la valeur de *K*. Pour un itérateur bidirectionnel ou d’accès aléatoire, toutefois, cela peut également signifier que *N* commence par la plus grande valeur de la plage et est décrémenté sur la plage jusqu’à ce que la condition *X* soit remplie.

- Les expressions comme *X* - *Y*, où *X* et *Y* peuvent être des itérateurs autres que des itérateurs d’accès aléatoire, doivent être interprétées au sens mathématique. La fonction n’évalue pas nécessairement opérateur **-** si elle doit déterminer une telle valeur. Cela vaut également pour les expressions comme *X* + *N* et *X* - *N*, où *N* est un type entier.

Plusieurs algorithmes utilisent un prédicat qui effectue une comparaison par paire, comme avec `operator==`, pour générer un **bool** résultat. La fonction de prédicat `operator==`, ou tout remplacement, ne doit pas modifier l'un de ses opérandes. Il doit générer le même **bool** résultat chaque fois qu’elle est évaluée, et il doit avoir le même résultat si une copie de des opérandes est remplacée par l’opérande.

Plusieurs algorithmes utilisent un prédicat qui doit imposer un classement faible strict sur des paires d’éléments d’une séquence. Pour le prédicat *pred*(*X*, *Y*) :

- Strict signifie que *pred*(*X*, *X*) a la valeur false.

- Faible signifie que *X* et *Y* ont un ordre équivalent si \! *pred*(*X*, *Y*) & & \! *pred*(*Y*, *X*) (*X* == *Y*ne doivent pas être définis).

- Classement signifie que *pred*(*X*, *Y*) & & *pred*(*Y*, *Z*) implique *pred*(*X*, *Z*).

Certains de ces algorithmes utilisent implicitement le prédicat *X* \< *Y*. Sont d’autres prédicats qui répondent en général à l’exigence d’ordre faible strict *X* > *Y*, `less`(*X*, *Y*), et `greater`(*X*, *Y*). Notez cependant que des prédicats comme *X* \<= *Y* et *X* >= *Y* ne répondent pas à cet impératif.

Une séquence d’éléments désignée par des itérateurs dans la plage \[ *première*, *dernière*) est une séquence ordonnée par l’opérateur **<** if, pour chaque  *N* dans la plage \[0, *dernière* - *première*) et pour chaque *M* dans la plage (*N*, *Dernière* - *première*) le prédicat \!(\*(*première*  +  *M*) < \*(*première* + *N*)) a la valeur true. (Notez que les éléments sont triés par ordre croissant). La fonction de prédicat `operator<`, ou tout remplacement, ne doit pas modifier l'un de ses opérandes. Il doit générer le même **bool** résultat chaque fois qu’elle est évaluée, et il doit avoir le même résultat si une copie de des opérandes est remplacée par l’opérande. En outre, elle doit imposer un classement faible strict sur les opérandes qu’elle compare.

Une séquence d’éléments désignée par des itérateurs dans la plage \[ `First`, `Last`) est un tas ordonné par `operator<` si, pour chaque *N* dans la plage \[1, *dernière*  -  *Première*) le prédicat \!(\*_première_ < \*(*première*  +  *N*)) a la valeur true. (Le premier élément est le plus grand.) Sa structure interne est également connue uniquement pour les fonctions de modèle [make_heap](../standard-library/algorithm-functions.md#make_heap), [pop_heap](../standard-library/algorithm-functions.md#pop_heap), et [push_heap](../standard-library/algorithm-functions.md#push_heap). Comme avec une séquence ordonnée, la fonction de prédicat `operator<`, ou tout remplacement, ne doit pas modifier un de ses opérandes et elle doit imposer un ordre faible strict sur les opérandes qu’elle compare. Il doit générer le même **bool** résultat chaque fois qu’elle est évaluée, et il doit avoir le même résultat si une copie de des opérandes est remplacée par l’opérande.

Les algorithmes de la bibliothèque C++ Standard se trouvent dans les fichiers d’en-tête [\<algorithm>](../standard-library/algorithm.md) et [\<numeric>](../standard-library/numeric.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
