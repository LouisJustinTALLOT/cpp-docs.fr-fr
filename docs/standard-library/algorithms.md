---
title: Algorithmes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c67a509c17558c7b388aa288612d73ea26062ec0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846660"
---
# <a name="algorithms"></a>Algorithmes

Les algorithmes sont un élément fondamental de la bibliothèque C++ Standard. Ils ne fonctionnent pas avec des conteneurs proprement dits, mais plutôt avec des itérateurs. Par conséquent, le même algorithme peut être utilisé par la plupart des conteneurs de la bibliothèque C++ Standard (voire tous). Cette section traite des conventions et de la terminologie des algorithmes de la bibliothèque C++ Standard.

## <a name="remarks"></a>Notes

Les descriptions des fonctions de modèle d'algorithme emploient plusieurs expressions raccourcies :

- L’expression « dans la plage [*A*, *B*) » désigne une séquence de zéro, une ou plusieurs valeurs discrètes commençant par *A* et allant jusqu’à *B* non compris. Une plage est valide uniquement si *B* est accessible à partir de *A*. Vous pouvez stocker *A* dans un objet *N* (*N* = *A*), incrémenter l’objet zéro, une ou plusieurs fois (++*N*) et vérifier si l’objet est égal à *B* après un nombre fini d’incréments (N == B *).*

- L’expression « chaque *N* dans la plage [*A*, *B*) » signifie que *N* commence par la valeur *A* et est incrémenté zéro, une ou plusieurs fois jusqu’à être égal à la valeur *B*. Le cas *N* == *B* n’est pas dans la plage.

- L’expression « la plus petite valeur de *N* dans la plage [*A*, *B*) telle que *X* » signifie que la condition *X* est déterminée pour chaque *N* dans la plage [*A*, *B*) jusqu’à ce que la condition *X* soit remplie.

- L’expression « la plus grande valeur de *N* dans la plage [*A*, *B*) telle que *X* » signifie que *X* est déterminé pour chaque *N* dans la plage [*A*, *B*). La fonction stocke dans `K` une copie de *N* chaque fois que la condition *X* est remplie. Si ce stockage se produit, la fonction remplace la valeur finale de *N*, qui est égale à *B*, par la valeur de `K`. Pour un itérateur bidirectionnel ou d’accès aléatoire, toutefois, cela peut également signifier que *N* commence par la plus grande valeur de la plage et est décrémenté sur la plage jusqu’à ce que la condition *X* soit remplie.

- Les expressions comme *X* - *Y*, où *X* et *Y* peuvent être des itérateurs autres que des itérateurs d’accès aléatoire, doivent être interprétées au sens mathématique. La fonction n’évalue pas nécessairement operator**-** si elle doit déterminer cette valeur. Cela vaut également pour les expressions comme *X* + *N* et *X* - *N*, où *N* est un type entier.

Plusieurs algorithmes utilisent un prédicat qui effectue une comparaison par paire, par exemple avec `operator==`, pour générer un résultat `bool`. La fonction de prédicat `operator==`, ou tout remplacement, ne doit pas modifier l'un de ses opérandes. Elle doit générer le même résultat `bool` chaque fois qu'elle est évaluée et doit générer le même résultat si l'opérande est remplacé par une copie de l'un ou l'autre opérande.

Plusieurs algorithmes utilisent un prédicat qui doit imposer un classement faible strict sur des paires d’éléments d’une séquence. Pour le prédicat `pr`(*X*, *Y*) :

- Strict signifie que `pr`(*X*, *X*) a la valeur false.

- Faible signifie que *X* et *Y* ont un ordre équivalent si !`pr`(*X*, *Y*) && !`pr`(*Y*, *X*) (*X* == *Y* ne doit pas obligatoirement être défini).

- Ordre signifie que `pr`(*X*, *Y*) && `pr`(*Y*, Z) implique `pr`(*X*, Z).

Certains de ces algorithmes utilisent implicitement le prédicat *X* \< *Y*. *X* > *Y*, **less**(*X*, *Y*) et `greater`(*X*, *Y*) sont d’autres prédicats qui répondent en général à l’exigence d’ordre faible strict. Notez cependant que des prédicats comme *X* \<= *Y* et *X* >= *Y* ne répondent pas à cet impératif.

Une séquence d’éléments désignée par des itérateurs dans la plage [`First`, `Last`) est une séquence ordonnée par operator**<** si, pour chaque *N* de la plage [0, `Last` - `First`) et pour chaque *M* de la plage (N, `Last` - `First`), le prédicat !(\*(`First` + *M*) < \*(*First* + *N*)) a la valeur true. (Notez que les éléments sont triés par ordre croissant). La fonction de prédicat **operator<**, ou tout remplacement, ne doit pas modifier l’un de ses opérandes. Elle doit générer le même résultat `bool` chaque fois qu'elle est évaluée et doit générer le même résultat si l'opérande est remplacé par une copie de l'un ou l'autre opérande. En outre, elle doit imposer un classement faible strict sur les opérandes qu’elle compare.

Une séquence d’éléments désignée par des itérateurs dans la plage [`First`, `Last`) est un tas ordonné par **operator<** si, pour chaque *N* de la plage [1, `Last` - `First`) le prédicat !(\*`First` < \*(`First` + *N*)) a la valeur true. (Le premier élément est le plus grand.) Sa structure interne est autrement connue uniquement des fonctions de modèle [make_heap](../standard-library/algorithm-functions.md#make_heap), [pop_heap](../standard-library/algorithm-functions.md#pop_heap), et [push_heap](../standard-library/algorithm-functions.md#push_heap). Comme avec une séquence ordonnée, la fonction de prédicat **operator<**, ou tout remplacement, ne doit pas modifier l’un de ses opérandes et elle doit imposer un ordre faible strict sur les opérandes qu’elle compare. Elle doit générer le même résultat `bool` chaque fois qu'elle est évaluée et doit générer le même résultat si l'opérande est remplacé par une copie de l'un ou l'autre opérande.

Les algorithmes de la bibliothèque C++ Standard se trouvent dans les fichiers d’en-tête [\<algorithm>](../standard-library/algorithm.md) et [\<numeric>](../standard-library/numeric.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
