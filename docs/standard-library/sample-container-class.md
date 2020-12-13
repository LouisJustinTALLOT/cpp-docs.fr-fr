---
description: 'En savoir plus sur : exemple de classe de conteneur'
title: sample container, classe
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: 728cec44462a8e09aad7f87000520f0fa5a15b3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148874"
---
# <a name="sample-container-class"></a>sample container, classe

> [!NOTE]
> Cette rubrique se trouve dans la documentation de Microsoft C++ comme un exemple non fonctionnel de conteneurs utilisés dans la bibliothèque standard C++. Pour plus d’informations, consultez [Conteneurs disponibles dans la bibliothèque standard C++](../standard-library/stl-containers.md).

Décrit un objet qui contrôle une séquence de longueur variable d’éléments, en général de type `Ty` . La séquence est stockée de différentes manières en fonction du conteneur utilisé.

Un constructeur conteneur ou une fonction membre peut trouver l’occasion d’appeler le constructeur **Ty**(**const Ty&**) ou la fonction **Ty::operator=**(**const Ty&**). Si cet appel lève une exception, l’objet conteneur est tenu de maintenir son intégrité et de lever toute autre exception interceptée. Vous pouvez en toute sécurité échanger, assigner, effacer ou détruire un objet conteneur qui a levé l’une de ces exceptions. En général, vous ne pouvez toutefois pas prédire l’état de la séquence contrôlée par l’objet conteneur.

Voici quelques avertissements supplémentaires :

- Si l’expression `~Ty` lève une exception, l’état résultant de l’objet conteneur n’est pas défini.

- Si le conteneur stocke un objet Allocator *al* et que *al* lève une exception autre que le résultat d’un appel à `al.allocate` , l’état résultant de l’objet conteneur n’est pas défini.

- Si le conteneur stocke un objet fonction *comp* pour déterminer comment ordonner la séquence contrôlée et que l’objet *comp* lève une exception quelconque, l’état résultant de l’objet conteneur n’est pas défini.

Les classes de conteneur définies dans la bibliothèque standard C++ satisfont plusieurs conditions supplémentaires, comme cela est décrit dans les paragraphes suivants.

La [liste](../standard-library/list-class.md) des modèles de classe de conteneur fournit un comportement déterministe et utile, même en présence des exceptions décrites ci-dessus. Par exemple, si une exception est levée au moment de l’insertion d’un ou de plusieurs éléments, le conteneur n’est pas modifié et l’exception est levée une nouvelle fois.

Pour *toutes* les classes de conteneur définies par la bibliothèque standard C++, si une exception est levée pendant les appels aux fonctions membres suivantes,, `insert` `push_back` ou `push_front` , le conteneur n’est pas modifié et l’exception est de nouveau levée.

Pour *toutes* les classes de conteneur définies par la bibliothèque standard C++, aucune exception n’est levée pendant les appels aux fonctions membres suivantes : `pop_back` , `pop_front` .

La fonction membre [erase](../standard-library/container-class-erase.md) lève une exception uniquement si une opération de copie (construction assignment ou copy) lève une exception.

En outre, aucune exception n’est levée pendant la copie d’un itérateur retourné par une fonction membre.

La fonction membre [swap](../standard-library/container-class-swap.md) ajoute des promesses pour *toutes* les classes de conteneur définies dans la bibliothèque standard C++  :

- La fonction membre lève une exception uniquement si le conteneur stocke un objet allocateur al, et `al` lève une exception à la fin de la copie.

- Les références, pointeurs et itérateurs qui désignent les éléments des séquences contrôlées permutées restent valides.

Un objet d’une classe de conteneur définie dans la bibliothèque standard C++ alloue et libère du stockage pour la séquence qu’il contrôle via un objet stocké de type `Alloc` (en règle générale, un paramètre de modèle). Un tel objet allocateur doit avoir la même interface externe qu’un objet de classe `allocator<Ty>` . En particulier, `Alloc` doit être du même type que `Alloc::rebind<value_type>::other`

Pour *toutes les* classes de conteneur définies par la bibliothèque standard C++, la fonction membre `Alloc get_allocator const;` retourne une copie de l’objet allocateur stocké. Notez que l’objet allocateur stocké n’est *pas* copié lorsque l’objet conteneur est assigné. Tous les constructeurs initialisent la valeur stockée dans `allocator` , à `Alloc` si le constructeur ne contient pas de paramètre Allocator.

Selon la norme C++, une classe de conteneur définie dans la bibliothèque standard C++ effectue les suppositions suivantes :

- Tous les objets de la classe `Alloc` sont comparés sur une base égale.

- `Alloc::const_pointer`Le type est identique à `const Ty *` .

- `Alloc::const_reference`Le type est identique à `const Ty&` .

- `Alloc::pointer`Le type est identique à `Ty *` .

- `Alloc::reference`Le type est identique à `Ty&` .

Dans cette implémentation, cependant, les conteneurs ne font pas de telles suppositions de simplification. Par conséquent, ils fonctionnent correctement avec des objets allocateurs plus complexes :

- Tous les objets de la classe `Alloc` ne sont pas forcément comparés sur une base égale. (Vous pouvez conserver plusieurs pools de stockage.)

- `Alloc::const_pointer`Le type ne doit pas nécessairement être le même que `const Ty *` . (Un pointeur const peut être une classe.)

- `Alloc::pointer`Le type ne doit pas nécessairement être le même que `Ty *` . (Un pointeur peut être une classe.)

## <a name="requirements"></a>Spécifications

**En-tête**: \<sample container>

## <a name="see-also"></a>Voir aussi

[\<sample container>](../standard-library/sample-container.md)
