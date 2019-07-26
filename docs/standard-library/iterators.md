---
title: Iterators
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: ec23cbea63bc6884a361600362fcf0061e927ca6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449964"
---
# <a name="iterators"></a>Iterators

Un itérateur est un objet qui peut itérer sur les éléments dans un conteneur de bibliothèque standard C++ et fournir un accès à des éléments spécifiques. Les conteneurs de bibliothèque standard C++ fournissent tous des itérateurs permettant aux algorithmes d’accéder à leurs éléments de façon standard, sans avoir à se préoccuper du type de conteneur où les éléments sont stockés.

Vous pouvez utiliser des itérateurs explicitement à l’aide de fonctions membres `begin()` et `end()` globales, telles **++** que **--** et, et des opérateurs tels que et pour avancer ou reculer. Vous pouvez également utiliser des itérateurs implicitement avec une boucle for Range ou (pour certains types d’itérateurs) l'  **\[** opérateur d’indice].

Dans la bibliothèque standard C++, le début d’une séquence ou d’une plage est le premier élément. La fin d'une séquence ou d'une plage est toujours définie comme étant à l'emplacement suivant le dernier élément. Les fonctions `begin` globales `end` et retournent des itérateurs à un conteneur spécifié. La boucle d'itérateur explicite standard sur tous les éléments d'un conteneur ressemble à ceci :

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

La même chose peut être accomplie plus simplement avec une boucle for basée sur un intervalle :

```cpp
for (auto num : vec)
{
    // no deference operator
    cout << num << " ";
}
```

Il existe cinq catégories d'itérateurs. Par ordre de puissance croissante, les catégories sont :

- **Sortie**. Un *itérateur* `X` de sortie peut itérer vers l’avant sur une séquence **++** à l’aide de l’opérateur et ne peut écrire un élément qu' __\*__ une seule fois, à l’aide de l’opérateur.

- **Entrée**. `X` Un *itérateur d’entrée* peut itérer vers l’avant sur une séquence à l’aide de l’opérateur + + et peut lire un élément un nombre quelconque **&ast;** de fois à l’aide de l’opérateur. Vous pouvez comparer les **++** itérateurs d’entrée à l’aide des opérateurs et **! =** . Une fois que vous incrémentez une copie d'un itérateur d'entrée, aucune des autres copies ne peut être comparée, déréférencée ou incrémentée de façon fiable par la suite.

- **Vers l’avant**. Un *itérateur* `X` vers l’avant peut itérer vers l’avant sur une séquence à l’aide de l’opérateur + + et peut lire n’importe quel élément ou écrire des éléments non **&ast;** const un nombre quelconque de fois à l’aide de l’opérateur. Vous pouvez accéder aux membres de l’élément **->** à l’aide de l’opérateur et comparer les **==** itérateurs vers l’avant à l’aide des opérateurs et **! =** . Vous pouvez effectuer plusieurs copies d'un itérateur vers l'avant, chacune d'elles pouvant être déréférencée et incrémentée indépendamment. Un itérateur vers l’avant qui est initialisé sans référence à un conteneur est appelé un *itérateur vers l’avant null*. La comparaison d'itérateurs vers l'avant null donne toujours une égalité.

- **Bidirectionnel**. Un *itérateur* `X` bidirectionnel peut remplacer un itérateur vers l’avant. Toutefois, vous pouvez également décrémenter un itérateur bidirectionnel, comme dans `--X`, `X--`ou `(V = *X--)`. Vous pouvez accéder aux membres de l'élément et comparer des itérateurs bidirectionnels de la même façon que pour des itérateurs vers l'avant.

- **Accès aléatoire**. `X` Un *itérateur à accès aléatoire* peut remplacer un itérateur bidirectionnel. Avec un itérateur à accès aléatoire, vous pouvez utiliser l'  **\[** opérateur d’indice] pour accéder aux éléments. Vous pouvez utiliser les **+** opérateurs **-** **+=** , et **-=** pour déplacer vers l’avant ou vers l’arrière un nombre spécifié d’éléments et pour calculer la distance entre les itérateurs. Vous pouvez comparer les itérateurs bidirectionnels à **==** l’aide de, **\<** **! =** ,, **>=** **>** , **\< =** et.

Tous les itérateurs peuvent être affectés ou copiés. Ils sont censés être des objets légers et sont souvent passés et retournés par valeur, et non par référence. Notez également qu'aucune des opérations décrites précédemment ne peut lever une exception lorsqu'elle est effectuée sur un itérateur valide.

La hiérarchie des catégories d'itérateur peut être résumée en indiquant trois séquences. Pour l'accès en écriture seule à une séquence, vous pouvez utiliser l'une des catégories suivantes :

> itérateur de sortie \
> -> l’itérateur vers l’avant \
> -> itérateur bidirectionnel \
> -> itérateur d’accès aléatoire

La flèche droite signifie "peut être remplacé par". Tout algorithme qui appelle un itérateur de sortie doit fonctionner correctement avec un itérateur vers l’avant, par exemple, mais *pas* dans l’autre sens.

Pour l'accès en lecture seule à une séquence, vous pouvez utiliser l'une des catégories suivantes :

> itérateur d’entrée \
> -> l’itérateur vers l’avant \
> -> itérateur bidirectionnel \
> -> itérateur d’accès aléatoire

Un itérateur d'entrée est le plus faible de toutes les catégories, dans ce cas.

Enfin, pour l'accès en lecture/écriture à une séquence, vous pouvez utiliser l'une des catégories suivantes :

> itérateur vers l’avant \
> -> itérateur bidirectionnel \
> -> itérateur d’accès aléatoire

Un pointeur d'objet peut toujours servir d'itérateur à accès aléatoire, il peut donc être utilisé comme catégorie d'itérateur s'il prend en charge l'accès approprié en lecture et en écriture à la séquence qu'il désigne.

Un itérateur `Iterator` autre qu'un pointeur d'objet doit également définir les types de membres requis par la spécialisation `iterator_traits<Iterator>`. Notez que ces exigences peuvent être remplies en dérivant `Iterator` de la classe de base publique [iterator](../standard-library/iterator-struct.md).

Il est important de comprendre les promesses et les limites de chaque catégorie d’itérateur pour voir comment les itérateurs sont utilisés par les conteneurs et les algorithmes dans la bibliothèque standard C++.

> [!NOTE]
> Vous pouvez éviter d'utiliser des itérateurs explicitement avec des boucles for basées sur un intervalle. Pour plus d’informations, consultez [instruction for basée sur une plage](../cpp/range-based-for-statement-cpp.md).

Microsoft C++ propose désormais des itérateurs vérifiés et des itérateurs de débogage pour s’assurer que vous ne remplacez pas les limites de votre conteneur. Pour plus d’informations, consultez [itérateurs vérifiés](../standard-library/checked-iterators.md) et [Itérateurs de débogage, prise en charge](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
